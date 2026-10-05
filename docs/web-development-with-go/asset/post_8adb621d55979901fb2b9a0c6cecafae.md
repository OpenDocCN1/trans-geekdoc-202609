
## 13.6. WHITE-LISTING ERROR MESSAGES

Now when we write an error message like "models: email is taken" it will be turned into "Email is taken" via the Public method.

We need to update all of our errors that are intended to be public, so we are going to replace all of our existing errors with ones of the new modelError type, and because we made the underlying type of our modelError string we can define these as constants instead of variables.

```go
const (
// The comments for each error should remain unchanged.
// They are excluded here for brevity.
ErrNotFound modelError = "models: resource not found"
ErrIDInvalid modelError = "models: ID provided was invalid"
ErrPasswordIncorrect modelError = "models: incorrect " + 
"provided"
ErrPasswordTooShort modelError = "models: password must " + 
"be at least 8 characters long"
ErrPasswordRequired modelError = "models: password is required"
ErrEmailRequired modelError = "models: email address is " + 
"required"
ErrEmailInvalid modelError = "models: email address is " + 
"not valid"
ErrEmailTaken modelError = "models: email address is " + 
"already taken"
ErrRememberRequired modelError = "models: remember token " + 
"is required"
ErrRememberTooShort modelError = "models: remember token " + 
"must be at least 32 bytes"
)
```

Now we are finally ready to update our users controller to use the new SetAlert method.

## CHAPTER 13. DISPLAYING ERRORS TO THE END USER

```bash
$ atom controllers/users.go
```

Find the two places where we create an alert and replace them with a call to the
SetAlert method. We can also get rid of the code that logs the error message as
our SetAlert method handles that.

```go
func (u *Users) Create(w http.ResponseWriter, r *http.Request) {
	var vd views.Data
	var form SignupForm
	if err := parseForm(r, &form); err != nil {
		vd.SetAlert(err)
		u.NewView.Render(w, vd)
		return
	}
	user := models.User{
		Name: form.Name,
		Email: form.Email,
		Password: form.Password,
	}
	if err := u.us.Create(&user); err != nil {
		vd.SetAlert(err)
		u.NewView.Render(w, vd)
		return
	}

	err := u.signIn(w, &user)
	if err != nil {
		http.Redirect(w, r, "/login", http.StatusFound)
		return
	}
	http.Redirect(w, r, "/codietest", http.StatusFound)
}
```

Restart your server and verify that your new errors are working. You should
be seeing specific error messages when your password is too short, an email
address is taken, or any other time a validation fails, and each of those
have a capitalized first letter and the “models:” prefix should be removed.

Box 13.5. Interfaces can be defined anywhere

## 13.7. HANDLING LOGIN ERRORS

> One worth noting with our PublicError interface is that our modelError type inside the models package never directly sees or interacts with the type. It is possible to implement an interface in Go without ever importing or using the interface directly. This is a very big difference from other languages like Java where you have to explicitly state “this class implements interface X”, but it is also a very powerful feature of Go.

## Source code

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/13.6

Changes - book.usegolang.com/13.6-diff

## 13.7 Handling login errors

Next on our agenda is to address how we are handling errors that occur when logging users via the Login action inside our users controller. Open your users controller source file and find the Login method.

```bash
$ atom controllers/users.go
```

The first error we need to address is one we saw in the Create method; whenever we fail to parse a form we need to render the login form again along with an alert explaining that something went wrong.

```go
func (u *Users) Login(w http.ResponseWriter, r *http.Request) {
	var vd Data
	var form LoginForm
	if err := parseForm(r, &form); err != nil {
		vd.SetAlert(err)
		u.LoginView.Render(w, vd)
		return
	}
	// ... the rest of the code stays the same
}
```

After that we need to look at any errors returned when we attempt to Authenticate the user's email address and password. While it is tempting to just call the SetAlert method with any errors, we are still going to write a custom message for the ErrNotFound, as this error isn't as clear as telling the user the error provided didn't match any users.

We can get rid of the ErrIncorrect error so our switch statement will get a bit smaller, and regardless of which error we see we want to render the LoginView again returning.

```go
user, err := u.us.Authenticate(form.Email, form.Password)
if err != nil {
	switch err {
		case models.ErrNotFound:
			vd.Alert = views.Alert(
				tLevel: views.AlertLvlError,
				Message: "No user exists with that email address",
			)
		case default:
			vd.SetAlert(err)
	}
	u.LoginView.Render(w, vd)
	return
}
```

The last error we need to handle is the one returned by the signIn method. When we get an error here we want to render the login page again so the user can try logging in again.

```go
err = u.signIn(w, user)
if err != nil {
	vd.SetAlert(err)
	u.LoginView.Render(w, vd)
	return
}
http.Redirect(w, r, "/cookiest", http.StatusFound)
```

With that we are handling errors in our Login method. The last bit of code we are going to write is entirely optional, but is intended to make it easier to generate Alerts moving forward.

We saw in our switch statement earlier that when we want to write a custom error message we can't use the SetAlert method, and instead need to manually construct the Alert object. There is nothing wrong with this, but you can also write a method to simplify this if you prefer.

```bash
$ atom views/data.go
```

```go
func (d *Data) AlertError(msg string) {
	d.Alert = &Alert{
		Level: AlertLvlError,
		Message: msg,
	}
}
```

We can update the switch statement inside of our Login method to use the AlertError method instead of building the alert manually.

```go
user, err := u.us.Authenticate(form.Email, form.Password)
if err != nil {
	switch err {
	case models.ErrNotFound:
		vd.AlertError("No user exists with that email address")
	default:
		vd.SetAlert(err)
	}
```

```go
	u.LoginView.Render(w, vd)
	return
}
```

While this actually resulted in more code now, it will eventually end up saving us code later if we find ourselves writing custom alert messages in different controllers.

## Source code

The links below have the completed source code and a diff of all the code changed in this section. 

Completed - book.usegolang.com/13.7

Changes - book.usegolang.com/13.7-diff

## 13.8 Recovering from view errors

The final class of errors we need to address is one we have been ignoring a bit; whenever we attempt to render our templates it is possible to run into an error. This could occur for any number of reasons, such as attempting to access data that wasn't provided or calling a function that ends up returning an.

Unfortunately there isn't a great way to handle errors like this. As soon as we start writing to ResponseWriter the 200 status code is set and any data that has already been written can't be taken back. That basically leaves us with two options:

- 1. Try to insert an error message in the middle of the page when ourtemplate errors.
- 2. Execute the entire template into a temporary buffer, then copy it to the ResponseWriter we know has executed correctly.

The first option uses less memory and can be faster when shaving every millisecond matters, but for most web applications this isn’t important. The memory footprint is relatively.

We will be going with the second option because it won’t slow down our application noticeably, and it provides a much better user experience. Rather than ending up with a half-rendered page users will get a clear error page, and we will also have a chance to set the proper status code.

We will be working inside the views package to implement these changes.

```bash
$ atom views/view.go
```

The first thing we are going to change is the Render method’s return type. We currently have it returning an error whenever we run into one executing our templates, leaving the error handling up to whoever called the Render method. Moving forward we are going to handle those errors inside the Render method, so we do not have to return an.

> Note: If you want to continue returning errors so you can track when errors occur you can, but we won’t be doing that in this course.

```go
func (v *View) Render(w http.ResponseWriter, data interface{}) {
	// .. . we will edit the internals of this method shortly
}
```

After we need to skip down to the return statement where we execute our template. We are going to start off by creating a Buffer, a type that comes from the bytes package.
