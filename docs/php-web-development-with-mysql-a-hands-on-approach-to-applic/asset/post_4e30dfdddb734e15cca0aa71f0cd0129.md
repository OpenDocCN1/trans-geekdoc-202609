
## PHP Web Development with MySQL

A Hands On Approach to Application Programming

by Kenneth E. Marks

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_0_0.png)

## PHP Web Development with MySQL

## A Hands On Approach to Application Programming

by Kenneth E. Marks

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_1_0.png)

## PHP Web Development with MySQL
A Hands On Approach to Application Programming

Contents Copyright ©2021 Kenneth E. Marks—All Rights Reserved

Book and cover layout, design and text Copyright ©2021 musketeers.me, LLC. and its predecessors—All Rights Reserved. Print and Digital copies available from https://www.phparch.com/books/.

php[architect] edition published: July 2021

|  |  |
|---|---|
| Print ISBN: | 978-1-940111-95-7 |
| PDF ISBN: | 978-1-940111-96-4 |
| ePub ISBN: | 978-1-940111-97-1 |
| Mobi ISBN | 978-1-940111-98-8 |

Produced & Printed in the United States

No part of this book may be reproduced, stored in a public retrieval system, or publicly transmitted in any form or by means without the prior written permission of the publisher, except in the case of brief quotations embedded in critical reviews or articles.

## Disclaimer

Although every effort has been made in the preparation of this book to ensure the accuracy of the information contained therein, this book is provided "as-is" and the publisher, the author(s), their distributors and retailers, as well as all affiliated, related or subsidiary parties take no responsibility for any inaccuracy and any and all damages caused, either directly or indirectly, by the use of such information. We have endeavored to properly provide trademark information on all companies and products mentioned in the book by the appropriate use of capitals. However, we cannot guarantee the accuracy of such information.

musketeers.me, the musketeers.me logo, php[architect], the php[architect] logo are trademarks or registered trademarks of musketeers.me, LLC, its assigns, partners, predecessors and successors. All other trademarks are the property of the respective owners.

Written by
Kenneth E. Marks

Published by
musketeers.me, LLC.
4627 University Dr
Fairfax, VA 22030 USA

Managing Editor
Oscar Merida

240-348-5PHP (240-348-5747)
info@phparch.com
www.phparch.com

Editor
Kara Ferguson

Layout
Oscar Merida

## Table of Contents

- **Introduction** XVII
- **1. The Life and Times of a PHP Script** 1
- Static Vs. Dynamic Websites 2
- The Browser and the Server 2
- The Server and PHP 3
- **2. Writing Your First PHP Script** 5
- Setting Up a Development Environment 6
- Hello World! 15
- Exercises 21
- **3. Why Variables Matter** 23
- Variables in PHP 24
- Types of Variables 25
- Constants 31
- Exercises 31
- **4. Basic String Interpretation** 33
- Concatenation 34
- Interpolation 34
- Escaping 35
- Heredoc 36
- Exercises 36
- **5. Operators, Expressions, and Basic Arithmetic** 37
- Operators and Expressions 38
- Math Functions 41

## 6. Arrays 43

- Simple Arrays in PHP 44
- Associative Arrays 45
- Adding Values 46
- Explicit Versus Short Array Syntax 46
- Useful Array Functions 46
- Multidimensional Arrays 52
- Exercises 54

## 7. Truth, Comparisons, Conditions, and Compound Conditions 55

- Comparison Operators 56
- Conditional Logic 59
- Compound Conditional Logic Using Logical Operators 62
- Exercises 64

## 8. Verifying Variables and Type Checking 65

- Verifying Variables 66
- Verifying and Checking Variable Types 68
- Exercises 71

## 9. Looping 73

- Counting Loops 74
- Sentinel Loops 76
- Exiting and Continuing a Loop 78
- Exercises 79

## 10. Functions 81

- Simple Function 82
- Function Parameters/Arguments 83
- Returning Values from a Function 84
- Further Advice On Writing Good Functions 85
- Exercises 88

## 11. Working with HTML Forms 89

A Simple Form 90

Processing Our Form and Outputting Back to the Web Page 91

Cleaning It Up Using a Self Referencing Page 93

Exercise: Badlibs, Part 1 95

## 12. Inserting Data Into a MySQL Database 97

Using the MySQL CLI 98

Create a PHP Application to Insert Data 108

Exercises 116

## 13. Returning Data from a MySQL Database 117

Returning Database Rows in a PHP Application 118

Exercise: Badlibs, Part 2 121

## 14. Validating Form Data and Creating Sticky Fields 123

Modifying FullName Behavior Based On Validation 124

Adding Field Validation 125

Making the First and Last Name Fields Sticky 127

Testing Our Script with Sticky Fields 130

Exercise: Contact Form 131

## 15. Displaying a List of Item Details 133

Designing the Database 134

Creating the Database 135

Adding Movie Data 139

Creating the Main Movie Listing Page 141

Creating the Movie Details Page 149

Exercises 155

## 16. Adding Data Using the Web Application 157

Creating a Page to Add Movies 158

Complete Code Listing 169

Link to the “Add a Movie” Page from the Listing Page 174

Exercises 174

## 17. Removing Data Using the Web Application 175

- Adding Deletion Links to Movie Listings 176
- Creating a “Remove a Movie Page” 178
- Complete Code Listing 186
- Exercises 189

## 18. Editing Data Using the Web Application 191

- Linking Movie Details to the Edit Page 192
- Create the Editing Page 193
- Complete Code Listing 209
- Exercises 213

## 19. Working With Files and Feature Additions to Existing Code 215

- Add a Field for File Information 217
- Create a Folder for Uploaded Movie Image Files 219
- Adding File Upload Capability 219
- Displaying Thumbnail Images of Movies on Main Page 248
- Displaying Movie Image on Details Page 252
- Add Image File Uploads to the Editing Page 256
- Displaying Image on Deletion Page 269
- Exercises 276

## 20. Basic HTTP Authentication 277

- Password Protection with HTTP Authentication 278
- How Does HTTP Authentication Work? 279
- Create authorizeaccess.php 280
- Adding Authorization to Pages 283
- Exercises 284

## 21. Persistence 285

- Cookies 286
- Session Variables 294
- Cookies and Session Variables 299
- The Database 300
- Best Practices in Solving the Persistence Problem 300
- Exercises 300

## 22. Creating Secure Web Applications 301

- Secure Password Protection for Authenticating 302
- Guarding Against SQL Injection 306
- Leaking Information to Hackers 314
- Preventing Cross-Site Scripting Attacks 315
- File Uploads 319
- Securing Your Session 321
- Final Thoughts 322
- Exercises 322

## 23. Adding User Logins 323

- Create a user Table 325
- Create a Signup.php script 326
- Create a login.php Script 341
- Create a logout.php Script 351
- Allow Users with Administrative Access 352
- Exercises 356

## 24. Adding a Navigation Menu 357

- Create Navbar Logic 358
- Add the Navigation Bar 362
- Add Navigation Bar to Details Page 363
- Add Login Link to Navigation Bar 365
- Add Logout Link to Navigation Bar 367
- Add Sign Up Link to Navigation Bar 368
- Add Navigation Bar to addmovie.php 369
- Add Navigation Bar to Unauthorizedaccess.php 372
- Add Navigation Bar to editmovie.php 372
- Add Navigation Bar to removemovie.php 375
- Complete Code Listings 376
- Exercises 378

## 25. Adding Reservation Features 379

- Add Number of Copies and Number Reserved 380
- Persisting Movie Reservations for Users 397
- Checking Movies Reserved by Users 398
- Modify Homepage Based On Access Privileges 400
- Refactoring to Remove Duplicate Inclusions 405
- Script for Reserving Movies 407
- Adding Cart to Navigation Menu 418
- Add a Script for a Shopping Cart 420
- Navigating to Reserved Movies 432
- Showing and Returning Reserved Movies 435
- Features to Add 448
- Flaws in This Application 449
- Exercises 450

## 26. Introduction to Object-Oriented Programming in PHP 451

- Classes 452
- Properties 453
- Encapsulation Using Access Modifiers 454
- Accessor Methods 454
- The $this Variable 456
- General Purpose Methods 458
- Instantiating and Using a Class 458
- Validating Input to a Setter Method 461
- Inheritance 465
- Overriding Methods 468
- Constructors 469
- Creating Parameterized Queries Using OOP 473
- Exercises 485

## Index 487
