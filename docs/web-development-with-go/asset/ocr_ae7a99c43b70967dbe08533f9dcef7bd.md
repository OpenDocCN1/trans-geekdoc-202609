# 14.3. CONSTRUCTING MANY SERVICES

```
services, err := models.NewServices(psqlInfo)
if err != nil {
    panic(err)
}
// TODO: Simplify this
defer services.User.Close()
services.User.AutoMigrate()

staticC := controllers.NewStatic()
usersC := controllers.NewUsers(services.User)

// ... the routing code remains unchanged
```

Our code should now compile and run much like it did before, but rather constructing each service individually we are constructing them all with a single function call. We are still manually auto-migrating and closing the user service, but we will address that in the next section.

**To recap:** In this section we wrote code that is intended to make it easier to construct all of our services exported by the models package. At this point our code won’t functionally be much different than it was before, but this will make it easier to use the models package in the rest of our code.

# Source code

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/14.3

Changes - book.usegolang.com/14.3-diff