# Validation Rules <!-- omit from toc -->

- [Todo](#todo)
- [Steps](#steps)
  - [Step 1](#step-1)
- [Testing](#testing)

## Todo

Define validation rules as shown below.

- required
- min:number (eg. min:10 )
- max:number (eg. max:255)
- number
- unique
- file
- image
- video
- nullable

## Steps

### Step 1

Add more validation rules in the controllers

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

## Testing

More defined validations rules must work correctly.

[Previous](./validation.md) | [Next](./validation-automatic-redirection.md)
