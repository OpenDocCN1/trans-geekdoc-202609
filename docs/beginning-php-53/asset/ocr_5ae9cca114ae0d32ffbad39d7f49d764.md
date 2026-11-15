# Running PHP with other Web Servers

As mentioned earlier in the chapter, you're not limited to running PHP with Apache. It's also possible to run it with Microsoft's Internet Information Server (IIS) on Windows, as well as with other Web servers such as Zeus.

A common setup is to use PHP with IIS running on Windows. This gives you the advantage of not having to install Apache, and also means that you can run other Microsoft technologies such as ASP.NET on the same Web server. You can install PHP as either an ISAPI module, which means it can integrate directly with IIS, or as a stand-alone CGI binary. The ISAPI approach is recommended for tighter security.

This book doesn't go into the details of the installation process, but you can find out how to get PHP working with IIS on the www.php.net Web site:

```
http://www.php.net/manual/en/install.windows.iis.php
```

# Compiling PHP Yourself

The installation techniques you looked at earlier in this chapter all work with precompiled binaries of PHP. This helps to keep things simple, because it's easier to work with binaries — especially on a Windows computer — than it is to compile PHP from the source code.

However, compiling PHP from source is useful if:

+   - You want to really get under the hood and tweak PHP to your heart's content

+   - You want to try out the latest and greatest version of PHP (known as a snapshot) before it's released as a binary package. For example, if PHP 5.3 still isn't available as a package for your operating system at the time you read this, you can download the PHP 5.3 source code and compile it yourself

*Windows binaries of various development versions of PHP are available, which saves you having to compile from scratch. See http://windows.php.net/snapshots/ for details.*

The basic steps for compiling PHP are:

+   1. Install a C compiler on your computer if it doesn't already have one (on Ubuntu install gcc and related packages; on Windows install Visual C++; and on the Mac install Xcode).

+   2. Download the PHP source code from http://www.php.net/downloads.php or the latest snapshot from http://snaps.php.net/ and unzip/untar the file.

+   3. Run the configure script inside the distribution folder to set various compile-time options. This allows you to specify things such as compiling PHP as an Apache module, and including or excluding specific libraries such as the GD or MySQL library.

+   4. Run make to compile PHP.

+   5. Run make install to install the compiled binary files.