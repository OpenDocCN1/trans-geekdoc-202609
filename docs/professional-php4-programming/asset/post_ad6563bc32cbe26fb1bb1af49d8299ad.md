
## Summary

In this chapter we've looked deeply into optimizing PHP code.

We've suggested a methodology for optimizing code based on:

- Profiling
- Analysis of script profiles
- Optimization of bottlenecks

Then we looked into several different optimization approaches like:

- Optimizing code
- Optimizing the database
- Buffering output
- Caching

While PHP programmers are proud of the "speed of coding" concept, the "speed of code" goal may appear. So PHP programmers should be aware of optimization techniques.

## PHP Extension Libraries

PHP comes with over 75 extensions to the core language. These extensions allow developers to handle such diverse tasks such as the creation of PDF files to scripting Flash movies, from creating dynamic WAP and WML pages to creating images on the fly.

Extension support in PHP came with the release of PHP3 in which dynamic module support was made available. This meant (and is still true for PHP4) that third-party authors could easily write PHP extensions to add functionality to their programs.

One of the first and most widely used extension libraries is the PHP Base Library (also known as PHPLIB). PHPLIB, though written explicitly for PHP3, still contains many useful session handling functions, which you might like to have a look at. PHPLIB is available at http://phplib.netuse.de/. Note that PHPLIB is not an extension library per se, it is a collection of PHP scripts which are intended to extend the functionality of PHP3.

PHP-GTK is a new library, intended to give PHP functionality outside of the web atmosphere. It is now available at http://www.php.net/. This extension implements GTK+ language bindings, allowing an object-oriented interface to GTK+ functions and classes. This allows programmers to write cross-platform GUI applications. Note that GTK+ is not for use in an Internet environment and is provided solely for the creation of standalone applications.

Using libraries with PHP sometimes seems like overkill. Programs which make use of extensions can be composed of many function calls to perform a simple task such as generating text or outputting an image. However, keep in mind that PHP extension libraries provide wonderful ways of achieving tasks that would otherwise be impossible using PHP alone.

Note that the code for the examples in this chapter, and working examples of the code snippets, are available for download on the Wrox web site (http://www.wrox.com/).

## The PDF Library

The free PDFLib is quite a useful extension in that it allows the creation and modification of PDF documents (PDF documents are Adobe's attempt to provide a standardized high-quality document format). Additionally, since this method of creating PDF files is free, it is a great way to create them.

### Installation

Installing PDFLib on Windows systems is quite easy: copy the dynamic extension (php_pdf.dll) to your "extensions" directory (if it is not already there), and uncomment extension=php_pdf.dll in php.ini.

Installing on UNIX and UNIX flavored systems, however, can be quite a different story. There are two different methods of adding PDFLib support to these systems: using loadable modules, as with Windows, or by building PDFLib into PHP. The latter method is quite a difficult task, as you must rebuild PHP to incorporate the support. Before installing PDFLib, however, you will need to install LibTIFF and LibJPEG, which can be found at http://www.libtiff.org/ and ftp://ftp.uu.net/graphics/jpeg/, respectively.

> The binary distribution of PDFLib is for commercial licensing only. If you would like to use the PDF Import Library (also referred to as PDI), you must use the binary version of PDFLib, as PDI is not available in the source form.

To install PDFLib as a loadable module, which is the recommended way of installing PDFLib on your system, you must first make sure the following conditions are met:

- PDFLib support must not have already been compiled into PHP. You can check this by using the phpinfo() function. If you see a line in the configure script that says --with-pdflib=yes or --with-pdflib=<dir>, you will need to recompile PHP with the --with-pdflib=no configuration option.
- The module must be placed in the directory set as the extensions directory in php.ini.
- php.ini must include both safe_mode=Off and enable_dl=On.
- Properties of your PHP version must match the loadable module build – your build must not be a debug version and it must be thread safe. If you get an error, you may want to check the <pdflib-directory>/bind/php/ directory, which may contain a module that will work with your specific build of PHP.

If you have already compiled PDFLib into PHP and are wondering why you would want to use the pre-built binary module, it contains PDI support, which is, as previously mentioned, not found in the sources. Currently, dynamic modules for PHP 4.0.4pl1, PHP 4.0.5, and PHP 4.0.6 (for UNIX and Windows) are available in the distributed tarball.

Once the extension has been copied to the directory specified in php.ini, you should load it using the extension=php_pdf.dll or extension=libpdf_php.so. If you don't wish to add this line to your php.ini file, you can include PDFLib support in individual files using the dl("'<pdflib_module>'") function. Using the dl() function can be quite beneficial when PHP is running as a CGI process (as opposed to running as a module) and allows the extension to be loaded as needed, as opposed to every time a new process of PHP is started.

To build PDFLib support into PHP, you will need to follow these steps:

- Unpack the PDFLib distribution (binary or source) to <pdflib_directory> and run "make" and "make install".
- Copy the PDFLib files for PHP into your PHP source tree with "cp <pdflib_directory>/bind/php/ext/pdf/* <php_directory>/ext/pdf".
- When rebuilding PHP with PDFLib from source, configure PHP with "--with-pdflib=<pdflib_installation_directory>" where the installation directory will be your operating system distribution's equivalent of /usr/lib/. Otherwise, configure PHP with "--with-pdflib=<pdflib_directory>/bind/c".
- Rebuild PHP as you normally would ("make; make install").

## Using PDFLib

The PDFLib functions are self-explanatory and most are generally easy to use. The only hard thing about PDFLib is the fact that scripting a document takes longer than actually writing one, thus the actual creation of a PDF document can get a tad confusing.

Assuming we have built PDFLib into PHP (or included it in our php.ini file), we can make a simple PDF file with PHP, containing very simple information. This may look like quite a bit of code just to create a PDF file that says "Sample Text in Arial Font!". Fortunately, most of the following commands are parts of a template for any other PDF document you wish to create.

This text will come at the top of any PHP-generated PDF document you write:

```
<?php
//pdfdemo.php

$pdfFile = pdf_new();
PDF_open_file($pdfFile, "");
```

Here, we set standard PDF document information about who created this document, and what it is for:

```
pdf_set_info($pdfFile, "Author", "Devon O'Dell");
pdf_set_info($pdfFile, "Creator", "Devon O'Dell");
pdf_set_info($pdfFile, "Title", "PDFLib Demonstration");
pdf_set_info($pdfFile, "Subject", "Demonstrating the PDFLib");
```

This line begins a new page. You will probably want to use 595 and 842 for the width and height of your document every time you make a new one, as these values are the standard size of a page:

```
pdf_begin_page($pdfFile, 595, 842);
```

This function adds a bookmark for the following page. This is quite useful if we have multiple sections in our document and need to jump around with a table of contents (TOC). When using this function, the PDF reader will automatically make a TOC at the right hand side of the screen which allows users to jump around to different pages in the document quickly, based upon the topic:
