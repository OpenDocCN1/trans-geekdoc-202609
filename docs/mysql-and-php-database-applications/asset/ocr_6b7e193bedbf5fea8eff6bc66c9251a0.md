# # Chapter 1

# # Database Design with MySQL

IN THIS CHAPTER

+   - Identifying the problems that led to the creation of the relational database
- Learning the normalization process
- Taking a look at database features that MySQL does not currently support

THE BULK OF THIS CHAPTER is for those of you who have made it to the early 21st century working with relational databases. If you're a seasoned database pro, having worked with Oracle, Sybase, or even something like Microsoft Access or Paradox, you may want to skip this little lesson on database theory. However, I suggest that you look at the final section of this chapter, where I discuss some of MySQL's weirder points. MySQL's implementation of SQL is incomplete, so it may not support what you might be looking for.

# # Why Use a Relational Database?

If you're still here and ready to read with rapt attention about database theory and the wonders of normalization, you probably don't know much about the history of the relational database. You may not even care. For that reason, IBM in brief. Dr. E. F. Cobb was a research scientist at IBM in the 1960s. A mathematician by training, he was unhappy with the available models of data storage. He found that all the available methods were prone to error and redundancy. He worked on these problems and, in 1970, published a paper titled “A Relational Model of Data for Large Shared Databanks,” in all honesty, nothing has been the same.

A programmer named Larry Ellison read the paper and worked on software that could put Dr. Cobb's theories into practice. If you've been a resident of this planet over the past 20 years, you may know that Ellison's product and company took the name Oracle and that he is now one of the richest men in the world. His earliest product was designed for huge mainframes. Responding to market demands over the years, Oracle, and many other companies that have sprung up since, have designed systems with a variety of features geared toward a variety of