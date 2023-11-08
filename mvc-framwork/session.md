# Flash Message <!-- omit from toc -->

- [Todo](#todo)
- [Steps](#steps)
  - [Step 1](#step-1)
  - [Step 1](#step-1-1)
  - [Step 3](#step-3)
- [Testing](#testing)

## Todo

- Create `Session` class as [Laravel Session](https://laravel.com/docs/5.3/session#using-the-session)

## Steps

### Step 1

Create a file in `Core/Session.php`. 

```php
<?php

namespace Core;

class Session
{
    public function put($key, $value)
    {
        // Store $value to session
    }

    public function get($key, $default = null)
    {
        // Retrieve $value from session by $key
        // What if not found, return $default
    }

    public function has($key)
    {
        // To determine if a $value is present in the session.
    }

    public function flash($key, $value)
    {
        // Store $value in session by $key name
        // delete after calling from session function by $key name
    }

    public function forget($key)
    {
        // Remove $value from session by $key name
    }

    public function flush($key)
    {
        // Remove all data from the session
    }
}
```

### Step 1

In Controller, put flash message after `create` or `update` or `delete`.

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

In view, display flash message.

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

Flash message must shown after created or updated.