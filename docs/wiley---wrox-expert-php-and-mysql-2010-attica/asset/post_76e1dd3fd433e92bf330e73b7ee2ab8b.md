
This chapter detailed a number of great tools that you can use to analyze the status of and debug MySQL. You have many different ways to debug MySQL — many more than could fit in this book — but this chapter should point you in the right direction to diagnose any MySQL problem.

Understanding and knowing the `EXPLAIN` output and PHP profiling output are essential skills for an expert PHP and MySQL developer.

Using these skills and the other skills outlined in this book, you can create finely tuned and robust applications with PHP and MySQL.

## INDEX

[ ] (square brackets) in regular expressions, 50

### A
abstract keyword, 3
abstract methods, 353
access permissions, views, 223–224
aCFB encryption, 504
ACID, 238
  atomicity
    non-transactional tables, 238–239
    transactional tables, 239–240
  consistency, 240–241
  durability, 247–250
  foreign keys, 38
  isolation, 242
    levels, 247
    READ_COMMITTED, 244–245
    READ_UNCOMMITTED, 245–246
    REPEATABLE_READ, 242–244
    replication, 247
    SERIALIZABLE, 246–247
  relational integrity, 35
ACLs (Access Control Lists), 473–474
Aksyonoff, Andrew, 369
algorithms, UDFs, 277
aliases, MySQL, 22
ALTER ROUTINE privilege, 230
alternation in regular expressions, 51
AND operator (MySQL), 33
anonymous functions, 78
ANSI control codes, 523
APC (Alternative PHP Cache), 132
  configuration, 132–133
  installation, 132–133
  serialization, 135
  when to use, 138
appending, memcached, 166–167
application sample view, 67–69

Archive storage engine, 109–110
args key, 544
arguments
  checking for string, 285
  functions, in extensions, 331–334
  type, checking, 274
  UDFs, 192
ArrayAccess interface, 77–78
arrays
  accessing, 347–349
  associative, 70, 348
  building, 347–349
  tracking unlinks, 77
associative arrays, 70, 348
atomicity (ACID)
  non-transactional tables, 238–239
  transactional tables, 239–240
auditing, 500–501
authorization, memcached, 140
autoconf, 292
  macros, 292
automation attacks, 514–515

### B
b-tree indexes, 365
back-references in regular expressions, 53
basic authentication, 461–463
Beanstalk, 442
bi-directional encoding
  mcrypt extension, 503–505
  XOR Cipher, 501–503
binary, definition, 327
binary logging, 500
  file analysis, 256–257
  replication and, 251
bindings (SOAP), 537–538
bison, 308
Blackhole storage engine, 108–109

### C
  blocking sockets, 346
BlogEntry class, polymorphism, 2
Boolean query syntax, 385
boundary characters in regular expressions, 49
breaking replication, 261–262
breakpoints in debugging, 302–303
built-in functions, 335–336
built-in rewrite maps, 451
bytecode caching, 132
C
  C++ and, 308
  UDFs, 273
  Zend engine, 308
C++
  C and, 308
  UDFs, 273
C-libraries, UDFs and, 272
cache replication, 145
caching, 180–188
  bytecode, 132
  cache locality, 171–173
  cache replication, 145
  cache status, checking, 135–138
  catalogue table, 142
  deterministic, 144
  file system, 145
  introduction, 131
  LRU (Least Recently Used), 140
  memcached, 138–140
    authorization, 140
    consistent hashing, 140
    replication, 140
  non-deterministic, 144
  opcode, 132
  page, 145
  partial page, 145
  proactive, 145
  read-through, 141, 216–219
  session, 145
  state, 145
  strategies, 144–145
  user, enabling, 133
  write-back, 142
  write-through caching, 141
_call( ) magic method, 11
callback functions, lambda functions, 78
  callback parameter, 81
callbacks, read-through caching callback, 165
calling methods, 356
_callStatic( ) magic method, 11
CAPTCHA (Complete Automated Public Turing test to tell Computers and Humans Apart), 514
cardinality, 550–551
CAS (check and set), 174–176, 201–202
case sensitivity, joins (MySQL), 26–27
catalogue table, 142
CBC (Cipher Block Chaining) encryption, 504
CentOS, memcached installation, 145–146
CFB (Cipher-Feedback Mode) encryption, 504
character classes (MySQL), 60
character sets, 486–487
  collations, 487–488
ciphers, 502
C10K problem, 132
class entry, 350
class key, 544
__CLASS__ magic constant, 8
classes
  CodeGen_PECL, example, 320–321
  command-line scripts, 521–522
  constants, 354
  definition, 350–351
  EmailValidator, 56–57
  FileLog, 9–10
  ForumTopic, 4
  inheritance, 350–351
  interfaces
    implementing, 7
    inheritance, 7
  LoggingProxy, 13–14
  methods, magic, 9–11
  MultitonExample, 12–13
  namespaces, 350–351
  Node, defining, 3–4
  Pagination, 75–76
  SingletonExample, 11–12
  variables, 3
CLI (Command Line Interface), 312
  command-line scripts, 517
clients
  memcached, 153
  PECL/memcached, 162–163
_clone( ) magic method, 11
clone keyword, 12
closures, 81–83
code, critical section, 360

CodeGen_PECL, 314
  classes, example, 320–321
  constants, defining, 318
  dependencies, 338
  extensions, as XML documents, 314
  functions, defining, 316–317
  globals, 318–319
  INI directives, 318–319
  interfaces, 321
  methods, defining, 320
  objects, defining, 319
  properties, defining, 320
  XML files, creating, 314–316
Cole, Jeremy, 483
collations of character sets, 487–488
colored text, 523–524
column privileges, 490–491
command-line scripts
  classes, 521–522
  CLI, 517
  color, 523–524
  creating, 517–524
  cron jobs, 522–523
  input
    prompting for, 520–521
    reading, 518–520
  shebang, 518
commands
  CREATE USER, 496
  DROP USER, 497–498
  GRANT, 268, 497
  mysql_secure_installation, 494
  replication, 261
  REVOKE, 268, 497
  SHOW, 491–492
  SHOW TABLE STATUS, 92
  SHOW ENGINES, 89–90
comments
  functions, 330
  regular expressions, 49, 54
COMMIT command, implied, 250
complex joins (MySQL), 27
complex subqueries (MySQL), 47–49
compressed tables, MyISAM storage engine, 96
concrete decorators, 16
CONDITION clause, 229–230
conditional rewrite rules, 447–450
  exclamation point, 448
  testing for patterns, 449
  testing to check file or path, 449

conditions, 229–230
config.m4 file, 310
config.w32 file, 310
consistency (ACID), 240–241
consistent hashing, 140
constants, 354
  CodeGen_PECL, defining, 318
  magic, 8–9
  MINIT function, 357
constraints, 35
  NOT NULL, 35–36
  UNIQUE KEY, 37
  UNSIGNED, 36
constructors, copy constructors, 329
contexts, 343–344
cookies, 471–473
copy constructor, 329
correlated subqueries (MySQL), 46
count( ) method, 73
countable interface, 73–74
CREATE ROUTINE privilege, 230
CREATE USER command, 496
CREATE VIEW privilege, 223
CREDITS file, 310
critical section, 360
cron jobs, 522–523
crontab, 522
CSRF attack, 511–514
CSV (Comma Separated Value), 112
CSV storage engine, 112
CTR (Counter Mode) encryption, 504
cURL, 528–529
current( ) method, 72
cursors, 229

### D
\d shorthand character, 50
Danga Interactive, 139
data capture
  MySQL, 61
  regular expressions, 53–54
data sources, Sphinx, 376–379
data storage, disk, 275
data types
  ENUM, 36–37
  function definitions file, 312–313
  SET, 36–37
  data warehousing
  InfiniDB, 124
  Infobright, 125
views, 225
databases, user authentication, 458
Day, Eric, 412
db_bytes( ) function, 283, 287
db_bytes_deinit( ) function, 284
db_bytes_init( ) function, 284
DealNews, 402
debug back-trace, 544
debuggers
  gdb, 273
  attaching to running process, 301-302
  Microsoft debugger, 273
  MySQL and, 564-565
  UDFs, 273
debugging, 543
  breakpoints, 302-303
  debug back-trace, 544
  literal values and, 304
MySQL
  commands, 564
  error log, 560-561
  PROCESSLIST, 562-564
  slow query log, 561-562
stack traces, creating, 544-545
stepping through code, 302-303
UDFs, 300-301
DECLARE clause, 229
decorating objects, 14
decorator pattern, 14-16
decrementing, memcached, 168-169
default users, new installation, 494
defining, interfaces, 7
delete( ) method, 168
DELETE command, triggers, 235-236
DELETE statement, 556-558
delta indexes, 389-394
dependencies, CodeGen_PECL, 338
dependent queries, 45
derived tables (MySQL), 46-47
deriving interfaces, 7
design patterns
  decorator, 14-16
  façade, 13-14
  multiton, 11-13
  observer, 18-19
proxy, 13-14
publisher/subscriber, 18-19
singleton, 11-13
destructors, 5
deterministic cache, 144
Digest Authentication, 507
digest authentication, 463-466
Digg, 402
_DIR_ magic constant, 9
directives, rewrite rules, 444
  RewriteCond, 447
directories
  ext, 308
  main, 308
  project directory organization, 281-283
  Zend, 308
disk space, InnoDB storage engine, 99-100
disk storage, 275
distributed indexes, 373
DML statements, Blackhole storage engine, 108
drivers, MySQL, 88
Drizzle, 124, 126
DROP USER command, 497-498
dumb server, 140
durability (ACID), 247-250

### E
eAccelerator, 132
  configuration, 133-134
  installation, 133-134
  opcode, optimizer, 134
  serialization, 135
  when to use, 138
eBay Memory storage engine, 127
ECB (Electronic Code Book) encryption, 503
elements, unsetting, 77
EmailValidator class, 56-57
encoding
  bi-directional
    mcrypt extension, 503–505
      XOR Cipher, 501–503
  single-directional, 505-506
encryption
  aCFB, 504
  CBC, 504
  CFB, 504
  CTR, 504
