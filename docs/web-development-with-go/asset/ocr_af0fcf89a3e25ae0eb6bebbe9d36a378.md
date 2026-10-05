146

CHAPTER 7. CREATING A SIGN UP PAGE

Completed - book.usegolang.com/7.4.5

Changes - book.usegolang.com/7.4.5-diff

# 7.5 Cleaning up and creating a static controller

Thus far we have been working with the users controller, but in this section we are going to look at how you can use a controller for pages that don't really map to a resource like a user, but instead closer to static pages in your web application.

A great example of this is your contact page. You might be able to put this under something like an inquiries controller because it is how users find out how to make inquiries, but this controller would end up with one action - the page that shows all of your contact information.

Instead of creating a bunch of unnecessary controllers that could get confusing, we are going to create one controller to hold all of our pages that are not quite static pages, but are pretty close to being a static page. We are going to call this the static controller, and inside of it we will have actions for the home page and the contact page.

# 7.5.1 Creating the static controller

Just like before when we created the users controller, our static controller will live inside the controllers package. Create and open a new source code file inside of the controllers directory for your static controller.

```
$ atom controllers/static.go
```

The first thing we need to do is declare the Static type. Inside of this we