Inheriting wealth is not always good.

# Inheritance Abuse

I couldn't very easily get to the end of a chapter on Inheritance without going into something that I've come to call Inheritance Abuse. You'll recall earlier in this chapter that I made mention of a particular horror story, one in which a company's homemade framework had the controllers extending the view? Well it wasn't quite simple as all that.

It didn't just have the developer create a controller by extending the View class directly. Instead, there were two, three or four intermediary levels of derived classes to contend with. If I recall correctly, the worst violation had seven in its inheritance hierarchy with the View class at one and the implemented Controller class at the other. The View class itself provided an init() method that allowed for the execution of some page setup routines. In some, but not all, of the derived classes called the init() method was overridden. For example, a page controller within the admin section of the site would need to extend a particular admin-flav child of the View class because its overriding init() method included a test to see whether the visitor accessing an admin page was a) logged in and b) had admin rights.

Of course this is an extreme example, one that was somehow oddly reminiscent of those word ladder puzzles we used to get as children. You know the ones I mean: We have a starting word at the top, and a target word at the bottom. On each level between you had to make a new word by changing just one letter of the previous word until you finally made the connection between the starting word and the target. That's how this company's framework felt at times; a word ladder.

Let's be thankful for merci though. PHP does not support multiple like C++; each class may only extend a single parent. As we have seen though, it places no restriction on the creation of multi-tier inheritance hierarchies. Any developer so without such thoughts can create their own “word ladders” in code, one little bit in each tier until finally the two extremities are connected. This is, in essence, the very thing that leads to what is known as the Yo-Yo problem, which I have personally experienced few more times than I would have preferred.

The Wikipedia page on the Yo-Yo problem makes a very apt description of it, so I shall simply quote the first sentence here