```
<head>
<title>Customer Information Form</title>
</head>
<body>
<form method='post' action='process_customer.php'>n<h2>Please enter information in all fields</h2>
First Name <input type='text' pattern='[a-zA-Z]*' title='15 or less alphabetic characters' maxLength='15' name='first_name' id='first_name'/><br />
Last Name <input type='text' pattern='[a-zA-Z]*' title='20 or less alphabetic characters' maxLength='20' name='last_name' id='last_name'/><br />
Address <input type='text' title='30 or less characters' maxLength='30' name='address' id='address'/> <br />
City <input type='text' pattern='[a-zA-Z]*' title='20 or less characters' maxLength='20' name='city' id='city'/><br />
State <input type='text' pattern='[a-zA-Z]*' title='2 characters' maxLength='2' name='state' id='state'/><br />
Zip code <input type='number' min='11111' max='99999' title='5 numerical characters' name='zip_code' id='zip_code'/><br />
<input type='submit' value="Click to submit your information" />
</form>
</body>
</html>
```

Note: Some indenting and whitespace has been removed from the examples in this book for better viewing in your Kindle device. Download the code from the author's website to assist you in understanding the code.

Example 1 provides a relatively typical web form that requests information from the user. The html shown also filters the information accepted by the user, using html 5, to ensure that information was provided in the proper format.

Note: If you don't know html, you should review some of the free tutorials and videos provided on the web. PHP is a web application language which commonly interfaces with html and JavaScript.

Once the user enters the information in the proper format and hits the submit button, the information will be sent to a program on the web server for processing. In this example, the html form line indicates that the process_customer.php application will accept and handle the information.

When the information is sent, it is actually sent as a series of properties and