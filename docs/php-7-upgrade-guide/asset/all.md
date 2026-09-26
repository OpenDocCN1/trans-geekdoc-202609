![](images/title_page.png)

![PHP 7 Upgrade Guide](images/title_page.png)

## PHP 7 Upgrade Guide

### Your guide to new features, breaking changes, and more.

 

#### Colin O'Dell

 

This book is for sale at [http://leanpub.com/php7](http://leanpub.com/php7)

This version was published on 2017-11-17

![publisher's logo](images/leanpub-logo.png)

\*   \*   \*   \*   \*

This is a [Leanpub](http://leanpub.com) book. Leanpub empowers authors and publishers with the Lean Publishing process. [Lean Publishing](http://leanpub.com/manifesto) is the act of publishing an in-progress ebook using lightweight tools and many iterations to get reader feedback, pivot until you have the right book and build traction once you do.

\*   \*   \*   \*   \*

© 2015 - 2017 Colin O'Dell 

This book is dedicated to all those who hunger to learn.

## Table of Contents

1.  [Preface](#chap00.xhtml#leanpub-auto-preface) 
    1.  [Who is this book for](#chap01.xhtml#leanpub-auto-who-is-this-book-for)
    2.  [Contents](#chap02.xhtml#leanpub-auto-contents)
    3.  [Other resources](#chap03.xhtml#leanpub-auto-other-resources)
    4.  [Acknowledgements](#chap04.xhtml#leanpub-auto-acknowledgements) 
        1.  [PHP Wiki and Documentation Content](#chap04.xhtml#leanpub-auto-php-wiki-and-documentation-content)
2.  [Getting Started with PHP 7](#chap05.xhtml#leanpub-auto-getting-started-with-php-7) 
    1.  [Ubuntu 14.04 and 16.04+](#chap06.xhtml#leanpub-auto-ubuntu-1404-and-1604)
    2.  [Debian 8 & 9](#chap07.xhtml#leanpub-auto-debian-8--9)
    3.  [Debian 6 & 7](#chap08.xhtml#leanpub-auto-debian-6--7)
    4.  [CentOS / RHEL](#chap09.xhtml#leanpub-auto-centos--rhel)
    5.  [Mac OS X](#chap10.xhtml#leanpub-auto-mac-os-x)
    6.  [Windows](#chap11.xhtml#leanpub-auto-windows)
    7.  [phpbrew](#chap12.xhtml#phpbrew)
    8.  [Docker](#chap13.xhtml#leanpub-auto-docker)
    9.  [Vagrant Image](#chap14.xhtml#leanpub-auto-vagrant-image)
    10.  [Build from Source](#chap15.xhtml#leanpub-auto-build-from-source)
3.  [Part 1 - New Features](#chap16.xhtml#leanpub-auto-part-1---new-features) 
    1.  [Chapter 1: Scalar Type Hints](#chap17.xhtml#chapter-1) 
        1.  [Type Checking Modes](#chap17.xhtml#leanpub-auto-type-checking-modes)
        2.  [Mixing Modes](#chap17.xhtml#leanpub-auto-mixing-modes)
        3.  [Backwards Compatibility](#chap17.xhtml#leanpub-auto-backwards-compatibility)
        4.  [Further Reading](#chap17.xhtml#leanpub-auto-further-reading)
    2.  [Chapter 2: Return Type Declarations](#chap18.xhtml#chapter-2) 
        1.  [Returning `null`](#chap18.xhtml#leanpub-auto-returning-null)
        2.  [Sub-Class Methods](#chap18.xhtml#leanpub-auto-sub-class-methods)
        3.  [Further Reading](#chap18.xhtml#leanpub-auto-further-reading-1)
    3.  [Chapter 3: Combined Comparison (Spaceship) Operator](#chap19.xhtml#chapter-3) 
        1.  [Comparing Values](#chap19.xhtml#leanpub-auto-comparing-values)
        2.  [Sorting](#chap19.xhtml#leanpub-auto-sorting)
        3.  [Sorting by multiple values](#chap19.xhtml#leanpub-auto-sorting-by-multiple-values)
        4.  [Further Reading](#chap19.xhtml#leanpub-auto-further-reading-2)
    4.  [Chapter 4: Null Coalesce Operator](#chap20.xhtml#chapter-4) 
        1.  [Differences From `?:`](#chap20.xhtml#leanpub-auto-differences-from-)
        2.  [Chaining](#chap20.xhtml#leanpub-auto-chaining)
        3.  [Further Reading](#chap20.xhtml#leanpub-auto-further-reading-3)
    5.  [Chapter 5: Unicode Codepoint Escape Syntax](#chap21.xhtml#chapter-5) 
        1.  [Why the `{}`s?](#chap21.xhtml#leanpub-auto-why-the-s)
        2.  [Limitations](#chap21.xhtml#leanpub-auto-limitations)
        3.  [Backwards Compatibility](#chap21.xhtml#leanpub-auto-backwards-compatibility-1)
        4.  [Further Reading:](#chap21.xhtml#leanpub-auto-further-reading-4)
    6.  [Chapter 6: Anonymous Classes](#chap22.xhtml#chapter-6) 
        1.  [Nesting Classes](#chap22.xhtml#leanpub-auto-nesting-classes)
        2.  [Use Cases](#chap22.xhtml#leanpub-auto-use-cases)
        3.  [Differences from Named Classes](#chap22.xhtml#leanpub-auto-differences-from-named-classes)
        4.  [Further Reading:](#chap22.xhtml#leanpub-auto-further-reading-5)
    7.  [Chapter 7: Group Use Declarations](#chap23.xhtml#chapter-7) 
        1.  [Compound Namespaces](#chap23.xhtml#leanpub-auto-compound-namespaces)
        2.  [Further Reading:](#chap23.xhtml#leanpub-auto-further-reading-6)
    8.  [Chapter 8: Closure `call` Method](#chap24.xhtml#chapter-8) 
        1.  [Further Reading:](#chap24.xhtml#leanpub-auto-further-reading-7)
    9.  [Chapter 9: Generator Return Expressions](#chap25.xhtml#chapter-9) 
        1.  [Further Reading:](#chap25.xhtml#leanpub-auto-further-reading-8)
    10.  [Chapter 10: Generator Delegation](#chap26.xhtml#chapter-10) 
         1.  [Yielding Values](#chap26.xhtml#leanpub-auto-yielding-values)
         2.  [Sending Values](#chap26.xhtml#leanpub-auto-sending-values)
         3.  [Exceptions](#chap26.xhtml#leanpub-auto-exceptions)
         4.  [Return Values](#chap26.xhtml#leanpub-auto-return-values)
         5.  [Further Reading:](#chap26.xhtml#leanpub-auto-further-reading-9)
    11.  [Chapter 11: Reliable User-land CSPRNG](#chap27.xhtml#chapter-11) 
         1.  [Backwards Compatibility](#chap27.xhtml#leanpub-auto-backwards-compatibility-2)
         2.  [Forwards Compatibility](#chap27.xhtml#leanpub-auto-forwards-compatibility)
         3.  [Further Reading](#chap27.xhtml#leanpub-auto-further-reading-10)
    12.  [Chapter 12: Integer Division](#chap28.xhtml#chapter-12) 
         1.  [Backwards Compatibility](#chap28.xhtml#leanpub-auto-backwards-compatibility-3)
         2.  [Further Reading](#chap28.xhtml#leanpub-auto-further-reading-11)
    13.  [Chapter 13: preg\_replace\_callback\_array](#chap29.xhtml#chapter-13) 
         1.  [Backwards Compatibility](#chap29.xhtml#leanpub-auto-backwards-compatibility-4)
         2.  [Further Reading](#chap29.xhtml#leanpub-auto-further-reading-12)
    14.  [Chapter 14: `IntlChar` Class](#chap30.xhtml#chapter-14) 
         1.  [Backwards Compatibility](#chap30.xhtml#leanpub-auto-backwards-compatibility-5)
         2.  [Further Reading](#chap30.xhtml#leanpub-auto-further-reading-13)
4.  [Part 2 - Language Changes & Improvements](#chap31.xhtml#leanpub-auto-part-2---language-changes--improvements) 
    1.  [Chapter 15: Performance](#chap32.xhtml#chapter-15) 
        1.  [Further Reading](#chap32.xhtml#leanpub-auto-further-reading-14)
    2.  [Chapter 16: Language Consistency](#chap33.xhtml#chapter-16) 
        1.  [Uniform Variable Syntax](#chap33.xhtml#chapter-16-uvs)
        2.  [Abstract Syntax Tree](#chap33.xhtml#chapter-16-ast)
        3.  [Further Reading](#chap33.xhtml#leanpub-auto-further-reading-15)
    3.  [Chapter 17: Semi-Reserved Words](#chap34.xhtml#chapter-17) 
        1.  [Further Reading](#chap34.xhtml#leanpub-auto-further-reading-16)
    4.  [Chapter 18: Error Handling and Exceptions](#chap35.xhtml#chapter-18) 
        1.  [Exceptions in the Engine](#chap35.xhtml#leanpub-auto-exceptions-in-the-engine)
        2.  [Reclassification of `E_STRICT` Notices](#chap35.xhtml#leanpub-auto-reclassification-of-estrict-notices)
        3.  [Backwards Compatibility](#chap35.xhtml#leanpub-auto-backwards-compatibility-8)
        4.  [Further Reading](#chap35.xhtml#leanpub-auto-further-reading-17)
    5.  [Chapter 19: Expectations](#chap36.xhtml#chapter-19) 
        1.  [`assert()` as a statement](#chap36.xhtml#leanpub-auto-assert-as-a-statement)
        2.  [Custom errors](#chap36.xhtml#leanpub-auto-custom-errors)
        3.  [Configuration](#chap36.xhtml#leanpub-auto-configuration)
        4.  [Backwards Compatibility](#chap36.xhtml#leanpub-auto-backwards-compatibility-9)
        5.  [Further Reading](#chap36.xhtml#leanpub-auto-further-reading-18)
    6.  [Chapter 20: Array Constants in `define()`](#chap37.xhtml#chapter-20) 
        1.  [Further Reading](#chap37.xhtml#leanpub-auto-further-reading-19)
    7.  [Chapter 21: Filtered `unserialize()`](#chap38.xhtml#chapter-21) 
        1.  [Secure filtering](#chap38.xhtml#leanpub-auto-secure-filtering)
        2.  [Examples](#chap38.xhtml#leanpub-auto-examples)
        3.  [Further Reading](#chap38.xhtml#leanpub-auto-further-reading-20)
    8.  [Chapter 22: `session_start` Options](#chap39.xhtml#chapter-22) 
        1.  [New options](#chap39.xhtml#leanpub-auto-new-options)
        2.  [Further Reading](#chap39.xhtml#leanpub-auto-further-reading-21)
    9.  [Chapter 23: Reflection Enhancements](#chap40.xhtml#chapter-23) 
        1.  [ReflectionGenerator](#chap40.xhtml#leanpub-auto-reflectiongenerator)
        2.  [ReflectionType](#chap40.xhtml#leanpub-auto-reflectiontype)
        3.  [ReflectionParameter](#chap40.xhtml#leanpub-auto-reflectionparameter)
        4.  [ReflectionFunctionAbstract](#chap40.xhtml#leanpub-auto-reflectionfunctionabstract)
        5.  [Backwards Compatibility](#chap40.xhtml#leanpub-auto-backwards-compatibility-10)
        6.  [Further Reading](#chap40.xhtml#leanpub-auto-further-reading-22)
    10.  [Chapter 24: Integer Semantics](#chap41.xhtml#chapter-24) 
         1.  [Casting NaN and Infinity](#chap41.xhtml#leanpub-auto-casting-nan-and-infinity)
         2.  [Negative bitwise shifting](#chap41.xhtml#leanpub-auto-negative-bitwise-shifting)
         3.  [Bitwise shifting too far](#chap41.xhtml#leanpub-auto-bitwise-shifting-too-far)
         4.  [Backwards Compatibility](#chap41.xhtml#leanpub-auto-backwards-compatibility-11)
         5.  [Further Reading](#chap41.xhtml#leanpub-auto-further-reading-23)
    11.  [Chapter 25: Division By Zero Semantics](#chap42.xhtml#chapter-25) 
         1.  [Backwards Compatibility](#chap42.xhtml#leanpub-auto-backwards-compatibility-12)
         2.  [Further Reading](#chap42.xhtml#leanpub-auto-further-reading-24)
    12.  [Chapter 26: JSON Library](#chap43.xhtml#chapter-26) 
         1.  [Fractional float values](#chap43.xhtml#leanpub-auto-fractional-float-values)
         2.  [Backwards Compatibility](#chap43.xhtml#leanpub-auto-backwards-compatibility-13)
         3.  [Further Reading](#chap43.xhtml#leanpub-auto-further-reading-25)
    13.  [Chapter 27: Behavior Changes to `foreach`](#chap44.xhtml#chapter-27) 
         1.  [Changes](#chap44.xhtml#leanpub-auto-changes)
         2.  [Backwards Compatibility](#chap44.xhtml#leanpub-auto-backwards-compatibility-14)
         3.  [Further Reading](#chap44.xhtml#leanpub-auto-further-reading-26)
    14.  [Chapter 28: Behavior Changes to `list`](#chap45.xhtml#chapter-28) 
         1.  [String Handling](#chap45.xhtml#leanpub-auto-string-handling)
         2.  [Empty List Assignment](#chap45.xhtml#leanpub-auto-empty-list-assignment)
         3.  [Variable Assignment Order](#chap45.xhtml#leanpub-auto-variable-assignment-order)
         4.  [Backwards Compatibility](#chap45.xhtml#leanpub-auto-backwards-compatibility-15)
         5.  [Further Reading](#chap45.xhtml#leanpub-auto-further-reading-27)
    15.  [Chapter 29: Parameter Handling Changes](#chap46.xhtml#chapter-29) 
         1.  [Duplicate Parameter Names](#chap46.xhtml#leanpub-auto-duplicate-parameter-names)
         2.  [`func_get_arg()` and `func_get_args()`](#chap46.xhtml#leanpub-auto-funcgetarg-and-funcgetargs)
         3.  [Backwards Compatibility](#chap46.xhtml#leanpub-auto-backwards-compatibility-16)
         4.  [Further Reading](#chap46.xhtml#leanpub-auto-further-reading-28)
    16.  [Chapter 30: Custom Session Handler Return Values](#chap47.xhtml#chapter-30) 
         1.  [Backwards Compatibility](#chap47.xhtml#leanpub-auto-backwards-compatibility-17)
         2.  [Further Reading](#chap47.xhtml#leanpub-auto-further-reading-29)
    17.  [Chapter 31: Errors on Invalid Octal Literals](#chap48.xhtml#chapter-31) 
         1.  [Backwards Compatibility](#chap48.xhtml#leanpub-auto-backwards-compatibility-18)
         2.  [Further Reading](#chap48.xhtml#leanpub-auto-further-reading-30)
5.  [Part 3 - Deprecations & Removals](#chap49.xhtml#leanpub-auto-part-3---deprecations--removals) 
    1.  [Chapter 32: Deprecation of PHP 4 Constructors](#chap50.xhtml#chapter-32) 
        1.  [Backwards Compatibility](#chap50.xhtml#leanpub-auto-backwards-compatibility-19)
        2.  [Further Reading](#chap50.xhtml#leanpub-auto-further-reading-31)
    2.  [Chapter 33: Deprecation of Salt Option for `password_hash()`](#chap51.xhtml#chapter-33) 
        1.  [Further Reading](#chap51.xhtml#leanpub-auto-further-reading-32)
    3.  [Chapter 34: Removal of Previously-Deprecated Features](#chap52.xhtml#chapter-34) 
        1.  [Removed Extensions](#chap52.xhtml#leanpub-auto-removed-extensions)
        2.  [Removed Language Features](#chap52.xhtml#leanpub-auto-removed-language-features)
        3.  [Removed Functions](#chap52.xhtml#leanpub-auto-removed-functions)
        4.  [Removed INI Options](#chap52.xhtml#leanpub-auto-removed-ini-options)
        5.  [Miscellaneous Removed Functionality](#chap52.xhtml#leanpub-auto-miscellaneous-removed-functionality)
        6.  [Backwards Compatibility](#chap52.xhtml#leanpub-auto-backwards-compatibility-20)
        7.  [Further Reading](#chap52.xhtml#leanpub-auto-further-reading-33)
    4.  [Chapter 35: Removal of Alternative PHP Tags](#chap53.xhtml#chapter-35) 
        1.  [Migrating From Alternative Tags](#chap53.xhtml#leanpub-auto-migrating-from-alternative-tags)
        2.  [Backwards Compatibility](#chap53.xhtml#leanpub-auto-backwards-compatibility-21)
        3.  [Further Reading](#chap53.xhtml#leanpub-auto-further-reading-34)
    5.  [Chapter 36: Reclassification and Removal of E\_STRICT Notices](#chap54.xhtml#chapter-36) 
        1.  [Examples](#chap54.xhtml#leanpub-auto-examples-1)
        2.  [Same (compatible) property in two used traits](#chap54.xhtml#leanpub-auto-same-compatible-property-in-two-used-traits)
        3.  [Accessing static property non-statically](#chap54.xhtml#leanpub-auto-accessing-static-property-non-statically)
        4.  [Only variables should be assigned by reference](#chap54.xhtml#leanpub-auto-only-variables-should-be-assigned-by-reference)
        5.  [Only variables should be passed by reference](#chap54.xhtml#leanpub-auto-only-variables-should-be-passed-by-reference)
        6.  [Calling non-static methods statically](#chap54.xhtml#leanpub-auto-calling-non-static-methods-statically)
        7.  [Backwards Compatibility](#chap54.xhtml#leanpub-auto-backwards-compatibility-22)
        8.  [Further Reading](#chap54.xhtml#leanpub-auto-further-reading-35)
    6.  [Chapter 37: Removal of Multiple Defaults in Switches](#chap55.xhtml#chapter-37) 
        1.  [Backwards Compatibility](#chap55.xhtml#leanpub-auto-backwards-compatibility-23)
        2.  [Further Reading](#chap55.xhtml#leanpub-auto-further-reading-36)
    7.  [Chapter 38: Removal of Numeric Hexadecimal String Support](#chap56.xhtml#chapter-38) 
        1.  [Backwards Compatibility](#chap56.xhtml#leanpub-auto-backwards-compatibility-24)
        2.  [Further Reading](#chap56.xhtml#leanpub-auto-further-reading-37)
    8.  [Chapter 39: Removal of Dead SAPIs and Extensions](#chap57.xhtml#chapter-39) 
        1.  [Dead SAPIs](#chap57.xhtml#leanpub-auto-dead-sapis)
        2.  [Dead Extensions](#chap57.xhtml#leanpub-auto-dead-extensions)
        3.  [Backwards Compatibility](#chap57.xhtml#leanpub-auto-backwards-compatibility-25)
        4.  [Further Reading](#chap57.xhtml#leanpub-auto-further-reading-38)
    9.  [Chapter 40: Removal of the `date.timezone` Warning](#chap58.xhtml#chapter-40) 
        1.  [Further Reading](#chap58.xhtml#leanpub-auto-further-reading-39)
6.  [Appendix - Backward Compatibility Breaks](#chap59.xhtml#bc-breaks) 
    1.  [Language Changes](#chap60.xhtml#leanpub-auto-language-changes) 
        1.  [Variable handling](#chap60.xhtml#leanpub-auto-variable-handling)
        2.  [`list()` behavior](#chap60.xhtml#leanpub-auto-list-behavior)
        3.  [`foreach` behavior](#chap60.xhtml#leanpub-auto-foreach-behavior)
        4.  [Parameter handling](#chap60.xhtml#leanpub-auto-parameter-handling)
        5.  [Integer handling](#chap60.xhtml#leanpub-auto-integer-handling)
        6.  [String handling](#chap60.xhtml#leanpub-auto-string-handling-1)
        7.  [Error handling](#chap60.xhtml#leanpub-auto-error-handling)
        8.  [Other language changes](#chap60.xhtml#leanpub-auto-other-language-changes)
    2.  [Standard Library Changes](#chap61.xhtml#leanpub-auto-standard-library-changes)
    3.  [Other Changes](#chap62.xhtml#leanpub-auto-other-changes) 
        1.  [Curl](#chap62.xhtml#leanpub-auto-curl)
        2.  [Date](#chap62.xhtml#leanpub-auto-date)
        3.  [DBA](#chap62.xhtml#leanpub-auto-dba)
        4.  [GMP](#chap62.xhtml#leanpub-auto-gmp)
        5.  [Intl](#chap62.xhtml#leanpub-auto-intl)
        6.  [libxml](#chap62.xhtml#leanpub-auto-libxml)
        7.  [Mcrypt](#chap62.xhtml#leanpub-auto-mcrypt)
        8.  [Session](#chap62.xhtml#leanpub-auto-session)
        9.  [Opcache](#chap62.xhtml#leanpub-auto-opcache)
        10.  [OpenSSL](#chap62.xhtml#leanpub-auto-openssl)
        11.  [PCRE:](#chap62.xhtml#leanpub-auto-pcre)
        12.  [PDO\_pgsql:](#chap62.xhtml#leanpub-auto-pdopgsql)
        13.  [Standard:](#chap62.xhtml#leanpub-auto-standard)
        14.  [JSON:](#chap62.xhtml#leanpub-auto-json)
        15.  [Stream:](#chap62.xhtml#leanpub-auto-stream)
        16.  [XSL:](#chap62.xhtml#leanpub-auto-xsl)
7.  [Notes](#chap63.xhtml#leanpub-endnotes)

## Guide

1.  [Begin Reading](#chap00.xhtml)

# Preface

## Who is this book for

This is book is for PHP developers looking to jump into PHP 7. You’ll need previous experience with PHP in order to understand the topics and examples we’ll cover. The more you know about PHP 5 and OOP, the more you’ll understand why some of the changes are important and how they’ll impact your development.

If you’re a manager or leader of a team looking to work in PHP 7, this book will help your developers quickly catch up on all the changes they need to know about, and even expose some new features they can take advantage of for faster, better development.

## Contents

[Chapter 1](#chap17.xhtml#chapter-1) summarizes the addition of scalar type hints. This allows your function parameters to explicitly require scalar types like `string`, `int`, `float`, or `bool`.

[Chapter 2](#chap18.xhtml#chapter-2) covers the declaration of function return types, including the scalar types mentioned in [chapter 1](#chap17.xhtml#chapter-1).

In [Chapter 3](#chap19.xhtml#chapter-3) we explore the brand new “Spaceship Operator” which drastically simplifies 3-way comparison of two expressions.

[Chapter 4](#chap20.xhtml#chapter-4) introduces another new operator, the “Null Coalesce Operators”. It’s a lot like `?:` but with a built-in `isset()` check.

[Chapter 5](#chap21.xhtml#chapter-5) demonstrates how to easily add Unicode characters to strings using a new `\u{...}` escape sequence.

[Chapter 6](#chap22.xhtml#chapter-6) reviews how anonymous classes can be used to create classes on-the-fly, which is particularly useful for mocking and implementing simple interfaces (like loggers and observers).

[Chapter 7](#chap23.xhtml#chapter-7) highlights the new ability to include multiple classes from a namespace with a single `use` statement.

[Chapter 8](#chap24.xhtml#chapter-8) introduces the new `Closure:call` method which drastically simplifies binding your closures to objects at call-time.

[Chapter 9](#chap25.xhtml#chapter-9) shows how generator can now `return` final values.

[Chapter 10](#chap26.xhtml#chapter-10) explores how generators can `yield from` arrays, iterators, and other generators (insert Xzibit “yo dawg” joke here).

In [Chapter 11](#chap27.xhtml#chapter-11) we see how PHP 7 drastically simplifies the process of generating strong random numbers for security-critical applications.

[Chapter 12](#chap28.xhtml#chapter-12) demonstrates how to safely and easily perform integer division.

[Chapter 13](#chap29.xhtml#chapter-13) unveils the new `preg_replace_callback_array` function for executing different callbacks per regular expression.

[Chapter 14](#chap30.xhtml#chapter-14) covers the new `IntlChar` class, which helps you work with Unicode characters.

[Chapter 15](#chap32.xhtml#chapter-15) shows how PHP 7 is dramatically faster than previous versions.

[Chapter 16](#chap33.xhtml#chapter-16) describes how syntax is more consistent and flexible.

[Chapter 17](#chap34.xhtml#chapter-17) explains how previously-reserved keywords can be used for property, constant, and method names. It contains a full list of such words.

[Chapter 18](#chap35.xhtml#chapter-18) walks through the new changes to engine errors and exceptions.

[Chapter 19](#chap36.xhtml#chapter-19) highlights the backwards-compatible improvements to the existing `assert()` feature.

[Chapter 20](#chap37.xhtml#chapter-20) touches on how `define()` now supports array constants.

[Chapter 21](#chap38.xhtml#chapter-21) demonstrates how to safely unserialize untrusted data by whitelisting which classes can be unserialized.

[Chapter 22](#chap39.xhtml#chapter-22) talks about configuring session options by passing them into `session_start()`.

[Chapter 23](#chap40.xhtml#chapter-23) outlines the enhancements made to the Reflection API.

[Chapter 24](#chap41.xhtml#chapter-24) shows how some integer behavior has changed in PHP 7.

[Chapter 25](#chap42.xhtml#chapter-25) touches on division by zero, and how it works in the latest version of PHP.

[Chapter 26](#chap43.xhtml#chapter-26) covers the new JSON library used by PHP, including a couple minor changes it introduces.

[Chapter 27](#chap44.xhtml#chapter-27) demonstrates the inconsistencies in PHP 5’s `foreach` loops and how its behavior differs from PHP 7.

[Chapter 28](#chap45.xhtml#chapter-28) describes some adjustments to the behavior of the `list()` construct.

[Chapter 29](#chap46.xhtml#chapter-29) explains some of the changes made to function parameter behavior.

[Chapter 30](#chap47.xhtml#chapter-30) unveils an old bug with custom session handlers and how PHP 7 resolves it.

[Chapter 31](#chap48.xhtml#chapter-31) briefly touches on octals and how PHP 7 handles invalid ones.

[Chapter 32](#chap50.xhtml#chapter-32) discusses the deprecation of PHP 4-style constructors.

[Chapter 33](#chap51.xhtml#chapter-33) covers why manual salt generation is now deprecated in the password hashing API.

[Chapter 34](#chap52.xhtml#chapter-34) lists all of the previously-deprecated functionality which has been fully removed from PHP 7.

[Chapter 35](#chap53.xhtml#chapter-35) talks about the removal of alternative PHP tags.

[Chapter 36](#chap54.xhtml#chapter-36) describes how several `E_STRICT` notices have been changed to other types.

[Chapter 37](#chap55.xhtml#chapter-37) shows how multiple `default` cases are no longer permitted within a `switch` block.

[Chapter 38](#chap56.xhtml#chapter-38) demonstrates PHP 5’s inconsistent handling of hexadecimal strings and why that incomplete functionality was removed.

[Chapter 39](#chap57.xhtml#chapter-39) lists the SAPIs which are no longer supported or maintained.

[Chapter 40](#chap58.xhtml#chapter-40) briefly highlights the removal of that annoying timezone warning.

And finally, [the last section of the book](#chap59.xhtml#bc-breaks) includes a detailed list of all the [breaking changes](#chap59.xhtml#bc-breaks) you’ll need to watch out for when migrating to PHP 7.

## Other resources

These official PHP resources were a huge help during the creation of this book, and you may find them useful:

*   [PHP Manual: Migrating from PHP 5.6.x to PHP 7.0.x](https://secure.php.net/manual/en/migration70.php)
*   [PHP 7 UPGRADING doc](https://github.com/php/php-src/blob/PHP-7.0.0/UPGRADING)
*   [PHP 7 Requests for Comments](https://wiki.php.net/rfc#php_70)
*   [PHPNG (next generation)](https://wiki.php.net/phpng)

There are plenty of other great resources out there too, including some paid and some free ones:

*   [Getting Ready for PHP 7](https://www.digitalocean.com/company/blog/getting-ready-for-php-7/)
*   [What to Expect When You’re Expecting: PHP 7, Part 1](https://blog.engineyard.com/2015/what-to-expect-php-7)
*   [What to Expect When You’re Expecting: PHP 7, Part 2](https://blog.engineyard.com/2015/what-to-expect-php-7-2)
*   [Zend: 5 Things You Must Know About PHP 7](http://www.zend.com/en/resources/php-7)
*   [The PHP 7 Revolution: Return Types and Removed Artifacts](http://www.sitepoint.com/php-7-revolution-return-types-removed-artifacts/)
*   [PHP 7: 10 Things You Need to Know](http://www.hongkiat.com/blog/php7/)
*   [#php7 on Twitter](https://twitter.com/hashtag/php7)
*   [GoPHP7 Extensions Project](http://gophp7.org/gophp7-ext/)
*   [Laracasts - PHP 7 Up and Running](https://laracasts.com/series/php7-up-and-running)

(Any commercial products or services listed here have not been tested or endorsed by the author - they are simply provided as a jumping-off point for your continued PHP 7 education.)

## Acknowledgements

I’d like to thank the following people for making this book possible:

*   All the programmers, testers, documentation writers, RFC authors, and everyone else who has contributed to the success of PHP. I’d have nothing to write about if it wasn’t for you.
*   The PHP community for sharing knowledge and expertise, thereby creating this amazing ecosystem for all developers.
*   Mike Spinosa, Scott Greenwell, Ben Thomas, and the whole team at Unleashed Technologies for encouraging and promoting my continuous growth.
*   Phil Sturgeon for being the catalyst behind my increased community involvement.

### PHP Wiki and Documentation Content

This book includes some content from the [PHP wiki](https://wiki.php.net/), [RFCs](https://wiki.php.net/rfc), and [documentation](https://php.net/docs.php). This content is licensed under [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/us/). All usages (and any modifications) will be noted immediately adjacent to the content within this book.

 begin mainmatter  

# Getting Started with PHP 7

Builds for PHP 7.0 and 7.1 are now available from both official and community repositories. In most cases, these new versions can be easily installed using your system’s package manager.

## Ubuntu 14.04 and 16.04+

[Ondřej Surý](https://launchpad.net/~ondrej) provides a [PPA for installing PHP 7.0 and 7.1](https://launchpad.net/~ondrej/+archive/ubuntu/php). The latest release can be installed using these commands:

```
sudo add-apt-repository ppa:ondrej/php
sudo apt-get update
sudo apt-get install php7.0
```

(Replace `7.0` with `7.1` if desired)

The full list of available packages can be found here: [https://launchpad.net/~ondrej/+archive/ubuntu/php/+packages?field.name\_filter=php7.0](https://launchpad.net/~ondrej/+archive/ubuntu/php/+packages?field.name_filter=php7.0)

## Debian 8 & 9

[Ondřej Surý also provides PHP 7.0 and 7.1 packages for Debian](https://packages.sury.org/php/) which can be installed using these commands:

```
sudo apt-get install apt-transport-https lsb-release ca-certificates
sudo wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg
sudo sh -c "echo 'deb https://packages.sury.org/php/ $(lsb_release -sc) main'" >\
 /etc/apt/sources.list.d/php.list
sudo apt-get update
sudo apt-get install php7.0
```

## Debian 6 & 7

PHP 7.0 can be installed using the [Dotdeb repository](https://www.dotdeb.org/):

Add these two lines to your `/etc/apt/sources.list` file, replacing `<distribution>` with either `squeeze`, `wheezy`, or `jessie`:

```
deb http://packages.dotdeb.org <distribution> all
deb-src http://packages.dotdeb.org <distribution> all
```

Add the GPG key:

```
wget https://www.dotdeb.org/dotdeb.gpg
sudo apt-key add dotdeb.gpg
```

Install PHP 7:

```
sudo apt-get update
sudo apt-get install php7.0
```

The full list of available packages can be found here: [http://packages.dotdeb.org/pool/all/p/php7.0/](http://packages.dotdeb.org/pool/all/p/php7.0/)

## CentOS / RHEL

PHP 7 can be installed using the [Webstatic Yum repository](https://webtatic.com/projects/yum-repository/):

If you’re using CentOS/RHEL 7.x, run these three commands to add the repository and install PHP 7:

```
rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm
yum install php70w
```

If you’re using CentOS/RHEL 6.x, run these two commands to add the repository and install PHP 7:

```
rpm -Uvh https://mirror.webtatic.com/yum/el6/latest.rpm
yum install php70w
```

The full list of available packages (including SAPIs and extensions) can be found here: [https://webtatic.com/packages/php70/#sapi](https://webtatic.com/packages/php70/#sapi)

## Mac OS X

PHP 7 can be installed using [homebrew](https://github.com/Homebrew/homebrew-php):

```
brew tap homebrew/dupes
brew tap homebrew/versions
brew tap homebrew/homebrew-php
brew install php70
```

Or you can install it via [Liip’s php-osx tool](http://php-osx.liip.ch/):

```
curl -s http://php-osx.liip.ch/install.sh | bash -s 7.0
```

## Windows

PHP 7 distributions for Windows can be found on the windows.php.net website: [http://windows.php.net/download#php-7.0](http://windows.php.net/download#php-7.0)

For local development, you could instead use third-party distributions like [XAMPP](https://www.apachefriends.org/index.html) or [EasyPHP](http://www.easyphp.org/). Both come with PHP 7, MySQL, and a web server so you can get up-and-running fast.

## phpbrew

[phpbrew](https://github.com/phpbrew/phpbrew) is a wonderful utility which allows you to easily build and switch between different versions of PHP on the same machine. It supports all modern versions of PHP, including PHP 7.

First we need phpbrew to fetch information about available versions:

```
phpbrew self-update
```

We can then install PHP 7.0, 7.1, or any other version:

```
phpbrew install php-7.0.25
phpbrew use php-7.0.25
```

## Docker

Official Docker images for PHP can be found at [https://hub.docker.com/\_/php/](https://hub.docker.com/_/php/).

```
docker pull php:latest
```

## Vagrant Image

Rasmus Lerdorf, the creator of PHP, provides a Vagrant box image on his GitHub: [https://github.com/rlerdorf/php7dev](https://github.com/rlerdorf/php7dev)

It’s based on Debian 8 and is pre-configured to help develop PHP apps and extensions.

## Build from Source

PHP.net also offers source packages for the alpha and beta releases which you can download and compile yourself. The source code can be downloaded from [https://downloads.php.net/~ab/](https://downloads.php.net/~ab/)

Documentation on compiling PHP 7:

*   https://wiki.php.net/phpng
*   http://www.zimuel.it/install-php-7/
*   http://www.hashbangcode.com/blog/compiling-and-installing-php7-ubuntu

# Part 1 - New Features

Perhaps the most exciting part of PHP 7 are the new features! This part of the book covers these features in detail, including examples of useful applications.

## Chapter 1: Scalar Type Hints

PHP 5 introduced the ability to require function parameters to be of a certain type. This provides a safeguard against invalid uses, like passing a UNIX timestamp to a method which expects a `DateTime` object. It also makes it clear to other developers how the function should be used. For example, compare the following method signatures with and without type hints:

```
// No type hint:
function getNextWeekday($date) { /*...*/ }

// Class type hint (PHP 5):
function getNextWeekday(DateTime $date) { /*...*/ }
```

These hints were initially limited to just classes and interfaces, but was soon expanded to allow `array` and `callable` types too. PHP 7 extends this further by allowing scalar types like `int`, `float`, `string` and `bool`:

```
// Scalar type hint (PHP 7):
function getNextWeekday(int $date) { /*...*/ }
```

### Type Checking Modes

PHP’s flexible type system is one of its most-useful features, allowing numeric strings to be used as integers and vice-versa. This tradition is continued in PHP 7 but now you have the option of enabling strict type enforcement like you’d see in other languages (such as Java or C#). This setting can be enabled using the [`declare` construct](https://php.net/manual/en/control-structures.declare.php).

#### Weak (“Coercive”) Type Checking

“Coercive” mode is the default type checking mode in PHP 7. This is identical to how previous versions of PHP handled scalar type hints for built-in functions. For example, take a look at the method signature for the `floor` function:

```
float floor ( float $value )
```

When you pass in numeric strings or integers PHP auto-converts them to a float automatically. This behavior has simply been extended to userland functions as well.

Here’s a table showing which scalar types are accepted in “Coercive” mode based on the declared type:

Allowed types, coercive mode

 
| Type declaration || int || float || string || bool || object |
| --- | --- | --- | --- | --- | --- |
| int || yes || yes\* || yes† || yes || no |
| --- | --- | --- | --- | --- | --- |
| float || yes || yes || yes† || yes || no |
| string || yes || yes || yes || yes || yes‡ |
| bool || yes || yes || yes || yes || no |

    \* Only non-`NaN` floats between `PHP_INT_MIN` and `PHP_INT_MAX` accepted.

    † If it’s a numeric string

    ‡ Only if object has a `__toString()` method

#### Strong (“Strict”) Type Checking

PHP 7 introduces a new “strict” mode which is enabled by placing `declare(strict_types=1);` at the top of your script like so:

```
<?php
declare(strict_types=1);

function welcome(string $name) {
    echo 'Hello ' . $name;
}

welcome('World'); // Prints: Hello World
```

This declaration enables strict mode for all uses in the entire file, including built-in PHP function calls and return values (see next chapter). It does not affect any included files nor any other files which include it.

Strict mode essentially requires you to pass in exact types declared. If you don’t, a `TypeError` will be thrown. For example, in strict mode, you cannot use numeric strings when a `float` or `int` is expected (like you can in weak/coercive mode):

This throws an error in strict mode 

```
<?php
declare(strict_types=1);

function welcome(string $name) {
    echo 'Hello ' . $name;
}

welcome(3);

// Fatal error: Uncaught TypeError: Argument 1 passed to welcome() must be of th\
e type string, integer given
```

There’s one exception to this rule though, which is that `float` declarations can accept `int` values:

Scope widening example 

```
<?php
declare(strict_types=1);

function add(float $a, float $b): float {
    return $a + $b;
}

add(1, 2); // float(3)
```

Allowed types, strict mode

 
| Type declaration || int || float || string || bool || object |
| --- | --- | --- | --- | --- | --- |
| int || yes || no || no || no || no |
| --- | --- | --- | --- | --- | --- |
| float || yes\* || yes || no || no || no |
| string || no || no || yes || no || no |
| bool || no || no || no || yes || no |

    \* Allowed due to widening primitive conversion

### Mixing Modes

Because the directive is set per-file, it’s entirely possible to mix modes in your application. For example, your strictly-checked app could use a weakly-checked library (or vice versa) without any issues or complications.

### Backwards Compatibility

You may no longer create classes named `int`, `float`, `string` or `bool` as these would conflict with the new scalar type hints.

### Further Reading

*   [RFC: Scalar Type Declarations](https://wiki.php.net/rfc/scalar_type_hints_v5)
*   [PHP Documentation: Type Hinting](https://php.net/manual/en/language.oop5.typehinting.php)

## Chapter 2: Return Type Declarations

In the previous chapter we saw how method parameters can have declared types. With PHP 7 you can also declare what type your method will return. This is done by placing a colon (`:`) and the return type just before the opening curly brace (`{`) like so:

```
function getAuthor(): UserInterface {
    return $this->comment->getUser();
}
```

If you accidentally return something different, like a `string` or a `BlogComment`, PHP will throw a TypeError:

```
function getAuthor(): UserInterface {
    // Let's pretend we forgot the "->getUser()" part:
    return $this->comment;
}

getAuthor();

// Uncaught TypeError: Return value of getAuthor() must be an instance of UserIn\
terface, instance of BlogComment returned
```

This guarantees that your code will always be working with the expected types.

This feature is completely optional though - your PHP 5 style functions will continue to work as usual.

### Returning `null`

Methods with declared return types are **never** allowed to return `null`. Doing so will cause a `Catchable fatal error` to be thrown:

```
class User
{
    public function getBirthday(): \DateTime {
        return null;
    }
}

$user = new User();
$d = $user->getBirthday();

// Uncaught TypeError: Return value of User::getBirthday() must be an instance o\
f DateTime, null returned
```

This matches the behavior of method argument types where `null` cannot be used (unless it’s a default value).

```
class Event
{
    public function setDate(\DateTime $date) {
        // ...
    }
}

$birthdayParty = new Event();
$birthdayParty->setDate(null);

// Uncaught TypeError: Argument 1 passed to Event::setDate() must be an instance\
 of DateTime, null given
```

It also eliminates the need to litter your code with `null` checks (a problem frequently encountered in languages like Java).

Even though `null` return values aren’t currently allowed, there is a [Nullable Types RFC](https://wiki.php.net/rfc/nullable_types) which may provide this ability in the future.

### Sub-Class Methods

Overridden methods in sub-classes must declare the same exact type as the parent method. For example, given the following method:

```
abstract class VehicleFactory
{
    static function create(): Vehicle {
        // ...
    }
}
```

Any classes which extend `VehicleFactory` and override the `create()` method **must** use the same `Vehicle` return type:

```
class CarFactory extends VehicleFactory
{
    static function create(): Vehicle {
        // ...
    }
}

class TruckFactory extends VehicleFactory
{
    static function create(): Vehicle {
        // ...
    }
}
```

This is required because the method signature enforcement is invariant; you’re not able to define a more-specific return type or PHP will raise an error:

```
class CarFactory extends VehicleFactory
{
    static function create(): Car {
        // ...
    }
}

// Fatal error: Declaration of CarFactory::create() must be compatible with Vehi\
cleFactory::create(): Vehicle
```

Even though `Car` extends from `Vehicle`, making it covariant, the return type *declaration* must remain exactly the same.

If the parent didn’t declare a return type then the child may optionally declare any type (if desired). For example, all of the following are allowed:

```
interface CacheInterface
{
    public function get($key);
}

// No return type
class SimpleCache implements CacheInterface
{
    public function get($key) {
        // ...
    }
}

// Returns a string
class HtmlCache implements CacheInterface
{
    public function get($key): string {
        // ...
    }
}

// Returns a certain object type
class DatabaseQueryCache implements CacheInterface
{
    public function get($key): QueryResult {
        // ...
    }
}
```

### Further Reading

*   [RFC: Return Type Declarations](https://wiki.php.net/rfc/return_types)

## Chapter 3: Combined Comparison (Spaceship) Operator

PHP 7 introduces a new three-way comparison operator `<=>` (`T_SPACESHIP`) which takes two expressions: `(expr) <=> (expr)`. It compares both sides of the expression and, depending on the result, returns one of three values:

| 0 || If both expressions are equal |
| --- | --- |
| 1 || If the left is greater |
| \-1 || If the right is greater |

You may be familiar with this if you’ve worked with existing comparison functions like `strcmp` before.

It has the same precedence as the equality operator (`==`, `===`, `!=`, `!==`) and behaves identically to the [existing comparison operators](http://php.net/manual/en/language.operators.comparison.php) (`<`, `<=`, `==`, `>=`, `>`).

### Comparing Values

You can compare everything from scalar values (like `int`s and `float`s) to arrays and even objects too. Here are some examples from the [relevant RFC](https://wiki.php.net/rfc/combined-comparison-operator):

PHP RFC examples (licensed under CC BY 3.0) 

```
// Integers
echo 1 <=> 1; // 0
echo 1 <=> 2; // -1
echo 2 <=> 1; // 1

// Floats
echo 1.5 <=> 1.5; // 0
echo 1.5 <=> 2.5; // -1
echo 2.5 <=> 1.5; // 1

// Strings
echo "a" <=> "a"; // 0
echo "a" <=> "b"; // -1
echo "b" <=> "a"; // 1

echo "a" <=> "aa"; // -1
echo "zz" <=> "aa"; // 1

// Arrays
echo [] <=> []; // 0
echo [1, 2, 3] <=> [1, 2, 3]; // 0
echo [1, 2, 3] <=> []; // 1
echo [1, 2, 3] <=> [1, 2, 1]; // 1
echo [1, 2, 3] <=> [1, 2, 4]; // -1

// Objects
$a = (object) ["a" => "b"];
$b = (object) ["a" => "b"];
echo $a <=> $b; // 0

$a = (object) ["a" => "b"];
$b = (object) ["a" => "c"];
echo $a <=> $b; // -1

$a = (object) ["a" => "c"];
$b = (object) ["a" => "b"];
echo $a <=> $b; // 1

// only values are compared
$a = (object) ["a" => "b"];
$b = (object) ["b" => "b"];
echo $a <=> $b; // 0
```

### Sorting

Perhaps the best application of this operator is to simplify sorting, as functions like `usort` expect you to perform a comparison and return `-1`, `0`, or `1` accordingly:

This simplification is especially apparent when comparing objects by some property value:

```
class Spaceship {
    public $name;
    public $maxSpeed;

    public function __construct($name, $maxSpeed) {
        $this->name = $name;
        $this->maxSpeed = $maxSpeed;
    }
}

$spaceships = [
    new Spaceship('Rebel Transport', 20),
    new Spaceship('Millenium Falcon', 80),
    new Spaceship('X-Wing Starfighter', 80),
    new Spaceship('TIE Bomber', 60),
    new Spaceship('TIE Fighter', 100),
    new Spaceship('Imperial Star Destroyer', 60),
];

// Sort the spaceships by name (in ascending order)
usort($spaceships, function ($ship1, $ship2) {
    return $ship1->name <=> $ship2->name;
});

echo $spaceships[0]->name; // "Imperial Star Destroyer"

// Sort the spaceships by speed (in descending order)
// Notice how we switch the position of $ship1 and $ship2
usort($spaceships, function ($ship1, $ship2) {
    return $ship2->maxSpeed <=> $ship1->maxSpeed;
});

echo $spaceships[0]->name; // "TIE Fighter"
```

Without the comparison operator, these functions would be much more complex:

```
usort($spaceships, function ($ship1, $ship2) {
    if ($ship1->maxSpeed == $ship2->maxSpeed) {
        return 0;
    } elseif ($ship1->maxSpeed < $ship2->maxSpeed) {
        return 1;
    } else {
        return -1;
    }
});
```

### Sorting by multiple values

You can take advantage of the array comparison behavior to easily sort by multiple fields:

```
// Sort by speed (asc), then by name (asc)
usort($spaceships, function ($ship1, $ship2) {
    return [$ship1->maxSpeed, $ship1->name] <=> [$ship2->maxSpeed, $ship2->name];
});

foreach ($spaceships as $ship) {
    printf("%3d is the max speed of a(n) %s\n", $ship->maxSpeed, $ship->name);
}

// Outputs:
//  20 is the max speed of a(n) Rebel Transport
//  60 is the max speed of a(n) Imperial Star Destroyer
//  60 is the max speed of a(n) TIE Bomber
//  80 is the max speed of a(n) Millenium Falcon
//  80 is the max speed of a(n) X-Wing Starfighter
// 100 is the max speed of a(n) TIE Fighter
```

### Further Reading

*   [RFC: Combined Comparison (Spaceship) Operator](https://wiki.php.net/rfc/combined-comparison-operator)
*   [PHP Manual: Comparison Operators](https://secure.php.net/manual/en/language.operators.comparison.php)

## Chapter 4: Null Coalesce Operator

Dealing with `null` objects can be annoying (just ask any Java developer). The new “null coalesce operator” (`??`) makes life easier by combining ternary operator functionality (`?:`) with `isset` checks:

```
$sortBy = $_GET['sort'] ?? 'date';
```

It takes two expressions, returning the left one if it’s not `null`, or the right one otherwise. This makes it easy to provide an alternative value instead of a `null`.

This is particularly useful when dealing with array keys which may not exist. If you tried using `?:` for this purpose, you’d get an `E_NOTICE` if the `sort` key wasn’t present:

```
$sortBy = $_GET['sort'] ?: 'date'; // E_NOTICE
```

We’d need to add an extra check to avoid this problem, but the code becomes too verbose:

```
// This is too verbose
if (isset($_GET['sort'])) {
    $sortBy = $_GET['sort'];
} else {
    $sortBy = 'desc';
}

// This isn't much better
$sortBy = isset($_GET['sort']) ? $_GET['sort'] : 'date';
```

Or, with the null coalesce operator, we simply do this:

```
// Super easy!
$sortBy = $_GET['sort'] ?? 'date';
```

### Differences From `?:`

You may be thinking that this is awfully similar to the short ternary operator (‘?:’) and you’d be right, but two important distinctions:

*   `??` checks if the left-side expression exists (as seen above).
*   `??` will return the left side for `false` values, whereas `?:` would return the right side. For example:

```
var_dump(false ?: 'foo');
// Displays: string(3) "foo"

var_dump(false ?? 'foo');
// Displays: bool(false)
```

### Chaining

You can even chain several operators together if you want to. This is useful in situations where you’d like to return the first available value of several array keys:

```
$user = json_decode('{"username": "jsmith", "firstName": "John", "lastName": "Sm\
ith" }', true);

// Display the user's nickname, falling-back to their firstName or username if n\
one exists.
printf('Welcome back %s!', $user['nickname'] ?? $user['firstName'] ?? $user['use\
rname']);

// Displays "Welcome back John!"
```

### Further Reading

*   [RFC: Null Coalesce Operator](https://wiki.php.net/rfc/isset_ternary)

## Chapter 5: Unicode Codepoint Escape Syntax

PHP’s lack of native Unicode support can make things difficult when coding for the web. While libraries like `iconv` and `mbstring` have simplified working with strings, there were no simple mechanisms available to create Unicode characters or strings without converting them from an HTML or JSON representation:

Workaround examples 

```
$char = html_entity_decode('&#x2603', 0, 'UTF-8');
$char = mb_convert_encoding('&#x2603', 'UTF-8', 'HTML-ENTITIES');
$char = json_decode('"\\u2603"');
```

PHP 7 finally introduces native support for Unicode character escape sequences within strings, just like you’d see in Ruby or ECMAScript 6:

```
$char = "\u{2603}";
```

This makes it much easier (and quicker) to embed Unicode characters, especially ones that aren’t easily typed. These can be used in strings alongside other characters too. For example, here’s the `U+202E RIGHT-TO-LEFT OVERRIDE` character being used to display the string in reverse:

```
echo "\u{202E}This is backwards"; // displays: sdrawkcab si sihT
```

You can omit leading `0`s if you’d like:

```
echo "\u{58}"; // "X"
echo "\u{0058}"; // "X"
```

### Why the `{}`s?

Some other languages (C/C++/Java) use a format without the `{}` characters: `\uXXXX`. Unfortunately this limits their use to the Basic Multilingual Plane (`U+0000` to `U+FFFF`). However, Unicode supports other characters beyond 16 bits.

For example, if we wanted to represent the `U+1F427 PENGUIN` emoji, our escape sequence would look something like this: `\u1F427`. Most languages would intepret this as `U+1F42 GREEK SMALL LETTER OMICRON WITH PSILI AND VARIA` plus a `7`, which is not what we want. In these languages, you’d have to encode it using two 16-bit sequences like this: `\uD83D\uDC27`. This isn’t very clear though.

Wrapping with `{}` characters allows us to easily go beyond that 16-bit limitation without sacrficing clarity: `\u{1F427}`

### Limitations

This feature follows the behavior of all other escape sequences in PHP - they can only be used within double-quoted strings and heredocs:

Example usage 

```
$foo = "\u{2109}\u{2134}\u{2134}";
// ℉ℴℴ

$bar = <<<EOT
    \u{212C}\u{212B}\u{211D}
EOT;
// ℬÅℝ
```

And like other sequences such as `\t`, they will *not* be expanded when they occur in single-quoted strings or nowdocs:

These will not work 

```
$foo = '\u{2109}\u{2134}\u{2134}';
// \u{2109}\u{2134}\u{2134}

$bar = <<<'EOT'
    \u{212C}\u{212B}\u{211D}
EOT;
// \u{212C}\u{212B}\u{211D}
```

### Backwards Compatibility

Double-quoted strings and heredocs containing `\u{` followed by an invalid sequence will now result in an error. This can be avoided by escaping the leading backslash with another backslash (`\\u{`).

### Further Reading:

*   [RFC: Unicode Codepoint Escape Syntax](https://wiki.php.net/rfc/unicode_escape)

## Chapter 6: Anonymous Classes

PHP 5.3 gave us the ability to create anonymous functions (also known as “closures”). Version 7 takes this idea one step further, allowing us to create anonymous classes. You may be familiar with this concept if you’ve worked with other object-oriented language like C# and Java which support this same feature.

These are virtually identical to named classes, but without the name (just like named functions vs. anonymous ones). Even the syntax looks similar:

```
$wrapper = new class($foo) {
    public function __construct($var) {
        $this->var = $var;
    }
}
```

Anonymous classes support inheritance and traits too. This makes it trivial to implement lightweight interfaces on-the-fly:

```
$httpClient->setLogger(new class implements SimpleLoggerInterface {
    public function log($data) {
        file_put_contents('http.log', $data, FILE_APPEND);
    }
});

$authHandler->addListener(new class implements AuthenticationEventListener {
    public function onAuthSuccess (AuthEvent $event) {
        // ...
    }

    public function onAuthFailure (AuthEvent $event) {
        // ...
    }
});
```

You can even extend other classes, use traits, and implement constructors:

```
$email = new class($user) extends AbstractEmailMessage implements LoggerAwareInt\
erface {
    private $logger;
    private $user;

    use MarkdownConverterTrait;

    public function __construct($user) {
        $this->user = $user;
    }

    public function setLogger(LoggerInterface $logger) {
        $this->logger = $logger;
    }
}
```

### Nesting Classes

You can absolutely nest an anonymous class within another class. However, this will not automatically give that inner anonymous class access to the outer scope:

```
class Outer
{
    protected $var = 1;

    public function foo()
    {
        return new class() {
            public function bar() {
                // THIS WILL NOT WORK
                return $this->var;
            }
        }
    }
}
```

You’ll either need to pass those values in via the constructor, or extend from the outer class:

```
class Outer
{
    protected $var = 1;

    public function foo()
    {
        return new class() extends Outer {
            public function bar() {
                // This works just fine
                return $this->var;
            }
        }
    }
}
```

### Use Cases

While you should be careful not to overuse anonymous classes, they do have many useful applications including:

*   Creating simple, single-use classes
*   Quickly implementing a light-weight interface (like a logger or event observer)
*   Overriding a single field/method of a class without having to subclass it
*   Mocking tests by creating implementations on-the-fly
*   Creating a simple wrapper around something
*   Creating a nested inner class with access to protected members of the outer class

### Differences from Named Classes

#### Auto-Generated Names

PHP will automagically generate a unique name for your anonymous class based on its address in memory and whether it extends a named class. Multiple anonymous classes created in the same position (factory method, in a loop, etc) will always have the same name.

```
<?php
function createClass() {
    return new class {};
}

// Call the above factory method multiple times.
// Note how we get the same class name.
echo get_class(createClass()); // class@0x7fcb8fc76035
echo get_class(createClass()); // class@0x7fcb8fc76035
echo get_class(createClass()); // class@0x7fcb8fc76035

// Create another anonymous class using the same syntax.
// Note how the name is different even though it appears to be identical.
echo get_class(new class {});  // class@0x7fcb8fc760be
```

#### Equivalence

Anonymous classes can be tested for equivalence using the `==` operator. Classes which were defined in the same location (and thus have the same name) will be equal. An identical class created elsewhere will not be equal since it has a different name.

#### Serialization

Anonymous classes cannot be serialized. Attempting to do so will result in an error, just like anonymous functions do.

#### Reflection

You can test whether a class is anonymous using `ReflectionClass::isAnonymous()`.

### Further Reading:

*   [RFC: Anonymous Classes](https://wiki.php.net/rfc/anonymous_classes)
*   [Example usage of anonymous classes (from Oracle’s Java documentation)](https://docs.oracle.com/javase/tutorial/java/javaOO/anonymousclasses.html)

## Chapter 7: Group Use Declarations

Developers frequently find themselves needing to import several classes from the same namespace. This usually results in a large number of `use` statements poluting the top of their classes - here’s an example from Symfony’s `AbstractToken` class:

```
<?php

namespace Symfony\Component\Security\Core\Authentication\Token;

use Symfony\Component\Security\Core\Role\RoleInterface;
use Symfony\Component\Security\Core\Role\Role;
use Symfony\Component\Security\Core\User\UserInterface;
use Symfony\Component\Security\Core\User\AdvancedUserInterface;
use Symfony\Component\Security\Core\User\EquatableInterface;
```

PHP 7 simplifies this by allowing us to import several classes with a single declaration much like other languages do (such as Rust, Scala, and Python):

```
<?php

namespace Symfony\Component\Security\Core\Authentication\Token;

use Symfony\Component\Security\Core\Role\{ RoleInterface, Role };
use Symfony\Component\Security\Core\User\{ UserInterface, AdvancedUserInterface,\
 EquatableInterface};
```

These declaration can even span multiple lines, if desired:

```
<?php

namespace Symfony\Component\Security\Core\Authentication\Token;

use Symfony\Component\Security\Core\Role\{
    RoleInterface,
    Role,
};
use Symfony\Component\Security\Core\User\{
    UserInterface,
    AdvancedUserInterface,
    EquatableInterface,
};
```

In addition to being less verbose and redundant, it also helps clarify which namespaces are being used. This is particularly nice when reviewing diffs and patches, as the change is more pronounced and readable. Compare the old way…

```
  use League\CommonMark\Block\Element\AbstractBlock;
  use League\CommonMark\Block\Element\AbstractInlineContainer;
  use League\CommonMark\Block\Element\Document;
+ use League\CommonMark\Block\Element\ListBlock;
  use League\CommonMark\Block\Element\Paragraph;
  use League\CommonMark\Util\TextHelper;
```

To this:

```
  use League\CommonMark\Block\Element\{
      AbstractBlock,
      AbstractInlineContainer,
      Document,
+     ListBlock,
      Paragraph,
}
use League\CommonMark\Util\TextHelper;
```

The change is much clearer in the second example.

### Compound Namespaces

Compound namespace support allows you to group the namespaces like so:

```
<?php

namespace Symfony\Component\Security\Core\Authentication\Token;

use Symfony\Component\Security\Core\{
    Role\RoleInterface,
    Role\Role,
    User\UserInterface,
    User\AdvancedUserInterface,
    User\EquatableInterface,
};
```

### Further Reading:

*   [RFC: Group Use Declarations](https://wiki.php.net/rfc/group_use_declarations)

## Chapter 8: Closure `call` Method

PHP 5.4 introduced the ability to bind `$this` to any given object using either the `Closure::bind` static method or the `Closure::bindTo` method:

```
// Here's a class which hold a secret number
class SecretNumber { private $secretNumber = 3; }
// Here's a closure which can reveal it
$revealer = function() { return $this->secretNumber; };

// In order to use it in PHP 5.4-5.6, we must first
// bind the scope to a temporary intermediate closure:
$boundRevealer = $revealer->bindTo(new SecretNumber(), 'SecretNumber');

// And now we can use it:
echo $boundRevealer(); // 3
```

PHP 7 simplifies this process by adding a new `call` method:

```
mixed Closure::call(object $to[, mixed ...$parameters])
```

This eliminates the need to create a temporary closure first - you simply just call `call()` with your object scope and any parameters:

```
// Here's a class which hold a secret number
class SecretNumber { private $secretNumber = 3; }
// Here's a closure which can reveal it
$revealer = function() { return $this->secretNumber; };

// Just call it directly
echo $revealer->call(new SecretNumber()); // 3
```

In addition to simplifying your code, this approach also improves performance since that intermediate closure is no longer created.

This new `call` method can be used in most cases where you’re calling `bind` or `bindTo` followed by a closure invocation.

### Further Reading:

*   [RFC: Closure::call](https://wiki.php.net/rfc/closure_apply)
*   [PHP Manual: `Closure::call`](https://secure.php.net/manual/en/closure.call.php)

## Chapter 9: Generator Return Expressions

The `yield` keyword allows generators to provide the result of each individual step. This works perfectly for “streaming” large amounts of data. Generators can also break large computations into smaller units of work, allowing the function to suspend itself and resume later. In these cases, it’s especially useful to have a standard way of accessing the final results of those computations.

To demonstrate the use of return expressions, let’s build a function which computes the size of all files within a directory, yielding its current progress along the way:

```
function calculateSize($directory) {
    $size = 0;
    $count = 0;
    foreach (scandir($directory) as $entry) {
        if (is_file($entry)) {
            $size += filesize($entry);
            yield $count++;
        }
    }

    return $size;
}

$task = calculateSize('./downloads');
foreach ($task as $step) {
    echo "Processed $step files so far\n";
}

echo "Total size: " . $task->getReturn();
```

Prior to PHP 7, that `return $size` would have thrown an error since returning from generators wasn’t supported. You’d have to use a workaround like this instead:

```
function calculateSize($directory) {
    $size = 0;
    $count = 0;
    foreach (scandir($directory) as $entry) {
        if (is_file($entry)) {
            $size += filesize($entry);
            yield $count++;
        }
    }

    yield $size;
}
```

(Ab)using the final `yield` as a return value technically works but has two major shortcomings:

*   Consumers should be able to rely on yielded values having the same types and meanings
*   It isn’t unambiguously clear that this is a final result and no other work will be done

This becomes especially important when you’re trying to multitask several different processes:

```
function downloadAndZipAFile($url) {
    $download = yield downloadFromInternet($url);

    $zipFile = yield compressAndSave($download);

    yield 'user/uploads/' . $zipFile;
}
```

In that example, we’re yielding three times, but only two of them are actual steps. It would be much cleaner and easier to understand if we used a simple return instead:

```
function downloadAndZipAFile($url) {
    $download = yield downloadFromInternet($url);

    $zipFile = yield compressAndSave($download);

    return 'user/uploads/' . $zipFile;
}
```

### Further Reading:

*   [RFC: Generator Return Expressions](https://wiki.php.net/rfc/generator-return-expressions)

## Chapter 10: Generator Delegation

PHP 7 introduces new `yield from` syntax which allows generators to delegate operations to arrays, `Traversable` objects, or even other generators. This allows work to be broken up into smaller units of code, much like you’d break classes or functions up into several smaller bits.

This feature allows full bi-directional communication between the delegating generator and the sub-generator:

*   Values are yielded directly through the delegating generator to its caller
*   Values sent into the delegating generator’s `send()` method are also passed directly to the sub-generator’s `send()` method
*   Any thrown exceptions are also propogated to the delegating generator
*   Return values an be captured and passed through

Let’s walk through each of these in detail.

### Yielding Values

Here’s a simple example of a generator:

```
function main() {
    // Process the first value
    yield 'a';

    // Process a bunch of values
    yield 'b';
    yield 'c';
    yield 'd';

    // Process one more value
    yield 'e';
}

foreach (main() as $letter) {
    var_dump($letter);
}

/*
string(1) "a"
string(1) "b"
string(1) "c"
string(1) "d"
string(1) "e"
*/
```

What if we wanted to break the `Processing a bunch of values` bit into a separate generator? We can use the `yield from <expr>` syntax to do just that. This will advance through the given traversable `<expr>`, yielding each value directly to the original caller.

```
function subGenerator() {
    yield 'b';
    yield 'c';
    yield 'd';
}

function main() {
    // Process the first value
    yield 'a';

    // Process a bunch of values
    yield from subGenerator();

    // Process one more value
    yield 'e';
}

foreach (main() as $number) {
    var_dump($number);
}

/*
string(1) "a"
string(1) "b"
string(1) "c"
string(1) "d"
string(1) "e"
*/
```

As mentioned earlier, you can also delegate to arrays and `Iterable`s. These two functions would produce the same output as above:

```
function main() {
    // Process the first value
    yield 'a';

    // Process a bunch of values
    yield from ['b', 'c', 'd'];

    // Process one more value
    yield 'e';
}
```

```
function main() {
    // Process the first value
    yield 'a';

    // Process a bunch of values
    yield from new ArrayIterator(['b', 'c', 'd']);

    // Process one more value
    yield 'e';
}
```

### Sending Values

Values can also be sent into sub-generators. This is especially useful in the context of coroutines where data is sent into the function during execution:

```
// Generates random numbers until told to stop
// If you don't send that command it'll loop forever
function getRandomNumbers() {
    while (true) {
       $cmd = (yield rand(1, 10));
       if ($cmd == 'stop') {
           break;
       }
    }
}

// Combines two "infinite streams" of random numbers
function foo() {
    yield from getRandomNumbers();
    yield from getRandomNumbers();
}

$generator = foo();
foreach ($generator as $randomNumber) {
    var_dump($randomNumber);

    // Stop the generator once we get a 3
    if ($randomNumber == 3) {
        $generator->send('stop');
    }
}

/*
int(4)
int(7)
int(5)
int(1)
int(8)
int(3) // The first "stream" of random numbers stops here
int(5)
int(9)
int(3) // The second one stops here
*/
```

### Exceptions

Thrown exceptions will bubble up as usual:

```
function a() {
    yield 1;
    yield 2;

    throw new Exception('oh noes!');
}

function b() {
    yield 'foo';
    yield from a();
    yield 'bar';
}

foreach (b() as $var) {
    var_dump($var);
}

/*
string(3) "foo"
int(1)
int(2)

Fatal error: Uncaught Exception: oh noes! in /tmp/gen.php:7
Stack trace:
#0 /tmp/gen.php(12): a()
#1 /tmp/gen.php(16): b()
#2 {main}
  thrown in /tmp/gen.php on line 7
*/
```

There are also two specific cases where using `yield from` may throw an `EngineException`:

1.  Attempting to `yield from` something other than an array or `Traversable`
2.  Attempting to `yield from` a generator which previously threw an uncaught exception

### Return Values

If `<expr>` happens to a sub-generator then `yield from <expr>` will provide the eventual return value of that sub-generator:

```
function a() {
    yield 1;
    yield 2;

    return 42;
}

function b() {
    yield 'foo';
    $retVal = yield from a();
    yield 'bar';
    return $retVal;
}

$generator = b();
foreach ($generator as $var) {
    var_dump($var);
}
var_dump($generator->getReturn());

/*
string(3) "foo"
int(1)
int(2)
string(3) "bar"
int(42)
*/
```

* * *

To summarize: with delegation, it doesn’t matter to your callers whether the `yield`s exist in the main generator or a sub-generator; receiving and sending values will always behave consistently as you’d expect them to.

### Further Reading:

*   [RFC: Generator Delegation](https://wiki.php.net/rfc/generator-delegation)

## Chapter 11: Reliable User-land CSPRNG

PHP 7 introduces a cryptographically-secure psueod-random number generator (CSPRNG) API which vastly simplifies the process of generating high-quality random data:

```
random_bytes(int length);

random_int(int min, int max);
```

These methods produce “cryptographicaly-secure” random numbers which are suitable for high-stakes applications like generating encryption keys, salting passwords, shuffling card decks, etc.

If you wanted to generate such values in previous versions of PHP, you’d need to write code to interface with mcrypt/openssl or directly access `/dev/*random`. This technically worked but your code wouldn’t be portable because of the hard-coded dependencies on the library or OS you coded against.

With PHP 7, you simply call `random_bytes` or `random_int` and PHP will intelligently select the best available source of randomness on the current machine. This could be:

*   `CryptGenRandom` for Windows environments
*   `arc4random_buf()` if available (generally BSD specific)
*   `/dev/arandom` or `/dev/urandom`

If no sufficient source of randomness is available, an error will be thrown.

### Backwards Compatibility

You may no longer define functions named `random_int()` or `random_bytes()` in the global namespace.

### Forwards Compatibility

The [`paragonie/random_compat` library](https://github.com/paragonie/random_compat) back-ports these new functions to PHP 5.x. Simply drop this into your application and it’ll define those functions if they don’t exist, thus allowing you to write secure code which runs on both 5.x and 7.

### Further Reading

*   [RFC: Easy User-land CSPRNG](https://wiki.php.net/rfc/easy_userland_csprng)
*   [PHP Manual: CSPRNG Functions](http://us3.php.net/manual/en/ref.csprng.php)
*   [How to Safely Generate Random Strings and Integers in PHP](https://paragonie.com/blog/2015/07/how-safely-generate-random-strings-and-integers-in-php)
*   [ircmaxell: Random Number Generation in PHP](http://blog.ircmaxell.com/2011/07/random-number-generation-in-php.html)

## Chapter 12: Integer Division

PHP has historically lacked the ability to perform integer division. For example, if you were to divide `5 / 2`, you’d always get a float value of `2.5`; should you want an integer result instead, you’d have to cast it like so: `(int) 5 / 2`. This works okay for most applications, especially where smaller numbers are involved. However, because the result is a float, you’re subjected to a significant limitation: **floats cannot accurately represent integers greater than 53 bits**.

In order to avoid this limitation (and the need for a cast-based workaround), PHP 7 has introduced a new `intdiv()` method:

```
intdiv(int $numerator, int $divisor)
```

It works exactly as you’d expect, dividing two integers and providing an integer result. It doesn’t use utilize floating-point division, thus avoiding that 53-bit limitation.

If `$divisor` is 0, the function will throw a `DivisionByZeroError`.

### Backwards Compatibility

You may no longer create functions named `intdiv()` in the global namespace.

### Further Reading

*   [RFC: intdiv()](https://wiki.php.net/rfc/intdiv)
*   [PHP Manual: intdiv()](https://secure.php.net/manual/en/function.intdiv.php)

## Chapter 13: preg\_replace\_callback\_array

`preg_replace_callback_array` is a new PCRE function which enables you find and replace multiple patterns using callbacks:

```
preg_replace_callback_array(array $pattern, $subject, $limit, &$count)
```

Here’s an example of this in action:

```
$song = "99 bottles of beer on the wall\n99 bottles of beer\nTake one down, pass\
 it around\n98 bottles of beer on the wall";

echo preg_replace_callback_array([
    '/bottles of (beer|ale|cider)/' => function($matches) {
        return 'little bugs';
    },
    '/on the (wall|table|floor)/' => function($matches) {
        return 'in the code';
    },
    '/pass/' => function($matches) {
        return 'patch';
    },
    '/98/' => function($matches) {
        return rand(100, 200);
    },
], $song);

/**
 * 99 little bugs in the code
 * 99 little bugs
 * Take one down, patch it around
 * 146 little bugs in the code
 */
```

This type of functionality used to be possible prior to PHP 5.5.0, using the `/e` modifier:

```
$song = "99 bottles of beer on the wall\n99 bottles of beer\nTake one down, pass\
 it around\n98 bottles of beer on the wall";

echo preg_replace(
    [
        '/bottles of (beer|ale|cider)/',
        '/on the (wall|table|floor)/',
        '/pass/',
        '/98/e',
    ],
    [
        'little bugs',
        'in the code',
        'patch',
        'rand(100, 200)',
    ],
    $song
);

/**
 * 99 little bugs in the code
 * 99 little bugs
 * Take one down, patch it around
 * 179 little bugs in the code
 */
```

However, the `/e` modifier was deprecated in PHP 5.5.0, thus removing the ability to pair a matched pattern with a callback. The introduction of `preg_replace_callback_array` re-enables this functionality.

### Backwards Compatibility

You may no longer define functions named `preg_replace_callback_array()` in the global namespace.

### Further Reading

*   [RFC: preg\_replace\_callback\_array](https://wiki.php.net/rfc/preg_replace_callback_array)

## Chapter 14: `IntlChar` Class

PHP supports internationalization (i18n) and localization (l10n) via the `intl` extension. This extension is basically just a wrapper around the ICU library and therefore provides near-identical methods and features.

PHP 7 exposes ICU’s Unicode character features via the new [`IntlChar` class](https://secure.php.net/manual/en/class.intlchar.php). This class contains 600 constants and 59 static methods, so we won’t cover them all, but here are some examples you may find useful:

```
// Returns the Unicode allocation block that contains the character.
public static function getBlockCode(mixed $codepoint): int;

// Determines whether the specified code point is a letter character.
static public function isalpha(mixed $codepoint): bool;

// Determines whether the specified code point is a punctuation character.
static public function ispunct(mixed $codepoint): bool;

// Determines whether the specified code point is a "graphic" character
// (printable, excluding spaces).
static public function isgraph(mixed $codepoint): bool;

// Determines whether the specified code point is a "blank" or
// "horizontal space", a character that visibly separates words on a line.
static public function isblank(mixed $codepoint): bool;

// The given character is mapped to its lowercase equivalent; if the character
// has no lowercase equivalent, the character itself is returned.
static public function tolower(mixed $codepoint): mixed;

// Retrieve the name of a Unicode character.
static public function charName(mixed $codepoint, int $nameChoice = IntlChar::UN\
ICODE_CHAR_NAME)
```

### Backwards Compatibility

You may no longer create classes named `IntlChar` in the global namespace.

### Further Reading

*   [RFC: IntlChar class](https://wiki.php.net/rfc/intl.char)
*   [PHP Manual: IntlChar](https://secure.php.net/manual/en/class.intlchar.php)
*   [ICU 55.1: uchar.h File Reference](https://ssl.icu-project.org/apiref/icu4c/uchar_8h.html#func-members)

# Part 2 - Language Changes & Improvements

PHP 7 includes several major improvements to the language, as well as some changes to existing features.

Learn about the features and changes which make PHP 7 faster and more flexible than ever!

## Chapter 15: Performance

PHP 7 is faster than ever. Most real-world applications will see a 100%+ boost in performance simply by upgrading! Here are some actual benchmarks from the Zend Performance Team^([1](#chap63.xhtml#fn-zendbenchmarks)):

![Zend Performance Team Benchmarks](images/benchmark.png)

Zend Performance Team Benchmarks

This improvement is largely due to the PHPNG (PHP Next-Gen) project which refactored the Zend Engine to be super-performant. Some of the under-the-hood changes include things like:

*   Using more-compact data structures
*   Reducing the number of heap allocations and deallocations
*   Utilizing native thread local storage

The net result is a faster PHP which also uses less memory. These changes also pave the way for future improvements, like JIT compilation, which will make PHP even faster.

### Further Reading

*   [Zend: Turbocharging the Web with PHP 7](https://www.zend.com/en/resources/php7_infographic)
*   [Rasmus Lerdorf - PHP Australia Keynote](http://talks.php.net/oz15#/)

## Chapter 16: Language Consistency

PHP 7’s syntax is now more consistent and flexible than before, thanks to two major changes: Uniform Variable Syntax and the addition of an Abstract Syntax Tree.

### Uniform Variable Syntax

PHP 7 supports several new types of expressions which weren’t possible in previous versions:

Source: RFC: Uniform Variable Syntax RFC 

```
// support missing combinations of operations
$foo()['bar']()
[$obj1, $obj2][0]->prop
getStr(){0}

// support nested ::
$foo['bar']::$baz
$foo::$bar::$baz
$foo->bar()::baz()

// support nested ()
foo()()
$foo->bar()()
Foo::bar()()
$foo()()

// support operations on arbitrary (...) expressions
(...)['foo']
(...)->foo
(...)->foo()
(...)::$foo
(...)::foo()
(...)()

// two more practical examples for the last point
(function() { ... })()
($obj->closure)()

// support all operations on dereferencable scalars (not very useful)
"string"->toLower()
[$obj, 'method']()
'Foo'::$bar
```

You’ve probably tried using these types of expressions in the past and were surprised when they didn’t work - I know I certainly was. Getting these expressions to work as expected required re-thinking the fundamental problem of handling the variable-variable syntax: `$$foo['bar']`. In PHP 5, this expression was interpreted from right-to-left: evaluate `$foo['bar']` and then lookup the variable with that name. This methodology ultimately prevented left-to-right interpretation, which would be required for all the examples listed above.

PHP 7 eliminates that special case and interprets all expressions from left-to-right. `$$foo['bar']` is now interpreted as “take the value of `$$foo` and lookup the value at key `bar`”. Here are several other example from the RFC demonstrating the change:

```
                        // old meaning            // new meaning
$$foo['bar']['baz']     ${$foo['bar']['baz']}     ($$foo)['bar']['baz']
$foo->$bar['baz']       $foo->{$bar['baz']}       ($foo->$bar)['baz']
$foo->$bar['baz']()     $foo->{$bar['baz']}()     ($foo->$bar)['baz']()
Foo::$bar['baz']()      Foo::{$bar['baz']}()      (Foo::$bar)['baz']()
```

Additionally, global keywords now only accept simple variables:

```
// Invalid in PHP 7:
global $$foo->bar;

// Use this instead:
global ${$foo->bar};
```

#### Backwards Compatibility

As shown above, this change will break backwards compatibility in these types of variable-variable dereference expressions. Thankfully this isn’t very common, so realistically the impact is fairly low.

If you need an expression to be evaluated in a certain way, you can always use the `{}` characters to enforce the desired behavior. This will make the code compatible with both 5.x and 7.x.

### Abstract Syntax Tree

Previous versions of PHP would emit opcodes directly from the parser as it read through your code. While this worked fine in most cases, it sometimes led to some strange behavior requiring hacks, workarounds, or artificial limitations.

PHP 7 fixes this by fully decoupling the parser from the compiler by using an Abstract Syntax Tree (AST) - a common technique in other languages. In addition to making the engine easier to maintain, it also allows several syntax issues to be resolved:

*   Using `yield` in expressions no longer requires parentheses
*   Expressions like `($foo['bar'])` and `$foo['bar']` now behave identically
*   The `__clone()` magic method can be called directly

Implementing an AST could also enable the future implementation of features common in other languages, such as:

*   Array deconstruction without using `list`: `[$foo, $bar] = $array`
*   Python-like expressions such as `$x*$x for $x in $list`
*   LINQ-style expressions

#### Backwards Compatibility

While this is certainly a step in the right direction, these changes do result in subtle changes to how `list()` works. Perhaps the one you’re most likely to encounter is that `list()` now works left-to-right:

```
list($array[], $array[], $array[]) = [1, 2, 3];
var_dump($array);

// PHP 5: $array = [3, 2, 1]
// PHP 7: $array = [1, 2, 3]
```

There are some other minor changes surrounding non-standard `list()` usage, which the RFC covers in great detail should you be interested in learning more.

### Further Reading

*   [RFC: Uniform Variable Syntax](https://wiki.php.net/rfc/uniform_variable_syntax)
*   [RFC: Abstract Syntax Tree](https://wiki.php.net/rfc/abstract_syntax_tree)

## Chapter 17: Semi-Reserved Words

PHP 5.x has ~64 globally-reserved words, such as `default` and `list`. Because they’re reserved globally, it was impossible to use these terms as class methods or properties:

Example from the RFC; these would cause syntax errors 

```
class Collection {
    public function forEach(callable $callback) { /* */ }
    public function list() { /* */ }
}
```

PHP 7 implements a new context-sensitive lexer, making it smart enough to determine the context of keywords; it can differentiate between normal keyword usage and usage within classes. All of the following reserved words from PHP 5.x are now **semi-reserved**:

| abstract || and || array |
| --- | --- | --- |
| as || break || callable |
| case || catch || class |
| clone || const || continue |
| declare || default || die |
| do || echo || else |
| elseif || enddeclare || endfor |
| endforeach || endif || endswitch |
| endwhile || exit || extends |
| final || finally || for |
| foreach || function || global |
| goto || if || implements |
| include || include\_once || instanceof |
| insteadof || interface || list |
| namespace || new || or |
| parent || print || private |
| protected || public || require |
| require\_once || return || self |
| static || switch || throw |
| trait || try || use |
| var || while || xor |
| yield ||   ||   |

These semi-reserved words can now be used as property, constant, and method names for classes, interfaces, and traits:

Some basic examples 

```
class Collection {
    public function forEach(callable $callback) { }
    public function list() { }
}

class BaseballPlayer {
    public function throw(Baseball $ball, BaseballPlayer $target) { }
    public function catch(Baseball $ball) { }
}
```

Here are some other examples from the RFC:

Using ‘include’ as a public method 

```
class View {
    public function include(View $view) {
        //...
    }
}
$viewA = new View('a.view');
$viewA->include(new View('b.view'));
```

Using ‘continue’ as a class constant 

```
class HTTP {
    const CONTINUE = 100;
    const SWITCHING_PROTOCOLS = 101;
    /* ... */
}
```

Fluent interface using reserved words like ‘and’, ‘or’, & ‘list’ 

```
$projects =
    Finder::for('project')
        ->where('name')->like('%secret%')
        ->and('priority', '>', 9)
        ->or('code')->in(['4', '5', '7'])
        ->and()->not('created_at')->between([$time1, $time2])
        ->list($limit, $offset);
```

There are only two restrictions to this:

1.  It only works within OO-scope (classes, interfaces, and traits).
2.  `class` cannot be used as a constant, since it would conflict with the class name resolution syntax (`SomeClass::class`). It **can** be used for method and property names though.

### Further Reading

*   [RFC: Context Sensitive Lexer](https://wiki.php.net/rfc/context_sensitive_lexer)
*   [PHP manual: List of Keywords](https://secure.php.net/manual/en/reserved.keywords.php)
*   [PHP manual: List of other reserved words](https://php.net/manual/en/reserved.other-reserved-words.php)

## Chapter 18: Error Handling and Exceptions

PHP 7 has drastically improved error handling. It’s now easier than ever to handle errors and exceptions in your code, thanks to some major changes and simplifications.

### Exceptions in the Engine

Fatal and recoverable fatal errors are no longer “raised”, like warnings and deprecations - they are now exceptions thrown by the engine. Let’s take a look at this short example:

```
$foo = 'test';
$foo->someMethod();
```

In previous versions of PHP, this would result in a fatal error:

```
Fatal error: Call to a member function someMethod() on a non-object
```

PHP 7 will instead throw an `Error`:

```
Uncaught Error: Call to a member function someMethod() on string
```

Just like normal exceptions, these are catchable and can be acted upon:

```
try {
    $foo = 'test';
    $foo->someMethod();
} catch (Error $e) {
    var_dump($e);
}

/**
  Output:

  object(Error)#1 (7) {
    ["message":protected]=>
    string(48) "Call to a member function someMethod() on string"
    ["string":"Error":private]=>
    string(0) ""
    ["code":protected]=>
    int(0)
    ["file":protected]=>
    string(9) "/in/mhr0k"
    ["line":protected]=>
    int(5)
    ["trace":"Error":private]=>
    array(0) {
    }
    ["previous":"Error":private]=>
    NULL
}
**/
```

There are five pre-defined sub-classes of `Error`:

*   `TypeError` - throw when an argument doesn’t match the required type hint (see [Chapter 1](#chap17.xhtml#chapter-1))
*   `ParseError` - thrown when `eval()` fails to parse the given code
*   `AssertionError` - thrown when an assertion (`assert(...)`) fails (see [Chapter 18](#chap35.xhtml#chapter-18))
*   `ArithmeticError` - thrown when an error occurs during a mathematical operation
*   `DivisionByZeroError` - a sub-class of `ArithmeticError` thrown when dividing something by `0`

\## `Throwable` interface

PHP 7 introduces a new `Throwable` interface which both `Exception`s and `Error`s extend from:

*   `interface Throwable` 
    *   `Exception implements Throwable`
    *   `Error implements Throwable`

This interface provides the following methods:

*   `getMessage()`
*   `getCode()`
*   `getFile()`
*   `getLine()`
*   `getTrace()`
*   `getTraceAsString()`
*   `__toString()`

Because `Error` and `Exception` share a common interface, you can `catch` either type:

```
try {
    // Some code
} catch (Exception $e) {
    // Oops, our code failed for some reason, so we should handle this.
} catch (Error $e) {
    // Something was wrong with our code; we should log the issue and fix it!
}
```

Or even catch both at once:

```
try {
    // Some code
} catch (Throwable $e) {
    // Fail
}
```

You cannot implement the `Throwable` interface yourself - you must extend from either `Error` or `Exception` instead.

### Reclassification of `E_STRICT` Notices

The `E_STRICT` notice type has always been somewhat unclear and redundant. In an effort to simplify PHP’s error model, all such instances of `E_STRICT` have been reclassifed or removed. The [corresponding RFC](https://wiki.php.net/rfc/reclassify_e_strict) has a helpful list describing all such changes along with the rationale for each decision.

The `E_STRICT` constant is not being removed though, thereby maintaining backwards compatibility with scripts which may contain code like `error_reporting(E_ALL|E_STRICT)`. However, there may be some BC breakage since some `E_STRICT` instances are now more-severe, which could affect some error handlers.

### Backwards Compatibility

In PHP 5.x it’s possible to silently ignore recoverable fatal errors with a custom error handler. Because these errors are now thrown as exceptions, this capability is removed.

Similarly, any parse errors generated while using `eval()` were previously non-fatal but are now thrown as exceptions. You’ll want to wrap any calls to `eval()` in a `try {} catch{}` block if you wish to gracefully handle any such errors in PHP 7.

The following class names can no longer be used in the global namespace:

*   `Throwable`
*   `Error`
*   `TypeError`
*   `ParseError`
*   `AssertionError`
*   `ArithmeticError`
*   `DivisionByZeroError`

### Further Reading

*   [RFC: Exceptions in the Engine](https://wiki.php.net/rfc/engine_exceptions_for_php7)
*   [RFC: Throwable Interface](https://wiki.php.net/rfc/throwable-interface)
*   [RFC: Catchable “call to a member function of a non-object”](https://wiki.php.net/rfc/catchable-call-to-member-of-non-object)
*   [RFC: Reclassify E\_STRICT notices](https://wiki.php.net/rfc/reclassify_e_strict)
*   [PHP manual: Throwable](https://secure.php.net/manual/en/class.throwable.php)
*   [PHP manual: Error](https://secure.php.net/manual/en/class.error.php)

## Chapter 19: Expectations

PHP 4 introduced assertions via the `assert()` function. An assertion is a helpful debugging feature which verifies assumptions in your code. Think of them like comments which actually test themselves. You simply provide a PHP statement which should always evaluate to true; any false values would indicate a bug, code misuse, or faulty assumption on your end. In PHP 4 and 5 `assert()` has the following signature:

```
bool assert ( mixed $assertion [, string $description ] )
```

The behavior of `assert()` is configurable, thus allowing you to completely disable it in production. This is particularly useful if the assertions would have negative side effects or incur performance penalties.

Here are some example use-cases of assertions:

Loops which should always return a value 

```
foreach ($a as $b) {
    if ($b->isActive()) {
        return $b;
    }
}

assert(false, 'Our loop should always return a value');
```

Ensuring a required extension is available 

```
function createThumbnail($image) {
    assert(extension_loaded('gd'));
    // ...
}
```

Guarding against unexpected enum values 

```
function setSuit($suit) {
    case CLUBS:
    case DIAMONDS:
    case HEARTS:
    case SPADES:
        $this->suit = $suit;
    default:
        assert(false, 'Unrecognized suit');
}
```

Fall-through expectations 

```
if ($i % 3 == 0) {
    // ...
} else if ($i % 3 == 1) {
    // ...
} else {
    assert ($i % 3 == 2);
}
```

Because `assert` is a function in PHP 4/5, any expressions (like the one above) are always evaluated, even if assertions are disabled for production! A workaround is to wrap the expression in a string, which PHP will then evaluate if necessary:

```
assert ('$i % 3 == 2');
```

This is somewhat better but still not ideal.

### `assert()` as a statement

PHP 7 upgrades `assert()` to become a full-fledged statement instead. You no longer need to wrap your code in a string - just provide it as-is:

```
assert ($i % 3 == 2);
```

Unlike previous versions, PHP 7 will not evaluate that statement unless required.

### Custom errors

Older versions of PHP will raise an `E_WARNING` when an assertion fails, using the second parameter as the warning message. PHP 7 adds the ability to raise your own custom error types, if desired:

```
ini_set('assert.exception', 1);

class MissingExtensionError extends AssertionError {}

assert(extension_loaded('foo'), new MissingExtensionError('The "foo" extension s\
hould be enabled for this to work'));
```

Throwing an exception (rather than emitting an error) means you’ll get a stack trace to help investigate the issue.

### Configuration

There are two new `php.ini` settings used to control the behavior and allow backwards-compatiblity:

*   assert.exception - defaults to `0`
*   zend.assertions - defaults to `1`

**assert.exception** controls the failure behavior of `assert()`:

*   **0** - raise a `warning` on failure (old behavior)
*   **1** - throw an `AssertionError` on failure

**zend.assertions** controls how the PHP parser should handle assertions it finds:

*   **1** - generate and execute the assertion code (development mode)
*   **0** - generate the code, but skip it at runtime
*   **\-1** - don’t generate any code (zero-cost production mode)

### Backwards Compatibility

PHP 7 maintains full backwards-compatibility with the old behavior:

*   If `$expression` is a string, it will be evaluated as needed
*   If `$expression` is false(y), the assertion will fail
*   If the second parameter is a string, it will be used as the message for the `AssertionError`

### Further Reading

*   [RFC: Expectations](https://wiki.php.net/rfc/expectations)
*   [PHP Manual: `assert()`](https://secure.php.net/manual/en/function.assert.php)

## Chapter 20: Array Constants in `define()`

PHP 5.6 added the ability to define array constants on classes by using the `const` keyword:

```
const LUCKY_NUMBERS = [4, 8, 15, 16, 23, 42];
```

PHP 7 brings this same functionality to the `define()` function:

```
define('LUCKY_NUMBERS', [4, 8, 15, 16, 23, 42]);
```

### Further Reading

*   [PHP Manual: `define()`](https://secure.php.net/manual/en/function.define.php)
*   [PHP Manual: Constant arrays using `define()`](https://secure.php.net/manual/en/migration70.new-features.php#migration70.new-features.define-array)

## Chapter 21: Filtered `unserialize()`

Unserializing untrusted data is a risky practice as malicious users could potentially inject their own data and objects into applications. This is particularly dangerous for objects with destructors, as those methods will always be executed, even if you don’t actually use the unserialized object.

Here’s an actual example from Drupal 7’s `Archive_Tar` class:

```
function __destruct() {
  $this->_close();
  //...
}

function _close() {
  //...
  if ($this->_temp_tarname != '') {
    @drupal_unlink($this->_temp_tarname);
    //...
  }
  //...
}
```

An attacker could use this to delete arbitrary files from the server simply by providing a specially-crated string to **anywhere that `unserialize` is used**:

```
O:11:"Archive_Tar":6:{s:8:"_tarname";s:0:"";s:9:"_compress";b:0;s:14:"_compress_\
type";s:4:"none";s:10:"_separator";s:1:" ";s:5:"_file";i:0;s:13:"_temp_tarname";\
s:11:"/etc/passwd";}
```

Other functions like `__toString()`, `__call()`, etc. can also be vulnerable.

### Secure filtering

PHP 7 adds an `array $options` parameter to the `unserialize()` function to control the unserialization process. It currently supports a single `allowed_classes` option to control the unserialization of objects. This can take the following values:

*   **true** - allows all objects to be restored
*   **false** - prevents all objects from being restored
*   **string\[\]** - array of allowed class names

Omitting this option is the same as defining it as `true`.

If a class is not allowed, PHP will unserialize it as an “incomplete class” object (`__PHP_Incomplete_Class`). This is the same behavior PHP already uses when you try to unserialize a class which doesn’t exist.

### Examples

```
// These will unserialize everything as before
$data = unserialize($foo);
$data = unserialize($foo, ['allowed_classes' => true]);

// This will convert all objects into __PHP_Incomplete_Class object
$data = unserialize($foo, ['allowed_classes' => false]);

// this will convert all objects except ones of Foo and Bar into __PHP_Incomplet\
e_Class object
$data = unserialize($foo, ['allowed_classes' => ['Foo', 'Bar']]);
```

### Further Reading

*   [RFC: Filtered Unserialize](https://wiki.php.net/rfc/secure_unserialize)
*   [PHP Manual: `unserialize()`](https://secure.php.net/manual/en/function.unserialize.php)

## Chapter 22: `session_start` Options

The `session_start()` function can now be passed an array of INI settings, therefore allowing per-session configuration. For example, the following code will set `session.cache_limiter=private`:

```
session_start(['cache_limiter' => 'private']);
```

### New options

PHP 7 also introduces two new session options:

*   **read\_and\_close** - Session is opened for reading data and then immediately closed.
*   **lazy\_write** (default=On) - Session data is only written if it has been changed.

### Further Reading

*   [RFC: session\_start() options](https://wiki.php.net/rfc/session-lock-ini)

## Chapter 23: Reflection Enhancements

PHP 7 adds some new classes and methods to the Reflection API.

### ReflectionGenerator

A new `ReflectionGenerator` class provides information about generators and their state:

```
class ReflectionGenerator {
    public __construct(Generator $generator)
    public string getExecutingFile()
    public Generator getExecutingGenerator()
    public int getExecutingLine()
    public ReflectionFunctionAbstract getFunction()
    public object getThis()
    public array getTrace($options = DEBUG_BACKTRACE_PROVIDE_OBJECT)
}
```

### ReflectionType

A new `ReflectionType` class has been added to report information about a function’s parameters and return types (to support the new scalar and return type hints). This class has the following methods:

```
class ReflectionType
{
    public bool allowsNull()
    public bool isBuiltin()
    public string __toString()
}
```

### ReflectionParameter

Two new methods have been added to `ReflectionParameter` to determine the defined types:

```
class ReflectionParameter
{
    // ...
    public bool hasType()
    public ReflectionType getType()
}
```

The `getType()` method will return the new `ReflectionType` object type as described above.

### ReflectionFunctionAbstract

This class also has two similarly-named methods to determine the defined return types of a function:

```
class ReflectionFunctionAbstract
{
    // ...
    public bool hasReturnType()
    public ReflectionType getReturnType()
}
```

### Backwards Compatibility

You may no longer define classes named `ReflectionGenerator` or `ReflectionType` in the global namespace.

### Further Reading

*   [PHP Manual: `ReflectionType`](https://secure.php.net/manual/en/class.reflectiontype.php)
*   [PHP Manual: `ReflectionGenerator`](https://secure.php.net/manual/en/class.reflectiongenerator.php)
*   [PHP Manual: `ReflectionParameter`](https://php.net/manual/en/class.reflectionparameter.php)
*   [PHP Manual: `ReflectionFunctionAbstract`](https://php.net/manual/en/class.reflectionfunctionabstract.php)

## Chapter 24: Integer Semantics

Certain integer behavior has been revised for cross-platform consistency, making it more intuitive for developers.

### Casting NaN and Infinity

Casting NaN (`NAN`) and Infinity (`INF`) to an integer will always result in a `0` value. Previously, the resulting values would be undefined and vary between different platforms.

### Negative bitwise shifting

You’re no longer allowed to bitwise shift by a negative number of bits. Attempting to do so will result in an `ArithmeticError` being thrown.

### Bitwise shifting too far

Even though some CPUs support proper wrapping behavior, not all of them do, which can result in certain edge cases. PHP 7 therefore standardizes this behavior for cross-platform consistency.

Left bitwise shifts beyond the bit-width of an integer will always result in `0`, even if the platform supports wrapping around.

Right bitwise shifts beyond the bit-width of an integer will always result in `0` or `-1` (depending on the sign), even if the platform supports wrapping around.

### Backwards Compatibility

Relying on the old PHP 5.x behavior in these specific cases will no longer work.

### Further Reading

*   [RFC: Integer Semantics](https://wiki.php.net/rfc/integer_semantics)
*   [PHP manual: Bitwise Operators](https://secure.php.net/manual/en/language.operators.bitwise.php)

## Chapter 25: Division By Zero Semantics

Prior to PHP 7, dividing by `0` would emit an `E_WARNING` and return `false`. Returning a boolean value for an arithmetic operation doesn’t make much sense, so PHP 7 will now return one of the following float values in addition to emitting the `E_WARNING`:

*   `+INF`
*   `-INF`
*   `NAN`

For example:

```
var_dump(42/0);  // float(INF)  + E_WARNING
var_dump(-42/0); // float(-INF) + E_WARNING
var_dump(0/0);   // float(NAN)  + E_WARNING
```

When using the modulus operator (`%`), PHP 7 will instead throw a `DivisionByZeroError`:

```
var_dump(0%0); // DivisionByZeroError
```

The `intdiv()` function will throw an `ArithmeticError` whenever you provide a valid integer argument which would result in an incorrect result due to integer overflow:

```
var_dump(intdiv(PHP_INT_MIN, -1)); // ArithmeticError
```

### Backwards Compatibility

*   The division operator will no longer return `false` when dividing by zero.
*   The modulus operator will throw an error (instead of returning `false`) when dividing by zero.

### Further Reading

*   [PHP manual: DivisionByZeroError](https://secure.php.net/manual/en/class.divisionbyzeroerror.php)
*   [PHP manual: ArithmeticError](https://secure.php.net/manual/en/class.arithmeticerror.php)

## Chapter 26: JSON Library

The current json extension used by PHP 5 does not have a free license, which is a problem for some Linux distributions. Debian previously handled this by providing a separate `php5-json` extension outside of the main PHP codebase. In addition to licensing concerns, the old library had several other issues:

*   Code was outdated
*   There was no active maintainer
*   The implementation suffered from several performance issues

PHP 7 solved these issues by replacing the current json extension with new code based on the PECL jsond extension. The userland API is identical, but the licensing is better and it also offers better performance in some cases.

### Fractional float values

The new JSOND library introduces a new option to `json_encode` to preserve the fractional part of float values:

```
echo json_encode(10.0); // Output: 10
echo json_encode(10.1); // Output: 10.1

echo json_encode(10.0, JSON_PRESERVE_ZERO_FRACTION); // Output: 10.0
echo json_encode(10.1, JSON_PRESERVE_ZERO_FRACTION); // Output: 10.1
```

Being able to toggle this behavior is useful when working with other languages. For example, both Go and JavaScript will encode `10.0` as `10`, whereas Python, C, and Ruby would encode it to `10.0`.

### Backwards Compatibility

The old extension handled certain number formats which weren’t exactly valid according to the JSON spec (RFC 7159). The new JSOND extension therefore rejects certain number formats which previously worked in PHP 5.x:

*   Numbers cannot end with a decimal point.
*   The `e` exponent cannot immediately proceed a decimal point.

These JSON strings are therefore no longer valid:

```
'42.'
'42.e1'
```

You should remove the decimal points or add a `0` immediately afterwards to allow successful JSON parsing:

```
'42' or '42.0'
'42e1' or '42.0e1'
```

### Further Reading

*   [RFC: Replacing current json extension with jsond](https://wiki.php.net/rfc/jsond)
*   [RFC: Preserve Fractional Part in JSON encode](https://wiki.php.net/rfc/json_preserve_fractional_part)
*   [PHP manual: json\_decode](https://secure.php.net/manual/en/function.json-decode.php)
*   [PHP bug #63520](https://bugs.php.net/bug.php?id=63520)
*   [IETF RFC 7159: JSON Data Interchange Format](https://tools.ietf.org/html/rfc7159)

## Chapter 27: Behavior Changes to `foreach`

PHP’s `foreach` statement had some quirky, undefined behavior. These edge cases were caused by low-level implementation details and were never truly supported. In an effort to provide consistent, documented behavior, several of these edge cases were corrected.

The majority of these edge cases deal with manipulating the internal pointer or modifying elements of an array. The conceptual behavior of `foreach` itself remains unchanged.

For example, look at these two very similar examples from the RFC:

Example 1 

```
$a = [1,2,3];
foreach($a as $v) {
    echo $v . " - " . current($a) . "\n";
}
```

Example 1: Output 

```
1 - 2
2 - 2
3 - 2
```

However, if you make one small modification before the loop, you get a different result:

Example 2 

```
$a = [1,2,3];
$b = $a;
foreach($a as $v) {
    echo $v . " - " . current($a) . "\n";
}
```

Example 2: Output 

```
1 - 1
2 - 1
3 - 1
```

### Changes

Here are some examples demonstrating the new semantics in PHP 7

#### Iterating arrays by value

Ignoring modifications to the original array 

```
$a = [1,2,3];
$b = &$a;

foreach($a as $v) {
    unset($a[1]);
    echo $v . " - " . current($a) . "\n";
}
```

PHP 5.x Output 

```
1 - 3
3 - 2
```

PHP 7 Output 

```
1 - 1
2 - 1
3 - 1
```

#### Iterating arrays by reference

The `current()` function is no longer affected by the iteration of the array:

```
$a = [1,2,3];

foreach($a as &$v) {
    echo $v . " - " . current($a) . "\n";
}
```

PHP 5.x Output 

```
1 - 2
2 - 3
3 -
```

PHP 7 Output 

```
1 - 1
2 - 1
3 - 1
```

#### Iterating objects by value

Iterating objects by value behaves similarly to iterating arrays by reference, except that it uses the object’s value instead of its reference. You can therefore modify the object but not replace it within a `foreach` loop.

#### Iterating objects by reference

This behaves identically to iterating an array by reference.

#### Other functions

Because the state of a `foreach` loop is now independent from the internal state of an array/object pointer, built-in functions which use that internal pointer (`reset`/`key`/`current`/`next`/`prev`) will no longer represent the state of the loop.

### Backwards Compatibility

Any code relying on the old, undocumented behavior will no longer work in PHP 7.

### Further Reading

*   [RFC: Fix “foreach” behavior](https://wiki.php.net/rfc/php7_foreach)

## Chapter 28: Behavior Changes to `list`

### String Handling

The PHP documentation has always stated that the `list()` construct wouldn’t unpack strings. However, in some cases, it actually would work:

Example 1 

```
list($a, $b) = 'ab';
var_dump($a, $b);
```

Example 1: Output 

```
NULL
NULL
```

Example 2 

```
$a[0] = 'ab';
list($a, $b) = $a[0];
var_dump($a, $b);
```

Example 2: Output 

```
string(1) "a"
string(1) "b"
```

This undocumented behavior was caused by an implementation “feature” and was not intentional.

This string handling edge-case no longer works with PHP 7.

### Empty List Assignment

Using `list()` without any variables will now result in a fatal error:

```
$a = [1, 2, 3];

list() = $a;   // Fatal error: Cannot use empty list
list(,,) = $a; // Fatal error: Cannot use empty list
```

### Variable Assignment Order

Because of the new [Abstract Syntax Tree](#chap33.xhtml#chapter-16-ast), values are assigned left-to-right, whereas PHP 5.x assigned them right-to-left.

### Backwards Compatibility

*   `list()` no longer works with string values in some cases; variables will always be set to `NULL` in these cases
*   Calling `list()` without any variables will trigger a fatal error
*   Depending on the old right-to-left assignment ordering will no longer work

### Further Reading

*   [RFC: Fix list() behavior inconsistency](https://wiki.php.net/rfc/fix_list_behavior_inconsistency)
*   [RFC: Abstract Syntax Tree](https://wiki.php.net/rfc/abstract_syntax_tree#changes_to_list)

## Chapter 29: Parameter Handling Changes

### Duplicate Parameter Names

Previous versions of PHP allowed multiple function parameters to use the same name. This functionality is no longer supported in PHP 7. Attempting to use duplicate parameter names will now cause a fatal error.

```
function foo($a, $a) {
    return $a;
}

echo foo(1, 2);
```

PHP 5 Output 

```
2
```

PHP 7 Output 

```
Fatal error: Redefinition of parameter $a
```

### `func_get_arg()` and `func_get_args()`

The `func_get_arg()` and `func_get_args()` functions used to return the original parameter values, even if those variables changed during function execution. This behavior no longer occurs in PHP 7 - both functions will instead provide the current value(s). For example, given the following code:

```
function foo($a) {
    $a++;
    var_dump($a);
}
foo(1);
```

PHP 5.x would display the original value of `1`, whereas PHP 7 will display `2`.

This behavioral change also applies to the display of function arguments in backtraces.

### Backwards Compatibility

Code using duplicate parameter names will now result in a fatal error. Simply removing the previous instances will maintain full compatibility with PHP 5.x and 7.x.

Code relying on `func_get_arg()` and `func_get_args()` to return the original (not current) value may not behave as expected.

### Further Reading

*   [RFC: phpng](https://wiki.php.net/phpng)

## Chapter 30: Custom Session Handler Return Values

PHP allows you to implement your own session storage and retrieval mechanisms via the `session_set_save_handler()` function. You simply define some functions (or implement the `SessionHandlerInterface`) to handle operations like loading and saving the session data.

According to the documentation, several of these functions (like `open()` and `close()`) should return `true` on success or `false` on failure. However, these return values never worked properly prior to PHP 7 due to a major bug with how PHP’s internals handled your return value. Essentially, return values of `false` were never interpreted as failures. Developers eventually figured out they could return `-1` to indicate failure, but this contradicted the documentation.

PHP 7 resolves this bug so that both `true` and `false` return values are interpreted properly. If you return any other value (including the `return -1` workaround from PHP 5.x), this will cause a failure and emit an `E_WARNING`.

### Backwards Compatibility

*   `return false` will actually work as expected now.
*   Using the `return -1` workaround will cause a warning.

### Further Reading

*   [RFC: Fix handling of custom session handler return values](https://wiki.php.net/rfc/session.user.return-valuey)
*   [PHP manual: session\_set\_save\_handler](http://us2.php.net/session_set_save_handler)

## Chapter 31: Errors on Invalid Octal Literals

Attempting to use an invalid octal literal (containing digits larger than 7) will now produce a parse error:

Invalid Octal in PHP 7 

```
echo 0781; // Parse error: Invalid numeric literal
```

Prior versions of PHP would silently truncate the literal, resulting in unexpected values:

Invalid Octal in PHP 5.x 

```
echo 0781; // 7
```

### Backwards Compatibility

*   Using invalid octal literals will result in a parse error

### Further Reading

*   *n/a*

# Part 3 - Deprecations & Removals

PHP 7 deprecates a couple features and removes several others which worked in previous versions of PHP. You’ll want to adjust your code accordingly before upgrading to PHP 7.

## Chapter 32: Deprecation of PHP 4 Constructors

Creating constructor methods for PHP 4 classes involved declaring a method with the same name as the class:

PHP 4-Style Constructor Example 

```
class Post {
    // Recognized as a constructor in PHP 4 and 5
    function post() {}
}
```

PHP 5 added the new `__construct()` method we’re all familiar with, but it also preserved the older style constructors too. This led to some strange behavior in different cases.

For example, PHP 4-style constructors worked fine in global classes but not namespaced classes:

Namespaced PHP 5 Class 

```
namespace Blog;
class Post {
    // Not recognized as a constructor because of the namespace
    function post() {}
}
```

And if you declared both a PHP 4 and PHP 5-style constructor, you’d get different behavior based on which was listed first in the code:

PHP 5-Style Constructor First 

```
class Post {
    // Constructor
    function __construct() {}

    // Normal method; not a constructor
    function post() {}
}
```

PHP 4-Style Constructor First 

```
class Post {
    // Normal method; not a constructor
    function post() {}

    // Emits an E_STRICT
    function __construct() {}
}
```

Instead of preserving this odd behavior, PHP 7 makes two important changes:

1.  `E_DEPRECATED` is emitted whenever any PHP 4-style constructor is used.
2.  `E_STRICT` is no longer emitted when both types of constructors are present.

Furthermore, PHP 8 will not recognize the PHP 4-style constructors, therefore always interpreting them as standard class methods.

Because this old style is deprecated, you should strongly consider removing them altogether from code you migrate to PHP 7.

### Backwards Compatibility

*   Custom error handlers may be affected by the new `E_DEPRECATED` errors being emitted.

### Further Reading

*   [RFC: Remove PHP 4 Constructors](https://wiki.php.net/rfc/remove_php4_constructors)
*   [PHP Manual: Constructors and Destructors](http://us2.php.net/manual/en/language.oop5.decon.php)

## Chapter 33: Deprecation of Salt Option for `password_hash()`

PHP 5.5 introduced a new password hashing API to make secure hashing easy (and abstract away some of bcrypt’s complexity). Part of this API included a new `password_hash()` method which allowed users to provide a custom salt. However, these salts were often generated using cryptographically insecure sources (like `mt_rand()`), thus compromising the effectiveness of the salts.

PHP 7 therefore deprecates this `salt` option. It’s strongly recommended that you omit this and simply use the salt whatever cryptographically-secure salt PHP generates for you.

### Further Reading

*   [PHP Manual: `password_hash`](http://us2.php.net/manual/en/function.password-hash.php)

## Chapter 34: Removal of Previously-Deprecated Features

PHP 7 removes **ALL** features that were deprecated in prior versions.

### Removed Extensions

| Extension Name || Deprecated Since || Alternative |
| --- | --- | --- |
| `ext/mysql` || PHP 5.3 || `ext/mysqli` or `ext/pdo_mysql` |
| --- | --- | --- |
| `ext/ereg` || PHP 5.3 || `ext/pcre` |

### Removed Language Features

| Feature Description || Deprecated Since || Alternative |
| --- | --- | --- |
| Assignment of `new` by reference || PHP 5.3 || Use normal assignment instead |
| --- | --- | --- |
| Scoped calls of non-static methods from incompatible `$this` context || PHP 5.6 ||   |

### Removed Functions

| Function Name || Deprecated Since || Alternative(s) |
| --- | --- | --- |
| `dl` on fpm-fcgi || PHP 5.3 ||   |
| --- | --- | --- |
| `set_magic_quotes_runtime` || PHP 5.4 ||   |
| `magic_quotes_runtime` || PHP 5.4 ||   |
| `set_socket_blocking` || PHP 5.4 || `stream_set_blocking` |
| `mcrypt_generic_end` || PHP 5.4 || `mcrypt_generic_deinit` |
| `mcrypt_ecb`, `mcrypt_cbc`, `mcrypt_cfb` and `mcrypt_ofb` || PHP 5.5 || `mcrypt_encrypt` and `mcrypt_decrypt` |
| `datefmt_set_timezone_id` || PHP 5.5 || `datefmt_set_timezone` |
| `IntlDateFormatter::setTimeZoneID` || PHP 5.5 || `IntlDateFormatter::setTimeZone` |

### Removed INI Options

| INI Options || Deprecated Since || Alternative |
| --- | --- | --- |
| `xsl.security_prefs` || PHP 5.4 || `XsltProcessor::setSecurityPrefs` |
| --- | --- | --- |
| `iconv.input_encoding` and `mbstring.http_input` || PHP 5.6 || `php.input_encoding` |
| `iconv.internal_encoding` and `mbstring.internal_encoding` || PHP 5.6 || `php.internal_encoding` |
| `iconv.output_encoding` and `mbstring.http_output` || PHP 5.6 || `php.output_encoding` |

### Miscellaneous Removed Functionality

| Functionality || Deprecated Since || Alternative |
| --- | --- | --- |
| The ``$is_dst` parameter of `mktime()`` and `gmmktime()` || PHP 5.1 ||   |
| --- | --- | --- |
| `#`-style comments in `ini` files || PHP 5.3 || `;`-style comments |
| String category names in `setlocale()` || PHP 5.3 || `LC_*`` constants |
| Unsafe curl file uploads || PHP 5.5 || `CurlFile` |
| `preg_replace()` eval modifier || PHP 5.5 || `preg_replace_callback()` |
| `PDO::PGSQL_ATTR_DISABLE_NATIVE_PREPARED_STATEMENT` driver option || PHP 5.6 || `PDO::ATTR_EMULATE_PREPARES` |
| `CN_match` and `SNI_server_name` stream context options || PHP 5.6 || `peer_name` option |

### Backwards Compatibility

Any code relying on previously-deprecated functionality will break in PHP 7.

### Further Reading

*   [RFC: Remove deprecated functionality in PHP 7](https://wiki.php.net/rfc/remove_deprecated_functionality_in_php7)

## Chapter 35: Removal of Alternative PHP Tags

Alternative PHP tags are no longer supported. These include ASP tags and script tags:

*   `<%` opening tag
*   `<%=` opening tag with `echo`
*   `%>` closing tag
*   `(<script\s+language\s*=\s*(php|"php"|'php')\s*>)i` opening tag
*   `(</script>)i` closing tag

### Migrating From Alternative Tags

If your code uses these tags, you’ll need to migrate them to using the normal (`<?php ?>`) or short (`<? ?>`) tags. You can find a porting script here: https://gist.github.com/nikic/74769d74dad8b9ef221b

To run it:

```
php -d asp_tags=1 portAlternativeTags.php path/to/files/
```

### Backwards Compatibility

Code using the alternative tags will no longer work. This may result in your source code being displayed to visitors.

### Further Reading

*   [RFC: Remove alternative PHP tags](https://wiki.php.net/rfc/remove_alternative_php_tags)

## Chapter 36: Reclassification and Removal of E\_STRICT Notices

Several things which used to emit `E_STRICT` notices in PHP 5 now emit different error types. These new types are more descriptive and more consistent with the rest of the language. Here’s a detailed list of those changes:

### Examples

#### Indexing by a resource

Using a resource as an array index will now emit an `E_NOTICE` instead of `E_STRICT`:

```
$file = fopen('test.zip', 'r');
$array[$file] = true;

// Notice: Resource ID#5 used as offset, casting to integer (5)
```

#### Abstract static methods

Notices are no longer emitted when declaring abstract static methods. This is consistent with how interfaces allow the declaration of such abstract static methods.

```
abstract class Foo {
    abstract static function bar();
}
```

#### Signature mismatch during inheritance

Mismatched method signatures will now emit an `E_WARNING` instead of `E_STRICT`:

```
class Foo {
    public function method() {}
}

class Bar extends Foo {
    public function method($arg) {}
}

// Warning: Declaration of Bar::method($arg) should be
// compatible with Foo::method()
```

### Same (compatible) property in two used traits

Using the same property in multiple traits will no longer raise any warnings:

```
trait A {
    public $prop;
}

trait B {
    public $prop;
}

class C {
    use A, B;
}
```

### Accessing static property non-statically

Attempting to access a static property non-statically (without `::`) will now emit an `E_NOTICE` instead of `E_STRICT`:

```
class Foo {
    public static $prop = 0;
}

$obj = new Foo;
$obj->prop = 42;

// Notice: Accessing static property Foo::$prop as non static
```

### Only variables should be assigned by reference

Attempting to assign a non-variable (like a function result) by reference will now emit an `E_NOTICE` instead of `E_STRICT`:

```
$a =& substr('foo', 1);

// Notice: Only variables should be assigned by reference
```

### Only variables should be passed by reference

Similarly, trying to pass a non-variable (like a function result) by reference will also emit an `E_NOTICE` instead of `E_STRICT`:

```
function by_ref(&$ref) {}
by_ref(substr("foo", 1));

// Notice: Only variables should be passed by reference
```

### Calling non-static methods statically

Attempting to call a non-static method statically (with `::`) will no emit an `E_DEPRECATED` instead of `E_STRICT`:

```
class Foo {
	  public function bar() {}
}

Foo::bar();

// Deprecated: Non-static method Foo::method() should not be called statically
```

(You should be annotating such methods with `static` anyway.)

### Backwards Compatibility

*   Code relying on `E_STRICT` may no longer function properly.
*   Things that used to emit `E_STRICT` may now emit a higher error category like `E_WARNING`, which could break custom error handlers.

### Further Reading

*   [RFC: Reclassify E\_STRICT notices](https://wiki.php.net/rfc/reclassify_e_strict)

## Chapter 37: Removal of Multiple Defaults in Switches

Previous versions of PHP allowed a `switch` statement to contain multiple `default` cases. Only the last one would actually be used, making the previous ones useless.

Attempting to use multiple `default` cases in PHP 7 will now cause a fatal error.

```
switch ($expr) {
    default:
        neverExecuted();
        break;
    default:
        executed();
}

// Fatal error: Switch statements may only contain one default clause
```

### Backwards Compatibility

Code using multiple `default`s will now result in a fatal error. Simply removing the earlier instances will maintain full compatibility with PHP 5.x and 7.x.

### Further Reading

*   [RFC: Make defining multiple default cases in a switch a syntax error](https://wiki.php.net/rfc/switch.default.multiple)

## Chapter 38: Removal of Numeric Hexadecimal String Support

Earlier versions of PHP do not consistently handle numeric hexadecimal strings like `"0x123"`:

PHP 5.x behavior 

```
var_dump(is_numeric("0x123"));
// bool(true)

var_dump((int) "0x123");
// int(0)

var_dump((float) "0x123");
// float(0)

var_dump("0x123" * 2);
// int(582)

var_dump("0x123" == '291');
// bool(true)

var_dump((int) "0x123" == (int) "291");
// bool (false)
```

PHP 7 resolves this discrepancy by simply removing the old partial support for such strings.

### Backwards Compatibility

Using hexadecimal numbers in strings is no longer supported in these contexts:

*   The `is_numeric()` function
*   Mathematic operations
*   Internal PHP functions which accept numeric strings

### Further Reading

*   [RFC: Remove hex support in numeric strings](https://wiki.php.net/rfc/remove_hex_support_in_numeric_strings)

## Chapter 39: Removal of Dead SAPIs and Extensions

### Dead SAPIs

PHP contains SAPIs for several servers. Some of these are no longer available or haven’t been supported for a very long time. They have therefore been removed from PHP 7. The list includes:

*   `sapi/aolserver`
*   `sapi/apache`
*   `sapi/apache_hooks`
*   `sapi/caudium`
*   `sapi/continuity`
*   `sapi/isapi`
*   `sapi/milter`
*   `sapi/phttpd`
*   `sapi/pi3web`
*   `sapi/roxen`
*   `sapi/thttpd`
*   `sapi/tux`
*   `sapi/webjames`

### Dead Extensions

The following extensions are no longer maintained and have been removed:

*   `ext/mssql`
*   `ext/sybase_ct`

### Backwards Compatibility

Systems relying on these SAPIs and extensions will not work with PHP 7. Consider finding an alternate SAPI or extension to replace any that are being removed.

### Further Reading

*   [RFC: Removal of dead or not yet PHP7 ported SAPIs and extensions](https://wiki.php.net/rfc/removal_of_dead_sapis_and_exts)

## Chapter 40: Removal of the `date.timezone` Warning

In previous versions of PHP, failing to define the `date.timezone` INI setting would result in the following behavior:

*   Defaulting to UTC
*   Emitting a warning message

PHP 7 will no longer emit a warning in these case. UTC will continue to be the default timezone if none is specified in the configuration.

### Further Reading

*   [RFC: Remove the date.timezone warning](https://wiki.php.net/rfc/date.timezone_warning_removal)

# Appendix - Backward Compatibility Breaks

If you’re coming from a modern version of PHP (like 5.5 or 5.6), most of your code will probably work fine as-is. Nevertheless, we’ll cover most of the important breaking changes in this section so you’ll be prepared to fix any such issues in your projects.

The majority of these BC breaks were covered in previous chapters. We’ll link back to those sections as needed.

This list comes directly from the php-src `UPGRADING` document as of 7 November 2015. It may not be exhaustive. Please check [https://github.com/php/php-src/blob/PHP-7.0.0/UPGRADING](https://github.com/php/php-src/blob/PHP-7.0.0/UPGRADING) for the latest version.

## Language Changes

### Variable handling

#### Left-to-right parsing

Indirect variable, property and method references are now interpreted with left-to-right semantics. Some examples:

```
  $$foo['bar']['baz'] // interpreted as ($$foo)['bar']['baz']
  $foo->$bar['baz']   // interpreted as ($foo->$bar)['baz']
  $foo->$bar['baz']() // interpreted as ($foo->$bar)['baz']()
  Foo::$bar['baz']()  // interpreted as (Foo::$bar)['baz']()
```

To restore the previous behavior add explicit curly braces:

```
  ${$foo['bar']['baz']}
  $foo->{$bar['baz']}
  $foo->{$bar['baz']}()
  Foo::{$bar['baz']}()
```

#### Global Keywords

The global keyword now only accepts simple variables. Instead of

```
  global $$foo->bar;
```

it is now required to write the following:

```
  global ${$foo->bar};
```

#### Parenthesis influencing behavior

Parentheses around variables or function calls no longer have any influence on behavior. For example the following code, where the result of a function call is passed to a by-reference function

```
  function getArray() { return [1, 2, 3]; }

  $last = array_pop(getArray());
  // Strict Standards: Only variables should be passed by reference
  $last = array_pop((getArray()));
  // Strict Standards: Only variables should be passed by reference
```

will now throw a strict standards error regardless of whether parentheses are used. Previously no notice was generated in the second case.

#### By-reference assignment ordering

Array elements or object properties that are automatically created during by-reference assignments will now result in a different order. For example

```
  $array = [];
  $array["a"] =& $array["b"];
  $array["b"] = 1;
  var_dump($array);
```

now results in the array \[“a” ⇒ 1, “b” ⇒ 1\], while previously the result was \[“b” ⇒ 1, “a” ⇒ 1\];

### `list()` behavior

#### Variable assignment order

list() will no longer assign variables in reverse order. For example

```
  list($array[], $array[], $array[]) = [1, 2, 3];
  var_dump($array);
```

will now result in $array == \[1, 2, 3\] rather than \[3, 2, 1\]. Note that only the **order** of the assignments changed, but the assigned values stay the same. E.g. a normal usage like

```
  list($a, $b, $c) = [1, 2, 3];
  // $a = 1; $b = 2; $c = 3;
```

will retain its current behavior.

#### Empty list assignments

Empty list() assignments are no longer allowed. As such all of the following are invalid:

```
  list() = $a;
  list(,,) = $a;
  list($x, list(), $y) = $a;
```

list() no longer supports unpacking strings (while previously this was only supported in some cases). The code

```
  $string = "xy";
  list($x, $y) = $string;
```

will now result in $x == null and $y == null (without notices) instead of $x == “x” and $y == “y”. Furthermore list() is now always guaranteed to work with objects implementing ArrayAccess, e.g.

```
  list($a, $b) = (object) new ArrayObject([0, 1]);
```

will now result in $a == 0 and $b == 1. Previously both $a and $b were null.

### `foreach` behavior

#### Interaction with internal array pointers

Iteration with foreach() no longer has any effect on the internal array pointer, which can be accessed through the current()/next()/etc family of functions. For example

```
  $array = [0, 1, 2];
  foreach ($array as &$val) {
      var_dump(current($array));
  }
```

will now print the value int(0) three times. Previously the output was int(1), int(2) and bool(false).

#### Array iteration by-value

When iterating arrays by-value, foreach will now always operate on a copy of the array, as such changes to the array during iteration will not influence iteration behavior. For example

```
  $array = [0, 1, 2];
  $ref =& $array; // Necessary to trigger the old behavior
  foreach ($array as $val) {
      var_dump($val);
      unset($array[1]);
  }
```

will now print all three elements (0 1 2), while previously the second element 1 was skipped (0 2).

#### Array iteration by-reference

When iterating arrays by-reference, modifications to the array will continue to influence the iteration. However PHP will now do a better job of maintaining a correct position in a number of cases. E.g. appending to an array during by-reference iteration

```
  $array = [0];
  foreach ($array as &$val) {
      var_dump($val);
      $array[1] = 1;
  }
```

will now iterate over the appended element as well. As such the output of this example will now be “int(0) int(1)”, while previously it was only “int(0)”.

#### Object iteration

Iteration of plain (non-Traversable) objects by-value or by-reference will behave like by-reference iteration of arrays. This matches the previous behavior apart from the more accurate position management mentioned in the previous point.

Iteration of Traversable objects remains unchanged.

### Parameter handling

#### Duplicate parameter names

It is no longer possible to define two function parameters with the same name. For example, the following method will trigger a compile-time error:

```
  public function foo($a, $b, $unused, $unused) {
      // ...
  }
```

Code like this should be changed to use distinct parameter names, for example:

```
  public function foo($a, $b, $unused1, $unused2) {
      // ...
  }
```

#### Retrieving argument values

The func\_get\_arg() and func\_get\_args() functions will no longer return the original value that was passed to a parameter and will instead provide the current value (which might have been modified). For example

```
  function foo($x) {
      $x++;
      var_dump(func_get_arg(0));
  }
  foo(1);
```

will now print “2” instead of “1”. This code should be changed to either perform modifications only after calling func\_get\_arg(s)

```
  function foo($x) {
      var_dump(func_get_arg(0));
      $x++;
  }
```

or avoid modifying the parameters altogether:

```
  function foo($x) {
      $newX = $x + 1;
      var_dump(func_get_arg(0));
  }
```

#### Effect on backtraces

Similarly exception backtraces will no longer display the original value that was passed to a function and show the modified value instead. For example

```
  function foo($x) {
      $x = 42;
      throw new Exception;
  }
  foo("string");
```

will now result in the stack trace

```
  Stack trace:
  #0 file.php(4): foo(42)
  #1 {main}
```

while previously it was:

```
  Stack trace:
  #0 file.php(4): foo('string')
  #1 {main}
```

While this should not impact runtime behavior of your code, it is worthwhile to be aware of this difference for debugging purposes.

The same limitation also applies to debug\_backtrace() and other functions inspecting function arguments.

### Integer handling

#### Invalid octal literals

Invalid octal literals (containing digits larger than 7) now produce compile errors. For example, the following is no longer valid:

```
  $i = 0781; // 8 is not a valid octal digit!
```

Previously the invalid digits (and any following valid digits) were simply ignored. As such $i previously held the value 7, because the last two digits were silently discarded.

#### Negative bitwise shifting

Bitwise shifts by negative numbers will now throw an ArithmeticError:

```
  var_dump(1 >> -1);
  // ArithmeticError: Bit shift by negative number
```

#### Left bitwise shifts

Left bitwise shifts by a number of bits beyond the bit width of an integer will always result in 0:

```
  var_dump(1 << 64); // int(0)
```

Previously the behavior of this code was dependent on the used CPU architecture. For example on x86 (including x86-64) the result was int(1), because the shift operand was wrapped.

#### Right bitwise shifts

Similarly right bitwise shifts by a number of bits beyond the bit width of an integer will always result in 0 or -1 (depending on sign):

```
  var_dump(1 >> 64);  // int(0)
  var_dump(-1 >> 64); // int(-1)
```

### String handling

#### Hexadecimal numeric strings

Strings that contain hexadecimal numbers are no longer considered to be numeric and don’t receive special treatment anymore. Some examples of the new behavior:

```
  var_dump("0x123" == "291");     // bool(false)     (previously true)
  var_dump(is_numeric("0x123"));  // bool(false)     (previously true)
  var_dump("0xe" + "0x1");        // int(0)          (previously 16)

  var_dump(substr("foo", "0x1")); // string(3) "foo" (previously "oo")
  // Notice: A non well formed numeric value encountered
```

filter\_var() can be used to check if a string contains a hexadecimal number or convert such a string into an integer:

```
$str = "0xffff";
$int = filter_var($str, FILTER_VALIDATE_INT, FILTER_FLAG_ALLOW_HEX);
if (false === $int) {
    throw new Exception("Invalid integer!");
}
var_dump($int); // int(65535)
```

#### Unicode escape sequence

Due to the addition of the Unicode Codepoint Escape Syntax for double-quoted strings and heredocs, “\\u{“ followed by an invalid sequence will now result in an error:

```
  $str = "\u{xyz}"; // Fatal error: Invalid UTF-8 codepoint escape sequence
```

To avoid this the leading backslash should be escaped:

```
  $str = "\\u{xyz}"; // Works fine
```

However, “\\u” without a following { is unaffected. As such the following code won’t error and will work the same as before:

```
  $str = "\u202e"; // Works fine
```

### Error handling

#### Errors as throwables

There are now two exception classes: Exception and Error. Both classes implement a new interface Throwable. Type hints in exception handling code may need to be changed to account for this.

#### Fatal errors

Some fatal errors and recoverable fatal errors now throw an Error instead. As Error is a separate class from Exception, these exceptions will not be caught by existing try/catch blocks.

For the recoverable fatal errors which have been converted into an exception, it is no longer possible to silently ignore the error from an error handler. In particular, it is no longer possible to ignore type hint failures.

#### Parser errors

Parser errors now generate a ParseError that extends Error. Error handling for eval()s on potentially invalid code should be changed to catch ParseError in addition to the previous return value / error\_get\_last() based handling.

#### Internal class constructor failures

Constructors of internal classes will now always throw an exception on failure. Previously some constructors returned NULL or an unusable object.

#### Reclassification of E\_STRICT

The error level of some E\_STRICT notices has been changed.

### Other language changes

#### Static calls to non-static methods

Removed support for static calls to non-static methods from an incompatible `$this` context. In this case $this will not be defined, but the call will be allowed with a deprecation notice. An example:

```
  class A {
      public function test() { var_dump($this); }
  }

  // Note: Does NOT extend A
  class B {
      public function callNonStaticMethodOfA() { A::test(); }
  }

  (new B)->callNonStaticMethodOfA();

  // Deprecated: Non-static method A::test() should not be called statically
  // Notice: Undefined variable $this
  NULL
```

Note that this only applies to calls from an incompatible context. If class B extended from A the call would be allowed without any notices.

#### Reserved words

It is no longer possible to use the following class, interface and trait names (case-insensitive):

```
  bool
  int
  float
  string
  null
  false
  true
```

This applies to class/interface/trait declarations, class\_alias() and use statements.

Furthermore the following class, interface and trait names are now reserved for future use, but do not yet throw an error when used:

```
  resource
  object
  mixed
  numeric
```

#### Parenthesis requirement for `yield`

The yield language construct no longer requires parentheses when used in an expression context. It is now a right-associative operator with precedence between the “print” and “⇒” operators. This can result in different behavior in some cases, for example:

```
  echo yield -1;
  // Was previously interpreted as
  echo (yield) - 1;
  // And is now interpreted as
  echo yield (-1);

  yield $foo or die;
  // Was previously interpreted as
  yield ($foo or die);
  // And is now interpreted as
  (yield $foo) or die;
```

Such cases can always be resolved by adding additional parentheses.

#### Other removals

*   Removed ASP (`<%`) and script (`<script language=php>`) tags. (RFC: https://wiki.php.net/rfc/remove_alternative_php_tags)
*   Removed support for assigning the result of new by reference.
*   Removed support for scoped calls to non-static methods from an incompatible `$this` context. See details in [https://wiki.php.net/rfc/incompat\_ctx](https://wiki.php.net/rfc/incompat_ctx).
*   Removed support for `#`-style comments in ini files. Use `;`-style comments instead.
*   `$HTTP_RAW_POST_DATA` is no longer available. Use the `php://input` stream instead.

## Standard Library Changes

*   `substr()` now returns an empty string instead of `FALSE` when the truncation happens on boundaries.
*   `call_user_method()` and `call_user_method_array()` no longer exists.
*   `ob_start()` no longer issues an `E_ERROR`, but instead an `E_RECOVERABLE_ERROR` in case an output buffer is created in an output buffer handler.
*   The internal sorting algorithm has been improved, what may result in different sort order of elements that compare as equal.
*   Removed `dl()` function on fpm-fcgi.
*   `setcookie()` with an empty cookie name now issues an `E_WARNING` and doesn’t send an empty set-cookie header line anymore.

## Other Changes

### Curl

*   Removed support for disabling the CURLOPT\_SAFE\_UPLOAD option. All curl file uploads must use the curl\_file / CURLFile APIs.

### Date

*   Removed $is\_dst parameter from mktime() and gmmktime().

### DBA

*   dba\_delete() now returns false if the key was not found for the inifile handler, too.

### GMP

*   Requires libgmp version 4.2 or newer now.
*   gmp\_setbit() and gmp\_clrbit() now return FALSE for negative indices, making them consistent with other GMP functions.

### Intl

*   Removed deprecated aliases datefmt\_set\_timezone\_id() and IntlDateFormatter::setTimeZoneID(). Use datefmt\_set\_timezone() and IntlDateFormatter::setTimeZone() instead.

### libxml

*   Added LIBXML\_BIGLINES parser option. It’s available starting with libxml 2.9.0 and adds suppport for line numbers >16-bit in the error reporting.

### Mcrypt

*   Removed deprecated mcrypt\_generic\_end() alias in favor of mcrypt\_generic\_deinit().
*   Removed deprecated mcrypt\_ecb(), mcrypt\_cbc(), mcrypt\_cfb() and mcrypt\_ofb() functions in favor of mcrypt\_encrypt() and mcrypt\_decrypt() with an MCRYPT\_MODE\_\* flag.

### Session

*   session\_start() accepts all INI settings as array. e.g. \[‘cache\_limiter’⇒‘private’\] sets session.cache\_limiter=private. It also supports ‘read\_and\_close’ which closes session data immediately after read data.
*   Save handler accepts validate\_sid(), update\_timestamp() which validates session ID existence, updates timestamp of session data. Compatibility of old user defined save handler is retained.
*   SessionUpdateTimestampHandlerInterface is added. validateSid(), updateTimestamp() is defined in the interface.
*   session.lazy\_write(default=On) INI setting enables only write session data when session data is updated.

### Opcache

*   Removed opcache.load\_comments configuration directive. Now doc comments loading costs nothing and always enabled.

### OpenSSL

*   Removed the “rsa\_key\_size” SSL context option in favor of automatically setting the appropriate size given the negotiated crypto algorithm.
*   Removed “CN\_match” and “SNI\_server\_name” SSL context options. Use automatic detection or the “peer\_name” option instead.

### PCRE:

*   Removed support for /e (PREG\_REPLACE\_EVAL) modifier. Use preg\_replace\_callback() instead.

### PDO\_pgsql:

*   Removed PGSQL\_ATTR\_DISABLE\_NATIVE\_PREPARED\_STATEMENT attribute in favor of ATTR\_EMULATE\_PREPARES.

### Standard:

*   Removed string category support in setlocale(). Use the LC\_\* constants instead.
*   Removed set\_magic\_quotes\_runtime() and its alias magic\_quotes\_runtime().

### JSON:

*   Rejected RFC 7159 incompatible number formats in json\_decode string - top level (07, 0xff, .1, -.1) and all levels (\[1.\], \[1.e1\])
*   Calling json\_decode with 1st argument equal to empty PHP string or value that after casting to string is empty string (NULL, FALSE) results in JSON syntax error.

### Stream:

*   Removed set\_socket\_blocking() in favor of its alias stream\_set\_blocking().

### XSL:

*   Removed xsl.security\_prefs ini option. Use XsltProcessor::setSecurityPrefs() instead.

# Notes

# Part 2 - Language Changes & Improvements

1https://www.zend.com/en/resources/php7\_infographic[↩](#chap32.xhtml#fnref-zendbenchmarks)