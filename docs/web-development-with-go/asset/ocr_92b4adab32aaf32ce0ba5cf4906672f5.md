# 14.5. CREATING NEW GALLERIES

```
}
d.LogMode(true)
return &Services(
    User: NewUserService(db),
    Gallery: NewGalleryService(db),
    db,
    nil
)
```

With that we have a working gallery service and can insert new galleries into our database's galleries table with the Create method we implemented. We don't validate the data yet, but we can wait to do that until we implement the controller and actions needed to render and process a new gallery form.

# Source code

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/14.5.1

Changes - book.usegolang.com/14.5.1-diff

# 14.5.2 The galleries controller

In this section we are going to introduce the galleries controller, along with a New view used to render the new gallery form. We will look at the source code to process the form in the next section - for now we just want to render it and get our controller setup.

We are going to start by creating the template for our view, which means we need to create a directory to store our gallery views and then create a template file there.