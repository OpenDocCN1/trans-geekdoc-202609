
## 8.4. USING GORM TO INTERACT WITH A DATABASE

```go
if db.Error != nil {
    panic(db.Error)
}
fmt.Println(u)
```

In Listing 8.30 we are telling GORM that we would like the first user in our database to be retrieved and stored in the u object. By passing in an address to a user object, GORM knows to query the users table, and knows to put the resulting record into the object passed in the first argument.

If there was an error it would be present on our db object, so we need to check to see if db.Error has a value before using our user object. We will be doing this with every example moving forward, and it is a general pattern you can follow when using GORM. Instead of returning errors it frequently attaches them to the db object.

# Box 8.5. Where did the extra SQL come from?

If you have enabled logging you might be asking yourself “Where did all of the extra SQL code in my SQL query come from?”. We didn’t write anything about the deleted_at field being NULL in our query, and we definitely didn’t specify an order for the SQL query.

By default, GORM assumes that you use the deleted_at field to mark a record as deleted rather than actually deleting the record from your database. As a result, it will ignore any record that has a value set for this by default.

GORM also sets a default order for queries to provide a little more consistency with our queries. As a result, when you call the First () method you can rest assured that it will always return the record with the lowest ID unless your query specifies a different order to sort the results.

# Listing 8.31: Querying for the first user with id=1

```go
var u User
id := 1

db.First(&u, id)
if db.Error != nil {
    panic(db.Error)
}
fmt.Println(u)
```

Our second example in Listing 8.31 is very similar to our first except we are now providing a second argument to the First () method - an ID.

GORM allows us to provide an ID as the second argument to the First () method as a handy way of querying for objects with a specific ID without writing out a WHERE statement. We will end up going a bit in our code.

# Listing 8.32: Querying with the Where () method

```go
var u User
maxID := 3

db.Where("id <= ?", maxID).First(&u)
if db.Error != nil {
    panic(db.Error)
}
fmt.Println(u)
```

Listing 8.32, our third example, demonstrates how to chain the Where () method along with the First () method to create a WHERE query. In this example we are looking for any user whose ID is less than or equal to the provided id, which happens to be 3 in this case.

GORM offers several helper methods like Where () that can be chained together to create more complex queries, and you can find examples of most of them in the GORM querying documentation.

## 8.4. USING GORM TO INTERACT WITH A DATABASE

When using these queries, you might have noticed that we use the ? character instead of $1 and $2 like we were using with the database/sql package. They end up doing the same thing, but because we don't have numbered parameters we need to include the same argument multiple times if we intend to use it in multiple spots in our query.

```go
Listing 8.33: Querying with an existing user
```go
var u User
u.Email = "jon@calhoun.io"
db.Where(u).First(&u)
if db.Error != nil {
    panic(db.Error)
}
fmt.Println(u)
```



In addition to querying with strings, you can also query by passing a model that matches what you are looking for to the Where() method. In Listing 8.33 we are searching for a user with the email address “jon@calhoun.io” by setting the email address on our User object and then passing that object into our Where() method.

This can be useful for building a more complex query because you can have different parts of your code set different attributes of the user object before finally executing your query, but it can also be confusing at times because an attribute you weren't expecting to be set could end up affecting your query.

There are a lot of other ways to query with GORM, and we will be covering several of them throughout this book, but rather learning them all upfront I suggest you wait until you need a new query and then check out the GORM docs to figure out how to create what you need. This allows you to be productive immediately, and also ensures you are only learning things you will actually use in practice.

# Source code

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/8.4.6

Changes - book.usegolang.com/8.4.6-diff

## 8.4.7 Querying multiple records with GORM

Querying for multiple records with GORM is nearly identical to querying for a single records, except we will be using the Find() method instead of the First () method, and we will be passing in a slice of users instead of a single user.

Listing 8.34: Querying for multiple users
```go
var users []User
db.Find(&users)
if db.Error != nil {
    panic(db.Error)
}
fmt.Println("Retrieved", len(users), "users.")
fmt.Println(users)
```

Behind the scenes the major difference between Find() and First () is that First () will automatically add a LIMIT 1 to the query because it is aware that we only want one item returned.

# Source code

The links below have the completed source code and a diff of all the code changed in this section.

## 8.4. USING GORM TO INTERACT WITH A DATABASE

Completed - book.usegolang.com/8.4.7

Changes - book.usegolang.com/8.4.7-diff

## 8.4.8 Creating related models with GORM

When we were learning about the database/sql package before we created an additional table, the orders table. In this section we are going to recreate that table using GORM and fill it with some fake data that we will use in the next section to demonstrate how to query related records using GORM.

The first thing we need to do is create the Order type. Doing this will be very similar to our User type; We will be embedding the gorm.Model type and declaring other fields we inside of the type.

```go
type Order struct {
  gorm.Model
  UserID      uint
  Amount      int
  Description string
}
```

The only part in this code that might warrant a second glance is the UserID being of the type uint, an unsigned integer. We are doing this because we are never using negative IDs in our database, so we can reflect that in our Go code by using the uint instead of int.

We will be creating a few orders, so we are going to write a function to make this little faster. We will simply pass the data needed to create an order into the function and let it handle checking for errors and saving to the database.

```go
func createOrder(db *gorm.DB, user User, amount int, desc string) {
  db.Create(&Order{
    UserID: user.ID,
    Amount: amount,
    Description: desc,
  })
  if db.Error != nil {
    panic(db.Error)
  }
}
```

With these two pieces we are ready to put it all together and look up a user, then create several orders for that user. The final code can be found in Listing 8.35. You should update your exp/main.go file with this code and then run it to create a few orders to use in the next section.

# Listing 8.35: Creating the orders table

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

type User struct {
    gorm.Model
    Name string
    Email string `gorm:"not null;unique_index"`
}

type Order struct {
    gorm.Model
    UserID uint
    Amount int
    Description string
}

func main() {
    psqlInfo := fmt.Sprintf("host=%s port=%d user=%s" +
    "password=%s dbname=%s sslmode=disable", host, port, user, password, dbname)
    db, err := gorm.Open("postgres", psqlInfo)
    if err != nil {
        panic(err)
    }
    defer db.Close()

    db.LogMode(true)
    db.AutoMigrate(&User{}, &Order{})

    var user User
    db.First(&user)
    if db.Error != nil {
        panic(db.Error)
    }

    createOrder(db, user, 1001, "Fake Description #1")
    createOrder(db, user, 9999, "Fake Description #2")
    createOrder(db, user, 8800, "Fake Description #3")
}
```
