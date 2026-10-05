# 10.4. IMPLEMENTING PASSWORD HASHING FOR OUR USERS 255

Bcrypt is a hashing package that is part of the Go project, but is maintained outside of the standard library. The primary reasons for this is to allow the developers to maintain them under a looser set of guidelines. For example, the Go standard library ensures backwards compatibility with all API changes, where libraries under the /x/ path might make breaking changes when a new major version is released.

You can check out bcrypt's docs here: https://godoc.org/golang.org/x/crypto/bcrypt

The primary functions we will be using in this package are:

+   * GenerateFromPassword 1
* CompareHashAndPassword 2

The first is used to generate a password hash from an raw user password, and the second is used to compare a user-provided password with a hash we have stored to verify whether or not they match.

We are going to be using bcrypt inside of our users model, so we can start by opening up that source code.

```
$ atom models/users.go
```

We can't use the bcrypt package without first importing it...

```
import (
  "errors"

  "github.com/jinzhu/gorm"
  _ "github.com/jinzhu/gorm/dialects/postgres"
  "golang.org/x/crypto/bcrypt"
)
```

> 1https://godoc.org/golang.org/x/crypto/bcrypt#GenerateFromPassword
2https://godoc.org/golang.org/x/crypto/bcrypt#CompareHashAndPassword