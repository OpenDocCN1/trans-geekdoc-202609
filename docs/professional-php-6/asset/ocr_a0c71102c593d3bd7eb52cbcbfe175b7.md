Load testing can be conducted only if you can deploy the application onto a realistic environment, usually the production server. There is no point in testing your application on your Xeon-driven Linux development server if you know you'll be forced to deploy onto a Sun box running Solaris. A number of packages are available, the most popular of which is probably LoadRunner (visit https://h10078.www1.hp.com/cda/hpms/display/main/hpms_content.jsp?zn=bto&cp= 1-11-126-17%5E8_4000_100&jumpid=reg_R1002_USEN for more information). Similar results, however, can be achieved using a suite of custom built test scripts.

The key to load testing is to never be afraid to turn the volume up as high as it will go until the speakers explode. Simply knowing that the client’s traffic expectations can be handled is good, but knowing exactly how much more they can handle beyond that is even better. The client will be gratified if you can provide an exact figure, such as “the site will handle 1,000 simultaneous users without any problems.”

# Handover

Having produced a thoroughly documented, well-designed, fully tested piece of software, it is vital to arrange a proper handover meeting with the client. This is the client’s final sign-off — either for the whole project or for this component, depending on which process (described earlier in the chapter) you decided to adapt.

During the handover process, you should ensure that the client is fully comfortable with the inner workings of the finished product. An element of training may be required as a result. In addition, remember what you’re there to do — hand over the project. Presenting the client with a DVD containing a copy of the source code can have a symbolism that is hard to measure.

It is almost inevitable that small change requests will crop up during the handover process. Later in this chapter, you will learn how to handle them.

# Programming Methodologies and Practices

Let’s look briefly at the build process itself. There are a couple of best-practice methodologies you may want to adapt during the build process, regardless of the overall project process you have chosen.

# Test-Driven Development

In Chapter 13, you briefly met PHPUnit, and you learned how to use it to build unit testing frameworks. This knowledge can only be applied, of course, if you have built your application in a unit-driven fashion.

Test-driven development requires that you write the test before the code. The act of writing the test for the class in which you intend to code forces you to think about exactly how you plan to use a particular class, what it needs to do, and what its interface should be. PHPUnit (available through PEAR at http://pear.php.net) is a good framework for testing.

You want to confirm that your unit test works before attempting to write the class itself. This may require using a dummy class with the same interface as that of your real class to make the test run and naturally fail.