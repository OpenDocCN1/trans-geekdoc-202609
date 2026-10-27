3. Copy the following XML format into an object (for example) and save it as my_custom_data.xml:

```
<?xml version="1.0" encoding="UTF-8"?>
```

4. Now, you can set up a simple PHP script that writes out the values from the my_custom_data.php file using the following code (we also print out the Content-Type):

```
<?php
```

5. Add this code to your index.php file and make sure you change my_custom_data.xml to point at your my_custom_data.php file. Now your content is available for use on the web!

```
<?php
```

6. To test this, create an HTML page and follow the previous steps, except instead of my_custom_data.xml add:

```
<?xml version="1.0" encoding="utf-8"?>
```

7. To get the values out of my_custom_data.php, you'll need to make two calls, one for the article and one for the message. In my example, I'm converting each value into an array, but you can get fancy with this and use objects or whatever works best for you. Here's an illustration of how to use my_custom_data.php to retrieve the values:

```
<?php
```

8. Now, you can simply write the XML format into your HTML page, and you're done! To test this, create a new HTML page and follow the previous steps, except instead of my_custom_data.php add:

```
<?xml version="1.0" encoding="utf-8"?>
```

# The Syntax for RESTful APIs

There are three ways to access or use RESTful APIs. The first is to create a file that contains the API parameters, which can be accessed from a Javascript file. Another way is by making an HTTP GET request. And lastly, you can make an HTTPS request with the same application.

A JSON object is used to pass parameters and values into RESTful APIs:

GET request:

This means that the API URL will allow you two different ways of accessing the data in your query parameter. These include:

GET request