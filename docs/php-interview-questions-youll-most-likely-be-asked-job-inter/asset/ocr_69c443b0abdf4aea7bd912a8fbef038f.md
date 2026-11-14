# 183: How do you prevent form hijacking in PHP?

Answer:
User input sanitization (client side data validation), form submission key validation, prevention of SQL injection attacks, are some of the important factors to prevent form hijacking in PHP.

# 184: Where does PHP store the cookies and sessions data?

Answer:
PHP stores the cookies on client’s machine and session data on server.

# 185: What are the differences between GET and POST methods?

Answer:
The data submitted by GET method is displayed as part of the URL of the web page and hence it is used for small amount of data, which is insensitive. POST method is used for sensitive and/or large data.

# 186: How do you write the form tag for correct upload of files with PHP?

Answer:
We need to use the method as POST and encytpe as “multipart/form-data” in order for upload to work properly.

# 187: How do you get the browser properties using PHP?

Answer:
One can get the browser properties using this - echo $_SERVER[‘HTTP_USER_AGENT’] in PHP. Additionally, one can use get_browser function.

# 188: How do you delete the cookie with PHP?

Answer:
One can set the cookie in the past to achieve this.

# 189: What is a persistent cookie?