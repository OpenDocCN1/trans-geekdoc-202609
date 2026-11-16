
These lines can be added virtually anywhere, but should be placed near all the other AddType and AddHandler directives in the file in order to keep things clean. Note that PHP should already have edited this file to add the following line:

```
LoadModule php6_module lib/apache/libphp6.so
```

Confirm that the preceding line is already in your httpd.conf file. If not, add it.

## Testing Your Installation

All that remains is to test your installation. Start Apache using the following syntax:

```
# /usr/local/apache/bin/apachectl start
```

Now create a file in /usr/local/apache/htdocs called test.php containing the following code:

```php
<?php
phpinfo();
?>
```

Save it and, in your workstation's Web browser, point it to the IP address of your UNIX machine, followed by /phpinfo.php. For example, if your server is 192.168.1.1, point it to http://192.168.1.1/phpinfo.php. You should see a screen showing the full details of your PHP installation.

If so, congratulations. Your PHP installation has been successful! You will probably want to create virtual server entries for each project that you work on, however. Much more information on this can be found in Chapter 21.

## When Windows Is Needed

Scenarios do crop up for which you will simply have to use Windows. The most classic example is for the installation of a closed system onto a large company's IT infrastructure, which is already Windows-based, and management has resolutely refused to install a UNIX server.

With some adaptation, the examples in this book will all still work just fine. The following pointers may help you transfer your PHP from UNIX to Windows.

## Changing Paths

Don't forget that paths on Windows look very different from paths on UNIX. References to paths such as /data/res/1230.jpg on disk need to be changed to a Windows equivalent, such as C:\data\res\1230.jpg.

PHP is kind and allows you to keep the slashes oblique (/). If you avoid drive letters by using relative paths, you may be able to keep your application more portable.

## External Libraries

Because Windows does not come with a built-in and highly pervasive C/C++ compiler in the same way UNIX does, PHP does not require a myriad of external libraries to work under Windows. Instead, PHP supplies with its Windows installations a huge set of precompiled DLLs for the various extensions discussed in this appendix. Note that these DLLs are only supplied with the ZIP distribution of the Windows binaries. You should not install PHP on Windows using the .msi installer.

To enable such extensions, ensure that the PHP extensions directory is in the system PATH (such as C:\php\ext), ensure that the extension_dir directive is set properly in php.ini (it is not, by default, set to a useful value for a Windows installation), and restart your Web server. You should find that the relevant functionality becomes available to PHP right away.

## Using PEAR

Using the PEAR repository to install library packages in Windows is a little different from how it is accomplished under UNIX. Before you can use PEAR, you must set it up using the following bundled script:

```
C:\php\PEAR>..\php go-pear.php
Welcome to go-pear!
Go-pear will install the 'pear' command and all the files needed by
it. This command is your tool for PEAR installation and maintenance.
```

This script will ask you various questions about proxy servers and so forth, but creates a single pear command as a batch file, which you can then use in exactly the same manner as its UNIX counterpart.

## Summary

In this appendix, you learned the key reasons why this book has opted for UNIX, Apache, and PostgreSQL in its examples, and why you might want to consider doing the same in your own PHP enterprise development.

You then learned the fundamental steps involved in setting up a working, practical installation of Apache, PHP, and PostgreSQL on a UNIX platform from start to finish.

Finally, you learned some of the key differences between PHP on Windows and UNIX, and how to circumnavigate them effectively in your own development.

### A

- _a flag, rsync, 564
- abstract class diagram, observer pattern, 84-86
- abstract classes
  - designing widgets to descend from, 88
  - indicating inheritance from, 38
  - interfaces vs., 77
  - in PHP 6, 29
  - when to use in class diagram, 77
- abstract methods
  - DataBoundObject class, 181
  - defining in parent class to implement in child, 174, 181
  - implementing all interface, 26
  - implementing in subclasses, 26
- AbstractInstrument class, 77-81
- academic skills, of PHP professional, 630
- accessor methods
  - DataBoundObject class, 183
  - overview of, 10-11
  - prototyping business objects, 160
- account manager, choosing, 411
- activation, UML sequence diagrams, 45
- activity diagrams, UML, 42-44, 190
- actors, use case diagrams, 33-35
- AddConstraint() method, 329
- _addFunction method, SoapServer, 229
- addItem() method, Collection class, 105-107, 109
- addObserver() method, Observable interface, 86, 87-88
- addRecord() method, Observable interface, 88
- administrator
  - CMS building, 588-589
  - login to Mantis as, 547-548
- Advanced PHP Debugger (APD), 664
- agenda, identifying project, 395
- aggregates, UML class diagrams, 39
- agile development methodologies, 426
- Agile Modeling: Effective Practices for eXtreme Programming and the Unified Process (Ambler and Jeffries), 630
- algorithms
  - performance bottlenecks in, 664
  - performance problems, 662
- Alternative PHP Cache (APC), 662
- ampersand (&), 81
- annotating bugs, Mantis, 553
- Apache Web server
  - choosing for PHP installation, 674
  - configuration in live staging environment, 557-558
  - configuration in studio staging environment, 557
  - handling PHP high traffic/high availability, 598-599
  - installing PHP and, 677-679
  - testing installation, 679
  - Ulysses only compatible with, 362
- APC (Alternative PHP Cache), 662
- APD (Advanced PHP Debugger), 664
- app log, 209
- application architecture
  - MVC. See MVC (model-view-controller) design pattern
  - overview of, 305-306
  - true templating, 333-342
  - unit testing. See unit testing
- application frameworks
  - application structure, 356
  - database abstraction, 359
  - deployment considerations, 379-380
  - development environments for. See development environments
  - example application. See Ulysses
  - form persistence, 358
  - object relation mapping, 358-359
  - overview of, 355-356
  - Prado, 377-378
  - separation of code and display logic, 356-357
  - summary, 380
  - URL rewriting, 357
  - use case scenario, 359-361
  - utility classes, 359
  - validation, 357
  - Zend Framework, 378-379
- application servers, 599, 616
- application structure
  - frameworks providing, 356
  - Ulysses framework, 376
- architecture, high-performance, 667
- archive mode, rsync, 564
- $arRelationMap member variable, 170
- arrows, Zend Studio Debug window, 651
- ASP-based Web sites, Web servers for, 673
- asset servers
  - hardware load balancing and, 604
  - improving infrastructure performance, 615
- associations, class diagrams, 37-38
- associative arrays (hashes), Smarty, 337
- attribute types, class diagrams, 36
- authentication
  - HTTP, 277
  - sessions and. See sessions and authentication
  - SMS code-sending as, 250
- author, CMS building, 588
- automated version control, repository extraction. See also version control
  - overview of, 562
  - using CVS, 562-563
  - using subversion, 563
- availability, in PHP. See high traffic/high availability

### B

- backup requirements, 434
- bandwidth
  - calculating CIR, 437
  - calculating monthly transfer, 438
  - high, 595
- base64 encoding, 531-533
- BaseCamp, 428
- basic authentication, live staging, 558
- beginTransaction() method, PDO, 142-143
- bi-directional navigability, 37
- binary files, version control and, 646
- bindColumn() method, PDOStatement, 147
- binding element, WSDL, 236
- bindParam() method, PDO, 140-141
- bindValue() method, PDO, 141
- bitwise logic, MVC mini toolkit constants, 312-314
- black box
  - creating test suite for your class, 345
  - unit testing with, 540
- blank servlets, 366
- bleeding servers, 424
- blind recipients, 260, 262
- bookmarks, 280
- Boolean flags, 170
- bottlenecks, performance
  - methods causing, 666-667
  - tracking down, 663-664
  - types of, 659-661
- branching, version control technique, 645
- breakpoints, Zend debugging, 653
- brief, formal project
  - budget, 401-403
  - business requirements, 398-399
  - commercial terms, 403-404
  - future plans, 404
  - look and feel, 404-405
  - overview of, 397-398
  - scope, 399-400
  - summary, 405-406
  - support, 405
  - technology, 405
  - timelines, 400-401
  - when to say no, 408-409
- broadcast e-mail providers, 274
- budget
  - business requirements, 434
  - receiving formal brief of, 401-403
- bugs, in Mantis, 550-554
- build process, 424
- builder pattern
  - considerations, 100
  - Director, 99-100
  - implementation of, 97-99
  - overview of, 96-97
- building application
  - cleaning up, 475-482
  - finalized Travel Expense Report, 514-529
  - finishing iteration, 483-492
  - mock objects, 529-533
