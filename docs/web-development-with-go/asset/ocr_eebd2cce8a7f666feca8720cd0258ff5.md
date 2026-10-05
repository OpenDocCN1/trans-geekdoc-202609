```
// Errors are the same as ByEmail.
func (us *UserService) ByRemember(token string) (*User, error) {
    var user User
    rememberHash := us.hmac.Hash(token)
    err := first(us.db.Where("remember_hash = ?", rememberHash), &user)
    if err != nil {
        return nil, err
    }
    return &user, nil
}
```

Note: It might seem a little odd that we are using remember_hash in our Where() method, GORM uses the snake case^14 of all fields when creating the columns in the database tables, so this is indeed the correct name to use.

We are returning the same errors as ByEmail because we are using the same first function. This makes it easy for us to return errors like ErrNotFound when a record isn't found, making it clear to users of the Remember method that we didn't run into an error but were simply unable to find a user with that remember token.

# 11.7.6 Resetting our DB and testing

The final piece of our puzzle is a test. This won't be a traditional test file, but we need to at least verify that our code works as intended.

While doing this we are also going to reset our database using the DestructiveReset method, as any existing users will not have a valid RememberHash field and we haven't created a migration to handle this. Since our users are pretty useless without this field, it is simpler to reset the database and start from scratch.

Note: If you forget to do this, you will probably see the following message in your logs:

> ^14https://en.wikipedia.org/wiki/Snake_case