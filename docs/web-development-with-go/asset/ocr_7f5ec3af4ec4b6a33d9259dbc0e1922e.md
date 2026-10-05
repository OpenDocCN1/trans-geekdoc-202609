# Chapter 17

# Filling in the gaps

The final chapter of the book is going to be a bit different than the previous chapters, as most of the code we will be looking at involves adding optional features that could be implemented in a variety of ways.

For instance, when we start to look at sending emails we will be using Mailgun to send them, but there are plenty of other emailing services out there and in some companies they will have their own internal solution. Regardless, it is still useful to see an example of how you might send emails to users.

# 17.1 Deleting cookies and logging out users

Our users are likely going to want a way to sign out at some point, let’s look at how to implement that feature.

Creating a sign out link will entail roughly two major steps:

+   1. Adding a button to sign out to the navigation bar whenever a user is signed in.