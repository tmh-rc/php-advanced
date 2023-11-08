# Auto loading Classes <!-- omit from toc -->

- [Todo](#todo)
- [Steps](#steps)
  - [Step 1](#step-1)
  - [Step 2](#step-2)
  - [Step 3](#step-3)
  - [Step 4](#step-4)
- [Testing](#testing)

## Todo
- Create your own auto loading classes in the `autoload.php` file.

## Steps

### Step 1

Create a project folder named 'movie-app'. Inside this folder, establish controllers and routes following the outlined structure, and include a 'test.php' file for testing purposes.

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

The code structure in `HomeController.php` must follow the specified guidelines.

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

The code structure in `Router.php` must follow the specified guidelines.

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

Write code in `autoload.php` using the `spl_autoload_register` function to see following result when run the `test.php` file in terminal.

**In terminal**
```
php test.php
```

**Result**
```
I am HomeController.
I am Router.
```