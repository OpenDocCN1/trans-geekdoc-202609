Whatever technique you use for caching, there are potential pitfalls. When deploying new content, it may be frustrating for your content authors if the content is not visible for several hours until the cache has expired. Hence, you may need to provide a manual mechanism to “flush” or otherwise reset the cache to bring forward the visibility of new content. In addition, should you be using caching in a load-balanced environment with multiple servers, you must ensure that their caches are in sync at all times; otherwise, users may not receive a consistent reflection of content from request to request.

These pitfalls aside, caching provides an excellent way to maximize the power of your infrastructure. A good rule of thumb is if you don’t really need to run the PHP code, or you don’t really need to hit the database, then don’t.

# Content Generation

In a similar vein to caching, the concept of _content generation_ takes account of the fact that plain old Web servers are exceptionally good at serving up static content — that is, files read straight off the hard disk with absolutely no processing whatsoever.

In such a scenario, pages on your Web application are (wherever possible) generated in advance into static .html files and associated imagery. Consider the alternative: a complex PHP script that uses the database to dynamically build the page with each and every request. If that page isn’t changing much from hour to hour, it makes sense to generate it “offline” and save the results to disk. That way, users don’t have to wait while the page regenerates. A database can still be used, of course. The difference is that the database will be accessed only by the script that rebuilds the pages. User requests won’t go anywhere near the database — they’ll get static HTML.

This technique is used to great effect on the BBC news Web site, http://news.bbc.co.uk/, which gets hundreds of million hits a day. Almost everything you see is statically generated using PERL scripts — simple PERL CGI scripts used to provide dynamic functionality _only when it’s needed_. It’s not exactly high tech, but it certainly copes with the traffic, even during major world news events such as 9/11.

During your development cycle, you may encounter pages on your Web application that are “nearly static” — that is, they are consistent from request to request apart from some small, dynamic area. Maybe there is a news ticker on the bottom right-hand corner of the page, or there’s a small login lozenge stating “you’re not logged in” or “currently logged in as Ed,” or similar. That whole page could be generated statically were it not for that tiny dynamic area.

You have a couple of options here, should you wish to stick to your guns and go the code-generation route. The first is to use IFRAMEs or JavaScript. In such a scenario, the HTML sent to the client is identical, but the client is instructed to request a piece of JavaScript or a separate IFRAME that will always be dynamically generated. There is still server burden in generating these pieces of content, but it is far less than would be involved in generating the whole page. This does have implications for search engine visibility and accessibility, however, as search engines and screen readers are generally incapable of reading JavaScript and will usually ignore IFRAMES, assuming they are advertising.

The second option is to use server-side includes (SSIs), which is a simple “tag” in the generated HTML that tells the server when to bring in an external resource. Contrary to popular belief, it’s perfectly possible to use SSIs to bring in a piece of PHP to generate that dynamic segment. For example, consider how you would include a piece of HTML using SSIs as follows:

```
<!--#include virtual="header.html" -->
```