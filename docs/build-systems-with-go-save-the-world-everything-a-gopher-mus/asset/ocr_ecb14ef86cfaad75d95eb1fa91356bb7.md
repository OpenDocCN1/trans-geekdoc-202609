# Example 18.15: GORM queries (continuation).

```
var retrievedUsers []User
db.Find(&retrievedUsers)
fmt.Println("Find: %v", retrievedUsers)
db.Find(&retrievedUsers, []int{2,4})
fmt.Println("Find ID=2, ID=4: %v", retrievedUsers)
var user *User
db.Where("name = ?", "Jeremy").First(&user)
fmt.Println("Where name = ?: %v", retrievedUsers)
db.Where("name LIKE ?", "%%Jeremy%%").Find(&retrievedUsers)
fmt.Println("Where name LIKE%%Jeremy%%: %v", retrievedUsers)
db.Where("name LIKE ?", "%%Ny%%").Find(&retrievedUsers)
fmt.Println("Name with o or y: %v", retrievedUsers)
var user *User
db.Where(&User{Name: "Mary"}).First(&user)
fmt.Println("User with name Mary, %v", user)
db.Order("name asc").Find(&retrievedUsers)
fmt.Println("All users ordered by name", retrievedUsers)
```

Find [1 John] (2 Mary) (3 Peter) [4 Jeremy]
ID=2, ID=4 [4 Jeremy]
Where name=Jeremy [4 Jeremy]
Where name=%s ([1 John] (4 Jeremy))
Name with 2 or y [1 John] (2 Mary) [4 Jeremy]
User with name Mary (2 Mary)
All users ordered by name [[4 Jeremy] (1 John) (2 Mary) (3 Peter)]

Eager loading
GORM forms an eager loading for relationships. This feature permits programmatically queries to be executed before. This is particularly useful to populate structs with fields that are foreign keys. In Example 18.16 we have a one-to-many relationship where a user can have several laptops. If we retrieve a user from the database the returned row has no laptops. These entries are already in the database. These entries are referred by a foreign key and the content requires an additional query to be retrieved. Adding eager reloading with db.Preload("Laptops") identifies to GORM that there are laptops to populate the resulting record. When executed, the retrieved rows contain the Laptops field populated.

# Example 18.16: GORM preload.

```
package main
import (
	"fmt"
	"gorm.io/driver/sqlite"
	"gorm.io/gorm"
)
```