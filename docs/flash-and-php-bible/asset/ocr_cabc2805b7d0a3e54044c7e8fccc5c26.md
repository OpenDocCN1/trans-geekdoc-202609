# # Gathering information about Apache

As you continue to work with Apache, there are some commands and tools that can result in more time to develop an application instead of micromanaging the server.

# ## Starting and stopping Apache

Sometimes Apache can act up just like any other piece of software or hardware on your system. Oftentimes when this occurs, a simple restart will fix the issue. For instance, as more users request files from Apache, it can start to fill up internal memory and temporary files.

To restart Apache you can simply call the following command in UNIX from the command line or restart the service on Windows:

```
```
$ /usr/local/apache/bin/apachectl restart
```
```

> > NOTE The path to the apachectl application can vary depending on the installation of Apache.

If you want to stop Apache and not have it restart, use the following command. This would most likely be done when installing new modules or updating Apache itself.

```
```
$ /usr/local/apache/bin/apachectl stop
```
```

To start the server again after you complete the update, simply use the start option:

```
```
$ /usr/local/apache/bin/apachectl start
```
```

# ## Determining the version of Apache

Occasionally, when installing new software, you need to know which version of Apache you are currently running. For example, when installing PHP you need to know which version of Apache you are using. This is found by running a simple command switch.

```
```
$ /usr/local/apache/bin/httpd -V
```
```

The result of that command would be something similar to Figure 2.1.

# ## Determining which modules are installed in Apache

You can very easily determine which modules are currently installed in Apache by using the following command-line flags in UNIX.

```
```
$ /usr/local/apache/bin/apachectl -t -D DUMP_MODULES
```
```

To determine the modules in Windows, you would run the following command:

```
```
httpd -t -D DUMP_MODULES
```
```