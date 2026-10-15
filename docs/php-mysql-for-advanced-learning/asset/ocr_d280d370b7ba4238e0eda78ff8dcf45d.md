Hirdesh Bhardwaj

Now let‘s create a Database and table (Open MYSQL
localhost://phpmyadmin) as required below

**Database Name:** mydb

**Table Name:** employees

**Column List:** name, email, password, phone

# __To create a above database mydb run the following command__

```
Create database mydb;
```

# __To create table employees containing columns as mentioned above
run the following command -__

```
Create table employees (name varchar(20), email varchar(30),
password varchar(20), phone varchar(25));
```

# __Connecting to the MySQL Server__

Before you can do anything with MySQL, you must first connect
to the MySQL server using your specific connection variables.
Connection variables consist of the following parameters, which
you must know before you make connectivity to the server:

**Host name**- In our case, it‘s the localhost because we‘ve installed
everything locally. You will need to change this to whatever host is
acting as your MySQL server.

**User name**- We‘ve used just the root user for local computer, but
you may have another user name that you‘ll need to create
username while making site live.