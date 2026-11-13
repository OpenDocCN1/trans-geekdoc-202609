
(In these lines, up to 'flush privileges', we are setting up basic permissions for the database, where 'nobody' is the account used by the NetSloth site itself, and 'content_admin' is an example of an account for an administrator of the content management application itself.)

```
delete from mysql.user where user = 'content_admin';
delete from mysql.db where Db = 'netsloth';
delete from mysql.tables_priv where Db = 'netsloth';
grant select on netsloth.*
to nobody@localhost
identified by 'nobody'
;
grant reload on *.*
to content_admin@localhost identified by 'supersecret'
;
grant delete, insert, select, update, create
on netsloth.*
to content_admin@localhost
with grant option
;
grant delete, insert, select, update, create on mysql.user to
content_admin@localhost ;
grant delete, insert, select, update, create on mysql.db to
content_admin@localhost ;
grant delete, insert, select, update, create on mysql.columns_priv
to content_admin@localhost ;
grant delete, insert, select, update, create on mysql.tables_priv to
content_admin@localhost ;
flush privileges;
```

```
drop table if exists stage_seq;
create table stage_seq
(
 id int not null auto_increment
, primary key (id)
)
type=InnoDB
;
drop table if exists stages;
create table stages
(
 stage_id integer not null auto_increment
, stage varchar(20) not null
, stage_dsc text null
, stage_table   varchar(32) not null
, primary key (stage_id)
)
type=InnoDB
;
```

```
drop table if exists stories;
create table stories
(
    story_id    integer not null auto_increment
    , stage_id  integer not null
    , publish_dt date null
    , headline  varchar(255) null
    , subtitle  varchar(255) null
    , byline_prefix  varchar(20) null
    , summary   text null
    , body      text null
    , primary key (story_id)
    , index (stage_id)
)
type=InnoDB
;
```

```
drop table if exists story_author_map;
create table story_author_map
(
    story_id  integer not null
    , author_id  integer not null
    , primary key (story_id)
    , index (author_id)
    , foreign key (story_id) references stories (story_id) on delete
    cascade
    , foreign key (author_id) references authors (author_id) on delete
    cascade
)
type=InnoDB
;
```

```
drop table if exists story_seq;
create table story_seq
(
    id int not null auto_increment
    , primary key (id)
)
type=InnoDB
;
```

```
drop table if exists story_versions;
create table story_versions
(
    story_id integer not null
    , modify_dt timestamp
    , modify_by varchar(20) not null
    , stage_id integer not null
    , publish_dt date null
    , headline varchar(255) null
    , subtitle varchar(255) null
    , byline_prefix varchar(20) null
    , summary text null
    , body text null
    , primary key (story_id, modify_dt)
    , foreign key (story_id) references stories (story_id) on delete
cascade
)
type=InnoDB
;
```

```
drop table if exists user_seq;
create table user_seq
(
    id int not null auto_increment
    , primary key (id)
)
type=InnoDB
;
```

```
drop table if exists user_stage_map;
create table user_stage_map
(
    user_id integer not null
    , stage_id integer not null
    , primary key (user_id,stage_id)
    , index (stage_id,user_id)
    , foreign key (user_id) references users (user_id) on delete cascade
    , foreign key (stage_id) references stages (stage_id) on delete
cascade
)
type=InnoDB
;
```

```
drop table if exists users;
create table users
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

## Code Overview

At this point, we assume that you are getting comfortable with the way the applications in this book have been constructed. Even with the simple safe_mysql_query() function in the guestbook example, you saw the usefulness of having a standard way of working with PHP's native MySQL routines. The built-in routines will let you do what you need to do, no question. But in the course of using them, you may find that you're writing the same kind of code multiple times, a sure signal that some higher-level functions are called for. Also, should you ever want to port your code to a different DBMS for some crazy reason, like because you're being paid to, going through your code and converting those MySQL-specific functions to some other system can be a big pain.

If you've ever done any work with Perl, you may be familiar with the DBI library. It provides a standard interface to multiple database systems. You may have also used Comprehensive Perl Archive Network (CPAN), the big code library where you can find all sorts of previously invented wheels. The same kinds of benefits are available with PHP, thanks to the good people who have built—and are building even now—PEAR.

To quote from the PEAR Manifest (http://pear.php.net/manual/en/introduction.php): "PEAR is short for 'PHP Extension and Application Repository' and is pronounced just like the fruit." PEAR has several facets. It's a library of PHP code that solves many common problems encountered by Web developers. It's also a means of packaging and distributing code, to make it simpler to install code from that library, and to encourage people to share their own code. The best place to find out more is at the Web site: http://pear.php.net. Here you'll find the code, the main PEAR documentation, mailing lists, and other useful information.

PEAR is very much a moving target, undergoing constant improvement and extension, and it has the rough edges that brings. So by way of introduction, we'll focus on one of the most widely used—and most completely documented—classes, the DB class. It's one of the core PEAR classes that are automatically distributed and installed as part of PHP (at least, as of this writing). Like Perl's DBI class, DB provides a standard interface to multiple database systems. It makes it easy to do the kinds of things you'll want to do to get data out of a database (like building an associative array from the results of a query) and to put data into a database (like handling those pesky quote marks).

As you work through, less and less of the code should require explanation. Thus, our descriptions of the code will deal only with those parts that are really new or tricky.

Here, most of the newer looking code will come from assigning the privileges discussed in the previous section. The application sends queries that you haven't used before.

## Code Breakdown

Once again, the code in this application will make heavy use of the functions in the /functions folder. A lot of the code presented here will make calls to those functions. The great thing about functions is that they become part of your library of code that you can re-use for other purposes.

## Functions from /dsn

The PEAR DB library takes a connection string that will look somewhat familiar if you've used Perl's DBI class, and that is easy to figure out in any case. It typically looks something like this:

```
phptype://username:password@hostspec/database
```

where *hostspec* might be replaced with the port number and name of the local-host. The routine that accepts connections also accepts an associative array with all the parts spelled out as key/value pairs, so that's what we'll use.

Rather than store usernames and passwords in the code of the example, as we have done up until now, we've moved the connection information for the database to a function in a separate directory, outside the document root of the Apache server. This provides a small amount of extra security – though if you're on a shared server, this information is still vulnerable. But at least moving it out of the Web-server document root means that no one can download the file as a Web page.

In our setup, the /dsn directory is parallel to the /htdocs directory. In there is one file, db_dsnlist.php, defining one function, db_dsnlist():

```
function db_dsnlist()
{
    static $_defaults = array(
        'application' => 'default'
    );
    static $_simple = array(
```
