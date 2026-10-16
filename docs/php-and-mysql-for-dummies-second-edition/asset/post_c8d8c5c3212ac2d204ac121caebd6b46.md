
The existing database in which you want to build all the tables. Use the entire path and filename for the backup file. For instance, a command to restore the PetCatalog database might be

```
mysql -u root -p PetCatalog < c:\mysql\bak\PetCatalog.bak
```

The tables might take a short time to restore. Wait for the command to finish. If a problem occurs, an error message is displayed. If no problems occur, you see no output. When the command is finished, the prompt appears.

To restore only selected tables from the backup file, make a file that contains only the queries for the selected tables that you want to restore. Then follow Steps 1-3 in the preceding list. In Step 3, type the path name or filename for the file with the subset of queries that you want instead of the full backup file.

If the database is not there at all, you need to create it before you can use the queries in the backup file to rebuild all the tables. To restore the database when nothing exists, use the following steps:

1. Add the following two lines to the top of the backup file:

    ```sql
    CREATE DATABASE databasename;
    use databasename;
    ```

    where *databasename* is the name of the database that you want to restore. For instance, the commands for the PetCatalog database are

    ```sql
    CREATE DATABASE PetCatalog;
    use PetCatalog;
    ```

    **Note:** Make sure that you add a semicolon (;) at the end of each line.

2. Change to the bin subdirectory in the directory where MySQL is installed.

    **On Linux/Unix/Mac:**  
    Type a `cd` command to change to the correct directory (for instance, type `cd /usr/local/mysql/bin`).

    **On Windows:**  
    a. Open a command prompt window.  
    For instance, choose Start→Programs→Accessories→Command Prompt.  
    b. Type a `cd` command to change to the correct directory (for instance, type `cd c:\mysql\bin`).

3. Type the command that sends the SQL queries in the backup file.

    **On Linux/Unix/Mac:**

    Type this:

    ```
    mysql -u accountname -p < path/backupfilename
    ```

    where *accountname* is an account that has create permission. If the account doesn’t require a password, leave out the -p. If you use the -p, you will be asked for the password. Use the entire path and filename for the backup file. For instance, a command to restore the database might be

    ```
    mysql -u root -p < /usr/backupfiles/PetCatalog.bak
    ```

    **On Windows:**

    Type this:

    ```
    mysql -u accountname -p < path\backupfilename
    ```

    where *accountname* is an account that has create permission. If the account doesn’t require a password, leave out the -p. If you use the -p, you will be asked for the password. Use the entire path and filename for the backup file. For instance, a command to restore the PetCatalog database might be

    ```
    mysql -u root -p < c:\mysql\bak\PetCatalog.bak
    ```

The tables might take a short time to restore. Wait for the command to finish. If a problem occurs, an error message is displayed. If no problems occur, you see no output. When the command is finished, the prompt appears.

Your database is now restored with all the data that was in it at the time the copy was made. If the data has changed since the copy was made, the changes are lost. For instance, if more data was added after the backup copy was made, the new data is not restored. If you know the changes that were made, you can make them manually in the restored database.

## Part III: PHP

### The 5th Wave

By Rich Tennant

![](img/d82df0828cfbc6d6be1e9a991861f3b7_133_0.png)

> "Your database is beyond repair, but before I tell you our backup recommendation, let me ask you a question. How many index cards do you think will fit on the walls of your computer room?"

### In this part . . .

In this part, you find out how to use PHP for your Web database application. Here are some of the topics described:

- ✔ How to add PHP to HTML files
- ✔ What features PHP has that are useful for building a Web database application
- ✔ How to use the PHP features
- ✔ How to use forms to collect information from users
- ✔ How to show information from a database in a Web page
- ✔ How to store data in a database
- ✔ How to move information from one Web page to the next

You find out everything you need to know to write the PHP programs you need.

## Chapter 6: General PHP

### In This Chapter

- Adding PHP sections to HTML files
- Writing PHP statements
- Using PHP variables
- Comparing values in PHP variables
- Documenting your programs

Programs are the application part of your Web database application. Programs perform the tasks. They create and display Web pages, accept and process information from users, store information in the database, get information out of the database, and perform any other necessary tasks.

PHP, the language that you use to write your programs, is a scripting language designed specifically for use on the Web. It is your tool for creating dynamic Web pages. It has features designed to aid you in programming the tasks needed by dynamic Web applications.

In this chapter, I describe the general rules for writing PHP programs — the rules that apply to all PHP statements. Consider these rules similar to general grammar and punctuation rules. In the remaining chapters in Part III, you find out about specific PHP statements and features and how to write PHP programs to perform specific tasks.

### Adding a PHP Section to an HTML Page

PHP is a partner to HTML (HyperText Markup Language) that extends its abilities. It enables an HTML program to do things it can’t do on its own. For example, HTML programs can display Web pages, and HTML has features that allow you to format those Web pages. HTML also allows you to display graphics in your Web pages and to play music files. But HTML alone does not allow you to interact with the person viewing the Web page.

![](img/d82df0828cfbc6d6be1e9a991861f3b7_136_0.png)

### How the Web server processes PHP files

When a browser is pointed to a regular HTML file with an .html or .htm extension, the Web server sends the file, as-is, to the browser. The browser processes the file and displays the Web page that is described by the HTML tags in the file. When a browser is pointed to a PHP file (with a .php extension), the Web server looks for PHP sections in the file and processes them instead of just sending them as-is to the browser. The steps that the Web server uses to process a PHP file are as follows:

1. The Web server starts scanning the file in HTML mode. It assumes that the statements are HTML and sends them to the browser without any processing.
2. The Web server continues in HTML mode until it encounters a PHP opening tag (`<?php`).
3. When it encounters a PHP opening tag, the Web server switches into PHP mode. This is sometimes called escaping from HTML. The Web server then assumes that all statements are PHP statements and executes the PHP statements. If there is output, the output is sent by the server to the browser.
4. The Web server continues in PHP mode until it encounters a PHP closing tag (`?>`).
5. When the Web server encounters a PHP closing tag, it returns to HTML mode. It resumes scanning, and the cycle continues from Step 1.

HTML is almost interactive. That is, HTML forms allow users to type information that the Web page is designed to collect; however, you can’t access that information without using a language other than HTML. PHP processes form information, without requiring a separate program, and allows other interactive tasks as well.

HTML tags are used to make PHP language statements part of HTML programs. The program file is named with a .php extension. Other extension(s) can be defined by the PHP administrator, such as .phtml, .php4, or .php5, but .php is the most common. So for this book, I will assume that .php is the extension for PHP programs. The PHP language statements are enclosed in PHP tags with the following form:

```
<?php ?>
```

![](img/d82df0828cfbc6d6be1e9a991861f3b7_136_1.png)

Sometimes you can use a shorter version of the PHP tags. You can try using `<?` and `?>` without the php. If short tags are enabled, you can save a little typing.
