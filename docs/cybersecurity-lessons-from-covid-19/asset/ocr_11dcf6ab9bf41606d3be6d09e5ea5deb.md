chance of a breach of privacy but also allows more information to be given about where and when you might have been at risk.

If I subsequently test positive for infection, I upload my numbers (but not my name or any other location history that’s not part of the app) for the past two weeks to a public database. Daily, your phone checks the public database to see if any of the uploaded numbers is in its local database. If it finds my number, it tells you that at some point in the past two weeks you were close enough to an infected person to get infected or possibly that at 3 PM on Wednesday you were within Bluetooth range of a potentially contagious person at McDonald’s.

So, each day, everyone’s phone downloads 88,000 new numbers (the worldwide total of new daily cases yesterday: the number will vary) and compares the list against the numbers it has collected over the past 14 days.

Unlike a centralized approach, this does not require big horsepower to centrally crunch large volumes of data and there is no central cache of personally identifiable information. Of course, it also means that the authorities do not automatically get a list of names for contact tracing (unless you turn yourself in).

As I mentioned earlier, there are variations in regard to this basic idea. As noted, more or less data can be sent to the central database. Sometimes, the number pseudo-randomly generated is itself hidden further by hashing which hides the actual data but can be used for comparison. If this area interests you, there are a number of resources for further study. Possibly the first is the paper which gives the technical details of the DP-3T model, which allows for low-cost, decentralized, and hybrid models for proximity tracing. It also details the privacy risks of all three versions:

https://github.com/DP-3T/documents/blob/master/DP3T%20White%20Paper.pdf.

Apple and Google have agreed on a common protocol and provided an API (application programming interface) which can be used by other developers to create consistent and somewhat interoperable apps. (Interestingly, their beacon, called a proximity identifier, has a lifetime of 15 minutes.) An amalgamation of comments on their work can be found at:

http://catless.ncl.ac.uk/Risks/31/67#subj2.