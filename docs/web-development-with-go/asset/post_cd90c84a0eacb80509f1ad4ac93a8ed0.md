
# CHAPTER 8. AN INTRODUCTION TO DATABASES

| 1 | jon@calhoun.io | Jon Calhoun | 1 | 1000 | USB-C Adapter x1 |
| 1 | jon@calhoun.io | Jon Calhoun | 2 | 2000 | USB-C Adapter x2 |
| 1 | jon@calhoun.io | Jon Calhoun | 3 | 3000 | USB-C Adapter x3 |
| 2 | bob@calhoun.io | Bob Calhoun | 4 | 4000 | USB-C Adapter x4 |
| 2 | bob@calhoun.io | Bob Calhoun | 5 | 5000 | USB-C Adapter x5 |

Doing with Go's database/sql package is actually pretty easy if you understand the SQL, and your code will be nearly identical to Section 8.3.5 but you will need to update the SQL you pass into db.Query() and then you will need to update your rows.Scan() method call to pass in variables for the additional data.

This is what makes the database/sql package powerful - if you already understand SQL it doesn't take much additional learning to get your code up and running with your database.

## 8.3.8 Delete the SQL tables we were testing

We are now done using the database/sql package directly and we will be trying out the github.com/jinzhu/gorm package. As we no longer need the tables we created in this chapter and we can safely delete them by opening psql and running the SQL code in Listing 8.22.

> Listing 8.22: Dropping the orders and users tables

```
DROP TABLE orders;
DROP TABLE users;
```

## 8.4. USING GORM TO INTERACT WITH A DATABASE

## 8.4 Using GORM to interact with a database

GORM is an ORM, which stands for an object-relational mapping. ORMs are used to simplify the process of mapping data in one system to data.

In the case of SQL, GORM allows us to express what our data will look like in Go, and then handles translating that into a format that our Postgres database understand. This is really handy when developing a new web application because it allows us to skip writing a translation layer manually.

GORM also provides a few helper functions that help simplify our code when working with an SQL database. For example, we don't need to write full SQL and instead can use some helper methods to write shorter queries.

In this section and the upcoming subsections we are going to look at how to install GORM, and then we will walk through replicating most of the things we did with raw SQL using GORM so you can see the difference between the two.

We will still be working in exp/main.go, and we will be reusing the constants with your database connection information, so be sure to keep those if you decide to clean up your code a bit.

### 8.4.1 Installing GORM and connecting to a database

The first thing we need to do install GORM. We have done this several times in the book so, so you should be pretty comfortable doing this.

| Listing 8.23: Install github.com/jinzhu/gorm |

```
go get -u github.com/jinzhu/gorm
```

Once you have GORM installed, connected to a database is very similar to what we were doing with the database/sql package, but there are two notable changes.

First, we are going to import the GORM dialects for Postgres instead of the github.com/lib/pq package.

``` evenimport (
    "github.com/jinzhu/gorm/dialects/postgres"
)
```

Behind the scenes this will still load github.com/lib/pq, but it is a little easier to remember and handles any other initializations GORM might require to operate correctly with PostgreSQL. It is also a little clearer to why we need it since we can see GORM being used in this file

Along with the imports change, we are going to update our code to use gorm.Open () to open our database instead of calling sql.Open ( ). We will still use the same arguments, and the two behave very similarly, but gorm.Open ( ) will return us a *gorm.DB instead of a *sql.DB.

Listing 8.24: Connecting to a database with GORM

```go
package main

import (
    "fmt"

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

func main() {
    psqlInfo := fmt.Sprintf("host=%s port=%d user=%s user=%s " +
    "password=%s dbname=%s sslmode=disable", host, user, password, dbname)
    db, err := gorm.Open("postgres", sqlInfo)
    if err != nil {
        panic(err)
    }
    defer db.Close()
```

### 8.4.2 Defining a GORM model

Up until now we have been what our database tables will have in them by writing SQL to create the table. With GORM we are going to try taking another approach - we are going to define a struct type in our code and let GORM translate that into an SQL table and create the table for us.

First let's open our experimental main.go source file.

```bash
$ atom exp/main.go
```

We are going to leverage the gorm.Model type which already has the basic fields that we will almost always want, like the unique ID for each resource and a timestamp for when the resources was created and updated.

We can also create custom fields. For example, we might want to add a field for a user's email address and name on top of the basic fields provided by gorm.Model. Listing 8.25 demonstrates how to create a struct that includes both the base gorm.Model as well as a few custom fields. Add the source code to your experimental main.go source file.

> Listing 8.25: First GORM model

```go
type User struct {
    gorm.Model
    Name string
    Email string
}
```

In our previous users table we also had a unique constraint on the email field of a user. This is done with GORM by using tags, which are a form of metadata. If you have used the encoding/json package much in Go, you have likely been introduced to tags, even if you haven't used them the only thing you need to know is allow us to tell our code a little more about how we want fields to be treated.

The code in Listing 26 illustrates how to ensure the.

```go
type User struct {
    gorm.Model
    Name string
    Email string `gorm:"not null;unique"`
}
```

By using an index we also get the added benefit that searching for users by email address will be more efficient than looking at every user in our database.

GORM offers a wide variety of ways to declare a model, and all of them are covered in the docs You can check these out if you are curious, or if you need one that isn't used in this book, but we should cover most of the more common ones while creating our application.

> ^3http://jinzhu.me/gorm/models.html#model-definition

## 8.4.3 Creating and migrating tables with GORM

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/8.4.2

Changes - book.usegolang.com/8.4.2-diff

### 8.4.3 Creating and migrating tables with GORM

While we may have declared a type in our Go code, we have actually created a table in our database. To do this we are going to use the migrations features offered by GORM. This will allow us to update our models without actually writing SQL.

The first tool we are going to look at is the AutoMigrate function. This takes in instances of several types and creates corresponding tables in our SQL database based on the tags we set, the names of the fields and the type, and other factors. In Listing 8.27 our code will create a table named users because it is the snake case plural of User. Inside of that table it would have the fields id, created_at, updated_at, deleted_at from the embedded gorm.Model, and it would also have the name, and email fields. The last two are created by taking the attributes of the User type and turning them into snake case field names.

Listing 8.27: Automigrating with GORM
```go
package main

import (
	"fmt"
	"github.com/jinzhu/gorm"
	"github.com/lib/pq"
)
```
