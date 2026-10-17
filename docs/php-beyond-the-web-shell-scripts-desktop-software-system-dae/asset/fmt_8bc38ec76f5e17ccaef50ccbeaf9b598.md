
# Big Data Processing with PHP

Before we continue, let's clarify what we mean by `big` data. Hadoop and other MapReduce algorithms have an inherent overhead in the way they work. This means that they only start producing benefits (at least performance wise) the larger the dataset gets. Your mileage will vary depending on the algorithms you want to apply to your data, and the alternatives methods available, but typically your data set needs to be well into the Gb range before you will start seeing noticeable benefits, and significantly bigger before these may outweigh the engineering effort needed to implement MapReduce on your task.

If your data falls into this particular definition of “big data” then you can harness the power of Hadoop with PHP. While Hadoop is written in Java, it is language agnostic when writing the map and reduce jobs that drive the data processing. It also uses standard streams (`STDIN` and friends) for data interchange, which we’ve seen in earlier chapters are easy to handle natively in PHP. There is even a PHP framework to aid in writing those map and reduce jobs.

The following links should start you along the road of big data processing in PHP if you think that your dataset qualifies as “big”.

> **Further Reading**
> “MapReduce: Simplified Data Processing on Large Clusters” - the original google paper  
> [http://research.google.com/archive/mapreduce.html](http://research.google.com/archive/mapreduce.html)
> “What is MapReduce” - a very simple explanation of MapReduce  
> [http://www-01.ibm.com/software/data/infosphere/hadoop/mapreduce/](http://www-01.ibm.com/software/data/infosphere/hadoop/mapreduce/)
> “Using Hadoop and PHP” beginners tutorial by Jason Graves  
> [http://collaboradev.com/2010/12/10/using-hadoop-and-php/](http://collaboradev.com/2010/12/10/using-hadoop-and-php/)
> HadooPHP - PHP Hadoop framework  
> [https://github.com/dzuelke/HadooPHP](https://github.com/dzuelke/HadooPHP)
> “Big Data Analytics (with Hadoop and PHP)” presentation by David Zuelke  
> [https://speakerdeck.com/dzuelke/big-data-analytics-with-hadoop-and-php-dpc2013-2013-06-06](https://speakerdeck.com/dzuelke/big-data-analytics-with-hadoop-and-php-dpc2013-2013-06-06)
> Criticisms of MapReduce on Wikipedia  
> [http://en.wikipedia.org/wiki/MapReduce#Criticism](http://en.wikipedia.org/wiki/MapReduce#Criticism)

## 9.18 Data caching

At various points in this chapter (and elsewhere) we have mentioned that it is often good practice to cache data where possible. For the uninitiated, this simply means that when we generate some data (be it variables for use in our script, or text or other program output) that we may want to use again later, then instead of re-generating it each time we instead store it somewhere until we need it again.

It should be obvious as to how we can do this, you are likely to be familiar with creating variables, writing files to disk or database, and so on. However while caching data can speed up your programs, it can also come with its own set of problems, such as when to delete the cached data (cache invalidation), how to deal with cache priorities when disk space or memory runs low, how to share cached data between processes and even machines, and other things you (and I) likely haven’t even thought of.

> *“There are only two hard things in Computer Science : Naming things, cache invalidation and off-by-one errors”* - saying based on quote by Phil Karlton

While PHP can’t help us with the first and last of those, it can help us out a little when working with caches. The following information sources give some details of caching in PHP.

> **Further Reading**
> Using Memcached, the high-performance, distributed memory object generic caching system, with PHP  
> [http://www.php.net/manual/en/book.memcached.php](http://www.php.net/manual/en/book.memcached.php)
> Mysql query caching  
> [http://php.net/manual/en/mysqlnd-qc.quickstart.caching.php](http://php.net/manual/en/mysqlnd-qc.quickstart.caching.php)
> Using output buffering for simple caching  
> [http://www.theukwebdesigncompany.com/articles/php-caching.php](http://www.theukwebdesigncompany.com/articles/php-caching.php)
> See the section on “Virtual Files - tmpfs” in Chapter 7 of this book for accessing memory based disks  
> “More - The file system is slow” - by Kevin Schroeder, discusses file system performance and why OS caching may mean that using memory drives aren’t necessarily much better for cache uses etc.  
> [http://www.eschrade.com/page/more-on-the-file-system-is-slow/](http://www.eschrade.com/page/more-on-the-file-system-is-slow/)

## 9.19 Know thy functions

When profiling, you may find some sections of problematic code, often as little as one or two lines, which are running slowly, but for the life of you you can’t work out how to re-write them. It’s worth knowing that in PHP there are often multiple functions that do the same or similar things, but they are implemented in a different way and so can take (sometimes vastly) different times to achieve the same goal.

Below are two “cheat sheets” for this situation. The first is a web page (that you can also download to run on your own machine) that benchmarks groups of functions that perform similar tasks. This can let you see at a glance which alternative functions may be available and how they might perform. Do be aware that the performance of most functions depends on the code surrounding them, so always profile each one in the context of your own application!

The second link is a Q&A that attempts to list Big O times for many PHP functions. Again this can be used to estimate which function may perform better in your scenario. If you’re not familiar with Big O notation, it is a way to describe how the time (or resource) taken by an algorithm increases as the data input size increases. A link to the Wikipedia article on Big O notation is also given.

> **Further Reading**
> PHP benchmarking script, grouped by function performed  
> [http://maettig.com/code/php/php-performance-benchmarks.php](http://maettig.com/code/php/php-performance-benchmarks.php)
> Q&A listing Big O times for various functions  
> [http://stackoverflow.com/questions/2473989/list-of-big-o-for-php-functions](http://stackoverflow.com/questions/2473989/list-of-big-o-for-php-functions)
> Big O notation on Wikipedia  
> [http://en.wikipedia.org/wiki/Big_O_notation](http://en.wikipedia.org/wiki/Big_O_notation)
> An article that shows how using alternative functions in unusual ways can elicit performance gains  
> [http://www.puremango.co.uk/2010/06/fast-php-array_unique-for-removing-duplicates/](http://www.puremango.co.uk/2010/06/fast-php-array_unique-for-removing-duplicates/)
> An alternative benchmarking web page  
> [http://www.phpbench.com/](http://www.phpbench.com/)

## 9.20 Outsourcing code to other languages

When you really hit the limits of PHP performance, and more hardware is not an option, one strategy is to move resource heavy code out into better performing languages. There are two ways to do this, either by creating stand-alone programs that you “shell out” to (see chapter 5), or creating PHP extensions (which are generally faster to access than separate processes). If you’re going to do this, you’ll need to learn or leverage another language, so it’s a topic mostly beyond the scope of this book. The following links should give you a good idea of where to start.

> **Further Reading**
> “PHP at the Core: A Hackers Guide” on the official PHP documentation. Covers PHP internals with reference to writing extensions.  
> [http://www.php.net/manual/en/internals2.php](http://www.php.net/manual/en/internals2.php)
> “Extension Writing” on Zend Developer Zone - A good introduction to writing extensions
