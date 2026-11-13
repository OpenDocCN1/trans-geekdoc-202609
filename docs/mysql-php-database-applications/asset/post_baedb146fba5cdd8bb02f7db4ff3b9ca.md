
Probably the best-known organization involved in security certificates is VeriSign. You can find out about their offerings at this site: http://www.verisign.com/products/site/ss/index.html.

### SECURE PROTOCOL

HTTP by its very nature is open to eavesdropping. Packets that move across the Internet's routers are full of messages just waiting to be sniffed and read. Normally, the fact that you can easily read data sent via HTTP is a good thing. It makes the transfer and rendering of information quite simple. However, in cases where you need security, HTTP won't work well.

For example, if you are giving credit-card information to a site—for example, the commerce site you set up—you want to make sure that the information is unreadable. To ensure that, you need to make use of the Secure Sockets Layer, or SSL. SSL is an additional protocol by means of which the keys and certificates from your site are transferred to a browser or another server. Over SSL, your browser is able to verify the certificate from your site so that it knows you are who you say you are. Sites can also use it to verify each other's identity.

All the encryption in the world can't stop someone who has hacked into your box or who has legitimate access. Most credit-card theft is done by dishonest employees with too much access.

## ENCRYPTION AND SECURITY TOOLS

Given what you have just read about encryption and security, it probably stands to reason that you are going to need some new tools. Here's a basic rundown.

First off, you are going to need to add SSL to Apache. As with everything else discussed in this book, adding SSL does not require you to pay for specialized software. All you need to do is install Apache with mod_ssl (which you can read more about at http://www.modssl.org). You'll want to have a look at the products of the Apache-SSL project as you configure your server for secure connectivity.

The process of installing SSL modules is documented by the project teams and is best found on the Web, so we won't cover it here. If you are having trouble getting mod_ssl, PHP, and MySQL to work for you, we recommend this site, which goes through the installation step by step: http://www.devshed.com/Server_Side/PHP/SoothinglySeamless/page8.html. Even though it deals with rsaref, which is no longer strictly required, the steps remain valid.

## Configuring Apache for credit-card authorization

When Apache is configured with SSL your site is able to talk to browsers securely. If the URL starts with https:// the browser knows to look on port 443 and to look for a certificate. However, the question of how your site talks with the entity that processes credit cards and either accepts or rejects the transaction still exists. Fortunately, PHP's integration of HTTP streams with its regular file-handling functions, like fopen() and file_get_contents(), has gotten even better. If PHP is built with SSL enabled, you can use these functions to exchange data with your credit-card processor via a secure connection. (Be aware, though, setting up the certificates for use in this way is more complicated than it is to go to an https:// URL in your browser. The bank or service you choose will have more information on their requirements for you.)

## Configuring for session handling

When we start breaking down the code, you can see the exact functions you need in order to work with sessions. But while talking about configuration options it's best to cover the different ways sessions can be implemented in PHP. However, first we present a little about what sessions in PHP actually do.

Suppose you want to track the activity of your users across a number of pages, as with this shopping cart. You need to remember who has put what in a cart. To do this you could pass some rather complex variables via a cookie that holds all the elements and their prices, but that approach is kind of messy and might expose more of the workings of your application than you are comfortable exposing. Moreover, the cookie specification (http://www.netscape.com/newsref/std/cookie_spec.html) allows only 20 cookies per domain and only 4 bytes per cookie.

A better idea is to give each person who visits your site a unique identifier, some value that identifies who that person is. Then, as the user adds items to the cart, information associated with the unique identifier can be stored on the server. If you were to code a function that stored the information by hand, you might create a unique string that would be put in a cookie; then, in some directory on the server, you could have a file that has the same name as the unique user ID. Within that file you could store all the variables associated with the user. For example, you might store an array of items that a specific user put in his or her cart.

In fact, this is a description of almost exactly what sessions do. When you indicate in your code (or by settings in your php.ini) that you'd like to start a session, PHP creates a unique identifier and an associated file, which is stored on the server (the location is set in the php.ini and, by default, is in the /tmp directory). Then, as a user moves from page to page, all the variable information that the user chooses can be stored in the file on the server, and all the script needs to keep track of is the unique identifier.

Many configuration options are possible when it comes to sessions, but probably the most important decision is whether the session ID is propagated in a URL or in a cookie. Most e-commerce sites make use of cookies. However, it is possible that some of your users will not be able to use your site properly if they have their browsers set to reject cookies. For this reason, in PHP it is very easy to include the session ID in the page request. You have two options.

- First, you can append the session identifier to the URL, as in this example: http://www.fakeo.domain/?SID=ABCDEFG. That corresponds to the HTTP GET operation.
- Alternatively, you can include the session identifier in a hidden form field, which is submitted to the server when the form in which it is embedded is submitted. This corresponds to the HTTP POST operation.

However, this is NOT recommended. Though it's theoretically possible for a session to be “hijacked” in some way no matter how you set things up, putting the session cookie in as highly visible a place as the URL or the source of the form makes life easier for anyone trying to break in. It might be better in the long run to try to guide any recalcitrant users into allowing you to give them a cookie.

## Code Overview

As you might have guessed by now, this example uses two function sets that are relatively unique:

- The functions that deal with sessions
- The functions associated with the cURL library

We cover both sets of functions in some detail in this section.

First, though, we need to make another note about the advantages of the object-oriented approach. When you read Chapter 12 (you did read Chapter 12, right?) you saw some of the principles of object-oriented programming in practice. Specifically, you might have noticed how inheritance is used. When a class inherits the properties and methods of a parent class, it has access to all of the methods and properties of the parent.

In this application you are extending the code you used in the catalog, so it makes sense that this application creates classes that extend the classes used in the catalog. Please be sure you are familiar with the catalog classes in Chapter 12 before proceeding.

## Session functions

If you head over to the session page in the PHP manual (http://www.php.net/manual/ref.session.php), you will find at least 20 different functions. Depending on your needs, you may have to use a majority of these, but in many circumstances you can get away with using one: session_start(). The actual storing of variables in your session data, and removal of them, is just a matter of setting or unsetting a value in the $_SESSION superglobal array, once you’ve started your session.
