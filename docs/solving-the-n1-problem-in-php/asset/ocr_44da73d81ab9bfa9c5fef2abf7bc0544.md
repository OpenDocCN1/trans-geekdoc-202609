# 1. Introduction

# The Slow Reporting Script

The web page was taking three hours to load. Let that sink in for a moment: three hours. The code backing the page was a reporting script written in PHP, attempting to build 40,000 entity objects from 2 million database rows. Sometimes the page never loaded at all. At least the client could tell when it failed, because a big ugly error popped up in the browser window. Unfortunately that was also around the three hour point. The client was understandably frustrated.

I was assigned to troubleshoot the problem. It turned out the cause was not that the database was optimized. It was not the number of rows being returned. It was not even the number of objects being built.

No, the cause was the number of queries being issued from the reporting script. The high volume of queries, in turn, was a result of how the script was assembling the entity objects. When I say "high volume", I mean two hundred thousand and one queries. These 200,000+ queries were used to build each root entity along with each of its five associated collections and entities. No wonder the script was taking three hours to finish!

After discovering this, I was able to apply the "query-and-stitch" technique presented in this book to refactor how the entity objects were assembled. Over the course of a few days of refactoring I was able to reduce the load time from 3+ hours to just under 6 minutes. That's a 30x improvement, and still so by typical standards, it was much more bearable for the client. (Later refactorings improved the load time ever.)

The causes leading to the terrible performance of the Slow Reporting Script have a name: N+1 Problem. The problem has various aliases, such as the "1+N problem", "N+1 queries", "SELECT N+1", and so on, but they all refer to the same thing.