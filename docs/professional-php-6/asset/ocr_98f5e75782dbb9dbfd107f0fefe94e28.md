+   6. The .php file then includes the appropriate .phtml file, which effectively takes over execution.

+   7. The .phtml file recurses that supervariable, displaying it in whatever form is appropriate, and rendering whatever new user input components are required, such that the user is presented with the finished Web page.

This may sound more complex than it actually is; in fact, it is a remarkably simple process. You’ll see some examples later in this chapter showing how this native templating is best implemented. For now, you’ll take a look at a few toolkit classes that can help you in the quest to use an MVC design pattern in PHP by vastly simplifying some of the steps set out previously.

Later in this chapter, you’ll learn how this toolkit integrates neatly with the native templating techniques just discussed.

# The MVC Mini Toolkit

The mini toolkit you are about to meet makes sticking to an MVC design pattern a whole lot easier. The toolkit concerns itself only with the controller element of the MVC trio. You’ve already looked at the model side of things in Chapter 7. Later you’ll meet an off-the-shelf PEAR package called Smarty that allows for an effective implementation of the view components.

# Introducing the Toolkit

The mini toolkit enables you to handle the connection between view and model in a consistent, clean, and clear manner. The core of this is a request object that seeks to provide a more object-oriented perspective on the user’s input into your application. As well as sporting the usual means for interrogating the user’s input directly, it supports the concept of applying constraints to each parameter, such that you may easily specify in your code what you are and are not prepared to accept.

Such error-checking practices are almost certainly not new to you, of course. However, the concept of constraints enables you to separate the view and model by providing a universal approach to your controller development. Because the model may now assume that its input is within expected parameters, you can divorce cleanly such code from methods within the model, safe in the knowledge that it has been vetted by the controllers of your MVC design pattern.

This is an entirely appropriate approach. After all, sanity checks are not core to your model’s functionality. By leaving responsibility for such checks well outside the model itself, you can also apply different rules for different controllers and different views talking to the same model. This is very much in keeping with the philosophy behind MVC.

You may want to extend or modify these classes to suit your own needs better. What is provided here is a very basic implementation. For example, you may want to examine the feasibility of adding methods to automatically perpetuate GET and POST variables using hidden form parameters, without having to turn to session variables. This may prove useful for the purposes of pagination forward and backward through a data set of search results, maintaining those search criteria with each request for a new page. Such functionality could easily be integrated into the request object itself. In Chapter 14, you’ll meet a number of PHP frameworks that have already done just that.