
- Chapters 3-7 cover specific PHP HTTP client libraries and their features, usage, and advantages and disadvantages of each.
- Chapter 8 goes into developing a custom client library and common concerns when using any library including prevention of throttling, access randomization, agent scheduling, and side effects of client-side scripts.
- Chapter 9 details use of the tidy extension for correcting issues with retrieved markup prior to using other extensions to analyze it.
- Chapters 10-12 review various XML extensions for PHP, compare and contrast the two classes of XML parsers, and provide a brief introduction to XPath.
- Chapter 13 is a study of CSS selectors, comparisons between them and XPath expressions, and information on available libraries for using them to query markup documents.
- Chapter 14 explores regular expressions using the PCRE extension, which can be useful in validating scraped data to ensure the stability of the web scraping application.
- Chapter 15 outlines several general high-level strategies and best practices for designing and developing your web scraping applications.

## Chapter 2

### HTTP

The first task that a web scraping application must be capable of performing is the retrieval of documents containing the information to be extracted. If you have used a web browser without becoming aware of all that it does “under the hood” to render a page for your viewing pleasure, this may sound trivial to you. However, the complexity of a web scraping application is generally proportional to the complexity of the application it targets for retrieving and extracting data.

For targets consisting of multiple pages or requiring retention of session or authentication information, some level of reverse-engineering is often required to develop a corresponding web scraping application. Like a complex mathematics problem with a very simple answer, the development of web scraping applications can sometimes involve more analysis of the target than work to implement a script capable of retrieving and extracting data from it.

This sort of reconnaissance requires a decent working knowledge of the **HyperText Transfer Protocol** or **HTTP**, the protocol that powers the internet. The majority of this chapter will focus on familiarization with that protocol. The end goal is that you become capable of performing the necessary research to learn how a target application works such that you are capable of writing an application to extract the data you want.

### Requests

The HTTP protocol is intended to give two parties a common method of communication: **web clients** and **web servers**. Clients are programs or scripts that send requests to servers. Examples of clients include web browsers, such as Internet Explorer and Mozilla Firefox, and crawlers, like those used by Yahoo! and Google to expand their search engine offerings. Servers are programs that run indefinitely and do nothing but receive and send responses to client requests. Popular examples include Microsoft IIS and the Apache HTTP Server.

You must be familiar enough with the anatomy and nuances of HTTP requests and responses to do two things. First, you must be able to configure and use your preferred client to view requests and responses that pass between it and the server hosting the target application as you access it. This is essential to developing your web scraping application without expending an excessive amount of time and energy on your part.

Second, you must be able to use most of the features offered by a PHP HTTP client library. Ideally, you would know HTTP and PHP well enough to build your own client library or fix issues with an existing one if necessary. In principle, however, you should resort to finding and using an adequate existing library first and constructing one that is reusable as a last resort. We will examine some of these libraries in the next few chapters.

### Supplemental References

This book will cover HTTP in sufficient depth as it relates to web scraping, but should not in any respect be considered a comprehensive guide on the subject. Here are a few recommended references to supplement the material covered in this book.

- RFC 2616 HyperText Transfer Protocol – HTTP/1.1 (http://www.ietf.org/rfc/rfc2616.txt)
- RFC 3986 Uniform Resource Identifiers (URI): Generic Syntax (http://www.ietf.org/rfc/rfc3986.txt)
- "HTTP: The Definitive Guide" (ISBN 1565925092)
- “HTTP Pocket Reference: HyperText Transfer Protocol” (ISBN 1565928628)
- “HTTP Developer's Handbook” (ISBN 0672324547)
- Ben Ramsey's blog series on HTTP (http://benramsey.com/http-status-codes)

### GET Requests

Let’s start with a very simple HTTP request, one to retrieve the main landing page of the Wikipedia web site in English.

```
GET /wiki/Main_Page HTTP/1.1
Host: en.wikipedia.org
```

The individual components of this request are as follows.

- **GET** is the **method or operation**. Think of it as a verb in a sentence, an action that you want to perform on something. Other examples of methods include POST and HEAD. These will be covered in more detail later in the chapter.
- **/wiki/Main_Page** is the **Uniform Resource Identifier** or **URI**. It provides a unique point of reference for the **resource**, the object or target of the operation.
- **HTTP/1.1** specifies the **HTTP protocol version** in use by the client, which will be detailed further a little later in this chapter.
- The method, URL, and HTTP version collectively make up the **request line**, which ends with a <CR><LF> (carriage return-line feed) sequence, which corresponds to ASCII characters 13 and 10 or Unicode characters U+000D and U+000A respectively. (See RFC 2616 Section 2.2 for more information.)
- A single **header** Host and its associated value en.wikipedia.org follow the request line. More header-value pairs may follow.
- Based on the resource, the value of the Host header, and the protocol in use (HTTP, as opposed to HTTPS or HTTP over SSL), http://en.wikipedia.org/wiki/Main_Page is the resulting full URL of the requested resource.

### URI vs URL

URI is sometimes used interchangeably with URL, which frequently leads to confusion about the exact nature of either. A URI is used to uniquely identify a resource, indicate how to locate a resource, or both. URL is the subset of URI that does both (as opposed to either) and is what makes them usable by humans. After all, what's the use of being able to identify a resource if you can't access it! See sections 1.1.3 and 1.2.2 of RFC 3986 for more information.

GET is by far the most commonly used operation in the HTTP protocol. According to the HTTP specification, the intent of GET is to request a representation of a resource, essentially to "read" it as you would a file on a file system. Common examples of formats for such representations include HTML and XML-based formats such as XHTML, RSS, and Atom.

In principle, GET should not modify any existing data exposed by the application. For this reason, it is considered to be what is called a **safe operation**. It is worth noting that as you examine your target applications, you may encounter situations where GET operations are used incorrectly to modify data rather than simply returning it. This indicates poor application design and should be avoided when developing your own applications.

### Anatomy of a URL

If you aren't already familiar with all the components of a URL, this will likely be useful in later chapters.

```
http://user:pass@www.domain.com:8080/path/to/file.ext?query=$var=value#anchor
```

- http is the protocol used to interact with the resource. Another example is https, which is equivalent to http on a connection using an SSL certificate for encryption.
- user:pass@ is an optional component used to instruct the client that Basic HTTP authentication is required to access the resource and that user and pass
