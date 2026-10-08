
### Search Engine Optimization and Indexing Best Practices

-   Search engines typically have between 10 and 20 billion web pages in their index. A database of this size takes a long time to build, so don’t be surprised if an amendment to your site doesn’t show up in Google for a few weeks.

-   Ensure that every page on your site has a page title. See page 53 for how to do this.

-   Make sure every page has a “description” and “keywords” meta-tag, as outlined on page 55.

-   Every page on the site should be reachable by at least one hyperlink, so that the search engine can follow the links in order to find all your pages.

-   Be aware that search engines are very poor when it comes to indexing information that is held in MySQL databases and which doesn’t exist as a static HTML page. The reason for this should be obvious. Google can’t access your MySQL database directly, but only through your website. So if you have a page which says “Please enter a name to search for”, the only way for Google to extract every name from the database would be to electronically “type” every possible name in the world into that box. So, in the case of database-driven sites, it’s especially important to also have a handful of “real” pages (ie, without a ? in the URL) that contain lots of relevant information about the site.

-   Google Sitemaps, often known as XML Sitemaps, are a way of helping Google and other search engines find their way around a web site in order to index it. If you have a site where the majority of content is generated dynamically from a database, rather than existing as static HTML files, it is well worth investigating these. Don’t get confused with standard site maps, as mentioned below, which consist of easy-to-read collections of links, which are designed to help human visitors navigate your site. An XML or Google Sitemap isn’t as easy to read, at least not by humans.

-   Offer a site map to your visitors, with links that point to the important parts of your site. Even if visitors don’t use it, search engines will. If the site map is larger than 100 or so links, you may want to break the site map into separate pages.

-   Don’t try to cheat. Some people include keywords that don’t accurately reflect the content of their pages. Or they use tricks such as white text on a white background to hide extra information within a page that Google will see but which is hidden from human visitors. When Google’s automatic systems detect this, your site will be removed from all of Google’s indexes and it’s very difficult to get reinstated.

-   Think about the words users would type to find your pages, and make sure that your site actually includes those words within it.

-   Use text instead of images to display important names, content, or links. The Google crawler doesn't recognize text contained in images. If you must use images (such as a logo, or a picture of a chart or graph) for textual content, also use the "alt" attribute to include a few words of descriptive text.

-   Make sure there are no broken HTML links in your pages.

-   Ensure that all pages validate correctly. There's more about this on page 56.

-   Ensure that every page specifies a DOCTYPE. There's more about this on page 60.

-   If you use a "keywords" meta-tag on a page, ensure that the page also mentions those keywords. Otherwise Google might assume that you're trying to cheat, by listing keywords that are actually nothing to do with the content of the page.

-   Ensure that HTML page filenames and image filenames are, where possible, relevant to the content of the site rather than just a meaningless name. For example, in a site about a hotel, a page called *vacant_rooms.html* which contains an image called *sample_room.jpg* is better than a file called *vr01.html* and an image called *samp.jpg*.

-   The more often you update your pages, the higher they'll be ranked by search engines. Google doesn't favour out-of-date sites.

-   Use proper hierarchical HTML tags in your pages, regardless of whether you generate the content from a database or you use static HTML files. This is known as using semantic markup, and you'll find out more by searching for the phrase in Google. Essentially, use the built-in h1, h2, h3 etc heading tags, correctly structured. So start with an h1 tag at the top of the page, then one or more h2 tags, and perhaps also some h3 headings within the h2 ones. Don't put, say, an h3 heading directly within h1 section. This all helps the search engine understand the structure of the page.

-   Google regards your page as especially important if there are lots of links to it from other sites. So encourage friends and business partners to link from their site to yours, perhaps in exchange for a link from your site to theirs.

## Keeping the Crawlers Away

Most of the time, you want to encourage Google and other search engines to crawl your site and add your content to their index. But sometimes there will be areas of your site that you would rather didn’t get indexed. For example, the folder or directory that holds unfinished pages that aren’t for public consumption.

There’s a way of telling search engines which folders to ignore, and it’s done through the use of a robots.txt file. This is a special text file that you need to place in the top-level folder of the publicly accessible part of your web site. In the case of hostmonster, that means the public_html folder. A typical robots.txt file, which you can create with any text editor such as Wordpad or PSpad (but not a word processor like Word), might look like this:

```
User-agent: *
Disallow /joomla/images
Disallow /hms
```

The first line is where you could, if you wanted, specify which search engines you wish to ban from your site. Chances are, you’ll want to block them all, which is what the line in the above example does. Then, just list all the folders you want to block, using Disallow commands. In this case, I’m blocking Joomla’s images folder and our HMS system.

Note that there’s no compulsion for search engines to obey the contents of a robots.txt file, but almost all of them do.

Regardless of whether you use a robots.txt file or not, don’t use a web server as a way of storing or exchanging private information. That’s not what they’re designed for. Even though you don’t include a link to your private file area from your public web pages, that doesn’t mean that Google won’t already have found the files and indexed them for the rest of the world to find. This happens a lot. Try a Google search for "private and confidential" or "commercial in confidence" for some worrying examples.

## If at First you Don’t Succeed, Pay

Each page of Google search results contains two sorts of information. In the image below, where I’ve used Google to search for a "cheap camera", the results at the very top, as well as those down the right hand side, are discretely labelled as Sponsored Links and shaded in a very pale yellow. I’ve made the yellow a little brighter, and highlighted the "sponsored links" text, to illustrate just how much of Google’s results are not as independent and merit-based as you might think.

This book is free of charge. To get the latest version, see www.the-web-book.com
Please do not make copies of the PDF file for others. All downloads must be from www.the-web-book.com
We can produce custom versions of this book for other web hosts. Email info@the-web-book.com for details.

![](img/50e1558b8202f19b96c1cc386ea5ec66_316_0.png)

So how do you sponsor a link, and get your page into those yellow boxes? All you need to do is pay. It’s a Google product called Adwords. You can read more about it on page 303.

To sign up with the web hosting company featured in this book, please visit www.the-web-book.com/hosts.html
It costs you just the same, but brings me a small commission that funds the development of this book. Thanks!

## The End. So, What Now?

Congratulations. That’s the end of this book, and you’ve managed to make it all the way through. So where do you go from here? Hopefully you’ll have followed some or all of the examples, and you’ll have one or more web sites that do much of what you set out to achieve. But a web developer’s work is never done, so there are probably more things that you’re aching to do.

Sadly, this book can’t cover everything about the subject. If you were to buy or borrow comprehensive books on everything we’ve covered here, such as HTML, CSS, Javascript, PHP, MySQL and web page design, it’s likely that your collection would run to 10,000 pages or more.

This book is being expanded all the time, however, so check back at **www.the-web-book.com** regularly to ensure that you’re always working from the latest revision. But if there’s more that you want to find out, then the web, and especially a search engine, should be your next stop. Whether you need to know about one specific PHP function, or general advice about how to make your CSS-based designs look better, everything you need to know is out there if you know how to search. And because PHP is such a popular choice for writing software, there are hundreds of web sites and helpful forums devoted to it. Whatever you want to do, chances are that someone’s already done much of the hard work for you and is willing to share the code.

In the future, I’m hoping to include some more advanced topics in The Web Book. These will include:

-   Ajax and DHTML
-   Database indexes
-   A login and authentication framework for building secure sites
-   MySQL table joins
-   PHP Sessions
-   Object-oriented PHP programming

The web is indeed a wonderful place. But you probably knew that already. I guess that’s why you started reading this book. I just hope you enjoyed it, and that you’ll tell your friends and colleagues to download their own copy too.
