# 17.5. RESETTING PASSWORDS

```
// ResetPw displays the reset password form and has a method
// so that we can prefill the form data with a token provided
// via the URL query params.
//
// GET /reset
func (u *Users) ResetPw(w http.ResponseWriter, r *http.Request) {
	var views ViewsData
	var form ResetPwForm
	view.Yield = &form
	if err := parseURLParams(r, &form); err != nil {
		dviews.SetAlert(err)
	}
	u.ResetPwView.Render(w, r, views)
}
```

The final function we are going to add to our users controller will be used to process the reset password form.

```
// CompleteReset processed the reset password form
// POST /reset
func (u *Users) CompleteReset(w http.ResponseWriter, r *http.Request) {
	var views ViewsData
	var form ResetPwForm
	view.Yield = &form
	if err := parseForm(r, &form); err != nil {
		dviews.SetAlert(err)
	}	u.ResetPwView.Render(w, r, views)
	return
}

user, err := u.us.CompleteReset(form.Token, form.Password)
tif err != nil {
		dviews.SetAlert(err)
	u.ResetPwView.Render(w, r, views)
	return
}

u.signIn(w, user)
tviews.RedirectAlert(w, r, "/galleries", http.StatusFound, views.Alert({
	Level: views.AlertLevelSuccess,
	Message: "Your password has been reset and you have been logged in!"
}))
}
```

In CompleteReset we first parse the form to get the token and new password.