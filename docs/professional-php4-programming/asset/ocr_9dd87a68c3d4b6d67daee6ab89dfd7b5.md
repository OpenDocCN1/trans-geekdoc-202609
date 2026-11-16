```
session_register("currentFolder");
// Set the current Folder
if ($fold == ".") {
  // Do nothing
} else if ($fold == "..") {
  $pos = strrpos($currentFolder, "/");
  $currentFolder = substr($currentFolder, 0, $pos);
} else {
  $currentFolder = $currentFolder . "/" . $fold;
}
```

Make sure that the $currentFolder contains $username. This is done to prevent users from accessing folders belonging to other users:

```
// Current folder should always contain $username
if (!strstr(strtoupper($currentFolder), strtoupper($username)) ) {
  sendErrorPage("Error: Cannot access " . $currentFolder);
  exit;
}
```

Include main.php:

```
include_once("main.php");
?>
```

# Logging Off

The following PHP script implements the logout functionality:

```
<?php
include("common.php");
```

Check if the user is authenticated:

```
if (!isSessionAuthenticated()) {
  sendErrorpage("User session has expired. Please login again");
  exit;
}
```

Destroy the session:

```
session_destroy();
?>
<html>
<head>
<title> Online Storage Application </title>
</head>
<body>
<h1> Thanks <?php echo($username) ?> </i>
for using Online Storage Application </h1>
</body>
</html>
```