# 8.4. USING GORM TO INTERACT WITH A DATABASE

```
u := User{
Name: name,
Email: email,
}
if err = db.Create(u).Error; err != nil {
panic(err)
}
fmt.Printf("%s+v\n", u)

func getInfo(name, email string) {
reader := bufio.NewReader(os.Stdin)
fmt.Println("What is your name?")
name, _ = reader.ReadString('\n')
name = strings.TrimSpace(name)
fmt.Println("What is your email?")
email, _ = reader.ReadString('\n')
email = strings.TrimSpace(email)
return name, email
}
```

Run the code in Listing 8.29 a few times to create few users in your database.
We will be using these in the next section when we start to query our database for specific users.

```
$ go run exp/main.go
```

# Source code

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/8.4.5

Changes - book.usegolang.com/8.4.5-diff