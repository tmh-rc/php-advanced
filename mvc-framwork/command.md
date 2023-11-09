# Command

## Todo

- Create own artisan command.

## Steps

### Step 1

Create a file named `artisan`.

```diff
    movie-app/
    ├── Controllers/
    │   ├── HomeController.php
    │   ├── LoginController.php
    │   ├── RegisterController.php
    │   └── MovieController.php
    ├── config/
    │   └── database.php
    ├── Core/
    │   ├── Router.php
    │   ├── Database.php
    │   ├── Validator.php
    │   ├── Auth.php
    │   ├── Facade.php
    │   └── File.php
    ├── Facades/
    │   └── Database.php
    ├── public/
    │   └── index.php
    ├── routes/
    │   └── web.php
    ├── views/
    │   ├── movies/
    │   │   ├── index.php
    │   │   ├── create.php
    │   │   └── edit.php
    │   └── auth/
    │       ├── login.php
    │       └── register.php
    ├── autoload.php
    ├── test.php
+   └── artisan
```

### Step 2

Write a code in `artisan` file to run PHP web server. When run in terminal following command

```
php artisan serve
```

Must work as following command

```
php -S localhost:8080 -t public/
```

### Step 3

Must be able to change port. Default port is 8080.

```
php artisan serve --port=8000
```

## Testing

App must be up and running ‌as before when run the command `php artisan serve` or `php artisan serve --port=8080`.

```
http://localhost:8080
```