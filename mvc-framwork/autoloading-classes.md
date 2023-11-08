# Autoloading Classes

## Todo
- Create own autoloading classes in `autoload.php` file.

## Steps

### Step 1

Create project folder named `movie-app`. Inside the folder, create controllers and routes following tree. The `test.php` file for testing.

```
movie-app
├─ Controllers
│  └─ HomeController.php
├─ Core
│  └─ Router.php
├─ autoload.php
└─ test.php
```

### Step 2

The code in `Controllers/HomeController.php` must be following

```php
<?php

namespace Controllers;

class HomeController
{
    public function index()
    {
        echo "I am HomeController.\n";
    }
}
```

### Step 3

The code in `Core/Router.php` must be following

```php
<?php

namespace Core;

class Router
{
    public function route()
    {
        echo "I am Router.\n";
    }
}
```

### Step 4

Write following code in `test.php` to test `autoload` is working or not.

```php
<?php

require 'autoload.php';

use Controllers\HomeController;

(new HomeController)->index();
(new HomeController)->index();
```

## Testing

Write code in `autoload.php` using `spl_autoload_register` function to see following result when run the `test.php` file in terminal.

**In terminal**
```
php test.php
```

**Result**
```
I am HomeController.
I am Router.
```