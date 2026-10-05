# Chapter II.7: Authorization and Authentication 291

# II.7.10. Encrypting Database-Stored Passwords

A registration system may be built based on the script and database considered in Section 4.1. Only the SQL query adding a new user must be modified, as follows:

```
INSERT INTO userslist VALUES (NULL, '$POST[name]', MD5 ($POST[pass]),
'$POST[email]', '$POST[url])
```

![](bbox=[0.047, 0.235, 0.138, 0.368])

When implementing the authorization system, the entered password is encrypted using the MD5 algorithm and the obtained hash sum is compared with the corresponding hash sum in the database.

To protect the plaintext passwords of registered users, the passwords should be encrypted using the md() function when implementing the new authorization system. This can be done by executing the UPDATE userslist SET pass = md5(pass) SQL query.

![](bbox=[0.047, 0.481, 0.138, 0.555])

The authorization system can be implemented using one of the scripts from Section II.7.9, with the script deched modified as follows:

```
SELECT COUNT(*) FROM userslist
WHERE name = '$POST[name]' AND pass = MD5('$POST[password])'
```

![](bbox=[0.047, 0.692, 0.138, 0.765])

# II.7.11. Basic HTTP Authorization

To implement HTTP authorization, the following HTTP headers are sent to the client browser:

```
WWW-Authenticate: Basic realm = "Admin Page"
HTTP/1.0 401 Unauthorized
```