# View

## Todo

- Make view

## Steps

Create view files `index.php`, `create.php`, `edit.php` in `views/movies` folder

```diff
    movie-app/
    ├── Controllers/
    │   ├── HomeController.php
    │   └── MovieController.php
    ├── Core/
    │   └── Router.php
    ├── public/
    │   └── index.php
    ├── routes/
    │   └── web.php
+   ├── views/
+   │   └── movies/
+   │       ├── index.php
+   │       ├── show.php
+   │       ├── create.php
+   │       └── edit.php
    ├── autoload.php
    └── test.php
```

Put this code in `views/movies/index.php`
```html
Movie list
```

Put this code in `views/movies/show.php`
```php
Movie detail by ID: <?php echo $id ?>
```

Put this code in `views/movies/create.php`
```php
Movie Create
```

Put this code in `views/movies/edit.php`
```php
Movie Edit by ID: <?php echo $id ?>
```

Response view from `index`, `show`, `create`, `edit` methods of controller

```php
<?php

namespace Controllers;

class MovieController
{
    public function index()
    {
        echo view('movies.index');
    }

    public function show($id)
    {
        echo view('movies.show', [
            'id' => $id
        ]);
    }

    public function create()
    {
        echo view('movies.create');
    }

    public function edit($id)
    {
        echo view('movies.edit', [
            'id' => $id
        ]);
    }
}
```

Page must work [previous movie routes](./routing.md#testing)
