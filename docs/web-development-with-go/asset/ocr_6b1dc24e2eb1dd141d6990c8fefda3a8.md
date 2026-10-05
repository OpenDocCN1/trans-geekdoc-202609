Completed - book.usegolang.com/11.7.1

Changes - book.usegolang.com/11.7.1-diff

# 11.7.2 Setting remember token when a user is created

Now that the RememberHash field is required for every user we need to update our code to set a remember token when users are created. Without this, we wouldn't be able to create users without manually setting a remember hash which is a pretty poor experience.

We are going to update our user service to automatically set the remember token whenever a user is created, and then later we will update our code to hash a remember token if it is set and store this in the user's RememberHash field, making it easy to update this field without knowing any of the specifics about how it is hashed.

Once again we will be working inside the users model source file.

```
$ atom models/users.go
```

The first thing we need to add is an import for the rand package we created earlier.

```
import (
  "errors"

  // This is the only new import
  "lenslocked.com/rand"

  "github.com/jinzhu/gorm"
  "github.com/jinzhu/gorm/dialects/postgres"
  "golang.org/x/crypto/bcrypt"
)
```