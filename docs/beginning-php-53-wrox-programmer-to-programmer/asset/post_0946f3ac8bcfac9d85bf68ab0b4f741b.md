
# Contents

- Accessing Information on Uploaded Files 257
- Limiting the Size of File Uploads 258
- Storing and Using an Uploaded Form 259
- Redirecting after a Form Submission 264
- Summary 266
- Exercises 266

# Chapter 10: Preserving State With Query Strings, Cookies, and Sessions 267

- Saving State with Query Strings 268
- Building Query Strings 268
- Accessing Data in Query Strings 270
- Working with Cookies 274
- Cookie Components 274
- Setting a Cookie in PHP 276
- Accessing Cookies in Your Scripts 277
- Removing Cookies 277
- Using PHP Sessions to Store Data 282
- Creating a Session 282
- Reading and Writing Session Data 283
- Destroying a Session 289
- Passing Session IDs in Query Strings 289
- Changing Behavior 290
- Summary 296
- Exercises 296

# Chapter 11: Working with Files and Directories 297

- Understanding Files and Directories 298
- Getting Information on Files 298
- Time-Related Properties 299
- Retrieving a Filename from a Path 299
- Opening and Closing Files 300
- Opening a File with fopen() 300
- Closing a File with fclose() 302
- Reading and Writing to Files 302
- Reading and Writing Strings of Characters 303
- Testing for the End of a File 306
- Reading One Line at a Time 307
- Reading CSV Files 308
- Reading and Writing Entire Files 309
- Random Access to File Data 311
- Working with File Permissions 312
- Changing Permissions 313
- Checking File Permissions 314
- Copying, Renaming, and Deleting Files 315
- Working with Directories 316
- Other Directory Functions 318
- Working with Directory Objects 320
- Telling a File from a Directory 321
- Building a Text Editor 325
- The Text Editor Script 325
- Testing the Editor 328
- Examining the Editor Code 329
- Summary 334
- Exercise 335

# Chapter 12: Introducing Databases and SQL 337

- Deciding How to Store Data 338
- Database Architectures 338
- Database Models 339
- Choosing a Database 340
- Understanding Relational Databases 341
- Normalization 341
- Talking to Databases with SQL 343
- Setting Up MySQL 349
- Starting the MySQL Server 349
- Setting Up the MySQL root Password 350
- A Quick Play with MySQL 353
- Creating a New Database 353
- Creating a Table 354
- Adding Data to a Table 356
- Reading Data from a Table 356
- Updating Data in a Table 357
- Deleting Data from a Table 358
- Deleting Tables and Databases 358
- Connecting to MySQL from PHP 359
- Making a Connection 360
- Handling Errors 360
- Reading Data 361
- Summary 365
- Exercises 365

# Chapter 13: Retrieving Data from MySQL with PHP 367

- Setting Up the Book Club Database 367
- The BINARY Attribute and Collations 369
- The UNIQUE Constraint 370
- The ENUM Data Type 370
- The TIMESTAMP Data Type 371

### Retrieving Data with SELECT 371

- Limiting the Number of Rows Returned 372
- Sorting Results 373
- Using Pattern Matching for Flexible Queries 374
- Summarizing Data 376
- Eliminating Duplicate Results 377
- Grouping Results 378
- Pulling from Multiple Tables 379
- Using Aliases 381
- Other MySQL Operators and Functions 382

### Creating a Member Record Viewer 385

- Creating the config.php File 386
- Creating the common.inc.php File 387
- Creating the DataObject Class File 388
- Building the Member Class 390
- Building the LogEntry Class 394
- Creating the view_members.php Script 395
- Creating the view_member.php Script 399
- Testing the Application 400

## Summary 401
## Exercises 402

# Chapter 14: Manipulating MySQL Data with PHP 403

- Inserting Records 403
- Updating Records 406
- Deleting Records 407

### Building a Member Registration Application 408

- Adding More Common Code 408
- Enhancing the Member Class 409
- Creating the Registration Script 411
- Testing the Application 417

### Creating a Members' Area 417

- Adding an Authentication Method to the Member Class 418
- Enhancing the LogEntry Class to Record Page Views 419
- Adding More Common Code 420
- Writing the Login Script 421
- Creating the Logout Function 424
- Creating the Pages for Members' Area 424
- Testing the Members' Area 426
- Creating a Member Manager 428
- Adding Update and Delete Methods to the Member Class 428
- Tweaking the view_members.php Script 430
- Creating the view_member.php Script 431
- Testing the Member Manager 437
- Summary 438
- Exercises 439

# Chapter 15: Making Your Job Easier with PEAR 441

- Installing PEAR 442
- Testing the PEAR Manager on Ubuntu 442
- Testing PEAR using Mac OS and WAMP 443
- Installing and Testing PEAR with WampServer on Windows 444
- Installing a Package 446
- Installing Dependencies 447
- Uninstalling Packages 447
- Using a PEAR Package 448
- Creating Tables with the HTML_Table Package 450
- Web Forms the Easy Way with HTML_QuickForm 455
- Installing HTML_QuickForm 455
- Working with HTML_QuickForm 455
- Using Validation Rules 460
- Summary 470
- Exercises 470

# Chapter 16: PHP and the Outside World 471

- Working with Dates and Times 472
- Understanding Timestamps 472
- Getting the Current Date and Time 472
- Creating Your Own Timestamps 473
- Extracting Date and Time from a Timestamp 475
- Formatting Date Strings 478
- Checking Date Values 481
- Working with Microseconds 481
- DateTime: The Future of PHP/Time Handling 487
- Working with HTTP 488
- Understanding HTTP Requests 490
- Modifying an HTTP Response 493
- Getting Information from the Web Server 494
- Sending Email 497
- Specifying the Sender Address and Headers 498
- Controlling the Return Path 499
- Sending HTML Emails 500
- Summary 505
- Exercises 506

# Chapter 17: Generating Images with PHP 507

- Basics of Computer Graphics 507
- Coordinate Systems 508
- Image Types 509
- Creating Images 510
- Creating a New Image 510
- Allocating Colors 510
- Outputting Images 511
- Drawing in an Image 512
- Manipulating Images 520
- Opening an Existing Image 521
- Applying a Watermark 523
- Creating Thumbnails 528
- Using Text in Images 531
- Adding Standard Text 531
- Using TrueType Fonts 533
- Summary 536
- Exercises 537

# Chapter 18: String Matching with Regular Expressions 539

- What Is a Regular Expression? 540
- Pattern Matching in PHP 541
- Exploring Regular Expression Syntax 542
- Matching Literal Characters 542
- Matching Types of Characters using Character Classes 544
- Matching Multiple Characters 545
- Greedy and Non-Greedy Subpatterns to Group Patterns 546
- Referring to Previous Subpattern Matches 547
- Matching Alternative Patterns 548
- Using Anchors to Match at Specified Positions 548
- Finding Multiple Matches with preg_match_all() 550
- Searching Arrays with preg_grep() 556
- Replacing Text 557
- Replacing Text with preg_replace() 557
- Replacing Text using a Callback Function 560
- Altering Matching Behavior with Pattern Modifiers 560
- Splitting a String with a Regular Expression 562
- Summary 571
- Exercises 571

# Chapter 19: Working with XML 573

# What Is XML? 574

# XML Document Structure 575

- Major Parts of an XML Document 576
- XML Syntax Rules 577
- Using XML Elements and Attributes 578
- Valid XML Documents: DTDs and XSDs 578

# Reading XML Documents with PHP 582

- How XML Parser Works 582
- Creating a New Parser 582
- Creating Event Handlers 583
- Parsing the XML Document 584
- Dealing with Parse Errors 584

# Writing and Manipulating XML Documents with PHP 589

- DOM Basics 590
- Creating an XML Document using the DOM 595
- Manipulating XML Documents using the DOM 599

# Doing XML the Easy Way with SimpleXML 606

- Reading an XML Document 608
- Creating an XML Document 610
- Converting Between SimpleXML and DOM Objects 612

# Working with XSL and XSLT 613

# Summary 615
# Exercises 616

# Chapter 20: Writing High-Quality Code 619

- Writing Modular Code 620
- Including Files 621
- Including a File Only 622
- Working with Include Paths 623
- Dynamic Includes 625
- Using Namespaces to Avoid Clashes 625
- Using Coding Standards for Consistency 630
- Documenting Your Code 631
- Writing Good Comments 632
- Using phpDocument to Generate External Documentation 633
- Checking Input and Encoding Output 641
- Checking Input 642
- Encoding Output 643
- Handling Errors 644
- Understanding Error Levels 644
- Triggering Errors 646
- Controlling Where Error Messages Are Sent 647
- Logging Your Own Error Messages 647
- Letting Your Script Handle Errors 648
- Fine-Tuning Error Reporting 651
- Using Exception Objects to Handle Errors 652
- Separating Application Logic from Presentation Logic 660
- Automated Code Testing with PHPUnit 666
- Summary 671
- Exercises 672
- Appendix A: Solutions to Exercises 673
- Appendix B: Configuring PHP 719
- Appendix C: Alternatives to MySQL 757
- Appendix D: Using PHP from the Command Line 765
- Index 775
