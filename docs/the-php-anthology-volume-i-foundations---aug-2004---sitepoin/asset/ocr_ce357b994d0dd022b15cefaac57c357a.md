PHP’s four include commands should not be confused with the various file-related functions (discussed in Chapter 4); these are intended for fetching files without parsing them immediately as PHP scripts, thereby allowing you to work on their contents.

Note that throughout this book I’ll be talking about “including” a file even when I’m using one of the require commands. This is a common convention for talking about PHP that stems from older programming languages used by the first PHP pioneers.

# Path Finding

So far, I’ve only looked at including files in the same directory as the script that contains the include command. In practice, you’ll usually want to organize files into subdirectories based on the job they do. This can be a source of much confusion, particularly when you’re using third party code, as there are numerous alternative approaches to dealing with includes in other directories.

The first thing to be aware of is that all includes are calculated relative to the directory in which the main script (where execution began) resides. For example, imagine we have three files in the following locations:

/home/username/www/index.php
/home/username/www/includes/script.php
/home/username/www/another.php

First, let’s consider index.php. The command include 'includes/script.php'; will correctly include script.php, assuming index.php is the actual file requested.

But what if we use the following command in script.php:

```
include '../another.php'; // ???
```

If script.php is the page we’re viewing, this command will correctly include another.php. However, if index.php is the page we’re viewing, and it includes script.php, this command will fail, because the location of another.php is calculated relative to the location of index.php, not relative to script.php.

We have two choices. We can modify script.php so that it includes another.php as follows:

```
include 'another.php';
```