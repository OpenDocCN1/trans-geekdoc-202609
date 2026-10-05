who was considering buying the mine.

Regardless, salting was the first term to be coined, and then the term pepper came about because the two are so similar and "salt & pepper" is a popular duo
(at least in the United States).

# 10.4 Implementing password hashing for our users

Now that you understand how we are going to be storing passwords, let's go ahead and look at how to implement everything we have discussed. We are going to start by adding fields to our user model to store our password. After that we will learn how to hash passwords using `bcrypt`, a password hashing function. Once that is done we will need to update some of our controller code to pull the password from the sign up form, and then finally we learn how to salt and pepper our password when hashing them.

# 10.4.1 Adding password fields to the user model

Our first changes will be made to the user model.

```
$ atom models/users.go
```

While we are only accepting a single password input from users when we sign up, we are going to add two fields to our user model. The first field will be named Password, and it will be used to store the raw (unhashed) password. That means that we will NEVER save this field in the database, and GORM provides us with a way to ensure this via the - struct tag.

> Note: We should also avoid logging the user’s raw password, so keep this in mind when writing any logging code.