# The Presentation Layer

In the presentation layer we'll build an HTML class to generate forms, to display the form, to create tables, and so on. This will be a highly generic class that will grow a lot as we create new applications requiring new presentation features. The data presentation component will have methods to display the poll form, to show the results, and to create forms. This class will be a client to the HTML class: the idea is that no HTML code at all will be present in the data presentation class (only calls to the HTML class are used).

# The Classic Multi-Tiered Architecture

Let's take a look at what happens if we design and create our poll application using this architecture. First, we can see here that we have a strong separation between the content layer, the logic layer, and the presentation layer. We also achieved independence of the database using the DB abstraction class and independence of the presentation language using the HTML class. Let's see what happens if we have to modify the application.

# Case 1: The Poll Result Display Changes

We used a table showing the options, the number of votes, and the results. The designers decide they now want to display a graphical representation of the percentage of votes in each option.

Using this architecture, we just modify the data presentation layer to use functions in the HTML class that create graphical bars. If we do not have that functionality in the HTML class then we would have to create it. However, there might be other applications using graphical bars that will be favored by this code that they can later reuse the functions. As we can see, no change at all is needed in the logic layer. Presentation and logic are therefore independent.

# Case 2: Prevent the User from Voting Multiple Times

This will imply a change to the logic. We can use cookies to prevent users for voting twice in the same poll. Advanced users can delete the cookies but we can live with that. Once this is decided, we just add the use of cookies and the controls to the logic layer of our application. These changes will not impact on the content or presentation layers.

# Case 3: A Flash Version

The design team strikes again: they now want to present the whole application using nice Flash animations with sound, graphics, and dancing bears. Then we can just create a Flash class that will have the same interface as the HTML class and implement each method of the HTML class using PHP Flash functions. We do not have to change anything else there, but we have a Flash polls application. See Chapter 25 for examples of PHP's Flash functions.