```
# Caching a value in Redis using Python
import redis
redis_client = redis.Redis()
redis_client.set('key', 'value', ex=3600) # Set to expire after 1 hour
```

+   3. Caching in Distributed Systems: Ideal for applications that scale across several servers or locations. It ensures cache data consistency across servers, maintaining data uniformity and accessibility.

+   4. CDN Caching: Leveraging CDNs to cache static content near users, CDNs minimize latency for static resources such as images, videos, and CSS files.

# Caching Approaches

+   1. Cache Invalidation: Defines the process for updating or discarding cached data. Strategies include time-based expiration, where data is invalidated after a set duration, and event-based invalidation, triggered by changes in the base data.

+   2. Filling the Cache: Concerns the method for introducing data into the cache. Lazy loading only caches data upon request if it's missing in the cache, whereas write-through caching adds data to the cache simultaneously with database writes.

+   3. Cache Eviction Policies: When cache space is limited, eviction policies decide which data to evict. Policies like Least Recently Used (LRU) remove the least accessed items first, while Least Frequently Used (LFU) targets items with minimal access.