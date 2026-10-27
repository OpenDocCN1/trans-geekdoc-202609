# The Design Pattern of Model_View_Controller

The design pattern of MVC (design view controller) denotes three separate regions in a software architecture's domain model, presentation, and actions based on user input:

# *Model*

The underlying data's model is actually the data's structure.. The model is in control of the application domain's behavior and data.

# *View*

The View is a representation of what the user or consumer sees graphically. The View is a graphical representation of the model that defines how data is displayed by enquiring about the current state of the Model.

# *Controller*

The Controller component is in charge of processing data in response to user input. The Controller issues command to the Model that causes it to change its state.

When these three facets are separated, loose coupling is simple to design, as the controller can communicate with a wide variety of Model and View components. The Model is accessed by the View as well as the Controller. By contrast, a Model is completely independent of both the View and the Controller. Separation has a number of advantages, one of which is the ability to maintain a separate relationship. Because of this separation, The model may be generated and tested as a part of the visual display.

There are various popular and high-quality MVC frameworks available for PHP, each with their own set of advantages and disadvantages to consider. To avoid unnecessary complexity, we will not study any existing frameworks at this time; instead, we will create our own unique MVC framework. As you may recall, we have already created our restaurant carte management application's data model, which is contained in the CarteModel.PHP file and consists of the base Carte Class, the CarteProduct class, DBMapper is a subclass of Carte that extends the basic class, and all derived sub-Carte classes that also extend the base Carte class. Now we're going to wrap everything up in a custom MVC framework and add our View and Controller components.

# The MCV URL Structure & URL Mapping

To begin, you're probably familiar with the basic MVC framework URL structure:

```
http://domain/controller/action/id
```