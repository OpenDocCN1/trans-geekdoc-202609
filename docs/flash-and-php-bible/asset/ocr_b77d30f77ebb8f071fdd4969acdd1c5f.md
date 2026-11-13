# FIGURE 1.25

# PHP information displayed in a Web browser

![](bbox=[0.115, 0.176, 0.755, 0.556])

# Installing PHP for UNIX

Installing PHP for UNIX is more detailed and requires more configuration. This is true for most command-line installation setups. You can download the installer files from the book’s Web site or one the official PHP Web sites.

After you obtain the PHP installer files, you can begin the process of installation. Before you begin the installation, it is a good idea to stop Apache to ensure none of the files becomes corrupted.

```
/usr/local/apache/bin/apachectl stop
```

To start the installation, create the directory where PHP will be installed.

```
mkdir /usr/local/php5
```

You can substitute php5 for simply php. However, adding the version number makes it easier to have multiple installations and will be easier to manage in the future.

```
cd /usr/local/php5
```