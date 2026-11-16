# # Unified Modeling Language (UML)

If you’re the only programmer working on a small project, drawing a small sketch of the application on paper or keeping the design completely in your mind is often sufficient. A solo programmer can usually complete a project without any problems this way.

Suppose, however, that you were to get a larger project requiring two developers. You’re the one who’s responsible for designing the system, and the second developer is there to help you write the code. How would you communicate the design of this system to the other person? You could describe in words what classes were necessary, and provide a description of how the system functions both for the end user and internally. After a while, you might end up with a lot of text describing the system. If you imagine a larger project, it quickly becomes clear that describing a large software system purely in words is not practical; and if you created diagrams of your own design, then you would have the added task of explaining your system of notation to the other members of the team.

The Unified Modeling Language (UML) was designed to solve this problem. UML is primarily a language of standardized diagrams, each of which lends itself to describing a particular area of software design. UML gives everyone the same way of “speaking” about a system, and provides a powerful method of visualizing it.

In this chapter, you’ll work through the design and development of a hypothetical band-tracking system called BandSpy. In the process, you’ll learn about UML diagrams and where they fit into the process.

# ## Requirements Gathering

Here’s the hypothetical scenario for this chapter. A client from a record company has contacted you to develop a Web-based system to track the bands that the client represents. During an initial phone conversation, the client explains that BandSpy should enable Web users to view details