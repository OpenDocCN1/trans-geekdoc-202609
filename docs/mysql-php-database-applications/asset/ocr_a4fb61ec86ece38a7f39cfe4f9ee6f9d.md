![](bbox=[0.172, 0.091, 0.839, 0.463])

Figure 8-6: Reporting a duplicate entry

# # Designing the Database

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
)
```