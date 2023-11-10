# CSV <!-- omit from toc -->

- [Todo](#todo)
- [Steps](#steps)
  - [Step 1](#step-1)
  - [Step 2](#step-2)
  - [Step 3](#step-3)
- [Testing](#testing)

## Todo

Create CSV exporting and importing of user data without using any package.

## Steps

### Step 1

Implement CRUD operations for users inspired by the movie system

### Step 2

Multiple users can be created, edited, or deleted with validation by importing from a CSV file. Refer to the following CSV format.

> If the action is `CREATE`, the row must be created.
> If the action is `UPDATE`, the row must be updated.
> If the action is `DELETE`, the row must be deleted.

```
id, name, email, password, action
, Mg Mg, mgmg@gmail.com, 123123123, CREATE
, Tun Tun, tuntun@gmail.com, 123123123, CREATE
5, Aye Aye, mgmg@gmail.com, 123123123, UPDATE
9, Mg Mg, mgmg@gmail.com, 123123123, DELETE
```

### Step 3

Execute the export of multiple users in CSV format. Refer to the following CSV format.

```
id, name, email, created at, updated at
1, Mg Mg, mgmg@gmail.com, 2023-11-10 00:00:00
2, Tun Tun, tuntun@gmail.com, 2023-11-10 00:00:00
3, Aye Aye, mgmg@gmail.com, 2023-11-10 00:00:00
4, Mg Mg, mgmg@gmail.com, 2023-11-10 00:00:00
```

## Testing

The CSV export and import features need to work properly.
