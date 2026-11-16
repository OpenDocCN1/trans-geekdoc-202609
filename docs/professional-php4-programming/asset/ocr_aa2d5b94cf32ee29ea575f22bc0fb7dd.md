The md5( ) function is a message-digest function: it receives a string and after several computations provides a 128 bit digest of the string. It has the following properties:

+   - If we change the string (no matter if it is very long and we only change a byte) the md5 changes
+   - It's difficult to find two strings producing the same md5 value
+   - If we have the MD5 value it's impossible to recover the original string

That's why, probabilistically, md5( ) is a great function to generate values representing strings that are unique. The probability of 2 strings generating the same md5 number and thus crashing the system is pretty low. Chapter 23 covers md5( ) and other similar functions in relation to security.

# # Validation Criteria

Validation criteria are the way we determine if a cache entry is valid or not. The most common task is to check the last modification time of the cache file or entry, and if it's younger than a determined time then the entry is valid. This is a good way to force cache entries to be refreshed after a fair amount of time. For example, we may want to cache our home page but refresh it after 10 minutes in the cache.

Other validation criteria depend on what's being cached and how. For example, if we were to cache a process that parses an XML file and outputs some data, then our cache entry is invalid if the XML file has changed. In this situation we'll have to check the last modification time of the XML file, and if it is greater than the limit of the cache entry, we refresh the cache.

# # Refreshing Policies

If we don't want our cache to grow ad-infinitum then we'll need to specify a refreshing policy for the cache. A process that checks the cache for old data should be run at some time interval. If any old data is found it should be deleted. There are many algorithms for this procedure, like deleting the entries older than "x" minutes, deleting the "n" least recently used entries, or deleting the "n" least used entries. For some of these methods we need to store additional information in the cache, such as number of accesses or last access time. Sometimes the file system will provide the data and sometimes we'll have to store it ourselves.

Generally "least recently used" (LRU) algorithms are best for purging the cache. The refreshing procedure is usually implemented as a cron job running at regular time intervals. We can code the refreshing procedure in PHP using it as a scripting language and then setting it up in the crontab (in UNIX systems), as detailed in Chapter 20.

A LRU algorithm defines that if you have to delete "n" entries for the cache you must select the entries which have the maximum time unused in the cache. This policy assumes that recently accessed files will probably be accessed again if the data is in use. Data that has not been used for a long time can be deleted since it's less probable that it will be used again.

# # What Data Should be Cached?

Generally there are two types of data that can be cached – content and database queries.

# ### Caching Content

Caching content implies storing dynamically generated content in a file or group of files and then retrieving the data from a file instead of generating the data again. It is supposed that the generation process is either complex, slow, or that it depends on some external source so caching is necessary. To cache content you can use two different approaches – generic caching of all generated content, and ad-hoc caching of modules or some parts of the code.