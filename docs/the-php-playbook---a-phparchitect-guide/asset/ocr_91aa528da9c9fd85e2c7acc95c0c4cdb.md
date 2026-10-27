chases to their needs. For example, database servers should be equipped with large amounts of storage space and very fast disks, while Memcached servers will have large amounts of RAM and relatively little disk space. Web servers should be able to handle high numbers of concurrent connections and have processing power to serve many threads of the web server.

Tailoring the servers to their specific roles can improve the performance of each server in the completion of that task, which in turn helps reduce the need for additional machines (because each machine already in use is more efficient).

# The Drawbacks of Expanding Hardware

Adding hardware does present some significant challenges, and is not without drawbacks.

When adding web servers, the first reality is that the file system is no longer an adequate place to store things, from media (images, uploads, etc.) to caches. Because the file system may be different on each machine, and depending on the load balancing setup, a user may not end up on the same machine on each request; sessions are an obvious casualty and must be moved to a more stable medium, such as Memcached.

Additional hardware also increases maintenance costs and reduces the ease with which new products can be rolled out. Since they must be rolled out to multiple machines, the planning process gets longer, and since there are multiple machines to maintain, failed disks and necessary upgrades cost that much more.

Finally, adding additional hardware adds complexity to the process of developing the application. With the file system gone as a resource and the possibility that any one of several database servers might be serving requests, issues with concurrency, latency, slave lag, missing cache data, multiple user tabs on the same session and a whole host of other issues come into play; that are not issues on a single server, or on single web server plus database master setups. These issues are challenging, and add to the overall complexity of managing an application.