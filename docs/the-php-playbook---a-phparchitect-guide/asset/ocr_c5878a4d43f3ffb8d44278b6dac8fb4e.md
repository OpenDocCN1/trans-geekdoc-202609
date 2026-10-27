# Adding Database Servers

As web applications grow, the point where strain often becomes evident is in the database layer. This is for a number of reasons, including the fact that many web applications are heavily data-driven, meaning that they are heavy users of the database. Most of the time, the database is the first thing that has to be scaled.

In fact, it is always a good idea for a web application to have two database servers, which can preserve data from loss and help protect against downtime. It also helps developers determine the best way to write their applications for more than a single database server, which in turn makes scaling easier.

The most common approach to adding database servers is to create a master-slave configuration. In this kind of setup, a single master can support a number of slaves. The master is the only server against which writes are performed. The changes are then synchronized to the slaves, which are used for the purposes of reading data. This setup is common and fairly easy to implement.

There are, however, several caveats that developers should be careful about. First, it takes effort to determine which server should be written to and which should be read from. Developers therefore should use a common API for this task. Additionally, developers should be careful to write their applications in such a way as to not rely on the database to instantaneously make the written data available to them; as slaves will take a small amount of time (usually unnoticeable) to receive the replicated data. If there is any kind of a lag in this, the data may be unavailable.

Both of these caveats require careful programming, but provide benefits during subsequent attempts to add database hardware. Once the initial work of adding a master-slave setup is accomplished, developers can freely add additional slaves to handle the load of reading from the database (which is typically the most common operation).

# Adding Web Servers

Sites that have reached the limits of what they can serve effectively using a single web server may find the need to add additional web servers, as well as a load balancer. Typically this happens after the need for additional database hardware becomes relevant, because most of the time it is not the code that is eating the majority of the processing time. Still, as sites grow, this need increases.