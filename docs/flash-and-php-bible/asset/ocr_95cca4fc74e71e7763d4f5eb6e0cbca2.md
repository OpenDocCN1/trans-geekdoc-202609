# FIGURE 9.6

Here is a sample response from the third AMFPHP service method.

![](bbox=[0.105, 0.175, 0.74, 0.565])

# Building a Real-World Application Using AMFPHP

Now that you have seen AMFPHP service usage and how to implement it in Flash, you can continue by building a real-world application. A good example of a real-world application is a Flash-based album listing applications, which is explained in the next sections.

The database used for this example is the same one that is created in Chapter 2. If you haven't completed that chapter at this point, I recommend starting here.

# AMFPHP services

The AMFPHP services needed for this example are responsible for querying the database based on passed-in arguments. This also requires a database connection system that will need to be secure. This means methods will not be exportable or viewable by AMFPHP.