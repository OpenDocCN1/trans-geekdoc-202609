# Introduction and Installation Configuration

Second, let's discuss altering the log-bin configuration option that can be found in the following section of the my.cnf file:

```
# Uncomment the following if you want to log updates
#log-bin
```

This is very important if you are all about monitoring which updates are made to your MySQL tables (and you should). This logs all activity to the tables, and this topic is greater in detail Chapter 16. We recommend that you uncomment the log-bin line to at least make the data available. Whether or not you do anything with it is another story.

# Setting Up Users and Privileges

Hackers (or the malicious breed known as "crackers") can be quite crafty in the ways which they break into your system, if you are directly connected to the Internet. MySQL allows you to pick and choose what user is allowed to perform function based on the "privileges" you establish. All user privilege information is stored in a database mysql, which is located, by default, in your c\mysql\data directory.

If you're the only accessing the MySQL database, you may not have to worry about adding updates. However, what if you have, say, an Aunt Edna is going to help you out by inputting logged information? You want her to be able to go into the tables and look at things, and even insert some information. You probably don't want her to delete your entire database. By restricting her as a user, you will help to protect your data.

# Try It Out Setting Up Privileges

In order to set up the initial privileges parameters, you need to make sure you're logged on "root.\ Then you're going to GRANT Aunt Edna some privileges as a new user, so type this following:

```
mysql> GRANT SELECT, INSERT, UPDATE
>--> ON *.*
>--> TO edna@localhost
>--> IDENTIFIED BY 'ednapass'
```

# How It Works

You have established that "edna" is a valid user who will be allowed to access your MySQL system, provided two things:

+   - She attempts her connection from the "localhost" host—not a different connection from where else.

+   - She supplies the correct password: "ednapass".

Your Aunt Edna will now be allowed to select information from the database, insert new information in the database, and update old information in the database. By giving her access to all the tables in the database (via the use of ON *.*), we have allowed her to modify any table in existence.