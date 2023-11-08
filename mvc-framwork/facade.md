# Facade <!-- omit from toc -->

- [Todo](#todo)
- [Steps](#steps)
  - [Step 1](#step-1)
  - [Step 2](#step-2)
  - [Step 3](#step-3)
  - [Step 4](#step-4)
- [Testing](#testing)

## Todo

- Create a Facade as [Laravel Facade](https://laravel.com/docs/10.x/facade)

## Steps

### Step 1

Create the files following:

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
+   │   └── Facade.php
+   ├── Facades/
+   │   └── DB.php
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
    └── test.php
```

### Step 2

Create DB facade. Code must be following:

```php
<?php

namespace Core\Facades;

use Core\Database;

/**
 * @see \Core\Database
 */
class DB extends Facade
{
    protected static function getFacadeAccessor()
    {
        return new Database();
    }
}
```

### Step 3

Replace all `DB` facade at `Database`. See following eg.

```diff
+   use Facades\DB;

    class MovieController
    {
-      private $db;

-      public function __construct()
-      {
-          $this->db = new Database;
-      }

        public function index()
        {
-           $movies = $this->db->query('SELECT...')->get();
+           $movies = DB::query('SELECT...')->get();

            echo view('movies.index', [
                'movies' => $movies
            ]);
        }
```

### Step 4

Consider what code should write in `Facade` class

```php
<?php

namespace Core\Facades;

use RuntimeException;

class Facade
{
    // TODO: code here
}
```

## Testing

- All query must work as previous although replace `DB` facade.