686

# CHAPTER 17. FILLING IN THE GAPS

we will explore how to do that in the next section where we will be implementing the password reset feature.

To verify your code is working, visit the following URL and see if the email address field is automatically populated by your signup form:

[localhost:3000/signup?email=michael%40dundermifflin.com]http://localhost:3000/signup

# Source code

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/17.4

Changes - book.usegolang.com/17.4-diff

# 17.5 Resetting passwords

We want users to be able to reset their password if they forget it. To do this, we are going to implement the following workflow:

+   1. Visit a page and submit the email address associated with the account they forgot the password to.
2. If we find a user with that email address, we will create a password reset token and email it to the account's email address. It is important that we don't display this token in the browser or send it to another email address otherwise we might let attackers get into someone else’s account.
3. The user would then visit their email and find the token, along with a link to our password reset form.