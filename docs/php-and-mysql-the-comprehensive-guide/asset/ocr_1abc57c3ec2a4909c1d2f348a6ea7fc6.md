As CGI: the Common Gateway Interface was one of the first approaches to enable server-side programming on web servers. In the early days, CGI was almost synonymous with Perl. PHP can be executed as a CGI module in virtually any web server. FastCGI (the fastcgi.com website is inactive, but there is an archived copy at https://fastcgi-archives.github.io) is an extension of CGI that offers better performance and has now become almost universally accepted. This is the preferred variant, especially under Windows.

![](bbox=[0.14, 0.24, 0.55, 0.45])

Figure 2.1 Integration of PHP into the Web Server Is Crucial

Both variants, SAPI and CGI, are supplied with PHP. You can obtain PHP from its official homepage, www.php.net. PHP is available as source code. Of course, this must first be compiled. This is quite common practice in Linux, but most Linux distributions also supply PHP as ready-made packages (such as RPM or DEB files). For Windows, there are also binaries—that is, compiled versions—which you can then install more conveniently.

> **Note**
> As even small changes to the version numbers usually contain security updates, you should update your test system regularly. However, the version number on your (own or rented) web server is decisive. Incidentally, with every version change, you should first look at the most important changes, the so-called changelog. Sometimes the behavior of a function changes, which you then have to adapt in your script, or a new security setting is added to the php.ini configuration file.

The automatic installers have also contributed to the spread of PHP. They are available for Windows as a package with Apache and MySQL or MariaDB; for Linux, RPM or DEB packages are available in various versions. Installers are very practical, which is why we will introduce some of them. However, there is no harm in doing the installation by hand. You have the advantage of being able to update PHP more easily and quickly.