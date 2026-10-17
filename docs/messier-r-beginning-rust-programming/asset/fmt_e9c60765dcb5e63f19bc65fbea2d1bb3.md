
If we didn't happen to get a valid command, we need to deal with that. Since we're done with what happens if we do have a valid command, we need to look at what happens if the earlier `if validate_input()` clause wasn't true. In this case, we just print that it's not a valid command, and we'll fall through the loop to start over, where we try again by accepting the user input and making another attempt to validate a command.

Just to clean all the way up, once we have dealt with the other end of the earlier `match` clause, we can move on to the rest of the function. If an `Ok()` is returned from the user input, we run through the process of validating it, getting it to the server, getting results, and dealing with any errors. We still have the case where we got an error from reading user input. Presumably something weird happened since we're just asking for the user to type something in at the console or command prompt. However, in a `match` statement, you have to handle all possibilities, and `Err()` is a possibility from a `Result`, so we need to handle the error case. We're just going to take the error and print it out so the user can see that something happened.

At this point, you have a working client that can communicate with the server from the last chapter. There is still a lot of additional work to do, including potentially adding encryption as well as a lot of additional commands, but you have the framework of a client/server application in place.

## ADDITIONAL RESOURCES

*   Transport Layer Security - `developer.mozilla.org/en-US/docs/Web/Security/Transport_Layer_Security`

*   Networking 101, Transport Layer Security - `hpbn.co/transport-layer-security-tls/`

*   What is TLS and How Does it Work? - `www.internetsociety.org/deploy360/tls/basics/`

*   Crate regex - `docs.rs/regex/1.4.2/regex/`

*   Regular Expressions - `developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions`

*   What is Regular Expression - `www.regexbuddy.com/regex.html`

*   Using TLS with Rust Authentication - `ayende.com/blog/185764-A/using-tls-with-rust-authentication`

# 8  

Going Relational

Doing basic input/output (I/O) operations is nice, but at some point, you want what you are doing to be persistent. Once you start to persist information you are working with, it's helpful for it to be found again. Chances are you may not be working with a single data set over and over. Modern applications are more likely to deal with complex data structures, and once you start talking about complex data structures, you need a structured way to store and retrieve them. Ideally, you'd also be able to search through all the data you have in an efficient manner, rather than reading every single record you have to determine whether it's the right record. Think of flipping through every page in a cookbook in order to find the one recipe you are desperate for. You're hungry, after all, and the longer it takes to find the recipe, the worse off you're going to be when you get around to eating.

You may get lucky, and it may be one of the first dozen recipes. Imagine, though, that you are looking through *The Joy of Cooking*, with thousands of recipes. It seems like it would be far easier to find what you were looking for if there were a way to categorize or index the recipes. Fortunately, a book like that would have an index, making recipes easier to find. There may also be a categorization scheme that would help you get to what you were looking for faster. This is what a database does for us. A database allows us to store data in a structured way as well as providing us the ability to quickly retrieve data records without having to serially read through all the records to find what we're looking for.
