
## CHAPTER 8. AN INTRODUCTION TO DATABASES

```go
const (
    host = "localhost"
    port = 5432
    user = "postgres"
    password = "your-password"
    dbname = "lenslocked_dev"
)

type User struct {
    gorm.Model
    Name string
    Email string `gorm:"not null,unique_index"`
}

func main() {
    pgInfo := fmt.Sprintf("host=%s port=%d user=%s password=%s dbname=%s sslmode=disable", "
        host, port, user, password, dbname)
    db, err := gorm.Open("postgres", pgInfo)
    if err != nil {
        panic(err)
    }
    defer db.Close()

    db.AutoMigrate(&User{})
}
```

You can also use the db.AutoMigrate function to update models. For example, if we added the Age int attribute to the User type and then used GORM's auto-migrate we would get the age field added to our users table.

This makes migrating our database tables really easy, but it does have limits. AutoMigrate will only create things that don't already exist, so if you already have a table named users it would not delete that table and attempt to make a new one. Likewise, it will not delete a column or replace it with a new type as these both have the potential to delete data unintentionally. Instead you will need to handle those types of migrations on your own.

## 8.4. USING GORM TO INTERACT WITH A DATABASE

### Source code

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/8.4.3

Changes - book.usegolang.com/8.4.3-diff

## 8.4.4 Logging with GORM

When using GORM it is often useful to enable logging so that you can track what SQL statements are being run behind the scenes. This is incredibly useful when things aren’t acting the way you expect and you need to dig in and debug.

GORM’s logging can be enabled by calling the LogMode method provided by the gorm.DB type. Open up your experimental main.go source file and we will enable it now.

```
$ atom exp/main.go
```

The LogMode method takes in a single argument - a boolean (true or false). It should be true when you want to enable logging, false when you want to disable it. We will call this inside of our main function after the database connection is opened and we have checked for errors.

```go
func main() {
    sqlInfo := fmt.Sprintf("host=%s port=%d user=%s " + 
        "password=%s db=%s sslmode=disable",
	host, port, user, password, dbname)
    db, err := gorm.Open("postgres", sqlInfo)
    if err != nil {
        panic(err)
    }
    defer db.Close()

    db.LogMode(true)
    db.AutoMigrate(&User{})
}
```

With logging enabled we will start to see output like the following when SQL statements are run.

```
(/Users/jon/go/src/lenslocked.com/exp/main.go:35)
[2017-07-18 17:04:12] [6.85ms] CREATE TABLE "users" ...

(/Users/jon/go/src/lenslocked.com/exp/main.go:35)
[2017-07-18 17:04:12] [1.18ms] CREATE INDEX ...

(/Users/jon/go/src/lenslocked.com/exp/main.go:35)
[2017-07-18 17:04:12] [1.00ms] CREATE UNIQUE INDEX ...
```

You will only see output this when SQL statements are actually run, so if you have already created your users table you won't see this output. If you would like, you can drop the users table and then rerun your code to see output like above.

### Source code

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/8.4.4

Changes - book.usegolang.com/8.4.4-diff

## 8.4.5 Creating a record with GORM

Taking everything the past sections, we are going to write a program that will ask the user for their name and email address and then create a record in our database with that information. The code in Listing 8.28 demonstrates how to create a new record with GORM. We first create a User instance and fill in the Name and Email attributes. We do not need to set the ID or any of the attributes provided by gorm.Model because they are going to be filled in automatically by GORM. Once we have the user object db.Create() returns a gorm.DB instance, so we can then grab the Error to verify that create happened successfully, and then check if the error is nil before proceeding.

Listing 8.28: Create a new record with GORM

```go
name, email := // get the name and email from the user
u := &User{
    Name: name,
    Email: email,
}
if err := db.Create(u).Error; err != nil {
    panic(err)
}
fmt.Printf("%+v\n", u)
```

If we don't use a unique email address every time we run our program we will eventually get an error like pq: duplicate key violates unique constraint "users_email" which means that you are trying to write an email address that already exists in our database. To counter this, it would be nice to have a function that will ask the user for name and email before creating the user object. In Listing 8.29 I have put all of the code from the last sections together; I have also provided getInfo() function which will ask the user for their name and email but I won't be going over the details of what is going here. Just be aware that it will ask you for your name and email every time you run the program and use those values to create a new user.

```
$ atom exp/main.go
```

### Listing 8.29: Creating a dynamic record with GORM

```go
package main

import (
    "bufio"
    "fmt"
    "os"
    "github.com/jinzhu/gorm"
    "github.com/lib/pq"
)
const (
    host = "localhost"
    port = 5432
    user = "postgres"
    password = "your-password"
    dbname = "lenslocked_dev"
)
type User struct {
    gorm.Model
    Name string
    Email string `gorm:"not null,unique_index"`
}
func main() {
    psqlInfo := fmt.Sprintf("host=%s&port=%d&user=%s&password=%s&dbname=%s&sslmode=disable",
        host, port, user, password, dbname)
    db, err := gorm.Open("postgres", psqlInfo)
    if err != nil {
        panic(err)
    }
    defer db.Close()
    db.LogMode(true)
    db.AutoMigrate(&User{})

    name, email := getInfo()
    u := User{
        Name: name,
        Email: email,
    }
    if err = db.Create(u).Error; err != nil {
        panic(err)
    }
    fmt.Printf("%+v\n", u)
}

func getInfo() (string, string) {
    reader := bufio.NewReader(os.Stdin)
    fmt.Println("What is your name?")
    name, _ = reader.ReadString('\n')
    name = strings.TrimSpace(name)
    fmt.Println("What is your email?")
    email, _ = reader.ReadString('\n')
    email = strings.TrimSpace(email)
    return name, email
}
```

Run the code in Listing 8.29 a few times to create a few users in your database. We will be using these in the next section when we start to query our database for specific users.

```
$ go run exp/main.go
```

### Source code

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/8.4.5

Changes - book.usegolang.com/8.4.5-diff

## 8.4.6 Querying a single record with GORM

GORM offers a wide variety of ways to query records, but they all are essentially just helpers for writing SQL, so they are pretty easy to get the hang of.

### Box 8.4. You may want to enable logging here

In Section 8.4.4 we discussed how to enable logging with GORM which causes it to start outputting logs with information about every SQL query it attempts to execute.

It is helpful to enable logging in this section as it will help clarify what piece of code is doing to see the SQL that it generates. As a result, I suggest you enable logging with GORM for the rest of this section and testing out each example to see what SQL is being executed.

In general I prefer to keep this enabled in all development environments so that I can easily debug things.
