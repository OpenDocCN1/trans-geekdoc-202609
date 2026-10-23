```
return nil
}
```

Hopefully that feels nice and straightforward — we’re using the same code patterns that we did for the CRUD operations on our `movies` table earlier in the book.

The only difference is that in some of the methods we’re specifically checking for any errors due to a violation of our unique `users_email_key` constraint. As we’ll see in the next chapter, by treating this as a special case we’ll be able to respond to clients with a message to say that “this email address is already in use”, rather than sending them a 500 `Internal Server Error` response like we normally would.

To finish all this off, the final thing we need to do is update our `internal/data/models.go` file to include the new `UserModel` in our parent `Models` struct. Like so:

```
File: internal/data/models.go

package data

...

type Models struct {
    Movies MovieModel
    Users  UserModel // Add a new Users field.
}

func NewModels(db *sql.DB) Models {
```