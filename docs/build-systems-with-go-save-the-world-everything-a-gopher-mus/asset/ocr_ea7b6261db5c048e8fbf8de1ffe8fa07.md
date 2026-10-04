This is the most complex kind of relationship where there is no restriction in the number of entities that can be referred to. In this example, a user can speak many languages and a language can be spoken by many users. Many-to-many relationship has to be represented using a joining table. The field tag manymany defines the name of the join table to be used. Additionally, we have laptops shared by users. A laptop can be used by many users. In this case, Laptops Users fields are arrays that have to be found in a manymany table. Observe, that the array items are pointers. This differs from speaking many languages because the language is meaningful on its own and does not belong to any user.

# Example 18.12: Many to many relationship.

```
type User struct {
ID uint
Name string
Email string
Languages []Language `gorm:"manymany:user_languages`'
Laptops []Laptop `gorm:"manymany:user_laptops`'
}
type Laptop struct {
ID uint
SerialNumber string
Users []User `gorm:"manymany:user_laptops`'
}
```

# 18.3 MANIPULATE DATA

The GORM db type is the main entry to the database and the data models. It controls all the SQL statements to be generated to create, read, update, or delete instances. This Section describes how to use this type to create, query, and manipulate database entries.

Create

The db.Create method receives any object with a migrated schema and writes a new record with the information it contains. Fields that autoincrement like GORM managed do not have to be populated. This can be seen in Example 18.13. The Create method returns a *DB that contains any error found during the operation and the number of rows affected by the operation. In the case of creating several records, the CreateInBatches method optimizes the process by generating groups of SQL statements with a given number of records (5 in the Example).

# Example 18.13: GORM creation of records.

```
package main
```