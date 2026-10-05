# 9.2. CREATING THE USERSERVICE INTERFACE AND QUERYING FOR USERS213

# 9.2 Creating the UserService interface and querying for users

In Section 8.4.5 we explored using GORM to write records to our SQL database, but we left out a lot of details at the time to make things simpler. As a result, we were able to interact directly with the gorm.DB object and demonstrate how GORM can be used to interact with a database, but we won't to interact with GORM directly in most of our application.

For starters, we might eventually want to change our application to use the database/sql package, or ever another database altogether. If we were to scatter the gorm.DB object across all of our code would be very hard to change in the future. It would also be very hard to test our application without setting up a real database, and we would end up with a lot of duplicate code.

Rather than using GORM everywhere in our code, we are instead going to write a layer of abstraction that defines what methods our controllers will be using, but hides those implementation details. This will allow us to change our database implementation details in the future without needing to update any controller or view code.

> Box 9.2. What is an abstraction layer?

In programming, an abstraction layer is a way of hiding implementation details.

Take a vehicle for example - when you put your foot on the gas pedal expectation is that the engine will provide power to the wheels and that your car will move. The actual implementation details of this are irrelevant. You don't care if your car is electric, gas, or a hybrid; as long as the gas pedal still causes the engine to provide power and accelerate the vehicle you should still be able to drive it.

Abstraction layers in programming are very similar. Most of your code won't actually care how data is saved or what database is being used. All that will matter