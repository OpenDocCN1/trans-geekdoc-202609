# Chapter 6: PHP’s Built-in Functions

Probably the most common use of output buffering is to ensure you don't get errors by sending headers after text has been sent to the browser. Prevent this, you could start a buffer, write some of an HTML page to the buffer, and then,
given a specific condition, write a header (maybe a cookie), and then output the result of the page. When you flush the buffer, the contents will be written to the browser without error.

![](bbox=[0.181, 0.246, 0.253, 0.299])

If you are frequently using buffering to prevent headers from causing errors, rethink your page logic. Decisions first, output second.

People have also been playing with using output buffering to gzip page contents. Then, in browsers that are capable of unzipping, the page could be downloaded a lot faster. However browser craziness, we wouldn't recommend this.

# BUFFERING FUNCTIONS USED IN THE BOOK

There are quite few object buffering functions. We used very few of them.

OB_START() This starts the buffer.

```
void ob_start(void)
```

FLUSH() This clears the buffer.

```
void flush(void)
```

# BUFFERING FUNCTIONS NOT USED IN THE BOOK

Check the manual for some more sophisticated buffering functions.

# INFORMATION FUNCTIONS

These functions will give you information about the environment in which you are working.

PHPINFO() Your guide to all that is available in your PHP environment. Use it. Use it. Use it and then take it off your system. No point in letting crackers get a look at the specifics of your system.

PHPVERSION() Returns only the version of PHP you are using.