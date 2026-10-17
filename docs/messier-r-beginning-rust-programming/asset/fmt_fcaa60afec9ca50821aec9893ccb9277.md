
We can certainly use style guides with Rust. In fact, there is a style guide already available for Rust, although it's not one of the Google style guides since Google apparently doesn't use Rust as one of its development languages. This may not be especially surprising, considering Google has a language that was developed by scientists at the company, including Ken Thompson, one of the people responsible for Unix and the C programming language (since he created the precursor language, B). Some of the Rust development team have created a style guide, stored on GitHub, defining how to write Rust programs. In some cases, they are simple visual style considerations like the number of blank lines in between statements (zero or one). Other cases, as shown in [Figure 10.2](#c10.xhtml#c10-fig-0002), suggest that any attributes belonging to a block of code should be on a line by themselves.

![FIGURE 10.2: Rust style guide](images/c10f002.png)

[**FIGURE 10.2**](#c10.xhtml#R_c10-fig-0002): Rust style guide

Much of the Rust style guide is about creating consistency in formatting the language. As mentioned before, this makes it easier to read and understand. It's been stated several times, but it's hard to overstate the value of writing readable and understandable code.

## HYPERTEXT TRANSFER PROTOCOL

The Hypertext Transfer Protocol (HTTP) was developed as a way to communicate hypertext documents. Hypertext itself is a concept that goes back to the 1960s, taking the idea of *hyper* from the Greek for “over” or “above.” Think about the idea of hyperspace or hypercubes, which aren't larger versions of space or cubes but, instead, space or cubes with more dimensions. The same is true of *hypertext*, which is a word coined by Ted Nelson in 1965. Take a text document and add some additional dimensions to it, and you have hypertext. Today, we are very used to hypertext documents, but in the 1960s, it was a revolutionary idea; and if you think about someone conceiving of a way to take a static document and be able to hop up and out of that document, it was an astounding way to look at the world.

In the late 1980s, the Internet was just taking its form out of a collection of semi-interconnected research and academic networks. This was in part because of the National Science Foundation (NSF), which created a high-speed network called the NSFNET based on 1.5 Mb per second data connections. This was significantly faster than the previous connection speeds, which may have been 56 Kb per second or even slower.

Up to that point, these wide area networks were used for research purposes so researchers could collaborate and share information. All of this is to say that there was a need for more efficient ways of sharing information. In the late 1980s, a team at the European Organization for Nuclear Research (CERN, after the French) started the WorldWideWeb project, which resulted in the creation of the Hypertext Markup Language (HTML) as a way to create text-based pages that included links to other documents. This page-formatting language offered a way for documents to be viewed easily before doing something with them. This was unlike the File Transfer Protocol (FTP), which allowed for moving files around but required the transfer to happen before opening the file in a local application. HTML allowed for the possibility of it happening all at once in a single application.

When the researchers at CERN created the markup language, they also needed a server application to serve up these pages, as well as the application that would talk to the server. This resulted in the creation of HTTP so the client application could send requests to the server and get documents returned from the server. The early version of HTTP only allowed for a single request type, `GET`. Only later versions began adding in other request types.

Like any other protocol, there is a grammar that has to be followed because the server expects requests to be well-formatted in order to understand the requests and fulfill them unambiguously. There are different versions of HTTP at this point, and each of them has different requirements when it comes to requests. We're going to skip the early versions of HTTP and start with HTTP version 1.0. A simple request in that version of HTTP looks like this:

This request is composed of three elements. The first element is the verb. This is the request type being made. We are making a `GET` request, which means we are requesting a document for retrieval. The second part of the request is the resource. In this context, the resource commonly refers to a page, which may include a relative path, meaning it's the path starting at the top of the directory tree the web server knows about. Finally, the last part of the request is the version of HTTP the request will be using. Different versions have different requirements. The reason for using version 1.0 is it's the simplest version to use when interacting with the server. The only elements of a request that are necessary are the ones indicated here. If you want to bump up to version 1.1, which is the version that was most widely used since the late 1990s, you need to add another line. Following is a request using version HTTP 1.1:

This doesn't change the request line, aside from the version number, but it does add an additional line. The reason is that in version 1.0, you could only serve up content for a single host on a single system. This is very inefficient, all things considered. I have a second domain or hostname I want to serve up content on, and I need a whole new server, which required a whole new piece of hardware in the 1990s because virtualization, especially application virtualization, wasn't anywhere near the thing it is today. It was possible to have multiple services serving up on separate IP addresses, but it was harder to do.

With HTTP 1.1, virtual servers became possible. All you needed to do was have multiple fully qualified domain names (FQDNs) point to one IP address and configure the web server to be able to point requests to a hostname at a directory where the content for that server was. [Figure 10.3](#c10.xhtml#c10-fig-0003) shows what that might look like. Out in front is the web server. If a request comes into `www.wubble.com`, the web server knows where in the filesystem the content for that server is located. The web server will then find the right file on disk and send it back to the client, based on what resource was requested.

`GET` is not the only request you can perform now that we have moved on from version 1.0. The following table includes the verbs that are commonly used in HTTP, as well as what they are used for:

![FIGURE 10.3: Web server directory tree](images/c10f003.png)

[**FIGURE 10.3**](#c10.xhtml#R_c10-fig-0003): Web server directory tree

**HTTP Verbs**

| VERB || FUNCTION |

| --- | --- |

|   ||  |

| --- | --- |

| GET || Retrieve a file from the server. |

| POST || Send data from the client to the server. |

| HEAD || Retrieve data without getting the data, only the headers. |

| OPTIONS || Retrieve the options available on the remote server. |

| TRACE || Follow the path within the server when parameters are sent. |
