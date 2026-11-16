that an experienced senior designer with interface architecture skills is on hand to ensure that the polish on your finished product stays well and truly intact.

When a small change is requested late in the project, it is tempting to cut corners and allow a software engineer to take ownership of the new feature. Do this only if you have a rock-solid style guide in place, as discussed in Chapter 16. Otherwise, you may find your beautiful application blighted by the appearance of a grey, rectangular Submit button on an otherwise lovely interface.

# # Testing

It goes without saying that the single most effective way to ensure that the core qualities alluded to previously pervade your project and that is to test, test, and test some more.

Testing can take many forms, however. Each of the previous qualities has one or more testing methodologies associated with it. Let’s look at them in turn.

# # Unit Testing

The good news is that you’ve already done this at least once before — that is, you have if you followed Chapter 13 in detail, where you would have encountered unit testing as part of the build of the Widget World application.

The concepts of unit programming and a testing framework were touched upon earlier in this book, including the theory of why these are good practices to employ in large projects. In Chapter 13, you put that theory into practice in building the application.

Let’s recap briefly, however. Unit-driven programming involves constructing your application in neatly packaged, distinct components that have an interface yielding human-predictable results from a given set of data. A testing framework is then constructed for each component that asserts a series of human-determined theoretical results based on a series of theoretical inputs, and then tests the validity of those assertions by comparing those theoretical results against the actual results derived from the execution of that component’s methods.

These frameworks become black boxes that enable you to continuously test the functionality of your components throughout their evolution. You can construct such frameworks, therefore, early in your project, and regression-test your components as they evolve and become more sophisticated to ensure that they still produce the results expected. Put crudely, you can test to ensure that your changes have not broken something that used to work!

Unit testing picks up coding errors. Such errors are typically oversights on the part of the programmer. Unit testing does not pick up any other form of a problem; hence, it is only a part of the testing required to ensure high levels of quality with respect to functional compliance.

As an example, consider a Web mail application. You may have built a user class, a mailbox class, and a message class. All three may pass your unit tests. However, consider the Reply button on a message being viewed. It would instantiate a new message object and copy the sender property of the original message object to the recipient object of the message object. This action may not be performed by any specific method in any class, and hence may not be the subject of any unit test.