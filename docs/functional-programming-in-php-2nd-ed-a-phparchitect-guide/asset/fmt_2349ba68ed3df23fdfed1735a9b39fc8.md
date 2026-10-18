
Now whenever your project is called it will automatically load the correct autoloaders to satisfy your application’s dependency requirements. To speed up slow SPL autoloaders Composer also comes with an autoloader cache that it is recommended for use in production environments.

From the desired directory, when you want to create an autoload cache file you simply run the following command and Composer will automatically generate it for you.

```
```

There is much more functionality available from Composer you can use to help you manage dependencies, but that small introduction should be enough to complete the tasks in this book and provide a jumping off point for your own research. Composer is the recommended way of specifying any dependencies for any application you may be working on as it makes installation and implementation fast and easy.

### PECL Extensions

PHP extensions are usually formed of one or more C files that need to be compiled before the extension can be enabled and used. They may come from the PECL repository in which case the `pecl` command is very useful, or you can download them independently as tarballs.

The standard method to install a stable version of a PECL extension is to call:

```
```

Should the package be in alpha or beta state, you can easily install it by appending the release status to the install command like so:

```
```

or

```
```

Another option is to set your `pecl` command line manager to always install beta or alpha packages if they are available:

```
```

or

```
```

You can also easily install a specific version of a PECL extension by including the number after the package name:

```
```

Besides alpha and beta versions of the extensions there can also be devel and stable releases.

PECL can also install extensions from the archive packages, which can be downloaded from the PECL website:

```
```

To manually build and install a PECL extension is also relatively easy from an extracted tarball directory:

```
```

So once the extension is built using any of the aforementioned methods you will also need to enable it in the `php.ini` file by adding:

```
```

It should be noted here, if you are using this extension with a website rather than on the PHP CLI then you will need to restart your web server for the new PHP configuration to take effect.

PHP extensions provide a way of creating fast running functionality for PHP via a C interface to the core of the language itself. C code runs much faster than its PHP counterpart, so this is one means of speeding up some applications.

### HHVM

There are two ways to install HipHop Virtual Machine (HHVM) on a Linux machine with manual compilation (time consuming) and installing a ready made binary. As we are not going to be making use of any HHVM extensions we can happily use a pre-built package. To make things even easier, the code we will implement on HHVM is available in the version provided by Facebook for Ubuntu 14.04.

This makes installing the HHVM alternative runtime as simple as a few calls to Ubuntu’s `apt-get` package management system.

```
```

You should now be able to call `hhvm` directly on the command line like you would with PHP’s CLI. A word of caution though; the just-in-time compiler or JIT that HHVM employs to speed up the running of PHP and Hack code is not active on the command line by default. This makes sense because there is a startup cost of bytecode compilation with the JIT turned on that would only make sense to incur on long running scripts.

That said, if you do want to force the HHVM JIT on for the command line, you do so by passing a parameter to the HHVM command line client.

```
```

HHVM is a more simplified means of speeding up code than a PHP extension and it also brings with it a horde of goodies in the Hack language additions to PHP. The primary interest in HHVM for this book are the data structures and little pieces of syntactic sugar Hack adds to the base PHP language.

Hack can also be installed on other Linuxes and MacOS, but Ubuntu was the preferred platform during development of HHVM. Users of both Haiku OS

* * *

1.  [PsySH](http://psysh.org)[↩](#ch004.xhtml#fnref1)

2.  [Boris](https://github.com/d11wtq/boris)[↩](#ch004.xhtml#fnref2)

3.  [PHPsh](http://phpsh.org)[↩](#ch004.xhtml#fnref3)

4.  [3V4L](http://www.3v4l.org)[↩](#ch004.xhtml#fnref4)

5.  [Composer Documentaion](http://getcomposer.org/doc/)[↩](#ch004.xhtml#fnref5)

6.  [PECL](http://pecl.php.net)[↩](#ch004.xhtml#fnref6)

7.  [PSR-1: Basic Coding Standard](http://www.php-fig.org/psr/psr-1/)[↩](#ch004.xhtml#fnref7)

8.  [PSR-2: Coding Style Guide](http://www.php-fig.org/psr/psr-2/)[↩](#ch004.xhtml#fnref8)

9.  Haiku OS is an open source reincarnation of the now long forgotten, but once much loved BeOS prized for its concurrency (something of interest to functional programmers) leading to an ultra-responsive user interface[↩](#ch004.xhtml#fnref9)

# 2 What is Functional Programming?

> “Programming where your entire program is a single referentially transparent expression composed of other referentially transparent expressions. No side effects. No mutability. No global mutable state.”

> 

> —Rúnar Bjarnason (Functional programmer, @runarorama)

It is difficult to categorically define functional programming as all functional languages vary, and there is not a universally agreed upon specification. Couple that with the fact there are varying opinions amongst programmers as to what makes a functional language, and you have a conundrum. To confuse matters further, many languages have functional elements or primitives defined in them.

While perilous, I will make an attempt at a very simplified explanation of a core tenet. Programming in a functional way is essentially coding without any assignment of values. There, I said it! Of course, there’s a lot more to it, but this is the most simplistic—and also the most mind blowing—statement for those of us from an imperative programming background like PHP.

This is a very simplified allusion to the functional approach of removing state from your programs and emphasizing purity. It is, of course, also an incendiary challenge to your current programming practices. As your understanding of functional programming grows you will begin to understand more encompassing descriptions of what constitutes a functional piece of code.

To begin with, it is important to define what imperative programming means so there is a good base to build upon. Imperative programming is often thought of as the diametric opposite of functional programming allowing us to eliminate it from the description of what functional programming actually is. It is a style where the programmer tells the computer step by step exactly what it should do to complete a computation or program.

You may think this just applies to procedural PHP (code that does not make use of PHP’s object oriented constructs and functions), but you would be wrong. Simon Peyton Jones of Haskell fame describes imperative programming as

> “…a sequence of steps. Every line says do this, then do this, do this. When you call a method often there are no results \[returned\]…because the sole reason for calling it is to have an effect on the world. To change the state of something.”

He points out a very noteworthy property of imperative programming—there are hidden changes to state. This means if you call a method in an imperative program you cannot be sure if it will just compute the result given your arguments or whether it will also adjust the state of the programming. As functional programming seeks to be pure, these changes in state must be eliminated.

A number of people describe functional programming based on this property of no changes to state. One such person is Erik Meijer who has a love of Haskell and has worked on the C# programming language, among others. He describes functional programming as being
