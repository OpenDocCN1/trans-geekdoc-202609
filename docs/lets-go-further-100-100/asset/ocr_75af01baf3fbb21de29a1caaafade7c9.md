# Working with SQL Migrations

Now that the `migrate` tool is installed, let’s illustrate how to use it by creating a new `movies` table in our database.

The first thing we need to do is generate a pair of *migration files* using the `migrate create` command. If you’re following along, go ahead and run the following command in your terminal:

```
$ migrate create -seq -ext=.sql -dir=./migrations create_movies_table
/home/alex/Projects/greenlight/migrations/000001_create_movies_table.up.sql
/home/alex/Projects/greenlight/migrations/000001_create_movies_table.down.sql
```

In this command:

+   - The `-seq` flag indicates that we want to use sequential numbering like `0001`, `0002`, `...` for the migration files (instead of a Unix timestamp, which is the default).
+   - The `-ext` flag indicates that we want to give the migration files the extension `.sql`.
+   - The `-dir` flag indicates that we want to store the migration files in the `./migrations` directory (which will be created automatically if it doesn’t already exist).