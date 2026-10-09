# ## Improving performance using the cache

The cache software design pattern is where you store a result that takes a long time to generate. This could take the form of a lengthy view script or a complex database query. The storage destination needs to be highly performant, of course, if you wish to improve the user experience of website visitors. As different installations will have different potential storage targets, the cache mechanism lends itself to the adapter pattern as well. Examples of potential storage destinations include memory, a database, and the filesystem.

# How to do it...

+   1. As with a couple of other recipes in this chapter, as there are shared constants, we define a discreet Application\Cache\Constants class:
   ```php
   <?php
   namespace Application\Cache;

   class Constants
   {
       const DEFAULT_GROUP   = 'default';
       const DEFAULT_PREFIX  = 'CACHE_';
       const DEFAULT_SUFFIX  = '.cache';
       const ERROR_GET      = 'ERROR: unable to retrieve from cache';
       // not all constants are shown to conserve space
   }
   ```

+   2. Seeing as we are following the adapter design pattern, we define an interface next:
   ```php
   namespace Application\Cache;
   interface CacheAdapterInterface
   {
       public function hasKey($key);
       public function getFromCache($key, $group);
       public function saveToCache($key, $data, $group);
       public function removeByKey($key);
       public function removeByGroup($group);
   }
   ```

+   3. Now we are ready to define our first cache adapter, in this illustration, by using a MySQL database. We need to define properties that will hold column names as well as prepared statements:
   ```php
   namespace Application\Cache;
   use PDO;
   use Application\Database\Connection;
   ```