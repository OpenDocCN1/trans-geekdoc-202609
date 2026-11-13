# Caching

The topic of caching is normally looked at once you experience bottlenecks in an application, but you can install caching solutions before a problem occurs.

# Working with memcached

One of the bottlenecks in server-side scripts is the database. You have the ability to tweak the configuration, which you did in the previous section. Sometimes this can only go so far as a system continues to grow.

The answer to this problem is to install software to help deal with database slowdowns, such as memcached, which is a high-performance memory object caching system. This system is built with the intent to speed up dynamic Web applications by removing database load, which is encountered more often as the system continues to grow. You can download the latest version of memcached from danga.com at www.danga.com/memcached/.

# Installing memcached on Linux

The following section will cover the installation process of memcached on a Linux Web server. This version requires another library to be installed, which will also be covered.

# Installing libevent

Before you install memcached, you need to install a dependency library. This is libevent, which can be downloaded at www.monkey.org/~provos/libevent/.

Unpack the archive and perform the same installation steps you have seen in the previous examples when installing applications.

```
$ tar -xvf libevent-1.3b.tar.gz
```

Change the current directory to the newly created libevent to continue the installation process.

```
$ cd libevent-1.3b
```

The last step to setting up the dependency is to configure and build the necessary install files and install the libevent library.

```
$ ./configure
$ make
$ make install
```

# Installing memcached

Once libevent is installed, you can continue with the installation of memcached.

```
$ gunzip memcached-x.x.x.tar.gz
```