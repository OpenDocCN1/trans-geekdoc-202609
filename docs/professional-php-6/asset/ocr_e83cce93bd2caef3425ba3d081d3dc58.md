# Best Practice PHP Installation

These days, it seems anyone can handle a simple installation. Even your mom and dad could probably handle popping the latest version of Windows on their PC.

The exception to this rule seems to be server applications such as PHP. Although the PHP Web site and supplied documentation do touch on how to get it up and running, they never really go as far as explaining exactly that. Having a usable installation is quite a different matter and requires some inside knowledge.

This appendix examines the ins and outs of getting PHP properly set up in a configuration best suited to the kind of enterprise development detailed in this book. You’ll learn about the differences between PHP on Windows and PHP on UNIX, and discover which is better suited for enterprise development.

# Introduction to PHP Installation

PHP is an application language. It is not a server in its own right, or a piece of software in the traditional sense. Nor is it a compiler such as Pascal or C++. It must be installed — wrapped, if you like — in a Web server. With this in mind, for every installation of PHP, you need some kind of Web server, such as Apache.

The phrase “installing PHP,” therefore, is perhaps not quite accurate. The phrase “installing PHP and Apache” would be better, but that omits the fact that PHP is heavily dependent on third-party libraries and applications for any of its more sophisticated functionality.

To make things worse, most applications that this book introduces you to, as well as anything useful you’ll write yourself, require some kind of a back-end database. This book advocates PostgreSQL over MySQL, but they are much the same in practice.