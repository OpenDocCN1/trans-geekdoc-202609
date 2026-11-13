```
(
  user_id  integer not null auto_increment
  , username  varchar(20) not null
  , password  varchar(16) not null
  , name  varchar(50) not null
  , email  varchar(255) null
  , primary key (user_id)
  -- , unique (username)
)
type=InnoDB
;
```

# Code Overview

At this point, we assume that you are getting comfortable with the way the applications in this book have been constructed. Even with the simple safe_mysql_query() function in the guestbook example, you saw the usefulness of having a standard way of working with PHP’s native MySQL routines. The built-in routines will let you do what you need to do, no question. But in the course of using them, you may find that you’re writing the same kind of code multiple times, a sure signal that some higher-level functions are called for. Also, should you ever want to port your code to a different DBMS for some crazy reason, like because you’re being paid to, going through your code and converting those MySQL-specific functions to some other system can be a big pain.

If you’ve ever done any work with Perl, you may be familiar with the DBI library. It provides a standard interface to multiple database systems. You may have also used Comprehensive Perl Archive Network (CPAN), the big code library where you can find all sorts of previously invented wheels. The same kinds of benefits are available with PHP, thanks to the good people who have built—and are building even now—PEAR.

To quote from the PEAR Manifest (http://pear.php.net/manual/en/ introduction.php): “PEAR is short for ‘PHP Extension and Application Repository’ and is pronounced just like the fruit.” PEAR has several facets. It’s a library of PHP code that solves many common problems encountered by Web developers. It’s also a means of packaging and distributing code, to make it simpler to install code from that library, and to encourage people to share their own code. The best place to find out more is at the Web site: http://pear.php.net. Here you’ll find the code, the main PEAR documentation, mailing lists, and other useful information.

PEAR is very much a moving target, undergoing constant improvement and extension, and it has the rough edges that brings. So by way of introduction, we’ll focus on one of the most widely used—and most completely documented—classes, the DB class. It’s one of the core PEAR classes that are automatically distributed and installed as part of PHP (at least, as of this writing). Like Perl’s DBI class, DB