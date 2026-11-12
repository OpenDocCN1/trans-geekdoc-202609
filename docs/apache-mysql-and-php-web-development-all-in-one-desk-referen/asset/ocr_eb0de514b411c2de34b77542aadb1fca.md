If you enable the module as a DSO, using shared, the compiled module
is stored in the modules subdirectory in the Apache main directory. A
LoadModule directive is needed in the main configuration file to tell Apache
to load the module and provide the location of the module. During the build
process, the LoadModule directive is automatically added to the configura-
tion file for you, along with the correct location for the module.

If you install the module as a DSO, you have more flexibility. You can remove
or add the module whenever you need to with the LoadModule directive,
without needing to recompile Apache.

# Using external modules

Many third-party modules are available for use with Apache. If you want to
use an external module, check the third party's Web site for information
about the module. Use the installation instructions provided with the module.
Some modules need to be installed statically; some work better as a DSO.

# Some Useful Modules

The following sections describe some modules with useful features.

# PHP

PHP is a scripting language used to make Web sites dynamic. PHP is the
most popular Apache module, according to a survey of Apache module use
conducted by SecuritySpace (www.securityspace.com/s_survey). Over
13 million domains use PHP, according to Netcraft (www.php.net/usage.php).

PHP is open-source software that runs on most operating systems and
works with most Web servers, not just on Linux with Apache. The PHP proj-
ect is supported by the Apache Software Foundation, the same group that
supports the development of Apache. Consequently, PHP runs particularly
well with Apache. PHP can be statically compiled and run as part of Apache
or can run as a DSO module.

PHP was designed specifically for use on Web sites and is particularly well
suited for that purpose. Book V discusses PHP in detail.

# Secure Sockets Layer (SSL) module

If you plan to send any important information between Apache and Web site
visitors' browsers, you need to use the Secure Sockets Layer (SSL) protocol.
With SSL, information sent between Apache and the browser is encrypted,
preventing anyone who intercepts the information from being able to under-
stand it. In addition, the SSL server holds a digital certificate, issued by
certificate authorities that verify the server's identity.