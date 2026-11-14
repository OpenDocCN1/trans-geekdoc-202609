> **note**
> 
> Figures 3.2 and 3.3 together show every file and folder that will be created over the next four chapters.

Figure 3.2 shows the server organization, where the **html** folder is the Web root directory (www.example.com points there).

If you can’t put anything below the Web root directory, which is common on shared hosts, you should use a structure like that shown in Figure 3.3.

> **note**
> 
> The **robots.txt** file shown in the figures won’t be formally developed in this book but is available for viewing in the downloadable code.

![](bbox=[0.31, 0.26, 0.74, 0.5])

![](bbox=[0.76, 0.21, 0.93, 0.5])

Figure 3.2

Figure 3.3

As a precaution, use the Web server’s tools to restrict access to the **includes** directory. Doing so will deny people access to it and the **pdfs** subfolder but won’t interfere with a PHP script’s ability to access its contents. Chapter 7 will discuss ways of doing this in detail.

# # FILE EXTENSIONS

When a user requests a page that uses a **.html** extension, the server will pass along the page’s contents directly to the browser without any additional server processing. But when the user requests a page with a **.php** extension, the server will first run the page’s content (that is, the code) through the PHP interpreter, which will then execute the code. (These are the standard settings; servers can be set up to treat extensions in other ways.) With this in mind, it’s important that the site’s primary pages — those that the user will directly access — use the **.php** extension in order for the code to be processed. Pages that are included by other PHP scripts and not run directly in the browser aren’t handled by

the server directly, so you have your choice of what extension to use.

I use the **.html** extension for files that are primarily HTML, such as the header and footer. For pages that are primarily PHP, but are intended as included files, I use a combination: **.inc.php**. The **.inc** part indicates that it’s a file to be included, but the **.php** prevents the code from being revealed should the file somehow be run directly in a Web browser. If you were to use just **.inc**, the server would probably not send the contents through the PHP interpreter, thereby sending potentially sensitive information to the browser. That’s a security risk that’s not worth taking.