
## The architecture of a web application

The *World Wide Web*, or web, consists of many components that work together to bring a web page to your desktop over the *Internet*. Before you start PHP programming, you need to have a basic understanding of how these components interact and where PHP fits into this architecture.

### How a client-server architecture works

*Web applications* use a *client-server architecture*. This architecture consists of servers that share resources with clients over a *network*. Figure 1-1 shows the components of a simple client-server architecture.

A *server* can share resources such as files, printers, websites, databases, and e-mail. A *web server* is a server that shares websites, and a *web browser* is the client software used to access the web server.

A *network* is a communication system that allows clients and servers to communicate. A *Network Interface Card (NIC)* connects the computer to the network. This connection can either be wired or wireless. Ethernet is a common type of wired network. Wi-Fi is a common type of wireless network.

The network is responsible for getting information from one computer to another. This process is called routing. A *router* is a device that is connected to two or more networks. When information comes in from one network, the router determines which network is closest to the destination and sends the information out on that network.

Networks can be categorized by size. A *Local Area Network (LAN)* is a small network of computers that are near each other and can communicate with each other over short distances. Computers on a LAN are typically in the same building or in adjacent buildings. This type of network is often called an *intranet*, and it can be used to run web applications for use by employees only.

A *Wide Area Network (WAN)* consists of multiple LANs that have been connected together over long distances using routers. A WAN can be owned privately by one company or it can be shared by multiple companies.

An *Internet Service Provider (ISP)* is a company that owns a WAN that is connected to the Internet. An ISP leases access to its network to other companies that need to be connected to the Internet.

The Internet is a global network consisting of multiple WANs that have been connected together. ISPs connect their WANs together at large routers called *Internet Exchange Points (IXP)*. This allows anyone connected to the Internet to exchange information with anyone else.

This figure shows an example of data crossing the Internet. In the diagram, data is being sent from the client in the top left to the server in the bottom right. Here, the data leaves the client’s LAN and enters the WAN owned by the client’s ISP. Next, the data is routed through an IXP to the WAN owned by the server’s ISP. Then, it enters the server’s LAN and finally reaches the server. All of this can happen in less than 1/10th of a second.

### How static web pages are processed

A static web page is a web page that only changes when the web developer changes it. It is a plain text file that contains all the content to be displayed in the web browser. This web page is sent directly from the web server to the web browser when the browser requests it.

Figure 1-2 shows how a web server processes a request for a static web page. The process begins when a user requests a web page in a web browser. The user can either type in the address of the page into the browser’s address bar or click a link in the current page that specifies the next page to load.

In either case, the web browser builds a request for the web page and sends it to the web server. This request, known as an *HTTP request*, is formatted using the *HyperText Transfer Protocol (HTTP)*, which lets the web server know which file is being requested. In this figure, you can see the content of a simple HTTP request.

When the web server receives the HTTP request, it retrieves the requested web page from the disk drive and sends it back to the browser as an *HTTP response*. This response includes the *HTML (HyperText Markup Language)* for displaying the requested page. In this figure, you can see the HTTP response for a simple web page, which includes the HTML for the page.

When the browser receives the HTTP response, it uses the HTML to format the page and displays the page in the web browser. Then, the user can view the content. If the user requests another page, either by clicking a link or entering another web address in the browser’s address bar, the process begins again.

Incidentally, this process depends not only on the HTTP protocol but also on the *Transmission Control Protocol/Internet Protocol (TCP/IP)* suite of protocols. The protocols in TCP/IP let two computers communicate over the network.

### How dynamic web pages are processed

A *dynamic web page* is a page that’s created by a program or script that’s running on a server. This means that the page can be changed each time it is viewed.

The changes in the page can come from processing the form data that the user submits or by displaying data that’s retrieved from a *database server*. A database server stores information that’s organized in tables, and this information can be quickly retrieved by a database query.

Dynamic web pages enable web developers to create interactive web applications. As a result, users can purchase goods and services, search the web for information, and communicate with other users through forums, blogs, and social networking sites. Sites like these would be difficult or impossible to create without database-driven, dynamic web pages.

Figure 1-3 shows how a web server processes a dynamic web page with PHP. The process begins when the user requests a page in a web browser. The user can either enter the URL of the page in the browser’s address bar, click a link that specifies the dynamic page to load, or click a button that submits a form that contains the data that the dynamic page should process.

In each case, the web browser builds an HTTP request and sends it to the web server. If the user submits form data, that data will be included in the HTTP request.

When the web server receives the HTTP request, it looks up the file extension of the requested web page to determine which server or program should process the request. For a PHP page, the web server forwards the request to the *PHP interpreter*, which is running on the web server.

The PHP interpreter gets the appropriate PHP script from the hard drive. It also loads any form data that the user submitted. Then, it executes the script. As the script executes, it generates a web page as its output. The script may also request data from a database server and use that data as part of the web page it is generating.

When the script is finished, the PHP interpreter passes the dynamically generated web page back to the web server. Then, the web server sends the page back to the browser in an HTTP response that includes the HTML for the page.

When the web browser receives the HTTP response, it formats and displays the web page. This is called *rendering* a page. Note, however, that the web browser has no way to tell whether the HTML in the HTTP response was from a static page or a dynamic page because all it receives is HTML.

When the page is displayed in the browser, the user can view the content. Then, when the user requests another page, the process begins again. The process that begins with the user requesting a web page and ends with the server sending a response back to the client is called a *round trip*.

### How a web server processes a dynamic web page with PHP

![](img/b7dd5fec6684a99ab526c7fe8e21e7de_32_0.png)

### Description

- A *dynamic web page* is a web page that’s generated by a server-side program or script. Often, the web page changes according to the information that’s submitted by the web browser to the server.
- When a web server receives a request for a dynamic web page, it uses the extension of the requested file to determine which server or program should process the request. If the extension is php, the web server calls the *PHP interpreter* to process the request and the data that’s submitted with the request.
- The PHP page can use the data that it gets from the web browser to access the appropriate data from a *database server*. The application can also store the data that it gets from the web browser in the database server.
- When the PHP interpreter finishes processing the PHP page, it generates an HTML page and returns it to the web server. The web server then returns the page to the web browser.
- The browser can’t tell whether the HTML that is returned to it was retrieved from a static web page or generated dynamically by the PHP interpreter. Either way, the browser simply displays (*renders*) the HTML that it receives.
- The process that begins with the user requesting a web page and ends with the server sending a response back to the client is called a *round trip*.

![](img/b7dd5fec6684a99ab526c7fe8e21e7de_32_1.png)
