
Each time the page is loaded, the old values are displayed and the new values set. Notice that if you surf to other websites and then come back, these values are remembered, but if you close your web browser and come back, the values are reset.

### Using Session Variables

One of the advantages of session variables over cookies is their ability to use PHP's data types. Cookie values are always simple text values, but a session variable can take any value that a regular PHP variable can.

For instance, to store a list of items in a cookie, you would have to create an array and pass it to `serialize` to store. By using a session variable, you can create an array directly and store that data structure in the session.

The example in **Listing 14.2** uses an array stored in the session to retain a list of values entered through a form. This is a fairly trivial example, but it demonstrates the flexibility you have when using session variables.

### Listing 14.2. Using Arrays as Session Variables

```php
<?php

session_start();

if (isset($_POST["word"]))
    $_SESSION["words"][] = $_POST["word"];

if (is_array($_SESSION["words"])) {
    foreach($_SESSION["words"] as $word) {
        echo $word . "<br>";
    }
}

?>
<FORM ACTION="list.php" METHOD=POST>
Enter a word: <INPUT SIZE="10" NAME="word">
<INPUT TYPE=SUBMIT VALUE="Add word to list">
</FORM>
```

## Summary

In this lesson you have learned how to set cookies from PHP and how to use PHP's session management to store values within a browser session. In the next lesson you will use these techniques to create a user authentication system using PHP.

## Lesson 15. User Authentication

In this lesson you will build a user authentication process that can be used to protect certain pages of your website by using a password.

### Types of Authentication

Chances are you have needed to log in to a website in the past, so you should be aware of how the process of authentication works from a user's point of view. Generally speaking, you are asked to enter a username—sometimes your email address—and a password.

There are actually two ways that a website can authenticate a user, though: using basic HTTP authentication and using session-based authentication. The following sections clarify the differences between these two methods.

#### Basic HTTP Authentication

Basic HTTP authentication can be performed by web server, without having anything to do with PHP script. The example in this section assumes that you are using Apache web server; for other web servers, you should refer to your documentation.

Authentication is usually done on a per-directory basis but can be set up to apply to individual files if required. By using an .htaccess file on your website, you can specify for that directory a custom configuration that instructs the web server to require a login before proceeding. A typical set of configuration directives would look like this:

```
AuthType Basic
AuthName "Protected Website"
AuthUserFile /home/yourname/htpasswd
require valid-user
```

AuthUserFile points to the location of a password file that is created by using the htpasswd program. To create a new password file, you would run a command like the following:

```
$ htpasswd c /home/yourname/htpasswd chris
New password:
Re-type new password:
```

> **Password Files** You should use the c switch only when you want to create a new file. The htpasswd program does not ask whether you want to overwrite an existing file. Running htpasswd without the c option on an existing password file adds a user.

You have to enter the new password twice, after which an entry is added to the password file given. The entry consists of the username and an encrypted version of the password, separated with a colon character. However, you should never need to work with this file directly. A typical password file entry might look like this:

```
chris:XNiv7qSUTFPU6
damon:ZxxE2PTExEVNU
shelley:SVzAEtXmMLEAls
vanessa:cX/t1Pv2oQfrY
```

When you try to access a file in the protected directory, your web browser pops up a window that asks for a username and password, and the page requested loads only after you have entered the correct information.

The `require valid-user` directive instructs the web server to show the page to any authenticated user. You might want to grant access to only certain users, which you can do with the `require user` directive:

```
require user chris damon shelley
```

Basic HTTP authentication also allows you to set up user groups to give access to particular sections of the site only to certain users. You can then use the `require group` directive to specify access to one or more user groups.

The following groups file, usually named `htgroups`, divides the users in the password file into two groups:

```
boys: chris damon
girls: shelley vanessa
```

To give access only to the boys group, you could use the following `.htaccess` file:

```
AuthType Basic
AuthName "Boys Only"
AuthUserFile /home/yourname/htpasswd
AuthGroupFile /home/yourname/htgroup
require group boys
```

Although it is fairly easy to set up and reasonably flexible, basic HTTP authentication has some drawbacks. First, you cannot change the look and feel of the pop-up login box. If you want to customize the process at all, you cannot use this method. Furthermore, the password file is stored on the server's filesystem, and updating it from a script may be problematic; you will learn more about these issues when dealing with reading and writing to files in Lesson 17, "Filesystem Access."

**Apache Add-ons** Several third-party modules for the Apache web servers such as `mod_auth_mysql` and `mod_auth_sqlite` allow you to use basic HTTP authentication with password information stored in a database. Check with your web host to see whether these modules are installed.

#### Session-Based Authentication

To provide a completely customizable login process for your website, you must implement it yourself, and doing so in PHP requires using session variables.

In a nutshell, once a user is logged in, the browser's session contains enough information to convince the scripts on the website that you are allowed to view a page. Users log in by using a form on your site where they enter their username and password. You can set up the layout and flow of the login process any way you see fit.

One fairly significant difference from basic HTTP authentication is that the instruction to check the validity of a user's session appears in the script itself, not in a per-directory configuration file.

**Protecting HTML** If your website includes plain HTML files that contain no PHP, you need to add PHP code to them to prevent them from being viewable to an anonymous user. You also need to change their file extension to `.php`.

### Building an Authentication System

The rest of this lesson walks you through building an authentication mechanism using PHP sessions.

#### How the System Works

There are two main components of the authentication system you're going to build now. First, you need a login processor that checks the validity of the username and password entered in the form. You also need a piece of code that can be put at the top of each script to check the session and make sure the user is authenticated before continuing.

> **Login Forms** You need to make sure you always use the POST method for login forms. Submitting a username and password by using the GET method causes these values to appear in the URL of the next page for anyone to see!

You should split off the session-checking code into an include file, auth.inc, so that it is simple to protect a page by simply putting the following statement at the top of the script:

```
include "auth.inc";
```

You can use a single session variable to store the username of the logged-in user. If the variable contains a username, that user is logged in; logging a user out is as simple as deleting this session variable. As long as nobody else shares the domain on which your website is hosted and could create a conflicting session, this is adequately secure. Knowing this, auth.inc can really be as simple as the following:

```
session_start();
if (!isset($_SESSION["auth_username"])) {
    echo "You must be logged in to view this page";
    exit;
}
```

Here you simply display a message and exit the script if the user is not logged in. You will see later on how you can improve this for usability, but you need to create the login process itself first.
