
Note that it will write one file for each PHP request / process that is executed. So, for example, if you wish to analyze a form post, one profile will be written for the GET request to display the HTML form. The `XDEBUG_PROFILE` parameter will need to be passed into the subsequent POST request to analyze the second request which processes the form. Therefore when profiling it is sometimes easier to run `curl` to POST a form directly.

Once written the profile cache can be read by an application such as KCachegrind.

![](Image01653.jpg)

This will display information including:

![](Image01654.jpg)

*   Functions executed
*   Call time, both itself and inclusive of subsequent function calls
*   Number of times each function is called
*   Call graphs
*   Links to source code

Obviously performance tuning is very specific to each application's use cases. In general it's good to look for:

![](Image01655.jpg)

*   Repeated calls to the same function you wouldn't expect to see. For functions that process and query data these could be prime opportunities for your application to cache.
*   Slow-running functions. Where is the application spending most of its time? the best payoff in performance tuning is focusing on those parts of the application which consume the most time.

**Note**: Xdebug, and in particular its profiling features, are very resource intensive and slow down PHP execution. It is recommended to not run these in a production server environment.

## Section 97.2: Memory Usage

| php | | . | ini |
| --- | --- | --- | --- |

PHP's runtime memory limit is set through the INI directive `memory_limit`. This setting prevents any single execution of PHP from using up too much memory, exhausting it for other scripts and system software. The memory limit defaults to 128M and can be changed in the `php.ini` file or at runtime. It can be set to have no limit, but this is generally considered bad practice.

| `memory_get_usage` |
| --- |

The exact memory usage used during runtime can be determined by calling `memory_get_usage()`. It returns the number of bytes of memory allocated to the currently running script. As of PHP 5.2, it has one optional boolean parameter to get the total allocated system memory, as opposed to the memory that's actively being used by PHP.

![](Image01656.jpg)

| `memory_get_peak_usage` |
| --- |

Now `memory_get_usage` gives you memory usage at the moment it is run. Between calls to this function you may allocate and deallocate other things in memory. To get the maximum amount of memory used up to a certain point, call `memory_get_peak_usage()`.

![](Image01657.jpg)

Notice the value will only go up or stay constant.

## Section 97.3: Profiling with XHProf

[XHProf](https://github.com/phacility/xhprof) is a PHP profiler originally written by Facebook, to provide a more lightweight alternative to XDebug.

After installing the xhprof PHP module, profiling can be enabled / disabled from PHP code:

![](Image01658.jpg)

| `doSlowOperation` |
| --- |

The returned array will contain data about the number of calls, CPU time and memory usage of each function that has been accessed inside `doSlowOperation()`.

| `xhprof_sample_enable` | | `()` / | `xhprof_sample_disable` |
| --- | --- | --- | --- |

`xhprof_sample_enable()` can be used as a more lightweight option that will only log profiling information for a fraction of requests (and in a different format).

XHProf has some (mostly undocumented) helper functions to display the data ([see example](https://github.com/phacility/xhprof/blob/master/examples/sample.php)), or you can use other tools to visualize it (the platform.sh blog [has an example](https://platform.sh/2015/07/29/flamegraphs/)).

# Chapter 98: Multiprocessing

## Section 98.1: Multiprocessing using built-in fork functions

You can use built-in functions to run PHP processes as forks. This is the most simple way to achieve parallel work if you don't need your threads to talk to each other.

This allows you to put time intensive tasks (like uploading a file to another server or sending an email) to another thread so your script loads faster and can use multiple cores but be aware that this is not real multithreading and your main thread won't know what the children are up to.

Note that under Windows this will make another command prompt pop up for each fork you start.

**master.php**

![](Image01659.jpg)

**worker.php**

![](Image01660.jpg)

## Section 98.2: Creating child process using fork

PHP has built in function `pcntl_fork` for creating child process. `pcntl_fork` is same as fork in unix. It does not take in any parameters and returns integer which can be used to differentiate between parent and child process.

Consider the following code for explanation

![](Image01661.jpg)

As you can see `-1` is an error in fork and the child was not created. On creation of child, we have two processes running with separate PID.

| `pcntl_wait` | | `(` | `$status` |
| --- | --- | --- | --- |

Another consideration here is a zombie process or defunct process when parent process finishes before child process. To prevent a zombie children process simply add `pcntl_wait($status)` at the end of parent process. ![](Image01662.jpg) `pcntl_wait` suspends execution of parent process until the child process has exited.

It is also worth noting that zombie process can't be killed using SIGKILL signal.

## Section 98.3: Inter-Process Communication

Interprocess communication allows programmers to communicate between different processes. For example let us consider we need to write an PHP application that can run bash commands and print the output. We will be using `proc_open`, which will execute the command and return a resource that we can communicate with. The following code shows a basic implementation that runs `pwd` in bash from php

![](Image01663.jpg)

`proc_open` runs bash command with `$descriptor` as descriptor specifications. After that we use `is_resource` to validate the process. Once done we can start interacting with the child process using `$pipes` which is generated according to descriptor specifications.

After that we can simply use `fwrite` to write to stdin of child process. In this case `pwd` followed by carriage return.

Finally `stream_get_contents` is used to read stdout of child process.

![](Image01664.jpg) Always remember to close the child process by using `proc_close()` which will terminate the child and return the exit status code.

# Chapter 99: Multi Threading Extension

## Section 99.1: Getting Started

| `pthreads` - ext |
| --- |

To start with multi-threading, you would need the `pthreads` extension for php, which can be installed by

![](Image01665.jpg)

| php | . | ini |
| --- | --- | --- |

and adding the entry to `php.ini`.

A simple example:

![](Image01666.jpg)

## Section 99.2: Using Pools and Workers

![](Image01667.jpg) Pooling provides a higher level abstraction of the Worker functionality, including the management of references in the way required by pthreads. From: [http://php.net/manual/en/class.pool.php](http://php.net/manual/en/class.pool.php)

Pools and workers provide an higher level of control and ease of creating multi-threaded

![](Image01668.jpg)

![](Image01669.jpg)

# Chapter 100: Secure Remember Me

I have been searching on this topic for sometime till i found this post [https://stackoverflow.com/a/17266448/4535386](https://stackoverflow.com/a/17266448/4535386) from ircmaxell, I think it deserves more exposure.

## Section 100.1: “Keep Me Logged In” - the best approach

store the cookie with three parts.

![](Image01670.jpg)

Then, to validate:

![](Image01671.jpg)

# Chapter 101: Security

As the majority of websites run off PHP, application security is an important topic for PHP developers to protect their website, data, and clients. This topic covers best security practices in PHP as well as common vulnerabilities and weaknesses with example fixes in PHP.

## Section 101.1: PHP Version Leakage

By default, PHP will tell the world what version of PHP you are using, e.g.

![](Image01672.jpg)

To fix this you can either change `php.ini`:

![](Image01673.jpg)

Or change the header:
