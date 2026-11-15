```
<html>
<head>
<title>Sessions</title>
</head>
<body>
<p>Programming language:

<?php
if (isset($_SESSION["Programming language"])) {
 echo htmlspecialchars($_SESSION["Programming language"]);
 }
?>
</p>
<p>Language version:

<?php
if (isset($_SESSION["Language version"])) {
 echo htmlspecialchars($_SESSION["Language version"]);
 }
?>
</p>
<p><a href="?php echo htmlspecialchars($_SERVER['PHP_SELF']); ?>">Reload</a></p>
</body>
</html>
```

# Listing 15.2 The Session Data Is Read Out ("read.php")

![](bbox=[0.145, 0.615, 0.83, 0.79])

# Figure 15.3 The Session Data in the Web Browser

If you take a closer look at the generated HTML code, you will notice that now, after the second call of a page with session support, the URL is no longer extended by the session ID if you have activated cookie support in your browser (see Figure 15.3). Otherwise, the