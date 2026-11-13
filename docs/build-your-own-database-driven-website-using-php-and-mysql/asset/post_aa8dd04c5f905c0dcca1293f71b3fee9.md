
Just like your Web server, MySQL is a program that should be run in the background so that it may respond to requests for information at any time.
The server program may be found in the "bin" subfolder of the folder into which you installed MySQL. To make things complicated, however, there are actually several versions of the MySQL server to choose from:

- **mysqld.exe** This is the basic version of MySQL if you run Windows 95, 98, or ME. It includes support for all advanced features, and includes debug code to provide additional information in the case of a crash (if your system is set up to debug programs). As a result of this code, however, the server might run a little slow, and I've generally found that MySQL is so stable that crashes aren't really a concern.

- **mysqld-opt.exe** This version of the server lacks a few of the advanced features of the basic server, and does not include the debug code. It's optimized to run quickly on today's processors. For beginners, the advanced features are not a big concern. You certainly won't be using them while you complete the tasks in this book. This is the version of choice for beginners running Windows 95, 98, or ME.

- **mysqld-nt.exe** This version of the server is compiled and optimized like `mysqld-opt`, but is designed to run under Windows NT/2000/XP as a service. If you're using any of those operating systems, this is probably the server for you.

- **mysqld-max.exe** This version is like `mysqld-opt`, but contains advanced features that support transactions.

- **mysqld-max-nt.exe** This version's similar to `mysqld-nt`, but has advanced features that support transactions.

All these versions were installed for you in the `bin` directory. If you're running on Win98/ME I recommend sticking with `mysqld-opt` for now - move to `mysqld-max` if you ever need the advanced features. On Windows NT/2000/XP, `mysqld-nt` is my recommendation. Upgrade to `mysqld-max-nt` when you need more advanced features.

Starting MySQL is also a little different under WinNT/2000/XP, but this time let's start with the procedure for Win95/98/ME. Open an MS-DOS Command Prompt and proceed to the MySQL `bin` directory, and run your chosen server program:

```
C:\mysql\bin> mysqld-opt
```

Don't be surprised when you receive another command prompt. This command launches the server program so that it runs in the background, even after you close the command prompt. If you press Ctrl-Alt-Del to pull up the task list, you should see the MySQL server listed as one of the tasks that's active on your system.

To ensure that the server is started whenever Windows starts, you might want to create a shortcut to the program and put it in your Startup folder. This is just like creating a shortcut to any other program on your system.

On WinNT/2000/XP, you must install MySQL as a system service. Fortunately, this is very easy to do. Simply open a Command Prompt and run your chosen server program with the `-install` option:

```
C:\mysql\bin> mysqld-nt --install
```

This will install MySQL as a service that will be started the next time you reboot Windows. To manually start MySQL without having to reboot, just type this command (which can be run from any directory):

```
C:\> net start mysql
```

To verify that the MySQL server is running properly, press Ctrl-Alt-Del and open the Task List. If all is well, the server program should be listed on the Processes tab.

## Installing PHP

The next step is to install PHP. At the time of this writing, PHP 4.x has become well-established as the version of choice; however, some old servers still use PHP 3.x (usually because nobody has bothered to update it). I'll cover the installation of PHP4 here, so be aware that if you're still working with PHP3 there may be some minor differences.

Download PHP for free from http://www.php.net/ (or one of its mirrors listed at http://www.php.net/mirrors.php). You'll want the Win32 Binaries package, and be sure to grab the version that includes both the CGI binary and the server API versions if you have a choice.

In addition to PHP itself, you will need a Web server such as Internet Information Services (IIS), Apache, Sambar or OmniHTTPD. PHP was designed to run as a plug-in for existing Web server software. To test dynamic Web pages with PHP, you'll need to equip your own computer with Web server software, so that PHP has something to plug into. If you have Windows 2000/XP, then install IIS (if it's not already on your system): open Control Panel, Add/Remove Programs, Add/Remove Windows Components, and select IIS from the list of components. If you're not lucky enough to have IIS at your disposal, you can instead use a free Web server like Apache. I'll give instructions for both options in detail.

First, whether you have IIS or not, complete these steps:

- Unzip the file you downloaded into a directory of your choice. I recommend C:\PHP and will refer to this directory from here onward, but feel free to choose another directory if you like.

- Find the file called php4ts.dll in the PHP folder and copy it to the System32 subfolder of your Windows folder (e.g. C:\Windows\System32).

- Find the file called php.ini-dist in the PHP folder and copy it to your Windows folder. Once there, rename it to php.ini.

- Open the php.ini file in your favorite text editor (use WordPad if Notepad doesn't display the file properly). It's a large file with a lot of confusing options, but look for a line that begins with extension_dir and set it so that it points to the extensions subfolder of your PHP folder:

extension_dir = C:\PHP\extensions

A little further down, look for a line that starts with session.save_path and set it to your Windows TEMP folder:

session.save_path = C:\WINDOWS\TEMP

Save the changes you made and close your text editor.

Now, if you have IIS, follow these instructions:

- In the Windows Control Panel, open Administrative Tools | Internet Information Services.

- In the tree view, expand the entry labeled local computer, then under Web Sites look for Default Web Site (unless you have virtual hosts set up, in which case, choose the site you want to add PHP support to). Right-click on the Web Site and choose Properties.

- Click the ISAPI Filters tab, and click Add.... In the Filter Name field, type PHP, and in the Executable field, browse for the file called php4isapi.dll in the sapi subfolder of your PHP folder (e.g. C:\PHP\sapi\php4isapi.dll). Click OK.

- Click the Home Directory tab, and click the Configuration... button. On the Mappings tab click Add. Again choose your php4isapi.dll file as the executable and type .php in the extension box (including the '.'). Leave everything else unchanged and click OK. If you want your Web server to treat other file extensions as PHP files (.php3, .php4, and .phtml are common choices), repeat this step for each extension. Click OK to close the Application Configuration window.

- Click OK to close the Web Site Properties window. Close the Internet Information Services window.

- Again, in the Control Panel under Administrative Tools, open Services. Look for the World Wide Web Publishing service near the bottom of the list. Right-click on it and choose Restart to restart IIS with the new configuration options. Close the Services window.

- You're done! PHP is installed!

If you don't have IIS, you'll first need to install some other Web server. For our purposes I'll assume you have downloaded and installed Apache server from http://httpd.apache.org/; however, PHP can also be installed on Sambar Server (http://www.sambar.com/), OmniHTTPD (http://www.omnicron.ab.ca/httpd/), and others.

Once you've downloaded and installed Apache according to the instructions included with it, open http://localhost/ in your Web browser, to make sure it works properly. If you don't see a Web page explaining that Apache was successfully installed, then either you haven't run Apache yet, or your installation is faulty. Check the documentation and make sure Apache is running properly before you install PHP.

If you've made sure Apache is up and running, you can add PHP support:

- On your Start Menu, choose Programs, Apache httpd Server, Configure Apache Server, Edit Configuration. This will open the httpd.conf file in Notepad.

- All of the options in this long and intimidating configuration file should have been set up correctly by the Apache install program. All you need to do is add the following three lines to the very bottom of the file:

```
LoadModule php4_module c:/php/sapi/php4apache.dll
AddType application/x-httpd-php .php .php3 .phtml
AddType application/x-httpd-php-source .phps
```

Be sure the LoadModule line points to the php4apache.dll file on your system, and note the use of slashes instead of backslashes.

- Save your changes and close Notepad.

- Restart Apache by choosing Programs, Apache httpd Server, Control Apache Server, Restart on the Start menu. If all is well, Apache will start up again without complaint.

- You're done! PHP is installed!

With MySQL and PHP installed, you're ready to proceed to the Post-Installation Setup Tasks section on page 20.
