# Creating the Database

We will use the Adminer tool to create our database and our tables. However, before we do, it is a good and secure practice to create a separate database user for our movie database.

# Creating a Separate Database User

We will use the MySQL CLI tool to create a new user called movieguru and grant all privileges on all the tables in the Movie database.

Logging in as root in the MySQL CLI tool, execute the following commands:

```
CREATE USER 'movieguru'@'localhost' IDENTIFIED BY 'ilikemovies';
GRANT ALL PRIVILEGES ON Movie.* TO 'movieguru'@'localhost';
FLUSH PRIVILEGES;
```

Running this in the MySQL CLI tool to create a user and grant all privileges for the movie database, we see Figure 15.1.

> We do not need to have the database created before we grant privileges on it.

![](bbox=[0.12, 0.52, 0.85, 0.86])