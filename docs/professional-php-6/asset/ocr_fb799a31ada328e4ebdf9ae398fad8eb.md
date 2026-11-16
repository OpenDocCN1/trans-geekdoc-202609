# Chapter 23: Handling High Traffic and High Availability

In this exercise, therefore, you’ve been able to work out your “worst-case scenario” in terms of
bandwidth and requests per second for your hypothetical Web site.

How you use this data is up to you. You could, for example, use your peak Mbps figure in the course of
your contractual negotiations with your ISP — perhaps asking for a 10 Mbps connection with the ability
to “burst” to 100 Mbps when needed without financial penalty.

You might also seek to ensure that your entire infrastructure is capable of handling the peak of 1,000
HTTP requests per second, perhaps using load-testing software such as LoadRunner to achieve this, or
even rolling your own test scripts to simulate load.

Either way, you have used a simple mathematical exercise to take a commercial objective — page
impressions per month — and map it to a real technical requirement. Sure, you’ve used assumptions to
get there, but businesses use assumptions all the time. At least there’s some logic behind the
infrastructure you’re specifying.

# Caching

PHP is fast and lightweight, and properly architected PHP applications run quickly with only fairly
modest hardware behind them. Nonetheless, wherever you can save weight, you should, and page
caching enables you to do just that, by executing code only when you really need to.

By using some variety of caching, each request to your Web application is inspected carefully, and, if
possible, delivered to the client without executing the underlying code in full — indeed, sometimes not
executing it at all. As a result, the burden on your application server — and perhaps on your database
server — is decreased. This is achieved by caching output (that is, storing a copy of it) upon the first request.

Generally speaking, the requested URL, HTTP GET, and POST parameters, as well as cookies are
inspected. The combination of the four provides a sort of “unique key.” Should an identical request
(based on those four parameters) have been generated in the recent past, content will be retrieved from
the cache and sent to the end user; if not, the code will be executed as normal, but the output captured
and stored in the cache. The word “recent” is almost always defined using a cache expiry constant;
something around the two-hour mark is common.

Caching can take place at many points. PHP itself can execute caching. You can easily rig up your code
to inspect input parameters by serializing `$_POST`, `$_GET`, `$_COOKIES`, and `$_SERVER [ "REQUEST_URI" ]`
into a unique key using the `md5()` function. You can equally easily capture output buffer contents using
`ob_get_contents()`. In so doing, you can use simple conditional statements to determine whether or
not to proceed with the execution of your script, or whether to serve up content from the cache.

You can also cache at the point of access to the database. You could easily create a wrapper around PDO
to, for example, inspect `SELECT` queries as they are made, and, if an identical query has been made in the
past few hours, intercept the call to the database and instead return a cached response retrieved from
memory or disk.

It’s also not uncommon to use dedicated caching code at the point of request, particularly when
combined with load balancing. In such a scenario, the load-balancing appliance determines when to
forward a user’s request to (one of) the Web server(s). It may simply serve up content from the cache,
particularly in the case of HTTP `GET` requests.