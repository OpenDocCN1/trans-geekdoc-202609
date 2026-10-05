# 12.2. THE USERDB INTERFACE

Our last step in this section is to add the third and final layer, the validation layer. For now this won't actually do much, but we are going to add it to so that when we start adding validation code we have a proper place to put it.

The source code for this is going to look very similar to one of the examples we discussed earlier in this chapter but didn't actually code. It will be an unexported type named `userValidator`, and it will start off with a single embedded field of the UserDB.

```
// userValidator is our validation layer that validates
// and normalizes data before passing it on to the next
// UserDB in our interface chain.
type userValidator struct {
  UserDB
}
```

As we add validation and normalization code to our application we will add it to this type by defining any necessary UserDB methods and adding the validation code before we perform our interface chaining to the underlying UserDB. For example, we might validate an ID with the code below.

```
func (uv *userValidator) ByID(id uint) (*User, error) {
  // Validate the ID
  if id < 0 {
    return nil, errors.New("Invalid ID")
  }
  // If it is valid, call the next method in the chain and
  // return its results.
  return uv.UserDB.ByID(id)
}
```

> Note: You DO NOT need to write this code, as we will be covering it in a later section. It is simply meant as an example of where we are going.

By doing this we can validate data before the next UserDB ever gets called, meaning we can validate data before our userGorm methods ever start to interact with our database.