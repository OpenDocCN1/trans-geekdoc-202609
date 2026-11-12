made more complex, so you should have no problems adding further methods to it.

# How do I build an online calendar?

Now that the DateMath class is ready, I have a couple of methods that will help us build a calendar. Aside from the specific date-related issues that DateMath solves, the hard part is to build an online calendar that suits everybody. If one site needs a calendar as HTML, but another needs WML (wireless markup language), we have a problem. The trick to solving this problem is to separate the building of the calendar’s “data structures” from the rendering of output.

To cut a long story short, in top cooking program style it’s time to say that magic phrase, “Here’s one I prepared earlier!” as I introduce a collection of classes that can help build calendar data structures. Once we’ve got a grasp on these, we’ll use them to build our calendar.

As shown in the UML diagram in Figure 6.1, all the classes in this example inherit a great deal of functionality from the Calendar base class.