# RESTful API <!-- omit from toc -->

- [Todo](#todo)
- [Steps](#steps)
  - [Step 1](#step-1)
  - [Step 2](#step-2)
  - [Step 3](#step-3)
  - [Step 4](#step-4)
- [Testing](#testing)

## Todo

- Create `Response` class in `Core` folder
- Create `RESTful` API

```diff
    movie-app/
    ├── Controllers/
    │   ├── HomeController.php
    │   ├── LoginController.php
    │   ├── RegisterController.php
    │   ├── MovieController.php
+   │   └── API/
+   │       └── MovieController.php
    ├── config/
    │   └── database.php
    ├── Core/
    │   ├── Router.php
    │   ├── Database.php
    │   ├── Validator.php
    │   ├── Auth.php
    │   ├── Facade.php
    │   ├── File.php
+   │   └── Response
    ├── Facades/
    │   └── Database.php
    ├── public/
    │   └── index.php
    ├── routes/
    │   ├── web.php
+   │   └── api.php
    ├── views/
    │   ├── movies/
    │   │   ├── index.php
    │   │   ├── create.php
    │   │   └── edit.php
    │   └── auth/
    │       ├── login.php
    │       └── register.php
    ├── autoload.php
    ├── test.php
    └── artisan
```

## Steps

### Step 1

Create a file in `Core/Response.php`. The code structure of `Response` class must follow the specified guidelines.

```php
<?php

namespace Core;

class Response
{
    public static function json(array $data = [],int $statusCode = 200): array
    {
        // TODO: code here
    }
}
```

### Step 2

Create RESTful routes for movies in `routes/api.php`

```php
use

use Controllers/API/MovieController;

$router->get('movies', [MovieController::class, 'index']);
$router->get('movies/{id}', [MovieController::class, 'show']);
$router->post('movies', [MovieController::class, 'store']);
$router->put('movies/{id}', [MovieController::class, 'update']);
$router->delete('movies/{id}', [MovieController::class, 'destroy']);
```

### Step 3

Create a file in `Controller/API/MovieController.php`. The code structure must follow the specified guidelines.

```php
<?php

namespace Controllers\API;

use Core/Database;

class MovieController
{
    public function index()
    {
        $movies = DB::query('SELECT...')->paginate();

        echo Response::json($movies, 200);
    }

    public function show($id)
    {
        $movie = DB::query('SELECT...', ['id' => $id])->first();

        if(! $movie) {
            echo Response::json(['message' => 'Page not found.'], 404);
            return;
        }

        echo Response::json($movies, 200);
    }

    public function store()
    {
        $validator = Validator::make(request()->all(), [
            'title' => ['required'],
            'duration_minutes' => ['required'],
            'plot_summary' => ['required'],
            'released_at' => ['required'],
            'poster_image' => ['required', 'image'],
        ])->validate();

        $filePath = request()->file('poster_image')->store('upload/image/');

        DB::query('INSERT...', [
            'title' => request('title'),
            'duration_minutes' => request('duration_minutes'),
            'plot_summary' => request('plot_summary'),
            'released_at' => request('released_at'),
            'poster_image_path' => $filePath,
        ]);

        $movie = DB::query('SELECT...', ['id' => $id])->first();

        echo Response::json($movies, 200);
    }

    public function update($id)
    {
        $movie = DB::query('SELECT...', ['id' => $id])->first();

        if(! $movie) {
            echo Response::json(['message' => 'Page not found.'], 404);
            return;
        }

        $validator = Validator::make(request()->all(), [
            'title' => ['required'],
            'duration_minutes' => ['required'],
            'plot_summary' => ['required'],
            'released_at' => ['required'],
            'poster_image' => ['nullable', 'image'],
        ])->validate();

        if (request()->hasFile('poster_image')) {
            File::delete($movie['poster_image_path']); // delete old image
            $filePath = request()->file('poster_image')->store('upload/images/');
        }

        DB::query('UPDATE...', [
            'id' => $id,
            'title' => request('title'),
            'duration_minutes' => request('duration_minutes'),
            'plot_summary' => request('plot_summary'),
            'released_at' => request('released_at'),
            'poster_image_path' => $filePath,
        ]);

        $movie = DB::query('SELECT * ..', ['id' => $id])->first();

        echo Response::json($movie, 200);
    }

    public function destroy($id)
    {
        $movie = DB::query('SELECT...', ['id' => $id])->first();

        if(! $movie) {
            echo Response::json(['message' => 'Page not found.'], 404);
            return;
        }

        $movie = DB::query('DELETE...', ['id' => $id]);

        echo Response::json([], 200);
    }
}
```

### Step 4

API response must be following.

<details>
<summary><code>GET</code> <code>/movies</code></summary>

##### Code: 200 <!-- omit from toc -->

##### Content <!-- omit from toc -->

```json
[
    {
        "id": 1,
        "title": "Movie Title",
        "duration_minutes": 120,
        "plot_summary": "Lorem ...",
        "released_at": "2023-11-9",
        "poster_image_path": "http://localhost:8080/upload/image/image_name.png"
    },
    ...
]
```

</details>

<details>
<summary><code>GET</code> <code>/movies/{id}</code></summary>

##### Code: 200 <!-- omit from toc -->

##### Content <!-- omit from toc -->

```json
{
  "id": 1,
  "title": "Movie Title",
  "duration_minutes": 120,
  "plot_summary": "Lorem ...",
  "released_at": "2023-11-9",
  "poster_image_path": "http://localhost:8080/upload/image/image_name.png",
  "created_at": "2023-11-9 00:00:00",
  "updated_at": "2023-11-9 00:00:00"
}
```

</details>

<details>
<summary><code>POST</code> <code>/movies</code></summary>

##### Parameters <!-- omit from toc -->

| Name             | Type     | Data Type |
| ---------------- | -------- | --------- |
| title            | required | string    |
| duration_minutes | required | int       |
| plot_summary     | required | string    |
| released_at      | required | date      |
| poster_image     | required | file      |

##### Code: 200 <!-- omit from toc -->

##### Content <!-- omit from toc -->

```json
{
  "id": 1,
  "title": "Movie Title",
  "duration_minutes": 120,
  "plot_summary": "Lorem ...",
  "released_at": "2023-11-9",
  "poster_image_path": "http://localhost:8080/upload/image/image_name.png",
  "created_at": "2023-11-9 00:00:00",
  "updated_at": "2023-11-9 00:00:00"
}
```

##### Code: 422 <!-- omit from toc -->

##### Content <!-- omit from toc -->

```json
{
  "errors": {
    "title": ["The title field is required."],
    "duration_minutes": ["The duration minutes field is required."],
    "plot_summary": ["The plot summary field is required."],
    "released_at": ["The released at field is required."],
    "poster_image": ["The poster image field is required."]
  }
}
```

</details>

<details>
<summary><code>POST</code> <code>/movies/{id}</code></summary>

##### Parameters <!-- omit from toc -->

| Name             | Type     | Data Type | Description         |
| ---------------- | -------- | --------- | ------------------- |
| \_method         | required | string    | The value is 'PUT'. |
| title            | required | string    |                     |
| duration_minutes | required | int       |                     |
| plot_summary     | required | string    |                     |
| released_at      | required | date      |                     |
| poster_image     | required | file      |                     |

##### Code: 200 <!-- omit from toc -->

##### Content <!-- omit from toc -->

```json
{
  "id": 1,
  "title": "Movie Title",
  "duration_minutes": 120,
  "plot_summary": "Lorem ...",
  "released_at": "2023-11-9",
  "poster_image_path": "http://localhost:8080/upload/image/image_name.png",
  "created_at": "2023-11-9 00:00:00",
  "updated_at": "2023-11-9 00:00:00"
}
```

##### Code: 422 <!-- omit from toc -->

##### Content <!-- omit from toc -->

```json
{
  "errors": {
    "title": ["The title field is required."],
    "duration_minutes": ["The duration minutes field is required."],
    "plot_summary": ["The plot summary field is required."],
    "released_at": ["The released at field is required."],
    "poster_image": ["The poster image field must be image."]
  }
}
```

</details>

<details>
<summary><code>POST</code> <code>/movies/{id}</code></summary>

##### Parameters <!-- omit from toc -->

| Name     | Type     | Data Type | Description ...        |
| -------- | -------- | --------- | ---------------------- |
| \_method | required | string    | The value is 'DELETE'. |

##### Code: 200 <!-- omit from toc -->

##### Content <!-- omit from toc -->

```json
{}
```

</details>

## Testing

Perform CRUD operations.

[Previous]() | [Next]()
