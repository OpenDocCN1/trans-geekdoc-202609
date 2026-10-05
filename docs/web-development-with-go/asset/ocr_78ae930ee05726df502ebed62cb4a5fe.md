# 7.3. CREATING OUR FIRST CONTROLLER

| Listing 7.16: Updating the router |
| r.HandleFunc("/signup", usersC.New) |

It is important that you **do not** add parenthesis after “New”. Your editor may try to autocomplete and add these for thinking that you are calling this method, but that is not what we want. Rather than calling the *New* method, we are instead passing this method itself as an argument to the `HandleFunc` function call.

At this point your program should start compiling again and will work much like it did before we introduced the users controllers.

By changing the last argument in the call to `HandleFunc` we have instructed our router that we want it to use the *New* method to handle any web requests for the page `/signup`. Because this method matches the definition of a HandlerFunc our program will accept it happily. It doesn't matter to our router that All that matters is that the *New* method will accept two arguments of the type `ResponseWriter` and Request.

While it may not matter to our router that this is a method, it is very important to us because it means our *New* method has access to any data stored on the **Users** type, such as the `NewView` we setup earlier.

We are now ready to stop and restart your program if you haven't already. Make sure everything is compiling correctly and that all of our pages are working. We still won't be able to submit our sign up form, but the form should render correctly again.

# Source code

The links below have the completed source code and a diff of all the code changed in this section.