endeavours and come to a sudden end once the individuals in question stop contributing their time. Otherwise, there is some emphasis on maintaining a degree of standardization throughout the library. For example, all error handling should be performed using PEAR::Error, and the code should be documented using the PHPDoc standard, which means you should be able to extract the API documentation using PHPDocumentor[6] (see Volume II, Chapter 6) if you can't find it on the PEAR Website.

Be warned: the degree of integration between the packages within PEAR is currently fairly low when compared to, say, the Java class library. This means, in some cases, that you'll be confronted with decisions like whether to use PEAR::HTML_QuickForm's validation functionality, or PEAR::Validate, or both. It's a good idea to invest some time investigating which fits your development style up-front, rather than jumping straight in and using a PEAR class for a critical part of your application, only to discover later that it wasn't the best fit for the problem.

One important point to be clear on is that referring to “PEAR” can actually mean one of two things: the repository as a whole, or the PEAR front end (also known as the package manager), which provides tools for installing and upgrading the PEAR packages you use.

Note that it’s not a requirement that you use the PEAR package manager to install PEAR packages. If you need to, you can download them directly from the PEAR Website and manually extract them to your PHP’s include path. Make sure you check the dependencies listed on the site (these being other required packages) and be aware that most packages implicitly require PEAR “base” package[7] for tasks like error handling.

# Installing PEAR

These days, the foundations of PEAR are provided with PHP distribution itself, but Web hosts typically fail to provide customers with their own default PEAR installation, so it’s worth knowing how to go about doing this from scratch. The process can differ slightly between Unix and Windows based systems.

Step one is to make sure you can run PHP scripts via the command line. This is always possible if you type the full path to the PHP binary. For a Unix based system, you’d use the following:

[6] http://www.phpdoc.org/
[7] http://pear.php.net/package/PEAR