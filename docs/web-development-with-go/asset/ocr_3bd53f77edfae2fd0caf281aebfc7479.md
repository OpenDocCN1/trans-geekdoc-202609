# 616 CHAPTER 16. DEPLOYING TO PRODUCTION

Note: Another way of handling this would be to only apply the middleware routes that require it, much like we do with our RequireUser middleware. It ends up being more code, but reduces how tightly linked our middleware and routes are. In your own applications you will have to decide which route makes the most sense.

Restart your server and visit a page with images, like a gallery you have created. Before making these changes you likely saw many log messages like:

```
SELECT * "users" WHERE ...
```

Now that we have updated our code you should see these less frequently because our application is querying the database less often.

# Source code

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/16.4

Changes - book.usegolang.com/16.4-diff

# 16.5 Fixing bugs

The only web applications that will ship to production without any bugs are likely going to be ones with no features whatsoever. The instant you add new features there is always a risk that something will go wrong, or that you won't think about obscure edge case.

While this might sound terrible, the truth is this is just part of the development process and it is why Go stresses being highly readable over nearly everything