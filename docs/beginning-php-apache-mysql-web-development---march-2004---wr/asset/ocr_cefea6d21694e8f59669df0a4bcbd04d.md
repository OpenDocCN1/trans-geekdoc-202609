# Chapter 2

You make each of these settings as follows:

```
setcookie('cookiename', 'value', 'expiration time', 'path', 'domain',\n
  secure connection);
```

As you know now, those values will be referenced in the script as $_COOKIE['cookiename'].

# Try It Out Setting a Cookie

Let's have the Web site set cookie on Joe's machine so that (theoretically) doesn't have to type his username (Joe1235) every time he comes back to. To do this, follow these steps:

+   1. Modify moviel.php file as shown:

```
<php
setcookie('username', 'Joe', time(+60));
session_start();
//delete this line: $_SESSION['username']=Joel12345';
$_SESSION['auther']=1;
?>
<HTML>
<HEAD>
<TITLE>Find my Favorite Movie!</TITLE>
</HEAD>
<body>
<?php
$myfavmovie=urlencode('Life of Brian');
echo "*<a href=\"http://localhost/moviesite.php?favmovie=$myfavmovie\**";
echo "*click here to see information about my favorite movie!*"";
echo "*</a>*";
?>
<BODY>
</HTML>
```

+   2. Save the file.

+   3. Make the changes to your moviesite.php file:

```
<php
session_start();
//check to see if user has logged in with a valid password
if ($_SESSION['auther']!=1) {
echo "*Sorry, but you don't have permission to view this\npage, you loser!";
exit();
}
?>
<HTML>
<HEAD>
<TITLE>My Movie Site - <?php echo $_REQUEST['favmovie'] ?>></TITLE>
</HEAD>
<body>
```