Using your favorite text editor, create a very simple HTML page, such as the following:

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en">
<head>
<title>My Custom Page</title>
</head>
<body>
<h1>Welcome to my custom page</h1>
<p>This is a test of the customization of Apache!</p>
<p>Pretty cool huh?</p>
</body>
</html>
```

Save this new file in the Apache Web directory and name it myPage.html. After saving the file, open it in your Web browser to witness the flexibility in Apache.

This is not the most advanced example, but it should give you the basic idea of how to modify and work with the Apache Web server. Now is the time to create more useful examples, because you have the basics down.

At this point, with Apache installed and tested, you can move on to the installation and configura- tion of PHP, or you can jump ahead to the configuration process of Apache.

Alternatively, you can read through the installation of Apache on UNIX, which is covered in the next section.

The installation of Apache in UNIX would be closer to working with a remote server, because you will find that most Web servers are built on Linux. This doesn't mean you will never find a Windows-based live Web server, but it certainly isn't as common.

# # Installing Apache for UNIX

The installation process in UNIX is more advanced than the Windows installation. However, the UNIX installation is often the more common scenario for a live server.

The first step to installing Apache is downloading the source. This source can either be down- loaded from the book's site or directly from Apache's Web site. Using the source provided on the book site ensures you're running a nearly identical system to the one used for writing this book.

You will find the source, as shown in Figure 1.6, directly from Apache at the following URL: http://httpd.apache.org/download.cgi.