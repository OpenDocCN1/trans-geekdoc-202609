# 8.4. USING GORM TO INTERACT WITH A DATABASE

# Source code

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/8.4.3

Changes - book.usegolang.com/8.4.3-diff

# 8.4.4 Logging with GORM

When using GORM it is often useful to enable logging so that you can track what SQL statements are being run behind the scenes. This is incredibly useful when things aren’t acting the way you expect and you need to dig in and debug.

GORM’s logging can be enabled by calling the LogMode method provided by the gorm.DB type. Open up your experimental main.go source file and we will enable it now.

```
$ atom exp/main.go
```

The LogMode method takes in a single argument - a boolean (true or false). It should be true when you want to enable logging, false when you want to disable it. We will call this inside of our main function after the database connection is opened and we have checked for errors.

```
func main() {
    sqlInfo := fmt.Sprintf("host=%s port=%d user=%s " + 
        "password=%s db=%s sslmode=disable",
	host, port, user, password, dbname)
    db, err := gorm.Open("postgres", sqlInfo)
    if err != nil {
        panic(err)
    }
    defer db.Close()
}
```