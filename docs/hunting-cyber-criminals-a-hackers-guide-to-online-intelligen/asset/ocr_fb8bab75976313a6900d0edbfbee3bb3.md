# # CHAPTER
# 14

14 Publicly Accessible Data Storage

# # Publicly Accessible Data Storage

Discovering data breaches (or data leaks) is never an easy thing. What I mean by that is figuring out how to deal with the situation once you have discovered the breach or leak is, in my experience, the most difficult part of the entire process.
This chapter will focus on both sides of that story. We will look at methods for discovering data in several common NoSQL databases like MongoDB and Elasticsearch, as well as data located on publicly accessible cloud storage platforms such as Amazon buckets and Digital Ocean spaces. I will also reveal some of my personal discoveries and experiences surrounding those discoveries.
But first, a word from Bob Dichenko, a man who has personally uncovered more high-profile data leaks that anyone else knows.

> EXTIP: BOB DIACHENKO

There is no stable pattern that I will use [to find data] every time, I change [the methods] based on the results that I receive. And I also deliberately to minimize the searching of results. When I look through reports, I always do that manually. I do this in the past, when I have overlooked important information and made a list of mistakes when I rely on automated scripts.

When I started reviewing the results, I was surprised to see that many interesting items were overlooked. So then I started to go through the results myself, which is how I come up with my current process.