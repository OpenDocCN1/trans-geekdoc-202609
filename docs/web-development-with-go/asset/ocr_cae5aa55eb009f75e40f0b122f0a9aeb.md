# 17.5. RESETTING PASSWORDS

+   4. When the user goes to the password reset form we will ideally prefill in the remember token for them using URL query parameters in the URL we give them. The user would then type in a new password and submit the form.

+   5. After submitting the password reset form our server will look up the token and verify it is valid. Our definition of valid for now will be that the token is less than 12 hours old, and it is one we can find in the database. Assuming the token is valid, we would then update the user's password with the new password provided via the reset form.

+   6. Finally, our server would log the user into that account and notify them that the password has been updated.

In order to implement this we need add quite a bit of code to our application. We will need a place to store the password reset tokens, code to verify that they haven't expired, code to email a user their password reset token, and code to render and process the forget password and reset password forms.

While this may feel like a lot at first, most of it will be very similar to code we have already learned about. Rendering forms, for example, is something we have been doing for some time now.

In order to make implementing this a little easier we will be breaking the process into roughly five steps covered in subsections.

# 17.5.1 Creating the database model

Our first step is to focus on creating everything related to the database table where we will store the password reset tokens.

While we could store these as a column in the users table we created earlier, this could become problematic long-term. For starters, we will have extra columns added to every single user in our database that frequently aren't