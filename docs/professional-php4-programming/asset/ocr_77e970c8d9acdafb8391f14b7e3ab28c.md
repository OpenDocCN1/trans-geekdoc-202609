Here, we create a new `FormControlFactory` instance and create three new classes using its factory methods. The first two calls to `createTextField()` create text fields that store a first and last name. The next call creates a submit button with the caption "Submit Name". At this point, our application can do anything it needs to with these new objects. The importance is not the meaning of the application, but the structure and understanding of what factory methods are and how to use them in your web applications.

Factory classes are not limited to creating methods alone. You can add other methods that make sense to the factory model such as find methods that look up objects in the factory and return them, and delete methods that can scrap objects inside the factory. These implementations are project specific and are up to you, the application designer. Now, let us turn our attention to the principles of encapsulation and information hiding.

# Encapsulation

When you take your pain reliever for your headache, you probably don't know what it contains. All you care about is its ability to remove your headache. This is so very true when programmers use objects supplied to them. When we started using our `Car` object, we didn't know about the transmission, exhaust system, or the engine in the vehicle. All we wanted was to turn the key and start the car. The goal should remain the same when designing your objects.

Include all the complex data and logic within the object and provide users only with meaningful services that they would expect to interact with that object. Here you are, in effect, encapsulating the complex data and logic details inside the object. If done properly, we gain the benefit of information hiding, which we are going to illustrate next.

As we mentioned before, it's important for users of the class to be completely unaware of the data members within the class.

> Although it is perfectly valid in PHP to modify the members of an instantiated object at any time, doing so is considered bad practice.

Here is an example that illustrates a few disastrous events that may happen if we modify the object's members without going through the object's interface. In this example we assume that there is a method to set the speed of a car, called `setSpeed($speed)`, which will fail if you set it over 200km/h or when the speed is less than 0km/h. Let's also assume that our constructor does not initialize the engine and the required key to start the car:

```
$myKey = new Key('Key of my Porsche');
$car = new Car();
$car->engine = new Engine();

$car->speed = 400;
$car->start($myKey);

$car->engine = 0;
$car->stop();
```