# Authorization And Middleware <!-- omit from toc -->

- [Todo](#todo)
- [Steps](#steps)
  - [Step 1](#step-1)
- [Testing](#testing)

## Todo

- Create middleware in Router

## Steps

### Step 1

Add middleware in auth routes. See following:

```php
$router->get('/login', LoginController::class, 'create')->middleware('guest');
$router->post('/login', LoginController::class, 'store')->middleware('guest');
$router->post('/logout', LoginController::class, 'destroy')->middleware('auth');

$router->get('/register', RegisterController::class, 'create')->middleware('guest');
$router->post('/register', RegisterController::class, 'store')->middleware('guest');
```

## Testing

- `login` and `register` can be used to only allow unauthenticated users
- `logout` can be used to only allow authenticated users
