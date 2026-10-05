# 9.8. EXERCISES 241

and coded. If you do write and run any of this code, be sure to reset your database to reflect the user table we will be using in the rest of the book.

# 9.8.1 Ex1 - Add an Age field to our user resource

Adding a new field to a resource involved a few steps. Try to walk through them to see if you can figure out what all code you would need to add in order to let a user provide their age when creating an account and have it persisted in the database.

# 9.8.2 Ex2 - Write a method to query the first user with a specific age

Once you have added the age field to your users model, write a method that will allow you to query users with a specific age. This should be attached to the UserService like our other query methods, and should be pretty similar to our ByID method.

# 9.8.3 Ex3 - [HARD] Write a method to query many users by age range

Our last exercises are a little harder only because you will need to write a bit more code and dig into GORM more.

Check out the last chapter and combine the information there demonstrating how to query multiple users with your knowledge of how GORM's Where method works to create a InAgeRange method on our user service.

The InAgeRange method should accept two arguments, a minimum age and a maximum age, and then it should return all users within that age range. If no