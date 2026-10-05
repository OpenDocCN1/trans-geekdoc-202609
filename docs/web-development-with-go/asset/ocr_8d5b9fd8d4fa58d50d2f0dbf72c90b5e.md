Completed - book.usegolang.com/7.1.2

Changes - book.usegolang.com/7.1.2-diff

# 7.1.3 Adding the sign up link to our navbar

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
</ul>
```

We want to add this code to our navbar, so open up the navbar template.