# Elastic search

Paczka Scout / Elasticsearch

{% embed url="https://github.com/Jeroen-G/Explorer" %}

Docker compose Jędrzeja

```
version: '3.7'
services:
  app:
    build:
      context: ./docker
      dockerfile: Dockerfile-dev
    restart: unless-stopped
    volumes:
    - .:/usr/src/app
    command:
    - bash
    - -c
    - |
      if [ ! -f "/usr/src/init" ]; then
        composer install
        php artisan key:generate
        sleep 15
        php artisan migrate --seed
        php artisan jwt:secret --always-no
        touch /usr/src/init
      fi
      exec apache2-foreground
    depends_on:
      - mysql_service
      - elasticsearch
  mysql_service:
    image: mariadb:10.5
    restart: unless-stopped
    environment:
      MYSQL_ROOT_PASSWORD: ${DB_PASSWORD}
      MYSQL_DATABASE: ${DB_DATABASE}
    ports:
      - ${DB_PORT:-3306}:3306
  adminer:
    image: adminer
    restart: unless-stopped
    environment:
      - ADMINER_DEFAULT_SERVER=mysql_service
  redis:
    image: redis:5.0
    restart: unless-stopped
    ports:
      - ${REDIS_PORT:-6379}:6379
  elasticsearch:
    build:
      context: ./docker
      dockerfile: Dockerfile-elastic
    ports:
      - ${ELASTICSEARCH_PORT:-9200}:9200
    environment:
      - xpack.security.enabled=false
      - discovery.type=single-node
  kibana:
    image: docker.elastic.co/kibana/kibana:8.1.0
    environment:
      - ELASTICSEARCH_HOSTS=http://elasticsearch:${ELASTICSEARCH_PORT:-9200}
    depends_on:
      - elasticsearch
  nginx:
    image: nginx
    restart: unless-stopped
    volumes:
      - ./docker/nginx:/etc/nginx/templates
    ports:
      - ${DOCKER_PORT:-80}:80
    environment:
      - ADMINER_PREFIX=${DOCKER_ADMINER_PREFIX:-adminer}
      - KIBANA_PREFIX=${DOCKER_KIBANA_PREFIX:-kibana}
      - SILVERBOX_PREFIX=${DOCKER_SILVERBOX_PREFIX:-silverbox}
    depends_on:
      - app
      - adminer
      - kibana
  silverbox:
    image: heseya/silverbox:1.2.0
    restart: unless-stopped
    command:
      - bash
      - -c
      - |
        if [ ! -f "/usr/src/init" ]; then
          php silverbox client:add ${SILVERBOX_CLIENT} ${SILVERBOX_KEY}
          chown -R www-data:www-data storage
          touch /usr/src/init
        fi
        exec apache2-foreground
    networks:
      default:
        aliases:
          - ${SILVERBOX_HOST}
```



{% embed url="https://www.elastic.co/" %}

