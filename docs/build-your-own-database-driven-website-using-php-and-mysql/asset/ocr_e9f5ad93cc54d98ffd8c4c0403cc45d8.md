Just like your Web server, MySQL is a program that should be run in the background so that it may respond to requests for information at any time.
The server program may be found in the "bin" subfolder of the folder into
which you installed MySQL. To make things complicated, however, there are
actually several versions of the MySQL server to choose from:

+   **mysqld.exe** This is the basic version of MySQL if you run Windows
+   95, 98, or ME. It includes support for all advanced features, and
+   includes debug code to provide additional information in the case of
+   a crash (if your system is set up to debug programs). As a result of
+   this code, however, the server might run a little slow, and I've
+   generally found that MySQL is so stable that crashes aren't really a
+   concern.

+   **mysqld-opt.exe** This version of the server lacks a few of the
+   advanced features of the basic server, and does not include the debug
+   code. It's optimized to run quickly on today's processors. For
+   beginners, the advanced features are not a big concern. You certainly
+   won't be using them while you complete the tasks in this book. This is
+   the version of choice for beginners running Windows 95, 98, or ME.

+   **mysqld-nt.exe** This version of the server is compiled and
+   optimized like `mysqld-opt`, but is designed to run under Windows
+   NT/2000/XP as a service. If you're using any of those operating
+   systems, this is probably the server for you.

+   **mysqld-max.exe** This version is like `mysqld-opt`, but contains
+   advanced features that support transactions.

+   **mysqld-max-nt.exe** This version's similar to `mysqld-nt`, but has
+   advanced features that support transactions.

All these versions were installed for you in the `bin` directory. If you're
running on Win98x/ME I recommend sticking with `mysql-opt` for now -
move to `mysqld-max` if you ever need the advanced features. On Windows
NT/2000/XP, `mysqld-nt` is my recommendation. Upgrade to `mysqld-
max-nt` when you need more advanced features.

Starting MySQL is also a little different under WinNT/2000/XP, but this time
let's start with the procedure for Win95/98/ME. Open an MS-DOS Command
Prompt and proceed to the MySQL `bin` directory, and run your chosen server
program:

```
C:\mysql\bin> mysqld-opt
```

Don't be surprised when you receive another command prompt. This
command launches the server program so that it runs in the background,
even after you close the command prompt. If you press Ctrl-Alt-Del to pull