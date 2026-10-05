```
import (
  "strings"
  // ... the rest of these stay the same
)
```

Next we need to add our normalization function that uses the strings package to manipulate a user's email address. We can't really run into errors here, so the code ends up being pretty short.

```
func (uv *Validator) normalizeEmail(user *User) error {
  user.Email = strings.ToLower(user.Email)
  user.Email = strings.TrimSpace(user.Email)
  return nil
}
```

Our last step is to find any functions that need this validation and add it. The easiest way to do this is to walk over all the functions in our UserDB and ask ourselves if each one needs this validation. Looking over those methods, it looks like the only three that will need this are ByEmail, Create, and Update.

ByEmail needs this normalization so that we don't accidentally search for email addresses that haven't been normalized. We know that all of the email addresses stored in our database is going to be lowercase, there is no guarantee that users will use lowercase when logging in to their account.

Create and Update both need this normalization because each of these could be to change a user's email address, and we need to verify it is normalized before we store it in our database.

Let's start with the ByEmail method. The Validator doesn't have this method yet, so we need to add it. We also need to create a User object and set the email address so our normalizer has a user to operate on.