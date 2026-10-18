# TABLE 7.1  ‘XMLHttpRequest’ object properties

| Property | Description |
|---|---|
| `onreadystatechange` | Event handler for an event that fires at every change in the `readyState` |
| `readyState` | The status of the request, which can be in the following states:<br>0 = uninitialized<br>1 = loading<br>2 = loaded<br>3 = interactive<br>4 = complete |
| `responseText` | Data returned from the server as a string |
| `responseXML` | Data returned from the server as an XML document |
| `status` | HTTP status code, for example 200 (OK), 404 (not found) |
| `statusText` | Message string describing the status code |

# TABLE 7.2  ‘XMLHttpRequest’ object methods

| Method | Description |
|---|---|
| `abort()` | Aborts the current request |
| `getAllResponseHeaders()` | Returns all headers (names and values) as a single string |
| `getResponseHeader(headerName)` | Returns the value of the specified header |
| `open(method, URL, asyncFlag, username, password)` | Opens a connection and retrieves a response from the specified URL. The method is usually either GET or POST; optionally, there can be a username and password for secure sites |
| `send(content)` | Sends the request to the server (can include data as a string or DOM object if it is a post request) |
| `setRequestHeader(name, value)` | Assigns the given value to the named header |

# Using Ajax and RSS

Later in this book, we see how to build Ajax applications where we connect from our JavaScript client to our own server-side applications. However, as a first example, we see how to create an Ajax application that connects to server-side data sources that are available from web sites in the public domain. There are many types of data on the web that we could potentially connect to using an Ajax application, but one of the simplest would be an RSS feed. RSS feeds were first introduced in 1999 and have become increasingly popular. During this time, increasing standardisation has been applied to try to ensure interoperability. RSS is an acronym that has some confused roots, standing variously for Really Simple Syndication, Rich Site Summary or RDF Site Summary. However they all