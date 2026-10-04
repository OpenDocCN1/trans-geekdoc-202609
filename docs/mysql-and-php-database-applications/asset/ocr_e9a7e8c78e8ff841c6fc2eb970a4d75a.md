# Chapter 4: Getting Started with PHP — Variables 83

Sessions
PHP4, like ASP and ColdFusion, natively supports sessions, only it does a much better job. What's a session? Basically, it's another way of maintaining state between pages. Your script declares a session should start with the start session() function. At that point PHP registers a unique session ID, and usually that ID is sent to the user via a cookie. PHP creates a corresponding file on the server that can then keep track of any variables. The file has the same name as the session ID.

Once the session is started, you can register any number of variables. The values of these variables are kept in the file on the server. As long as the session lives, these variables will be available to any page within the same domain that wishes to access them. This is a much more convenient than setting variables from page to page through form elements or bloated cookies.

Of course, there is the possibility that some users will not allow cookies. For this reason, PHP allows you to track the Session ID through the querystring. You can do this manually by appending the Session ID onto the querystring, or by changing a configuration option.

To add the session ID to the querystring manually, use <?=SID?>. This automatically prints out like this:

```
PHPSESSID=07d696c4d787dc6c7b734fb485520
```

Adding to a link will pass the PHPSESSID variable via the querystring. Adding something like this:

```
<a href="mypage.php<?=SID?>">click to page</</a>
```

![](bbox=[0.181, 0.62375, 0.253, 0.68375])

<= is shorthand for echo. You can use it any time you like, not just with sessions.

If PHP is compiled with the -enable-trans-id option the session ID will automatically be added to every relative link. Basically, it is pretty simple. The following script will write a session variable $my_var, and will assign it a value of "hello world".

```
<<?nsession_start();
session_register("my_var");
$my_var = "hello world";
?>
```