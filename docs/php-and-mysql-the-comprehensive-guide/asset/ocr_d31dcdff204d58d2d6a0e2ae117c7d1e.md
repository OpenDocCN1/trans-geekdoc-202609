# 36.2 Install PHPUnit

PHPUnit offers numerous possibilities and functionalities for all of this. We want to use a simple example to show you how to get started with PHPUnit.

There are two approaches to installing PHPUnit. On the one hand, you can use the Composer package manager, which we discuss in more detail in Chapter 38. As soon as Composer is set up on the system, it installs the following instruction (see Figure 36.1):

```
composer require --dev phpunit/phpunit
```

![](bbox=[0.145, 0.275, 0.73, 0.66])

Figure 36.1 Installation of PHPUnit via Composer

> **Note**
> 
> You need the mbstring PHP extension for the latest PHPUnit versions, which you install as usual via the `php.ini` file.

Alternatively, you can also download a PHAR package from PHPUnit. The URL for the latest minor version of a major version number is https://phar.phpunit.de/phpunit-X.phar, where X has the value 10, for example. Here, we assume that you then save this archive under the name phpunit.phar. You can find all releases at https://phar.phpunit.de. Make the PHAR file executable, and then call it up as shown in Figure 36.2.