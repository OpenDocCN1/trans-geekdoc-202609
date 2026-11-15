# ## Embedded Databases

An embedded database engine, as its name implies, sits inside the application that uses it (PHP in this case). Therefore it always runs — and stores its data — on the same machine as the host application. The database is not networked, and only one program can connect to it at any given time. Moreover, the database can’t be shared between different machines because each one would simply end up storing and manipulating its own separate version of the data.

On the plus side, embedded databases tend to be faster, easier to configure, and easier to work with.

Long-standing examples of embedded database engines include dBase and dbm, and PHP supports both these engines in the form of PHP extensions. A more recent addition to the fold is SQLite, which is bundled with the PHP engine itself, making it easy to install. It’s well worth a look, and some impressive performance stats certainly help back up its placement as the rising star of PHP database technologies. You can learn more about SQLite in Appendix C.

# ## Client-Server Databases

Client-server databases are, generally speaking, more powerful and flexible than embedded databases. They are usually designed for use over networks, enabling many applications in a network to work simultaneously with the same data. The database engine itself acts as a server, serving up data to its clients (much like Web servers serve pages to Web browsers). In principle it can field requests from just about anywhere with a network connection and a suitable client program. That said, there’s no reason why you can’t run both server and client on the same machine; in fact this is a very common setup.

This is the kind of database you’re more likely to find in a large company, where large quantities of data need to be shared among many people, where access may be needed from all sorts of different locations, and where having a single centralized data store makes important jobs like administration and backup relatively straightforward. Any applications that need to access the database use specialized, lightweight client programs to communicate with the server.

Most relational databases — including Oracle, DB2, and SQL Server — have a client-server architecture. (You look at relational databases in a moment.)

# ## Database Models

As well as the architecture of the database system, it’s worth thinking about the database model that you want to use. The model dictates how the data is stored and accessed. Many different database models are used today, but in this section you look at two common ones: the simple database model and the relational database model.

# ## Simple Databases

Simple database engines are, as the name implies, just about the simplest type of database to work with. Essentially, the simple model is similar to an associative array of data. Each item of data is referenced by a single key. It’s not possible to define any relationships between the data in the database.

For smaller applications there can often be advantages to using a simple database model. For example, if all you need to do is look up data based on keys, simple databases are lightning fast.

Common examples of simple-model databases include dbm and its variants, of which Berkeley DB is the most popular these days.