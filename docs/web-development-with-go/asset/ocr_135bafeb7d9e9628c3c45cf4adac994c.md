```
return nil, ErrInvalidPassword
default:
  return nil, err
}
```

Putting this all together we get the implementation shown in Listing 10.8. I am not showing the comments in the listing for brevity, but you should keep the comments we wrote earlier in this section.

# Listing 10.8: Fully implemented Authenticate method.

```
func (us *UserService) Authenticate(email, password string) (*User, error) {
  foundUser, err := us.ByEmail(email)
  if err != nil {
    return nil, err
  }

  err = bcrypt.CompareHashAndPassword(
    []byte(foundUser.PasswordHash),
    []byte(password-userPwPepper))
  switch err {
  case nil:
    return foundUser, nil
  case bcrypt.ErrMismatchedHashAndAndPassword:
    return nil, ErrInvalidPassword
  default:
    return nil, err
  }
}
```

That's it! We are ready to start using the authenticate method inside of our login action in the users controller.

# Source code

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/10.5.3