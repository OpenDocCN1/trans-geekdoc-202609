I saved this file as myfile.php. Next, I type the following line at the Linux command prompt:

```
php myfile.php
```

The PHP processor reads the myfile.php file and displays the following output on-screen (you might see different numbers if you’re using a different version of PHP):

```
X-Powered-By: PHP/4.1.2
Content-type: text/html

Hi
```

You can see that the processor output the word Hi. It also output a carriage return, which is the \n inside the double quotes. (The \n stands for newline.)

But what’s all that junk that appears at the beginning of the output? These “junk” lines at the beginning of the output tell the browser what type of information follows. In this case, HTML follows, which is what text/html means. The other part, X-Powered-By, tells how the HTML was generated, in case the browser wants this information.

Say you take the myfile.php file and put it on a Web server, and then go to a client computer and browse to the .php file like so:

```
www.jeffcogswell.com/myfile.php
```

You see the word Hi appear in your Web browser. Now when you view the source for the file in the Web browser, you see this:

```
Hi
```

The output includes a newline at the end, exactly as the PHP program requested. This is getting pretty nifty!

For a .php file to get processed, the PHP processor must be present on the Web server. The Web server also must be configured to send .php files through the PHP processor.

You can’t simply open a .php file in your browser. If you store a local .php file on your computer and open it in the browser, the browser treats it as an .html file and ignores all your PHP code.

If you want to try out some PHP at home, you can use one of the following two methods: