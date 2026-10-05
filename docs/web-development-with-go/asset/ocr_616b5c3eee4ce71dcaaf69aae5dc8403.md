# 9.3. CREATING USERS

```
password = "your-password"
dname = "lenslocked_dev"
}
func main() {
	psqlInfo := fmt.Sprintf("host=%s port=%d user=%s "
	password=%s db=%s sslmode=disable",
	host, port, user, password, dbname)
	us, err := models.NewUserService(psqlInfo)
	if err != nil {
	panic(err)
}
	defer us.Close()
	us.DestructiveReset()

// This will cause error because you DO NOT have a user with
// this ID, but we will create one soon.
	user, err := us.ByID(1)
	if err != nil {
	panic(err)
}
	fmt.Println(user)
}
```

# Source code

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/9.2

Changes - book.usegolang.com/9.2-diff

# 9.3 Creating users

If you ran the source code for exp/main.go in the last section, you probably noticed that it isn’t very useful yet. We don’t have any users, and we haven’t written a method to create them, so trying to look one up is a pretty pointless.