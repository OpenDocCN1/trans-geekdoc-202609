# 11.7. HASHING REMEMBER TOKENS IN THE USER SERVICE

With that last code change we are ready to start persisting remember tokens, but before we can make much use of them we need to write a function that allows us to lookup a user based on their remember token.

# Source code

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/11.7.4

Changes - book.usegolang.com/11.7.4-diff

# 11.7.5 Retrieving a user by remember token

We are still working in the users model, so make sure you have it open.

```
$ atom models/users.go
```

The next piece of code we are going to write is a new method on the UserService that allows us to pass in a raw remember token, and then returns either a user that has remember token or an error. In order for this to work, our method is going to need to first hash the raw remember token so that it matches what we store in our database, and then query the database for a user with remember token hash.

We have already seen how to do each of these individual pieces, so that all is left is to put them all together.

```
// ByRemember looks up a user with the given remember token
// and returns that user. This method will handle hashing
// the token for us.
```