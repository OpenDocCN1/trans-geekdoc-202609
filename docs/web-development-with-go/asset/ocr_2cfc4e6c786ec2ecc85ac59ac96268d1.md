# 8.3. USING POSTGRES WITH GO AND RAW SQL

# 8.3 Using Postgres with Go and raw SQL

While Go offers the database/sql package as part of the standard library, we will also need to install a Postgres specific driver to go along with. For this we are going to use github.com/lib/pq which is written in Go and passes the compatibility test for SQL drivers.

To this do you will need to use the go get command again.

+   Listing 8.4: Install lib/pq.

```
$ go get -u github.com/lib/pq
```

# 8.3.1 Connecting to Postgres with the database/sql package

Next we need to write some code that actually uses these two packages. This isn't quite we will use in our final product, so the exp directory we created in Section 4.4 is going to be a good place for this code to live.

If you don't already have a file exp/main.go you should create one. You may also need to create the exp directory.

```
$ mkdir exp # this may already exist
$ atom exp/main.go
```

Delete everything in the file your experimental source file. We are going to be starting from scratch and won't need any of the existing code.

The first thing we want to declare our package and specify our imports. We will be importing the database/sql package so that we can access our SQL database, the fmt package for printing to the terminal and formatting strings, and finally the github.com/lib/pq package which implements the Postgres driver used by the database/sql package.