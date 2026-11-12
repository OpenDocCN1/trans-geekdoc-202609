do not support transactions. They are ISAM, which is an older version of MyISAM and one that may not be present when MySQL version 5.0 ships; and HEAP, which is a highly optimized form stored strictly in memory (and not on the hard drive) that’s useful for temporary data.

However, MySQL supports other formats that *do* allow for transactions. You are also free to mix table types within a single database. These transaction-supporting formats are InnoDB and BerkeleyDB:

+   **InnoDB** is a separate product from MySQL, which was built primarily to work along with MySQL. You can find out more about InnoDB, a free (GNU Public License) and extremely powerful database system at www.innodb.com and at www.mysql.com/doc/en/InnoDB.html.

+   **Berkeley DB** (BDB for short) is also a separate database engine, but was built specifically for MySQL by Sleepycat Software. BDB is free and has its own licensing program. You can find out more about BDB at www.sleepycat.com and in the MySQL documentation at www.mysql.com/doc/en/BDB.html.

# Building a Forum or Message Board

Many Web sites these days include special forum areas. In years past, you either had to hope that your Web host had a forum or had to provide a link to a third-party forum site.

Although linking to a third-party forum site is still a good idea if you’re anticipating heavy forum usage, you can also store your own forums in your MySQL databases. (The forum messages themselves are stored as memo fields.)

Here are some things you can include in your forum:

+   Forms for filling out the messages.

+   .php files that sort the messages by thread and print them in fancy ways.

+   The ability for users to enter special symbols like smilies. You can save the smilies as their actual text as in :-) and then parse through the messages to display them, replacing the text :-) with an <img> HTML tag pointing to a graphics file containing the smilie picture.

+   A username and password system.

![](bbox=[0.137, 0.839, 0.234, 0.921])

If you want to see a good example of a forum written in MySQL with Perl, running on Apache, take a look at the SlashDot site, http://www.slashdot.org. You can read about their code (which is open source and freely available) at http://slashcode.com/faq.shtml#Slashcodecom0.