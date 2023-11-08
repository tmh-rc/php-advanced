# File Downloading

## Todo

- Add `download` method in File class

## Steps

### Step 1

Add `download` method in File class. See following

```php
class File
{
    ...
    public function download($path)
    {
        // TODO: Write code to download the file
    }
}
```

### Step 2

Add download link button in movie detail page.

```php
<a href="<?php \Core\File::download($movie['poster_image_path']) ?>">Download Movie</a>
```

## Testing

When click the download button, the movie must download.