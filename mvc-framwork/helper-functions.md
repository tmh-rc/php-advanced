# Helper Functions

Write following helper functions as [Laravel helpers](https://laravel.com/docs/10.x/helpers) in `Core/helpers.php`

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
```
- [dd]()
- [base_path]()
- [public_path]()
- [url]()
- [redirect]()
- [abort]()
- [bcrypt]()
- [request]()
- [response]()

## Usage Functions

Use base_path function in `public/index.php` file

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
