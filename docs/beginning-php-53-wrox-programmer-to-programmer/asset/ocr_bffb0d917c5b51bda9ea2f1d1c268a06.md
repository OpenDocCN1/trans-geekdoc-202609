Thanks for using go-pear!

* WINDOWS ENVIRONMENT VARIABLES *
 convenience, a REG file is available under C:\wamp\bin\php\php5.2.6\PEAR-\nENV.reg
This file creates ENV variables for the current user.

Double-click this file to add it to the current user registry.
Press any key to continue

```
C:\wamp\bin\php\php5.2.6>
```

As instructed by the file's output, it's a good idea to open Windows Explorer and double-click the
PEAR_.reg registry file in the folder to set up various Windows environment variables. This will\make life easier when installing and using PEAR packages.

Now you can test your Windows PEAR installation by typing

```
pear
```

and pressing Enter. As with Ubuntu and Mac OS X, you should see a list of available commands appear
on the screen.

# Installing a Package

Now that you have set and verified PEAR, you can use the package manager to install a PEAR package.
Start by installing a simple package called Net_UserAgent_Detect; you can use this package to
identify the type and version of the browser used by each visitor to your Web site.

To install a package, run the package manager as described in the last few sections, adding the command
install on the command line, followed by the name of the package you want to install. For example,
on Ubuntu, just type:

```
pear install Net_UserAgent_Detect
```

Then press all goes well, the package manager should download and install the package,
displaying output similar to the following:

```
$ pear install Net_UserAgent_Detect
downloadinging Net_UserAgent_Detect-2.5.0.tgz ...
Starting to download Net_UserAgent_Detect-2.5.0.tgz (11,343 bytes)
.....done: 11,343 bytes
install ok: channel://pear.php.net/Net_UserAgent_Detect-2.5.0
$
```

446