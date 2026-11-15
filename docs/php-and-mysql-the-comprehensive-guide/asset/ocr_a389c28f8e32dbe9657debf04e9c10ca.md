# Chapter 23

# PostgreSQL

Another popular open-source database is PostgreSQL. It is therefore not surprising that there is a corresponding extension for PHP to access it.

The PostgreSQL database (www.postgresql.org) was originally developed by the University of California, Berkeley. The software earned recognition, but success only came after the source code was released as open source.

Many developers give PostgreSQL a wide berth because it is supposedly unstable and prone to data corruption. Fortunately, this is outdated information; unfortunately, it is only slowly disappearing from the minds of the developer community. PostgreSQL has blossomed into a really good database. Of course, some things are different from the established top dogs, but that is by no means an exclusion criterion.

However, the use of PostgreSQL in Windows was problematic for some time; additional packages had to be installed, some of which were even marked as deprecated—that is, obsolete. This too is now a thing of the past—albeit only recently.

PostgreSQL is a powerful database that could fill a book on its own. As in the other database chapters, we will focus on the standard tasks, so that you can implement projects with PostgreSQL, and then present some selected specialties of the database to motivate you to continue experimenting.

# 23.1 Preparations

At the beginning, there is always the installation. Binary versions for various operating systems are available directly on the PostgreSQL website at www.postgresql.org/download. This makes installation a breeze (this was not always the case in the past). Don't be surprised that the graphical installation programs are obtained from https://enterprisedb.com—that's quite right. Download the installation file and click through the installation. When specifying the data directory for PostgreSQL in particular, make sure that the database has write permissions for it. For the Windows program directory (see the default value from Figure 23.1), this is not automatically the case.