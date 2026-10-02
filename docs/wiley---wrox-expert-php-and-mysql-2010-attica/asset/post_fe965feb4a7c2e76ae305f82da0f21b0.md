
## Variables in PHP Extensions 321
- Setting and Testing zvals 323
- Reading and Comparing zvals 324
- Dealing with Strings as zvals 326
- Advanced Memory Management 328

## Using Functions in Extensions 329
- Basic Definitions 329
- Using Arguments 331
- Defining Argument Information 334
- Returning Values 334
- Built-In Functions 335
- Creating and Consuming PHP API Functions 336
- More Notes and Creating Helper Functions 339

## Input/Output 340
- Standard Out 340
- Files and Streams 341
- Networking 344
- Errors and Warnings 346

## Arrays and Hash Tables 347
- Building and Accessing Arrays 347
- Accessing and Modifying Hash Tables 349

## Objects and Interfaces 349
- Creating a Class 350
- Interacting with Objects 355

## Constants, INI Directives, and Globals 357
- Constants 357
- Globals and INI Directives 358

## Describing an Extension 361
- Printing a Description 361
- Building a Table 362
- Specifying a Logo 362

## Summary 364

## CHAPTER 9: FULL-TEXT SEARCHING 365
### MySQL FULLTEXT Indexes 365
- Using MySQL FULLTEXT Indexes 367
- MySQL FULLTEXT Index Issues 368

### A Better Solution: The Sphinx Full-Text Search Engine 369
- Sphinx Configuration and Installation 370
- Sphinx.conf Settings 371
- Starting Sphinx 382
- Searching Sphinx 383
- Delta Indexes 389
- Merging Indexes 394
- Developing Applications That Use SPHINX 395
- Sphinx and PHP 395
- Summary 399

## CHAPTER 10: MULTI-TASKING IN PHP AND MYSQL 401
### Gearman 401
### What Is Gearman? 402
- Installing and Running Gearman 404
- Using the Gearman MySQL UDFs 407
- PHP and Gearman 409
### Narada: A Search Engine Application 412
- Obtaining Narada 413
- Narada Components 413
- Database Tables for the Search Engine Application 415
- Sphinx Setup 416
- Gearman Workers 429
- Index Page 435
- One Other Tidbit of Code 438
- The Big Picture 439
- Running Narada 439
- To-Do List for Narada 441
- Other Job Server Systems 442
### Summary 442

## CHAPTER 11: REWRITE RULES 443
### Using Rewrite Rules 444
- Understanding the Purpose and Structure of Rewrite Rules 444
- Understanding and Controlling Rewrite Rule Flow 445
- Conditional Rules 447
- Logging and Optimization 450
### Rewrite Maps 451
- Built-In Maps 451
- Random and Text Lookups 452
- Using PHP and MySQL 452
### Summary 456

## CHAPTER 12: USER AUTHENTICATION 457
### Designing the Database 458
### HTTP-Based Authentication 460
- Basic Authentication 461
- Digest Authentication 463
### Pure PHP Authentication 466
- Using PHP Sessions 467
- Building Secure Cookies 471
### Access Control Lists 473
### Summary 475

## CHAPTER 13: UNDERSTANDING THE INFORMATION_SCHEMA 477
### Using the INFORMATION_SCHEMA 478
### Table Objects Tables 479
### Other Database Objects Tables 481
### MySQL Status Tables 482
- PROCESSLIST (5.1) 482
- SESSION_STATUS/GLOBAL_STATUS (5.1) 484
- SESSION_VARIABLES/GLOBAL_VARIABLES (5.1) 485
### MySQL Meta Data Tables 486
- CHARACTER_SETS 486
- COLLATIONS 487
- COLLATION_CHARACTER_SET_APPLICABILITY 488
### MySQL ACL Permissions Tables 488
- USER_PRIVILEGES 488
- SCHEMA_PRIVILEGES 489
- TABLE_PRIVILEGES 489
- COLUMN_PRIVILEGES 490
### INFORMATION_SCHEMA Extensions 491
### SHOW Cross Reference 491
### Summary 492

## CHAPTER 14: SECURITY 493
### Hardening Your MySQL Server 493
- Installation Defaults 494
- Operating System Security 495
- MySQL Security Permissions 495
- Additional Database Security 500
- Auditing 500
### Encoding Data 501
- Bi-directional Encoding 501
- Single-Directional Encoding 505
### PHP Security Recipes 506
- Protecting against SQL Injection 506
- Protecting against Replay Attacks 507
- Protecting against XSS 509
- Protecting against CSRF 511
- Automation Attacks 514
### Summary 516

## CHAPTER 15: COMMAND-LINE AND WEB SERVICES 517
### Creating Command-Line Scripts 517
- Reading Command-Line Input 518
- Prompting for Input 520
- Completed Classes 521
- Setting Up Cron Jobs 522
- Bonus: Output in Color 523
### Creating Web Services 524
- RESTful Web Services 524
- SOAP Web Services 532
- Getting Started with the SOAP Library 533
### Summary 541

## CHAPTER 16: OPTIMIZATION AND DEBUGGING 543
### Debugging PHP 543
- Creating Stack Traces 544
### Optimizing Queries 545
- Reducing SQL 545
- Identifying SQL Statements 545
- Optimizing SELECT 546
- Optimizing UPDATE 556
- Optimizing DELETE 556
- Optimizing INSERT 558
- Optimizing REPLACE 558
- INSERT ... ON DUPLICATE KEY UPDATE 558
### Debugging MySQL 560
- Error Log 560
- Slow Query Log 561
- Processlist 562
- Other Commands 564
- Using a Debugger with MySQL 564
### Summary 565

## INDEX 567

## INTRODUCTION

**PHP AND MYSQL HAVE BEEN USED FOR YEARS** to power some of the most popular websites and open source applications anywhere. It's no secret that the Web has evolved. Modern web sites are expected to be dynamic and the user count for popular sites is now measured in the millions.

This book examines some of the technologies and techniques needed to make robust and scalable applications perform in today's high-demand world. Early chapters focus on essential concepts. For example:
- Object Oriented Programming
- Design Patterns
- Advanced MySQL queries

Later chapters get down into the trenches and focus on ways to improve application performance through caching with memcached (and others), full-text search with Sphinx, and multitasking with Gearman.

Today's PHP programmer can't be afraid to get their hands dirty. By the time this book is done you will be well on your way to extending PHP and MySQL using C. In PHP we cover extension writing. In MySQL we cover User Defined Functions.

The book focuses on critical skills and best practices in the areas of security, optimization, and software architecture. The examples are written with the assumption that you already know the basics so common code is occasionally stripped out to make the examples more readable and focused. And as such you will see examples in the book that don't check the return value of a function for errors. Don't put code like that onto your live server; fix it first! You know how.

This book will give you the tools that you need to write mission critical applications with PHP and MySQL — including high-traffic ones. The hope is that you can use some of the skills covered in this book to create your own open source projects and eventually contribute to the PHP and MySQL communities. Or perhaps you just use this book to help you create the next PHP and MySQL powered success story

## WHO THIS BOOK IS FOR

This book is designed to cover some of the most advanced topics in the PHP and MySQL worlds. It is intended for advanced PHP and MySQL users who have significant experience and have already worked on several projects. Some people who should read this book include:
- Programmers creating mission-critical applications
- Programmers creating websites or applications that need to support thousands (if not millions) of users
- Programmers who create applications that need to store and access large amounts of data or require lots of processing
- Programmers who just find things like design patterns, PHP extensions, and MySQL UDFs interesting and who want to learn more

This book assumes that you also have a working knowledge of C as well and that you have at least compiled a C program or two (PHP and MySQL count). PHP extensions and MySQL User Defined Functions are both written in C.

This book starts off easy but quickly dives into many advanced topics. It's all right if you're not already an advanced PHP, MySQL, and C programmer but you'll probably want to keep some other Wrox books handy for reference.

## WHAT THIS BOOK COVERS

PHP and MySQL are both well established with many libraries and extensions available. It would be impossible to cover every expert topic in a single book. Likewise, this book doesn't try to cover beginner level topics at all. The authors did, however, hand pick topics that they think are essential for any expert PHP and MySQL programmer to know.

The book is laid out like this:
- Chapters 1 through 3 are intended as a crash course in concepts that you absolutely must know before reading the rest of the book. They cover topics like design patterns, iterators, and the difference between the MySQL storage engines.
- Chapters 4 and 5 take a brief break from the essentials and focuses on one of the most important concepts for creating scalable applications: caching.
- Chapter 6 revisits the essentials and touches on some advanced MySQL topics.
- Chapters 7 and 8 dive into extending PHP and MySQL with C. They are the only chapters in the book where you're not writing code in just PHP or SQL.
- Chapter 9 goes over full-text search and introduces Sphinx.
- Chapter 10 covers multitasking and discusses Gearman.
- Chapters 11 and 12 cover essentials including advanced rewrite rules, custom session handling and user security.
- Chapter 13 goes over MySQL INFORMATION_SCHEMA.
- Chapter 14 touches on security some more.
- Chapters 15 and 16 wrap up the book with other uses of PHP and MySQL besides web applications and optimizing and debugging.
