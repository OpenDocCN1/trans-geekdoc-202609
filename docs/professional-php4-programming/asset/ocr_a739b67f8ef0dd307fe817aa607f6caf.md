```
list ($fileName, $mimeType) = split(":", $line);
if ($fileName == $file) {
    $contentType= $mimeType;
    break;
   }
}
```

Send the Content-Type HTTP header in the reply. The value of the Content-Type HTTP header is the mime type of the file that is sent:

```
if (isset($contentType)) {
    header("Content-Type: ".$contentType);
}
```

Get the absolute path of $file. The variable $file is passed from the main page:

```
$fileAbsPath = getAbsolutePath($currentFolder . "/." . $file);
```

Open the file. Here we are assuming that if the mime type of the file contains text, then the file contains text data, otherwise it contains binary data:

```
if (isset($contentType) & strstr($contentType, "text/")) {
    $fp = fopen($fileAbsPath, "r");
} else {
    $fp = fopen($fileAbsPath, "rb");
}
```

Send the file content to the client:

```
fpassthru($fp);
?>
```

# Viewing Folders

The following script viewFolder.php displays the contents of the current folder:

```
< ?php
include("common.php");
```

Check if the user is authenticated:

```
if (!isSessionAuthenticated()) {
    sendErrorpage("User session has expired!!. Please login again");
    exit;
}
```

Set the session currentFolder folder; the PHP script main.php displays the contents of the folder specified by the session variable $currentFolder: