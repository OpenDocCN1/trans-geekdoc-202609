
The GRANT query to add a new account for use in the PHP programs for the PetCatalog database might be

```
GRANT select ON PetCatalog.* TO phpuser@localhost
IDENTIFIED BY 'A41!14a!'
```

## Adding and changing passwords

You can add or change passwords by using the GRANT query. You can include a password requirement when you add a new account, as I describe in the preceding section. If an account already exists, you can change its password by using the following GRANT query:

```
GRANT permission ON * TO accountname@hostname
IDENTIFIED BY 'password'
```

You need to fill in the following information:

- ✓ *permission*: You must list at least one permission in a GRANT query. If the permission has already been granted, it is not changed.
- ✓ *accountname@hostname*: If the account already exists, it's given the indicated permission and password. If the account doesn't exist, the account is added. The account is identified by the accountname and hostname as a pair. If an account exists with the specified account name but a different hostname, the account is not changed; a new one is created.
- ✓ *password*: The password in the GRANT query replaces the existing password. If you supply an empty password using

```
IDENTIFIED BY ''
```

the existing password is replaced with a blank, leaving the account with no password. For tips on choosing a good password, check out the "Finding out about passwords" section, earlier in the chapter.

## Removing permissions

To remove permissions, use the REVOKE query. The general format is

```
REVOKE permission (columns) ON tablename
FROM accountname@hostname
```

You need to fill in the following information:

- **permission (columns):** You must list at least one permission. You can remove each permission from one or more columns by listing the column name in parentheses following the permission. If no column name is listed, the permission is removed from all columns in the table(s). You can list as many permission/columns as needed, separated by commas. The possible permissions are listed in Table 5-1. For instance, a `REVOKE` query might start like this:

```
REVOKE select (firstName,lastName), update, insert (birthdate) ...
```

- **tablename:** Indicate which tables the permission is being removed from. At least one table is required. You can list several tables, separated by commas. The possible values for `tablename` are
  - **tablename:** The entire table named `tablename` in the current database. You can use an asterisk (`*`) to mean all tables. If you use an asterisk when no current database is selected, the privilege will be revoked on all tables on all databases.
  - **databasename.tablename:** The entire table named `tablename` in `databasename`. You can use an asterisk (`*`) for either the database name or the table name to mean *all*. Using `*.*` revokes the permission on all tables in all databases.
- **accountname@hostname:** The account is identified by the `accountname` and `hostname` as a pair. If an account exists with the specified account name but a different hostname, the `REVOKE` query will fail, and you will receive an error message.

## Removing accounts

Removing an account is usually not necessary. If you created an account with permissions that you don’t want, just change the permissions. If you don’t want to use an account, remove all the permissions so that the account can’t do anything. To remove all the permissions for an account, use a `REVOKE` query with the following syntax:

```
REVOKE all ON *.* FROM accountname@hostname
```

To actually be able to remove an account, you need an account with the necessary permissions on the `mysql` database. You need to use a `DELETE` query on the user table in the `mysql` database. For more information on the structure of the `mysql` security database, see “The MySQL security database” sidebar, elsewhere in this chapter. Be careful using a `DELETE` query because with incorrect format, it can remove the wrong account or even all the accounts. See the discussion of the `DELETE` command at the end of Chapter 4.

## Backing Up Your Data

You need to have at least one copy of your valuable database. Disasters occur rarely, but they do occur. The computer where your database is stored can break down and lose your data, the computer file can become corrupted, the building can burn down, and so on. Backup copies of your database guard against data loss from such disasters.

You should have at least one backup copy of your database, stored in a location that is separate from the copy that is currently in use. More than one copy — perhaps as many as three — is usually a good idea.

- ✔ Store one copy in a handy location, perhaps even on the same computer, to quickly replace a working database that has been damaged.
- ✔ Store a second copy on another computer in case the computer breaks down, and the first backup copy isn't available.
- ✔ Store a third copy in a completely different physical location, for that remote chance that the building burns down. If the second backup copy is stored via network on a computer at another physical location, this third copy isn't needed.

![](img/d82df0828cfbc6d6be1e9a991861f3b7_124_0.png)

If you don't have access to a computer offsite where you can back up your database, you can copy your backup to a portable medium, such as a tape or a CD, and store it offsite. Certain companies will store your computer media at their location for a fee, or you can just put the media in your pocket and take it home.

If you use MySQL on someone else's computer, such as the computer of your employer or a Web hosting company, the people who provide your access are responsible for backups. They should have automated procedures in place that make backups of your database. A good question to ask when evaluating a Web hosting company is what its backup procedures are. You want to know how often backup copies are made and where they are stored. If you aren't confident that your data is safe, you can discuss changes or additions to the backup procedures.

If you are the MySQL administrator, you are responsible for making backups. MySQL provides a program called `mysqldump` that you can use to make backup copies; `mysqldump` creates a text file that contains all the SQL statements needed to re-create your entire database. The file contains the `CREATE` statements for each table and `INSERT` statements for each row of data in the tables. You can restore your database by executing the set of MySQL statements. You can restore it in its current location, or you can restore it on another computer if necessary.

Follow these steps to make a backup copy of your database in Linux/Unix/Mac:

1. **Change to the bin subdirectory in the directory where MySQL is installed.**

For instance, type **cd /usr/local/mysql/bin**.

2. **Type the following:**

```
mysqldump --user=accountname --password=password
databasename >path/backupfilename
```

where

- *accountname* is the name of the MySQL account that you're using to back up the database.
- *password* is the password for the account.
- *databasename* is the name of the database that you want to back up.
- *path/backupfilename* is the path to the directory where you want to store the backups and the name of the file that the SQL output will be stored in.

The account that you use needs to have select permission. If the account doesn't require a password, you can leave out the entire password option.

You can type the command on one line, without pressing Enter. Or you can type a backslash (\), press Enter, and then continue the command on another line.

For example, to back up the PetCatalog database, the command might be

```
mysqldump --user=root --password=bigsecret PetCatalog \ > /usr/local/mysql/backups/PetCatalogBackup
```

*Note:* The Linux/Unix account that you are logged into must have permission to write a file into the backup directory.

To make a backup copy of your database in Windows, follow these steps:

1. **Open a command prompt window.**

For instance, choose Start→Programs→MS-DOS prompt.

2. **Change to the bin subdirectory in the directory where MySQL is installed.**

For instance, type **cd c:\mysql\bin**.

![](img/d82df0828cfbc6d6be1e9a991861f3b7_125_0.png)
