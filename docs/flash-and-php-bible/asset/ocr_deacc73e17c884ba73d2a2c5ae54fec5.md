# Building a User Login Component in Flash

Now that the video player is pretty much packed full of features, it is pretty safe to assume the Web site should require registration in order to use the player. Adding the registration is a matter of creating a basic form and updating a database table, nothing that a few lines of code can't accomplish.

The more advanced portion of this feature is Flash's need to interact with the user login. To start, the Flash application needs to display a login pane when the application starts and also needs to disable the interface until the user successfully logs in.

Keeping with the idea of making the code reusable, let's develop the login component in a new Flash file and then simply drop it in place when it is completed.

Start by opening the login component starter file, which already has the design completed for you, as shown in Figure 17.5. All you need to be concerned with is the code behind the login component.

# FIGURE 17.5

The login component that has been previously designed

![](bbox=[0.115, 0.465, 0.55, 0.745])

When the component is open you will notice the MovieClip in the library is assigned to a class with a name of LoginWindow. You cannot customize that class so you need to create a new ActionScript file and save it in the project folder with the FLA.