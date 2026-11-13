
However, you can modify this setting by editing the `httpd.conf` file. You will find this configuration file in the `conf/` directory of your new Apache install.

Open this file in your favorite text editor or vi, if you are running a remote server, and modify the following block:

```
# Change this to Listen on specific IP addresses as shown below
# to prevent Apache from glomming onto all bound IP addresses
# (0.0.0.0)
#
#Listen 12.34.56.78:80
Listen 80
```

The majority of that block of code is a comment explaining what this parameter is responsible for. You can modify the port on which your development system can be found by changing this number to something similar to the following:

```
...
#
#Listen 12.34.56.78:80
**Listen 9004**
```

After you save and restart Apache, you can access this new install by visiting `http://localhost:9004`.

**NOTE** Applications on your machine use different ports, so it is best to check the port before choosing a new one.

## Working with bleeding-edge technology

When you have the new system installed, you can begin to experiment with new bleeding-edge technology without harming your live setup. Bleeding-edge software as shown in Figure 16.1 is newly released versions that have not been tested as much as stable releases would be. This allows you to work with more advanced and newer features, but also means you could run into bugs and development issues when using these versions. As you continue to test this new technology you can determine whether it should be used in a live environment and move it over when it is ready.

## Dependencies

Many libraries and tools that you will use on your Web server depend on other libraries. For example, PHP's GD library for image manipulation requires the libjpeg library in order to properly edit images.

When you update your server, you need to be aware of these dependencies because updating one portion can result in broken or incomplete installations. Oftentimes you will find information on the developer's site regarding specific update information or you can consult `php.net` in the comments section. There you will find other developers reporting their results in various development situations.

## FIGURE 16.1

An example of bleeding-edge releases from php.net

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_429_0.png)

## Caching and Optimizing

Keeping your server up to date is only one way to run an efficient server. In fact, there are much more important practices to follow first. One of these more important practices is optimizing your server-side code and the system it runs on. Not only should you follow best practices when developing your applications, you should also maintain your server to be optimized based on your specific needs.

## Optimizing PHP

Following the steps to optimizing your installation of PHP will allow you to run a better server overall. These optimization steps are fairly simple to follow and can easily be repeated as you work on more servers.

### Processor versus RAM

Unlike most applications that require more memory, PHP relies more heavily on the processor in your server. This means a dual-processor system is more efficient than a single processor with more memory. That does not mean memory is not important, because certain portions of PHP use a considerable amount of memory.

The output buffer and database plug-ins require more memory as they are accessed because they tend to store a majority of the information for quicker access next time. This means the first request is slow but requests following that are faster if you have enough memory to properly handle the requests to be stored.

This doesn't mean you should run out and immediately purchase more memory or even more processors because there are ways to optimize your server without spending any money on additional software or hardware.

### Ten tips for optimizing your code

The following is a list of ten tips to follow that will produce better performance in your code, as well as limit the strain on the Web server. They appear here in order from least important to most important.

- 1. Limit the amount of error handling your applications manage. Less error handling means better overall performance, unless you are experiencing bottlenecks already. Then error handling may be important.

- 2. Use the included functions; don't create your own. Whenever possible, try to use the provided functions in PHP because they are precompiled and are optimized to run more efficiently. They have also been tested over and over to ensure they work.

- 3. Use a select instead of multiple if/else statements. Not only will using a select produce cleaner code, it will also result in better performance when PHP executes that portion of your code.

- 4. Avoid myths like echo is faster than print. As with most programming languages, PHP has various myths, such as all code should be on one line. One of the most common myths is that echo is faster than print when sending code to the output buffer or screen. This is simply not true. You can use either statement. I personally prefer print because it is printing to the display or buffer.

- 5. Close database connections using functions such as mysql_close (for mysql) when not being used. Database connections end when the script completes, but this is not always the best way. For example, if you have a program that makes database calls and modifies these results, the database connection stays active (unless you close it) the entire time your script is working on the result set.

- 6. Use unset() to remove variables when they are no longer being used. Deleting variables, especially large arrays and objects when no longer in use, results in better performance overall.

- 7. Try to limit regular expressions and use standard string functions whenever possible. Regular expressions, while more robust, can consume a considerable amount of memory. Oftentimes you will find a simple string function (for example, `strstr`) produces the same result and with a significant performance increase in most cases.

- 8. Be smart about class usage. Simple tasks will suffer from unnecessary OOP code. You will find simpler tasks consume more memory when developed using OOP practices. It is important to not only know which techniques exist, but also when they should be used.

- 9. Monitor your applications to determine bottlenecks. Slowdowns in code performance can be traced back to one specific location, known as a bottleneck. Think of an actual bottle, where the neck slows down the flow of liquid as it groups to pass through the narrow top of the bottle. The same is true for code as most libraries and scripts have one point where they all meet.

A bottleneck in your application may exist in your code, but could also be in a database call or file system interaction. Monitoring your application will expose the issues and allow you to fix the performance problem.

- 10. Cache your PHP code, whenever possible.

After you optimize your code, but still need to improve more, caching may be an option. You can develop a custom solution or use an existing system, such as `memcached`, which is examined in the next section. You can also cache the actual PHP script by precompiling it, which speeds up subsequent requests.

PHP by default compiles your .php files every time they are requested. Caching avoids this by storing the precompiled code. This is much more efficient and means faster performance.

These ten tips are not the only ways to optimize your code, but provide a list of common slowdowns and myths when developing your applications. As you can now see, with a few code modifications and attention to how the Web server handles your scripts, you can ensure better performance while maintaining ultimate functionality.

I have seen some applications remove features when the program begins to expand, and this is simply the wrong approach. Removing features from a slow application is similar to throwing wild amounts of new hardware to solve a performance problem.

## Zend Optimizer

The Zend Optimizer is one product that is used to optimize and cache your code, but also provides a secure result because your code is compiled and encrypted. The encryption is achieved by running your source code through the Zend Guard, as shown in Figure 16.2, which obfuscates your open code.
