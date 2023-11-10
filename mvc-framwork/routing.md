# Routing <!-- omit from toc -->

- [Todo](#todo)
- [Steps](#steps)
  - [Step 1](#step-1)
  - [Step 2](#step-2)
  - [Step 3](#step-3)
  - [Step 4](#step-4)
  - [Step 5](#step-5)
- [Testing](#testing)

## Todo

- Write routing system in the `Core/Router.php` files.

## Steps

### Step 1

Create folders and files as following outlined structure within the `movie-app` folder.

> Note: No need to delete previous folders and files.

```diff
    movie-app/
    ├── Controllers/
    │   ├── HomeController.php
+   │   └── MovieController.php
    ├── Core/
    │   └── Router.php
+   ├── public/
+   │   └── index.php
+   ├── routes/
+   │   └── web.php
    ├── autoload.php
    └── test.php
```

### Step 2

The code structure in `MovieController.php` must follow the specified guidelines.

```php
<?php

namespace Controllers;

class MovieController
{
    public function index()
    {
        echo "Movie list";
    }

    public function show($id)
    {
        echo "Movie detail by ID: $id";
    }

    public function create()
    {
        echo "Movie Create";
    }

    public function store()
    {
        echo "Movie Store";
    }

    public function edit($id)
    {
        echo "Movie Edit by ID: $id";
    }

    public function update($id)
    {
        echo "Movie Update by ID: $id";
    }

    public function destroy($id)
    {
        echo "Movie Destroy by ID: $id";
    }
}
```

### Step 3

The code structure in `routes/web.php` must follow the specified guidelines.

```php
<?php

use Controllers/MovieController;

$router->get('movies', [MovieController::class, 'index']);
$router->get('movies/create', [MovieController::class, 'create']);
$router->post('movies', [MovieController::class, 'store']);
$router->get('movies/(\w+)/edit', [MovieController::class, 'edit']);
$router->put('movies/(\w+)', [MovieController::class, 'update']);
$router->get('movies/(\w+)', [MovieController::class, 'show']);
$router->delete('movies/(\w+)', [MovieController::class, 'destroy']);
```

### Step 4

The code structure in `public/index.php` must follow the specified guidelines.

```php
<?php

require '../autoload.php';

use Core\Router;

$router = new Router;
require 'routes/web.php';
$router->route();
```

### Step 5

The code structure in `Core/Router.php` must follow the specified guidelines.

```php
<?php

namespace Core;

class Router
{
    protected $routes = [];

    public function add($method, $uri, $action)
    {
        $this->routes[] = [
            'method' => $method,
            'uri' => $uri,
            'controller' => $controller,
            'action' => $action
        ];

        return $this;
    }

    public function get(string $uri,array $action)
    {
        return $this->add('GET', $uri, $action[0], $action[1]);
    }

    public function post(string $uri,array $action)
    {
        return $this->add('POST', $uri, $action[0], $action[1]);
    }

    public function delete(string $uri,array $action)
    {
        return $this->add('DELETE', $uri, $action[0], $action[1]);
    }

    public function patch(string $uri,array $action)
    {
        return $this->add('PATCH', $uri, $action[0], $action[1]);
    }

    public function put(string $uri,array $action)
    {
        return $this->add('PUT', $uri, $action[0], $action[1]);
    }

    public function route()
    {
        // Write code
    }
}
```

## Testing

Write code in the `route` method using regular expressions for the URI. Ensure that the following routes function correctly.

> Note: No form has been created yet. Therefore, test with [Postman](https://www.postman.com/).

<details>
<summary><code>GET</code> <code>/movies</code></summary>

##### Code: 200 <!-- omit from toc -->

##### Content <!-- omit from toc -->

```
Movie list
```

</details>

<details>
<summary><code>GET</code> <code>/movies/123</code></summary>

##### Code: 200 <!-- omit from toc -->

##### Content <!-- omit from toc -->

```
Movie detail by ID: 123
```

</details>

<details>
<summary><code>GET</code> <code>/movies/create</code></summary>

##### Code: 200 <!-- omit from toc -->

##### Content <!-- omit from toc -->

```
Movie Create
```

</details>

<details>
<summary><code>POST</code> <code>/movies</code></summary>

##### Code: 200 <!-- omit from toc -->

##### Content <!-- omit from toc -->

```
Movie Store
```

</details>

<details>
<summary><code>GET</code> <code>/movies/123/edit</code></summary>

##### Code: 200 <!-- omit from toc -->

##### Content <!-- omit from toc -->

```
Movie Edit by ID: 123
```

</details>

<details>
<summary><code>PUT</code> <code>/movies/123</code></summary>

##### Code: 200 <!-- omit from toc -->

##### Content <!-- omit from toc -->

```
Movie Update by ID: 123
```

</details>

<details>
<summary><code>DELETE</code> <code>/movies/123</code></summary>

##### Code: 200 <!-- omit from toc -->

##### Content <!-- omit from toc -->

```
Movie Destroy by ID: 123
```

</details>

[Previous](./autoloading-classes.md) | [Next](./advanced-routing.md)
