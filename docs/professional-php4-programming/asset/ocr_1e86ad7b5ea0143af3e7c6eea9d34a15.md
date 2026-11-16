# Sessions and Cookies

Sessions and cookies provide the ability to "remember" information about users, each providing a different way of storing variables for use between multiple pages. Sessions store data in temporary files on the server's hard drive. Cookies store small files on the client's computer, which the browser will send back to the server upon request.

PHP3 had no native support for sessions. Session support was achieved with a script library called PHPLib. PHPLib's session functions were defined in scripts that needed to be included within every script that required session support. PHP4's native session support is faster and more convenient than the PHPLib session functions.

Both sessions and cookies are great for applications like shopping carts and message boards, which need to incorporate the ability to track users among multiple pages.

In the course of this chapter, we will look at:

+   - Session support in PHP
+   - PHP sessions
+   - Custom session handling functions
+   - Session propagation through URLs and cookies
+   - Cookies
+   - Sample application to use cookies
+   - Problems with cookies
+   - Some more session functions