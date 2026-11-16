# Disadvantages of Caching

Caching has also some disadvantages, the worst being added complexity to a site. To cache data we'll have to add lots of logic to the code to cache the data, to check the validity of the data, to refresh the cache when necessary, and to detect if the cache is valid or not. Depending on the type of data being cached, we may find that the logic for caching is not simple and we'll have to write special functions for the cache.

# A Generic Caching Policy

First let's take a look at the logic of a generic caching mechanism. It is applicable to almost all caching schemes and it will be used to determine what decisions should be made before setting a caching system:

![](bbox=[0.31, 0.3, 0.68, 0.6])

+   - Identify data being accessed
+   The principle behind caching is simple – store results from some operations so the operation needn't be repeated if they are requested again. Since we are going to store data independently of where we generate it, we have to build a "name" for the data, so you need to check if that name exists in the cache. For example, if you are caching output from functions you can use names like `cache_funcName.dat` (see the Naming Conventions section). If you have the function `printTable()` you can cache the result of that function in a file named `cache_printTable.dat`.

+   - Check cache for valid entry
+   If there's an entry for the given name in the cache, you have to check if the data is valid. For example, we can decide that the data is valid in the cache only for 5 minutes, so that fresh data is generated in the site every 5 minutes. Alternatively, we can decide that cached data is valid until something changes. We can check the last time a file was modified using the PHP function `filemtime()`.

+   - Pull data from cache
+   You access the cache and retrieve the data for the given cache name. The way to access the data depends on the storage strategy used. For file-based caching systems, pulling data from the cache usually implies opening a file and reading its content. If the cache uses an alternative storage mechanism this may change.