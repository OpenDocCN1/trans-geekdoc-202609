
```
set t1 0 0 4
test
STORED
get t1
VALUE t1 0 4
test
END
delete t1
DELETED
get t1
END
```

Though this chapter hasn’t covered the various memcached operations yet, you can easily understand what is being done here. As mentioned in the introduction, memcached has both an ASCII and a binary client protocol. The preceding example uses the ASCII protocol (which a human can type into a telnet session), which is a very simple protocol that is described at http://github.com/memcached/memcached/blob/master/doc/protocol.txt.

This process has the following steps:

- 1. The `version` command is run, which produces as response of 1.4.4 the version of this specific memcached server running locally.
- 2. The `set` command is run, along with the key name “t1”, flags, expiration value, and the length of the data you intend to cache in memcached for this key. The response of STORED verifies that t1 was stored.
- 3. The `get` command is run, specifying only the key, which results in the value for this item being fetched.
- 4. A `delete` command deletes the item using the key “t1” with a response of DELETED verifying the item was deleted, which a subsequent get of “t1” shows to not be available anymore.

Back in the terminal, you had started memcached with the -vv flag, you can see the server doing its job:

```
<32 version
>32 VERSION 1.4.4
<32 set t1 0 0 4
>32 STORED
<32 get t1
<32 sending key t1
>32 END
<32 delete t1
>32 DELETED
<32 get t1
>32 END
```

Which indeed it is!

You can also use this if you are troubleshooting caching issues in your application — such as determining if items are being cached on a given server or whether your application is using the cache to obtain data first before attempting to obtain data from the database.

## memcached Clients

To use memcached, as with any server, you also need a client to interact with the server. As already mentioned, the client is where all the functionality is implemented for making memcached instances work as one single unit, or pool of cache through consistent hashing. The clients you will want to be familiar with as a PHP developer are:

- **libmemcached:** This is a fast and efficient C library originally written by Brian Aker, now actively maintained by Brian Aker, Trond Nordbye, and several other developers that many different interpreted languages such as PHP, Perl, Python, and Ruby wrap around.
- **PECL/memcached:** This is a newer PHP PECL memcached client, interfaced to libmemcached.
- **PECL/memcache:** This is the original PHP memcached client (note the “e” versus “ed” at the end), implemented in pure PHP, not wrapped around any C library.
- **PHP libmemcached:** This client is a wrapper of libmemcached.

So, what client do you use? Well, the most recent, actively developed and feature-rich client is PECL/memcached. PECL/memcached, because it uses libmemcached, has more features than PECL/memcache:

- Optional use of the new memcached binary protocol
- Supports CAS operations
- Supports delayed `get`
- Supports `get/set` to a specific server
- Can store numeric values natively versus converting them to string values
- Allows you to set timeout as well as other options (behaviors) in the client
- Supports append and prepend operations

PECL/memcache does have one feature that PECL/memcached does not: Automatic key fixup for invalid keys. PECL/memcached will return a false for invalid keys.

## LIBMEMCACHED

Libmemcached is a faster memcached client library written in C that both the PECL/Memcached (the PHP client, discussed in the next section) and the Memcached Functions for MySQL (discussed in the next chapter) are built on top of. It is a faster, more efficient, thread-safe, full-featured C library that has a significant performance gain over existing client libraries. Not only that, but you also have much more control over how the client functions because you can set the client behavior (`memcached_behavior_set()`) with numerous behavior settings such as hashing algorithm or controlling whether the client is blocking or non-blocking, providing CAS (Check and Set) support, and sorting server host sorting, and so on.

This section gives you some familiarity with libmemcached because it is now the de facto client library on top of which so many other interpreted languages, including PHP, are built. Also, libmemcached has a number of useful client tools that can help you to work with memcached directly rather than having to write a utility in an interpreted language.

### Libmemcached Features

Some of the design notes for memcached are that libmemcached has:

- Synchronous and Asynchronous support.
- A high degree of control in setting how the client itself behaves.
- The ability to fetch and store data by a master key which means you can group values or objects to a specific server.
- TCP and Unix Socket protocols.
- A half dozen or so different hash algorithms.
- Implemented new CAS, replace, and append operators.
- Extensive documentation. Man pages cover, in detail, the entire API.
- Implemented both modulo and consistent hashing solutions, having to do with how data is partitioned among servers within the cluster.

### Libmemcache Utility Programs

Libmemcached also includes several command-line tools, shown in Table 4-2, that allow you to debug your memcached cluster as well as gauge its performance:

TABLE 4-2: Command-Line Tools

| COMMAND | DESCRIPTION |
|---|---|
| memcat | Copies the value of a key to standard output |
| memflush | Flushes the contents of your servers |
| memrm | Removes a key(s) from the server |
| memcp | Copies files to a memcached server |
| memstat | Dumps the stats of your servers to standard output |
| memslap | Generates testing loads on a memcached cluster |

Also of particular interest to readers of this book, libmemcached provides several client interfaces/ libraries to other languages such as Ruby, Python, Perl, and for this book, PHP.

## Installing libmemcached

You can install libmemcached via the OS vendor’s specific install utilities such as yum or apt-get; however, because libmemcached is a new project and changes often, it’s preferable to compile libmemcached from source or use the latest RPM from the libmemcached project page if you’re using a Linux distribution that utilizes RPM. The project page for libmemcached is found at http://tangent.org/552/libmemcached.html.

The following shows the code for installing via RPM, Ubuntu/Debian and source:

- RPM (Redhat, Suse, Fedora, Centos):
  ```
  wget http://download.tangent.org/libmemcached-0.34-1.x86_64.rpm
  rpm -ihv libmemcached-0.34-1.x86_64.rpm
  ```
- Ubuntu/Debian:
  ```
  $ sudo apt-cache search libmemcached
  libmemcached-dbg - Debug Symbols for libmemcached
  libmemcached-dev - Development files for libmemcached
  libmemcached-tools - Commandline tools for talking to memcached via libmemcached
  libmemcached2 - A C and C++ client library to the memcached server
  sudo apt-get install libmemcached2
  ```
- Source:
  ```
  tar xvzf libmemcached-0.35.tar.gz
  ./configure
  make
  sudo make install
  ```

At this point, libmemcached will be installed. You can write programs that utilize the libmemcached library (including the PHP driver PECL/memcached, discussed in the section “PECL/Memcached”) as well as use the utility programs.

## LIBMEMCACHED UTILITY PROGRAMS

As mentioned before, libmemcached includes useful utility programs that provide various functionalities for testing your memcached cluster. These utilities are simple to use and all specify a list of servers included with the servers option.

### memcat

This utility displays the output of one or more cached values in memcached by key value. For example, two values were stored using the code:

```
$memc = new Memcached();

$servers = array(
    array('localhost', 11211),
    array('localhost', 22122)
);

$memc->set('somekey', "This is a value in memcached");
$memc->set('anotherkey', 123456789);
```

You can view these stored values by using memcat:

```
$ memcat --servers=localhost:22122,localhost:11211 somekey anotherkey
This is a value in memcached
123456789
```

This code is a convenient means to quickly check what you have stored for a certain value without writing any code. Now, if you have stored a PHP object or other data structure — something other than a simple scalar, the object will probably not display correctly because it is stored serialized in memcached. You can also use the following code to figure out what value is cached on what server:

```
$ memcat --servers=localhost:11211 somekey anotherkey
123456789
```

```
$ memcat --servers=localhost:22122 somekey anotherkey
This is a value in memcached
```

As you can see, in both cases, both keys were used and only one value was fetched. In the first case, you see how the value for anotherkey is obtained from the memcached server running on port 11211. In the second case, the value for somekey is obtained from the memcached server running on port 22122.

### memflush

This utility does what the name implies — cleans house. It flushes all servers listed in the argument to --servers. The following code shows the usage and result after using memflush (or lack thereof).

```
$ memflush --servers=127.0.0.1:22122,127.0.0.1:11211

$ memcat --servers=localhost:22122,localhost:11211 somekey anotherkey

$
```

### memcp

This is a really nifty utility that allows you to copy a file to memcached. The file is keyed with the name of the file sans directory path

```
$ cat /etc/redhat-release
CentOS release 5.2 (Final)

$ memcp --servers=localhost:11211 /etc/redhat-release
$ memcat --servers=localhost:11211 redhat-release
CentOS release 5.2 (Final)
```
