# 8.4. USING GORM TO INTERACT WITH A DATABASE

Completed - book.usegolang.com/8.4.7

Changes - book.usegolang.com/8.4.7-diff

# 8.4.8 Creating related models with GORM

When we were learning about the database/sql package before we created an additional table, the orders table. In this section we are going to recreate that table using GORM and fill it with some fake data that we will use in the next section to demonstrate how to query related records using GORM.

The first thing we need to do is create the Order type. Doing this will be very similar to our User type; We will be embedding the gorm.Model type and declaring other fields we inside of the type.

```
type Order struct {
  gorm.Model
  UserID      uint
  Amount      int
  Description string
}
```

The only part in this code that might warrant a second glance is the UserID being of the type uint, an unsigned integer. We are doing this because we are never using negative IDs in our database, so we can reflect that in our Go code by using the uint instead of int.

We will be creating a few orders, so we are going to write a function to make this little faster. We will simply pass the data needed to create an order into the function and let it handle checking for errors and saving to the database.

```
func createOrder(db *gorm.DB, user User, amount int, desc string) {
  db.Create(&Order{
    UserID: user.ID,
    Amount: amount,
  })
```