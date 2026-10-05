
# CHAPTER 5. UNDERSTANDING MVC

walk through a web request where a user is attempting to update their information, and we will follow along with Figure 5.1 and Figure 5.2.

- 1. A user submits an update to their contact info

![](img/d6be51afcf11b16bf97245d05fb9e635_77_0.png)

- 2. The router decides that the UserController should be used

- 3. The UserController uses the User model to update the User's contact info.

Figure 5.1: MVC Walkthrough Steps 1 to 3

## 1. A user submits an update to their contact information

This would typically happen when the user goes to their account settings and updates a few fields there. For example, they might update their name and email address. This web request is then sent to our server, where the router is the first code to take action.

## 2. The router decides that the UserController should be used

When the router gets the web request, it realizes that this is a request to update a User’s contact information based on the URL and HTTP method, so it forwards the request along to the UserController to handle the request.

## 3. The UserController uses the User model to update the user’s contact info

While handling the request, the UserController will need to make a change to data stored in our database, but with MVC our controllers don't interact directly with the database. Instead the controller will use the User model to update the contact information, which allows us to isolate all of our database specific code so that our controllers don't need to worry about it.

| Models | | |
| :--- | :--- | :--- |
| Photo | User | Gallery |

4. User model returns the updated data to the UserController

| Controllers | | |
| :--- | :--- | :--- |
| PhotosController | UserController | GalleriesController |

5. The UserController uses the ShowUser view to render the 'users/show.shtml' template and return it to the browser.

| Views | | |
| :--- | :--- | :--- |
| EditUser | ShowUser | ShowGallery |

6. The end user sees the updated User page in their browser.

![](img/d6be51afcf11b16bf97245d05fb9e635_79_0.png)

## 5.3. EXERCISES

- 4. The User model returns the updated data to the UserController

After updating the user in the database, the User model will then return the updated user object to the controller so that the controller can use this in the rest of its code.

- 5. The UserController uses the ShowUser view to render the correct template

Once the user controller gets the user back, it can then use the ShowUser view to render the updated user object to the end user. Again, this allows our controller to operate as a director that decides what code should run next, but doesn’t get bogged down with a lot of logic of its own.

- 6. The end user sees the updated User page in their browser

After everything is said and done, our ShowUser view will have rendered the HTML page that shows a user and the end user will now see their user account with the contact information updated. Mission success!

### 5.3 Exercises

For this section we won’t be coding during our exercises, but instead will review a few questions to ensure you understood what we covered.

### 5.3.1 Ex1 - What does MVC stand for?

What does each letter in the MVC acronym stand for?

### 5.3.2 Ex2 - What is each layer of MVC responsible for?

Try to jot down what each layer of MVC is responsible for and review the chapter to see if you are correct.

### 5.3.3 Ex3 - What are some benefits to using MVC?

We discusses a few reasons why MVC were important. Just take a moment to refresh your memory on what those are.

It is also good to remember that we DO NOT have to place all of our code into the MVC pattern. Not everything we write will be a model, view, or controller, and trying to force all of your code to fall into one of these three categories can be as bad as not using MVC at all.

## Chapter 6

## Creating our first views

In the last chapter we covered the MVC pattern, and in the chapter we introduced templates. In this chapter we are going to put all together views. Like everything we do in this book, we will start with. Finally, Bootstrap is a framework that will help us design. Bootstrap is a great place to use. We will eventually create layout and as of now it is just.

## 6.1. THE TEMPLATE

First, we need to open our 4.4. We need to to....................................................................................................... in the...

# Listing 6.4: Updating the home () function.

```go
func home(w http.ResponseWriter, r *http.Request) {
	w.Header().Set("Content-Type", "text/html")
	if err := homeTemplate.Execute(w, nil); err != nil {
		panic(err)
	}
}
```

## CHAPTER 6. CREATING OUR FIRST VIEWS

Finally, we need to update our home function so that it uses our. To do this we are going to call the template method like we did in 4.4, but instead of writing to Stdout we are going to write the results to ourWriter. This means the results of executing the template will be returned to the user who is making a request to our application.

The updated code is shown in Listing 6.4.

While executing the homeTemplate, we also added some error handling to our code. When calling the Execute method, it is possible for our template to encounter an error. For example, it might try to access a variable that we didn't provide and this might lead to an error.

If we encounter an error we are going to simply panic in our code so that we know about the issue. We shouldn't actually see any errors right now, but it is good to have this precaution in place for now as it will help us find any unexpected bugs in our code during development.

You might also notice that in 6.4 we are also passing nil to the Execute method instead of any actual data. This is because our template doesn't use any dynamic data, but we still need to provide that second argument. The simplest way to pass "no data" in this case is to pass nil.

At this point you are ready to stop your application (ctrl + c) and then restart it. If all goes well, your home page shouldn't look any different, but should now be rendered via the home. اہمیت template.
