```
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
```