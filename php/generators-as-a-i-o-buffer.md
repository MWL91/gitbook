# Generators as a I/O buffer

```php
function getLines($file) {
    $f = fopen($file, 'r');
    try {
        while ($line = fgets($f)) {
            yield $line;
        }
    } finally {
        fclose($f);
    }
}

foreach (getLines("file.txt") as $n => $line) {
    if ($n > 5) break;
    echo $line;
}
```

