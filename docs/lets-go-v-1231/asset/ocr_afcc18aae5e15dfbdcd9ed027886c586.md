Also update the UserModelInterface interface type to include the PasswordUpdate() method that you've just created.

[Show suggested code]

# ## Step 5

Update the accountPasswordUpdatePost handler so that if the form is valid, it calls the UserModel.PasswordUpdate() method (remember, the user's ID should be in the session data).

In the event of a models.ErrInvalidCredentials error, inform the user that they have entered the wrong value in the currentPassword form field. Otherwise, add a flash message to the user's session saying that their password has been successfully changed and redirect them to their account page.

[Show suggested code]

# ## Step 6

Update the account to include a link to the change password form, similar to this:

![](bbox=[0.112, 0.504, 0.884, 0.908])