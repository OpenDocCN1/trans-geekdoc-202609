
For each column, its name implies the value to be stored in that column. For one—`language`—I’ve used a MySQL keyword, simply to demonstrate how that can be done. The fix is to surround the column’s name in backticks so that MySQL doesn’t confuse this column’s name with the keyword “language.”

**8.** Populate the `languages` table:

```sql
INSERT INTO languages (lang, lang_eng) VALUES
('English', 'English'),
('Português', 'Portuguese'),
('Français', 'French'),
('Norsk', 'Norwegian'),
('Romanian', 'Romanian'),
('![Image](graphics/greek.jpg)', 'Greek'),
('Deutsch', 'German'),
('Srpski', 'Serbian'),
('![Image](graphics/japanese.jpg)', 'Japanese'),
('Nederlands', 'Dutch');
```

This is just a handful of the languages the site will represent thanks to some assistance provided me (see the sidebar “[A Note on Translations](#ch17.html#ch17sb02)”). For each, the native and English word for that language is stored ![Image](graphics/circle-k.jpg).

![Image](graphics/17_figure_11_k.jpg)

![Image](graphics/circle-k.jpg)The populated `languages` table, with each language written in its own alphabet.

**9.** Populate the `users` table ![Image](graphics/circle-l.jpg):

```sql
INSERT INTO users (lang_id, time_zone, username, pass, email) VALUES
(1, 'America/New_York', 'troutster', SHA1('password'), 'email@example.com'),
(7, 'Europe/Berlin', 'Ute', SHA1('pa24word'), 'email1@example.com'),
(4, 'Europe/Oslo', 'Silje', SHA1('2kll13'), 'email2@example.com'),
(2, 'America/Sao_Paulo', 'João', SHA1('fJDLN34'), 'email3@example.com'),
(1, 'Pacific/Auckland', 'kiwi', SHA1('conchord'), 'kiwi@example.org');
```

![Image](graphics/17_figure_12_l.jpg)

![Image](graphics/circle-l.jpg)A few users are added manually, as there is no registration process in this site (but see [Chapter 18](#ch18.html#ch18), “[Example—User Registration](#ch18.html#ch18),” for that).

Because the PHP scripts will show the users associated with posts, a couple of users are necessary. A language and a time zone are associated with each (see [Chapter 6](#ch06.html#ch06) for more on time zones in MySQL). Each user’s password will be encrypted with the `SHA1()` function.

**10.** Populate the `words` table:

```sql
INSERT INTO words VALUES
(NULL, 1, 'PHP and MySQL for Dynamic Web Sites: The Forum!', '<p>Welcome to our site.... please use the links above... blah, blah, blah.</p>\r\n <p>Welcome to our site....please use the links above...blah, blah, blah.</p>', 'Home', 'Forum Home', 'Language', 'Register', 'Login', 'Logout', 'New Thread', 'Subject', 'Body', 'Submit', 'Posted on', 'Posted by', 'Replies', 'Latest Reply', 'Post a Reply');
```

These are the words associated with each term in English. The record has a `lang_id` of 1, which matches the `lang_id` for English in the `languages` table. The SQL to insert words for other languages into this table is available from the book’s supporting Web site.

***

Tip

This chapter doesn’t go through the steps for creating the `mysqli_connect.php` page, which connects to the database. Instead, just copy the one from [Chapter 9](#ch09.html#ch09), “[Using PHP with MySQL](#ch09.html#ch09).” Then change the parameters in the script to use a valid username/password/hostname combination to connect to the `forum2` database.

***

Tip

As a reminder, the foreign key in one table should be of the exact same type and size as the matching primary key in another table.

***

### A Note on Translations

Several readers around the world were kind enough to provide me with translations of key words, names, message subjects, and message bodies. For their help, I’d like to extend my sincerest thanks to (in no particular order): Angelo (Portuguese); Iris (German); Johan (Norwegian); Gabi (Romanian); Darko (Serbian); Emmanuel and Jean-François (French); Andreas and Simeon (Greek); Darius (Filipino/Tagalog); Olaf (Dutch); and Tsutomu (Japanese).

If you know one of these languages, you may see linguistic mistakes made in this text or in the corresponding images. If so, it’s almost certainly my fault, having miscommunicated the words I needed translated or improperly entered the responses into the database. I apologize in advance for any such mistakes but hope you’ll focus more on the database, the code, and the functionality. My thanks, again, to those who helped!

***

### Writing the Templates

This example, like any site containing lots of pages, will make use of a template to separate out the bulk of the presentation from the logic. Following the instructions laid out in [Chapter 3](#ch03.html#ch03), “[Creating Dynamic Web Sites](#ch03.html#ch03),” a header file and a footer file will store most of the HTML code. Each PHP script will then include these files to make a complete HTML page ![Image](graphics/circle-a.jpg). But this example is a little more complicated.

![Image](graphics/17_figure_13_a.jpg)

![Image](graphics/circle-a.jpg)The basic layout and appearance of the site.

One of the goals of this site is to serve users in many different languages. Accomplishing that involves not just letting them *post messages* in their native language but making sure they can use the *whole site* in their native language as well. This means that the page title, the navigation links, the captions, the prompts, and even the menus need to appear in their language ![Image](graphics/circle-b.jpg).

![Image](graphics/17_figure_14_b.jpg)

![Image](graphics/circle-b.jpg)The home page viewed in French (compare with ![Image](graphics/graycircle-a.jpg)).

The instructions for making the database show how this is accomplished: by storing translations of all key words in a table. The header file, therefore, needs to pull out all these key words so that they can be used as needed. Secondarily, this header file will also show different links based upon whether the user is logged in or not. Adding just one more little twist: if the user is on the forum page, viewing all the threads in a language, the user will also be given the option to post a new thread ![Image](graphics/circle-c.jpg).

![Image](graphics/17_figure_15_c.jpg)

![Image](graphics/circle-c.jpg)The same home page as in ![Image](graphics/graycircle-a.jpg), but with an added link allowing the user to start a new thread.

The template itself uses CSS for some formatting (there’s not much to it, really). You can download all these files from the book’s supporting Web site (**[www.LarryUllman.com](http://www.LarryUllman.com)**).

#### To make the template

**1.** Begin a new document in your text editor or IDE, to be named `header.html` (**[Script 17.1](#ch17.html#ch17ex01)**):

```php
<?php # Script 17.1 - header.html

header ('Content-Type: text/html; charset=UTF-8');
```

As this script will need to do a fair amount of data validation and retrieval, it starts with a PHP block. The script also indicates to the Web browser its encoding—UTF-8, using the `header()` function. The idea of setting the encoding via a `header()` function call was mentioned in a tip in [Chapter 11](#ch11.html#ch11), “[Web Application Development](#ch11.html#ch11).”

**2.** Start a session:

```php
$_SESSION['user_id'] = 1;
$_SESSION['user_tz'] = 'America/New_York';
// $_SESSION = array();
```

To track users after they log in, the site will use sessions. Since the site doesn’t have registration and login functionality in this chapter, two lines can virtually log in the user. Ordinarily, both values would come from a database, but they’ll be set here for testing purposes. To virtually log the user out, uncomment the third line.

**3.** Include the database connection:

```php
require ('../mysqli_connect.php');
```

As with many other examples in this book, the assumption is that the `mysqli_connect.php` script is stored in the directory above the current one, outside of the Web root. If that won’t be the case for you, change this code accordingly.
