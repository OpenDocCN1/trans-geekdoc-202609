# Source code

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/6.2

Changes - book.usegolang.com/6.2-diff

# 6.3 Creating a reusable Bootstrap layout

Earlier, discussing views in the MVC chapter, I mentioned that I personally like to create views that allow me to reuse templates. We are going to start creating a navigation bar and footer for our website, so it would be nice to do this with a layout. That way we can always show the same navigation bar and footer, and our templates can focus solely on filling in the contents of each individual page.

In order to do this, we need to learn how named templates work.

> Box 6.2. We will also be using Bootstrap
While we are at it, we are going to include Bootstrap in our layout. Some people dislike the look of Bootstrap because it is used so frequently on the web, but I believe it is a great tool for creating the first version of a web application because it allows you to build quickly and customize the look and feel of your application once you have it working.
As much as I love a pretty website, they aren't much good to users unless they actually work which is what we are focusing on now.