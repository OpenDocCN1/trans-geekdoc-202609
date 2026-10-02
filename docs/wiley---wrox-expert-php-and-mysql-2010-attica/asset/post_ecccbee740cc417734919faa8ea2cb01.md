
| table_schema | num_tables |
|---|---|
| cacti | 49 |
| drizzle_stats | 6 |
| hipergate3 | 183 |
| information_schema | 17 |
| mediawiki | 38 |
| mysql | 17 |
| radius | 93 |
| remote | 1 |
| sugarcrm | 98 |
| test | 9 |
| wats | 14 |
| webapps | 17 |
| wordpress | 10 |

But how would you obtain the actual space used on disk for each schema? Some ways of doing this provide an approximate value using the information schema, but this number is not exact and has more to do with the space used in terms of what's being used internally as seen by MySQL. How could you obtain the actual value of disk space used by a database schema (which is a directory location in MySQL's data directory) in the same way you would see with a command such as du? This is where a UDF can be employed.

## UDF High-Level Design

The first thing you might want to do (at least to my way of thinking) is to come up with a simple C code snippet to obtain the value of a given directory. One family of standard C functions on UNIX for obtaining file information is the stat() family of functions. The manual page for fstat() gives information on what each of these functions provides and how they are used. Also, you will need functions and data types for working with directories and directory entries (the files and subdirectories contained within a directory). For this, you want to use the dirent.h system header file, which provides functions and data types for POSIX directory operations.

You will also want to gain an understanding of how MySQL stores data on disk. A schema in MySQL is organized as a directory within the data directory, known as the system variable datadir, which you can find out using the SQL statement:

```
mysql> show variables like 'datadir';
+-----------------+---------------+
| Variable_name   | Value         |
+-----------------+---------------+
| datadir         | /var/lib/mysql/ |
+-----------------+---------------+
```

In this MySQL instance, the value is /var/lib/mysql, which is most often the value of the datadir for installations of MySQL on various Linux platforms as configured by the operating system installation or package management tools. To see what is contained in these directories, simply view a given schema's directory within the data directory (you will need adequate permissions to view this directory). The following example views the directory for the schema test:

```
root@hanuman:/var/lib/mysql# ls -l test/
total 508
-rw-rw---- 1 mysql mysql  8586 2009-02-27 16:04 a1.frm
-rw-rw---- 1 mysql mysql    40 2009-02-27 16:12 a1.MYD
-rw-rw---- 1 mysql mysql  2048 2009-02-28 09:44 a1.MYI
-rw-rw---- 1 mysql mysql  8588 2009-07-14 10:28 a2.frm
-rw-rw---- 1 mysql mysql 98304 2009-07-14 10:28 a2.ibd
-rw-rw---- 1 mysql mysql  8602 2009-07-10 15:24 bench1.frm
-rw-rw---- 1 mysql mysql 98304 2009-07-10 15:24 bench1.ibd
-rw-rw---- 1 mysql mysql    65 2008-03-07 05:04 db.opt
-rw-rw---- 1 mysql mysql  8560 2009-01-26 17:20 schemalist.frm
-rw-rw---- 1 mysql mysql   184 2009-01-26 17:22 schemalist.MYD
-rw-rw---- 1 mysql mysql  1024 2009-01-29 18:16 schemalist.MYI
-rw-rw---- 1 mysql mysql  8556 2009-07-14 10:27 t3.frm
-rw-rw---- 1 mysql mysql 98304 2009-07-14 10:28 t3.ibd
-rw-rw---- 1 mysql mysql  8584 2008-08-15 07:12 test_table.frm
-rw-rw---- 1 mysql mysql     0 2008-08-15 07:12 test_table.MYD
-rw-rw---- 1 mysql mysql  1024 2008-08-15 07:12 test_table.MYI
-rw-rw---- 1 mysql mysql  8586 2009-07-14 10:19 users.frm
-rw-rw---- 1 mysql mysql 98304 2009-07-14 10:19 users.ibd
```

As you can see, there are two to three sets of files, each corresponding to a table name. This example contains several types of files:

- Files that end with .frm. These are table definition files, describing the table’s format. Every table in MySQL has a .frm file, regardless of the storage engine used.
- Both .MYD and .MYI files. These files are the table data and index files, respectively, for the MyISAM storage engine.
- Files ending with .ibd. These are tablespace files for the InnoDB storage engine — if the setting innodb_file_per_table is set to 1 (innodb_file_per_table = 1) in your my.cnf. This setting basically means that each table will have its own tablespace, containing both data and indexes. Having innodb_file_per_table set to 1 is a requirement for this UDF to properly give a summation of the byte count of all objects that comprise a schema. Otherwise, you would have a single InnoDB tablespace file for all tables in all schemas in your MySQL instance, and there would be no way to discern how many bytes a given schema uses.

You can see by using the following information schema that the tables listed correspond to the file types that you saw in the previous code:

```
mysql> SELECT TABLE_NAME, ENGINE FROM TABLES WHERE TABLE_SCHEMA='test';
+----------------+---------+
| TABLE_NAME     | ENGINE  |
+----------------+---------+
| a1             | MyISAM  |
| a2             | InnoDB  |
| bench1         | InnoDB  |
| schemalist     | MyISAM  |
| t3 | InnoDB |
| test_table | MyISAM |
| users | InnoDB |
+----------------+---------+
```

## Designing an Algorithm to Use for Your UDF

Now that you know what files you are examining, next you need to come up with a simple C program (if you don’t already have one) that you can use for the bulk of the UDF C function. This program will be a good refresher in C as well and allow you to iron out the logic of your program. You can also deal with any bugs you encounter and isolate them within a small program more easily than from within the MySQL server.

This program is a very simple program: given a directory path, it calculates the size of the files, recursively within the directory.

## Implementing the Program

The following code described here can be found within the code for Chapter 7, in particular the db_bytes sub-directory. The first file to be discussed is db_bytes/src/db_bytes.c.

To implement this program, follow these steps:

- 1. Include the necessary header files. The first header files are the standard files you might use in just about any C program:
- 2. Use an integer value for adding up the byte counts of each file. To ensure you have a large enough numeric value, unsigned (you won’t have a negative byte count!), you can use the type uint64_t, which requires including the stdint.h header file:
- 3. For printing out an error in the program, should the directory that you supply be unreadable — such as being nonexistent or not having the correct privileges — include the errno.h header file:
- 4. For reading the directory to obtain the directory entries (files and directories), as well as be able to call fstat() on the directory entry, and have access to the primitive system data types, the following header files are also included:

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
```

```
#include <stdint.h>
```

```
#include <errno.h>
```

```
#include <dirent.h>
#include <sys/stat.h>

#include <sys/types.h>
```

- 5. Determine the name of the function to do all the work of calculating the file sizes. For this example, the function is called db_bytes(). It takes one argument, a string, containing the value of the directory to be examined for total byte count. So you would then declare this function:

```
/* declare dir_byte_count */
uint64_t db_bytes(char *dir_str);
```

- 6. Next is the entry point to the program. This is C, so main() is the entry point. To make this program useful, you will want it to process a directory name, one string argument. You will also want main() to ensure the proper number of arguments, one, are passed, and if not, exit with an error.

```
/* main */
int main(int argc, char *argv[])
{
    uint64_t total;
    /* must have 1 argument (1st arg is prog name) */
    if (argc != 2)
    {
        printf("Error: you must supply a directory name!");
        exit(EXIT_FAILURE);
    }

    /* pass the directory */
    total= dir_byte_count(argv[1]);
    /* print total */
    fprintf(stderr, "total size of %s in bytes: %lu\n", argv[1], total);

    exit(EXIT_SUCCESS);
}
```

- 7. Define the function dir_byte_count(). This function takes as a single argument a string, which contains the directory name and recursively adds up the file sizes.

```
uint64_t dir_byte_count(char *dir_str)
{
    /*
        the variable containing the sum of file sizes
    */
    uint64_t total= 0;

    /* for return values from functions */
    uint64_t retval;

    /*
        pointer to the directory, when opened
    */
    DIR *pdir;

    /*
        pointer to current directory entry
```
