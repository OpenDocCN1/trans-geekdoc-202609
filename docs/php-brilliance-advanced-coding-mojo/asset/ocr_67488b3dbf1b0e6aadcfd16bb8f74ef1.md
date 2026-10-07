Encapsulating our ideas.

Following same principles, there’s no reason why we can’t return to the $balance-property that we eliminated early on and proceed to code up a BalanceManager class, one that encapsulates everything we need to know about handling a user’s balance.

to specify more than one billing and delivery address. Doesn’t that then lend itself admirably to the provision of an AddressManager class?

# Summary

We’ve taken a long and winding route to get here. At the beginning, I pointed out that encapsulation in the purest sense of the term is not the same as information hiding. And then I asked you to treat the two things as being one and the same. I rather hope that, instead of thinking of me as some sort of nut, you can understand my intent – everyone who finishes this chapter, irrespective of their starting knowledge, shares a common understanding at the end: when we talk about encapsulation in our daily work, we’re actually referring to the two concepts bundled as one.

A shared vernacular, a common tongue, is an important factor in collaborative software development. What I hope to have achieved is just a little piece of that ideal.

On our way through these pages, I’ve explored the evolution of a rather typical, though extremely skinny, model class and in doing so, I seem to have been overly on splitting off individual responsibilities into smaller, discrete bundles of code. There are some ancillary motivations for having done so and I will own up to now.

On the one hand, training classes like they are silos into which we can merrily dump utility methods is a habit that I heartily believe we should all leave behind. All too often, I’ve encountered some monstrous class definitions, both in quantity of methods and in the size of the individual methods. This is indicative of either poor initial design at the outset or of poor technical leadership during the build. It’s not uncommon for the more junior members of a development team to follow prior example and simply add new methods to the classes that are already there rather than take the bolder step of creating dedicated classes for dedicated streams