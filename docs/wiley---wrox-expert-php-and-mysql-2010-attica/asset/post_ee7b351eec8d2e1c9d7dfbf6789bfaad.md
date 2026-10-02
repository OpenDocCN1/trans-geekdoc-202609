
## 10

## Multi-tasking in PHP and MySQL

### WHAT'S IN THIS CHAPTER?

- Efficiently multi-tasking in PHP
- Using Gearman to multi-task and farm out work
- Seeing an application put Gearman and various other components discussed in this book together to build a search application

How many times have you developed a web application that has some functionality which requires running an external program or even forking a separate process? This is not something you generally like to do from your web application because you want to make it run as fast and efficiently as possible, yet you want to provide a lot of functionality for end users. Thus the problem arises of how to get a fast but full-featured application that can process as much as possible.

## GEARMAN

Many years ago (in the Internet time line) a web site, livejournal.com, was facing a similar dilemma. Users were uploading so many pictures to the web site that had to be processed into their respective accounts. This included resizing functionality such as creating thumbnails or reducing the raw image size to something more appropriate for the web site to display. These pictures mostly consisted of kittens — millions of pictures of kittens — overloading the web application that is Livejournal. Then the creative mind of Brad Fitzpatrick formulated a great idea to deal with this overload: have a server that spawns processes that do things such as processing pictures of kittens, outside of the web server application. Thus came the advent of Gearman.

### WHAT IS GEARMAN?

Gearman comprises a client component, one or more job servers that assign jobs requested by clients, and worker programs that register themselves for work and then carry out those job requests. It provides a distributed application framework. Gearman is used to farm out work to other machines in a distributed fashion, dispatching function calls to machines that are better suited to do work, to do work in parallel, to load balance many function calls, or to call functions between languages (as described on the project site). Gearman is multi-threaded and is known to be able to carry out 50 thousand jobs per-second. Hence, Gearman is the solution to splitting some functionality from your web application and handling it separately. Gearman is the ultimate tool for making this a reality. As Joe Stump from Digg put it:

> > “The way I like to think of Gearman is as a massively distributed, massively fault-tolerant fork mechanism.”

Some of the well-known sites using the C version of Gearman are:

- Digg: 45+ servers, 400 thousand jobs a day
- Yahoo: 120+ servers, 12 million jobs a day
- Livejournal, SixApart, DealNews, Xing.com, and others

Gearman was originally written in Perl, but the job servers and client API were recently rewritten in C by Eric Day because he wanted better performance. The process gearmand is the actual job server — it receives requests for jobs and then assigns them. The job server also keeps track of what workers are available and which ones have been tasked with jobs. It then handles the results from a worker, passing them back to the client that requested the job.

The basic Gearman setup consists of a client, a worker, and gearmand, the job server. The client creates a job request to send to the job server. The job server delegates the job to an appropriate worker and returns a response to the client when assigned. Workers, when started, register themselves for a particular kind of job, and when the job server receives a request for that type of job, it assigns the appropriate worker to it. Workers can do anything that you want them to do — fetch documents off the Web, cache data in memcached, stop and restart other servers — just about anything that you can code. A worker is somewhat a server and somewhat a client. The worker runs in a continual loop interestingly called work(), but has to connect to the job server to register itself and to await assignment to a job.

A worker can be run either synchronously or asynchronously, depending on what task you need done. For instance, think about the many web applications that you use to do something such as upload an image or leave a message. Often, you don’t need this task done immediately and in fact the web site will often have its application present a message that states “this thing you need done will happen eventually.” This concept is known as eventual consistency — which means that something will indeed happen, just not right away, and the ability to run Gearman workers asynchronously facilitates eventual consistency in your application.

If you think about it, many things in life are eventually consistent. For example, when you deposit money into your bank account at night by dropping a payment into the drop box, you get a receipt that you did this (a reply that the job was assigned!), but that deposited money doesn’t immediately go into your account, though the act of depositing the money has been initiated and you have some record for it. You accept this behavior because the money will eventually make its way into your account. You have a contract there that says “yes, we will get this money from the drop box to fund your account.” The same applies for checks eventually clearing and the actual monetary funds transferring from the payer’s to the payee’s bank account. So, too, you have a variety of particular, everyday actions on a dynamic web site where this eventually consistent behavior is considered satisfactory. Consider when you post a comment on your Facebook account. Sometimes your comment won’t immediately show up. Having your comment show up immediately is not a life or death situation so this behavior is sufficient.

Another application where Gearman is well suited is for map/reduce operations, a model of distributed computing over a large number of computers, or cluster, introduced by Google (see http://labs.google.com/papers/mapreduce.html). The idea is to take the large data set and break it up into smaller pieces and distribute each to worker nodes that process those pieces — this is the “map” stage. The “reduce” stage is to conglomerate the fractional results of the map stage and into one consistent result — think federation. As you can imagine, because Gearman enables you to farm out jobs to workers, it is well-suited for map/reduce.

> Although this book is about PHP, Gearman clients and workers can be written in other languages and for a number of environments and databases. There are language bindings and database bindings for PHP/C, Perl/C, MySQL (through UDFs), PostgreSQL, Java, JMS, Python/C, Twisted Python, OCaml, and many others.

A web environment utilizing Gearman is shown in Figure 10-1.

![](img/88e43d4c6a3d0e0d1f265975ce2f9f50_438_0.png)

FIGURE 10-1

Figure 10-1 shows the type of setup you might use for image resizing. Traditionally, the image resizing would have been implemented completely within the web application. The user would upload an image, and within the HTTP request to serve the page, the PHP code would have to run the image conversion — perhaps even using imagemagick — to perform the resizing. The page load would not be completed until the image resizing was completed. Now, with Gearman, the PHP web application can request image resizing by way of a Gearman client to the Gearman job server, gearmand, which would in turn tell a resize worker to perform the resizing operation. Now, the web application can return immediately with a message stating that the image is being processed and results will soon be provided, making the web application lighter weight than the traditional design. This changes the whole concept of how web applications can be written into distributed applications that work in concert instead of a single heavy-duty web application! With this in mind, you now have an application that has no single point of failure and offers a tremendous amount of flexibility.

## Installing and Running Gearman

Installing the latest version of Gearman is a very straightforward task. You can obtain the latest source on http://www.gearman.org/doku.php?id=download or visit https://launchpad.net/gearmand. These sites include links to every component you would need to run Gearman, the job server itself, and the Gearman MySQL UDFs.

### gearmand Job Server Install

To install the Gearman job server, follow these steps:

- **1.** Download the latest source distribution for gearmand into a directory where you usually compile source code such as `/usr/local/src` (you can also use the bazaar revision control system for the repository `lp:gearmand`). The first thing is to unpack the source distribution:
- **2.** Enter the gearmand source distribution directory:
- **3.** Now build and install gearmand:

```
tar xvfz gearmand-1.0.tar.gz
```

```
cd gearmand-1.0
./configure
```

```
make
make install
```

At this point, gearmand is installed and ready to use.

### PECL/Gearman

To install PECL/Gearman, consult the project page at http://pecl.php.net/package/gearman. The steps are essentially:

```
cd gearman-0.6.0/
phpize
./configure
make
sudo make install
```
