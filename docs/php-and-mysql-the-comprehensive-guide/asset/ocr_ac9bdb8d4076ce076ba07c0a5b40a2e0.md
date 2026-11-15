There is also the possibility that cookies are only stored in memory but not permanently on the hard disk. As a consequence, after restarting the browser, this data is no longer available. Under certain circumstances, this behavior may be desirable.

# ## 14.2.2 Restrictions

For the publication of the cookie specification, certain precautionary measures were taken.

Probably the most important restriction is that a cookie can only be read by the server that set it. A cookie from `www.php.net` is therefore not visible from the website `www.asp.net`—and vice versa. However, it is possible to bind cookies to a second-level domain (SLD). If `.php.net` is specified as the cookie domain (with a leading dot), this cookie can be read not only from `www.php.net` but also from `pecl.php.net` and `win-dows.php.net`, among others. It is even possible to restrict the cookie to a path within a domain. If the path of a cookie is set to `/government`, then it cannot be accessed from a page on `/opposition` and vice versa.

There are also restrictions regarding the amount of data. A cookie itself can only contain 4 KB (4,096 characters) of data. This applies to both the name and the value of the cookie. If these together exceed 4 KB, the value may be truncated but the name remains intact (provided it is smaller than 4 KB, which can probably be assumed). Note that this is a minimum requirement for the browser, which can also process longer cookies at its own discretion.

A web browser is also instructed to accept only a maximum of 300 cookies. Only 20 cookies are permitted per domain. As soon as one of these limits is exceeded (i.e., the 301st cookie in total or the 21st cookie of the domain arrives), the corresponding oldest cookie may be deleted. These limits date back to times when hard disk space was almost prohibitively expensive. Modern browsers are more relaxed about these limits.

# ## 14.2.3 The Transparent Surfer?

Cookies are therefore only read by the server that set them. So why do cookies have such a bad image? Cookies are often referred to as *transparent surfers*—evoking the horrifying vision of a web user who reveals all their personal data on a website without their knowledge.

One of the main reasons is still historical. In the March 1997 issue of *Byte* magazine, Jon Udell wrote an article about digital certificates. Among other things, it states that these digital IDs are clearly superior to cookies; even worse, cookies do not guarantee privacy, because any web server can read every cookie on the client computer. This false statement—as can be seen from the previous section—spread rapidly; there was even talk that cookies could be used by other web servers to read the user’s hard disk (well, cookies are indeed stored on the user’s hard disk).