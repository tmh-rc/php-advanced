# Validation Automatic Redirection <!-- omit from toc -->

- [Todo](#todo)
- [Steps](#steps)
  - [Step 1](#step-1)
- [Testing](#testing)


## Todo

- Add `validate` method to automatic redirection when validation failed

```php
class Validator
{
    public function validate():void
    {
        // code
    }
}
```

## Steps

### Step 1

```php
// Old
$validator = Validator::make(request()->all(), [
    'title' => ['required', 'min:10', 'max:255', 'unique:movie'],
    'duration_minutes' => ['required', 'number'],
    ...
]);

if ($validator->fails()) {
    Session::flash('errors', $validator->errors());
    return redirect('movie/create');
}
```

```php
// New
$validator = Validator::make(request()->all(), [
    'title' => ['required', 'min:10', 'max:255', 'unique:movie'],
    'duration_minutes' => ['required', 'number'],
    ...
])->validate();
```

## Testing

Must work previous state.