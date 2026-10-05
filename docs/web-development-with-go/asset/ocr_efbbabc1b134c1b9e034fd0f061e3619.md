# CHAPTER 8. AN INTRODUCTION TO DATABASES

In our previous users table we also had a unique constraint on the email field of a user. This is done with GORM by using tags, which are a form of metadata that can be looked up with the reflect package. If you have used the encoding/json package much in Go, you have likely already been introduced to tags, even if you haven't used them before the only thing you need to know is that allow us to tell our code a little more about how we want different fields in our struct to be treated by GORM.

The code in Listing 8.26 illustrates how to ensure that the Email field can't be null, and adds the unique constraint to the field. This will tell our database to keep an index of every email stored in the users table and ensure that each entry in this index is unique. Update your code to reflect the listing.

Listing 8.26: Adding a unique index to users
```go
type User struct {
  gorm.Model
  Name string
  Email string `gorm:not null;unique_index"
}
```

By using an index we also get the added benefit that searching for users by email address will be more efficient because searching a sorted index is much more efficient than looking at every user in our database to see if any of them have the email address we are looking for.

GORM offers a wide variety of ways to declare a model, and all of them are covered in the docs³. You can check these out if you are curious, or if you need one that isn't ever used in this book, but we should cover most of the more common ones while creating our application.

> ^3http://jinzhu.me/gorm/models.html#model-definition