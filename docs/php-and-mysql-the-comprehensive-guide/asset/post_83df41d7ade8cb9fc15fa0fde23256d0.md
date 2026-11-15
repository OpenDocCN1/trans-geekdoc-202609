
You can then see the URL of this pull request in the GitHub issue tracker. You then hope that the development team responsible for the module will take care of it. If everything is in order, your patch will be improved (or you will be asked to improve it), and finally—hopefully—the pull request will be accepted (see Figure 40.4).

![](img/ae7820c36e8f24c1623d26668b28e80e_979_0.png)

**Figure 40.4** The Patch Was Created and Merged Later

Your bug fix will then be included in the next PHP release! You can be sure of infinite fame, because those who have fixed a bug are usually named in the NEWS file and also in the release notes (see Figure 40.5 and Figure 40.6).

![](img/ae7820c36e8f24c1623d26668b28e80e_979_1.png)

**Figure 40.5** The Fixed Bug in the Release Notes

![](img/ae7820c36e8f24c1623d26668b28e80e_980_0.png)

Figure 40.6 More Information—and 15 Milliseconds of Fame—in the "NEWS" File

## 40.1.2 New Features

PHP is often accused of having grown very “organically” in certain areas, including inconsistent APIs. To avoid this accusation in future, the PHP project has defined a binding process that must be followed before a new feature is added to PHP. The whole thing is called Request for Comments (RFC) and can be found at https://wiki.php.net/rfc (overview; see Figure 40.7) and https://wiki.php.net/rfc/howto (step-by-step instructions). Essentially, the process is as follows:

- 1. Think of a new, useful feature for PHP.
- 2. Email internals@lists.php.net and describe your idea.
- 3. If you do not meet with total rejection, formulate an RFC (usually, an idea plus an implementation) and make it available for discussion.
- 4. After discussion and, if necessary, some adjustments, your RFC will be voted on.
- 5. If successful, your code will be added to the PHP project.

> **Further Reading Material**
> 
> Christopher Jones has formulated a somewhat more detailed guide to the RFC process at http://s-prs.co/v602258 and goes even further than the official RFC page. Ben Ramsey has successfully gone through the RFC process and describes the procedure in presentation slides, which you can view at http://s-prs.co/v602259.

![](img/ae7820c36e8f24c1623d26668b28e80e_981_0.png)

Figure 40.7 Current RFCs in Various Phases (Coordination, Discussion, and So On)

## 40.2 Further Options

However, the PHP project offers various ways to return something even without C knowledge. The Get Involved page at php.net/get-involved.php lists four approaches:

- 1. You can run the test suite supplied with PHP. Do errors occur? Are they already known and reported in the bug tracker?
- 2. If a test has an error, is it the test itself, or is there actually an error in PHP? This analysis, and possibly even a bug fix for the test (or for PHP), is very useful. The PHP quality assurance team provides further information on writing tests at http://qa.php.net/write-test.php.
- 3. Submit bugs in the bug tracker (which we have already mentioned a few times in this chapter).
- 4. Expand or translate the documentation.

We would like to mention a fifth option that is very close to our hearts. The PHP Foundation was founded by several companies and individuals from the PHP environment in order to put the open-source project on a more stable footing, particularly because the involvement of Zend, and especially that of Microsoft (which, among other things, has long supported the Windows version of PHP), has declined sharply. The organization not only promotes PHP, but also supports 10¹ developers monetarily “part-time” to work on PHP. If you or your company benefit from PHP, it wouldn't be a bad idea to give some of it back to the PHP Foundation. For more information and ways to support the work of the organization, please visit the project website at https://thephp.foundation (see also Figure 40.8).

1 At the time of manuscript submission at the end of January 2024. Here is the current list of people: http://s.prs.co/v6022100.

No matter how you participate in PHP yourself, and even if you only use it yourself and convince friends and colleagues: this is the only way to make the project even bigger, more successful, and better than it already is. Thank you very much!

![](img/ae7820c36e8f24c1623d26668b28e80e_982_0.png)

Figure 40.8 The Homepage of the PHP Foundation

## The Authors

![](img/ae7820c36e8f24c1623d26668b28e80e_983_0.png)

**Christian Wenz** is a consultant and software architect who specializes in web technologies and web security. He leads digitization projects in corporate environments. His books have been translated into more than a dozen languages.

![](img/ae7820c36e8f24c1623d26668b28e80e_983_1.png)

**Tobias Hauser** is a consultant, trainer, and author. He supports companies with his focus on PHP-based web applications, covering everything from system selection to interface architecture, and writes regularly about web topics.

## Index

- - ........................ 114
- -- ........................ 115
- \\ ........................ 106–107, 296
- \\\\ ........................ 100, 106–107
- ` ........................ 129
- ^ ........................ 126, 296
- __autoload() (function) ........ 351
- __call() (method) ........ 341
- CLASS (constant) ........ 333
- __construct() (method) ........ 321
- __destruct() (method) ........ 323
- DIR (constant) ........ 718
- FILE (constant) ........ 718
- FUNCTION (constant) ........ 352
- get() (method) ........ 343
- METHOD (constant) ........ 351
- NAMESPACE (constant) ........ 380
- set() (method) ........ 344
- sleep() (method) ........ 357
- soapCall() (method) ........ 767
- toString() (method) ........ 352
- wakeup() (method) ........ 357
- ! ........................ 124
- != ........................ 117
- !== ........................ 118, 939
- ? ........................ 297
- . ........................ 201, 296
- .. (Operator) ........ 166, 258, 339
- .htaccess ........ 896, 918
- .php ........ 37
- \\ ........ 101
- [^ADZ] ........ 296
- [] ........ 240, 296
- [a-z] ........ 296
- { ........ 136
- {} ........ 296
- } ........ 136
- @ ........ 129
- * ........ 114, 297
- ** ........ 115
- **= ........ 116
- *= ........ 115
- / ........ 114, 298
- /* ........ 95
- /* ... */ ........ 95
- // ........ 95
- /= ........ 115
- & ........ 110, 126
- && ........................ 123
- <?php ........................ 93
- # ........................ 95
- #[Override] ........................ 40, 309
- #[AllowDynamicProperties] ........................ 40, 309
- % ........................ 114
- %= ........................ 115
- + ........................ 114, 297
- ++ ........................ 115
- += ........................ 115
- < ........................ 117
- <% ........................ 94
- << ........................ 126
- <<< ........................ 193
- <= ........................ 117
- <=> ........................ 123
- <> ........................ 117
- <br /> ........................ 204
- -= ........................ 115
- = ........................ 101, 241
- == ........................ 117
- === ........................ 118, 939
- > ........................ 117
- >= ........................ 117
- >> ........................ 126
- | ........................ 126, 297
- || ........................ 124
- ~ ........................ 126
- $ ........................ 101, 107, 296
- $COOKIE ........ 111, 263, 469
- $ENV ........ 111, 263
- $FILES ........ 111, 263, 445, 745
- $GET ........ 111, 263, 867
- $POST ........ 111, 263, 867
- $REQUEST ........ 111, 263
- $SERVER ........ 111, 263
- $SERVER[PHP_AUTH_PW] ........ 901
- $SERVER[PHP_AUTH_USER] ........ 901
- $SESSION ........ 111, 263, 486
- $GLOBALS ........ 111, 171
- $HTTPS_COOKIE_VARS ........ 407
- $HTTP_GET_VARS ........ 112, 407
- $HTTP_POST_FILES ........ 407
- $HTTP_POST_VARS ........ 407
- $HTTP_SERVER_VARS ........ 262, 407
- $this ........ 315
- \0 ........ 215
- \000 ........ 107
