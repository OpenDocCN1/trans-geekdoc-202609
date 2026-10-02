
to use. Two types of user cache were discussed in this chapter: local and distributed. eAccelerator and APC (Alternative PHP Cache) provide opcode caching and the application should always have one of them installed. Both extensions are much faster than compiling the PHP script on the fly and/or hitting the database; however, they only provide local user caching for arbitrary data.

Memcached is a high-performance, distributed memory object caching system that enables you to cache data that you would otherwise have to obtain from the database. This can benefit your application in many ways, such as relieving the load on the database, reducing application calls to the database, and providing faster data access because obtaining data from memcached is extremely fast — faster than obtaining it from the database. Unlike local solutions, memcached also provides redundancy and has the benefits of pooled resources and the ability to invalidate and change values across all machines that use the cache.

This chapter showed you everything you could possibly want to know about using caching in PHP. First, the local data and opcode caching systems were discussed. Then the basic concept of memcached was explained: how memcached is a simple memory server that allocates a block of memory for storing data, which is accessible with key values. Also, how memcached can run on multiple servers making it so you can utilize less-powerful machines (than database or web server machines) that have ample memory and have all machines work collectively as a cluster.

This chapter also explained read-through, write-through, and write-back cache and some simple demonstrations of each.

## 5
## memcached and MySQL
### WHAT'S IN THIS CHAPTER?
- Obtaining, installing, and configuring the Memcached Functions for MySQL
- Syntax and usage examples for various user-defined functions included with Memcached Functions for MySQL
- Constructing database statements that obtain data from both memcached and MySQL
- Using triggers to automatically cache data in memcached

In Chapter 4, the PHP client library PECL/memcached that PHP applications use to interface with memcached server pools is implemented at the application layer. What about memcached and MySQL? Is there any sort of interoperability between the two given that they are so commonly used together? It would be great if there was some sort of “glue” between the two, perhaps not even requiring you to have your interaction to each implemented in your PHP application code.

In the open-sourced world, if there is a need, then there is probably a solution to that need! This is why the Memcached Functions for MySQL — aka Memcached UDFs — were written.

This chapter shows you how to take advantage of the Memcached Functions for MySQL, a suite of user-defined functions that make it possible to cache and retrieve cached data at the database layer — from within MySQL.

### THE MEMCACHED FUNCTIONS FOR MYSQL
As you will see in Chapter 7, MySQL has an API for writing user defined functions, otherwise known as UDFs. That chapter shows an example of a UDF that has a file stat on a directory containing a schema’s data files to calculate how much disk space a given schema uses. Because the UDF API is so flexible, it’s possible to write many different user-defined functions to do a number of things. With the advent of libmemcached, it became obvious that you could take advantage of this API, along with the UDF API, to create functions that interact with memcached through libmemcached. This could provide all the functionality that you would normally implement with an external language, at the application layer, and this gives you the ability to interact directly with memcached at the database level.

Developed and maintained by the author of this chapter, the Memcached Functions for MySQL are a suite of functions available to use with MySQL that provide you the ability to interact with memcached from MySQL. These functions perform most of the operations shown in Chapter 4, just like PECL/memcached, because these functions are also built using libmemcached.

Because you can use these functions from within MySQL, you have at your disposal the power of an SQL engine in order to initiate caching or data retrieval using the result sets from query. You can combine the fetching of data from one or more tables with the fetching of data from memcached and apply any SQL operations on that result set, such as LIMIT, sorting, and other conditional operations.

Some other aspects of these functions are that they:
- Are written in C using libmemcached and the Memcached Functions for MySQL API
- Provide get, set, CAS, append, prepend, increment, decrement, delete, replace, add, flush, stats, client behavior setting and retrieval functions, as well as other functionality
- Can be used to store procedures and triggers
- Allow you to interact with memcached and MySQL independent of the language in which the application is written, or for languages that don’t have clients for memcached
- Are open source

### HOW THE MEMCACHED FUNCTIONS FOR MYSQL WORK
These user-defined functions are built with the libmemcached client library for various operations with a memcached server pool. When a particular UDF is called — say, when the user types `memc_get('mykey')` — the UDF processes the arguments, ensuring the proper number of arguments have been passed — in this case one argument, the key mykey — for the value that you desire to be retrieved. The UDF then passes this argument to the appropriate libmemcached API call, in this case `memcached_mget()`, `memcached_fetch_result()` and `memcached_result_value()`. So, what these UDFs provide are convenient functions that have the advantage of using the fast, lightweight libmemcached library, hiding the implementation details of the libmemcached calls, much in the same way that the PECL/memcached Memcached class does for PHP.

Figure 5-1 illustrates how these UDFs give the user the ability to access data from MySQL and memcached, and how simple they are implemented using API functions of libmemcached. Although memcached client support isn’t an issue with PHP, these UDFs make it possible to interact with memcached using any client that can talk to MySQL and solves the problem of an application that has no client support for memcached.

![](img/88e43d4c6a3d0e0d1f265975ce2f9f50_228_0.png)

FIGURE 5-1

### INSTALLING THE MEMCACHED FUNCTIONS FOR MYSQL
The MySQL plugin interface allows you to easily load UDFs. All that is involved is compiling, installing, and then running the SQL command to load the UDF shared library.

> To obtain the source for the Memcached Functions for MySQL go to: https://launchpad.net/memcached-udfs. This page provides links to the source code either as a source archive file or as a Bazaar revision control system through Launchpad repository where you can obtain the latest source.

### Prerequisites
The prerequisites for building, installing, and actually using the memcached functions for MySQL are:
- A MySQL or MariaDB database server
- libmemcached installed (Chapter 4)
- One or more memcached servers
- A compiler

### Configure the Source
To configure the source, follow these simple steps:
1. Untar/gzip the source package:
   `gzcat memcached_functions_mysql-1.0.tar.gz | tar xf -`
2. Enter the project directory: `cd memcached_functions_mysql`
3. Run the configure script:
   `./configure --with-mysql=/usr/local/mysql/bin/mysql_config --libdir=/usr/local/mysql/lib/mysql/plugin/`

The two arguments are as follows:
- `--with-mysql`: This argument tells the configure program where to find the `mysql_config` program, which provides the necessary compiler flags for the specific system so the UDFs can be built properly.
- `--libdir`: This is the directory where the compiled shared libraries are installed. On MySQL 5.0, this is the directory where other libraries are found. With 5.1, the plug-in interface was changed for programs such as storage engines and UDFs so that shared libraries would reside in a directory one level deeper within the normal library directory, called `plugin`.

Additionally, you may want to add an entry on your operating system so you can load the shared library. Some operating systems might need this set because, by default, they don't load dynamic libraries in directories that are in their library path. For example, if you must add an entry for `/usr/local/mysql/lib/mysql/plugin`, you would add a `mysql.conf` file in `/etc/ld.so.conf.d` that might look like this:

```
/usr/local/mysql/lib/mysql
/usr/local/mysql/lib/mysql/plugin
/usr/lib64/mysql/
```

You would then run `ldconfig` to create the necessary links and cache to the most recent shared libraries found in the directories you specified in `/etc/ld.so.conf.d/mysql.conf`:

```
sudo ldconfig
```

### Build the Source
The next thing you do is compile the source:

```
make
sudo make install
```

When you install the built source, the dynamic library created from the compilation are installed to the directory specified in the directory you used in the `--libdir` argument.
