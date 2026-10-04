```
41 var retrieved User
42 db.First(&retrieved)
43 fmt.Println("Retrieved", retrieved)
44 }
```

Retrieved inside transaction (1 John newmail)
-github.com/juanmanuel-tirado/savetheworldwithgo/16_sql/gorm/transactions/example_01/main.go:33 UNIQUE constraint failed: users.id
(0.648ms) [rows:0] INSERT INTO 'users' ('name', 'email', 'id') VALUES ('John', 'newmail',1)
Retrieved 1 John john@gmail.com

Transactions can be cancelled manually using Begin, Commit, and RollBack similarly to how it is done in the standard library. 18.19 describes a similar situation to the previous example. However, we add a savepoint to avoid losing the changes to the user record. The savepoint is set after the record update and we rollback to the one exposed when the create operation fails. Finally, we execute the commit to finish the transaction.

# Example 18.19: GORM manual transaction.

```
1 package main
2
3 import (
4 "fmt"
5 "gorm.io/driver/sqlite"
6 "gorm.io/gorm"
7 )\)
8
9 type User struct {
10 ID uint
11 Name string
12 Email string
13 }
14
15 func RunTransaction(u *User, db *gorm.DB) error {
16 tx := db.Begin()
17 if tx.Error != nil {
18 return tx.Error
19 }
20 if err := tx.Model(u).Update("Email", "newmail").Error; err != nil {
21 return err
22 }
23 tx.SavePoint("savepoint")
24 if err := tx.Create(u).Error; err != nil {
25 tx.RollbackTo("savepoint")
26 }
27 return tx.Commit().Error
28 }
29
30 func main() {
31 db, err := gorm.Open(sqlite.Open("/tmp/example02.db"), &gorm.Config{})
```