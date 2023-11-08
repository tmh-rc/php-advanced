# File Uploading <!-- omit from toc -->

- [Todo](#todo)
- [Steps](#steps)
  - [Step 1](#step-1)
  - [Step 2](#step-2)
  - [Step 3](#step-3)
  - [Step 3](#step-3-1)
  - [Step 4](#step-4)
- [Testing](#testing)

## Todo

- Create a `File` class to handle files

## Steps

### Step 1

Create the following files

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
    │   ├── Facade.php
+   │   └── File.php
    ├── Facades/
    │   └── Database.php
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

The code structure of `File` class must follow the specified guidelines.

```php
<?php

namespace Core;

class File
{
    public function getClientOriginalName(): string
    {
        // TODO: code
    }

    public function storeAs($dir, $fileName): string
    {
        // TODO: code
    }

    public function store($dir): string
    {
        // TODO: code
    }

    public function delete(string $filePath): void
    {
        // TODO: code
    }
}
```

### Step 3

Add methods `file` and `hasFile` in the `Request` class as shown below.

```php
class Request
{
    ...
    public function file(string $name): File
    {
        return new File($name);
    }

    public function hasFile(string $name): bool
    {
        // TODO: Check file exist or not
    }
}
```

### Step 3

Change field `text` to `file` in the movie create and edit form.

`views/movies/create.php`

```diff
<h3>Movie Create</h3>
<form action="/movies" method="POST">
    ...
-   <input type="text" name="poster_image_path">
+   <input type="file" name="poster_image">
    ...
</form>
```

`views/movies/edit.php`

```diff
<h3>Movie Edit</h3>
<form action="/movies/<?php echo $movie['id'] ?>" method="POST">
    ...
-   <input type="text" name="poster_image_path" value="<?php echo $movie['poster_image_path']; ?>">
+   <input type="file" name="poster_image">
+   <img src="<?php echo asset($movie['poster_image_path']) ?>">
    ...
</form>
```

### Step 4

Update method `store` and `update` in MovieController as shown below.

```diff
    class MovieController
    {
        public function store()
        {
            ...

+           $filePath = request()->file('poster_image')->store('upload/image/');
+           // or
+           // $file = request()->file('poster_image');
+           // $fileName = $fil->getClientOriginalName();
+           // $filePath = $file->storeAs('upload/image/', $fileName);

            DB::query('INSERT...', [
                ...
-               'poster_image_path' => request('poster_image_path'),
+               'poster_image_path' => $filePath,
            ]);

            redirect('/movies');
        }

        public function update($id)
        {
            $validator = Validator::make(request()->all(), [
                ...
-               'poster_image_path' => ['required'],
+               'poster_image' => ['required', 'file', 'image'],
            ]);

+           if (request()->hasFile('poster_image')) {
+               File::delete($movie['poster_image_path']); // delete old image
+               $filePath = request()->file('poster_image')->store('upload/images/');
+           }

            DB::query('UPDATE...', [
                ...
-               'poster_image_path' => request('poster_image_path'),
+               'poster_image_path' => $filePath,
            ]);

            redirect('/movies');
        }
    }
```

## Testing

The image can be uploaded and displayed on the page.
