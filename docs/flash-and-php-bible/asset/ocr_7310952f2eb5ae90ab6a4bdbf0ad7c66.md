Your focus in this section is on the $_POST data and conditional check to determine if the password is correct or not. This result is then sent back to Flash where it is used to set logged-in status and whatever else a valid user would see.

A more robust example would have the PHP be evaluated against a database instead of a static string. The $storedPassword variable has an md5( ) hashed string. MD5 is a hashing algorithm that is available in many programming languages, one of which is PHP and is most frequently used when storing passwords in a database. You will look at MD5 a little more in depth in the security chapter, but for now the most important thing to note is that hashed string is your password.

You now have a complete login module using Flash and PHP. You could easily expand this example to include database integration and more importantly, an added level of security.

# Summary

In this chapter you learned how to build forms in Flash and how to make them interactive using PHP. As a more advanced project you then created a login component utilizing the previous information you learned about form development overall.