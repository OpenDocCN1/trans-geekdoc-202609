# Part III: Using PHP in Practice

+   - Learn how to use MySQL to create databases, as well as retrieve and modify the contents of a database
+   - Study the basics of connecting to and working with a MySQL database from within your PHP scripts

By the time you finish this chapter you’ll be well prepared to start using databases in earnest, which you do in Chapters 13 and 14.

# Deciding How to Store Data

Whenever you start work on a data-driven application, one of your first design decisions should be: how will the application store and access its data? The answer will depend on the application’s requirements. At the simplest level, you should be asking questions like:

+   - How much data will the application use?
+   - How often will it need access to the data?
+   - How often will it need to modify the data?
+   - How many users are likely to want access to the data at once?
+   - How much will the data grow over time?
+   - How much do I stand to lose if the data is broken, stolen, or lost?

If the answer to any of these questions is “a lot,” you probably want to steer clear of using plain text files to store your data. That’s not to say that text files are useless — in fact, if all you want to do is read a large amount of unfiltered or unsorted data, text files can often be the fastest approach — but generally speaking, if you need to store and access structured data quickly and reliably, plain text files aren’t a good bet.

Often, the most efficient alternative to text files is to use a database engine — commonly known as a Database Management System (DBMS) — to store, retrieve, and modify the data for you. A good database engine serves as a smart go-between for you and your data, organizing and cataloging the data for quick and easy retrieval.

So where does all the data go? Well, it depends to some extent on the database engine you’re using. Chances are, though, it’ll end up being stored in a number of files — yes, files! Truth is you can’t really get away from using files at some point. The trick is in finding ways to use them as efficiently as possible, and a good database engine has many, many such tricks up its metaphorical sleeves.

> This book, and developers in general, often use the word “database” to refer to the database engine, the data itself, or both. Usually the exact meaning is clear from the context.

# Database Architectures

Before you get going, you need to settle on a particular database with which to experiment, and that means first deciding on the type of database architecture you’re going to use. Broadly speaking, you have two main options: embedded and client-server. Let’s take a quick look at both.