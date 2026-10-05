```
if err != nil {
    return err
}
ncookie := http.Cookie{
    Name: "remember_token",
    Value: user.Remember,
}
ttp.SetCookie(w, &cookie)
return nil
```

Next step is to update the log in and sign up methods to call this method after a user successfully creates an account or logs in. We will also go ahead and redirect users to the cookie test page so we can verify a cookie was properly set without having to manually type in the URL.

Updating the Create method is easier as we only need to add some new code and remove the fmt.Fprintln at the end of the method.

```
func (u *Users) Create(w http.ResponseWriter, r *http.Request) {
    // ... This code remains unchanged

    // Delete this line:
    // fmt.Fprintln(w, "User is", user)

    // Add the following at the end of the Create method
    err := u.SignIn(w, &cookie)
    if err != nil {
        // Temporarily, return the error message for debugging
        http.Error(w, err.Error(), http.StatusInternalServerError)
        return
    }
    // Redirect to the cookie test page to test the cookie
    http.Redirect(w, r, "/cookietest", http.StatusFound)
}
```

In the Login method we will need to remove any code used to create a cookie and the print statement at the end of the method. We don’t need to manually create the cookie anymore because it is handled by the signIn method.