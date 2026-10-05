# 8.4. USING GORM TO INTERACT WITH A DATABASE

```
Orders []Order

type Order struct {
	gorm.Model
	UserID uint
	Amount int
	Description string
}

func main() {
	pqlInfo := fmt.Sprintf("host=%s port=%d user=%s " +
	"password=%s dbname=%s sslmode=disable",
	host, port, user, password, dbname)
	db, err :=orm.Open("postgres", psqlInfo)
	if err != nil {
		panic(err)
	}
	defer db.Close()


db.LogMode(true)
db.AutoMigrate(&User{}, &Order{})

\var user User
db.Preload("Orders").First(&user)
	if db.Error != nil {
		panic(db.Error)
	}
	fmt.Println("Email:", user.Email)
tfmt.Println("Number of orders:", len(user.Orders))
tfmt.Println("Orders:", user.Orders)
}
```

The code in Listing 8.36 will also work with the Find() method and will preload the orders for every user that ends up subset returned in the query. This is useful when you want to find a specific subset of data.

# Source code

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/8.4.9