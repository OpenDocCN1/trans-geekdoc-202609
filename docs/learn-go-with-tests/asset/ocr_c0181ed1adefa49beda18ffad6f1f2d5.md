Recapping what the handler from earlier does:

+   1. Write HTTP responses, send headers, status codes, etc.
+   2. Decode the request's body into a `User`
+   3. Connect to a database (and all the details around that)
+   4. Query the database and applying some business logic depending on the result
+   5. Generate a password
+   6. Insert a record

Taking the idea of a more ideal separation of concerns I'd want it to be more like:

+   1. Decode the request's body into a `User`
+   2. Call a `UserService.Register(user)` (this is our `ServiceThing`)
+   3. If there's an error act on it (the example always sends a `400 BadRequest` which I don't think is right), I'll just have a catch-all handler of a `500 Internal Server Error` for now. I must stress that returning `500` for all errors makes for a terrible API! Later on we can make the error handling more sophisticated, perhaps with error types.
+   4. If there's no error, `201 Created` with the ID as the response body (again for terseness/laziness)

For the sake of brevity I won't go over the usual TDD process, check all the other chapters for examples.

# New design

```
type UserService interface {
    Register(user User) (insertedID string, err error)
}
```

```
type UserServer struct {
    service UserService
}
```

```
func NewUserServer(service UserService) *UserServer {
```