
# Chapter 8: Guestbook 2000, the (Semi-)Bulletproof Guestbook 201

The pages that are called from the browser are named intuitively: view.php, sign.php, and edit.php. Each of these pages calls start_page.php and end_page.php. These contain standard header and footer information and are easy to read, so we will not discuss them here.

You may find the view.php, sign.php, and edit.php files surprisingly short. They only contain a couple of dozen lines of code each. This is because just about everything is written in reusable functions.

So once again the important thing is to understand the functions that are kept in /book/functions/basic.php and /book/guestbook2k/header.php.

## Code Breakdown

As mentioned in the previous section, the vast majority of the work is done in functions, and these functions are kept in files that will be included in the pages called from the browser.

## Reusable functions

We will cover the contents of function/basic.php and guestbook/header.php

### FROM FUNCTIONS/BASIC.PHP

We can address these in any order— alphabetical seems as good as any.

AUTHENTICATE() This little function sends a 401 HTTP response code. This header forces your browser to open the username and password box in Figure 8-9.

```php
function authenticate($realm="Secure Area")
{
    $errmsg="Please enter a username and password";
    Header("WWW-Authenticate: Basic realm=$realm");
    Header("HTTP/1.0 401 Unauthorized");
    die($errmsg);
}
```

The values entered into these text fields are set to PHP variables $PHP_AUTH_USER and $PHP_AUTH_PW. PHP can then query MySQL to check if the values are stored in the database. Note that this function merely sends the header. It does nothing to check the values entered in the text boxes. They are checked in the guestbook2k/authenticate.php file. This function is called if either no values have been entered or values match nothing in the database.

If the user hits the Cancel button the string stored in $errmsg is printed.

## 202 Part III: Simple Applications

![](img/245156cc770929860a3ede93c01f9981_232_0.png)

Figure 8-9: Results of a 401 unauthorized header

> This type of authentication is available only if PHP is installed as an Apache module. If you are using PHP as CGI, which is the only way to run it under Windows, this will not work. If you are doing some development work on Windows, go into the applications comment out the calls to authenticate() and create an entry for win_authenticate.php file.

CLEANUP_TEXT() This function goes a long way toward making sure we don't insert malicious text in our database.

```php
function cleanup_text($value = "", $preserve="", $allowed_tags="")
{
  if (empty($preserve))
  {
    $value = strip_tags($value, $allowed_tags);
  }
  $value = htmlspecialchars($value);
  return $value;
}
```

## Chapter 8: Guestbook 2000, the (Semi-)Bulletproof Guestbook 203

This accomplishes two things. First, it removes HTML tags. The `strip_tags()` function takes care of that. No need to worry about malicious script pictures here-unless you want them. You can indicate tags you want to keep with the second argument (allowed_tags). the second argument to strip_tags() could be a string like this: `<b><i></i>`.

Then `htmlspecialchars()` changes ampersands and double quotes to their proper entities (`&amp;` and `&quot;`). After being run through this little function, your query is to be rendered in the database.

SAFE_QUERY() This function will save you from pulling your hair out when you're trying to get your queries.

```php
function safe_query ($query = "") {
    if (empty($query)) { return FALSE; }
    $result = mysql_query($query)
    or die(".query failed: <error=".mysql_errno().".<error=".mysql_error().".<query=".$query);
    return $result;
}
```

Throughout the application, you will run your queries through this function. This way, if your query fails for some reason, you get a pretty good idea of what happened. This is another example of safe coding. After troubleshooting your code, you won't run into these problems often, but if a change is made somewhere (perhaps without your knowledge) you'll get a pretty good idea of what's going on.

![](img/245156cc770929860a3ede93c01f9981_233_0.png)

> For a site that is publicly available, there is a danger in running every query through this function. If a query fails, a hacker is likely to see more about your setup than you'd like. To prevent this from happening you could define a constant (discussed shortly) that prevents the function from printing out descriptive errors. Something like this:
```php
function safe_query ($query = "") {
    if (empty($query)) { return FALSE; }

    if(QUERY_DEBUG == "Off") {
        $result = mysql_query($query) or
```

## 204 Part III: Simple Applications

```php
die("Query failed: please contact the Webmaster");

else {
  $result = mysql_query($query)
  or die("<![query failed: <error=");
```

### FROM /GUESTBOOK2K/HEADER.PHP
Once again, this file will be included in every page in this application. It will keep all of the functions specific to this application. In addition, there are a few details that the first few lines of this application will see to to. Notice the use of the DOCUMENT_ROOT. This is an Apache variable, accessible through PHP, which indicates the default root folder. By making this variable, our entire application becomes portable. If we move the guest book folder and all of its sub-folders, files will be found and accessed properly. Keep in mind that this is an Apache variable; your operating system and Web server may require a different variable. Check phpinfo() to make sure.

```php
include($DOCUMENT_ROOT/book/functions/charset.php);
include($DOCUMENT_ROOT/book/functions/basic.php);
$conn = mysql_connect("localhost","username","password")
or die("could not connect to database");
mysql_select_db("guestbook2k",$conn);
die("could not select guestbook2k");
```

define("PAGE_LIMIT", 2);

The first line includes our default character set. The charset.php file contains one line.

```php
header("Content-Type: text/html; charset=ISO-8859-1");
```

## Chapter 8: Guestbook 2000, the (Semi-)Bulletproof Guestbook 205

This function will help prevent people from sending values encoded in a different character set. If they did send text in a different character set, the function in cleanup_text() would fail, and you would still be prone to some cross-site scripting hacks. This is a difficult problem. If you want more details check out these articles:

```
http://www.cert.org/tech_tips/malicious_code_mitigation.html
http://www.apache.org/info/css-security/encoding_examples.html
```

Here we've included something interesting: a constant, named PAGE_LIMIT. A constant is a variable in that it contains a value (in this instance, 2). However, value cannot be changed by a simple assignment or by functions other than define(). Constants do not run into the same problems that encountered with variables, so they can be used within functions without having to pass them as arguments. After running the define() function, the constant PAGE_LIMIT will the number of entries that will be viewable on each page. You are welcome to change this if you would like to see a larger number.

![](img/245156cc770929860a3ede93c01f9981_235_0.png)

If you are putting together a query using a constant, you will have to end your quoted string in order to make use of that constant. For example,
query = "select * from db_name limit PAGE_LIMIT"
will confuse because PHP has not replaced the name of the constant with its value. However, this will work:
query = "select * from db_name limit " PAGE_LIMIT

![](img/245156cc770929860a3ede93c01f9981_235_1.png)

PHP has many built-in constants you can use within your scripts. A list of constants is included in the PHP manual: http://www.php.net/manual/language.constants.php

PRINT_ENTRY() This prints the results of a query within a table.

```php
function print_entry($row,$preserve="") {
    $numargs = func_num_args();
    for ($i = 2; $i < $numargs; $i++) {
        $field = func_get_arg($i);
        $dbfield = str_replace("", "_", strtolower($field));
```
