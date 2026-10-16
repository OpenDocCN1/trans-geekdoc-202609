```
```text
command: --with-apxs=/usr/sbin/apxs or /usr/local/apache/bin/apxs. If you’re using Apache 2, the option is --with-apxs2=/usr/sbin/apxs.
```
```

+   10. **Type** make.

You will see many lines of output. Wait until it is finished. This might take a few minutes.

+   11. **Type** make install.

# # On Mac OS X

With the release of PHP 4.3, you can install PHP on Mac OS X as easily as on Unix/Linux. You install PHP by downloading source files, compiling the source files, and installing the compiled programs. This process isn’t as technical and daunting as it might appear. I provide step-by-step instructions in the next few sections. Read all the way through the steps before you begin the installation procedure to be sure that you understand it all clearly and have everything prepared so you don’t have to stop in the middle of the installation.

# ## Before installing

If you want to use PHP with Apache for your Web site, Apache must be installed. Most Mac OS X systems come with Apache already installed. For more information on Apache, see Appendix C.

Before beginning to install PHP, check the following:

+   - **The Apache version is recent:** See Appendix C for a discussion of Apache versions. To check the version, type the following on the command line:

```
```text
httpd -v
```
```

You might have to be in the directory where `httpd` is located before the command will work.

![](bbox=[0.121, 0.75, 0.21, 0.825])

As of this writing, PHP with Apache 2 is still considered experimental. For use on production Web sites, it might be better to use Apache 1.3 than Apache 2. See Appendix C for a discussion of Apache versions. Keep updated on the status of PHP with Apache 2 by checking the PHP Web site at `www.php.net/manual/en/install.apache2.php`.

+   - **The Apache module `mod_so` is installed.** It usually is. To display a list of all the modules, type the following:

```
```text
httpd -l
```
```