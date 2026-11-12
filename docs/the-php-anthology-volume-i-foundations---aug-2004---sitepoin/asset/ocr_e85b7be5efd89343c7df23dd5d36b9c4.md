the types of problems you’ll typically encounter in your applications; they make it easier to perform operations such as ordering a list or comparing two dates, for example. As a PHP developer, there are essentially two types of timestamp you’re likely run into—the Unix timestamp and the MySQL timestamp.

# Unix Timestamps

Unix timestamps are generally the most effective way to handle dates—they’re a simple solution to a tricky problem. A Unix timestamp reflects the number of seconds that have passed since January 1, 1970, 00:00:00 GMT. Converting dates to their Unix timestamps makes date- and time-related calculations easy.

The downside of Unix timestamps is that unless you’re a child prodigy they’re not human-readable; if I told you that 1047994036 was the number of seconds that had passed since January 1, 1970, could you tell me what the date was?

The other problem with Unix timestamps is that they can only be used within a limited date range, depending on your operating system. On Linux-based systems, you should be able to go back to somewhere around 1902, and forward as far as 2037. On Windows-based operating systems, the lower limit may be as recent as January 1, 1970. The problem lies in the size of the number. Any operating system can easily handle integer numbers up to a certain size (2^32, or 4,294,967,296 for current 32-bit operating systems), after which it must work harder to juggle oversized numbers. For the sake of efficiency, therefore, operating systems usually impose this “maximum” size on important values like dates and times. Linux at least allows you to have negative integer values for dates, hence you can work with dates occurring before January 1, 1970, while PHP on Windows may complain about such dates. What I’m saying here is that there’s potentially another Y2K-like problem looming somewhere around January 19, 2038, which will affect all 32-bit operating systems still in existence. Try searching Google for that date and you’ll see what I mean...

Although 2038 is a long way off and the timestamp issue may influence no more than your choice of pacemaker, it’s worth bearing in mind if you’re planning an application that will need to work with dates from the distant past or future (perhaps on a history Website). PHP provides functions such as time and mktime to help deal with Unix timestamps. To see the problem in action, try running the following script on as many different operating systems as you can:

```
<?php
echo '1st Jan 1899: ' . mktime(0, 0, 0, 1, 1, 1899) . '<br />';
```