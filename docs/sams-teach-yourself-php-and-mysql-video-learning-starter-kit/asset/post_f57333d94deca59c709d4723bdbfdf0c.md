
You can access shortcuts to these commands in the Start menu entries that the Apache installer created. If you installed Apache as a service, you can start or stop Apache by using the Windows service interface: In Control Panel, select Administrative Tasks and then click the Services icon.

## Apache Control Script

Although it is possible to control Apache on Linux/UNIX using the httpd binary, it is recommended that you use the apachectl tool. The apachectl support program wraps common functionality in an easy-to-use script. To use apachectl, type the following:

```
# /usr/local/apache2/bin/apachectl command
```

In this syntax, *command* can be stop, start, restart, or graceful. You can also edit the contents of the apachectl script to add extra command-line options. Some OS distributions provide you with additional scripts to control Apache; please check the documentation included with your distribution.

## Starting Apache for the First Time

Before you start Apache, you should verify that the minimal set of information is present in the Apache configuration file, `httpd.conf`. The following sections describe the basic information needed to configure Apache and to start the server.

## Check Your Configuration File

You can edit the Apache `httpd.conf` file with your favorite text editor. In Linux/UNIX and Mac OS X, this probably means `vi` or `emacs`. In Windows, you can use Notepad or WordPad. You must remember to save the configuration file in plain text, which is the only format Apache will understand.

There are only two parameters that you might need to change to enable you to start Apache for the first time: the name of the server and the address and port to which it is listening. The name of the server is the one Apache will use when it needs to refer to itself (for example, when redirecting requests). Apache can usually figure out its server name from the IP address of the machine, but this is not always the case. If the server does not have a valid DNS (domain name service) entry, you might need to specify one of the IP addresses of the machine. If the server is not connected to a network (you might want to test Apache on a standalone machine), you can use the value 127.0.0.1, which is the loopback address. The default port value is 80. You might need to change this value if a server is already running in the machine at port 80 or if you do not have administrator permissions—on Linux/UNIX and Mac OS X systems, only the root user can bind to privileged ports (those with port numbers lower than 1024).

You can change both the listening address and the port values with the Listen directive. The Listen directive takes either a port number or an IP address and a port, separated by a colon. If you specify only the port, Apache will listen on that port at all available IP addresses in the machine. If you provide an additional IP address, Apache will listen at only that address and port combination. For example, Listen 80 tells Apache to listen for requests at all IP addresses on port 80. Listen 10.0.0.1:443 tells Apache to listen at only 10.0.0.1 on port 443.

The ServerName directive enables you to define the name the server will report in any self-referencing URLs. The directive accepts a DNS name and an optional port, separated by a colon. Make sure that ServerName has a valid value. Otherwise, the server will not function properly; for example, it will issue incorrect redirects.

On Linux/UNIX and Mac OS X platforms, you can use the User and Group directives to specify which user and group IDs the server will run as. The nobody user is a good choice for most platforms. However, there are problems in the HP-UX platform with this user ID, so you must create and use a different user ID, such as www.

## Starting Apache

To start Apache on Linux/UNIX, change to the directory containing the apachectl script and execute the following command:

```
# /usr/local/apache2/bin/apachectl start
```

Mac OS X users can type the following at the prompt:

```
# /usr/sbin/httpd
```

To manually start Apache on Windows, click the Start Apache in Console link in the Control Apache Server section, within the Apache HTTP Server 2.2 program group in the Start menu. If you installed Apache as a service, you must start the Apache service instead.

If everything goes well, you can access Apache using a browser. A default installation page displays, such as the one shown in Figure 3.4. If you cannot start the web server or an error page appears instead, please consult the “Troubleshooting” section that follows. Make sure that you are accessing Apache in one of the ports specified in the Listen directive—usually port 80 or 8080.

![](img/be3c5789b9e58d6dc55dc804718f15b4_61_0.png)

FIGURE 3.4 Apache default installation page.

## Troubleshooting

The following subsections describe several common problems that you might encounter the first time you start Apache.

### Already an Existing Web Server

If a server is already running on the machine and is listening to the same IP address and port combination, Apache will not be able to start successfully. You will get an entry in the error log file indicating that Apache cannot bind to the port:

```
[crit] (48)Address already in use: make_sock: could not bind..[alert] no listening sockets available, shutting down
```

To solve this problem, you need to stop the running server or change the Apache configuration to listen on a different port.

### No Permission to Bind to Port

You will get an error if you do not have administrator permissions and you try to bind to a privileged port (between 0 and 1024):

```
[crit] (13)Permission denied: make_sock: could not bind to address 10.0.0.2:80 [alert] no listening sockets available, shutting down
```

To solve this problem, you must either log on as the administrator before starting Apache or change the port number (8080 is a commonly used nonprivileged port).

### Access Denied

You might not be able to start Apache if you do not have permission to read the configuration files or to write to the log files. You will get an error similar to the following:

```
(13)Permission denied: httpd: could not open error log file
```

This problem can arise if the user who built and installed Apache is different from the user trying to run it.

### Wrong Group Settings

You can configure Apache to run under a certain username and group. Apache has default values for the running server username and group. Sometimes the default value is not valid and you will get an error containing setgid: unable to set group id.

To solve this problem on Linux/UNIX and Mac OS X, you must change the value of the Group directive in the configuration file to a valid value. Check the /etc/groups file for existing groups.

## Installing and Configuring PHP

In this last of the three installation-related chapters, you will acquire, install, and configure PHP and make some basic changes to your Apache installation.

### Current and Future Versions of PHP

The installation instructions in this chapter refer to PHP version 5.2.5, which is the current version of the software.

> NOTE: If you are already using PHP 4.x.x in a production environment, or you want to stay with the 4.x.x development tree, please visit the Installation and Configuration section of the PHP Manual at http://www.php.net/install.
> 
> Because PHP 5 has been in use for more than three years and PHP 6 will likely become production-ready in 2009, the status of PHP 4 is officially “end of life”—this means the PHP Group has not made any updates to PHP 4 since December 31, 2007. For more information, visit: http://www.php.net/archive/2007.php#2007-07-13-1.
> 
> The code in this kit assumes the use of PHP 5 and not PHP 4; in some instances, the code is no different between the versions, but you should familiarize yourself with the difference between the two versions so that you can make the appropriate adjustments.
