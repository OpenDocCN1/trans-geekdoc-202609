# Session functions

These are explained in detail in Chapter 14. Sessions are means by which state is maintained between pages. Remember that HTTP, the language of the Web, does not allow servers to remember much of anything between requests for pages from a specific user. Sessions allow the server to keep track of activities by a single user.

# MySQL functions

These functions are explained in detail in Appendix J.

A total of 48 MySQL functions are available in the library. Only about a third of these are used in the applications in this book. You may find uses for some of the other MySQL functions in your applications, but you probably won’t use all of them.

# HTTP header functions

Three vital HTTP header functions exist, both of which you will need to get to know.

# header()

If you are going to be communicating with the browser or with other HTTP servers, this is the function to use.

```
int header (string string)
```

Essentially, you can send any header that would be expected under RFC 2616 (ftp://ftp.isi.edu/in-notes/rfc2616.txt), which defines HTTP. The RFC itself is a handful (and perhaps the sleepiest reading you’ll do all year). Here is a common header you are likely to send:

```
header("Location: http://www.php.net");
```

This is nothing more than a redirect: It sends the browser to a page you specify. If you have been working with straight HTML and JavaScript or the <META type=refresh> tag to do your redirects, you should switch to this type of header whenever possible. It will work for all browsers and the redirection will be totally transparent to the user.

![](bbox=[0.109, 0.795, 0.203, 0.87])

IMPORTANT — no, make that VERY IMPORTANT — you cannot send a header after anything — ANYTHING — has been sent to the browser. If you send a header after even a hard return, you will get an error. If you send a hard return before your opening <?php tag, you will get an error. If there is a hard return in an included file that precedes your header() function, you will