# # No Customer Registration

Another way in which the *Coffee* e-commerce project differs from the *Knowledge is Power* site is that this site does not obligate customers to register in order to make their purchases. Required registration, which is mandatory in a content access example, has actually been proven to hurt sales (truth be told, Amazon.com gets away with required registration just fine). So this site will focus on the purchases, not on the customer. This approach will have some interesting ramifications in terms of the database and how the site operates, as you'll learn in this chapter.

If you'd rather, you could provide your customers with the option of registering or not. In such a case, you would take the code from the *Knowledge is Power* example and modify it in order to add registration and login capability to your site.

# ## Implementing MVC

**tip** MVC is an example of a *design pattern*: an accepted and standard way to programmatically solve a problem.

For this coffee shop site, I've decided to implement somewhat of an MVC approach. MVC, which stands for *Model-View-Controller*, is a very popular way to design more complex Web (and other) applications. Within MVC, a project's code and files are divided into their discernible parts:

+   - **Model** is the data involved.
+   - **View** is the presentation layer (what the user sees).
+   - **Controller** is the logic that ties everything together and reacts to user activity.

**tip** Advanced programmers develop not for just today's expectations but also for what can reasonably be expected down the line.

By implementing MVC, you'll have a project that's easier to develop—especially when working on a team—and easier to maintain, with cleaner code. Further, the site will potentially be more scalable. *Scalability* is the ability to handle an increased load implicitly through an increase in resources. A Web site may start with one server and be able to handle up to X number of concurrent visitors. If the site can “scale well,” then it will also be able to handle, say, four times the concurrent visitors by just adding another server or two database servers. Conversely, a site that doesn't scale well could not properly handle four times the concurrent load even if you were to throw four or eight more servers at the problem. With the hope that an e-commerce site will take off, the ability for the site to scale well is a reasonable consideration.

**tip** OOP and frameworks generally use MVC and other design patterns by their very nature.

So what does MVC mean in terms of real code? It's actually simple in theory, although I'm applying MVC in a casual manner. The controller is represented by PHP code, which handles user behavior and reacts accordingly, often as an agent between the model and the view. The data, with few exceptions, is repre-