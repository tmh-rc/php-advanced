# Flash Message <!-- omit from toc -->

- [Todo](#todo)
- [Steps](#steps)
  - [Step 1](#step-1)
  - [Step 1](#step-1-1)
  - [Step 3](#step-3)
- [Testing](#testing)

## Todo

- Create a `Session` class as [Laravel Session](https://laravel.com/docs/5.3/session#using-the-session)

## Steps

### Step 1

Create a file in `Core/Session.php`. The code structure of `Session` class must follow the specified guidelines.

```php
<?php

namespace Core;

class Session
{
    public function put($key, $value)
    {
        //TODO: Store $value to session
    }

    public function get($key, $default = null)
    {
        //TODO: Retrieve $value from session by $key
        //TODO: What if not found, return $default
    }

    public function has($key)
    {
        //TODO: To determine if a $value is present in the session.
    }

    public function flash($key, $value)
    {
        //TODO: Store $value in session by $key name
        //TODO: delete after calling from session function by $key name
    }

    public function forget($key)
    {
        //TODO: Remove $value from session by $key name
    }

    public function flush($key)
    {
        //TODO: Remove all data from the session
    }
}
```

### Step 1

In the controller, add a flash message after performing `create`, `update`, or `delete` operations.

```diff
    class MovieController
    {
        public function store()
        {
            $this->db->query('INSERT...', [
                ...
            ]);

+           Session::flash('success', 'A movie was created successfully.');

            redirect('/movies');
        }

        public function update($id)
        {
            $this->db->query('UPDATE...', [
                ...
            ]);

+           Session::flash('success', 'A movie was updated successfully.');

            redirect('/movies');
        }

        public function destroy($id)
        {
            $movie = $this->db->query('DELETE...', ['id' => $id]);

+           Session::flash('success', 'A movie was updated successfully.');

            redirect('/movies');
        }
    }
```

### Step 3

In the view, display the flash message that was added from the controller.

```diff
    // views/movies/index.php
+   <div><?php echo \Core\Session::get('success'); ?></div>
    <ul>
    <?php foreach($movies as $movie): ?>
        ...
    <?php endforeach; ?>
    </ul>
```

## Testing

The flash message must be shown whenever performing `create`, `update`, or `delete` operations.