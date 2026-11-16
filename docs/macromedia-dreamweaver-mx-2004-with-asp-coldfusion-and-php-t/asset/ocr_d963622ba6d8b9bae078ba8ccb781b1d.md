# # SETTING UP PHP IN MAC OS X

Like Apache itself, PHP comes preinstalled in Mac OS X, so you don’t need to install it. Also like Apache, the version of PHP that ships with Mac OS X (PHP 4.12) is not current. You can download and install the latest and greatest version of PHP (to do so, see the Apple developer site, mentioned in the preceding Note). That requires some extra work, and it is sufficient for the purposes of this book to use the shipping version. In the remaining chapters, only one line of code won’t work in this version, and it has an easy workaround that I’ll point out when the time comes.

To use PHP on Mac OS X, you need to turn it on. In contrast to turning on the Apache Web server, you can’t just click a checkbox, though; you need to type some code in the Apache Web server’s configuration file, httpd.conf.

> **NOTE** _To develop for the Web on the Mac platform requires more than a passing familiarity with the Macintosh implementation of Unix, called Darwin, including using the Terminal window, navigating directories, using the permission system and the root user, as well as editing text in common Unix text editors, such as pico. The directions in this section assume you are competent working in the command line Unix interface. If this is new to you, I highly recommend Unix For Mac OS X: Visual QuickPro Guide (Peachpit), which is my personal favorite book on OS X._

+   1) In the Terminal window, open the file httpd.conf in a text editor. Typically, this file can be found in the following location /etc/httpd/httpd.conf.

+   2) Search or simply scroll until you see a number of lines that begin with LoadModule or #LoadModule. As the name suggests, LoadModule causes extensions, including PHP, to be activated on the Apache server.

‘The hash mark (#) that precedes some lines signals a comment. That is, the interpreter ignores any lines preceded by a hash mark.

+   3) Look through the LoadModule section for the following line of code. If it exists and is preceded with a # sign, remove that sign. If no such line exists, type it in at the end of the LoadModule block, exactly as you see below.

```
LoadModule php4_module libexec/httpd/libphp4.so
```

‘This is one of two lines in httpd.conf that activates PHP in Apache.