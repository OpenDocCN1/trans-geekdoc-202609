```
{
  "name": "Alice Smith",
  "email": "alice@example.com",
  "password": "pa55word"
}
```

When we receive this, the `registerUserHandler` should create a new `User` struct containing these details, validate it with the `ValidateUser()` helper, and then pass it to our `UserModel.Insert()` method to create a new database record.

In fact, we’ve already written most of the code we need for the `registerUserHandler` — it’s now just a case of piecing it all together in the correct order.

If you’re following along, go ahead and create a new `cmd/api/users.go` file:

```
$ touch cmd/api/users.go
```

And then add the new `registerUserHandler` method containing the following code:

```
File: cmd/api/users.go

package main
```