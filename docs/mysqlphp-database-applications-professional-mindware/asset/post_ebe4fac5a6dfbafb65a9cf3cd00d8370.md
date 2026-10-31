
![](img/de0823012275cf4ceebdb822a56e6b71_399_0.png)

All the encryption in the world will not stop someone who has hacked into your box or has legitimate access. Most credit-card theft is done by dishonest employees with too much access.

![](img/de0823012275cf4ceebdb822a56e6b71_399_1.png)

This has been a quick and dirty introduction to Web security. If you would like to learn more, I suggest starting with this page, and following any interesting links provided there: http://www.modssl.org/docs/2.6/ssl_overview.html

## Encryption and security tools

Given what you have just read about encryption and security, it probably stands to reason that you are going to need some new tools. Here's a basic rundown.

First off, you are going to need to add SSL to Apache. As with everything else discussed in this book, adding SSL does not require you to pay for specialized software. All you need to do is install Apache with mod_ssl. You can read more about it at http://www.mod_ssl.org. To get SSL to work with Apache in the United States, you will need an additional piece of software called rsaref from RSA.

The installation of these tools with Apache is well documented in INSTALL.SSL file, so we won't cover it here. If you are having trouble getting mod_ssl, PHP, and MySQL to work for you, we recommend this site, which goes through the installation step by step: http://www.devshed.com/Server_Side/PHP/SoothinglySeamless/page8.html.

![](img/de0823012275cf4ceebdb822a56e6b71_399_2.png)

Make sure you read about the credit-card authorization options in the following section before you configure Apache with PHP.

But before any of this will work for you, you are going to need to get a certificate. As I already mentioned, VeriSign is the most frequently used certification organization. And if you use a VeriSign certificate along with the PayflowPro (which is a service of VeriSign) functions described below, you may be able to get a good deal. Thawte, which used to be the second-largest certification organization, is now owned by VeriSign. Other options in this area can be found at the following URL: http://dmoz.org/Computers/Security/Public_Key_Infrastructure/PKIX/Tools_and_Services/Third_Party_Certificate_Authorities/.

## Configuring for credit-card authorization

When Apache is configured with SSL your site will be able to talk to browsers securely. If the URL starts with https://, the browser knows to look on Port 443 and to look for a certificate. However, there is still the question of how your site will talk with the entity that will process credit cards and either accept or reject the transaction. PHP has many great features for dealing with other sites. For instance, fopen() is URL-aware. But none of the filesystem or URL functions work with SSL, so you will need to make use of a specialized function set or a program outside of PHP.

I wholeheartedly recommend you look at some of the new options available in PHP4 before deciding on which payment processing services to use. I'll cover them briefly here.

### PAYFLOPRO

If you decide to use Verisign to process credit cards, you will want to make use of these functions. You will need to install a code library that you will get from Verisign. You will then need to compile PHP so that it will recognize the new functions. Details can be found at http://www.php.net/manual/ref.pfpro.php.

PayflowPro is very easy to work with. A function or two will process your request and you will get back a response. Once that response is compared to a set of known codes, you will know whether or not the transaction succeeded. This is very nice and will help keep your code very clean.

### CYBERCASH

Similarly, to make use of Cybercash, you will need to do a custom installation of PHP, using the libraries that come with the PHP distribution found at http://www.php.net/manual/ref.cybercash.php. The functions that come with PHP are not as clean as those that work with PayfloPro. However, there is a nice library in /ext/cybercash of your PHP installation that should make credit-card processing relatively easy.

### CURL:

This acronym stands for Client URL Library functions. It is a code library that you can use for communicating over the Internet using just about any protocol out there. It supports Gopher, Telnet, and (the best for our purposes) HTTPS.

You can now access this library through PHP functions if you installed PHP with the --with-curl flag. You will first have to download the library from http://curl.haxx.se/.

We don't think the cURL functions are as clean as the PayflowPro functions. However, they are open-source. We'll cover the functions in the Code Breakdown section.

## Configuring for session handling

When I start breaking down the code, you will see the exact functions you need to work with sessions. But while you are reading about configuration options, it's best
to cover the different ways sessions can be implemented in PHP. But first a little on what sessions in PHP actually do.

Say you want to track the activity of your users across a number of pages, as with this shopping cart. You need to remember who has put what in a cart. To accomplish this, you could pass some rather complex variables via a cookie that held the all of the elements and their prices. But this is kind of messy, and it may expose more of the workings of your application than you are comfortable exposing. Moreover, the cookie specification (http://www.netscape.com/newsref/std/cookie_spec.html) allows for only 20 cookies per domain and only 4KB per cookie.

A better idea is give each person who visits your site a unique identifier, some value that identifies who that person is. Then, as the user adds items to the cart, information associated with the unique identifier can be stored on the server. If you were to code a function that stored the information by hand, you might create a unique string that would be put in a cookie; then, in some directory on the server, you could have a file that has the same name as the unique user ID. Within that file you could store all the variables associated with the user. For example, you might have an array of items that a specific user put in his or her cart.

In fact, this is almost exactly what sessions do. When you indicate in your code (or by settings in your php.ini) that you'd like to start a session, PHP will create a unique identifier and an associated file, which is stored on the server (the location is set in the php.ini, and by default is in the /tmp directory). Then as a user moves from page to page, all the variable information that the user chooses can be stored in the file on the server, and all the script needs to keep track of is the unique identifier.

There are many configuration options when it comes to sessions, but probably the most important decision is where the session id will be propagated, in a URL or in a cookie. Most e-commerce sites make use of cookies. However, there is the chance that some of your users will not be able to use your site properly if they have their browsers set to reject cookies. For this reason, in PHP it is very easy to add the session id to the querystring. There are two ways to go about it.

The code <?= $ID ?> will print the session id. To append the session id to a URL, you would have to manually add it, like this:

```
<a href=mydomain.com?sid=<?=$SID?>
```

This can make for some tedious work if you want to put the session id on every link in your site. However, if you compile PHP with the flag --enable-trans-sid, the session id will be automatically appended to every relative link in your pages once a session has been started.

## Code Overview

As you might have guessed by now, there are two function sets used here that are relatively unique: the functions that deal with sessions and the functions associated with the cURL library. I will cover both sets of functions in some detail in this section.

First, though, I need to make another note about the advantages of the object-oriented approach. When you read Chapter 10 (you did read Chapter 10, right?) you saw some of the principles of object-oriented programming in practice. Specifically, you should have noticed how inheritance is used. When a class inherits the properties and methods of a parent class, it has access to all of the methods and properties of the parent.

In this application, you are extending the code you used in the catalog, so it makes sense that this application would create classes that extend the classes used in the catalog. Please be sure you are familiar with the catalog classes in Chapter 10 before proceeding.

## Session functions

If you head over to the session page in the PHP manual (http://www.php.net/manual/ref.session.php), you will find 16 different functions. Depending on your needs, you may have to use a majority of these, but in many circumstances you could get away with using a single function: session_register(). We'll explain.

![](img/de0823012275cf4ceebdb822a56e6b71_402_0.png)

There are many functions and settings regarding sessions that we don't cover here. As always, make sure to check the manual.

The first thing you will need to do is let PHP know that you wish to start a session. You can do that explicitly by using session_start(). Then you will need to let PHP know what variables you want to store. You can do this with session_register("variable_name"). Take the following page, for example:

![](img/de0823012275cf4ceebdb822a56e6b71_402_1.png)

The session_start() and session_register() functions should be at the very top of your PHP pages. These functions send cookies, which are a type of HTTP header. If you attempt to send any type of header after text has been sent to the browser, you will get an error.

```
<?
session_start();
session_register("mystring");

$mystring = "testing for a string";
?>
```
