
In Windows, the same approach applies — start a command prompt and use telnet in exactly the same manner.

To get real-world output, of course, you need to substitute the hostname and URL for real-world examples. Press Enter where you see a blank line, and enter spaces exactly as shown. You may find it easier to write it all out in Notepad and paste it into telnet.

Have a stopwatch handy when you do this. Observe where the delay lies, and infer as follows:

- A delay between pressing Enter and observing Trying 192.168.1.2 indicates a delay in resolving the IP address of the server against a name server. This is unusual. It could indicate unresponsive name servers, either those you are using yourself (typically those of your own ISP) or those serving the domain of the server in question (typically the ISP hosting the server). Why this unresponsiveness exists is outside the scope of this book, but you can at least reassure yourself PHP is not to blame. To a real-world user, this delay would be experienced only once, when first accessing the site, because most Web browsers (and, indeed, operating systems) cache the results of name server lookups.

- A delay between the Trying, ... line and the Connected line indicates that the server itself took a while to successfully respond to your requests to connect. A delay here is massively damaging, because a page with several images could easily consist of 20 or 30 HTTP requests. If each one has a delay attached, the page could appear dramatically sluggish even if script execution time is markedly quick. Unfortunately, the delay could exist in one of two places: Either in the network to/from the server, or in the server's capability to respond to connections in a timely manner. The latter could be caused by server load, which could in turn be caused by poorly optimized PHP (not necessarily this script) or other processes bringing the server to its knees. A quick check of memory and CPU utilization on the server can reveal the truth here. If it's the former, then troubleshooting it is outside the scope of this book. If it's the latter, then you should try to track down which script is causing the problem; and if it's PHP, apply the same methods shown here to that script.

- A delay between pressing Enter twice after having entered your HTTP request and seeing the HTML of your response almost certainly indicates poor performance at processing time. This can be validated and verified by adding watches in code.

Assuming that the delay can be traced to script processing time, you can now determine what in the script is causing the delay (or delays).

## Understanding the Anatomy of a PHP Request

Forgetting the wider edicts on good PHP architecture for just a moment, remember that PHP is a scripting language. Its scripts have a start, a middle, and an end, just like any scripting language. Indeed, at the most basic, simplified level, the pattern of execution of any PHP script looks something like the following:

- 1. For a request to index.php, open index.php and perform a lexical analysis of its contents (and the contents of any files included or required by index.php). This means interpreting $x = $y + 2 into something like this:

```
VARIABLE "x" EQUALS VARIABLE "y" PLUS 2
```

- 2. Next, parse the lexical representation of the string to create actual executable instructions. This includes ensuring that the variables $x and $y are valid, that the addition operator can be performed on $y and a constant integer, and then constructing the actual execution instructions, in the form of bytecode.

- 3. Pass the bytecode to the PHP virtual machine, and execute the instructions contained therein. This involves the following:

  - a. Read input parameters, be they GET, POST, or COOKIE.

  - b. Use those input parameters to make decisions, consulting external data sources in the process.

  - c. Produce output and send to Apache/IIS for transmission to the requesting client.

## Opcode Caching

One of the single biggest performance lags in a large PHP application (aside from those caused by bad application design) happens during the lexing/parsing step, which happens on every file included in the request, and is repeated for each request to that file(s), even though the source code hasn't changed. You can avoid having to repeat these two steps for each request, by using something called an operations code cache, or opcode cache, for short.

Opcode caching applications preserve the output of the parsing step, the actual instructions to the PHP VM, and save them, typically in memory, to be used on subsequent requests to the same source code files. In a large application containing thousands of lines of PHP code, this can boost performance quite dramatically. Moreover, in PHP 6, one of the best opcode caches is included with the distribution and is enabled (though not turned on) by default. Alternative PHP Cache (APC) has long been available through PECL as an optional (though highly recommended) PHP module. However, its utility, performance, configuration flexibility, and simplicity have promoted it to a first-class citizen in the PHP source code base, and it is now included with the PHP 6 source code.

To enable APC, set apc.enabled = 1 in your php.ini file. You will need to configure a few other parameters, such as how much memory should be allocated for the cache, what type of caching should be used, and any filters to exclude files from being cached. The available documentation on APC is reasonably good. A Google search should turn up a lot of useful material on how to properly configure APC. For the basic documentation, see www.php.net/manual/en/book.apc.php.

## Other Sources of Performance Problems

The remaining source of performance issues (once the lexing/parsing step has been eliminated, where possible) comes down to application design and systems engineering.

These delays will boil down to one of three things:

- Poor algorithms — Inefficient code resulting in high execution time

- Poor hardware — The code is not unreasonable, but the hardware it's running on is elderly or overworked.

- External bottlenecks — A database causing holdups

Hardware is rarely the problem. Except in extreme cases (such as intense usage of GD for graphics rendering, intense number crunching, or large reporting applications), the overhead imposed by PHP itself does not require significant system resources.

### Tracking Down the Bottleneck

There are straightforward steps to resolving each different variety of identifiable bottleneck, as discussed in the remainder of this appendix. However, your first task is to determine where the bottleneck can be found and into which of the three categories described previously it falls.

### Database Queries

The easiest offenders to track down are slow database queries. Almost all enterprise-class PHP applications depend on a database of some kind. This book has heavily advocated PostgreSQL, but many applications (particularly those you will encounter that are written by third parties) will make use of the more popular MySQL.

You must eliminate database bottlenecks before attempting to optimize code. Because most code is dependent on the database in some respect (even if only for the supply of data), looking at code before its data source is optimized is not time well spent.

The simplest way to determine whether database bottlenecks exist in a script is to temporarily adapt your database interaction code to add a timer method.

Consider the query method of your abstraction layer for PostgreSQL. By adding error log stamps before and after each query, you can show how long each query took and easily produce an analyzable log for your page. The following excerpt shows an example, demonstrating how you might measure the time taken to perform a query in the database abstraction layer by sandwiching the `execute query` statement as follows:

```php
$intTimeNow = microtime();
$q_handle = pg_exec($this->link_ident, $sql);
$intTimeTaken = microtime() - $intTimeNow;
error_log("DEBUG: QUERY: $sql\n");
error_log("DEBUG: TIME TAKEN: $intTimeTaken\n");
```

This will yield error log output similar to the following:

```
[Sun May 16 22:10:19 2004] [error] DEBUG: QUERY: SELECT id, logged_in, user_id FROM "user_sessions" WHERE session_id='98ce552be0a2ea6b6f69fbebcd14997c' AND user_agent='Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)' AND ip_address='192.168.4.3'
[Sun May 16 22:10:19 2004] [error] DEBUG: TIME TAKEN: 0.003752
```

Executing a typical PHP script with your database abstraction layer doctored as shown in the preceding example will then yield a series of `DEBUG: QUERY xx` and `DEBUG: TIME TAKEN` statements as shown.

The pattern of queries will be easier to analyze if you can ensure that no other warnings, error messages, or code-initiated debug statements are writing to the error log, and that the analysis of the time being taken by your query has exclusivity for now.
