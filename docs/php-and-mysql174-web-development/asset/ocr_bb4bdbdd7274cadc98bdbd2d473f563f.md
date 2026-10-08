The code to create the functionality shown in Figures 16.1–16.3 is shown in Listing 16.1.

The code from Listing 16.1 provides a simple authentication mechanism to allow authorized users to see a page, but it has significant problems:

+   - Has one username and password hard-coded into the script
- Stores the password as plain text
- Protects only one page
- Transmits the password as plain text

These issues can be addressed with varying degrees of effort and success.

# Storing Passwords

There are many places to store usernames and passwords inside the script. Inside the script, modifying the data is difficult. It is possible, but a bad idea, to write a script to modify itself. Doing so would mean a script on your server that is executed on your server that can be written or modified by others. Storing the data in another file on the server lets you more easily write a program to add and remove users and alter passwords.

Inside a script or other data file, you are limited to the number of users you can have without seriously affecting the speed of the script. If you are considering storing and searching through a large number of items in a file, you should use a database instead, as previously discussed. As a rule of thumb, if you want to store and search through a list of more than a handful of items, they should be in a database rather than a flat file.

Using a database to store usernames and passwords would not make the script much complex but would allow you to authenticate many different users quickly. It would also allow you to easily write a script to add new users, delete users, and allow users to change their passwords. When storing passwords in a database, however, be sure not to store plain text passwords. Instead, it is common to hash passwords using the built-in PHP md5 () function, for example, and comparing the hashed value of the user’s form input to the hashed value stored in the database table. Using this approach, you can still authenticate a user who is attempting to gain access to your protected resource, but you are not storing any actual passwords.

# Securing Passwords

Regardless of whether you store your data in a database or a file, storing the passwords as plain text is an unnecessary risk. A one-way hashing algorithm can provide better security with very little extra effort.