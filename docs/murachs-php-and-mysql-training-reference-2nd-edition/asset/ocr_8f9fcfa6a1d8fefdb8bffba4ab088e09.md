# How static web pages are processed

A static web page is a web page that only changes when the web developer changes it. It is a plain text file that contains all the content to be displayed in the web browser. This web page is sent directly from the web server to the web browser when the browser requests it.

Figure 1-2 shows how a web server processes a request for a static web page. The process begins when a user requests a web page in a web browser. The user can either type in the address of the page into the browser’s address bar or click a link in the current page that specifies the next page to load.

In either case, the web browser builds a request for the web page and sends it to the web server. This request, known as an *HTTP request*, is formatted using the *HyperText Transfer Protocol (HTTP)*, which lets the web server know which file is being requested. In this figure, you can see the content of a simple HTTP request.

When the web server receives the HTTP request, it retrieves the requested web page from the disk drive and sends it back to the browser as an *HTTP response*. This response includes the *HTML (HyperText Markup Language)* for displaying the requested page. In this figure, you can see the HTTP response for a simple web page, which includes the HTML for the page.

When the browser receives the HTTP response, it uses the HTML to format the page and displays the page in the web browser. Then, the user can view the content. If the user requests another page, either by clicking a link or entering another web address in the browser’s address bar, the process begins again.

Incidentally, this process depends not only on the HTTP protocol but also on the *Transmission Control Protocol/Internet Protocol (TCP/IP)* suite of protocols. The protocols in TCP/IP let two computers communicate over the network.