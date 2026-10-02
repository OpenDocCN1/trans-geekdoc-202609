
Alternatively, you can download it from SVN and compile and install it manually. It may also be necessary to enable the extension in the php.ini file. Once the extension is installed, you can use several configuration variables to change its behavior. Some of the most common configurations are outlined in this section.

Setting apc.stat to 0 can turn off the file-stat operation for the opcode cache. Under normal operation APC checks to see if the PHP file has been modified before executing the cached version. If the file was modified, the cache is refreshed. Turning off the file-stat means that if a PHP file is cached, no hit is made to the file system at all. This option can improve performance but you should use it with care, because changes to PHP files will not be reflected until the cache is cleared or the server is restarted. This setting is ideal for production systems where files typically only change during the release of a new version, but it should be left as the default in development environments where the PHP changes often. In practice, however, file stat operations are very fast on most file systems so don’t expect immense speed improvements by using this directive.

The directives apc.ttl and apc.user_ttl are used to specify the default time to live for cached opcode files and user data, respectively, in seconds. The default for both is 0, which means that the data will never be cleared. This means that it is possible for the cache to fill up with stale, rarely used data, which will block additional and potentially more relevant data from being stored. A time to live of zero may be desirable for opcode cache but it is often not ideal for user data. The meaning of user data is covered shortly.

## Installing and Configuring eAccelerator

eAccelerator is another popular opcode caching extension. It is based on an open source project called Turck MMCache and still retains some of the original code. It is licensed under the GNU General Public License and like APC also makes the full source code available. However, it is maintained independently from the PHP community.

Installing and configuring eAccelerator on a Linux-based system with a compiler and build environment already set up is easy:

```
phpize
./configure --with-eaccelerator-shared-memory
make
make install
mkdir -p /var/cache/eaccelerator
chmod 0777 /var/cache/eaccelerator
```

The parameter passed to the configuration script is important for enabling user caching. If you do not want a user cache, you can exclude it. The next step is to configure eAccelerator, which you must do manually by adding a few lines to the php.ini file:

```
extension="eaccelerator.so"
eaccelerator.shm_size="16"
eaccelerator.cache_dir="/tmp/eaccelerator"
eaccelerator.enable="1"
eaccelerator.optimizer="1"
eaccelerator.check_mtime="1"
eaccelerator.debug="0"
eaccelerator.filter=""
```

```
eaccelerator.shm_max="0"
eaccelerator.shm_ttl="0"
eaccelerator.shm_prune_period="0"
eaccelerator.shm_only="0"
eaccelerator.compress="1"
eaccelerator.compress_level="9"
```

The eaccelerator.cache_dir directive must be the same as the directory created in the previous step. All directives that include the term “shm” refer to shared memory. By setting time to live values and a maximum size of the shared memory it is possible to prevent the cache from becoming overwhelmingly large.

eAccelerator also has a built-in opcode optimizer that attempts to make the compiled PHP scripts more efficient. The optimization step occurs only during the initial compilation so it is inexpensive and it is usually best to leave it on.

Like APC, eAccelerator does not automatically evict data from the cache unless a time to live is specified. This means that the cache can become full or too large to fit in shared memory (and therefore slower). You can use the eaccelerator.shm_ttl directive to configure a default time to live for all data in shared memory. Unlike APC there is no way to configure the value for just the user cache, so the time to live will also affect opcode caches.

## User Cache

The user cache doesn’t have anything to do with any application-level concept of a user, but is rather a cache that can be used to store whatever the application wants. APC has user cache as a basic feature whereas, as mentioned earlier, it needs to be enabled at compile time in newer versions of eAccelerator.

User cache can store arbitrary values using an application-defined key. It is up to the application to make sure that the key is unique. Also, when caching a value into the cache it is possible to set a time to live for just that key. Because both extensions do not expire, cached data by default makes it possible to exclude this value from the function call if the data never changes or include it if the data is expected to become stale or irrelevant.

It is the responsibility of the application developer to determine the optimal time to live. There is a definite trade-off between keeping data longer and incurring extra storage costs or evicting data and requiring additional calculation if the data needs to be re-accessed later. However, when properly tuned the cache can prevent excess hits to external resources — like the MySQL database — and dramatically improve application performance.

The two most common methods in either extension are the set and get/fetch operations. The two operations can be easily invoked. For APC:

```
apc_store( "key", $object, 3600 );
$stored_object = apc_fetch( "key" );
```

For eAccelerator:

```
eaccelerator_put( "key", serialize($object), 3600 );
$store_object = unserialize( eaccelerator_get( "key" ) );
```

Both store methods have the same parameters in the same order: key, value, and then time to live. In each case the key is the word “key” (which is, incidentally, a very bad key name) and the time to live of one hour. The key difference is that eAccelerator does not automatically serialize the data. Forgetting to serialize an object when using eAccelerator causes a fatal error when the application tries to retrieve the data, making it difficult to debug errors.

In both cases it is not a bad idea to serialize objects. APC is known to have issues with some complex array structures, which can be solved by serializing. Also, in both cases, it is not necessary to serialize strings, Booleans, and numbers because those are already primitives.

The one thing that can never be stored in cache is a resource, which includes MySQL and file handles. Those have to be reopened on each execution.

The most common use of the user cache is to store content from a resource that is expensive to access, such as a database server, external HTTP server, or even the file system. It will always be faster to access the data from memory.

## Checking the Cache Status

It is often desirable to check the status of the cache to determine if it is effective and if the system has the right amount of resources allocated for it. Both APC and eAccelerator have different methods for determining cache utilizations and provide different qualities of information.

In eAccelerator it is possible to display all the keys currently stored in the user cache using the function eaccelerator_list_keys(). The return value is an array of key information that looks something like this:

```
Array
(
    [0] => Array
        (
            [name] => key_name
            [ttl] => 125655832
            [created] => 1256555787
            [size] => 23583
        )
)
```

Each item in the array is a different stored value. The output tells you the name of the key, the time when the key becomes stale, the time it was created, and the size in bytes. The value of ttl will be –1 if the key is stale and is ready to be garbage collected; however, the key will remain in memory until space is needed for additional storage.

Another useful function is eaccelerator_info(), which returns all the information available in phpinfo() about eAccelerator but also some additional data such as memory usage and how many scripts are cached:

```
Array
(
    [version] => 0.9.5.3
    [shm_type] => mmap_anon
)
```
