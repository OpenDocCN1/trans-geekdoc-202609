# 12.9. VALIDATING AND NORMALIZING REMEMBER TOK 415

```
uv.emailIsAvail)
// ... this is unchanged
}
```

```
func (uv +userValidator) Update(user +User) error {
err := runUserValFns(user,
uv.passwordMinLength,
uv.bcryptPassword,
uv.passwordHashRequired,
uv.rememberBytes,
uv.hashCember,
uv.rememberHashRequired,
uv.normalizeEmail,
uv.requireEmail,
uv.emailFormat,
uv.emailIsAvail)
// ... this is unchanged
}
```

With that are done writing validations for our user resource. We might find later that we need to create more, but this should be good enough for now.

At this point it is advisable to drop your database using the DestructiveReset function within main.go like we have in the past, and then to restart your server. It is very likely that you have invalid data stored in your data that was created before we made these validations, and this could potentially cause issues. Starting from scratch is a much safer option while we are in development.

After that head on to the next chapter where we will learn how to render nice error messages in our UI. This will give our users a much better experience than seeing a white page with a single error message when they try to sign up with an invalid email address.

# Source code

The links below have the completed source code and a diff of all the code changed in this section.