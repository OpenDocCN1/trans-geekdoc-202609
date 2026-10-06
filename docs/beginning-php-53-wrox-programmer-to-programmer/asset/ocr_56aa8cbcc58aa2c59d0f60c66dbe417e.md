# Part III: Using PHP in Practice

```
echo "Captain's: I'm getting a fuel problem from the warp engine.
It says: " . $e->getMessage() .
echo "We have " . $e->getRemainingFuel() . " dilithium left. I guess
we're not going anywhere.";
catch (Exception $e) {
    echo "Captain's: Something else happened, I don't know what. The
message is " . $e->getMessage() . "./";
}
```

If the method catches an InputException, it displays a message, including the requested warp factor by calling InputException::getInvalidWarpFactor(). Similarly, if a FuelException is caught, the method displays a different message, retrieving the message with FuelException::getMessage() and displaying the remaining fuel from FuelException::getRemainingFuel. Finally, the method catches any other potential Exception that might be thrown, and displays a generic error message. It's always a good idea to catch generic Exception objects in any custom Exception you might have created.

Finally, the script creates a new Captain object and sets various speeds using its newWarpOrder method. You can see from Figure 20-2 that various exceptions are raised and displayed as the script progresses.

# Separating Application Logic from Presentation Logic

When you first writing PHP scripts, you'll probably find that you naturally want to mix your PHP code (application logic) and HTML markup (presentation logic) in the same script file, or page. Indeed, most of the examples in this book follow this format, because it's easier to explain code's all in one place.

Though this approach is fine for small scripts, things start to get messy when you start building applications. You'll find that:

+   - Your code's logic becomes hard to follow, because the code is mixed with chunks of HTML
- You end up writing the same, or similar, chunks of code across multiple pages, which — as you say in "Writing Modular Code" wastes effort and makes maintenance hard
- It becomes tricky to change your application's front end — for example, when redesigning your site, converting your site from HTML to XHTML, translating the site into another language or locale, or producing a mobile version of a site — because all your markup is intermixed with chunks of PHP code
- For the same reason, it's hard for Web designers to alter the look of pages within your application, because they are not familiar with PHP code

660