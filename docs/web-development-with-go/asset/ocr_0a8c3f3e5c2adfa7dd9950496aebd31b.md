# 318
CHAPTER 11. REMEMBERING USERS

```
if err != nil {
    panic(err)
}
defer us.Close()
us.DestructiveReset()

user := models.User{
    Name: "Michael Scott",
    Email: "michael@undermifflin.com",
    Password: "bestboss",
}
err := us.Create(&user)
if err != nil {
    panic(err)
}

// Verify that the user has a Remember MemberHash
fmt.Printf("%v\n", user)
if user.Remember == ""
    panic("Invalid remember token")
}

// Now verify that we can look up a user with that remember
// token
user2, err := us.ByRemember(user.Remember)
if err != nil {
    panic(err)
}

fmt.Printf("%v\n", user2)
```

In this code we:

+   1. Reset our users table
2. Create a new user and allow our user service to set the remember token
3. Verify that the remember token was set, and panic otherwise
4. Search for a user via the remember token to verify the ByRemember method works and to verify that our remember token persisted correctly

You can run it out to test it yourself by running: