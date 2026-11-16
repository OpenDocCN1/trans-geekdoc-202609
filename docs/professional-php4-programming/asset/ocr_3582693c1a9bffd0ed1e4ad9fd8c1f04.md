# # User Privilege System

Complex multi-user applications often require that some users (such as managers) have the ability to do things that other users (such as data-entry staff) do not. In this case study, we'll create a general-purpose system for keeping track of user privileges. This system can be applied to any type of PHP application in which users are individually identifiable.

# ## Defining Requirements

To develop an application, we need a complete understanding of what capabilities the application will be expected to have. This determination of the program's requirements is best obtained through extensive interaction with intended users of the application. Many applications have more than one type of user. An online auction might have buyer users and seller users. A retail site might have customer users, agent users, and manager users. Many sites will have some type of administrator user who manages the operation of the site itself.

The proposed user privilege system is really a tool to be used by *developers* to achieve access-control on a site, although other types of users (such as managers) should also be consulted for specific implementations of the system, since such a system can have a direct impact on the business and operations aspects of the site.

Suppose that after consulting all affected parties, the following requirements have been delineated: