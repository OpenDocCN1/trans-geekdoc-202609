views/views/... (duplicate “views” directories) it likely means that your call to NewView is passing in the views/ prefix, and then the NewView function is calling the addNewTemplatePath prefix resulting in duplicate prefixes.

Likewise, if the file ends with .gohtml it probably means that you are passing in the extension with your files and then NewView function is appending another extension.

# Source code

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/7.5.2

# 7.6 Exercises

We covered a lot in this chapter, but towards the end we started to repeat a lot of things that we learned earlier in the chapter. For example, creating a static controller wasn't really much different than creating a users controller.

While we aren't technically using a framework, what we are doing is very similar to building our own. We don't have any fancy generators or other tools to help automate things, but we have helpers for creating views, a common design for our controllers, and before long we will also have something similar for our database layer.

Doing this also gives us lot of the benefits of a framework. For example, once a newcomer learns how we designed our controllers they could easily jump