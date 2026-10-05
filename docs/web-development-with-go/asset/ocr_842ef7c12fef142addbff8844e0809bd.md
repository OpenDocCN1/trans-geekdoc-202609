Completed - book.usegolang.com/11.7.3

Changes - book.usegolang.com/11.7.3-diff

# 11.7.4 Hashing remember tokens on create and update

With all of the pieces put in place, we can now update the Create and Update methods on the UserService to hash a remember token if it is.

Once again we will be working in the users model source file.

```
$ atom models/users.go
```

We will start with the Create method - find the comment we wrote earlier that reads:

```
// TODO: Hash the token and set it on user.RememberHash
```

Replace that comment with the line below.

```
user.RememberHash = us.hmac.Hash(user.Remember)
```

Next is the Update method. We don't want to update the remember hash if the remember token wasn't updated, so we need an if statement in this situation. We don't need this in the Create method because we always create a new remember token when creating a user.

```
func (us *UserService) Update(user *User) error {
	if user.Remember != "" {
	user.RememberHash = us.hmac.Hash(user.Remember)
	}
	return us.db.Save(user).Error
}
```