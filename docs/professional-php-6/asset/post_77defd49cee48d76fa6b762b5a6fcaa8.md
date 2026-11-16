
## Part IV: Pushing PHP to Its Limits

You might assume (based on either educated guesses or data available elsewhere) that 40 percent of the site’s traffic is likely to occur on the weekend, and 60 percent during the week. This indicates a bias toward the weekend. You can, therefore, infer that your busiest day in terms of traffic is likely to be either a Saturday or a Sunday. If each will receive traffic in equal measure, you can assume that on a Saturday or Sunday your site will receive around 461,000 page impressions.

Over the course of a day, though, that traffic is unlikely to be constant. You could use a working theory that 60 percent of the daily traffic is likely to be between 3 P.M. and 6 P.M., since the Web site supports a daily television show that airs at 3 P.M. and finishes at 4 P.M. That means in that three-hour window, the site is likely to receive 60 percent of its daily page impressions, or 276,000 impressions.

You might further hypothesize that in the three-hour slot, 3 P.M. to 4 P.M. is likely to account for 20 percent of that block of peak traffic, 4 P.M. to 5 P.M. (the hour immediately after) 50 percent, and 5 P.M. to 6 P.M. the remaining 30 percent. Your peak hour is therefore 4 P.M. to 5 P.M., when you can expect around 138,000 page impressions.

Using calculus, you might assume that over that hour, the page impressions are likely to be distributed approximately according to the normal distribution, with a peak at five minutes past the hour. By plotting a graph showing a normal distribution, with a mean of five minutes, you can experiment with different values of standard deviation and Y scalar until you find a shape that “fits” your projected traffic. This is neatly illustrated in Figure 23-4.

![](img/a1b732997d9cb194dceec0570dc79710_613_0.png)

Figure 23-4: Traffic during peak hour

As a normal distribution, the gradient (dy/dx) of the curve will equal zero at the mean point, which has already been stipulated as being five minutes past the hour. Therefore, by calculating the y-value of the curve where x is equal to 5, the peak traffic per minute page impressions can be calculated: approximately 2,800 page impressions per minute. This is backed up by a quick visual check of the graph.

If a page impression consists of one HTTP request for the page, followed by around 20 for images, CSS, JavaScript, and other assets, with a total combined “weight” of 100 KB, you may, therefore, assume a peak transfer of 280,000 KB in that minute. This equates to 37 Mbps. In terms of HTTP requests, if each page impression consists of 21 HTTP requests, you’ll need to be able to handle a throughput of 980 HTTP requests per second.

### Chapter 23: Handling High Traffic and High Availability

In this exercise, therefore, you’ve been able to work out your “worst-case scenario” in terms of bandwidth and requests per second for your hypothetical Web site.

How you use this data is up to you. You could, for example, use your peak Mbps figure in the course of your contractual negotiations with your ISP — perhaps asking for a 10 Mbps connection with the ability to “burst” to 100 Mbps when needed without financial penalty.

You might also seek to ensure that your entire infrastructure is capable of handling the peak of 1,000 HTTP requests per second, perhaps using load-testing software such as LoadRunner to achieve this, or even rolling your own test scripts to simulate load.

Either way, you have used a simple mathematical exercise to take a commercial objective — page impressions per month — and map it to a real technical requirement. Sure, you’ve used assumptions to get there, but businesses use assumptions all the time. At least there’s some logic behind the infrastructure you’re specifying.

### Caching

PHP is fast and lightweight, and properly architected PHP applications run quickly with only fairly modest hardware behind them. Nonetheless, wherever you can save weight, you should, and page caching enables you to do just that, by executing code only when you really need to.

By using some variety of caching, each request to your Web application is inspected carefully, and, if possible, delivered to the client without executing the underlying code in full — indeed, sometimes not executing it at all. As a result, the burden on your application server — and perhaps on your database server — is decreased. This is achieved by caching output (that is, storing a copy of it) upon the first request.

Generally speaking, the requested URL, HTTP GET, and POST parameters, as well as cookies are inspected. The combination of the four provides a sort of “unique key.” Should an identical request (based on those four parameters) have been generated in the recent past, content will be retrieved from the cache and sent to the end user; if not, the code will be executed as normal, but the output captured and stored in the cache. The word “recent” is almost always defined using a cache expiry constant; something around the two-hour mark is common.

Caching can take place at many points. PHP itself can execute caching. You can easily rig up your code to inspect input parameters by serializing `$_POST`, `$_GET`, `$_COOKIE`, and `$_SERVER["REQUEST_URI"]` into a unique key using the `md5()` function. You can equally easily capture output buffer contents using `ob_get_contents()`. In so doing, you can use simple conditional statements to determine whether or not to proceed with the execution of your script, or whether to serve up content from the cache.

You can also cache at the point of access to the database. You could easily create a wrapper around PDO to, for example, inspect `SELECT` queries as they are made, and, if an identical query has been made in the past few hours, intercept the call to the database and instead return a cached response retrieved from memory or disk.

It’s also not uncommon to use dedicated caching code at the point of request, particularly when combined with load balancing. In such a scenario, the load-balancing appliance determines when to forward a user’s request to (one of) the Web server(s). It may simply serve up content from the cache, particularly in the case of HTTP `GET` requests.

Whatever technique you use for caching, there are potential pitfalls. When deploying new content, it may be frustrating for your content authors if the content is not visible for several hours until the cache has expired. Hence, you may need to provide a manual mechanism to “flush” or otherwise reset the cache to bring forward the visibility of new content. In addition, should you be using caching in a load-balanced environment with multiple servers, you must ensure that their caches are in sync at all times; otherwise, users may not receive a consistent reflection of content from request to request.

These pitfalls aside, caching provides an excellent way to maximize the power of your infrastructure. A good rule of thumb is if you don’t really need to run the PHP code, or you don’t really need to hit the database, then don’t.

### Content Generation

In a similar vein to caching, the concept of _content generation_ takes account of the fact that plain old Web servers are exceptionally good at serving up static content — that is, files read straight off the hard disk with absolutely no processing whatsoever.

In such a scenario, pages on your Web application are (wherever possible) generated in advance into static .html files and associated imagery. Consider the alternative: a complex PHP script that uses the database to dynamically build the page with each and every request. If that page isn’t changing much from hour to hour, it makes sense to generate it “offline” and save the results to disk. That way, users don’t have to wait while the page regenerates. A database can still be used, of course. The difference is that the database will be accessed only by the script that rebuilds the pages. User requests won’t go anywhere near the database — they’ll get static HTML.

This technique is used to great effect on the BBC news Web site, http://news.bbc.co.uk/, which gets hundreds of million hits a day. Almost everything you see is statically generated using PERL scripts — simple PERL CGI scripts used to provide dynamic functionality _only when it’s needed_. It’s not exactly high tech, but it certainly copes with the traffic, even during major world news events such as 9/11.

During your development cycle, you may encounter pages on your Web application that are “nearly static” — that is, they are consistent from request to request apart from some small, dynamic area. Maybe there is a news ticker on the bottom right-hand corner of the page, or there’s a small login lozenge stating “you’re not logged in” or “currently logged in as Ed,” or similar. That whole page could be generated statically were it not for that tiny dynamic area.

You have a couple of options here, should you wish to stick to your guns and go the code-generation route. The first is to use IFRAMEs or JavaScript. In such a scenario, the HTML sent to the client is identical, but the client is instructed to request a piece of JavaScript or a separate IFRAME that will always be dynamically generated. There is still server burden in generating these pieces of content, but it is far less than would be involved in generating the whole page. This does have implications for search engine visibility and accessibility, however, as search engines and screen readers are generally incapable of reading JavaScript and will usually ignore IFRAMES, assuming they are advertising.

The second option is to use server-side includes (SSIs), which is a simple “tag” in the generated HTML that tells the server when to bring in an external resource. Contrary to popular belief, it’s perfectly possible to use SSIs to bring in a piece of PHP to generate that dynamic segment. For example, consider how you would include a piece of HTML using SSIs as follows:

```
<!--#include virtual="header.html" -->
```
