# Chapter 2

# Exploring Symfony's Code

At first glance, the code behind a symfony-driven application can seem quite daunting. It consists of many directories and scripts, and the files are a mix of PHP classes, HTML, and even an intermingling of the two. You'll also see references to classes that are otherwise nowhere to be found within the application folder, and the directory depth stretches to six levels. But once you understand the reason behind all of this seeming complexity, you'll suddenly feel like it's so natural that you wouldn't trade the symfony application structure for any other. This chapter explains away that intimidated feeling.

# The MVC Pattern

Symfony is based on the classic web design pattern known as the MVC architecture, which consists of three levels:

+   - The Model represents the information on which the application operates—its business logic.
+   - The View renders the model into a web page suitable for interaction with the user.
+   - The Controller responds to user actions and invokes changes on the model or view as appropriate.

Figure 2-1 illustrates the MVC pattern.

The MVC architecture separates the business logic (model) and the presentation (view), resulting in greater maintainability. For instance, if your application should run on both standard web browsers and handheld devices, you just need a new view; you can keep the original controller and model. The controller helps to hide the detail of the protocol used for the request (HTTP, console mode, mail, and so on) from the model and the view. And the model abstracts the logic of the data, which makes the view and the action independent of, for instance, the type of database used by the application.

Figure 2-1 - The MVC pattern