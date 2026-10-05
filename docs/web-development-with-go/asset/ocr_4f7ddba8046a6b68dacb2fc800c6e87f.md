# 17.5. RESETTING PASSWORDS

UserService will handle everything related to a user’s password. This includes reading and writing to the pwReset database table.

Let’s start by adding the methods we ultimately want to implement to our UserService interface.

```
$ atcm models/users.go
```

```
type UserService interface {
    Authenticate(email, password string) (*User, error)
    // InitiateReset will complete all the model-related tasks
    // to start the password reset process for the user with
    // the provided email address. Once completed, it will
    // return the token, or an error if there was one.
    InitiateReset(email string) (string, error)
    // CompleteReset will complete all the model-related tasks
    // to complete the password reset process for the user that
    // the token matches, including updating that user’s pw.
    // If the token expired, or if it is invalid for any
    // other reason the ErrTokenInvalid error will be returned.
    CompleteReset(token, newPw string) (*User, error)
UserDB
}
```

We are adding the methods to the user service because they ultimately relate to the User resource. Users of our models package don’t care about the details of how a password is reset, but instead only care that they can initiate and complete the process.

The first thing we need to implement these two functions is to add a pwResetDB to our UserService type.

```
func NewUserService(db *gorm.DB, pepper, hmacKey string) UserService {
    ug := &userGorm(db)
    hmac := hash.NewHMAC(hmacKey)
    uv := newUserValidator(ug, hmac, pepper)
    return UserService{
        UserDB: ug,
        pepper: pepper,
        pwResetDB: newPwResetValidator(pwResetGorm(db), hmac),
    }
}
```