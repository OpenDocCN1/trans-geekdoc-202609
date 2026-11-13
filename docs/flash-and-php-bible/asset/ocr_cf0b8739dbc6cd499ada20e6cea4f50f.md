Start by unpacking the archive that you just downloaded.

```
```bash
$ tar -xvf memcached-x.x.x.tar
```
```

Next, change the current directory to continue the installation.

```
```bash
$ cd memcached-x.x.x
```
```

The last step of the installation process is to create the installer script and install the application.

```
```bash
$ ./configure
$ make
$ make install
```
```

With memcached installed, start it up and move on to the PHP extension.

```
```bash
$ ./memcached -d -m 2048 -l 127.0.0.1 -p 11211
```
```

# ## Downloading the memcached extension for PHP

At this point, the next step is to install the PHP extension that is used to interact with memcached.

The first step is to download memcached from the PECL package repository.

```
```bash
$ wget http://pecl.php.net/get/memcache-x.x.x.tgz
```
```

> > **NOTE** The version number has been removed to ensure you download the correct version, rather than force a version on the reader. It is best to read the documentation before downloading a version.

# ## Installing the memcached PHP extension

Once the file is downloaded, unzip and untar the archive file.

```
```bash
$ gzip -df memcache-x.x.x.tgz
$ tar -xvf memcache-x.x.x.tar
```
```

Change to the directory that the memcached archive has created.

```
```bash
$ cd memcache-x.x.x
```
```

A call to phpize is made to build the unpacked files into a compatible PHP extension.

```
```bash
$ phpize
```
```

The next step is to configure the install, make the install files, and finally install the application using the following three commands:

```
```bash
$ ./configure
$ make
$ make install
```
```