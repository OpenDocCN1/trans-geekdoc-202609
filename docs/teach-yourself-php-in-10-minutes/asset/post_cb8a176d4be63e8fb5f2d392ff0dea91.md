
appropriate. For instance, to change the base installation directory, you should use the --prefix switch, followed by the desired location. You can enter configure --help to see a list of the possible configure switches.

You need to include at least the --enable-module=so switch to ensure that DSO support is available for loading the PHP module later on. You should enter the following command, adding any other configuration switches that you need to include:

```
# ./configure --enable-module=so
```

The configure command produces several screens full of output as it tries to detect the best compilation settings for your system. When it is done, you are returned to a shell prompt and can continue the installation.

To begin compiling, you issue the make command:

```
# make
```

Again, a lot of output is produced, and the time required for compilation depends on the speed of your system. When the build is done, you see the following line and are returned to a shell prompt:

```
make[1]: Leaving directory `/usr/local/src/httpd-2.0.52'
```

The final step is to install the newly built software. To do this, you simply enter make install , and the files are automatically copied to their correct system locations:

```
# make install
```

You issue the apachectl start command to start the Apache web server and enter your server's IP address in a web browser to test that the installation is successful. You use the following command if you have not changed the default installation location:

```
# /usr/local/apache/bin/apachectl start
```

## Compiling and Installing PHP

You can download the latest version of PHP from www.php.net/downloads.php . At the time of this writing, the latest version is 5.0.3, so the file to download is called php-5.0.3.tar.bz2 . If a later version is available, you should be sure to substitute the appropriate version number wherever it appears in a filename. You need to save this file to your filesystem in `/usr/local/src` or some other place where you keep source code. You uncompress the archive by using bunzip2 , as follows:

```
# bunzip2 php-5.0.3.tar.bz2
```

**Uncompressing** If your system does not include the bunzip2 utility, you should download the file called httpd-2.0.52.tar.gz instead. This archive is slightly larger but is compressed using gzip , which is more widely available.

When the file has been uncompressed, it loses the .bz2 file extension. Extract this uncompressed archive file by using tar :

```
# tar xvf php-5.0.3.tar
```

Files are extracted to a directory called php-5.0.3 . You should change to this new directory before continuing:

```
# cd php-5.0.3
```

Next, you should issue the configure command with any configuration switches that are appropriate. For example, to include database support through the MySQLi extension, you would use the --with-mysqli switch, followed by the path to the mysql_config utility. To see the full list of configure switches, you can run configure --help .

You need to include either the --with-apxs or --with-apxs2 switch; the latter is for Apache 2.0, followed by the location of the apxs utility on your system. You would use one of the following statements with a default Apache installation:

```
# ./configure --with-apxs2=/usr/local/apache2/bin/apxs
```

```
# ./configure --with-apxs2=/usr/local/apache/bin/apxs
```

The configure command produces several screens full of output as it tries to detect the best compilation settings for your system. When it is done, you are returned to a shell prompt and can continue the installation.

To begin compiling, you issue the make command:

```
# make
```

Again, a lot of output is produced, and the time required for compilation depends on the speed of your system. When the build is done, you see the following text and are returned to a shell prompt:

Build complete.
(It is safe to ignore warnings about tempnam and tmpnam).

The final step is to install the newly built PHP module into your web server. To do this, you enter make install , and the files are automatically copied to their correct system locations:

```
# make install
```

To complete the installation, you need to make a change to the web server configuration file to tell it that .php files should be passed to the PHP module. You should edit the httpd.conf file to add the following line:

```
AddType application/x-httpd-php .php
```

You can include other file extensions besides .php if you want.

When you next restart your web server by using the apachectl restart command, the PHP extension will be loaded. To test PHP, you can create a simple script, /usr/local/apache2/htdocs/index.php , that looks like this:

```
<?php
phpinfo();
?>
```

In your web browser, you can visit index.php on the IP address of your web server, and you should see a page that gives lots of information about the PHP configuration.

## Windows Installation

The instructions in this section take you through installing PHP into an Apache web server on a Windows system.

### Installing Apache

If you already have an Apache web server installed on your system, you can skip this section.

Download the latest version of Apache from httpd.apache.org . The file to get is the MSI Installer package, named apache_2.0.52-win32-x86-no_ssl.msi for the current Apache 2.0.52 release. Save this file to your desktop and double-click to begin the installation process.

The installation process is done through a wizard and is mostly self-explanatory. You must accept the license terms to continue with the installation, after which you are shown some release notes. Click Next after you have read these, and you are asked to enter your server information.

Enter your server's domain name and hostname and your email address. If you are installing on a personal workstation, you should use localhost and localdomain for your server information. You should leave the recommended option to install Apache on port 80 selected.

When asked to choose a setup type, you should select the typical setup. Then you are given the opportunity to select the destination folder for the Apache files. By default, this is C:\Program Files\Apache Group . Finally, Apache is ready to install, and clicking the Install button causes your system to start copying and setting up files on your system.

When the installation is complete, the Apache server and monitor program start up, and you see a new icon in your system tray. You can double-click this icon to bring up the Apache Service Monitor, which you can use to start and stop the web server process. A green light indicates a running server.

### Installing PHP

You can download the latest version of PHP from the Windows Binaries section of www.php.net/downloads.php . You should choose the zip file rather than the installer package; it is named php-5.0.3-Win32.zip for the latest version of PHP, which is 5.0.3 at this writing. If a later version is available, be sure to substitute the appropriate version number wherever it appears in a filename.

You need to save the zip file to your desktop and double-click it to extract it to C:\php . You can choose another location, as long as you also change the other instructions in this section to reflect it.

Next, you need to add the PHP module to Apache. Using the file explorer, you need to open the Apache configuration directory (if you used the default location, it should be C:\Program Files\Apache Group\Apache2\conf ) and edit httpd.conf . Then you need to add the following lines to the end of the file:

```
LoadModule php5_module c:/php/php5apache2.dll
AddType application/x-httpd-php .php
```

When you next restart your web server from the Apache monitor, the PHP extension will be loaded. To test PHP, you can create in the htdocs folder under your Apache installation location a simple script that looks like this:

```
<?php
phpinfo();
?>
```

In your web browser, if you visit http://localhost/index.php, you should see a page that gives lots of information on the PHP configuration.
