![](bbox=[0.142, 0.099, 0.858, 0.462])

Figure 38.1 The Composer Homepage

This procedure is also conceivable under Windows, but it is even easier: There is a Windows installer at https://getcomposer.org/Composer-Setup.exe that loads the latest version of Composer and automatically sets the PATH environment variable so that you can call composer directly from a command prompt. The installer checks some PHP settings, including whether the OpenSSL extension is installed, which is necessary for downloading data via HTTPS. If not, php.ini is automatically adjusted if required (see Figure 38.2). For a PHP installation in the delivery state, these are currently the following settings:

```
extension=openssl
extension=mbstring
```

During the installation, you will therefore also be asked to specify the location of the PHP installation to be used (important if there are several parallel versions on the system).

If you can run composer in a terminal after the installation, regardless of the operating system, then the global installation was successful (see Figure 38.3). If not, use the local variant. To do this, search for the composer.phar file and try the following call:

```
php composer.phar
```