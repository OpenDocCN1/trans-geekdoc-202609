# CHAPTER 12. NORMALIZING AND VALIDATING DATA

```
ByRemember(token string) (*User, error)

// Methods for altering users
Create(user *User) error
Update(user *User) error
Delete(id uint) error

```

Note: I intend to declare my exported types, especially interfaces, near the top of my source file, but you can put this anywhere in your source file.

The only method we will not be adding to this interface is the Authenticate method, as this does not require direct DB access. Instead it can be built using our UserDB layer to look up the user via their email address, and then verify the user using the hashed password and bcrypt. As a result, it doesn't make sense to add this to the UserDB interface.

We are also going to add some utility methods to our UserDB interface - like the ability to close our UserDB connection, or the ability to automatically migrate the table based on the update User type. While not all of these will stay here forever, it is much easier to make this code change if we include these methods.

```
type UserDB interface {
// ... Keep the existing methods in this interface and add
// the ones below.

// Used to close a DB connection
Close() error

// Migration helpers
AutoMigrate() error
DestructiveReset() error
}
```

Note: We will eventually remove the AutoMigrate and DestructiveReset methods from the UserDB interface when we perform migrations, but for now it simplifies things to keep them here.