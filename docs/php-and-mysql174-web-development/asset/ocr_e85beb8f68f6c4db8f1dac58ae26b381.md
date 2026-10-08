# Opening a File

![](bbox=[0.151, 0.115, 0.626, 0.355])

# # Bob's Auto Parts

# Order Results

Order processed at 16:34, 14th September 2015

Your order is as follows

+   - Items ordered: 6
- 1 tires
- 2 bottles of oil
- 3 spark plugs
- Subtotal: $132.00
- Total including tax: $145.20

Address to ship is to 123 Main Street, Sometown 95128

Warning: fopen(/home/peter/test/orders.txt): failed to open stream: No such file or directory in /var/www/pmwd5e/chapter02/processor.php on line 67

Your order could be processed at this time. Please try again later.

Figure 2.2 PHP specifically runs when you a file can't be opened

If you receive this error, you need to make sure that the user whose script runs has permission to access the file you are trying to use. Depending on how your server is set up, the script might be running as the web server user or the owner of the directory where the script is located.

On most systems, the script runs as the web server user. If your script is on a Unix system in the /public_html/chapter02/ directory, for example, you could create a group-writable directory in which to store the order by typing the following:

```
mkdir path/to/orders
chgrp apache path/to/orders
chmod 775 path/to/orders
```

You could also change ownership of the file to the web server user. Some people will choose to make the file world-writable as a shortcut here, but keep in mind that directories and files that anybody can write to are dangerous. In particular, directories that are accessible directly from the Web should not be writable. For this reason, our orders directory is outside the document tree. We discuss security more in Chapter 15, "Building a Secure Web Application."

Incorrect permission setting is the most common thing that can go wrong when opening a file, but it's not the only thing. If common that you can't open the file, you really need to know so that you don't try to read data from or write data to it.