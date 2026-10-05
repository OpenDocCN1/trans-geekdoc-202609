# 690 CHAPTER 17. FILLING IN THE GAPS

won't cover what it is doing in detail.

Next up is the validation layer. We will start with the pwResetValidator type.

```
import {
  "github.com/jinzhu/gorm"
  "lenslocked.com/hash"
  "lenslocked.com/rand"
}

func pwResetValidator(db pwResetDB, hmac hash.HMAC) +pwResetValidator {
  return &pwResetValidator{
    pwResetDB: db,
    hmac: hmac,
  }
}

tpwResetValidator struct {
  pwResetDB
  hmac hash.HMAC
}
```

We went ahead and added the HMAC here, because we know we will be hashing our tokens before storing them in the database.

Next up are the validation functions we will need.

```
func (pwrv *pwResetValidator) requireUserID(pwr *pwReset) error {
  if pwr.UserID <= 0 {
    return ErrUserIDRequired
  }
  return nil
}

func (pwrv *pwResetValidator) setTokenIfAbsent(pwr *pwReset) error {
  if pwr.Token != "" {
    return nil
  }
  token, err := rand.RememberToken()
  if err != nil {
    return err
  }
  pwr.Token = token
  return nil
}
```