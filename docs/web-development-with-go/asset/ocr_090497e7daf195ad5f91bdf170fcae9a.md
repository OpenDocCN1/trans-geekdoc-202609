# 194 CHAPTER 8. AN INTRODUCTION TO DATABASES

but I won't be going over the details of what is going on here. Just be aware that it will ask you for your name and email address every time you run the program and will use those values to create a new user.

```
$ atom exp/main.go
```

# Listing 8.29: Creating a dynamic record with GORM

```
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
    Email string `gorm:"not null;unique_index"`
)
func main() {
    psqlInfo := fmt.Sprintf("host=%s&port=%d user=%s&password=%s&dbname=%s&sslmode=disable",
        host, port, user, password, dbname)
    db, err := gorm.Open("postgres", psqlInfo)
    if err != nil {
        panic(err)
    }
    defer db.Close()
    db.LogMode(true)
    db.AutoMigrate(&User{})

name, email := getInfo()
```