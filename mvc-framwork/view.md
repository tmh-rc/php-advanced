# View  <!-- omit from toc -->

- [Todo](#todo)
- [Steps](#steps)
  - [Step 1](#step-1)
  - [Step 2](#step-2)
  - [Step 3](#step-3)
  - [Step 4](#step-4)
  - [Step 5](#step-5)
  - [Step 6](#step-6)
- [Testing](#testing)

## Todo

- Make view

## Steps

### Step 1

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

### Step 2

Put this code in `views/movies/index.php`

```html
Movie list
```

### Step 3

Put this code in `views/movies/show.php`

```php
Movie detail by ID: <?php echo $id ?>
```

### Step 4

Put this code in `views/movies/create.php`

```php
Movie Create
```

### Step 5

Put this code in `views/movies/edit.php`

```php
Movie Edit by ID: <?php echo $id ?>
```

### Step 6

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

## Testing

Page must work [previous movie routes](./routing.md#testing)
