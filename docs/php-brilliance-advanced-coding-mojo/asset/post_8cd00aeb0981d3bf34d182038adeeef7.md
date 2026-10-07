
## More Pub Time

As a result, assessing the security aspect of software quality entails a lot more than making sure we are protecting ourselves against SQL injection attacks, or hashing user passwords properly. It entails making sure we have the right kind of validation in place and that we've put that validation code in the right location. It entails making sure that a multi-stage data manipulation process can be rolled back to its original state should one of those stages fails. It entails a lot of things but the final outcome needs to be this: All of the right data in all of the right places and none of it anywhere else.

Making sure that we're ready for the user that `;DROP TABLE users;@hotmail.com` as an email address is one thing, but if a member of our team creates an algorithm that accidentally sets every user's first name to the four character "John" then we're already sailing down crap away and the paddle is nowhere to be seen.

## Efficiency

I've known developers in the past who have placed an inordinately high degree of importance on creating highly efficient, fast running, low memory usage code. Ones that have declared code can only be beautiful when it's fast.

Thankfully, most of us already know better.

In the days, months and years before the explosion of cloud computing and virtualization, the performance of an application could often be improved by an activity known as "throwing more tin at it". Adding another server to the rack or installing fast hard disks or more RAM was commonly cheaper than paying a developer's salary for the time required to optimise code.

Nowadays, we can still "throw more tin at it" but in a virtual sense by spinning up another instance.

Nevertheless, creating code that is performant and efficient is still very important if we hope to preserve our all-important pub time. Code that is already reliable, secure and maintainable can always be optimised for speed and efficiency.

But code that is written for speed first can rarely be optimised for reliability, security and maintainability after the fact.

That's not to say that speed and efficiency aren't important of course. An online application that takes thirty-seven minutes to turn a request into a response better be delivering absolutely critical information at the end of the cycle if it has even the slightest hope of retaining users.

The reality for the vast majority of online applications is that the request-response cycle needs to complete in a matter of seconds, not minutes. Fortunately for us in the online world, there are a number of techniques that we can employ in order to improve the perceived performance of an application and therefore improve the user experience.

Rather than dispatching that account activation email as part of the sign-up procedure, we can queue it for an independent process such as a cron or a daemon to take care of.

Rather than parsing and processing an uploaded CSV as part of the request-response cycle, we can move the file to a watched directory and allow the status of the file’s processing to be reported back the front end by a series of subsequent, asynchronous calls.

Of course, we can optimise the actual performance and efficiency of our application code and not just the perceived performance and efficiency. The developer who performs a `SELECT * FROM users` and then loops through the entire recordset in memory just to find the row for the user that has just logged in probably needs his butt kicked first and foremost being taught how to write a WHERE clause. Returning a single row in this situation is clearly much more efficient than pulling the entire table.

Despite being at the bottom of this list, efficiency is still a very important factor in a list of four factors for assessing the quality of an application and its code.

> Software quality is a huge topic in its own right, with hundreds of books and academic papers published on the subject. Here, I've only scratched the surface and only very lightly at that. Nevertheless, I hope I've been able to at least impart the vaguest impression of what is meant by quality code being reliable, maintainable, secure and efficient.

Which brings us closer to considering what the right kind of knowledge might be. Before we do that though, we should take a moment to consider the wrong kind of

## Hello World!

The learning process is well documented. Not just in programming circles but in any kind of trade or craft, a practitioner will go through a number of distinctive phases. At the start comes the novice, picking up the fundamentals and learning the first principles. It might be highly presumptuous of me to say this but I'd be prepared to wager a great many of us began this journey by writing "Hello World" on the screen, all thanks to Brian Kernighan way back in 1973.

Advancing beyond the novice stage is the journeyman, building upon the fundamentals by acquiring additional knowledge and combining it with experience in order to hone their skills and further their personal development before ready themselves for the final stage, that of the master craftsman.

Traditionally, the title of master craftsman would be bestowed upon a practitioner by the guild that oversees their particular trade or craft. When ready, the journeyman would prepare and submit a piece of work as part of the application process and would be the members of the guild who judge such piece of work and establish whether they deem it to be worthy or not.

In the world of online application creation we aren't fortunate to have such a structured approach to personal development; one cannot readily apprentice oneself to an established master craftsman. As such, our journeyman stage is a low-joy skip through a sun-drenched meadow and much more a stagger through a perilous swamp filled with traps and pitfalls.

It's also huge, thanks to the Internet. The journeyman developer is literally inundated with opportunities to advance their knowledge and abilities thanks the plethora of materials available to him or her. There are courses to follow both online and in more traditional bricks-and-mortar learning establishments, there are articles and blog posts that are numerous to count.

Which is precisely where the danger lies; the largely unrestrained and unregulated publication of tutorials and training videos presents a very real danger to the journeyman coder. With such an unfathomably large volume of information available, how does the journeyman coder hope to be able to sift the good quality information from the bad, especially when the bad keeps coming at an ever-increasing rate?

As a case in point, as recently as December 2015 I encountered two exceedingly poor quality tutorials linked to developer forums that I frequent. The first showed how to “easily populate variables using the extract() function”, which is a particularly dangerous “trick” to learn without making the reader fully aware of the dangers involved.

However, even that pales into insignificance when compared to the second tutorial, which illustrated how to use AJAX to send search terms from an html form to a PHP backend that would return the search results back to the front end after querying the database. On the face of it, this seems an entirely reasonable thing to post a tutorial about and as a topic, it has certainly been covered any number of times before.

However, in this particular tutorial, the example code illustrated the creation of a SQL query by iterating over the `$_POST` superglobal and using the values directly without any form of validation or sanitisation.

For any time-served developer this should be a horrifying state of affairs; that a tutorial posted in 2015 pays no help in preventing SQL injection attacks and proving the proverb “A little knowledge is a dangerous thing”.

Yet it is easy to forget that new coders take their very first steps onto a coding path every single day. Any such hapless copying and pasting this tutorial code into their endeavours would become vulnerable to those same SQL injection attacks, at least until they acquire the right kind of knowledge that would let them guard against these attacks.

Which brings us nicely back around considering what constitutes the right knowledge. Regrettably, at the time of writing there isn’t one definitive answer to that question. It is also dubious that there could ever be.

One of the great joys that a career in software development brings along with it is the fact that the learning process never ends. No matter how advanced a developer becomes in their mastery of the topic, there is always more to learn. On the one hand, this is because the topic itself is so vast. On the other, it is because the technology progresses relentlessly.

Complete mastery of application software development is entirely unobtainable for these two distinct reasons. At any given moment, there is already too much to fit into a single human brain. And today’s latest technique has every chance of being superseded tomorrow.
