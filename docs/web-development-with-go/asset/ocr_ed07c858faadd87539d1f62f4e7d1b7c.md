# Source code

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/11.7.2

Changes - book.usegolang.com/11.7.2-diff

# 11.7.3 Adding an HMAC field to the UserService

We will still be working in the users model, so navigate to that source file if it isn’t open already.

```
$ atom models/users.go
```

In order to access the HMAC type we created earlier we will need to import the hash package we created, so let’s start there.

```
import (
  "errors"

  "lenslocked.com/hash"
  "lenslocked.com/rand"

  "github.com/jinzhu/gorm"
  "github.com/jinzhu/gorm/dialects/postgres"
)
```

Next we want to add the hmac field to the UserService type. We are going to make this an unexported field because we don’t want it being changed or accessed by any code outside of our models package.