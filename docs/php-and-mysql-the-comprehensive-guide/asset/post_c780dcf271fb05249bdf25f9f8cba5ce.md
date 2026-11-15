
```
Command Prompt - php
C:\php-8.2.2\php go-pear.phar
PHP Warning:  Private methods cannot be final as they are never overridden by other classes in C:\php-8.2.2\go-pear.phar
on line 339
Warning: Private methods cannot be final as they are never overridden by other classes in C:\php-8.2.2\go-pear.phar on line 339
Are you installing a system-wide PEAR or a local copy?
(system/local) [system] :
Below is a suggested file layout for your new PEAR installation. To
change individual locations, type the number in front of the
directory. Type 'all' to change all of them at once simply press Enter to
accept these locations.
1. Installation base ($prefix)    : C:\php-8.2.2
2. Temporary directory for processing   : C:\php-8.2.2\tmp
3. Temporary directory for downloads    : C:\php-8.2.2\tmp
4. Binaries directory   : C:\php-8.2.2
5. PHP code directory ($php_dir)    : C:\php-8.2.2\pear
6. Documentation directory  : C:\php-8.2.2\docs
7. Data directory   : C:\php-8.2.2\data
8. User-modifiable configuration files directory  : C:\php-8.2.2\cfg
9. Public Web Files directory   : C:\php-8.2.2\www
10. System manual pages directory   : C:\php-8.2.2\man
11. Tests directory : C:\php-8.2.2\tests
12. Name of configuration file  : C:\WINDOWS\pear.ini
13. Path to CLI php.exe : C:\php

1-13, 'all' or Enter to continue :
```

### Figure 2.27 Installing PEAR via the Console (Warnings Included)

You must change the PATH Windows environment variable yourself if you want the pear
command in the command prompt to be available outside the PHP directory—for
example, C:\php (see Figure 2.28).

```
Command Prompt
Press Enter to continue:
** WARNING! Old version found at C:\php-8.2.2, please remove it or be sure to use the new C:\php-8.2.2\pear.bat command
The 'pear' command is now at your service at C:\php-8.2.2\pear.bat
** The 'pear' command is not currently in your PATH, so you need to
** use 'C:\php-8.2.2\pear.bat' until you have added
** 'C:\php-8.2.2' to your PATH environment variable.
Run it without parameters to see the available actions, try 'pear list'
to see what packages are installed, or 'pear help' for help.
For more information about PEAR, see:
http://pear.php.net/faq.php
http://pear.php.net/manual/
Thanks for using go-pear!
* WINDOWS ENVIRONMENT VARIABLES *
For convenience, a REG file is available under C:\php-8.2.2\PEAR_ENV.reg .
This file creates ENV variables for the current user.
Double-click this file to add it to the current user registry.
C:\php-8.2.2>
```

### Figure 2.28 The Installation Is Successfully Completed

To install new packages, use the pear command in the command prompt/console.
Enter the command without options to see all possible entries. If you want to try it out right away, simply install a package. To do this, go to the command prompt and then to the PHP directory—for example, C:\php. Then enter the following line:

```
pear install XML_SVG
```

This installs the XML_SVG PEAR package (see Figure 2.29).

![](img/ae7820c36e8f24c1623d26668b28e80e_75_0.png)

### Figure 2.29 The Installation Goes Smoothly

The PEAR command is quite powerful. Simply type it into the command prompt without any additions. You will then receive a list of all the options. We would like to briefly introduce some of them here:

- The PEAR installation uses so-called channels via which the content is delivered. Use `pear channel-update pear.php.net` to retrieve the current PEAR channel after installation. Via the channels, other libraries can also use the PEAR installer.

- If you want to install a PEAR package that does not yet have the status *Final*, you can specify the status as a switch. The most common switches are `-alpha` and `-beta`.

- With the `--alldeps` switch (see Figure 2.30), you can download all dependent packages. `onlyreqdeps` only downloads necessary packages:

```
pear install --alldeps HTML_CSS
```

![](img/ae7820c36e8f24c1623d26668b28e80e_75_1.png)

### Figure 2.30 Dependent Packages Are Also Installed, with Some Warnings for (Still) Not Stable or Outdated Packages

- You can also use the PEAR commands to update existing packages and search for specific packages. Simply enter `pear` in the command prompt, followed by `upgrade package name`. To search, use `pear search` and then the search term.

These explanations are intended in particular to provide a general understanding and explain why PEAR is mentioned in the Linux installation, for example. However, PEAR is not necessary for the other content in this book (there is a small exception in Chapter 32).

> **Note**
> There was once a second incarnation of PEAR, called PEAR2. This relied on a new PEAR installer called Pyrus. However, work on this has now been completely discontinued, and the homepage has been shut down.

## 2.2.2 PEAR Packages without Installation

The PEAR packages are PHP files and therefore do not necessarily require installation. You can also place the corresponding packages directly in a directory on the web server and simply include them with `require_once "path/package"`. The necessary steps can be found in the PEAR manual (http://s-prs.co/v602209).

> **Note**
> At http://s-prs.co/v602209, you will find tricks for installing PEAR at the host via Telnet/SSH or FTP. However, the setup sometimes does not work depending on the security settings of the host.

You should now have a functioning PHP system available. If not, take a look at the next chapter, Chapter 3, where you will find information on how to detect errors. And even if your system is currently running smoothly, you will find useful tips here just in case.

## Chapter 3

## Testing and Help

*In theory, everything always works as we imagine. In practice, however, it doesn't always work as in theory. That's why we show you common error messages in this chapter — and what you can do about them.*

You already know the most famous PHP test: phpinfo(). In this chapter, we have collected information that will also help you with the installation and operation of PHP. Section 3.1 collects some problems we have encountered in trainings, in projects, and in our daily work, while Section 3.2 tells you where you can find help on the internet. The focus here is on problems directly after installation: What could have gone wrong, and which steps may have been forgotten?

> **Note**
> Chapter 35 reveals how to find errors in the programming itself.

### 3.1 Common Errors

A list of common errors is never comprehensive, especially in the context of an installation. So if your error message or problem is not listed here, take a look at Section 3.2 or search the internet. However, we hope to be able to intercept some common problems here.

#### 3.1.1 The Page Cannot Be Displayed

Figure 3.1 shows a typical error message: some browsers are particularly "clever" and do not want to frighten their users with too many technical details. For certain types of errors, the browser displays the message shown here—for example, if the server cannot be found, the network cable is not plugged in, an error has occurred on the page, or you're under a full moon. To make a long story short: the error message is anything but informative.¹

¹ Bear this in mind when you send us a question. Unfortunately, we can't tell you anything with "The page cannot be displayed."

![](img/ae7820c36e8f24c1623d26668b28e80e_78_0.png)

Figure 3.1 The Page Cannot Be Displayed

The Chrome browser team in particular refuses to disable these "pretty" messages (see discussion at https://bugs.chromium.org/p/chromium/issues/detail?id=1695). When in doubt, it helps to look at the HTTP response (header and content) via the browser tools (press F12). Figure 3.2 shows this using the Chrome browser.

![](img/ae7820c36e8f24c1623d26668b28e80e_78_1.png)

Figure 3.2 The "Pretty" Error Message Is Less Useful than the Details in the Browser Console

#### 3.1.2 The Website Was Not Found—File Not Found

One of the classic error messages, HTTP status 404, means that the requested file has not been found (see Figure 3.3). Have you possibly made a typing error in the URL? Even
