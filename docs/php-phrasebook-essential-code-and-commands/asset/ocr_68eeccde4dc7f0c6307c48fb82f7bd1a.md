# Avoiding Security Traps
with File Access

One very important point: If you are using files with PHP, avoid retrieving the filename from external sources, such as user input or cookies. This might allow users to inject dangerous code in your website or force you to load files you did not want to open. Some so-called security experts had a self-programmed content management system that created uniform resource locators (URLs) like this: `index.php?page=subpage.html`. This just loaded the page `subpage.html` into some kind of page template and sent this to the browser. But what if the following URL is called: `index.php?page=../../../etc/passwd`? With some luck (or bad luck, depending on your point of view), the contents of the file `/etc/passwd` are printed out in the browser. This kind of attack—a so-called directory traversal attack—is quite common on the Web. However, you can avoid becoming a victim in several ways:

+   - If possible, do not use dynamic data in filenames.
+   - If you have to use dynamic data in filenames, use `basename()` to determine the actual name of the file, omitting the path information.
+   - Set the `php.ini` directive `open_basedir`. This expects a list of directories where PHP may access files. PHP checks the basedir rules whenever a file is opened, and refuses to do so if it isn't in the appropriate path.
+   - Set `include_path` to a directory you put all to-be-used files into and set the third parameter to `fopen()` to true, using the `include_path`.