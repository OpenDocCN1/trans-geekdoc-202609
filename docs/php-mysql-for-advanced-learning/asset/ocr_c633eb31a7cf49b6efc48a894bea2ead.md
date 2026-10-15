responseText: The responseText property will be returned once a request has gone through. If you are raising a request to a script of some sort, the output of the script will be returned through this property.

Once a request has been received, the server then decides what response to return. There are many different response codes as follow.

+   - 200 - OK
+   - 401 Unauthorized
+   - 403 Forbidden
+   - 404 Not Found
+   - 500 Internal Server Error

# Sending a Request to the Server:

In order to make a request to the server you need to decide what page (or script) you want to connect to, and then what area to load the page or script into.

# Let’s have a basic example-

```
<script>

function sendRequest(serverPage, objID)
{
```