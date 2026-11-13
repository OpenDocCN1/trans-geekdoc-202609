The PHP installer is built to configure both PHP and Apache to work together. This includes the editing of the configuration files of Apache.

On the Web Server Setup page, as shown in Figure 1.21, select the version of Apache that you previously installed. If you are unsure which version is installed, you can run the following command in the prompt:

```
/usr/local/apache2/bin/httpd -v
```

The following is a sample output from the previous command:

```
Server version: Apache/2.0.59
Server built:   Aug 31 2007 01:58:43
```

# FIGURE 1.21

# The PHP Installer Web Server Setup page

![](bbox=[0.12, 0.415, 0.59, 0.71])

The next page, see Figure 1.22, is where you inform the installer of the location of the Apache configuration directory. For example, if you followed the Apache installation guide at the beginning of this chapter, the path would be the following:

```
C:\\Program Files\\Apache Group\\Apache2\\conf\\
```

On the next page you choose the extra extensions needed for this book (see Figure 1.23). Those extensions are GD2, EXIF, MySQL, and PEAR. You can also choose to install any others that you think may be useful.