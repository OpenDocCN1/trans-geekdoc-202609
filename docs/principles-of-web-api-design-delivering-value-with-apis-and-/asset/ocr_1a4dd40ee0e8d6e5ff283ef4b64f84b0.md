# 306

# APPENDIX

```
GET http://www.google.com/HTTP/1.1
User-Agent: Mozilla/5.0 [en] (X11; Linux 2.2.013 i686)
Host: google.com
Accept: image/gif, image/x-bitmap, image/jpeg,/*
Accept-Encoding: gzip
Accept-Language: en
Accept-Charset: iso-8859-1, "*,utf-8
```

Figure A.3 A line-by-line examination of an HTTP request to https://www.google.com.

+   - Accept-Encoding: informs the server, if any, compression support the client is able to process it. This allows the server to compress the response using gzip or compress formats to reduce the byte size of the response.

The message body provides details to the server when data is submitted and may be human-readable or binary, as required by the server. For a retrieval request using GET, the message body may be empty.
Figure A.3 shows an example of an HTTP request sent to Google to request the homepage that contains the form search, documented line by line.

# HTTP Response

Once the request is received by the server, the server processes the request and sends a response. The response is composed of three parts: the response code, the response header, and the response body.

The response code is a number that corresponds to a success or error code indicating whether the request could be fulfilled. The response code sent must be one of the those outlined in the HTTP specification and are detailed later. Only one response code is allowed per response.

The response header tells the client about the result of the request. The header is composed of header fields in name:value format. Common HTTP response headers used with Web-based APIs include the following:

+   - Date: The date of the response.
- Content-Location: The fully qualified URL of the response. Useful if the request resulted in redirects that may require the client to update its URL for the resource.
- Resource: The length, in bytes, of the response message body.
- Content-Type: Informs the client of the content type of the message body.