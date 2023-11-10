# Batch Command <!-- omit from toc -->

- [Todo](#todo)
- [Steps](#steps)
  - [Step 1](#step-1)
  - [Step 2](#step-2)
  - [Step 3](#step-3)
- [Testing](#testing)

## Todo

- Create a batch command

## Steps

### Step 1

Create folders and files as following outlined structure for testing.

```diff
    movie-app/
+   ├── Commands/
+   │   └── ExportUsersBatch.php
    ├── Controllers/
    │   ├── HomeController.php
    │   ├── LoginController.php
    │   ├── RegisterController.php
    │   ├── MovieController.php
    │   └── API/
    │       └── MovieController.php
    ├── config/
    │   └── database.php
    ├── Core/
    │   ├── Router.php
    │   ├── Database.php
    │   ├── Validator.php
    │   ├── Auth.php
    │   ├── Facade.php
    │   ├── File.php
    │   └── Response
    ├── Facades/
    │   └── Database.php
    ├── public/
    │   └── index.php
    ├── routes/
    │   ├── web.php
    │   └── api.php
    ├── views/
    │   ├── movies/
    │   │   ├── index.php
    │   │   ├── create.php
    │   │   └── edit.php
    │   └── auth/
    │       ├── login.php
    │       └── register.php
    ├── tests/
    │   ├── MovieListTest.php
    │   ├── MovieShowTest.php
    │   ├── MovieCreateTest.php
    │   ├── MovieEditTest.php
    │   └── MovieDeleteTest.php
    ├── autoload.php
    ├── test.php
    └── artisan
```

### Step 2

Write code in `ExportUsersBatch.php` to export users.

```php
<?php

// Step 1: Connect to the Database
// Code to establish a database connection

// Step 2: Fetch all users from the database
// Code to retrieve user data

// Step 3: Prepare CSV data
// Code to format user data into CSV format

// Step 4: Download the CSV file
// Code to send the CSV file as a download

```

### Step 3

Call the `ExportUsersBatch.php` batch whenever want to download the users as a CSV file.

## Testing

The ExportUserBatch.php batch must function correctly.
