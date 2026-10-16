
- Copying, Moving, and Deleting Files 220
- Browsing the File System 221
- Using PHP Streams 222
- Using Bzip2 Archives 224
- Returning Files with an HTTP Request 227

## 8 Working with MySQL Databases 229

- Connecting to MySQLi 231
- Sending SQL to MySQL 233
- Prepared Statements with MySQL 235
- Retrieving Results of a Query to MySQL 236
- Retrieving the Last Inserted ID 239
- Using Transactions 240

## 9 Working with Other Databases 243

- Connecting to SQLite 244
- Sending SQL to SQLite 246
- Retrieving Results of a Query to SQLite 248
- Using Prepared Statements with SQLite 250
- Connecting to PostgreSQL 252
- Sending SQL to PostgreSQL 253
- Updating Data in PostgreSQL 254
- Retrieving Results of a Query to PostgreSQL 255
- Connecting to Oracle 257
- Sending SQL to Oracle 258
- Retrieving Results of a Query to Oracle 260
- Connecting to MSSQL 262
- Sending SQL to MSSQL 264
- Retrieving Results of a Query to MSSQL 265
- Using Prepared Statements with MSSQL 266
- Using MSSQL without Windows 268
- Connecting to Firebird 270
- Sending SQL to Firebird 271
- Retrieving Results of a Query to Firebird 272
- Connecting via PDO 273
- Sending SQL via PDO 275
- Retrieving Results of a Query via PDO 276

## 10 Using XML 279

- Parsing XML with SAX 280
- Parsing XML with XMLReader 282
- Using DOM to Read XML 284
- Using DOM to Write XML 285
- Using XMLWriter to Write XML 287
- Using SimpleXML 288
- Using XPath with SimpleXML 289
- Transforming XML with XSL 290
- Validating XML 291

## 11 Communicating with Others 295

- Connecting with HTTP Servers 295
- Connecting with FTP Servers 298
- Checking Whether a Server Is Still Reacting 300
- Creating a Web Service with NuSOAP 304
- Automatically Generating WSDL with NuSOAP 306
- Consuming a Web Service with NuSOAP 308
- Creating a Web Service with the PHP 5 SOAP Extension 309
- Consuming a Web Service with the PHP 5 SOAP Extension 312
- Using Ajax 313
- Exchanging Data with the Server 316

## Index 321

## About the Author

Christian Wenz is a professional phrasemonger, author, trainer, and consultant with a focus on web technologies. He has written or cowritten more than one hundred books. He frequently contributes articles to renowned IT magazines and speaks at developer conferences around the globe. Christian contributes to several PHP libraries and frameworks and other open source software. He holds university degrees in computer sciences and in business informatics and lives and works in Munich, Germany. He also is one of the authors of Zend's PHP 5 and PHP 5.3 certifications.

## We Want to Hear from You!

As the reader of this book, you are our most important critic and commentator. We value your opinion and want to know what we're doing right, what we could do better, what areas you'd like to see us publish in, and any other words of wisdom you're willing to pass our way.

You can email or write directly to let us know what you did or didn't like about this book—as well as what we can do to make our books stronger.

*Please note that we cannot help you with technical problems related to the topic of this book, and that due to the high volume of mail we receive, we might not be able to reply to every message.*

When you write, please be sure to include this book's title and author as well as your name and contact information.

Email: feedback@developers-library.info
Mail: Reader Feedback
Addison-Wesley Developer's Library
800 East 96th Street
Indianapolis, IN 46240 USA

## Reader Services

Visit our Web site and register this book at informit.com/register for convenient access to any updates, downloads, or errata that might be available for this book.

## Introduction

Some time ago, my favorite development editor, Damon Jordan, sent me an email and closed it with “Ich möchte eine Föhnwelle,” which means “I’d like a blow wave.” Unfortunately, I didn’t know what either a Föhnwelle or a blow wave was, so I declined. He then told me he had found this sentence in a German phrasebook he recently bought.

I was interested and had a look at some German phrasebooks. I think they are great tools to get around in a foreign country, although I personally think that some of the phrases offered just don’t make sense. For instance, in one phrasebook, I found a series of pickup lines, including the ingenious “You have a beautiful personality,” something that didn’t work for me either in English, in German, or in any other language! Some local guidance could also result in other problems—you either have to remember all the things to say while you are at it, or you have to hold the phrasebook in your free hand. And, finally, “Blow waves are as dead as a pet rock,” just to use another phrase.

Anyway, we were discussing phrasebooks a bit, and Damon said that he wanted to do a book series on phrasebooks. He also mentioned that he would like to team up with his and my favorite acquisitions editor, Shelley Johnston, so I was in.

While working on a concept, we found some differences between a language phrasebook and an IT phrasebook. For instance, a language phrasebook just contrasts the same sentence in two languages.

However, this is not always helpful. What if you want to change the phrase a bit, for instance if you want an en vogue blow wave (an oxymoron, one might say)?

So, we tried to create a concept that contains a lot of phrases, but all of them with good explanations so that it is easy to change the code and adapt it to one's needs. This, of course, makes the "foreign language" portions of a phrase a bit longer than the phrase itself, but we think that really helps when working with the book.

I also remember one famous Monty Python sketch in which someone uses a sabotaged dictionary, so that asking for directions results in getting roughed up. Therefore, it is vitally important to get a real explanation on what is going on within the phrase.

I then wrote a series concept and a sample chapter, and now, only a few months later, you hold the first phrasebook in your hands (one of many, we hope).

Something I really hate about reading computer books is when code samples are hacked into the word processor but never tested. To avoid this, every listing is also available for download at http://php.phrasebook.org: the filename is part of the listing's caption. So every code sample does exist as a file and has actually been tested, unlike in some other books. Of course, it's an illusion that this book is 100 percent error free, although we have taken several steps to come very close to that mark. Any errata, if known, will be posted to that site, too.

Another thing I really dislike with some books is that they tend to be very OS dependent, which is really unnecessary for PHP. Some books were obviously only tested under Windows, some others only under Linux, but it is possible to make code relatively platform independent. We have invested a lot of effort in testing the code from this book on many server platforms, including Linux, Windows, Mac OS X, and Solaris. Therefore, the screenshots in this book are also taken from those platforms, so you will find a healthy mixture of systems (and browsers). Ideology can be expressed with many phrases, but you won’t find any of them in this book. If something does run only on certain platforms (or PHP versions), it is noted in the text. Another phrase I promise you will not find in this book is anything that looks like foo, bar, baz, or any other proofs of very little imagination.

Of course, it is easy to find missing phrases in this book. PHP offers so much functionality that it is impossible to cover every aspect. Therefore, we had to select certain topics of interest—stuff that is relevant in a PHP programmer’s everyday work. If you think, however, that something has really been overlooked, please let me know (but do also nominate something that should then be removed from upcoming editions of this book to make room for the new phrases). I am looking forward to getting your feedback.

And now, to quote a phrasebook once more: “Bist du soweit? Da boxt der Papst.” That is, “Are you ready? It’s all happening there” (but literally, “There boxes the pope.”)

Your personal phrasemonger,

Christian Wenz
