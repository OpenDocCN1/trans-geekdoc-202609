```
$baseUrl = '/phpanth/WebPageElements/rewrite/';

// Create instance of PathVars
$pathVars = new PathVars($baseUrl);

// What's the first path variable?
switch ($pathVars->fetchByIndex(0)) {
case 'download':
  // Examine the second path variable
  if ($pathVars->fetchByIndex(1)) {
    echo 'Downloading file ' . $pathVars->fetchByIndex(1);
  } else {
    echo 'Download <a href="' . $baseUrl .
      'download/myStuff.zip">myStuff.zip</a><br />';
  }
  break;
case 'article':
  // Examine the second path variable
  if ($pathVars->fetchByIndex(1)) {
    echo 'Viewing article ' . $pathVars->fetchByIndex(1);
  } else {
    echo 'View <a href="' . $baseUrl .
      'article/123">Article 123</a><br />';
  }
  break;
default
  echo 'This is the home page<br />';
  echo '<a href="' . $baseUrl .
    'download/">Downloads</a><br />';
  echo '<a href="' . $baseUrl . 'article/">Articles</a><br />';
  break;
}
?>
```

In this code, I've used the PathVars class to allow index.php to handle most of
the requests on the site. Here are some of the URLs it might be asked to handle:

+   **http://www.example.com/phpanth/WebPageElements/rewrite/**
+   PathVars doesn't find any parameters in the URL suffix. The script will dis-
+   play the home page of the site.

+   **http://www.example.com/phpanth/WebPageElements/rewrite/download/myStuff.zip**
+   PathVars detects the parameters download and myStuff.zip in the URL
+   suffix. The script will send the specified file to the browser as a download.