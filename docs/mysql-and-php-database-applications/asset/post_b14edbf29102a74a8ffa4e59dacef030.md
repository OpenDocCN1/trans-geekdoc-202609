
# Appendix I: MySQL Function Reference 581

## User

This function returns the current MySQL username. In MySQL 3.22.11 or later, this includes the client hostname as well as the username.

```
USER()
or
SYSTEM_USER()
or
SESSION_USER() (used in examples)
RETURNS: string
```

## VERSION

This function returns a string indicating the MySQL server version.

```
VERSION()
RETURNS: string
```

## PASSWORD

This function calculates a password string from the plaintext password str.

```
PASSWORD(str) (used in examples)
RETURNS: string
```

This is the function that encrypts MySQL passwords for storage in the Password column of the user grant table. PASSWORD() encryption is one-way. PASSWORD() does not perform password encryption in the same way Unix passwords are encrypted. You should not assume that if Unix password and your MySQL password are the same, PASSWORD() will result in the same encrypted value as is stored in the Unix password file. See ENCRYPT().

## ENCRYPT

This function encrypts str using the Unix crypt() system call.

```
ENCRYPT(str[.salt])
RETURNS: string
```

The salt argument should be a string with two characters. (As of MySQL 3.22.16, salt may be longer than two characters.) If crypt() is not available on your system, ENCRYPT() always returns NULL. ENCRYPT() ignores all but the first eight

## ENCODE

This function encrypts str using pass_str as the password.

```
ENCODE(str,pass_str)
RETURNS: binary string
```

To decrypt the result, use DECODE(). The result is a binary string. If you want to save it in a column, use a BLOB column type.

## DECODE

This function decrypts the encrypted string crypt_str using pass_str as the pass-word. crypt_str should be a string returned from ENCODE().

```
DECODE(crypt_str,pass_str)
RETURNS: string
```

## MD5

This function calculates an MD5 checksum for the string. The value is returned as a 32-character alpha-numeric string. This is the same as the md5() functions used by PHP.

```
MD5(string)
RETURNS: string
```

## LAST_INSERT_ID

This function returns the last automatically generated value that was inserted into an AUTO_INCREMENT column.

```
LAST_INSERT_ID()
RETURNS: int
```

## GET_LOCK

This function tries to obtain a lock with a name given by the string str, with a timeout of timeout seconds. Returns 1 if the lock was obtained successfully, 0 if the attempt timed out, or NULL if an error occurred (such as running out of memory or the thread being killed with mysqladmin kill). A lock is released RELEASE LOCK() is executed, a new GET_LOCK() is executed, or the thread terminates.

```
GET_LOCK(str,timeout)
RETURNS: int
```

## RELEASE_LOCK

This function releases the lock named by the string str that was obtained with GET_LOCK(). It returns 1 if the lock was released, 0 if the lock wasn't locked by this thread (in which case the lock is not released) and NULL if the named lock didn't exist.

```
RELEASE_LOCK(str)
RETURNS: int
```

## Functions for Use with GROUP BY Clauses

Most of the functions that are used with the GROUP BY class were covered in Chapter 3. There are two additional functions which we did not cover.

## STD/STDDEV

This function returns the standard deviation of expr. It is an extension of ANSI SQL. The STDDEV() form of this function is provided for Oracle compatibility.

```
STD(expr)
```

or

```
STDDEV(expr)
RETURNS: float
```

## BIT_OR

This function returns the bitwise OR of all bits in expr. The calculation is performed with 64-bit (BIGINT) precision.

```
BIT_OR(expr)
RETURNS: int
```

## BIT_AND

This function returns the bitwise AND of all bits in expr. The calculation is performed with 64-bit (BIGINT) precision.

```
BIT_AND(expr)
RETURNS: int
```

# Appendix J

## What’s on the CD-ROM

TO GET THE APPLICATIONS Sections III and IV working you first need to install Apache, PHP, and MySQL. You can find these applications on this book's CD-ROM in the /apache, /php, and /mysql directories. Each has subdirectories for Windows and Unix. Use whichever is appropriate. Then follow the instructions in Appendix B to install these applications.

Once Apache, PHP, and MySQL are installed, you will need to copy the PHP scripts that load the databases and run the applications. Copy the entire /book directory from the CD, with all of its subfolders, to the htdocs/ directory of your Apache installation.

The files that install the databases are kept in /directory. If Apache is running on your system, all you will need to install the databases is the correct URL in your browser: http://yourdomain/book/install/index.php. (If Apache is on your local machine, the actual URL will likely be http://localhost/book/install/index.php).

Follow the instructions to install the databases you wish to use. Note that for the install script, you will need to enter a valid hostname, username, and password in the mysql_connect() function on the fourth line of the install/index.php file. You can then access all of the applications by moving to http://yourdomain/book/index.html/

You should then open the book/functions/db.php file. In the first function, change the $user, $password, and $server arguments to reflect strings that are valid for your installation.

Also on the CD, you will find the following:

- A PDF version of this book.
- Adobe Acrobat Reader 4.0.
- PHPmyadmin—This excellent utility gives MySQL a graphical user interface via a Web browser using PHP scripts.
- Manual Lemos' Creation and Validation Class—This is a very complete set of scripts for creating and validating form input.
- Manual Lemos' Database Abstraction Layer—This can be helpful if you need to access more than one database from your PHP scripts.

# Part V: Appendices

- PHP Base Library — A set of scripts useful for user authentication and other common processes.
- Scripts from Appendix G.
- PBMPPlus—This utility for manipulating images is used in Chapter 10. It will only work on Unix systems.

Files with .php extensions can simply be copied to the Web directory and will execute when the page is accessed. Files with .tar.gz extensions are intended for Unix systems and must be uncompressed before you will be able to use them. Use the following commands:

```
gunzip filename.gz
tar x filename.gz
```

Files with .zip extensions must be uncompressed using a Windows zip utility such as WinZip (available at http://www.winzip.com).

# End-User License Agreement

READ THIS. You should carefully read these terms and conditions before opening the software packet(s) included with this book (“Book”). If you do not agree and do not want to be bound by such terms and conditions, promptly return the Book and the unopened software packet(s) to the place you obtained them for a full refund.

1. License Grant. IDGB grants you (either an individual or entity) license to use one copy of the enclosed program(s) (collectively, the “Software”) for your own personal or business purposes on a single computer (whether a standard computer or a workstation of a network). The Software is in use on a computer when it is loaded into temporary memory (RAM) or installed into permanent memory (hard disk, CD-ROM, or other storage device). IDGB reserves all rights not expressly granted.

2. Ownership. IDGB is the owner of all right, title, and interest, including copyright, and in the compilation of the Software recorded on the disk(s) or CD-ROM (“Software Media”). Copyright to the programs recorded on the Software Media is owned by the individual or other authorized copyright owner of each program. Ownership of the Software and all proprietary rights hereto remain with IDGB and its licenses.

3. Restrictions On Use and Transfer.
(a) You may (i) make one copy of the Software for backup or archival purposes, or (ii) transfer the Software to a single hard disk, provided that you keep the original for backup or archival purposes. You may not (i) rent or lease the Software, (ii) copy or reproduce the Software through a LAN or other network system or any computer subscriber system or bulletin-board system, or (iii) modify, adapt, or create derivative works based on the Software.
(b) You may not reverse engineer, decompile, or disassemble the Software. You may transfer the Software and user documentation on a permanent basis, provided that the transferee agrees to accept the terms and conditions of this Agreement and you retain no copies. If the Software is an update or has been updated, any transfer must include the most recent update and all prior versions.
