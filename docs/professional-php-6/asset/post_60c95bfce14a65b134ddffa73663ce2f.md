
that an experienced senior designer with interface architecture skills is on hand to ensure that the polish on your finished product stays well and truly intact.

When a small change is requested late in the project, it is tempting to cut corners and allow a software engineer to take ownership of the new feature. Do this only if you have a rock-solid style guide in place, as discussed in Chapter 16. Otherwise, you may find your beautiful application blighted by the appearance of a grey, rectangular Submit button on an otherwise lovely interface.

## Testing

It goes without saying that the single most effective way to ensure that the core qualities alluded to previously pervade your project and that is to test, test, and test some more.

Testing can take many forms, however. Each of the previous qualities has one or more testing methodologies associated with it. Let’s look at them in turn.

## Unit Testing

The good news is that you’ve already done this at least once before — that is, you have if you followed Chapter 13 in detail, where you would have encountered unit testing as part of the build of the Widget World application.

The concepts of unit programming and a testing framework were touched upon earlier in this book, including the theory of why these are good practices to employ in large projects. In Chapter 13, you put that theory into practice in building the application.

Let’s recap briefly, however. Unit-driven programming involves constructing your application in neatly packaged, distinct components that have an interface yielding human-predictable results from a given set of data. A testing framework is then constructed for each component that asserts a series of human-determined theoretical results based on a series of theoretical inputs, and then tests the validity of those assertions by comparing those theoretical results against the actual results derived from the execution of that component’s methods.

These frameworks become black boxes that enable you to continuously test the functionality of your components throughout their evolution. You can construct such frameworks, therefore, early in your project, and regression-test your components as they evolve and become more sophisticated to ensure that they still produce the results expected. Put crudely, you can test to ensure that your changes have not broken something that used to work!

Unit testing picks up coding errors. Such errors are typically oversights on the part of the programmer. Unit testing does not pick up any other form of a problem; hence, it is only a part of the testing required to ensure high levels of quality with respect to functional compliance.

As an example, consider a Web mail application. You may have built a user class, a mailbox class, and a message class. All three may pass your unit tests. However, consider the Reply button on a message being viewed. It would instantiate a new message object and copy the sender property of the original message object to the recipient object of the message object. This action may not be performed by any specific method in any class, and hence may not be the subject of any unit test. If the recipient of the e-mail is not set correctly when Reply is clicked, then this is very clearly a functional error that must be resolved. It is not, however, one that a unit testing framework would pick up in any three of the tests being performed. You can see, therefore, that unit testing is not the ultimate test of functional compliance. In effect, it tests only the “model” in your model-view-controller (MVC) design pattern.

## Functional Testing

Functional testing is the other half of ensuring functional compliance quality on your project. It is normally conducted with due deference to the original functional specification of the project.

There are a number of possible approaches to formalizing functional testing. The most important rule to follow is that it is, in fact, formalized in the first place. Merely having a developer perform a quick run-through of key functionality isn’t enough on a large-scale project.

One approach to consider is to assemble a team of test personnel, ideally relatively intelligent individuals typical of your target audience, and issue them formal paperwork for completion. Consider assigning each test team member a specific area of the site to test.

## The Functional Test Paper

Considering the Web mail example, you might devise a form that looks something like Table 20-1. The “Action” and “Expected Result” columns should be completed by you in your role as project manager. Your test team will complete the “Actual Result” column, which you can then use to score each test as either a FAIL or a PASS.

Table 20-1: Functional Test Form for Web Mail Example

| Action | Expected Result | Actual Result | Score |
|---|---|---|---|
| Open the login page by clicking the login link on the navigation. | The login page is displayed, featuring username and password text boxes, and the Submit button. | Expected result | PASS |
| Enter the login joet1301f and the password ixrsh0z1 and click Login. | The form submits and the page reloads, stating that your login is successful. After five seconds, you are automatically transferred to the home page. | Expected result | PASS |
| Click the Inbox link in the navigation. | You will be taken to your Inbox. You will see a number of messages listed. For each message, subject, date received, and sender should be listed. The total number of pages comprising this mailbox will be shown. Previous and Next buttons will be visible if more than one page exists | Expected result except that no Next button displayed despite showing page 1 of 18 | FAIL |

It is, of course, extremely important that any FAIL marks are followed up. As project manager, you should assume a role whereby you first double-check any failures yourself. If any are found to be genuine, they can be entered into a fault-management system, the likes of which are discussed later in this chapter.

The actions you place on each functional testing paper will, of course, be derived directly from the functional specification in one form or another. Essentially, you are devising a user journey. Your test team will need to follow the actions sequentially. For example, it is obviously important that any logins take place before any activity dependent on the user being logged in. Advise your test users that if they find themselves unable to execute subsequent actions because of a block failure, they should mark their papers accordingly and move on.

## Functional Testing Considerations

You must ensure that each branch of the user journey is covered in testing, at least to the extent that you can be reasonably confident that the system is functionally correct. A branch occurs every time a decision is made. For example, if logins to your system come in three flavors (say, a normal user, super user, and administrator), you need to have three initial branches. If, for each of these logins, a user may choose one of three mailboxes to view, then an additional three branches per initial branch will be created.

It may be helpful to draw all the possible user journeys using a tree diagram of some sort, which you can then translate into the previous testing paperwork.

This method of functional testing is not infallible, but far more effective than simply asking the development team to “test thoroughly.” The resulting paperwork also forms a sort of affidavit that can be presented to the client as documented proof that the system has been thoroughly tested prior to handover.

## Load Testing

The general principle of load testing is to determine exactly what kind of extreme environmental conditions your application can cope with before it falls over.

The traditional belief is that it is sufficient to simply ascertain whether the application can support the number of simultaneous users specified in the technical specification, and whether the response times under such a usage level are within a reasonable limit.

A more bullish approach is to keep turning up the amp until the speakers blow. Clients much prefer to be told that “your site can, under its present infrastructure, support 530 simultaneous users” than simply “yes, your site supports the 500 simultaneous users you need it to.” Knowing that the system has support for only 30 additional users may not be the news that clients want to hear, but it is better that the client hears it sooner rather than later.

The principles of load testing are detailed further in Appendix C, “Performance Tuning PHP.”
