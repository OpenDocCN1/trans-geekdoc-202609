
It's also used to reduce the server load.

### 169: What is the use of “die”? Why use “die” for errors when script anyway terminates?

Answer:
We use die in order to prevent abnormal termination of script. The use of die() helps to prevent displaying the physical path of the script in case a fatal error is caught and we terminate the script using die.

### 170: Can you profile your PHP code?

Answer:
One can use the PEAR benchmark module to profile the PHP code.

### 171: How can one use LDAP authentication in PHP?

Answer:
One can use PEAR’s Auth class which supports LDAP authentication.

### 172: Can you add watermark to an image using PHP?

Answer:
The imagestring() function can be used to add a watermark to an image using PHP.

### 173: How do you search for a node or content in XML using PHP?

Answer:
One can use XML path language (XPath) to search for a node or content in XML.

### 174: Is it alright to enable display_errors in PHP.ini file?

Answer:
It should not be enabled as the user will be able to see the complete physical path to the script if some error occurs.

### 175: How can you load classes on demand as required by the interpreter?

Answer:
This can be achieved using __autoload magic function.

### 176: How can one write GUI applications using PHP?

Answer:
One can write GUI applications using PHP with PHP-GTK library.

### 177: How can you send the compressed content to browsers that support automatic decompression?

Answer:
We need to add this line to our PHP.ini file to achieve this –

```
zlib.output_compression=1
```

### 178: How do you find out the locales supported by your system?
How do you set a particular locale using PHP?

Answer:
On Linux/Unix, one can find the program at /usr/bin/locale and on MS Windows, we usually have this in the control panel -> regional options. We can set the locale using setLocale() function in PHP.

### 179: Can you exchange two variables without using a temporary variable in PHP?

Answer:
One can use a construct like this - list($x, $y) = array($y, $x) to swap the variables without using a temporary variable.

### 180: Can you list some predefined classes in PHP?

Answer:
Directory, stdClass, Closure, self, static, parent are some of the predefined classes in PHP.

### 181: How can you prevent the user from knowing the fact that the page has a PHP script in the back-end?

Answer:
RewriteRule in .htaccess file helps to do this. We can configure mod_rewrite() to hide the extensions to achieve this.

### 182: Why is it a good practice to check the referrer when dealing with form submits and uploads?

Answer:
This is necessary from security point of view. Though this can be faked, we can still take care of a large number of malicious activities by checking the referrer that it's the website from where the data is being sent.

## Forms, Cookies and Session Management

### 183: How do you prevent form hijacking in PHP?

Answer:
User input sanitization (client side data validation), form submission key validation, prevention of SQL injection attacks, are some of the important factors to prevent form hijacking in PHP.

### 184: Where does PHP store the cookies and sessions data?

Answer:
PHP stores the cookies on client’s machine and session data on server.

### 185: What are the differences between GET and POST methods?

Answer:
The data submitted by GET method is displayed as part of the URL of the web page and hence it is used for small amount of data, which is insensitive. POST method is used for sensitive and/or large data.

### 186: How do you write the form tag for correct upload of files with PHP?

Answer:
We need to use the method as POST and enctype as “multipart/form-data” in order for upload to work properly.

### 187: How do you get the browser properties using PHP?

Answer:
One can get the browser properties using this - echo $_SERVER['HTTP_USER_AGENT'] in PHP. Additionally, one can use get_browser function.

### 188: How do you delete the cookie with PHP?

Answer:
One can set the cookie in the past to achieve this.

### 189: What is a persistent cookie?

Answer:
A persistent cookie is a cookie which is stored permanently on browser’s machine. Persistent cookies can be used for tracking long term information.

### 190: How to read the value of a cookie that’s already set?

Answer:
A cookie’s value isn’t available in $_COOKIE during the request in which the cookie is set. In other words, the setcookie() function doesn’t alter the value of $_COOKIE. On subsequent requests, however, each cookie is stored in $_COOKIE.

### 191: How do you change the default session time in PHP?

Answer:
The default session time in PHP is 1440 seconds and that can be changed in PHP.ini file.

### 192: Suppose you want to retrieve a page that requires a cookie to be sent with the request for the page. Can you do it using PHP?

Answer:
This can be achieved using PHP cURL extension and CURLOPT_COOKIE option.

### 193: Can we store the session data in the database instead of plain files? What’s the advantage of doing this?

Answer:
One can store the session data in database instead of files using pc_DB_session class. The advantage of doing this is that multiple web servers can have access to the same database.

### 194: Can you have multiple active session objects at a time in PHP?

Answer:
No, it is not possible in PHP to have multiple active session objects at one time.

### 195: What should be done to handle multiple page form when we need to preserve from one page to the next?

Answer:
One needs to use session tracking to achieve this. Session tracking is secure because user cannot modify session variables.

### 196: Are you aware of the resubmission of form? How do you get around this issue?

Answer:
We can generate a unique identifier and pass this as a hidden field with the form. We can generate an error, if the token has been used already. This prevents the resubmission of the form.

### 197: What will happen to sessions if client side cookies are disabled?

Answer:
Session is kind of a cookie which works on server side. For working of session on server side, cookies should be enabled on server side and also on client side browser. But session will also work when cookies are disabled on client side. This works by using URL session passing.

### 198: What is meant by session in PHP?

Answer:
Session is a mechanism for persisting information between page requests from a particular user. After calling session_start(), data stored in the $_SESSION superglobal will continue to be accessible in future page requests from a client identified by a cookie, POST variable or GET parameter.

### 199: Which function do we need to use to use our own session-handling functions?

Answer:
One needs to use session_set_save_handler to use our own session handling functions.

### 200: How do you verify cookie data to make sure user has not altered the data?

Answer:
We can compute the MD5 hash of the data and verify it when you receive back the same data.

This page is intentionally left blank

## HR Questions

Review these typical interview questions and think about how you would answer them. Read the answers listed; you will find best possible answers along with strategies and suggestions.

### 1: What has been your biggest success?

Answer:
Your biggest success should be something that was especially meaningful to you, and that you can talk about passionately – your interviewer will be able to see this. Always have an answer prepared for this question, and be sure to explain how you achieved success, as well as what you learned from the experience.

### 2: What motivates you?

Answer:
It's best to focus on a key aspect of your work that you can target as a “driving force” behind your everyday work. Whether it's customer service, making a difference, or the chance to further your skills and gain experience, it's important that the interviewer can see the passion you hold for your career and the dedication you have to the position.

### 3: What do you do when you lose motivation?

Answer:
The best candidates will answer that they rarely lose motivation, because they already employ strategies to keep themselves inspired, and because they remain dedicated to their objectives. Additionally, you may impress the interviewer by explaining that you are motivated by achieving goals and advancing, so small successes are always a great way to regain momentum.

### 4: What do you like to do in your free time?

Answer:
What you do answer here is not nearly as important as what you don't answer – your interviewer does not want to hear that you like to drink, party, or revel in the nightlife. Instead, choose a few activities to focus on that are greater signs of stability and maturity, and that will not detract from your ability to show up to work and be productive, such as reading, cooking, or photography. This is also a great opportunity to show your
