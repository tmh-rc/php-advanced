# Validation Automatic Redirection

## Todos

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