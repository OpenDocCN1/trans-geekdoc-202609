# 12.1. SEPARATING RESPONSIBILITIES

we discussed earlier. For example, we could create a user service without a validator and one with.

```
usWithoutVal := UserService(
  UserReader: userGorm(db),
)

usWithVal := UserService(
  UserReader: userValidator(
    UserReader: userGorm(db),
  )
)
```

In the next section we will get back to writing code, and we will start by creating an interface that defines all of the ways we can interact with the users table in a database. We will then add a few layers to our UserService, setting ourselves up to start organizing our code properly.

If you are a little lost right now, try going through the rest of the chapter before giving up. Much of what we are discussing is hard to understand conceptually until you see it in action, but once you start to see the code it all becomes much clearer.

# Box 12.4. Testing is simpler with interfaces

Using embedded interfaces and many layers makes testing much simpler, and while we't be writing tests in this course I think it is important to learn to design code that is testable.

The many layers make testing easier because we can break our tests. When we test our database layer, we don't need to concern ourselves with invalid data. We simply need to test that this code works when passed valid data.

Similarly, our validation layer only needs to concern itself with validating data, and we don't really need to worry about interacting with a real database. In fact,