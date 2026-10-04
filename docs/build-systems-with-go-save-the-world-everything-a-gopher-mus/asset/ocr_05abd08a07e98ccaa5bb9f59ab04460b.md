3 Name string
4 Email string
5 CreatedAt time.Time
6 UpdatedAt time.Time
}

Actually, GORM defines the struct gorm.Model as follows:

```
1 type Model struct {
2 ID uint `gorm:"primaryKey"
3 CreatedAt time.Time
4 UpdatedAt time.Time
5 DeletedAt gorm.Deleted `gorm:"index"
6 }
```

This struct can be embedded to automatically extend metadata. Structs embedding the gorm.Model can automatically have the ID as the primary key and the corresponding field tracking fields.

In the context of database tables, embedding means that all the information from a struct has to be contained in a column value. GORM permits embedding any struct that implements the Scanner and valuer interfaces from the database/sql package. to be used with an associated entity. In this case, the embedded tag identifies the user field to be embedded into Operator.

```
1 type User struct {
2 Name string
3 Email string
4 }
5 type Operator struct {
6 ID uint
7 User User `gorm:"embedded"
8 Platform string `gorm:"not null"
9}
```

Observe that we have additionally used the "not null" tag to indicate that the field Platform cannot be empty in the database. The complete list of tags can be found in the documentation. Example 18.7 shows the code that permits struct User to be embedded. To serialize the struct using JSON encoding (see Section 8.2) to marshal the struct value in the Value method. In the Scan method we use the JSON unmarshal to populate the struct. Notice that the Scan method has the "User type receiver to ensure that we modify the original value. Additional tag constraints are set in the Dedication field to demonstrate how they can be used. When this field is set to values lower than five create query fields.

# Example 18.7: Embedded structs in GORM.

```
1 package main
2
```