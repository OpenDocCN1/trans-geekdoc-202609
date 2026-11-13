incorrect domain (browsers typically do not accept cookies for domains that don’t match the requesting server host).

# **Someone throws in a bad parameter.**

Cookies, like anything else that the client sends you, are easily fabricated. Don’t trust their values; verify them just as you would any form data.

# **You're trying to store an array in a cookie variable.**

You can’t do that. You can, however, use a serialized array (see “#5: Turning an Array into a Nonarray Variable That Can Be Restored Later” on page 12).

# #57: Using Sessions to Temporarily Store Data

A fairly common user interface design has a user entering a fairly extensive amount of data over several forms. You also may want to store a set of data for as long as the user’s browser is open (for example, for a shopping cart). Though this is technically possible with hidden form fields, it’s not desirable in most cases because of its complexity and browser-state problems.

PHP has a built-in *session management* system that you can use to store and access data on a per-browser basis. It does most of the dirty work of setting cookies (or setting a session ID parameter) and storing the data somewhere on your server. All you need to do in your PHP scripts is start the session manager with the *session_start()* function and then access session data with the $_SESSION array.

Here’s a form that uses session management to capture, summarize, and edit data. Let’s start with a simple form script. The first part starts the session and extracts existing session data:

```
```
<?
session_start();

$name = $_SESSION["name"];
$color = $_SESSION["color"];
```
```

New users won’t have these variables set, but if they return to this form at any point, this part of the script captures their old values. When printing the form, we use those old values as defaults:

```
```
print '<form action="sessionview.php" method="post">';
print 'What is your name? ';
print '<input name="name" type="text" value="" . $name . " " /><br/>';
print 'What is your favorite color? ';
print '<input name="color" type="text" value="" . $color . " " /><br/>';
print '<input type="submit" />';
print '<input type="submit" name="clear" value="Clear Details" />';
?>
```
```