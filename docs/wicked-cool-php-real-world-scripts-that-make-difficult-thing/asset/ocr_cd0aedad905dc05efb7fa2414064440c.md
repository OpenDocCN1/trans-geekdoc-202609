**NOTE** If you've overridden the tar directory structure and placed your library into a folder that's not the default, you'll need to add the path to the --with flag so that PHP can find it. This has happened in the apxs (Apache Extension Tool Synopsis) library in our example above, and the --with-apxs=/usr/local/apache/bin/apxs flag tells PHP that apxs is stored in the /usr/local/apache/bin/apxs directory.

+   **8.** **Fetch and unpack a new PHP source distribution; then change to that directory.** You can unpack the PHP source code just as you did for the library source code previously. If you already have a previous source code tree of PHP, you can use that, but run `make clean` there beforehand.

+   **9.** **Copy the configure command you created earlier from your text file, paste it onto the command prompt, and press ENTER to run it.** This reconfigures PHP with the new library, preserving any old libraries.

+   **10.** **Make PHP.** Run `make`, and then run `make install`. There will be a long wait as each command builds and installs all of PHP's components.

**NOTE** If you have made any changes to your .ini files, as shown earlier in this chapter, they may be overwritten with the defaults when PHP is recompiled. Take a look afterward to verify that your settings have been preserved.

+   **11.** **Restart Apache.** Run the `apachectl graceful` command.

+   **12.** **Test PHP.** First, try running a generic "Hello, world!" script to ensure that PHP is up and running without error, and then try running a couple of library-specific functions to see whether the new library works properly.

# **What Can Go Wrong?**

There are so many things that can go wrong during the build process that it's almost impossible to list them all. Although many errors are complicated, and many of them are library specific so that you will need to seek specific advice, three common problems pop up all the time.

The first major problem that could happen is that your distribution or release may not have the software development packages installed. You need the C compiler and various "development" versions of many other libraries so you can build code against them.

Second, you may need to configure PHP using a --with parameter that has an explicit path; for example, --with-mcrypt=/usr/lib/mcrypt.

The other common glitch is that you could have configured the extension's library package incorrectly. As mentioned earlier, you should configure Mcrypt with the --disable-nls --disable-posix-threads flags; otherwise, you may crash Apache. Other libraries require similar tweaking in order to work smoothly with PHP and Apache. Check the FAQs, man pages, and README files for details.