# Configuring Apache

When Apache starts, it reads information from a configuration file. If Apache can't read the configuration file, it can't start. Unless you tell Apache to use a different configuration file, it looks for the file `conf/httpd.conf` in the directory where Apache is installed.

# Changing settings

Apache behaves according to commands, called *directives*, in the configuration file. You can change some of Apache's behavior by editing the configuration file and restarting Apache so that it reads the new directives.

The configuration file is a text file containing commands called directives. Apache behaves according to the directives in this file. In most cases, the default settings allow Apache to start and run on your system. However, you may need to change the settings in some cases. Some reasons you might want to change the settings are

+   - **Installing PHP:** If you install PHP, you need to configure Apache to recognize PHP programs. How to change the Apache configuration for PHP is described in Appendix B.
+   - **Changing your Web space:** Apache looks for Web page files in a specific directory and its subdirectories, often called your Web space. You can change the location of your Web space.
+   - **Changing the port where Apache listens:** By default, Apache listens for file requests on port 80. You can configure Apache to listen on a different port.

To change any settings, edit the file `httpd.conf`. On Windows, you can access this file through the menu at Start→Programs→Apache HTTPD Server→Configure Apache Server→Edit the Apache httpd.conf File. When you click this menu item, the `httpd.conf` file is opened in Notepad.

The `httpd.conf` file has comments (beginning with `/#`) that describe the directives, but you should be sure you understand their function before changing any. All directives are documented on the Apache Web site.

When adding or change file path/names, use forward slashes, even when the directory is on Windows. Apache can figure it out. Also, path/names don't need to be in quotes unless they include special characters. A colon (:) is a special character; the underscore (_) and hyphen (-) are not. For instance, to indicate a Windows directory, you would use something like the following:

```
"c:/temp/mydir"
```