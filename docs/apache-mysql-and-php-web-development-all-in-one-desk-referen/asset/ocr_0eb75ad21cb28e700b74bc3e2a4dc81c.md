```
<br>
Favorite Actor:
<input type="text" name="actor">
<br>
<input type="submit">
</p>
</form>
</body>
</html>
```

This is a basic form in an HTML page. Figure 6-1 shows you what the form looks like when a client opens it in Internet Explorer.

Figure 6-1: This is what the form looks like on the client computer in Internet Explorer.

![](bbox=[0.25, 0.34, 0.6, 0.57])

After you have the form, you can put together the .php file that reads the data from the form. The process of the user filling in the data and the PHP program retrieving the form data goes like this:

+   1. The user receives the .html file containing the form.
+   2. The user enters data and clicks the Submit button.
+   3. The client browser sends a request for a PHP file and sends the entered data along with the request.
+   4. The server receives the request and sends it to the PHP processor, which accesses the data, processes the data, and builds a Web page.
+   5. The server sends the built Web page back to the client.

Before I show you a .php file that can process the data, I want to say a few words about these steps. When the user enters the data in a form and clicks the Submit button, the browser sends the data to the server by appending