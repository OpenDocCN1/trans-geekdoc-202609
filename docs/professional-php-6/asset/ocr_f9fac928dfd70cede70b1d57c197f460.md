# # Widgets

Continuing with the previous example, you’ll use the observer pattern to handle displaying price information for some of the instruments within graphical elements on a Web page. First, you must define some simple graphical components. These components will be basic HTML table structures whose functionality will be contained within an object. Such components are often referred to using the all-purpose term of _widgets_.

The widgets must display the same instrument information. For this example, that information is just the instrument’s name and price.

# ## Designing the Widgets

A graphical widget will have two responsibilities. It needs to draw its own HTML so that it can be seen on a Web page, and it needs to update the data it displays. You may have noticed (from Figure 4-7) that an `Update` method is defined in the `Observer` interface.

Each widget is an `Observer`. The item being observed is the data representing the instrument name and price information. The data source is `Observable`.

All widgets, then, should implement the `Observer` interface. In addition, each one should descend from an abstract class that defines some shared functionality between widget objects. This is an example of using interfaces and abstract classes together. Because the `update()` method is the same for all widgets, it can be implemented in the `abstract` class. The class diagram is shown in Figure 4-8.

![](bbox=[0.347, 0.51, 0.555, 0.835])