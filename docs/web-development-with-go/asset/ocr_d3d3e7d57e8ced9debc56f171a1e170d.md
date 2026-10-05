# 11.8.2 Restricting page access

Next we need to write some code to restrict a user's access when they try to visit pages and Long term we will want to redirect them to the login page when this happens, but for now we are going to do this by showing an error message so that we can verify our code is working as expected.

As luck would have it, our cookie test already has about half of the code we are going to need to do this. In the CookieTest method we already handle reading a cookie and checking for errors, so the first thing we want to do is update this code to read the new remember token we created.

Open the users controller and head to the cookie test method.

```
$ atom controllers/users.go
```

Update the CookieTest method to read the "cookie_test" cookie instead of the "email" cookie.

```
func (u *Users) CookieTest(w http.ResponseWriter, r *http.Request) {
	cookie, err := r.Cookie("remember_token")
	if err != nil {
		http.Error(w, err.Error(), http.StatusInternalServerError)
		return
	}
}
```

Next we are going to use this cookie's value to search for a user in our database. To do this, we will use the us field of our users controller, which is a User instance. We will be using the ByRemember method on the user service that we wrote earlier in this chapter.

Add this code after the cookie is retrieved and the error is checked. In short, add it right below the code we just wrote.