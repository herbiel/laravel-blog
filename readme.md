# Laravel Blog

A simple blog for demonstration purpose. Based on Laravel 7.0

## Requirements

- Laravel 7.0
- PHP >= 7.2.5
- OpenSSL PHP Extension
- PDO PHP Extension
- Mbstring PHP Extension
- Tokenizer PHP Extension
- XML PHP Extension
- Ctype PHP Extension
- JSON PHP Extension
- BCMath PHP Extension

## Demo

You can try the live demo : [http://gentle-everglades-40337.herokuapp.com/](http://gentle-everglades-40337.herokuapp.com/)

## Demo login info

user: contact@milon.im | password: password


## Installation

```
git clone https://github.com/milon/laravel-blog.git blog
cd blog
composer install
cp .env.example .env
php artisan key:generate
php artisan migrate
php artisan db:seed
```

If you want dummy data, then run this-

```
php artisan db:seed --class=DummyDataSeeder
```

## API Endpoints

This projects exposes some API endpoints. You could request those endpoints with the `api_token` passed as query parameters, like this- `/api/tags?api_token=YOUR_API_KEY`. You can also pass the token as a Authorization Bearer token. The API key could be obtained from `/api/auth/token` endpoint. Available endpoints are-

```
/api/auth/token
/api/auth/reset-password
/api/auth/change-password

/api/tags
/api/categories
/api/users     // only accessible by admin
/api/posts
```

These endpoints are also available as a [Postman](https://www.postman.com/) collection [here](./Laravel-Blog.postman_collection.json).

## Author

- [Nuruzzaman Milon](https://milon.im)

Feel free to email me, if you have any question.


### Docker
#### build image
```
cd Docker/nginx && docker build -t laravel-nginx:v1 .
cd Docker/php && docker build -t laravel-php:v1 .
```
#### start 
edit .env 
```
cp .env.example .env 
```
```
docker-compose up -d
``` 
#### init laravel-env
```
sudo docker-compose exec php composer install
sudo docker-compose exec php php artisan key:generate
sudo docker-compose exec php php artisan migrate
sudo docker-compose exec php php artisan db:seed
sudo docker-compose exec php chown -R 99:99 /app
sudo docker-compose exec nginx chown -R 99:99 /app
```