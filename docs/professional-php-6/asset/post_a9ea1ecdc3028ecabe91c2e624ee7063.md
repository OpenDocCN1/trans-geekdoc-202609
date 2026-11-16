
IIS has come a long way in recent years. Early releases were blighted with security problems. Just as seriously, performance and resilience under load have been called into question in recent years. While these deficiencies now have been largely addressed, one fact still remains: A given level of traffic under IIS on Windows can only be supported with a beefier hardware infrastructure than that required with, perhaps, Apache on UNIX.

Looking elsewhere, certain specialist Web servers can play an important role:

- Squid (*www.squid-cache.org*/) provides front-end traffic management, caching, and load distribution.
- lighttpd and thttpd are “lightweight” Web servers designed for serving only static assets such as images, CSS stylesheets, and downloadable binaries.
- Kernel-level Web servers such as TUX and KHTTPD provide an even more lightweight solution to the same problem, building the Web-serving capability directly into the operating system itself.

As you’ll see later in this chapter, the choice of a Web server is often dependent on the choice of an overall network infrastructure. In a larger setup, multiple servers can often run different Web servers and even different operating systems, all chosen with the laudable goal of maximizing performance in mind.

## Application Server

The concept of an *application server* is something not usually familiar to PHP developers. Because most developers run PHP as part of the Web server (be it as a module, compiled in, or, rarely, as a CGI module), the Web server and application server are perceived to be the same thing.

This is, of course, not the case. An application server runs applications; a Web server serves Web pages. The metaphor is aptly expressed in Java 2 Enterprise Edition (J2EE). An application server such as Tomcat, JBoss, or BEA/Weblogic may well accept requests over HTTP, but it’s likely to be coupled with a Web server on the front end trafficking requests through to it. Application servers generally support advanced features not found in a Web server (such as resource pooling, diagnostics, and support for advanced deployment techniques). As such, they are rightly considered “overkill” for serving up simple Web pages and other assets.

In the context of PHP, the phrase “application server” refers to the server that handles requests directly into the PHP engine. For optimum performance, this is typically Apache with PHP statically “compiled in” (rather than loaded as a module) such that a single executable serves the application. As shown later in this chapter, the addition of a static assets server and a front-end caching server allows for the smarter distribution of traffic, with each server playing to its strengths.

## Database

As you might expect, the choice of underlying database has substantial performance implications in any high-traffic PHP application. It’s expected that the bulk of HTTP requests for application pages will invoke some sort of SQL query. As a result, the speed with which each HTTP request can be completed is entirely dependent on the speed with which those SQL queries can be executed, and, if appropriate, data returned.

Much has been made in this book of the fact that well-architected PHP applications are database agnostic, insomuch as abstraction layers such as PDO and SQL generation techniques like ORM provide for a great degree of portability. Indeed, at low traffic levels, there is little to choose between databases.

At high traffic levels, however, everything changes. Much is made of MySQL's performance at running `SELECT` queries, but with an appropriate use of caching and page generation, the benefit this brings is negated. Of far greater importance is the database's performance in undertaking those transactions that inherently cannot be cached or pre-generated — for example, actions such as user registration, searching, and Web 2.0 functionality (e.g., instant messaging and post commenting).

In addition, application scalability is generally dependent on the ability to “add more of” a particular component. The database is no exception. With your choice of RDBMS, how simple is it to move from a single database server to two, three, four, or more?

That simplicity is governed by two features: clustering and replication. **Clustering** enables multiple physical database servers to represent themselves as a single virtual database server to connecting devices, thus distributing load in the process. **Replication** enables all those database servers to hold identical data sets at all times, thus ensuring that whichever physical server is chosen for a given request, the data returned is identical.

Some RDBMSs are better suited to clustering and replication than others. While this book is a big advocate of **PostgreSQL**, it is fair to say that its support for clustering and replication is entirely reliant on third-party packages such as **Slony-I** and **Continuent uni/cluster** for PostgreSQL. **MySQL** is somewhat better, but even its much vaunted **MySQL Cluster** platform is heavily caveated for enterprise deployment.

By contrast, Microsoft’s SQL Server and **Oracle 11g** support extensive clustering and replication out of the box. For that reason, there is, sadly, a realistic expectation that for truly high-traffic applications it’s still necessary to get the checkbook out.

## Software Architecture

Finally, it’s worth considering a human factor — one that, unless given adequate attention, can easily undo all the good work from following best practice across all of the issues previously discussed.

It doesn’t matter how much money is spent on excellent server hardware, a first class ISP, carrier-grade network equipment, and so forth, if the application is written poorly. A bad application is deeply vulnerable to cracking under pressure.

In Chapter 13, you were introduced to the fundamentals of designing well-architected PHP applications — builds that will be reliable, secure, extensible, modular, and easy to maintain. But a well-architected application will (more often than not) cope better under pressure, simply because it stops developers from making the human errors that can lead to performance leaks.

Perhaps just as important, the modular nature of well-architected applications means that when performance bottlenecks *are* discovered, they are easier to track down, identify, and address.

## Impact Factors

Having considered the core components of any Web application, it’s important for you to understand the role each can play in producing adverse performance or poor availability at high levels of traffic.

Remember that non-availability doesn’t just mean an application will be completely inaccessible. It can also mean that some core piece of functionality is temporarily disabled. The metric defined at the beginning of this chapter settled on 99.75 percent availability, but that means 99.75 percent of the time all functionality is present and correct — not just some of it.

Similarly, availability matters not one jot if performance isn’t up to scratch. A number of factors manifest themselves as poor performance:

- Socket response time — This is the time taken between initiating a socket connection to the Web server and that connection being achieved, once local network conditions have been subtracted. A time of around 50 milliseconds (ms) is fine. With a local network latency of 20 ms, this means a connection being opened within 70 ms of that request being made.
- HTTP latency — This is the time taken between the client issuing its HTTP request (be it GET, POST, or something else) and the server starting to return data to the client, once network delays have been isolated. Anything more than 100 ms is poor. That is, having issued a command such as GET /index.php, the server should start to return data to the client (be it HTML or something else) within 100 ms.
- Transfer rate — This is the rate (in bits, bytes, or kilobytes per second) at which data transfer can be effected. With connections in the home easily reaching 8 Mbps as of this writing, it’s increasingly important that your infrastructure can support a decent transfer rate, especially on larger files such as the binary assets that frequently comprise Flash movies and video (around 2 Mbps at a minimum).

As a rule of thumb, therefore, if under high traffic your application can’t respond to socket connections in under 50 ms, respond to HTTP requests within 100 ms, or shift data at least 2 Mbps, then it’s not up to scratch.

With that in mind, what factors can impact availability under load?

## Server Load

Every server supporting your application is under load. As a rule, the more traffic, the more load. A Web server, application server, and database server will all suffer an increasing burden on their natural resources (memory, CPU, and disk) as traffic levels (in terms of page impressions) increase.

The capability of a computer to carry out more than one operation at a time (multitasking and threading, in technical terms) is something of a myth. Each CPU can only carry out one instruction at a time. Each hard disk can only read or write to one part of the disk at a time. But smoke and mirrors provided by hardware controllers and the operating system itself allow for the illusion of multitasking.

This illusion is, in fact, a simple round-robin. If two tasks are competing for CPU time, the CPU alternates between the two with each clock cycle, although not necessarily on a 50/50 basis. Disks and memory generally work the same way. Requests not currently being serviced are effectively held in a queue. As load increases, that queue gets bigger, and so does the wait to get to the front of the line.
