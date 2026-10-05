# Testing Controllers

application/database/migrations/001_install_ion_auth.php
-> 20150920182600_install_ion_auth.php

# Database Migrations

Update the migration config file.

```
--- a/CodeIgniter/application/config/migration.php
+++ b/CodeIgniter/application/config/migration.php
@@ -6,7 +6,7 @@ $config['migration_auto_latest'] = FALSE
 | be upgraded | downgraded to.
 /*
-$config['migration_version'] = 20150907090030;
+$config['migration_version'] = 20150920182600;
 /*
 |\-
```

The listing above is in a format called unified diff. It shows the difference between two files. In short, remove the red line starting with - from the original file and add the green line starting with +, to get the new file. See Conventions Used in This Book for details.

Run the migrations via CLI.

```
$ php index.php dbfixture migrate
```

If there is no output, the migration ran and the groups, users, users_groups, login_attempts tables were created successfully. You can confirm this using the sqlite3 command.

```
$ sqlite3 application/data/sqlite-database.db
SQLite version 3.8.5 2014-08-15 22:37:57
Enter ".help" .schema groups
sqlite> CREATE TABLE "groups" (
  "id" INTEGER PRIMARY KEY AUTOINCREMENT,
  "name" VARCHAR NOT NULL,
  "description" VARCHAR NOT NULL
);
sqlite> .schema users
```