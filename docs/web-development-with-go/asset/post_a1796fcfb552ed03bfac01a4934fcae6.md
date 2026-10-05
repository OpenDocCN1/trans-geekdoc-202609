
Completed - book.usegolang.com/7.1.2

Changes - book.usegolang.com/7.1.2-diff

## 7.1.3 Adding the sign up link to our navbar

We have one last change to make to finalize the addition of our sign up view. We need to add a link to this page to our navbar! Ideally we would like to add this to the right of our navbar, since this is where most people expect to find a sign up link. To do this we are going to check out the Bootstrap docs one more time.

Open up the bootstrap default navbar docs:

http://getbootstrap.com/docs/3.3/components/#navbar-default

Note: If you are offline you can just get the code we use below

What we are looking at here is the ul HTML tag with the class navbar-right. This shows us how to create the right portion of the navbar example.

We won't be using everything in the example, and we will want to update the link to refer our sign up page. After making each of these changes we should end up with code similar to that in Listing 7.9.

Listing 7.9: Our navbar-right

```
<ul class="nav navbar-nav navbar-right">
  <li><a href="/signup">Sign Up</a></li>
</</ul>
```

We want to add this code to our navbar, so open up the navbar template.

## 7.1. ADD A SIGN UP PAGE WITH A FORM

```
$ atom views/layouts/navbar.gohtml
```

Next look for the existing ul tag that has the class navbar-nav. Our new code is going to go right after this ul tag. When you are done your code should match Listing 7.10.

```
Listing 7.10: Adding the sign up link to the navbar.
```html
(define "nav")
<nav class="navbar navbar-default">
  <div class="container-fluid">
    <div class="navbar-header">
      <button type="button" class="navbar-toggle collapsed"
          data-target="#navbar" aria-expanded="false" aria-controls="#navbar">
        <span class="sr-only">toggle navigation</span>
        <span class="icon-bar"></span>
        <span class="icon-bar"></span>
        <span class="icon-bar"></span>
      </button>
      <a class="navbar-brand" href="/">LensLocked.com</a></</a>
    </div>
    <div id="navbar" class="navbar-collapse collapse">
      <ul class="nav navbar-nav">
        <li><a href="/">Home</a></li>
        <li><a href="/contact">Contact</a></li>
      </ul>
      <ul class="nav navbar-nav navbar-right">
        <li><a href="/signup">Sign Up</a></li>
      </ul>
    </div>
  </div>
</nav>
({end})
```
```

Go ahead and restart your server to test all of changes. We should now have a sign up page, links to it in the navbar, and the page should have a blue panel around it. A screenshot is shown in Figure 7.2.

![](img/d6be51afcf11b16bf97245d05fb9e635_139_0.png)

Figure 7.2: Finished sign up form

You can also try resizing your browser window to see how bootstrap automatically changes the look and size of your panel based on the browser window. Neat, right?

## Source code

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/7.1.3

Changes - book.usegolang.com/7.1.3-diff

## 7.2. AN INTRO TO REST

REST is a subject that is often debated and could likely take up an entire book on its own. Obviously we don’t want to spend weeks discussing what is and isn’t RESTful, but we do need to take a few moments to get an overview of what REST is and how it will affect our application design.

REST is an architectural style for developing software and networked systems, and was used in the design of most of the World Web. It is also commonly used as a guide for designing web applications and APIs, and how we will be using it.

REST is perfectly abstract, so if someone tells you something isn’t RESTful, take it with a grain of salt. There is no golden standard of what is or isn’t RESTful, and (to my knowledge) aren’t any real world examples of what the ideal RESTful web application would look like. Instead developers are left to interpret it best they can.

So what does that mean for us? Well, it mostly means that we will be modeling most of the pieces of our application around resources. Resources are things like a user, a gallery, or an image. Things that can be created, read, updated, and deleted. Some people even think further and also consider things like a session or relationship as a resource that needs to be created within the context of our application.

While I don’t necessarily disagree with the idea of modeling a session as a resource, I want to stress that you shouldn’t get caught up in trying to find the perfect representation of everything in your application. Instead, use it as a guiding principle as you create your models, controllers, and views, but don’t bend backwards if it means your code will be harder to understand or maintain.

Table 7.2: HTTP request methods

| HTTP Method | Significance |
| :--- | :--- |
| GET | Reading a resource |
| POST | Creating a resource |
| PUT | Updating a resource |
| PATCH | Updating a resource |
| DELETE | Deleting a resource |

## 7.2.1 How REST affects our code

There are basically four (okay, we will look at five) HTTP request methods that can be used when requesting a web page. These are used to dictate your intent when you make a web request, and they are shown in Table 7.2.

Box 7.4. The difference between PUT and PATCH

Both PUT and PATCH are used to represent updating a resource, but so in a fundamentally different way. PUT generally is expected to accept an entirely new representation of an object, even if some of the fields didn't change, while PATCH was proposed as a way to update resources and signify that you won't be passing all of the fields for the resource, but instead only providing the updated fields. (Note: OCR text correction)

The HTTP methods listed in Table 7.2 are used in conjunction with paths in our web application to shape your code, and the paths are also a strong indicator as to what controllers we should be creating.

## 7.3. Creating OUR FIRSTROLLER

For example, we will eventually create a gallery resource that will have paths like the ones shown in Table 7.4. We will also create models, controllers, and organize our views according to this resource. That means that our application will eventually have a controller for the galleries resource, a model for the galleries resource, and views that deal with the gallery resource will be organized in a galleries folder and construct the galleries controller.

### 7.3 Creating our first controller

Over the course of this book we are going to create several controllers, and within each controller we are going to create handler functions.

Box 7.5. Actions are synonymous to handler functions

In this book I often refer to functions that handle web requests as handler functions because this is quite literally what they are. In the MVC world, the functions or methods that handle requests for a specific page are often referred to as “actions”. This terminology is especially popular in Rails and ASP.NET.

I have never found a well defined rule for what is or isn' an action, but generally speaking an action is a function that handles a web request for a specific path. For example, when we create the sign up page, it will be mapped to the New () method on the Users type. In this case, the New () method is an action used to render the sign up page.

Nearly every handler function we write from this point on in the book will be an action, so you might see me interchange the terms “handler function” and “action” along the way, but rest assured that I am referring to the same thing.

Table 7.4: Example gallery paths.

| HTTP Method and Path | What Path is Used For |
| :--- | :--- |
| GET /galleries/new | This path is used to retrieve a form or some other page that will allow you to create a new gallery. It would be akin to asking for a driver's license application - you don't create the gallery here, but you get the page that you are going to submit to create one. |
| POST /galleries | Whenever you use the HTTP method 'POST' it signifies that you want to create something or perform some action. When you POST to the bare resource path, it signifies that you want to create resource, and you are typically expected to provide the information to create resource along with the web request. In this case, we would be saying that we want to create a gallery and we would say to include the information used to create a gallery. The data will often come from an HTML form, but it could also be JSON or any other format. Going back to the driver's license metaphor, this would be like dropping off your application at the front desk and having them hand you a license in return. |
| GET /galleries/:id | This path is used to read a single gallery. The ':id' section is replaced with something we used to determine which gallery is being read, of ten numerical id like '313'. In our driver's license example, this would be looking up a driver's license by the unique number on each ID card. |
| PUT /galleries/:id | This path works similarly to the previous one, but because we are using the 'PUT' HTTP method we are stating that we want to update the gallery, and we are expected to provide the updated data along with our web request. With a driver's license this would be similar to submitting an application to change your address. |
| DELETE /galleries/:id | This path works similarly to the previous one - we use the ID to specify which gallery we are referencing, rather than updating it we are stating that we want to delete the resource. |
