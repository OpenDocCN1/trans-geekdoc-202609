# Source code

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/13.3

Changes - book.usegolang.com/13.3-diff

# 13.4 A more permanent data type for views

In the last sections we explored how having a predefined data type can be useful when rendering views. With it we can still place more dynamic page-specific data into a Yield field, while still having more common fields like Alert when we want to show the user alert message.

In this section we are going to define a more permanent data type for rendering views. We will name this struct type Data, and will be placing it inside the views package because it is used in rendering our views. While doing this we will also create an Alert data type in the views package to be used when rendering our alerts.

Let’s start off by adding the new data types in the views package. We will create a new source file for this code.

```
$ atom views/data.go
```

Inside of this file we need to first introduce the Data and Alert types. For now this can be identical to the one we created earlier inside of our controllers.