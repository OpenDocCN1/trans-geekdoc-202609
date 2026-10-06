# CHAPTER 12 TRYING NOT TO MAKE A MESS: DATA COLLECTION AND STORAGE

Python is called pickle. Anything can be saved this way, and it's common to save machine learning models this.

Another format that's becoming popular in cloud platforms is parquet, which is a good way to save a large amount of data because it can split across multiple files. Parquet files also work well with tools that split up time-consuming operations so the parts can be done simultaneously (this is called distributed computing, and it's common when working on cloud tools with large amounts of data).

There are more types of files for storing data emerging all the time, so it's good to stay on top of things.

# Databases

Database systems are a daily part of almost all data scientists' work. Databases are generally better than spreadsheets and text files for a variety of reasons, including from a storage management perspective and because of the ease of working with them. Database management systems are software that handle the storing of all information in databases. Users interact with it through a few ways, often with an interface hosted by the database to be written and run. Data scientists also use this interface, but much of the time, they interact with the system through Python or R code in other environments.

In the tech world, the term database itself basically means a collection of related data that can be accessed through a database management system. You'll often see the systems themselves referred to with the abbreviation DBMS (database management system), which can be any type of database. Most DBMS organize things at a high level into what they call databases, an object that can contain other objects like tables or other hierarchical objects. As a typical example, the Oracle DBMS has databases that can have many schemas, which have tables and objects objects inside them. A schema in this sense is simply an organizing object (for instance, permissions can be granted at the schema level