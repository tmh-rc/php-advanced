# Validation Rules <!-- omit from toc -->

- [Todo](#todo)
- [Testing](#testing)

## Todo

Must be validate following rules

- required
- min:number (eg. min:10 )
- max:number (eg. max:255)
- number
- unique
- file
- image
- video
- nullable

## Testing

Add more validation rules in controllers

```diff
    class MovieController
    {
        public function store()
        {
            $validator = Validator::make(request()->all(), [
-               'title' => ['required'],
+               'title' => ['required', 'min:10', 'max:255', 'unique:movie'],
-               'duration_minutes' => ['required'],
+               'duration_minutes' => ['required', 'number'],
                'plot_summary' => ['required'],
                'released_at' => ['required'],
                'poster_image_path' => ['required'],
            ]);
            ...
        }

        public function update($id)
        {
            $validator = Validator::make(request()->all(), [
-               'title' => ['required'],
+               'title' => ['required', 'min:10', 'max:255', 'unique:movie,title,' . $id . ',id'],
-               'duration_minutes' => ['required'],
+               'duration_minutes' => ['required', 'number'],
                'plot_summary' => ['required'],
                'released_at' => ['required'],
                'poster_image_path' => ['required'],
            ]);
            ...
        }
    }
```