
There is also the possibility that cookies are only stored in memory but not permanently on the hard disk. As a consequence, after restarting the browser, this data is no longer available. Under certain circumstances, this behavior may be desirable.

### 14.2.2 Restrictions

For the publication of the cookie specification, certain precautionary measures were taken.

Probably the most important restriction is that a cookie can only be read by the server that set it. A cookie from `www.php.net` is therefore not visible from the website `www.asp.net`—and vice versa. However, it is possible to bind cookies to a second-level domain (SLD). If `.php.net` is specified as the cookie domain (with a leading dot), this cookie can be read not only from `www.php.net` but also from `pecl.php.net` and `windows.php.net`, among others. It is even possible to restrict the cookie to a path within a domain. If the path of a cookie is set to `/government`, then it cannot be accessed from a page on `/opposition` and vice versa.

There are also restrictions regarding the amount of data. A cookie itself can only contain 4 KB (4,096 characters) of data. This applies to both the name and the value of the cookie. If these together exceed 4 KB, the value may be truncated but the name remains intact (provided it is smaller than 4 KB, which can probably be assumed). Note that this is a minimum requirement for the browser, which can also process longer cookies at its own discretion.

A web browser is also instructed to accept only a maximum of 300 cookies. Only 20 cookies are permitted per domain. As soon as one of these limits is exceeded (i.e., the 301st cookie in total or the 21st cookie of the domain arrives), the corresponding oldest cookie may be deleted. These limits date back to times when hard disk space was almost prohibitively expensive. Modern browsers are more relaxed about these limits.

### 14.2.3 The Transparent Surfer?

Cookies are therefore only read by the server that set them. So why do cookies have such a bad image? Cookies are often referred to as *transparent surfers*—evoking the horrifying vision of a web user who reveals all their personal data on a website without their knowledge.

One of the main reasons is still historical. In the March 1997 issue of *Byte* magazine, Jon Udell wrote an article about digital certificates. Among other things, it states that these digital IDs are clearly superior to cookies; even worse, cookies do not guarantee privacy, because any web server can read every cookie on the client computer. This false statement—as can be seen from the previous section—spread rapidly; there was even talk that cookies could be used by other web servers to read the user’s hard disk (well, cookies are indeed stored on the user’s hard disk).

Two months and issues later, in May 1997, the overdue correction appeared in a small box in the margin. The author admitted that he had not checked his claims at all, although this would have been technically very easy. He also claimed to have had an idea for how to "steal" the cookie information, but printed the possible result (cookies are insecure) without checking it. As it turned out, it was not possible. The author violated crucial basic journalistic rules, but the damage had already been done. Even today, many people are still unaware of what cookies are and what risks they entail (see also Section 14.5)—and which risks are simply scaremongering. Completely free of all prejudices and concerns, we will now look at how cookies can be used in PHP.

## 14.3 Working with Cookies in PHP

As noted, cookie processing (read/write) takes place entirely via HTTP headers. But PHP would not be PHP if this laborious process had to be carried out by the user.

### 14.3.1 Set Cookies

The setcookie() function has two different syntax options. The most common is the following syntax (we will deal with the alternative later):

```
boolean setcookie ( string name [, string value [, int expires [, string path [, string domain [, bool secure[, bool httponly]]]]]])
```

Table 14.1 explains the meanings of the seven parameters. Based on that quantity, you will appreciate PHP’s feature of named function parameters, but this will have to wait a few more pages, because there is a special feature to consider first.

| Parameters | Description | Data type |
| :--- | :--- | :--- |
| name | The name of the cookie; this parameter is the only mandatory one. All others are optional. | String |
| value | The value of the cookie. | String |
| expires | The expiration date of the cookie as the number of seconds since 1.1.1970. | Integer |
| path | The directory from which the cookie may be read. | String |
| domain | The domain that has access to the cookie. | String |
| secure | A value that specifies whether the cookie may only be sent via HTTPS connections or not. | Boolean |
| httponly | Indicates whether the cookie is "invisible" for JavaScript or not. | Boolean |

Table 14.1 The Parameters for "setcookie()"

The individual parameters (except name and value) are dealt with separately in detail ahead.

#### Expiration Date

There are two types of cookies, which differ according to the expiration date:

- Temporary cookies or session cookies, which are only valid until the browser is closed
- Permanent cookies or persistent cookies, which are valid until a specified expiration date

The expiration date is set as shown in Table 14.1, specified as an integer value. The "unit of measurement" used is the epoch value from the Unix world: the number of seconds elapsed since January 1, 1970. There are two main ways to calculate such a value quickly and intuitively:

- time() returns the current date and time as an epoch value. If you want a cookie to be valid for a certain period from the current time, add the corresponding period of time in seconds to the return value of time(). A cookie that is valid for exactly one day would have the following value for the expiration date: `time() + 60*60*24` That is, 60 seconds per minute, 60 minutes per hour, 24 hours per day.
- mktime() converts a date into an epoch value. A cookie that is valid until 12 noon on Christmas Eve in 2025 (December 24) would have the following value as the expiration date: `mktime(12, 0, 0, 12, 24, 2025)`

> Note
> You can find more information on these and other date functions in Chapter 9.

If a cookie does not have an expiration date (i.e., there is no third parameter for setcookie() or zero is the third parameter), it is a temporary cookie. This is deleted by the system when the browser is closed, so it is no longer there the next time the browser starts. The following code fragment sets some cookies:

```
<?php
setcookie("ProgrammingLanguage", "PHP",
time() + 60*60*12); // valid for 12 hours
setcookie("LanguageVersion", "8",
mktime(0, 0, 0, 12, 24, 2025)); // Dec 24, 2025
setcookie("Session", "abc123"); // temporary
?>
```

#### Path

Cookies can be bound not only to a domain, but also to a directory. This was particularly important in the past when own domains were still very expensive and therefore many websites had URLs along the lines of www.site.xyz/username. Of course, it would be fatal if a cookie was set on www.site.xyz/username1, which could then be read by the competition at www.site.xyz/username2. For this reason, the standard behavior of cookies under PHP is as follows: The directory in which you set the cookie is also used as the value for the cookie path. A cookie that you set at www.your-company.xyz/products/index.php cannot be read from your homepage at www.your-company.xyz/index.php! For this reason, it is a good idea to set the cookie path to the main directory:

```
<?php
setcookie("ProgrammingLanguage", "PHP",
time() + 60*60*12, "/");
?>
```

If you only need a cookie in a specific area of your website (such as the administration area), it is equally useful to set the path accordingly. Ultimately, you will achieve a small but significant performance gain: the cookie is no longer sent by the web browser in the HTTP header for all pages, but only for URLs within the specified path.

#### Domain

The fifth parameter for setcookie() is the domain that has access to the cookie. By default—that is, if you do not specify the domain name—the browser takes the relevant domain directly from the URL. Thus, if your users access your website via their IP address, only this will be used; the domain name will not work.

In the original specification, the Netscape developers stipulated that the domain name must consist of at least two dots. So if you want to "serve" pecl.php.net, windows.php.net, and www.php.net with a cookie, you must enter ".php.net" as the value, including the leading dot.

Newer browsers do not necessarily require the two dots. However, to achieve the greatest possible browser compatibility, you should always specify at least two dots in the domain name if possible.

Some have now come up with a clever trick to use and collect cookies across multiple domains. The entire procedure is described in Section 14.5 in detail. The core component of this method is to specify a foreign domain. This means that a cookie is set on www.php.net, but www.asp.net is specified as the domain name. However, such "foreign cookies" are rejected by several browsers or can be rejected. The following is a code fragment in which a cookie with a domain value is created:
