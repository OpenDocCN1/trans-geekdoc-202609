# Chapter 18. NETWORK

HTTP Authentication

Controlling Browser Cache

Setting Document Type

Email with Attachments

Verifying an Email Address

Most anything you write in PHP will be in the context of a network. It's a language intended primarily to produce HTML documents via the HTTP protocol. PHP allows you to code without worrying about the underlying protocols, but it also allows you to address the protocols directly when necessary. This chapter deals intimately with two important protocols, HTTP and SMTP. These are the protocols for transferring Web documents and I've attempted to describe some common problems and provide solutions. This chapter may address a particular problem you face, such as protecting a Page with basic HTTP authentication, but it also illustrates generally how to use HTTP headers and communicate with remote servers.

# HTTP Authentication

If you have any experience with the Web, you're familiar with basic HTTP authentication. You request a page, and a small dialog window appears asking for username and password. As described in Chapter 8, "I/O Functions," PHP allows you to open URLs with the fopen function. You can even specify a username and password in the URL in the same way you do in Navigator's location box. Authentication is implemented using HTTP headers, and you can protect your PHP pages using the header function.

To protect a page with basic HTTP authentication, you must send two headers. The WWW-Authenticate header tells the browser that a username and password are required. It also specifies a realm that groups pages. A username and password are good for an entire realm, so users don't need to authenticate themselves with each page request. The other header is, which should be HTTP/1.0 401 Unauthorized. Compare this to the usual header, HTTP/1.0 200 OK.

Listing 18.1 is an example of practicing a single page. The HTML to make a page is put into functions because it needs to be printed when the authentication succeeds or fails. The PHP_AUTH_USER and PHP_AUTH_PW variables are created automatically by PHP if a username and password are passed by the browser. The example requires my name, leon, for the username and secret for the password. A more complex scheme might match username and password against a list stored in a file or a database.