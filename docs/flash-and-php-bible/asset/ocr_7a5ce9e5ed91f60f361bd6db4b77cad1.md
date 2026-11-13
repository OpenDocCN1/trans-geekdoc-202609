To restart the Apache server, use this command:

```
$ usr/local/apache/bin/apachectl restart
```

Testing out the server is done by making a call to localhost from your web browser at http://localhost/.

As you can now see, the installation was a success. To further test and better understand how to modify the files Apache serves, create a new HMTL file and save it in the Apache Web root.

Using your favorite text editor, which in UNIX will most likely be vi, create this new HTML file. The following commands assume you are using vi.

Create a new file:

```
$ vi /usr/local/apache/htdocs/sampleFile.html
```

In order to begin entering the HTML code, you need to tell vi to enter Insert mode, which is done by pressing I. Press ESC to exit Insert mode.

Paste or type the following sample HTML code:

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en">
<head>
<title>My Custom Page</title>
<body>
<h1>Welcome to my custom page</h1>
<p>This is a test of the customization of Apache!</p>
<p>Pretty cool huh?</p>
</body>
</html>
```

Once the file is created, press ESC and type the following command to save and close the editor. Note, the : is part of the command.

```
:wq
```

Certain files you add or modify require you to restart Apache; however, basic Web files do not fall into that category. You can now display the new page by appending the filename to the local-host call at http://localhost/sampleFile.html.

As you can see, the Apache server has been properly installed and you were able to add a custom file that Apache properly served up. At this point, you should have a basic understanding of how Apache functions. The next section (platform independent) goes into more detail about how you can modify Apache.