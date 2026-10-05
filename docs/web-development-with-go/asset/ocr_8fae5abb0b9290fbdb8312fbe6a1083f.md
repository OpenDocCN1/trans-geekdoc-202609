# 17.5. RESETTING PASSWORDS

```
if duration > twelveHours {
    // ... our duration is over 12 hours, meaning our pwReset
    // was created over 12 hours ago and is invalid
}
```

Putting this all together, we can update our CompleteReset function with the source code below.

```
import (
    // Add this import
    "time"
)

func (us *userService) CompleteReset(token, newPw string) (user, error) {
    pwr, err := us.pwResetDB.ByToken(token)
    if err != nil {
        if err == ErrNotFound {
            return nil, ErrTokenInvalid
        }
        return nil, err
    }
    if time.Now().Sub(pwr.CreatedAt) > (12 * time.Hour) {
        return nil, ErrTokenInvalid
    }
    user, err := us.ByID(pwr.UserID)
    if err != nil {
        return nil, err
    }
    user.Password = newPw
    if err := us.Update(user); err != nil {
        return nil, err
    }
    us.pwResetDB.Delete(pwr.ID)
    return user, nil
}
```

Finally, we need to update the services.go source file's DestructiveReset and AutoMigrate methods so that our pwReset table gets constructed when we call them.