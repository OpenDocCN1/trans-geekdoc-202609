
Next, there must be a way to see who has signed the guestbook. For the sake of having readable Web pages, we created a standard style, shown in Figure 8-2, in which only two entries are printed on each page. At the bottom of the page are navigational elements that indicate whether previous or additional entries exist. These should be conditional and should disappear appropriately when you are at the beginning or end of the guestbook.

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_276_0.png)

Figure 8-2: Page for viewing the guestbook

Finally, we need a page that enables us to delete entries we don't want. The page in Figure 8-3 seems to do the trick. Access to this page needs to be limited to authorized users: We don't want any old schmo going in and cleaning out our guestbook.

## What do we need to prevent?

The major problem that we need to tackle in the guestbook application is one that is common to any application with form input: It is possible for vandals to input nasty code into your forms that will screw up the pages for everyone else who comes along. If you used the guestbook application in the introduction you could be in serious trouble. Consider what would happen if someone inserted the following code into a text field:

```
<script>alert("boo");</script>
```

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_277_0.png)

Figure 8-3: Page for administering the guestbook

The next time the page loaded, the viewer would be greeted with a little treat seen in Figure 8-4.

If some jerk felt like it, he or she could screw up your page with all sorts of tags, as follows:

```
`<img src=http://www.britney-spears.fsnet.co.uk/britney4.jpg>`
```

Additionally, this application requires some validation. When the user enters information, the application is going to see that it makes sense. The application will check for the following:

- Email addresses should contain an at symbol (@), one or more characters before the @, and a dot somewhere after the @. Email validation can get more complex (and will in later chapters).
- URLs should look like URLs, complete with an http:// prefix and at least one dot.
- Some text must be entered in the name field. There's little point to a guestbook entry without a name.
- No email address should appear more than once in the database.

Once the application has checked all of this, the user will need to be made aware of any errors. Figures 8-5 and 8-6 show how we will indicate these errors.

```
View

bool

OK

Name:
Location:
Email:
URL:http://www.joeblow.com
Comments:like, yo, this sucks

Name:joe blow
Location:kokomo
Email:joe@kokomo.com
URL:http://www.joeblow.com
Comments:like, yo, this sucks

Name:joe blow
Location:kokomo
Email:joe@kokomo.com
URL:http://www.joeblow.com
Comments:like, yo, this sucks

Name:joe blow
Location:kokomo
Email:joe@kokomo.com
URL:http://www.joeblow.com
Comments:like, yo, this sucks
```

Figure 8-4: Results of a problem entry

```
Sign My Guest Book!!

* jgreen_1@yahoo.com doesn't look like a valid email address
* kdiek doesn't look like a valid URL

Please try again

Name: Jay Greenspan
Location:
Email: jgreen_1yahooe.com
Url: kdiek
Comments:

Sign! Start Over
```

Figure 8-5: Reporting bad information

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_279_0.png)

Figure 8-6: Reporting a duplicate entry

## Designing the Database

We covered the normalization process in Chapter 1, and before long we’ll put these normalization skills to work. For this application the set of information is pretty simple. So simple, in fact, that a single table will do the job. Actually, that isn’t quite true. For administrative purposes, you should create a table against which user names and passwords can be authenticated. Here are the create statements that will make the tables:

```
drop table if exists guestbook;
create table guestbook
(
    entry_id        integer not null auto_increment
  , name            varchar(40) null
  , location        varchar(40) null
  , email           varchar(40) not null
  , url             varchar(40) null
  , comments        text null
  , created         timestamp
  , remote_addr     varchar(20) null
  , primary key (entry_id)
  , unique (email)
);
```

```
drop table if exists guestbook_admin;
create table guestbook_admin
(
	username	varchar(50) not null
	, password	varchar(255) not null
	, primary key (username)
);
```

When you are adding a user to the guestbook_admin table, it would be best to encrypt the password. The easiest way to do this is by using a built-in MySQL password encryption function like sha1(), as follows:

```
insert into guestbook_admin (username, password)
values ('jay', sha1('rules'));
```

After you've run this command, the actual value stored in the password column is caa155adf81fdd29ab4b21a1a47927fb0295eb53. When you need to find out whether a user knows the password, you can use the sha1 function again:

```
select * from guestbook_admin where
username = 'jay' and
password = sha1('rules');
```

> From the latest MySQL documentation: "Note: The PASSWORD() function is used by the authentication system in MySQL Server, you should NOT use it in your own applications. For that purpose, use MD5() or SHA1() instead. Also see RFC-2195 for more information about handling passwords and authentication securely in your application."

## Code Overview

In this, the first of your applications, you need to look at the architecture you will use in constructing your applications. The applications on the CD have been constructed so that they are as reusable and portable as possible.

To start with, the CD contains a folder named book, which should be copied to the document root directory of your Web server. On Apache this folder is usually named htdocs by default. The book folder contains all the applications documented in this book.

Within the book folder is a series of folders, one folder for each of the applications presented here, one labeled classes, and one labeled functions. For the purpose of this application we will concern ourselves with the basic.php file in the functions folder; this file defines some functions that you will use in a variety of applications. We'll discuss the functions in basic.php that are used in Guestbook 2003 in the section entitled “Code Breakdown.”

The code that is relevant only to Guestbook 2003 is kept in the guestbook2k folder. Here, startup code that needs to be run at the beginning of each page is run by the header.php file. The header.php file contains, in turn, two other files: globals.php and functions.php. This is a structure that we'll be using through all the examples in the book. The globals.php file is where you create global variables and define constants for use in the application. The functions that will need to be addressed across a number of pages are kept in the functions.php file. We will also explain these functions in detail in the “Code Breakdown” section.

The pages that are called from the browser are named intuitively: view.php, sign.php, and edit.php. The other page of the application is confirm_delete.php, which is called only by edit.php and not by the user directly.

You may find the view.php, sign.php, and edit.php files surprisingly short. They only contain a couple of dozen lines of code each. This is because just about everything is written in reusable functions.

So once again the important thing is to understand the functions kept in /book/functions/basic.php and /book/guestbook2k/functions.php, as well as the startup code run in /book/guestbook2k/header.php.

## Code Breakdown

As mentioned in the previous section, the vast majority of the work of this application is done in functions, and these functions are kept in files that will be included in the pages called from the browser.

### From functions/basic.php

The following are the main functions from basic.php that we'll be using in this application. We'll cover other functions later on, and they're all briefly documented in Appendix F. The functions are grouped by their general purpose, and that's the order in which we'll go through them.

### GENERAL UTILITY FUNCTIONS (OR, “IF ONLY PHP HAD A FUNCTION TO . . .”)

Here are some utility functions that we find helpful:

ARRAY_KEY_VALUE() With the advent of the new “superglobal” PHP variables like $_POST, you'll be getting most of the values you use in your code from associative arrays ($_GET, $_POST, and so on). The trouble is that if a particular key hasn't been
