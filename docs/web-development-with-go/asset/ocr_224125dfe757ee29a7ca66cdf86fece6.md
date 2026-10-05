# Source code

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/15.5

Changes - book.usegolang.com/15.5-diff

# 15.6 Rendering images in columns

Now that we have our images, along with a static file handler that permits us to serve them, we are going to look at how to render our images a little more elegantly. For instance, we likely want to show smaller versions of the photos when looking at an entire gallery, but we would like to be able to click on an image to view the full size version.

We would also like to be able to split our images into columns, but the actual number of columns is going to vary. For instance, on the edit page the user already knows what the images look like, so chances are we can split them into four columns with slightly smaller preview images, but when we render the gallery for public visitors on the show page we might want larger previews we can only use three columns.

We will start with the second feature, but will ultimately end up implementing both when we get to editing our HTML templates.

When we are rendering HTML with our templates, we end up filling things in one column at a time. For instance, if we wanted three columns we might have HTML that looks like:

```
<div class="row">
  <div class="col-md-4">
    <!-- Fill in HTML for the first column -->

```