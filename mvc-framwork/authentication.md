# Authentication <!-- omit from toc -->

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

- Create `Auth` class.

## Steps

### Step 1

Create the files according to the outlined structure.

```diff
    movie-app/
    ├── Controllers/
    │   ├── HomeController.php
+   │   ├── LoginController.php
+   │   ├── RegisterController.php
    │   └── MovieController.php
    ├── config/
    │   └── database.php
    ├── Core/
    │   ├── Router.php
    │   ├── Database.php
    │   ├── Validator.php
+   │   └── Auth.php
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
+   │       ├── login.php
+   │       └── register.php
    ├── autoload.php
    └── test.php
```

### Step 2

The code structure of `Auth` class must follow the specified guidelines.

```php
<?php

namespace Core;

class Auth
{
    public function attempt($credentials = []): array|null
    {
        // TODO: Authenticate the user
        // TODO: If authentication is successful, store user info to session and return user
        // TODO: else return null 
    }

    public function user(): array|null
    {
        // TODO: if login user is exist in session, return user otherwise null; 
    }

    public function id(): int|null
    {
        // TODO: if login user is exist in session, return user's id otherwise null; 
    }

    public function check(): bool
    {
        // TODO: check logged in or not
    }

    public function logout()
    {
        // TODO: remove user from session
    }
}
```

### Step 3

Create the auth routes.

```php
$router->get('/login', LoginController::class, 'create');
$router->post('/login', LoginController::class, 'store');
$router->post('/logout', LoginController::class, 'destroy');

$router->get('/register', RegisterController::class, 'create');
$router->post('/register', RegisterController::class, 'store');
```

### Step 4

The code in `RegisterController.php` must adhere to the following.

```php
class RegisterController
{
    public function create()
    {
        echo view('auth.register');
    }

    public function store()
    {
        $data = request()->all();

        Validator::make($data, [
            'email' => ['required', 'email', 'max:255'],
            'password' => ['required'],
        ])->validate();

        $db = new Database();
        $db->query('INSERT INTO users (email, password) VALUES (:email, :password)', [
            'email' => $data['email'],
            'password' => bcrypt($data['password']),
        ])

        redirect('/');
    }
}
```

### Step 5

The code in `LoginController.php` must adhere to the following.

```php
class LoginController
{
    public function create()
    {
        echo view('auth.login');
    }

    public function store()
    {
        $data = request()->all();

        Validator::make($data, [
            'email' => ['required', 'email', 'max:255'],
            'password' => ['required'],
        ])->validate();

        if (!$user = Auth::attempt($data)) {
            Session::flash('errors',[
                'email' => ['Email or password is incorrect.'],
            ]);

            return redirect('/login');
        }

        redirect('/');
    }

    public function destroy()
    {
        Auth::logout();

        redirect('/login');
    }
}
```

### Step 6

Create the `login` from in `views/auth/login.php` and `register` form in `views/auth/register.php`.

## Testing

It must be able to login and register.