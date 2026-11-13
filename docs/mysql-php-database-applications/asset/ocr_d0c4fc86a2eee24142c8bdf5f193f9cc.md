# Listing 13-1 (Continued)

```
type=InnoDB
:
drop table if exists problems;
create table problems
(
    problem_id    integer not null auto_increment
  , customer_id   integer not null
  , problem_code  char(8) not null
  , status_id     tinyint null
  , staff_id      integer null
  , summary       text
  , problem       text
  , entered_by    varchar(20) null
  , source_id     tinyint null
  , entry_dt      datetime
  , modify_dt     timestamp
  , last_public_entry_id int null
  , last_entry_id int null
)
, primary key (problem_id)
, key (customer_id)
, foreign key (customer_id) references customers (customer_id) on
delete cascade
, key (status_id)
, foreign key (status_id) references status (status_id) on delete
set null
, key (source_id)
, foreign key (source_id) references sources (source_id) on delete
set null
, key (staff_id)
, foreign key (staff_id) references staff (staff_id) on delete set
null
, unique (problem_code)
)
type=InnoDB
;
drop table if exists problem_seq;
create table problem_seq
(
  id int not null auto_increment
, primary key (id)
)
type=InnoDB
```