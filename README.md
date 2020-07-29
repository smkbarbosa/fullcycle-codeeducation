# Laravel APP

Aplicação base utilizando:

* Laravel
* Mysql
* Redis
* Nginx

## Como executar

1. Clone o repositório

```
git clone https://github.com/smkbarbosa/fullcycle-laravel.git
```

2. Inicie os containers
```
docker-compose up -d
```

3. Acesse o container e gere o .env

```
docker exec -it app bash
cp .env-example .env
```

4. Edite o .env e altere as informações de acesso ao banco de dados e redis
```
...
DB_CONNECTION=mysql
DB_HOST=db
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=root
DB_PASSWORD=root
...
REDIS_HOST=redis
REDIS_PASSWORD=null
REDIS_PORT=6379
```

5. Gere a key
```
php artisan key:generate
```

6. Faça as migrations
```
php artisan migrate
```

## Utilizando a imagem base do Laravel
Ocasionalmente, você pode pular os passos 3 a 6 utilizando a imagem:

<https://hub.docker.com/r/barbosasmk/laravel-fullcycle>

Para isso, edite o arquivo docker-compose.yml, retire a linha build do app e altere por:
```
services:
    app:
        image: barbosasmk/laravel-fullcycle

```

Depois, execute o docker-compose:
```
docker-compose up -d
```