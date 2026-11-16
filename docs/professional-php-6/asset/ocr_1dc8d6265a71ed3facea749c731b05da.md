That’s why it’s essential to understand this important topic right here and now. The database platform you choose for your project comes down to a number of important factors, and a true professional will almost certainly end up working with all four of the platforms mentioned previously at some point in his or her career.

Having said that, there will be moments where the choice is wide open, and it comes down to personal preference. The authors of this book prefer PostgreSQL in such circumstances. It’s free, fast, well supported, extensible, scalable, and reliable, and sports an enterprise-grade feature set that pips MySQL to the post. There’s no doubt this view goes against the grain, but, then again, so does the idea of PHP in the enterprise in the first place.

The important point here is that you realize that this is a *personal preference*; ultimately, *it does not matter*. Computer-related religious wars over anything (operating systems, languages, Web servers, databases) are deeply tiresome and are the hallmark of the spotty teenage programmer, not a professional. For every so-called expert who advocates platform X, you’ll find another who advocates platform Y, and who can probably do so every bit as eloquently.

So, to be blunt, *get over it*. This chapter (and, indeed, the rest of this book) will demonstrate to you why properly developed PHP applications are “database agnostic” — just as they are “Web-server agnostic” and “operating-system agnostic.” This book isn’t about “LAMP” or “LAPP”; if you took the nomenclature to its natural conclusion, this book is really about “XXXP” — that is, just PHP.

However, where you find examples in this book, they will be in PostgreSQL. You’ll find more information about its installation and configuration in Appendix D. If this choice bothers you intensely, the authors implore you to bite your tongue for the purposes of the broader education this book provides — and then go ahead and use *whatever you like* in your own projects. As this chapter and the next demonstrate, you won’t have to change very much to make the switch.

# Recap

Let’s recap how database connectivity in PHP has worked since the dawn of time. The following assumes a working installation of PHP, with PostgreSQL support enabled, and a working installation of PostgreSQL on the same box.

Create a new database in PostgreSQL at your console as follows:

```
$ /usr/local/pgsql/bin/createdb chaptersix
CREATE DATABASE
```

This syntax assumes PostgreSQL is installed on a Linux or other UNIX platform in the directory /usr/local/pgsql. If you’re running on Windows or Mac OS X, this might well be different. The PostgreSQL installer might have added the bin directory to your path. If this is the case, you can just enter createdb chaptersix.

The CREATE DATABASE message indicates that the database was created successfully from the console. That’s great, but your application must be able to connect to that database. Your application won’t run