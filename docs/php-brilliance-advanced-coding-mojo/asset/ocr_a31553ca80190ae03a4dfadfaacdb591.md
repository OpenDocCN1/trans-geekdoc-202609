PHP7

331

Clearly then, the opponents have a very strong case. How do the arguments stack up on the other side of the ring?

# In the red corner

The benefits for being able to type hint for scalar values are immediately obvious, but before we even get on to considering those there's a particularly relevant point to make first.

We can type hint for everything.

If you loop your mind back to the beginning chapters of the book, you'll remember the effort we went through to consider abstract classes as a means of laying down definitions for new data types. Why did we do this? We did this in recognition of the fact that the language's native data types don't fully represent our needs. They're not intended to of course. Through the provision of our custom data types we are making it possible for our application's code, and more importantly the developers wrote it, to enjoy the knowledge of how these things are intended to work.

A key part of this is that the abstract class documents as best as it can the intended behaviour of the instances derived from this data type. Part of the abstract's documentation includes informing the client code, the collaborators, how many parameters each method expects and of what type they should be. Unless those parameters are intended to be scalar values, that is.

Further, we re-examined the role played by interfaces and how they allowed us as developers to express guaranteed method availability in the objects that implement them. In the same way as with abstract classes, we are able to express the requirements of the methods in these interfaces quite succinctly. Again, with the exception of parameters expected to be scalar values.

The provision of scalar type hinting completes the circle. This alone provides enormous value to us as developers keen to exhibit PHP Brilliance. It's another weapon in our fight against the army of bugs that threaten constantly to creep into our applications and eat away at our precious time.

Going forward, scalar type hinting would make it possible for us to "type hint all the things". As far as the input parameters are concerned, every method we come would be able to declare for everything it needs and expects, rather than just most of them.