---
description: 'https://www.youtube.com/watch?v=zSOCPtYnlCQ&ab_channel=EscolaMobile'
---

# Composer packages development

How to make reusable code?

Polish version of this presentation you may find at: [https://docs.google.com/presentation/d/1T5EL4nj3UuLyXjORtK86YzQ8DK58Xff5iIWvoTeEW10/edit](https://docs.google.com/presentation/d/1T5EL4nj3UuLyXjORtK86YzQ8DK58Xff5iIWvoTeEW10/edit)

## Why you should use packages?

1. Keep reusable code that you can use in any project.
2. Work faster, more effective and keep quality at highest level.
3. Easy split work through all team members.
4. Easy code access, without unnecessary side effects. 
5. More independent than monolith, that allows you for easier refactors.

## How to initialize package?

### Composer init

See branch: stage/1

#### Add to required

```text
{
    "php": ">=7.4",
    "laravel/framework": ">=7.0",
}
```

#### Add to require-dev

```text
{
    "phpunit/phpunit": "^9.0",
    "orchestra/testbench": ">=5.0"
}
```

Then install your composer.

### Namespace register

See branch: stage/2

Add your package namespaces to composer for example

```text
"autoload": {
    "psr-4": {
        "Escola\\Presentation\\": "src",
        "Escola\\Presentation\\Tests\\": "tests",
        "Database\\Factories\\Escola\\Presentation\\Models\\": "database/factories"
    }
},
```

And create dirs:

```text
mkdir ./src
mkdir ./tests
mkdir -p ./database/factories
```

## How to write Laravel package

See branch: stage/3

### Defining ServiceProvider

#### Add Extra Composer key

```text
"extra": {
    "laravel": {
        "providers": [
            "Escola\\Presentation\\PackageServiceProvider"
        ]
    }
}
```

#### Create PackageServiceProvider class

Create class that extends `Illuminate\Support\ServiceProvider` and contains methods register and boot

```php
namespace Escola\Presentation;

use Illuminate\Support\ServiceProvider;

class PackageServiceProvider extends ServiceProvider
{
    public function register()
    {

    }

    public function boot()
    {

    }
}
```

#### Defining and loading migrations and factories

See branch: stage/4

```php
$this->loadMigrationsFrom(__DIR__ . '/../database/migrations');
```

All migrations will be now running from `./database/migrations` directory.

#### Configuration setup

Into your Service provider add

```php
$this->mergeConfigFrom(
    __DIR__ . '/config.php', 'presentation'
);
```

Your config will be available under `config("presentation.KEY")`.

#### Publishing files form library

See branch: stage/5

In final, we should also tell laravel, that this files may be also overwritten after publish.

To do that, add publishes method with array with key as file and value as publish destination.

```php
$this->publishes([
     __DIR__ . '/config.php' => config_path('presentation.php')
], 'presentation');
```

### Orchestra testbench as testing framework

See branch: stage/6

You already install testbench, but now let's try to use it.

`php ./vendor/bin/testbench` will prompt you with all available commands, like migrations, routes and much more.

For example, you can create migration for your package using:

```text
php ./vendor/bin/testbench make:migration create_example_table --path=./database/migrations --realpath
```

Adding `path` and `realpath` parameters are required - otherwise migration will be created under `./vendor/orchestra/testbench-core/laravel/database`

All the documentation you can find here: [https://packages.tools/testbench/getting-started/introduction.html](https://packages.tools/testbench/getting-started/introduction.html)

Let's add some columns to our migration.

```php
Schema::create('example', function (Blueprint $table) {
    $table->id();
    $table->string('name');
    $table->boolean('status');
    $table->timestamps();
});
```

And migrate it with `php ./vendor/bin/testbench migrate`. It will not give us any error, but in fact none migrations will be executed.

To do that, lets try to configure testbench.

#### Configure test environment

See branch: stage/7

To use our own configuration for database for example, we need to use `testbench.yaml` file.

```yaml
env:
  - DB_CONNECTION="sqlite"
  - DB_DATABASE="{ABSOLUTE_PATH}/db.sqlite"

providers:
  - Escola\Presentation\PackageServiceProvider
```

Adding provider to `testbench.yaml` is important - otherwise you will run declared migrations.

Also let's create db.sqlite in our directory.

```bash
touch ~/code/composer-presentation/db.sqlite
```

after run

```text
./vendor/bin/testbench migrate
```

we will have sqlite database with example table.

#### Write any tests

See branch: stage/8

Writing tests on packages is also easy and not required laravel bootstrap from app file. Let's create some test using orchestra.

First, let's define our phpunit configuration.

```markup
<?xml version="1.0" encoding="UTF-8"?>
<phpunit backupGlobals="false"
         backupStaticAttributes="false"
         bootstrap="vendor/autoload.php"
         colors="true"
         convertErrorsToExceptions="true"
         convertNoticesToExceptions="true"
         convertWarningsToExceptions="true"
         processIsolation="false"
         stopOnFailure="false">
    <testsuite name="Presentation package">
        <directory suffix="Test.php">./tests</directory>
    </testsuite>
    <php>
        <env name="APP_KEY" value="AckfSECXIvnK5r28GVIWUAxmbBSjTsmF"/>
        <env name="DB_CONNECTION" value="sqlite"/>
        <env name="DB_DATABASE" value="{ABSOLUTE_PATH}/db.sqlite"/>
    </php>
</phpunit>
```

And create example test:

```php
<?php

namespace Escola\Presentation\Tests\Features;

use Orchestra\Testbench\TestCase;

class AttachmentTest extends TestCase
{
    public function test_that_true_is_not_false(): void
    {
        $this->assertTrue(!false);
    }
}
```

Now, this example test could be written in PHPUnit Test case, but Orchestra can give us a little more options, like standard Laravel test can give us.

See branch stage/9

For example let's add new test:

```php
public function test_that_config_works(): void
{
    $this->assertEquals('example', config('presentation.test'));
}
```

And run it - we will not have valid result, but config function is known to our test.

What we should do to make it works, it's register information, similar to `testbench.yaml`.

```php
protected function getPackageProviders($app)
{
    return [\Escola\Presentation\PackageServiceProvider::class];
}
```

And add `test` key into config.php array with value `example`. Then run `phpunit`, and it will pass.

## How to use packages

1. path including
2. git link
3. packagist

