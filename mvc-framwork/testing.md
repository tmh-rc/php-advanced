# Testing <!-- omit from toc -->

## Todo

Write a integration testing for movie using [PHPUnit](https://packagist.org/packages/phpunit/phpunit)

## Steps

### Step 1

Create folders and files as following outlined structure for testing.

```diff
    movie-app/
    ├── Controllers/
    │   ├── HomeController.php
    │   ├── LoginController.php
    │   ├── RegisterController.php
    │   ├── MovieController.php
    │   └── API/
    │       └── MovieController.php
    ├── config/
    │   └── database.php
    ├── Core/
    │   ├── Router.php
    │   ├── Database.php
    │   ├── Validator.php
    │   ├── Auth.php
    │   ├── Facade.php
    │   ├── File.php
    │   └── Response
    ├── Facades/
    │   └── Database.php
    ├── public/
    │   └── index.php
    ├── routes/
    │   ├── web.php
    │   └── api.php
    ├── views/
    │   ├── movies/
    │   │   ├── index.php
    │   │   ├── create.php
    │   │   └── edit.php
    │   └── auth/
    │       ├── login.php
    │       └── register.php
+   ├── tests/
+   │   └── MovieListTest.php
+   │   └── MovieDetialTest.php
+   │   └── MovieCreateTest.php
+   │   └── MovieEditTest.php
+   │   └── MovieDeleteTest.php
    ├── autoload.php
    ├── test.php
    └── artisan
```

### Step 2

Install [PHPUnit](https://packagist.org/packages/phpunit/phpunit)

### Step 3

The code structure must follow the specified guidelines.

```php
// MovieListTest.php
<?php

use PHPUnit\Framework\TestCase;

final class MovieListTest extends TestCase
{
    public function test_movie_list_screen_can_be_rendered(): void
    {

    }

    public function test_can_paginate_movies(): void
    {
        
    }
}
```

```php
// MovieShowTest.php
<?php

use PHPUnit\Framework\TestCase;

final class MovieShowTest extends TestCase
{
    public function test_movie_detail_screen_can_be_rendered(): void
    {

    }

    public function test_can_be_see_a_specific_movie(): void
    {
        
    }
}
```

```php
// MovieCreateTest.php
<?php

use PHPUnit\Framework\TestCase;

final class MovieCreateTest extends TestCase
{
    public function test_movie_create_screen_can_be_rendered(): void
    {

    }

    public function test_authenticated_users_can_create_a_new_movie(): void
    {
        
    }

    public function test_unauthenticated_users_cannot_create_a_new_movie(): void
    {
        
    }

    public function test_a_movie_require_a_title(): void
    {
        
    }

    public function test_a_movie_require_a_duration_minutes(): void
    {
        
    }

    public function test_a_movie_require_a_plot_summary(): void
    {
        
    }

    public function test_a_movie_require_a_released_at(): void
    {
        
    }

    public function test_a_movie_require_a_poster_image(): void
    {
        
    }
}
```

```php
// MovieEditTest.php
<?php

use PHPUnit\Framework\TestCase;

final class MovieEditTest extends TestCase
{
    public function test_movie_edit_screen_can_be_rendered(): void
    {

    }

    public function test_authenticated_users_can_edit_a_movie(): void
    {
        
    }

    public function test_unauthenticated_users_cannot_edit_a_movie(): void
    {
        
    }

    public function test_a_movie_require_a_title(): void
    {
        
    }

    public function test_a_movie_require_a_duration_minutes(): void
    {
        
    }

    public function test_a_movie_require_a_plot_summary(): void
    {
        
    }

    public function test_a_movie_require_a_released_at(): void
    {
        
    }

    public function test_a_movie_require_a_poster_image(): void
    {
        
    }
}
```

```php
// MovieDeleteTest.php
<?php

use PHPUnit\Framework\TestCase;

final class MovieDeleteTest extends TestCase
{
    public function test_authenticated_users_can_delete_a_movie(): void
    {
        
    }

    public function test_unauthenticated_users_cannot_delete_a_movie(): void
    {
        
    }
}
```

## Testing

All test must pass.

```
./vendor/bin/phpunit tests/MovieListTest.php
./vendor/bin/phpunit tests/MovieShowTest.php
./vendor/bin/phpunit tests/MovieCreateTest.php
./vendor/bin/phpunit tests/MovieEditTest.php
./vendor/bin/phpunit tests/MovieDeleteTest.php
```