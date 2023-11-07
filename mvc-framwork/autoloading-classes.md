# Autoloading Classes

## Todo
- Create own autoloading classes in `autoload.php` file.

## Steps

Create project folder named `movie-app`. Inside the folder, create controllers and routes following tree.

```
movie-app
├─ Controllers
│  └─ HomeController.php
├─ Core
│  └─ Router.php
├─ autoload.php
└─ test.php
```

Put this code in `Controllers/HomeController.php`

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

Put this code in `Core/Router.php`

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

Put this code in `test.php`

```php
<?php

require 'autoload.php';

use Controllers\HomeController;

(new HomeController)->index();
(new HomeController)->index();
```

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