# Code Overview

In this, the first of your applications, you need to look at the architecture you will use in constructing your applications. The applications on the CD have been constructed so that they are reusable and portable as possible.

To start with, there is a folder book, which should be copied to the root directory of your Web server. On Apache this folder is htdocs by default. The book folder contains all the applications documented in this book. If you need some reason to copy the book folder to a spot other than the root directory, you will need to make sure to change the Include commands at the top of header.php.
8-8 shows the folder structure.

![](bbox=[0.166, 0.341, 0.74, 0.696])

Within the book folder, there is a series of functions, one for each of the applications presented here and one labeled functions. In this application we will concern ourselves with basic.php. This file will contain some functions that you will use in a variety of applications. We will discuss the functions in basic.php that are used in guestbook2k in the section entitled Code Breakdown. The code that is relevant only to guestbook2k is kept in the guestbook2k folder. Here, the functions that will need to be addressed across a number of pages are kept in the header.php file. We will also explain these functions in detail in the “Code Breakdown” section.