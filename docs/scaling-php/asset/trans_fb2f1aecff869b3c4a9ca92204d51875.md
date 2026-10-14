
-   [我快速在一个 i2.8xlarge EC2 服务器上进行了基准测试，过程非常简单——我创建了一个空的 Laravel 应用（没有数据库），其中一页（/public）始终返回 `Cache-Control: public`，另一页（/private）则始终返回 `Cache-Control: private`。我运行了 `ab`（Apache Benchmark）并进行了 100,000 个请求的基准测试——以下是每秒请求数：

```
1 /public  - 24690 requests per second, 4ms per request
2 /private - 3253  requests per second, 30ms per request
```

这里的关键是——如果可能的话，跳过 PHP 并直接从 HTTP 缓存中提供文件要快得多。即使是最基础的 PHP 脚本，结果也已经非常明显，如果 PHP 代码执行更复杂的操作（比如多次访问数据库），差距会更大。不过，有时候如果数据太动态，根本无法实现。但对于那些适合这样做的页面——这可是巨大的收益。

| ![question](images/leanpub_question.png) || \*\*How is the fastcgi cache stored on disk?The cached responses that the nginx fastcgi cache saves are stored on disk and can be easily manipulated. The output of the response from PHP-FPM is captured and stored in `fastcgi_cache_path` (`/tmp/cache` in our example). The filename is predictable and derived from the derived cache key of the request. For instance, for a `GET` request to `https://domain.com/index.html`, the derived cache key is `httpsGETdomain.com/index.html`. The response body will be stored in a file that is named `md5(httpsGETdomain.com/index.html)`, or `d5c94ba8b944742f64c115fa8c8e65ea`.The cache files aren’t just stored at the base of `/tmp/cache`, though. Nginx uses a two level folder structure to avoid having millions of files in a single directory which is bad for performance. The last three characters of the filename are used to build the folder structure, so for the example request above, the response body will be stored in `/tmp/cache/a/5e/d5c94ba8b944742f64c115fa8c8e65ea`. Why is this useful? If you delete this file, it will remove it from the fastcgi cache and force nginx to re-pull the page next time it’s requested. |

| --- | --- |

## Case Study: CakePHP Framework Caching

This is going to be a really awesome case study— I’m really pumped about it because it’s an interesting problem that not only took an incredible amount of blood, sweat, and tears to solve, but is also extremely applicable to the theme of this book because it’s something that could *only* be replicated at scale.

So first things first, I’ll set the stage with the some background and context and walk you through how I debugged, found the core issue, failed at solving it several times, and finally found the perfect solution.

### CakePHP, you devilish dessert

One of our several backend applications that I work on at [Life360](http://www.life360.com) is written in CakePHP. While I don’t think CakePHP is awesome, it gets the job done well enough and is fairly easy to work with.

CakePHP is a *large* framework. It handles everything from autoloading your PHP files for you, to introspecting your database models and learning about the different columns, to providing a faux query cache to cut down on the number of `SELECT` queries you make to MySQL. Typical framework stuff.

Without some type of cache to remember all of this information about your code between requests, Cake would have to regenerate it for each pageload, adding a significant amount of overhead. In order to remember the data, Cake provides a pluggable system cache which can store this data using APC, flat files, Memcache, or MySQL.

While the exact mechanics are specific to CakePHP, the problem itself is generic— almost every substantial PHP and non-PHP framework does something similar, persisting framework and system cache data somewhere.

#### APC gets removed from PHP 5.4 (aka, “the core problem”)

Our CakePHP framework cache was configured to use PHP’s APC cache. APC works great for this type of workload because it’s extremely fast and the data doesn’t need to be shared between multiple servers. Sadly, APC has been removed in PHP 5.5 in favor of supporting the much more advanced (and now, open-source) Zend OpCache.

Remember that APC provides two different functions to PHP— it provides a userland cache, similar to Memcache, which is how our CakePHP framework cache is using it, but its primary function is to cache compiled PHP bytecode, allowing our code *execute* faster. The faux-memcache functionality is a secondary feature to its primary role as a bytecode cache.

Zend OpCache is better than APC— it benchmarks faster and is all around more modern. Hands down, it makes a ton of sense and it’s why it has become the standard for PHP 5.5. Zend OpCache does one thing and does it well— it **only** does bytecode caching and doesn’t offer a comparable userland cache like APC.

The reason I mention this is because when upgrading from PHP 5.4 to 5.5, we could no longer use APC for our CakePHP system cache. At first glance, it doesn’t seem like it’s that much data and it’s not like it changes very much, so we just modified our configuration and told CakePHP to store its system cache data in flat files instead of APC— easy enough, right?

This worked seemingly well. No problems, it worked well at scale (400 million requests per day), everything was seemingly great. Little did I know, this small change would cause me to pull my hair out for months.

### The life and death of a CakePHP request

Let’s briefly run through how a PHP request is dispatched in CakePHP (or really, any MVC framework), and where the framework caching happens.

1.  Web request is sent from the browser to Nginx, Nginx sends the request to PHP-FPM

2.  PHP-FPM loads the bootstrap file of the framework, `index.php`

3.  Bootstrap file loads framework configuration, **reads the framework cache data from the filesystem (if it doesn’t exist, it has to regenerate it)**, and eventually invokes your controller.

4.  Your controller code runs and generates a response for the client.

5.  The framework **saves the newest system cache data to the filesystem** and sends your response upstream to nginx and eventually the browser.

There are two points at which the framework needs the cache data— at the beginning and end of the request. If the data doesn’t exist, it has to regenerate it (figure out which classes map to which files, figure out which columns are in which tables, etc). Simple enough.

### If it smells like a race condition…

So, with a fair understanding of how the cache works, what it accomplishes, and when it runs, let’s move on to discussing where things started to fall apart.

It’s typical Wednesday afternoon. We have some new code that we want to merge from our `development` branch to `master` and subsequently deploy to production. No big deal. Luckily, this is pretty automated and as soon as `master` gets updated, [`chef`](http://www.getchef.com/) kicks off, updates the production servers with the latest code and reloads PHP-FPM.

But here’s the weird part— when new code is deployed, we start seeing PHP-FPM processes pile up, quickly hit 100% CPU usage and spike server load to 80. We run out of free PHP-FPM children in no time, exceed the PHP-FPM backlog, and nginx starts throwing `502 Bad Gateway` HTTP responses. Bad news! And as quickly as it came, the problem would silently retreat and go away, never to be seen again until the next deploy.

It sort of became a ritual. Deploy new code, see a jump in errors, watch it mysteriously go away. It plagued me for months— no one wanted to deploy code, worried about causing brief downtime. We had a list of assumptions why this was happening (none of them were true), and it didn’t go away until I sat down for 4 days straight and tested each one.
