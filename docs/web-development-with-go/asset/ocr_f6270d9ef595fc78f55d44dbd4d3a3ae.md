# 17.4. PERSISTING AND PREFILLING FORM DATA

```
<!-- ... -->
</form>
{{end}}
```

Now that our template will take advantage of the additional data we need to update our Create method on the users controller to provide any known data.

```
$ atom controllers/users.go
```

There are a number of ways to implement this, but I personally prefer to set the Yield field of our view data to be a pointer to the SignupForm that we parse.

```
func (u *Users) Create(w http.ResponseWriter, r *http.Request) {
  var vd.Data
  var form SignupForm
  vd.Yield = &form
  if err := parseForm(r, &form); err != nil {
    //
  }
  //...
}
```

Note: If we do not use a pointer here the Yield field will be assigned a copy of the form, so when we then proceed to parse the original form variable we will get updated with new values but the vd. Yield field will not be updated. Using a pointer we ensure that anytime we change the form variable we will also see those changes in the vd. Yield field.

Now we will have all the form data available in our view as long as we pass that vd variable in the data.

To verify that the updated code is working, restart your server and fill out the sign up form with a password that is too short. Your web application should render the sign up form again with an error message, but this time your name and email address fields should retain the information you originally typed in.