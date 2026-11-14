
Before installing Apache, you'll probably want to make sure that you are not currently running a web server (for instance, a previous version of Apache, Microsoft Internet Information Services, or Microsoft Personal Web Server) on your machine. You might want to uninstall or otherwise disable existing servers. You can run several web servers, but they must run in different address and port combinations.

Before downloading the installer, take a moment—a very important moment—and look for a statement on the downloads page (found at http://httpd.apache.org/download.cgi) that says “If you are downloading the Win32 distribution, please read these important notes.”The direct URL to these notes is http://www.apache.org/dist/httpd/binaries/win32/README.html.

The Apache Software Foundation maintains this page for the benefit of Windows users who want to run a version of the Apache server. On this page, there are notes for nearly every flavor of Windows still in use, and it is in your best interest to read the information presented. I guarantee that if you are running Apache as either a production or development server, you find relevant information on the notes page.

When you're ready to begin the installation, look for the link labeled Win32 Binary (MSI Installer). After you download the installer, double-click the file to start the installation process. You will get a welcome screen, as shown in Figure 3.1.

![](img/be3c5789b9e58d6dc55dc804718f15b4_48_0.png)

FIGURE 3.1 The Windows installer welcome screen.

Click Next to continue the installation process and you will be prompted to accept the Apache license. Basically the license says that you can do whatever you want with the software—including making proprietary modifications—except claim that you wrote it, but be sure to read the license so that you fully understand the terms.

After you accept the license, the installer presents you with a brief introduction to Apache. Following that, it asks you to provide basic information about your computer, as shown in Figure 3.2. This includes the full network address for the server (for instance, mycomputer.mydomain.com) and the administrator's email address. The server name is the name your clients will use to access your server, and the administrator email address is added to error messages so that visitors know how to contact you when something goes wrong.

NOTE: If your machine does not have a full network address, use localhost or 127.0.0.1 as the server name.

Also on this screen, you are prompted to select which installation shortcuts should be installed—those for starting Apache as a service or those for starting Apache manually. Installing Apache as a service causes it to run every time Windows starts, and you can control it through the standard Windows service administration tools. Installing Apache for the current user requires you to start Apache manually and set the default port on which Apache listens to requests to 8080 (instead of 80). Select the appropriate radio button and click Next to continue.

The next screen enables you to choose the type of installation: typical or custom. A typical installation means that Apache binaries and documentation are installed, but headers and libraries are not. This is the best option to choose unless you plan to compile your own modules.

![](img/be3c5789b9e58d6dc55dc804718f15b4_50_0.png)

FIGURE 3.2 The basic information screen.

A custom installation enables you to choose whether to install header files or documentation. After selecting the target installation directory, which defaults to c:\Program Files\Apache Group, the program proceeds with the installation process. If everything goes well, it will present you with the final screen shown in Figure 3.3.

![](img/be3c5789b9e58d6dc55dc804718f15b4_50_1.png)

FIGURE 3.3 The successful installation screen.

In the next section, you'll learn about the Apache configuration file and eventually start up your new server.

## Apache Configuration File Structure

Apache keeps all its configuration information in text files. The main file is `httpd.conf`. This file contains directives and containers that enable you to customize your Apache installation. `Directives` configure specific settings of Apache, such as authorization, performance, and network parameters. `Containers` specify the context to which those settings refer. For example, authorization configuration can refer to the server as a whole, to a directory, or to a single file.

## Directives

The following rules apply for Apache directive syntax:

- The directive arguments follow the directive name.
- The directive arguments are separated by spaces.
- The number and type of arguments vary from directive to directive; some have no arguments.
- A directive occupies a single line, but you can continue it on a different line by ending the previous line with a backslash character (`\`).
- The pound sign (#) should precede the directive, and must appear on its own line.

The Apache server documentation offers a quick reference for directives at http://httpd.apache.org/docs/2.2/mod/quickreference.html. You'll soon learn about some of the basic directives, but you should supplement your knowledge using the online documentation.

The Apache documentation for directives typically follows this model:

- **Description**—This entry provides a brief description of the directive.
- **Syntax**—This entry explains the format of the directive options. Compulsory parameters appear in italics, optional parameters appear in italics and brackets.
- **Default**—If the directive has a default value, it will appear here.
- Context—This entry details the containers or sections in which the directive can appear. The next section explains containers. The possible values are server config, virtual host, directory, and .htaccess.
- Override—Apache directives belong to different categories. The Override field specifies which directive categories can appear in .htaccess per-directory configuration files.
- Status—This entry indicates whether the directive is built in Apache (core), belongs to one of the bundled modules (base or extension, depending on whether they are compiled by default), is part of a multi-processing module (MPM), or is bundled with Apache but not ready for use in a production server (experimental).
- Module—This entry indicates the module to which the directive belongs.
- Compatibility—This entry contains information about which versions of Apache support the directive.

Further explanation of the directive follows these entries in the documentation, and a reference to related directives or documentation might appear at the end.

## Containers

Directive containers, also called sections, limit the scope for which directives apply. If directives are not inside a container, they belong to the default server scope (server config) and apply to the server as a whole.

These are the default Apache directive containers:

- <VirtualHost>—A VirtualHost directive specifies a virtual server. Apache enables you to host different websites with a single Apache installation. Directives inside this container apply to a particular website. This directive accepts a domain name or IP address and an optional port as arguments.
- <Directory>, <DirectoryMatch>—These containers allow directives to apply to a certain directory or group of directories in the file system. Directory containers take a directory or directory pattern argument. Enclosed directives apply to the specified directories and their subdirectories. The DirectoryMatch container allows regular expression patterns to be specified as an argument. For example, the following allows a match of all second-level subdirectories of the www directory and made up of four numbers, such as a directory named after a year and month (0906 for September 2006):
<DirectoryMatch "^/www.*/[0-9]{4}">

- <Location>, <LocationMatch>—These containers allow directives to apply to certain requested URLs or URL patterns. They are similar to their Directory counterparts. LocationMatch takes a regular expression as an argument. For example, the following matches directories containing either "/my/data" or "/your/data":
<LocationMatch "^/(my|your)/data">

- <Files>, <FilesMatch>—Similar to the Directory and Location containers, Files sections allow directives to apply to certain files or file patterns.

Containers surround directives, as shown in Listing 3.1.

```
LISTING 3.1 Sample Container Directives
1: <Directory "/some/directory">
2:   SomeDirective1
3:   SomeDirective2
4: </Directory>
5: <Location "/downloads/*.html">
6:   SomeDirective3
7: </Location>
8: <Files "\.(gif|jpg)">
9:   SomeDirective4
10: </Files>
```

Sample directives SomeDirective1 and SomeDirective2 apply to the directory /some/directory and its subdirectories. SomeDirective3 applies to URLs referring to pages with the .html extension under the /downloads/ URL. SomeDirective4 will apply to all files with .gif or .jpg extensions.

## Conditional Evaluation

Apache provides support for conditional containers. Directives enclosed in these containers will be processed only if certain conditions are met.
