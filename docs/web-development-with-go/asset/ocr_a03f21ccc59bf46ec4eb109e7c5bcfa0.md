# CHAPTER 8. AN INTRODUCTION TO DATABASES

```
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
    Email string ``gorm:"not null,unique_index""
}

func main() {
    pgninfo := fmt.Sprintf("host=%s port=%d user=%s password=%s dbname=%s sslmode=disable", "
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