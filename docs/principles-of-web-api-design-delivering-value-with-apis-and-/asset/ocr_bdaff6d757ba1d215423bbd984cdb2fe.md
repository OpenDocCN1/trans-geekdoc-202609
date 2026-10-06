# # Appendix

# # HTTP Primer

To better understand how Web APIs work, it is important to start with an understanding of HTTP, the language of the Web. While the HTTP protocol can be hidden behind various libraries and frameworks, understanding the protocol provides a foundation for troubleshooting API integrations and improved API design.

This primer offers an introduction to the HTTP protocol, the elements that are involved in using HTTP for interacting with Web APIs, and some advanced features that help to shape more powerful API interactions.

# ## Overview of HTTP

The HTTP protocol is a client/server protocol. An HTTP client sends a request to a server. The HTTP server then determines if it can service the request with the information given. The server returns a response that includes a code indicating success or failure, along with a response payload containing the information requested or details about the error. This request/response flow is illustrated in Figure A.1.

HTTP is comprised of several elements:

+   - The Uniform Resource Locator (URL) where the request is sent
- The HTTP method that informs the server how the client wishes to interact with the resource
- The request headers and body
- The response headers and body
- A response code that indicates whether the request was successfully processed or an error was encountered