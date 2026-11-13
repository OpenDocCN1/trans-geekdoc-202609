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

# Compiling and Installing PHP

You can download the latest version of PHP from www.php.net/downloads.php . At the time of this writing, the latest version is 5.0.3, so the file to download is called php-5.0.3.tar.bz2 . If a later version is available, you should be sure to substitute the appropriate version number wherever it appears in a filename.