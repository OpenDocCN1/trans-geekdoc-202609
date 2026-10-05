```
// If the email and password are both valid, this will return
// user, nil
// Otherwise if another error is encountered this will return
// nil, error
func (us *UserService) Authenticate(
    email, password string) (*User, error) {
    // we will implement this in a moment
    return nil, nil
}
```

In every case except the very last one we will be returning an error defined by our models package. This is important because every case besides the last are use cases where we should be able to handle the error and render an appropriate error message to our end user, but in the last case we might not be able to render a useful error for the end user and instead need to interact with see what is wrong with our web application. For example, it might be experiencing an error because the database crashed.

Now that we have a rough understanding of what we want Authenticate method to do we will implement it. We will start by looking up a user with the provided email address.

```
foundUser, err := us.ByEmail(email)
if err != nil {
    return nil, err
}
```

If you recall from earlier, when a user isn't found with the email address our ByEmail method will return the ErrNotFound error, so we don't need to actually check for that error in our code. We can simply return whatever error is returned by the ByEmail method.

Assuming we retrieve a user without any problems, our next step is to see if the provided password is correct. We will be using bcrypt to decrypt this, using its CompareHashAndPassword function.

> ^4https://godoc.golang.org/x/crypto/bcrypt#CompareHashAndPassword