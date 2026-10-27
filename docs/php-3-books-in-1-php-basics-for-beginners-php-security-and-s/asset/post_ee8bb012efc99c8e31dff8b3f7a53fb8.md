
## Chapter 7

### RESTful APIs

![](img/232f65b1c63e7757b6150e92c9cc0d00_327_0.png)

A RESTful API is an interface that allows the software to be connected to a data source on the internet through web services. It returns HTTP responses, enabling software developers to use the data in JavaScript code and then process it into the desired format.

RESTful API is a collection of resources that provide data to further process in the application. When we make a call to the API, it returns XML or JSON format as a response.

A few things to note about an API:

All API calls must be wrapped in an XMLHttpRequest object (or flash equivalent). The requests themselves are simple HTTP GETs with parameters passed in form fields or within the URI.

All API resources must be accessed using a uniform URL structure (similar to Uniform Resource Identifiers.)

A RESTful API can be a simple static web page or an entire web service. The only thing required is the ability to call an API.

REST stands for Representational State Transfer. It is a set of architectural constraints for moving data between client and server on the Web. REST requests use HTTP and follow common HTTP conventions, such as using GET or POST commands, cookies, and XML or JSON responses.

### Benefits of RESTful APIs

- 1. RESTful APIs give you full control over data access. You're in charge of which data you access and when. Reading the data in JavaScript is a cinch, with no cryptic HTTP requests. So updating your data is just as simple.
- 2. RESTful APIs result in high performance. If a service already exists that can solve your problem, REST-style calls will quickly return the information you need and dramatically reduce wait times for your application's users.
- 3. RESTful APIs are easy to implement. Most developers understand REST in theory and know how to get started.
- 4. RESTful APIs are scalable and fit for the future. They're designed to be compatible with new technology, so you can use them now but don't have to worry about them becoming obsolete in the future.
- 5. RESTful APIs are secure enough for almost any application purpose. A service is designed to be a secure interface between your server and the rest of the web, so you can be sure that your data is safe. That means you don't have to add extra complexity or security layers to protect the rest of your application.
- 6. A RESTful API can be normalized across all your service providers. This means that you'll only have to deal with one set of data and one set of APIs for accessing that data.
- 7. RESTful APIs are easy to test and can be easily used with other applications.

### How to Create RESTful APIs

There are many ways to create RESTful APIs, but I want to go over a common method with examples. Depending on the language you use, the syntax will change slightly. Each example assumes that you have PHP installed on your server.

### Easy Steps to Creating a RESTful API in PHP

- 1. Create a new folder in the root of your PHP file, called arrays. Inside this folder, create another folder called values.
- 2. Inside the new values folder, create another new file called my_custom_data.php and make the contents look like this:

```
<?php
```

- 3. Copy the following XML format into an object (for example) and save it as my_custom_data.xml:

```
<?xml version="1.0" encoding="UTF-8"?>
```

- 4. Now, you can set up a simple PHP script that writes out the values from the my_custom_data.php file using the following code (we also print out the Content-Type):

```
<?php
```

- 5. Add this code to your index.php file and make sure you change my_custom_data.xml to point at your my_custom_data.php file. Now your content is available for use on the web!

```
<?php
```

- 6. To test this, create an HTML page and follow the previous steps, except instead of my_custom_data.xml add:

```
<?xml version="1.0" encoding="utf-8"?>
```

- 7. To get the values out of my_custom_data.php, you'll need to make two calls, one for the article and one for the message. In my example, I'm converting each value into an array, but you can get fancy with this and use objects or whatever works best for you. Here's an illustration of how to use my_custom_data.php to retrieve the values:

```
<?php
```

- 8. Now, you can simply write the XML format into your HTML page, and you're done! To test this, create a new HTML page and follow the previous steps, except instead of my_custom_data.php add:

```
<?xml version="1.0" encoding="utf-8"?>
```

### The Syntax for RESTful APIs

There are three ways to access or use RESTful APIs. The first is to create a file that contains the API parameters, which can be accessed from a Javascript file. Another way is by making an HTTP GET request. And lastly, you can make an HTTPS request with the same application.

A JSON object is used to pass parameters and values into RESTful APIs:

GET request:

This means that the API URL will allow you two different ways of accessing the data in your query parameter. These include:

GET request

This is the most regular method of RESTful API calling. The method allows you to make a GET request. All GET requests to use the query string, which contains parameters to be used in the requests made by your application. The parameters are separated from one another by "&" sign characters.

Our JavaScript code example will access this URL:

```
http://api-test.local/custom-data/my_data.xml?my_value=1234
```

This URL's parameters are:

my_value: 1234

When the GET request is successful, an XML document will be returned. The document contains the response and error, as well as a few extra tags that can be used to validate your calls with the API.

We'll keep the error part of this code simple. We'll have to create a new file called my_error.xml containing the following:

```
<?xml version="1.0" encoding="UTF-8"?>
```

Now let's focus on the data/response part of this example. We're getting the response from our my_custom_data.php file with a call to an if() function and then putting it into an array called data:

```
<?php
```

Here is our my_custom_data.xml file:

```
<?xml version="1.0" encoding="UTF-8"?>
```

And our PHP file:

```
<?php
```

Now we can create our function() function. This function is going to be sending the data that was in the my_custom_data.xml file to an if() function so that we can convert it into JSON data and then use that as its parameter in a call to the GET request. In our function() function, we need to do the following:

- 1. Create a new variable called xml (it's a key/value array).

```
<?php
```

- 2. Give the xml variable the value of my_custom_data.xml. The ip_array is going to hold all the IPs in our array that we created earlier:

```
<?php
```

- 3. Retrieve all of the elements from the my_custom_data.xml array by passing the value of the element into an array or object. Make sure that the data is being returned as a key/value array.

```
<?php
```

This is our output data:

```
<?php
```

Our application is now ready to be written into an HTML file and sent over to http://your-ip-address/api-test.local/custom-data/my_data.xml?my_value=1234&my_error=something went wrong.

## Chapter 8

### PHP and Internet Services

![](img/232f65b1c63e7757b6150e92c9cc0d00_333_0.png)

PHP is a popular server-side programming language for creating dynamic web pages. It's used by websites like Facebook, Wikipedia, and Hulu for its speed and efficiency, not only in the creation of sites but also in creating applications.

However, there are many ways you can use PHP to create your own network services or execute other tasks on the server. By simply installing a PHP script on your server, you can create virtually any functionality, from simple home pages to complex applications that involve both client and server.

### Benefits of Using PHP for Internet Services

- 1. **PHP scripts don't require compilation to run**

There is no need to compile the code in order for it to run. All that is needed is for the PHP extension (also known as a module) to be installed on the server. Once this has been completed, you can execute any of your PHP scripts, and they will run immediately.

- 2. **PHP can be used on virtually all operating systems**

PHP isn't specific to any particular operating system. In fact, it can be used on both Microsoft Windows and Linux servers. As PHP is open-source software, anyone can freely use it on most
