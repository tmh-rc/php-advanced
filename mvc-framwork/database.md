# Model <!-- omit from toc -->

- [Todo](#todo)
- [Steps](#steps)
  - [Step 1](#step-1)
  - [Step 1](#step-1-1)
  - [Step 3](#step-3)
- [Testing](#testing)

## Todo

Create Database class in `Core/Database.php` for Model

## Steps

### Step 1

Create a database `mtm_movie`

Create table `movies`

| Name              | Type                | Nullable | Default           |
|-------------------|---------------------|----------|-------------------|
| id                | int auto_increment  | No       |                   |
| title             | varchar(255)        | No       |                   |
| duration_minutes  | int                 | No       |                   |
| plot_summary      | text                | No       |                   |
| released_at       | date                | No       |                   |
| poster_image_path | varchar(255)        | No       |                   |
| created_at        | datetime            | No       | current_timestamp |
| updated_at        | datetime            | No       | current_timestamp |

### Step 1

Create files

```diff
    movie-app/
    ├── Controllers/
    │   ├── HomeController.php
    │   └── MovieController.php
+   ├── config/
+   │   └── database.php
    ├── Core/
    │   ├── Router.php
+   │   └── Database.php
    ├── public/
    │   └── index.php
    ├── routes/
    │   └── web.php
    ├── views/
    │   └── movies/
    │       ├── index.php
    │       ├── create.php
    │       └── edit.php
    ├── autoload.php
    └── test.php
```

### Step 3

Put code in `config/database.php`. Use correct database credentials.

```php
<?php

return [
    'host' => '127.0.0.1',
    'port' => '3306',
    'database' => 'mtm_movie',
    'username' => 'root',
    'password' => '',
    'charset' => 'utf8mb4',
    'collation' => 'utf8mb4_unicode_ci',
]

```

## Testing

Write code database abstraction layer in `Core/Database.php` to working following code.

```php
// test.php
$db = new Database();

// Insert
$db->query('INSERT INTO ....', [
        'title' => 'Movie Title',
        'duration_minutes' => '120',
        'plot_summary' => 'lorem ....',
        'released_at' => '2020-11-07',
        'poster_image_path' => 'upload/image/foo.png',
    ]);

// Fetch all
$movies = $db->query('SELECT * ....')->get();
dd($movies);

// Output
// [
//     [
//         'id' => 1,
//         'title' => 'Movie Title',
//         'duration_minutes' => '120',
//         'plot_summary' => 'lorem ....',
//         'released_at' => '2020-11-07',
//         'poster_image_path' => 'upload/image/foo.png',
//         'created_at' => '2020-11-07 00:00:00',
//         'created_at' => '2020-11-07 00:00:00',
//     ],
//         [
//         'id' => 2,
//         'title' => 'Movie Title 2',
//         'duration_minutes' => '120',
//         'plot_summary' => 'lorem ....',
//         'released_at' => '2020-11-07',
//         'poster_image_path' => 'upload/image/bar.png',
//         'created_at' => '2020-11-07 00:00:00',
//         'created_at' => '2020-11-07 00:00:00',
//     ]
// ]

// Fetch by id
$movie = $db->query('SELECT * FROM movies WHERE id=:id', ['id' => 1])->first();

dd($movie);

// Output
// [
//     'id' => 1,
//     'title' => 'Movie Title',
//     'duration_minutes' => '120',
//     'plot_summary' => 'lorem ....',
//     'released_at' => '2020-11-07',
//     'poster_image_path' => 'upload/image/foo.png',
//     'created_at' => '2020-11-07 00:00:00',
//     'created_at' => '2020-11-07 00:00:00',
// ]

// Update
$db->query('UPDATE ....', [
        'title' => 'Movie Title Changed',
    ]);

// Delete
$db->query('DELETE .... WHERE id=:id', [
        'id' => 1,
    ]);
```