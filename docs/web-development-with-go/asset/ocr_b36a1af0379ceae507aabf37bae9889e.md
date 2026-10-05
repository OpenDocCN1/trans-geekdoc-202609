# 12.3. THE USERSERVICE INTERFACE

# 12.3 The UserService interface

In this section we are going to transform our UserService into an interface. While this step isn’t completely necessary for our code, it is a step I like to take because it allows for more flexibility in our code much like our UserDB interface offers. For example, it can make testing much simpler in the long term.

To do this, we are going to first declare the UserService interface. After that, we will rename our existing UserService struct type to userService. Notice that this name is nearly identical, the first letter is lowercase. This means that this type won’t be exported, and more importantly it is different from our UserService, so we are allowed to use both as unique type names in our code.

> Note: You do not need to name this userService, and could really name anything you want. We are just doing it to make it clear what interface this type implements.

Open up your models source code.

```
$ atom models/users.go
```

We will start with the UserService interface declaration. This just defines methods we will be offering, so we will need the Authenticate method as well as all the methods offered by the UserDB interface.

```
// UserService is a set of methods used to manipulate and
// work with the user model
type UserService interface {
// Authenticate will verify the provided email address and
// password are correct. If they are correct, the user
// corresponding to that email will be returned. Otherwise
// You will receive either:
// ErrorFound, InvalidPassword, or another error if
// something goes wrong
Authenticate(email, password string) (+User, error)
UserDB
}
```