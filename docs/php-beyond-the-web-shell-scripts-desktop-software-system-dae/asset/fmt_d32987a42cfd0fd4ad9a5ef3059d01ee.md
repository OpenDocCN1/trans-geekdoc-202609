
Internal memory leaks and resource persistence issues with PHP itself are sometimes harder to work around, but these days they are quite rare and it really is worth upgrading to a modern version where possible. The better resource usage and higher performance of modern versions also have the benefit of minimising the impact of inefficiencies in your own code.

### 9.23 Avoid micro and premature optimisations

Now that I’ve convinced you of the need to consider performance and instructed you on the finer arts of speed and resource management in PHP, I’m going to try and convince you to put it to the back of your mind, at least for now. It is easy to get caught up with performance and optimisation and let it affect your workflow and productivity. While it is generally positive to follow good practice and consider the performance of your code at all stages of development, premature optimisation is often just that - premature, and micro-optimisations are not usually worth the paper they are written on.

As your author I have an embarrassing confession to make. Having started programming in PHP many years ago, when the performance difference between using single and double quotes around a string was measurable in some contexts (or at least it was “common knowledge” that it was), I still find myself automatically considering what type of quote to use each time I type out a string, not for syntactical reasons but for performance reasons. That’s despite the fact that the performance difference between the two now-a-days is definitely extremely, extremely negligible. Old habits die hard though, and many of the micro-optimisations that you will find on the web fall into a similar category. Profile your code, and you will quite likely find that a single verbose database call will make the time saved by calling `isset()` dozens of time to check variables instead of falling back on `@` to simply suppress warnings look incredibly small (that’s not to say that there aren’t other good reasons to do that though!). Developer time in writing and thinking about micro-optimisations is typically much more expensive than the extra processor cycles used to execute un-optimised code.

Premature optimisation typically occurs when developers start thinking about how to scale their code, before they’ve got any of the code working and deployed. There is no point working out how to scale code that may never see the light of day because the project over-runs and isn’t delivered. Unless you are sure of the volume of customers/users/data you will be processing, its usually a better idea to get something up and running, as a proof of concept if nothing else, and then scale it when you know that it will be needed. Indeed, scaling methods vary considerably depending on exactly what your code needs to do, and often this is not finalised until you have something up and running. So even if you deliver on time, your scaling efforts may all be in the wrong direction compared to how your project ends up functioning.

“But, but, but…” you cry, your project is different. It may well be, you might be lucky enough to work on a large scale well funded project that has a known high performance requirement, or be developing a tool that is specifically geared towards high performance uses. Congratulations, you can ignore this section (if you’re even at the level where reading this book is useful!). For the rest of us, and this is the majority of PHP projects, concentrate on getting it working and deployed first. Keep performance in mind during development, but don’t let it interfere with your work flow too much. Most projects fail for reasons other than poor performance.

| ![information](Images/image00248.jpeg) || **Further Reading**“PHP: Require/Include vs Autoloader”. An example of an article that espouses an optimisation method that is definitely premature (if worth it ever). The article shows that you can save a *whole 6 milliseconds in total*, in a script that runs the functions *100 times*. That’s not even worth thinking about for most people, who would only call it a hand-full of times at most, and in any case for whom 6 milliseconds isn’t a concern in the slightest.  

[http://www.endyourif.com/php-requireinclude-vs-autoloader/](http://www.endyourif.com/php-requireinclude-vs-autoloader/) |

| --- | --- |

## 10 Distribution and deployment issues

Now you’ve written your perfect piece of software, your audience eagerly awaits it’s delivery and installation onto their precious machines. Distributing and deploying software comes with its own set of headaches above and beyond those you encountered just writing the damn thing. This chapter covers some of the issues that you may come across when thinking about deployment and distribution of your software, that may vary from the common situation of pushing code to your own server for a PHP website. In particular, we are looking at scenarios where you distribute your software and it is no longer under your direct control and not on your own systems.

### 10.1 Error handling and logging

You will need to think about how you handle and log errors (and other information) in your scripts when you run with the `CLI SAPI`. You can use the normal PHP error handling functions and allow PHP to log errors to the file specified in `error_log` in `php.ini`. However bear in mind that you may not be able to control which user your software is run under, and so you need to log to an appropriate location where you can be sure your user has appropriate permissions to write to.

One alternative to the standard “log to a file” method in PHP is to instead send errors and other log information to the system’s `syslog`. In Linux systems this is `syslog(3)` (`man syslog` gives more information), in Windows this is the system `event log`. Using `syslog` has several advantages :

*   Virtually all users have permission to log to syslog (usually).

*   You don’t need to manage log rotation or truncation, concurrent accesses/file locking and other routine tasks.

*   There is a wide eco-system of tools for exploring and interacting with syslog

*   For system daemons and other critical software, system administrators will often expect to find (at least important) logging/error information in the syslog.

*   On systems designed to be scalable, syslog is often redirected to a central logging server/system. Writing your logs to syslog means that your software can scale to centrally managed log servers without any changes to your code.

To send your errors automatically to syslog, you simply need to set `error_log` in php.ini to the special string `syslog` rather than a filename. You can also set this from within your script using `ini_set('error_log', 'syslog')`. To log information other than PHP’s own errors, or if you’ve chosen to handle PHP errors internally and need to subsequently log them manually, you can use the `syslog()` function. `syslog()` takes two parameters, a priority level, and the message to be logged. The priority levels range from `LOG_DEBUG` for debugging messages at the lowest level up to `LOG_EMERG` to describe errors where the system is rendered unusable. The second parameter is a string with the message to log. Before you can call `syslog()`, you need to use `openlog()` to open a connection to the syslog first. The following is a brief example :
