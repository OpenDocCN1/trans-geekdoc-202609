
# Chapter 11: Working with Files and Directories

In the next chapter you are introduced to another popular way of storing application data: databases. This is quite a big topic, so it's spread over the next three chapters. Chapter 12 introduces the concept of databases; Chapter 13 shows how to read data from a database; and Chapter 14 shows how to manipulate data in a database.

Before leaving this chapter, try the following exercise to test your knowledge of file and directory handling in PHP. You can find the solution to this exercise in Appendix A.

# Exercise

Create a PHP application that can be used to find a particular directory by name when given a top-level directory to search. Make the application look through the given directory, as well as all directories under the given directory.

# Introducing Databases and SQL

In the last chapter you learned how your PHP scripts can use external files to store and retrieve data. Although files do a great job in many circumstances, they're pretty inflexible as data storage solutions go. For example, if you need to filter or sort the data retrieved from a file, you have to write your own PHP code to do it. Not only is this tiresome, but if you're working with large sets of data — for example, hundreds of thousands of user records — your script will probably grind to a halt. Not good if you're hoping to build a popular Web site.

Databases are specifically designed to get around this problem. With their capabilities of organization and immaculate record keeping, they're a bit like lending libraries staffed by superheroes. No more searching for hours through shelves of musty tombs; just a work at the front desk, a blur of blue and red, and the last remaining copy of Love in the Time of Cholera appears — as by magic — on the desk in front of you.

This is the first in a series of three chapters in which you explore databases and learn how you can use them to create powerful, efficient PHP applications. The next chapter shows how you can access data in databases, and Chapter 14 looks at inserting, updating, and deleting data.

The aim of this chapter is to get started with databases. In this chapter you:

- Examine the general advantages of using databases rather than files to store your data
- Learn about some of the popular databases that you're likely to come across, and how they differ
- Examine the idea of relational databases, and explore common concepts of relational databases such as normalization and indexing
- Find out how to configure MySQL, a database system that's freely available and widely used with PHP

# Part III: Using PHP Practice

- Learn how to use MySQL to create databases, as well as retrieve and modify the contents of the database
- Study the basics of connecting and working with a MySQL database from within your PHP scripts

By the time you finish this chapter you will be well prepared to start using databases in earnest, which you do in Chapters 13 and 14.

# Deciding How to Store Data

Whenever you start on a data-driven application, one of your first design decisions should be: how will the application store and access its data? The answer will depend on the application's requirements. At the simplest level, you will be asking questions like:

- How much data will the application use?
- How often will it need access to the data?
- How often will it need to modify the data?
- How many users are likely to access the data at once?
- How much will the data grow over?
- How much do I stand to lose if the data is broken, stolen, or lost?

If the answer to any of these questions is “a lot,” you probably want to steer clear of using plain text files to store your data. That's not to say text files are useless — in fact, if all you want to read a large amount of unfiltered or unsorted data, text files often be the fastest approach — but generally speaking, if you need to store and access data quickly and reliably, plain text files aren't a good bet.

The most frequent alternative to text files is to use a database engine — commonly known as a Database Management System (DBMS) — to store, retrieve, and modify the data for you. A good database engine serves as a smart-go between you and your data, organizing and cataloging the data for quick and easy retrieval.

Where does all the data go? It depends on extent to the database engine you're using. Chances are, though, it'll be stored in a number of files — yes, Truth is that you can't get away from using files at some point. The trick is in finding ways to use them as efficiently as possible, and a good database has many, such tricks tucked up its metaphorical sleeves.

This book, and developers in general, often use the word “database” to refer to the engine, the data itself, or both. Usually the exact meaning is clear from the context.

# Database Architectures

Before you go, you need to settle on a particular database with which to experiment, and that means first deciding on the type of database architecture you're going to use. Broadly speaking, you have two main options: embedded and client-server. Let's take a quick look at both.

# Chapter 12: Introducing Databases and SQL

An embedded database engine, as its name implies, sits inside the application that uses it (PHP in this case). Therefore it always runs — stores its data — on the same machine as the host application. The database is not networked, and only one program can connect to it at any given time. Moreover, the database cannot be shared between different machines because each one would simply up storing and manipulating its own version of the data.

On the plus side, embedded databases tend to be faster, easier to configure, and easier to with.

Long-standing examples of embedded database engines include dbase and,, which supports both these engines in the form of PHP extensions. A more recent addition to the fold is SQLite, which is bundled with the PHP engine, making it easy to install. Well it is worth a look, and some impressive performance stats dearly help its placement as the rising star of PHP database technologies. You can learn more about SQLite in Appendix C.

# Client-Server Databases

Client-server databases are, generally speaking, more powerful and flexible than embedded databases. They are usually designed for over networks, enabling many applications in a network to work simultaneously with the same data. The database engine itself acts as a server, serving data to clients (like Web server serves pages to Web browsers). In principle it can handle requests from just anywhere with a network connection and a suitable client program. That said, there is no reason why you cannot run client and server on the same machine: this is a very

This is the kind of database you're more likely to find in a large company, where large quantities of data need to be shared among many people, where access may be needed from all sorts of locations, and where having a single centralized data store makes jobs like administration and backup relatively straightforward. Any applications that need to access the database use specialized, lightweight client programs to communicate with the server.

Most relational databases — including Oracle, DB2, and SQL Server — have a client-server architecture. (You look at relational databases in a moment.)

# Database Models

As well as the architecture of the database system, it's worth thinking about the database model that you want to use. The model dictates how the data is stored and accessed. Many different database models are used today, in this section you will look at two common ones: the simple database model and the relational database model.

# Simple Databases

Simple database engines are, as the name implies, the simplest type of database to work with. Essentially, the simple model is similar to an associative array of data. Each item of data is referenced by a single key. It's not possible to define any relationships between the data in the database.

For smaller applications there can be advantages to using a simple database model. For example, if all you need to do is look up data on keys, simple databases are lightning fast.

Common examples of simple-database includes include dbm and its variants, which Berkeley DB is the most popular these days.
