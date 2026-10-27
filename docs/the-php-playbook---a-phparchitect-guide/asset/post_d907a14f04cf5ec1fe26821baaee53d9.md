
are faster than instantiated object methods. However, converting all objects into static classes and static methods would be a fool's errand; it violates the tenets of object-oriented development and introduces a testing and maintenance nightmare for whomever comes after. Similarly, there is evidence that language constructs like `isset()` run faster than functions like `array_key_exists()`. However, if `array_key_exists()` is the appropriate tool for the job, by all means use it.

Finally, developers should avoid optimizations that do not actually solve their issue. Sometimes, code cannot be optimized. Sometimes the “optimization” is worse than the original implementation. Sometimes there is a big ugly method in the middle of a class and there is nothing a developer can do to fix it. Simply put, sometimes the optimization is worse than the bottleneck, and in those cases, it should be avoided.

## When Not to Optimize

So when should a developer optimize, and when should a developer consider other alternatives? There are four cases when a developer should consider alternatives to optimization.

Do not optimize when the issue is performance. Optimization is a fantastic tool, but is unlikely to solve every single performance issue a developer encounters. Instead, developers who experience performance problems should implement solutions that improve performance considerably, rather than the bit by bit that optimization promises.

Too often developers think that all performance problems can be solved through optimization. This is not necessarily true. Developers can certainly build a well-optimized product, but at some point the traffic and load necessitates identifying and implementing performance-enhancing solutions that optimization simply cannot deliver.

Avoid optimizing when code needs heavy refactoring. Optimization should be viewed as fine tuning. Code that is in serious need of refactoring should be refactored (see Chapter 7); you should not optimize it as a solution.

This really comes down to picking the right tool for the job. If the code is a mess, has performance issues, and needs to be heavily rewritten, optimizing it will ultimately be a waste of time. It is better for the developer to refactor the code (presum-

## Adding Database Servers

As web applications grow, the point where strain often becomes evident is in the database layer. This is for a number of reasons, including the fact that many web applications are heavily data-driven, meaning that they are heavy users of the database. Most of the time, the database is the first thing that has to be scaled.

In fact, it is always a good idea for a web application to have two database servers, which can preserve data from loss and help protect against downtime. It also helps developers determine the best way to write their applications for more than a single database server, which in turn makes scaling easier.

The most common approach to adding database servers is to create a master-slave configuration. In this kind of setup, a single master can support a number of slaves. The master is the only server against which writes are performed. The changes are then synchronized to the slaves, which are used for the purposes of reading data. This setup is common and fairly easy to implement.

There are, however, several caveats that developers should be careful about. First, it takes effort to determine which server should be written to and which should be read from. Developers therefore should use a common API for this task. Additionally, developers should be careful to write their applications in such a way as to not rely on the database to instantaneously make the written data available to them; as slaves will take a small amount of time (usually unnoticeable) to receive the replicated data. If there is any kind of a lag in this, the data may be unavailable.

Both of these caveats require careful programming, but provide benefits during subsequent attempts to add database hardware. Once the initial work of adding a master-slave setup is accomplished, developers can freely add additional slaves to handle the load of reading from the database (which is typically the most common operation).

## Adding Web Servers

Sites that have reached the limits of what they can serve effectively using a single web server may find the need to add additional web servers, as well as a load balancer. Typically this happens after the need for additional database hardware becomes relevant, because most of the time it is not the code that is eating the majority of the processing time. Still, as sites grow, this need increases.

Adding web servers increases the challenges faced by a developer, for several reasons. First, they must identify a way to balance traffic coming into each web server, usually with a third machine known as a load balancer. This machine’s sole purpose is to divert traffic to a particular machine, and can be configured in a number of ways.

However, when implementing a load balancer, developers have to be careful, especially with local machine file system or memory operations. For example, if the web server also has a Memcached server on it that is storing sessions in memory, in a load balanced environment there is no guarantee that the user will be redirected back to that particular server on the next request. This also applies to file uploads and other activities that affect the memory or disk of the local machine; thus, it becomes increasingly important that developers use a CDN or other method for sharing common files across servers.

Adding web servers - especially a lot of them - increases the difficulty involved in deploying new code as well. Since it is possible that users can be directed to a different web server on each request, having only half updated at the time of a user’s request could result in them seeing very different code bases (or their session containing incorrect information for the particular environment). It is thus important to solve deployment issues right away.

Still, when adding web servers, there is a definite mark of accomplishment, as this means a site has grown to the point where additional resources are necessary. Unlike database servers, where it is common to have more than one, web servers are not always needed, and adding a second web server is a sure sign of progress for any website.

## The Benefits of Expanding Hardware

Adding hardware has some additional benefits. With more than one server, there is failover in the event that a particular system goes down. This redundancy is built in to the idea of adding additional hardware and so long as the master database server does not go down, the application can continue operating without a hitch.

When larger organizations add hardware, they may have the ability to specify the technical requirements of that hardware. Being able to require that hardware have certain technical specifications allows an organization to tailor their hardware purchases to their needs. For example, database servers should be equipped with large amounts of storage space and very fast disks, while Memcached servers will have large amounts of RAM and relatively little disk space. Web servers should be able to handle high numbers of concurrent connections and have processing power to serve many threads of the web server.

Tailoring the servers to their specific roles can improve the performance of each server in the completion of that task, which in turn helps reduce the need for additional machines (because each machine already in use is more efficient).

## The Drawbacks of Expanding Hardware

Adding hardware does present some significant challenges, and is not without drawbacks.

When adding web servers, the first reality is that the file system is no longer an adequate place to store things, from media (images, uploads, etc.) to caches. Because the file system may be different on each machine, and depending on the load balancing setup, a user may not end up on the same machine on each request; sessions are an obvious casualty and must be moved to a more stable medium, such as Memcached.

Additional hardware also increases maintenance costs and reduces the ease with which new products can be rolled out. Since they must be rolled out to multiple machines, the planning process gets longer, and since there are multiple machines to maintain, failed disks and necessary upgrades cost that much more.

Finally, adding additional hardware adds complexity to the process of developing the application. With the file system gone as a resource and the possibility that any one of several database servers might be serving requests, issues with concurrency, latency, slave lag, missing cache data, multiple user tabs on the same session and a whole host of other issues come into play; that are not issues on a single server, or on single web server plus database master setups. These issues are challenging, and add to the overall complexity of managing an application.
