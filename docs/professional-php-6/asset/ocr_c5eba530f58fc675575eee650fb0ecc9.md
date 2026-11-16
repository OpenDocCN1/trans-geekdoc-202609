+   4. Check the output of the script against what you expected (in your head).

+   5. If the output looks good, move on. If not, adjust the class and repeat Steps 3 and 4 until the output appears to work.

+   6. Possibly many weeks later, integrate the component into the mother application.

It sounds almost comical, but this kind of process is actually more widespread than you might think. The problem with approaching your component testing this way is that it's neither thorough nor systematic. In other words, not only are you potentially testing only a small subset of your component, you're also taking longer than you really need to. Furthermore, if you do find problems, your short test script won't be of much help when it comes to tracking them down. You'll have to decide whether your test is successful or not every time you test.

Thankfully, there is another way. Revise the component test workflow to look more like this:

+   1. Design the interface (but not the implementation) of the class.

+   2. Create a test suite for the (empty) class, and check that it tests okay.

+   3. Write the implementation of the class.

+   4. Run the test suite again.

+   5. Fix any errors that are causing unexpected results and then go back to Step 4.

+   6. Integrate the component into the other application.

Next, you'll take a look at these steps in more detail to discover exactly what is meant by a “test suite.” The concept of the test case is covered a little later in this chapter.

# Designing the Interface of Your Class

Let's first recap some object-oriented programming (OOP) edicts. In OOP design, it's often said that the most important part of your object hierarchy is the interface, and the least important part is the implementation.

This might sound odd, but think of it as follows. If you're designing a user class, what's actually going through your head?

> “I’ll need to have username, first name, last name, and encrypted password properties, and I’ll need methods to tell my application which security groups this user belongs to, and a method to work out how long it’s been since their last login, and . . .”

You're being smart without even realizing it. You're listing to yourself the methods and member variables of the object. This is the business analysis of object modeling. What you're not trying to do is to figure out how long it has been since the user's last login. In fact, there's probably more than one way to do that. It doesn't really matter. Whichever way you go about it won't affect your interface.

In fact, the interfaces of your application's suite of classes is subjective. In other words, some analytical skill is required in translating paper specifications into a class hierarchy with methods and member variables. Conversely, making those methods do what they say they will do is objective. It either works as expected or it doesn't work. As a PHP professional, you might prefer to have a junior software engineer