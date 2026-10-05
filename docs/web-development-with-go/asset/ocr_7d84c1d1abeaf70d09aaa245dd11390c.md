which means everything is working!

Again, I want to reiterate that it is important that if you are not using a password
you delete both the password constant and the password portion of the
connection string we are creating. Keeping it can lead to issues, but this code
will still appear to run correctly.

If you instead see an error like `panic: pq: role "bad_user" does not exist` this means that your user is incorrect. You can either create a
ew user in Postgres or you will need to figure out a valid user based on your
installation.

If you see an error like `panic: pq: database "lenslocked_dev" does not exist` this means that you didn’t create the database. You can typically
fix this by running `psql` and then running the SQL code in Listing 8.12

| Listing 8.12: Create a database with SQL |
| CREATE DATABASE lenslocked_dev; |

If your code is having errors with your host or port might take longer to run
because it is attempting to contact a server that isn’t responding. Generally
speaking, your code should run pretty instantly unless you are connecting to a
Postgres server hosted on another computer.

# Source code

The links below have the completed source code and a diff of all the code
changed in this section.

Completed - book.usegolang.com/8.3.1

Changes - book.usegolang.com/8.3.1-diff