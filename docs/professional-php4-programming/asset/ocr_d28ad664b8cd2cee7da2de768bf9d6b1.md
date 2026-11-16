# # Verifying XML Support

Before we get started, make sure that the computer you're working with was set up to support XML. If you are not sure that your existing PHP installation has XML support, check phpinfo.php from Chapter 2. If XML support is set to active, the output will contain a section similar to the following:

![](bbox=[0.168, 0.2, 0.847, 0.515])

If you do not see the above, then don't worry. We will cover setting up XML support for each API in the appropriate section. For further information refer the PHP manual for instructions on installing PHP with XML support at: http://www.php.net/manual/en/ref.xml.php.

# # XML APIs Comparison

The three main PHP APIs available for working with XML are SAX, DOM, and PRAX. SAX and DOM are available in most programming languages. PRAX is a much newer API and it is a port of the Perl XML::RAX API.

These XML APIs that are "native" to PHP have some problems:

+   - SAX has some problems that can cause a server crash.
+   - DOM has memory leaks in the code library libxml1. The memory leaks are in all the PHP releases (current release is 4.0.6), on most platforms, Windows98/NT/2000, Linux (Redhat, Debian, Mandrake, SuSE), and xBSD.
+   - PRAX does not work very well with complex XML documents.

In spite of these minor difficulties, each of these APIs deals with XML in different ways, and provides different functions. Choosing which API to use depends on your application.