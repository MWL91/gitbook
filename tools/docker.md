# Docker

## Budowanie czystego kontenera bez prune

docker-compose build --no-cache

docker-compose up --force-recreate

## Czyszczenie dockera

docker stop $(docker ps -a -q)

docker kill $(docker ps -q)

docker prune



Hadolint

Cntr
