# File Downloading <!-- omit from toc -->

- [Todo](#todo)
- [Steps](#steps)
  - [Step 1](#step-1)
  - [Step 2](#step-2)
- [Testing](#testing)

## Todo

- Add a `download` method in `File` class

## Steps

### Step 1

Add `download` method in File class as shown below

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

When the download button is clicked, the movie will start downloading.

[Previous](./file-uploading.md)
