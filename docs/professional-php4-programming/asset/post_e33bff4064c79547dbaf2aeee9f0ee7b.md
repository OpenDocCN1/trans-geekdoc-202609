
Once you have opened the directory, you can read its contents with the `readdir()` function. The `readdir()` function returns the name of the next entry in the directory. If there are no more entries in the directory, or if the directory handle is invalid, then the function returns false.

Apart from files and sub-folders, each directory contains two special entries "." and "..". The "." entry refers to the current directory and ".." refers to the parent directory.

The current directory can be opened by opening ".":

```
$dir = opendir(".")
```

Once you have read the contents of the directory, you should close it and free all the resources associated with it:

```
void closedir($dir)
```

The following code deletes files which were not accessed in the last ten days from the temp/ directory:

```
<html>
<head></head>
<body>
<?php
function cleanTemporaryFiles($directory)
{
    $dir = opendir($directory);
    while (($file = readdir($dir))) {
        if (is_file($directory . "/" . $file)) {
            $accessTime = fileatime($directory . "/" . $file);
            $time = time();
            if (($time - $accessTime) > 10*24*60*60) {
                if (unlink($directory . "/" . $file)) {
                    printf("File %s is removed from %s directory <br>\n",
                        $file, $directory);
                }
            }
        } else if (is_dir($directory . "/" . $file) &&
            ($file != ".") && ($file != "..")) {
            cleanTemporaryFiles($directory . "/" . $file);
        }
    }
    closedir($dir);
}
cleanTemporaryFiles("c:/temp");
?>
</body>
</html>
```

## Adding and Deleting Directories

```
int mkdir(string directoryname, int mode)
```

The mkdir() function can be used to create a new directory. The argument directoryname is the path name for the directory to be created. The argument mode specifies the access permissions for a UNIX directory. On Windows this argument is ignored. The mode entry is specified as an octet string and should always start with a zero character. The function returns true on success, false on failure.

The following code creates a new directory C:\temp\test:

```
<?php
if (mkdir("c:/temp/test", "0700")) {
    printf("New directory created");
} else {
    printf("Couldn't create directory");
}
?>
```

```
int rmdir(string dirname)
```

The rmdir() function can be used to delete a directory. This function returns true on success, false on failure. Note that the rmdir() function will fail if the directory is not empty.

The following function deletes a non-empty directory:

```
<?php
function removeDirectory($directory)
{
    $dir = opendir($directory);
    while (($file = readdir($dir))) {
        if (is_file($directory . "/" . $file)) {
            unlink($directory . "/" . $file);
        } else if (is_dir($directory . "/" . $file) &&
            ($file != ".") && ($file != "..")) {
            removeDirectory($directory . "/" . $file);
        }
    }
    closedir($dir);
    rmdir($directory);
    printf("Directory %s removed", $directory);
}
?>
```

The file entry "." and ".." point to the current and the parent directory respectively. This removeDirectory() method should not be called with these as arguments, that is, if you do not explicitly skip "." and ".." you could end up losing all your data!

## Uploading Files from Clients

There are two mechanisms that can be used by browsers for uploading files to the server:

- Based on the HTTP PUT method
- Based on the HTTP POST method

The HTTP protocol provides three basic methods GET, PUT, and POST for accessing information from the web server.

The GET method is used to fetch web pages. When GET is used to fetch dynamic pages, the form variables are passed as part of the URL. It is safe for the browser to fetch a page using the GET method as many times it likes – the GET method should not cause any permanent change on the server. Some web servers have a limit on the length of the URL (mostly 1024) that they can handle, so GET should not be used to pass form data greater than this limit.

The PUT method is used for updating information on the server. It requests that the enclosed data be stored as the requested URL on the server. The PUT method is used mostly for publishing pages.

The POST method is used if requesting the URL will cause a permanent change on the server. For example, deleting a folder in a web based e-mail application. The browser should not execute the POST method again without getting user confirmation. The POST method sends all the form variables as part of the request body. The POST method is also used when lots of form data needs to be passed to the URL.

### Uploading Files with PUT

A typical HTTP PUT request looks like this:

```
PUT /path/filename.html HTTP/1.1
```

In this case the client would like the web server to store the contents of the request as the specified URL (/path/filename.html) in the web server's URL namespace. The web server, by default, would not handle such a request. Rather it specifies a script to handle such requests. Web site specific policies for uploading files can be implemented in the specified script.

For example, in Apache this can be done with the script directive (stored in httpd.conf). The following script directive means that you want the cgi script put.cgi to handle HTTP PUT requests:

```
Script PUT /cgi-bin/put.cgi
```

PHP provides support for writing PUT handlers. When PHP gets a PUT request, it stores the contents of the request in a temporary file, which is deleted after the request is processed. The temporary file name is stored in the $PHP_PUT_FILENAME variable, and the URL name is stored in $REQUEST_URI.

This simple PHP script, for handling PUT requests, copies the uploaded file to the specified URL location in the web server's URL name space:

```
<?php copy($PHP_PUT_FILENAME, $DOCUMENT_ROOT.$REQUEST_URI); ?>
```

The PUT mechanism for uploading files is non-functional in the current implementations of PHP. You could monitor the status of this bug at http://www.php.net/bugs.php?id=10383.

### Uploading Files with POST

HTML form elements allow users to enter the name of the file that will be submitted to the web server. This feature is implemented by recent versions of both Netscape and Microsoft browsers. A simple HTML form (uploadfile.html) for submitting the file looks like this:

```
<html>
<head>
<title> A Simple Form for Uploading a File </title>
</head>
<body>
<h2> A simple form for uploading a file </h2>
```

The enctype attribute of the form element is set to multipart/form-data – this is required for file uploads to work. The enctype attribute specifies the encoding that should be used by the browser to encode the form parameters. The default value of enctype attribute is application/x-www-form-urlencoded:

```
<form action="upload.php" method="post" enctype="multipart/form-data">
```

The input element should be of type file:

```
Enter file name: <Input type="file" name="userfile"><br>
<input type="submit"><br>
</form>
</body>
</html>
```

This page will appear in the browser as:

![](img/9cf7789dba9b16ef3f8576d5aea89186_280_0.png)

On receiving an HTTP request with input elements of type file, PHP stores the contents of the uploaded file in a temporary file. The temporary file is created in the server's default temporary directory, unless another directory is specified by the upload_tmp_dir directive in the php.ini file. The server's default temporary directory can be changed by setting the environment variable TMPDIR. The temporary file is deleted at the end of the request, so the PHP script handling the request should copy the file if the file data is to be preserved for later use.

The details of the uploaded file are accessible to PHP scripts through a two-dimensional global array HTTP_POST_FILES. Supposing that the name of the input element (of type file) is userfile, then:

- The variable $HTTP_POST_FILES['userfile']['name'] contains the original name of the file on the client machine
- The variable $HTTP_POST_FILES['userfile']['type'] contains the mime type of the file
- The variable $HTTP_POST_FILES['userfile']['size'] contains the size, in bytes, of the uploaded file
- $HTTP_POST_FILES['userfile']['tmp_name'] contains the temporary filename of the file in which the uploaded file was stored on the server

Below is a PHP script, upload.php, which copies the uploaded file to the temp/ directory:

```
<html>
<head>
<title>Upload File Example</title>
</head>
<body>
<?php
