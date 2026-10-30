# TABLE 7-1 Basic HTTP Messages Sent by a Web Page

| Command | Purpose |
|---|---|
| GET | Request to read a web page |
| HEAD | Request to read a web page |
| PUT | Request to write a web page |
| POST | Request to append to a page |
| DELETE | Remove the web page |
| LINK | Connects two existing resources |
| UNLINK | Breaks an existing connection between two resources |

The most common are GET, HEAD, PUT, and POST. In fact, you might see only those four during most of your analysis of web traffic. LINK and UNLINK are a lot less common. You should know that the GET command actually is the server getting information. So it is very much like the POST command. The differences between the two are as follows:

+   - GET requests can be cached; POST requests are never cached.
+   - GET requests remain in the browser history; POST requests do not remain in the browser history.
+   - GET requests can be bookmarked; POST requests cannot be bookmarked.
+   - GET requests should never be used when dealing with sensitive data.
+   - GET requests have length restrictions; POST requests have no restrictions on data length.

The response codes are just as important. You have probably seen “Error 404 file not found.” But you may not be aware that there are a host of messages going back and forth, most of which you don’t see, as outlined in Table 7-2.

# TABLE 7-2 Web Server/Browser Messages Transparent to the User

| Message Range | Meaning |
|---|---|
| 100–199 | These are just informational. The server is telling your browser some information, most of which will never be displayed to the user. For example, when you switch from http to https, a 101 message goes to the browser telling it that the protocol is changing. |
| 200–299 | These are basically “OK” messages, meaning that whatever the browser requested, the server successfully processed. Your basic HTTP messages like POST, GET, HEAD, etc. should, if everything is working properly, get a 200 code in response. |
| 300–399 | These are redirect messages telling the browser to go to another URL. For example, 301 means that the requested resource has permanently moved to a new URL, but the message code 307 indicates the move is temporary. |