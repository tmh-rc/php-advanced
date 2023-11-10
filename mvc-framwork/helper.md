# Helper <!-- omit from toc -->

- [Todo](#todo)
- [Class](#class)
- [Functions](#functions)
- [Testing](#testing)

## Todo

Write the following helper functions and class as [Laravel helpers](https://laravel.com/docs/10.x/helpers) in `Core/helpers.php`

## Class

The code structure of `Request` class must follow the specified guidelines.

```php
<?php

namespace Core;

class Request
{
    public function all(): array
    {
        // TODO: return all user input requsts
    }

    public function query(): array
    {
        // TODO: return all query parameters
    }

    public function get(string $name, mixed $default = null): mixed
    {
        // TODO: return request by name
    }
}
```

## Functions

eg.

```php
<?php

if (!function_exists('dd')) {
    function dd($value)
    {
        echo '<pre>';
        var_dump($value);
        echo '</pre>';
        exit();
    }
}

if (!function_exists('request')) {
    function request(string $value, mixed $default): mixed
    {
        $request = new Request;

        return $value ? $request->get($value, $default) : $request;
    }
}
```

- [dd]()
- [base_path]()
- [public_path]()
- [url]()
- [redirect]()
- [abort]()
- [bcrypt]()

## Testing

Use `base_path` function in `public/index.php` file

```diff
// pubic/index.php
<?php

require '../autoload.php';

use Core\Router;

$router = new Router;
- require 'routes/web.php';
+ require base_path('routes/web.php');
$router->route();
```

[Previous](./advanced-routing.md) | [Next](./view.md)
