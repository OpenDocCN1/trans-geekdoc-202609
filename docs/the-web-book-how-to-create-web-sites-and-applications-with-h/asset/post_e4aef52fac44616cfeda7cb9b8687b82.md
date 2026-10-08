
+ Checkbox Arrays............................................................ 250
Feedback Forms............................................................. 252
Hidden Fields............................................................. 252

## Accessing MySQL Databases with PHP

+ Counting Rows...................................................... 257
Reading Data.................................................... 259
Searching A Table.............................................. 264
Preventing SQL Injection Attacks.............................. 269
Adding Data to a Table.......................................... 270
Editing a Data Record......................................... 276
Deleting Data.................................................. 284
Putting It All Together.......................................... 285

## Debugging and Global Variables

+ Syntax Errors...................................................... 287
Coding Errors.................................................... 288
The $_SERVER Variables............................................. 292

## Application Structure Revisited

+ Web Servers and the Real World................................. 296
Saving State.................................................... 297

## How to Back Up Your Web Site

+ Don't Forget the Data........................................... 298
Restoring Lost Information..................................... 300

## Promoting and Profiting

+ Promoting Your Site............................................ 302
Making Money................................................... 304
Accepting Online Payments...................................... 306
Managing your Marketing......................................... 308

## Search Engine Optimisation

+ SEO Tips........................................................... 313
Keeping the Crawlers Away....................................... 315
If at First You Don't Succeed, Pay................................. 316

## The End. So, What Now?

## Appendix A – Building a Test Server

+ Our Goal.......................................................... 319
First Install the OS............................................... 320
Some Useful Commands............................................ 321
Get Updated.................................................... 322
Test Your Web Server........................................... 323
Install the Telnet Server.......................................... 323
An FTP server................................................... 324
Webmin...................................................... 326
Webalizer.................................................... 327
PHP and MySQL................................................... 328

## About The Web Book

If you want to create web sites, there are hundreds of books and web pages that claim to show you how. Some of them are very good indeed. But this book isn't like all those other books and web pages, for a number of important reasons:

1. The Web Book is an electronic book, or e-book. You simply download it as a PDF file from www.the-web-book.com and print it yourself. Or read it on-screen.

2. The Web Book covers all of the technologies that you need to know in order to create Web sites, both using static HTML pages and database-driven sites.

3. Unlike many books on the subject that were written some years ago, The Web Book teaches you up-to-date methods. Follow the instructions here and you can be confident that you're doing things in the right way, rather than using old-fashioned techniques that are now frowned upon.

4. I've tried my hardest to keep everything non-technical. If you're "into" computers, you should be able to follow everything just fine. You certainly don't need to be a professional techie. In fact, if you are, you'll probably take offence at the way I've simplified some things. For which I apologise.

5. If you already look after a web site, perhaps for your school or college, or the department you work for, you may be itching to take your skills to the next level. Or maybe you didn't actually get much training when you took on the responsibility, and you don't really understand how everything fits together. In which case, this book is perfect for you. We don't just tell you to press buttons. We explain what those buttons do, and why you need to press (or not press!) them.

6. Here's the best bit. The Web Book is **free of charge**. So if you want to teach yourself how to do Web stuff, whether for creating your own sites or to make sites for other people, just grab a copy of the PDF file, print out the book, and away you go.

One word of warning, though. Creating a web site and doing it properly isn't a simple task that can be done in an afternoon. Yes, we've all seen 2-page magazine articles that imply otherwise, but sadly it's just not true. Even at 329 pages, this book is only a basic introduction to some of the more complex topics. It's quite possible to buy books on HTML, CSS, PHP and MySQL which each run to 800 pages. I wouldn't recommend it, however, unless you have trouble sleeping.

## Why We Recommend Hostmonster.com

If you want to create web sites, you need a company to host them for you. There are thousands of such companies out there. The examples in this book are based around one in particular, namely www.hostmonster.com. We chose this company because their products appear to be good, and they offer good value. They host the site from which you will have downloaded this book.

If you're looking for a web host, we'd love you to use hostmonster because, if you sign up via our web site at www.the-web-book.com, we get a small amount of commission. But the web is all about freedom of choice, so if you want to go elsewhere you're more than welcome to do so. You'll need to adapt the examples slightly, but details of any settings or concepts that are unique to hostmonster are clearly identified in the text.

If you're considering using a different host, check our web site first. There may be a custom edition of the book available for that host. We're working on new ones all the time.

## A Custom Edition For Your Company

If your company sells web hosting services and you wish to give away or sell copies of this e-book, we can create a custom version of the book for you, where all the examples feature your hosting. You can then point your customers at our web site to download their copy.

For information on this service, see www.the-web-book.com/customize.html or email info@the-web-book.com.

## Who's Written This Book? And Why?

The Web Book is written by Robert Schifreen, a UK-based journalist, writer and technical author. I have more than 25 years' experience of writing all sorts of technical articles for various computer magazines, and 9 years' experience developing web sites for myself and clients. I've also written a "traditional" book before, that was published in 2006 and was available as a real hardback in real bookshops. A Google search for "defeating the hacker" will find it for you.

Having taught web development to the 2,500 staff at a UK-based university for the past few years, I thought it might be helpful to turn my course into a book, which is loosely based on the stuff I teach and is also inspired by the questions that my students ask. From now on, when people ask me how to create a web site, or whether it's easy, I don't have to spend time explaining everything. I can just say "go to www.the-web-book.com and download my free book, which tells you everything you need to know".

To sign up with the web hosting company featured in this book, please visit www.the-web-book.com/hosts.html It costs you just the same, but brings me a small commission that funds the development of this book. Thanks!

This is the book which I really wish had existed when I started doing web stuff all those years ago. But, you're probably asking, why am I giving it away instead of selling it? There are 3 reasons.

One. I quite like the idea of being able to write what I want for a change, without having publishers and editors to answer to.

Two. I want as many people as possible to see this book, because I think it's useful. The trouble with traditional publishing is that, of the hard-earned money that you hand over to pay for a copy of a traditional book, most of it is swallowed up by the publishers and their marketing costs. The author, the guy who sat in front of his PC for months writing the thing, typically gets around 15% of your cash. Sometimes less. So I've decided to try something different. This book is free to download and use. It is financed in 3 ways:

- If you want to make a small donation via `www.the-web-book.com/donate.html` you're more than welcome.
- If you run a web hosting company and you would like me to produce a custom version of the book that features your hosting service, please see the page online at `www.the-web-book.com/customize.html` for details and pricing.
- If you want to sign up with a web host, I'd really appreciate you signing up with Hostmonster (who are featured in this edition of the book). Just click the Hostmonster icon on `www.the-web-book.com/download.php` and everything happens automatically. This brings me a small commission payment, which helps to pay for the 5 solid months it took me to write The Web Book. It won't cost you any more, but it means a lot to me.

And the third reason why I'm giving away the book? Having been a professional IT journalist, editor and writer since 1983, I've seen what the internet is doing to the publishers of magazines and books. Especially those companies which produce IT-related publications. Computer magazines across the world are being shut down and book sellers are having a hard time, because the Web, not the pages of a book, is undoubtedly the best place to find information about technical subjects.

In many cases, those publications shut down not because the product was poor, but because the publishers failed to see the internet coming and failed to act accordingly. Publishers need to work with the internet, not against it. Sure, a search engine means that I can find an answer to a technical problem instantly without having to plough through shelves of books and magazines. But the Web is also the greatest, biggest, best, cheapest and most efficient way of copying and disseminating information that's ever been invented. Just ask the music industry. So by promoting this book on the internet as a free download I hope that I can exploit the power of the internet rather than trying to work against it.
