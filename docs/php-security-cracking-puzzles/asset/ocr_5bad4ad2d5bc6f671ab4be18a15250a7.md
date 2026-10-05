# # Chapter II.4: MySQL and SQL Injections

![](bbox=[0.049, 0.193, 0.891, 0.363])

# ## II.4.1. Registering a new User System

Organizing a registration system involves providing an HTML form for users to enter the required information. After the information is entered, it is checked for compliance with the requirements. Finally, a check is performed for whether the given user name is already in use, and if it is not the new user is added to the database. Listing II.4.1 shows an example of a script that can be used to carry out all of these procedures.

Listing II.4.1. Registering a new user in the database

```
```
<table>
<form method=post>
<tr><td>Name:</td><td><input type=text name=name></td></tr>
<tr><td>Password:</td><td><input type=password name=pass></td></tr>
<tr><td>Confirm password:</td><td><input type=password name=pass_again></td></tr>
<tr><td>email:</td><td><input type=text name=email></td></tr>
<tr><td>URL:</td><td><input type=text name=url></td></tr>
<tr><td></td><td><input type=submit value='Register'></td></tr>
</table>
```
```