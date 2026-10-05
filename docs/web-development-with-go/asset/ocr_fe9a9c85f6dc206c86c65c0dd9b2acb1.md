# CHAPTER 17. FILLING IN THE GAPS

the text, “Remember your password?” This is handy for users who accidentally navigate to this page or suddenly remember their password.

We will be adding links like this to all of our authentication forms, and all will be placed inside a panel-footer, but the text and where they link will change based on what makes the most sense for that particular form. For instance, we will add a link to the forgot password form from the login page.

```
$ atom views/users/login.gohtml
```

Add the following footer below the panel-body section.

```
<div class="panel-footer">
  <a href="forgot">Forgot your password?</a>
</div>
```

When a user is logging an account it is likely that is when they will realize they forgot their password, so it is the most logical place to put a link to the forgot password page.

Similarly, when a user is creating an account they might realize they already have an account and need a link to the log in the page.

```
$ atom views/users/new.gohtml
```

Again again, the HTML below will go after the panel-body section.

```
<div class="panel-footer">
  <a href="login">Already have an account?</a>
</div>
```

Finally, we need to create the form for when a user is resetting their password and already has a reset token.