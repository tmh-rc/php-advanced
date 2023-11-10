# Pagination <!-- omit from toc -->

- [Todo](#todo)
- [Steps](#steps)
  - [Step 1](#step-1)
  - [Step 2](#step-2)
  - [Step 3](#step-3)
- [Testing](#testing)

## Todo

- Create Pagination

## Steps

### Step 1

Add `paginate` method in `Database` class.

```php
class Database
{
    ...
    public function paginate($limit = 15)
    {
        //TODO: code here
    }
}
```

### Step 2

Change `get` method to `paginate` in `index` method of the `MovieController`

```diff
class MovieController
{
    ...
    public function index()
    {
-       $movies = $this->db->query('SELECT...')->get();
+       $movies = DB::query('SELECT...')->paginate();

        echo view('movies.index', [
            'movies' => $movies
        ]);
    }
...
```

### Step 3

Show movies through pagination on the movie list page instead of showing all movies.

## Testing

The movies can be paginated.
