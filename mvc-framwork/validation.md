# Validation

## Todos

- Create `Validator` class. Must include `make`, `fails` and `errors` method as following

```php
<?php

namespace Core;

class Validator
{
    public static make($data, $rules)
    {
        // code
    }

    public static fails(): boolean
    {
        // code
    }

    public static errors(): array
    {
        // code
    }
}
```

## Steps

Create a `Core/Validator` file.

```diff
    movie-app/
    ├── Controllers/
    │   ├── HomeController.php
    │   └── MovieController.php
    ├── config/
    │   └── database.php
    ├── Core/
    │   ├── Router.php
    │   ├── Database.php
+   │   └── Validator.php
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

Usage Validating in controller

```diff
    <?php

    namespace Controllers;

    use Core/Database;
    use Core/Validator;

    class MovieController
    {
        public function store()
        {
+           $validator = Validator::make(request()->all(), [
+               'title' => ['required'],
+               'duration_minutes' => ['required'],
+               'plot_summary' => ['required'],
+               'released_at' => ['required'],
+               'poster_image_path' => ['required'],
+           ]);
+            if ($validator->fails()) {
+               Session::flash('errors', $validator->errors());
+               return redirect('movie/create');
+           }

            $this->db->query('INSERT...', [
                ...
            ]);

            redirect('/movies');
        }

        public function update($id)
        {
+           $validator = Validator::make(request()->all(), [
+               'title' => ['required'],
+               'duration_minutes' => ['required'],
+               'plot_summary' => ['required'],
+               'released_at' => ['required'],
+               'poster_image_path' => ['required'],
+           ]);
+
+           if ($validator->fails()) {
+               Session::flash('errors', $validator->errors());
+               return redirect("movie/$id/edit");
+           }

            $this->db->query('UPDATE...', [
                ...
            ]);

            redirect('/movies');
        }
    }
```

Display error in create and edit form

```diff
    // views/movies/create.php
    <h3>Movie Create</h3>
+   <?php if(\Core\Session::has('errors')): ?>
+       <ul>
+           <?php foreach(\Core\Session::get('errors') as $error): ?>
+               <li><?php echo $error ?></li>
+           <?php endforeach; ?>
+       </ul>
+   <?php endif: ?>
    <form action="/movies" method="POST">
        <input type="text" name="title">
        ...
        <input type="text" name="released_at">
        <button type="submit">Create</button>
    </form>
```

```diff
    // views/movies/edit.php
    <h3>Movie Create</h3>
+   <?php if(\Core\Session::has('errors')): ?>
+       <ul>
+           <?php foreach(\Core\Session::get('errors') as $error): ?>
+               <li><?php echo $error ?></li>
+           <?php endforeach; ?>
+       </ul>
+   <?php endif: ?>
    <form action="/movies/<?php echo $movie['id'] ?>" method="POST">
        <input type="hidden" name="_method" value="PUT">
        ...
        <button type="submit">Update</button>
    </form>
```

## Testing

Must display error message when validation failed.