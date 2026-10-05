We are going to be creating a new type for our users controller. How you name this is up to you, but I prefer to use a name like Users because it will often be referred to in other code as controllers.Users, making it clear that this is the users controller.

We don't really know what our users controller is going to need just yet, so we will start out with an empty struct as the type. The code is shown in Listing 7.11.

# Listing 7.11: Creating the Users controller type

```
package controllers
type Users struct {
```

That's it. We now have a Users controller available to use in our code, and we are ready to start adding views and any other relevant fields to it.

# Source code

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/7.3.1

# 7.3.2 Moving the sign up page code

We already have most of the sign up page created, but in this section we are going to migrate that page from our main.go source file into our users controller. It will become part of the users controller because submitting the form