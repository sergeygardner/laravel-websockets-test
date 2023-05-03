## Requirements

- the 8000 port mast be free 
- the 6001 port mast be free 

## Start project

```shell
docker-compose -f Service/Docker/docker-compose.yml up -d
```

## Using container
```shell
docker exec -ti web-socket-php sh 
```

## Before start services

```shell
composer install
php artisan migrate
php artisan vendor:publish --provider="BeyondCode\LaravelWebSockets\WebSocketsServiceProvider" --tag="config"
```

## Start websockets in the first instance for interacting with the container

```shell
php artisan websockets:serve
```

## Start application

```shell
php artisan serve --host 0.0.0.0
```

## Laravel Tinker

```shell
php artisan tinker
event (new \App\Events\Test('test'));
```

## Using curl

```shell
curl -o - --no-buffer --include --header "Connection: Upgrade" --header "Upgrade: websocket" --header "Sec-WebSocket-Key: x3JJHMbDL1EzLkh9GBhXDw==" --header "Sec-WebSocket-Version: 13" "http://0.0.0.0:6001/app/websocketkey"
```
