If you find PHP files, PHP is already installed, and you might not need to re-install it. For instance, even if you installed MySQL yourself after the PHP was installed, you might have installed it in the location where PHP is expecting it. Better safe than sorry, however: Perform the testing that I describe in the next section to see whether MySQL and PHP are working correctly together.

If you don’t find any PHP files, PHP is not installed. In order to install PHP, you need access to the Web server for your site. For instance, when you install PHP with Apache, you need to edit the Apache configuration file. All the information and software that you need is provided on the PHP Web site (`www.php.net`). I provide detailed installation instructions in Appendix B.

# # Testing, Testing, 1, 2, 3

Suppose you believe that PHP and MySQL are available for you to use, for one of the following reasons:

+   - The IT department at your company or your client company gave you all the information that you asked for and told you that you’re good to go.
+   - The Web hosting company gave you all the information that you need and told you that you’re good to go.
+   - You followed all the instructions and installed PHP and MySQL yourself.

Now you need to test to make sure that PHP and MySQL are working correctly.

# ## Testing PHP

To test whether PHP is installed and working, follow these steps:

+   1. **Find the directory in which your PHP programs need to be saved.**
+   
+      This directory and the subdirectories under it are your *Web space*. Apache calls this directory the *Document Root*. The default Web space for Apache is `htdocs` in the directory where Apache is installed. For IIS, it’s `Inetpub\wwwroot`. In Linux, it might be `/var/www/html`. The Web space can be set to a different directory by configuring the Web server (see Appendix C). If you’re using a Web hosting company, the staff will supply the directory name.