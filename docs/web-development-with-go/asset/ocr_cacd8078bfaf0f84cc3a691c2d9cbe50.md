# CHAPTER 16. DEPLOYING TO PRODUCTION

```
func newUserValidator(udb UserDB, hmac hash.HMAC,
pepper string) *userValidator {
return &userValidator{
UserDB: udb,
hmac: hmac,
pepper: pepper,
mailRegex: regexp.MustCompile(
	`"[a-z0-9\._%%+\-]+@[a-z0-9\-]+\.[a-z]{2,26}\$\`
),
}
```

```
type userValidator struct {
UserDB
hash.HMAC
emailRegex *regexp.Regexp
pepper string
}
```

After that we need to find our authentication code that previously used the pepper constant and replace it with our userService's pepper field.

```
func (us *userService) Authenticate(email,
password string) (*User, error) {
//...
err = bcrypt.CompareHashAndPassword(
[]byte(foundUser.PasswordHash),
// Change this line to be us.pepper
[]byte(password+us.pepper))
//...
}
```

We also need to update the bcryptPassword method provided by out-user.
Validator.

```
func (uv *userValidator) bcryptPassword(user *User) error {
//...
// Change this to be uv.pepper
pwBytes := []byte(user.Password + uv.pepper)
//...
}
```