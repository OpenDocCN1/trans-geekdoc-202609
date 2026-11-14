
credits are processed. Now say that Alice is an administrator who went to your site, was authenticated, and did whatever (it doesn't matter whether she used the add credit system or not). If Alice doesn't log out, there's still a cookie in her browser indicating that she's an authenticated user of your site. Next, Alice comes across some page in which hacker Bob has identified a PHP script as the source for an image tag:

```
<img src="http://www.yoursite.com/add_credits.php?user=12&credits=-100" />
```

This might be a public forum, or a review system, or any site that allows users to post images in some way.

When Alice loads the page with that image tag, her browser will make a request for the add_credits.php script on your site, passing along the user and credits numbers. This request will look, to the server, exactly the same as if Alice had consciously gone to the add_credits.php page. That page will first confirm that the requesting user is authenticated, which Alice is. The page would then, in theory, perform whatever action is the result of receiving those two values in the URL.

This is a blind attack in that the original hacker Bob will never see the results of the request being made: He's just putting this out there in the hopes that, in this case, his account at your site gets credited when some authenticated user stumbles upon this code. Know that just authenticating the user will not prevent this kind of attack, because it's that trust that makes this kind of attack plausible.

To prevent a CSRF attack, start by teaching your administrators to log out. Then, restrict the lifetime of an authentication cookie so that it will expire some minutes after they've stopped being active on your site (online banks may only allow ten or fifteen minutes of user inactivity). This will narrow the window of CSRF danger to just that brief cookie lifetime.

> CSRF attacks are more successful against very popular sites that use long-lasting cookies.

Not making sensitive information (like a user ID value) public is also important, but just relying on a hacker not knowing about something isn't real security. Although it's possible to perform CSRF requests via POST, relying upon posted data for sensitive requests is more secure (and is in keeping with the approach that POST is to be used when a request will result in site changes).

The true CSRF prevention comes from guaranteeing that sensitive requests, like the transfer of credits, are actually prompted by your own site. You cannot reliably use a browser's “referrer” value (that is, what page the browser was on before this one), though. Instead, create your own tie between the HTML form and the page that handles its request. The tie itself will be a secret token, uniquely generated for each request. Here’s what you’d do on the page that displays the form (with much of the code implied):

```php
<?php // form.php

...

$csrf_token = uniqid(); // or uniqid(rand(), true);
session_start();
$_SESSION['csrf_token'] = $csrf_token;

...

echo '<input type="hidden" name="csrf_token" value="' . $csrf_token . '" />';

...
?>
```

On the page that handles the request, validate the token:

```php
<?php // handle_form.php

...

session_start();
if ( $_SERVER['REQUEST_METHOD'] == 'POST' ) // only POST is allowed
&& ( isset($_SESSION['csrf_token'], $_POST['csrf_token']) ) // make sure the tokens exist
&& ( $_SESSION['csrf_token'] == $_POST['csrf_token'] ) ) { // OK!

...
} else { // Invalid request!
}

...
?>
```

> **tip**
>
> To prevent bots from trying to use a form, integrate a CAPTCHA (Completely Automated Public Turing test to tell Computers and Humans Apart) system.

Now the request will only be processed if Alice is still logged in (that is, her cookie is still live), if the request is via the POST method, if a csrf_token element exists in both $_SESSION and $_POST, and if the two values match. That’s pretty good security!

## PART TWO: SELLING VIRTUAL PRODUCTS

![](img/4f47e47c67bd619ac73250f11c9fc7ce_63_0.png)

## 3 FIRST SITE: STRUCTURE AND DESIGN

The first e-commerce site being developed in this book, Knowledge is Power, will provide content to paid subscribers. It will have these primary features:

- Straightforward use of HTML, PHP, and MySQL
- User accounts
- Ability for administrators to add HTML and PDF content
- PayPal for processing payments

This will be a relatively standard e-commerce example, applicable to most small- to medium-size businesses. By comparison, the more complex project, developed in Part Three, “Selling Physical Products,” of the book, will use HTML, PHP, and MySQL in more advanced ways, won’t require user accounts, will sell products that get shipped later (that is, the customer will not be billed immediately), and will integrate a different payment system. This is not to say that what you’ll learn in this part of the book won’t be applicable to real-world situations, quite the contrary.

The user account system will have several pieces: registering, logging in, logging out, retrieving forgotten passwords, and changing existing passwords. As a bonus, the user’s password will be handled with extra security, in a way that you perhaps have not yet seen.

The available content that the customer is paying to see will be in two formats: HTML and PDF. For the former, you’ll integrate a WYSIWYG editor into an HTML form so that administrators can easily create HTML without knowledge of HTML. For the latter, you'll write a *proxy script* that serves protected files not available over HTTP or to non-validated users.

In this chapter, you'll set the stage for developing the site. This includes the database design, the organization of files on the server, the HTML template, plus a couple of necessary helper files that every other PHP script will use. The entire code for the site is also downloadable from www.DMCInsights.com/ecom/.

### DATABASE DESIGN

The database I've designed for this example is simple, yet appropriate, with only five tables (Figure 3.1).

![](img/4f47e47c67bd619ac73250f11c9fc7ce_65_0.png)

Figure 3.1

The *categories*, *pages*, and *pdfs* tables represent the “products” side of this e-commerce example. The *categories* table just lists the categories into which the HTML content will be organized. Each category will contain one or more pages, but each page will be in only one category.

The *pages* table stores the actual HTML content. For each HTML page, there are three important fields: *title*, *description*, and *content*. The *title* will be used as a link to each page and will also be used as the browser’s title. The *description* is a short block of text that, um, describes the page’s content. This value will be viewable to any user and to search engines. The *content* column stores the actual HTML content. You’ll see all of this in action in Chapter 5, “Managing Site Content.”

> **tip**
>
> I'm a programmer, so I start designing the database and work my way to the HTML design. You might start with the user interface and work your way down to the database instead.

The **pdfs** table lists the particulars for each PDF file the site has, including a title for the PDF, like the HTML page title, a short description—viewable by anyone—the name of the actual PDF file, and its size in kilobytes. When a PDF file is uploaded to the site, it’ll be given a non-obvious, temporary name (for example, aofo7b9b15e38ca77219884a8bbage57d01fae88) that must also be stored; but when the PDF is served to the user, its original file name will be used instead. The PDFs are not being associated with information categories.

> **note**
>
> Most of the tables have a column that reflects when a record was added. The **users** table also has a field indicating when a record was last modified.

The **users** table stores a minimum amount of information about the customers. Each customer can create a username, and the system will also store their email address, a password, their first name, and their last name. The password will be stored as a **hash**, which is a representation of a value (as opposed to being an encrypted version that could be decrypted). Hashes always have exact lengths, so that column **could** be declared as a fixed **CHAR**. However, the password can take up less space if it’s stored as binary data, which is how the column will be defined.

The site will have two types of users — members and administrators — so an **ENUM** column (that is, an enumerated list of options) will store the type, with the default value being _member_. Although administrators will never have to pay for access to the site, I thought it would make sense to use the same login system the non-administrators use, which means the administrators must be registered in the database, too. The **users** table also has a **date_expires** column that stores the date through which their account is active (that is, paid). When the user first subscribes and pays, the account will be set to expire in a year. When the user renews their membership, the account will be updated to one year later. Users whose accounts have expired will still be able to log in, but they won’t be able to view any content and will be notified that they need to renew.

> **tip**
>
> With databases, it’s much, much better to save more information than you end up needing than to later discover you haven’t been storing something you do need.

All payments will be handled through PayPal. Even though PayPal will provide detailed logs of every transaction, it’s wise to record the basics of each transaction in this system as well. The **orders** table will store every transaction that goes through PayPal, associated with the ID of the user (as taken from the **users** table). Each order will be associated with exactly one user, but each user can have one or more records in the **orders** table. Three pieces of information from the PayPal transaction will be recorded, too: the **transaction_id**, which is a unique identifier; the **payment_status**, which is just a confirmation code; and the **payment_amount**. Storing this basic data will allow you to create a simple admin interface for viewing the total number of orders, amount of money taken in, and so on, without going to PayPal for that information. The **transaction_id** is the most sensitive piece of data stored in the database; through it, many details are accessible, but only to authorized PayPal users.
