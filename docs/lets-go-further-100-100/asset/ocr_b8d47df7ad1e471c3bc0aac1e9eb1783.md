```
```
}
return
}

// Add the user record to the request context and continue as normal.
r = app.contextSetUser(r, user)

next.ServeHTTP(w, r)
})
}
```
```

Lastly, to get this working, you’ll need to create a new `UserModel.Get()` method to retrieve the user details from the database based on their ID.

```
```go
File: internal/data/users.go

package data

...

func (m UserModel) Get(id int64) (*User, error) {
    query := `
        SELECT id, created_at, name, email, password_hash, activated, version
        FROM users
        WHERE id = $1`

    var user User

    ctx, cancel := context.WithTimeout(context.Background(), 3*time.Second)
    defer cancel()

    err := m.DB.QueryRowContext(ctx, query, id).Scan(
        &user.ID,
```
```