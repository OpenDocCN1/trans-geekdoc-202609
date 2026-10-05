# 9.7. CONNECTING THE USER SERVICE AND CONTROLLER

Completed - book.usegolang.com/9.6

Changes - book.usegolang.com/9.6-diff

# 9.7 Connecting the user service and controller

The user model wouldn't be very helpful unless we actually utilized it in our code, so that last thing we are going to cover in this chapter is how to use our user service inside of our users controller. Afterwards, when we submit the sign up form it will interact with our database using our user service. We still won't be validating our users, displaying useful error messages, hashing passwords correctly, or really anything that we need to do truly create a user resource, but those come later once we have all the major pieces connected.

We will complete this code in roughly 3 steps:

+   1. Update the forms to take the name field into account.

+   2. Update our main.go source file to construct a database connection string and set up a new user service.

+   3. Update the users controller to accept a user service in its constructor and utilize it in the Create method.

We will cover each of these in subsections below.

# 9.7.1 Adding the name field the sign up form

Our sign up form doesn't have any notion of a user's name, so we need to first add that to the HTML form.