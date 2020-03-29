# NoSQLite
*A Rusty NoSQL layer over SQLite*

![](https://github.com/HiruNya/nosqlite/workflows/Rust/badge.svg)
[![](https://github.com/HiruNya/nosqlite/workflows/Documentation/badge.svg)](https://hiru.dev/docs/nosqlite/nosqlite/index.html)

[Documentation can be found here.](https://hiru.dev/docs/nosqlite/nosqlite/index.html)

The intention of this crate is to allow the user to use this library
as if it was a NoSQL library (e.g. only deal with JSON objects, no schema, etc.)
but have the data stored in a SQLite database,
which is a great single-file database.
It does this by using SQLite's Json1 extension
and [`rusqlite`](https://github.com/jgallagher/rusqlite)'s safe bindings.

Unfortunately due to the requirement of parsing and serializing JSON,
this crate may not perform as fast as using `SQLite` directly.
However this crate does try to be as ergonomic and flexible as possible.

## Features
- Insert JSON objects.
- Get and remove JSON objects by primary key.
- Iterate through multiple entries in a table.
- Filter and Sort the entries by using the fields in a JSON object
or columns in the SQL table.
- Get *only* the primary key, JSON object,
or specific field(s) from the JSON object.
- Set, insert, replace, and remove fields in a JSON object.
- 'Patch' JSON objects with other JSON objects.

## To Do
- Set, insert, and replace fields of a single entry using its primary key.
- Add indexes to speed up queries.

## Install
In your `Cargo.toml` file add this
```toml
[dependencies]
nosqlite = { git = "https://github.com/HiruNya/nosqlite.git" }
```
This crate may have breaking changes in its API so I would recommend also adding
in the specific commit to ensure your code does not break.

I have considered publishing this crate onto [crates.io]
but since I'm the only one currently using it I decided against it.
If you wish to use this crate and would prefer installing it the normal way using [crates.io]
then please don't hesitate in making an issue.

## Inspirations
[hotpot-db](https://github.com/drbh/hotpot-db)
was the original database that used SQLite and its Json1 extension.
However it didn't have certain functions that I needed
for a personal project of mine but is still a great crate
depending on your use case.

[crates.io]: https://crates.io