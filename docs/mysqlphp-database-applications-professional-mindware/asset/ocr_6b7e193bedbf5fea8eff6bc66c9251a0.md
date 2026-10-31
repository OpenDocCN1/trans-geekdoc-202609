# Chapter 1

# Database Design with MySQL

# IN THIS CHAPTER

+   - Identifying the problems that led to the creation of the relational database
+   - Learning the normalization process
+   - Taking a look at database features that MySQL does not currently support

THE BULK OF THIS CHAPTER is for those of you who have made it to the early 21st century without working with relational databases. If you're a seasoned database pro, having worked with Oracle, Sybase, or even something like Microsoft Access or Paradox, you may want to skip this little lesson on database theory. However, I do suggest that you look at the final section of this chapter, where I discuss some of MySQL's weirder points. MySQL's implementation of SQL is incomplete, so it may not support some of what you might be looking for.

# Why Use a Relational Database?

If you're still here and are ready to read with rapt attention about database theory and the wonders of normalization, you probably don't know much about the history of the relational database. You may not even care. For that reason, I'll keep this very brief. Dr. E. F. Codd was a research scientist at IBM in the 1960s. A mathematician by training, he was unhappy with the available models of data storage. He found that all the available methods were prone to error and redundancy. He worked on these problems and then, in 1970, published a paper with the rousing title “A Relational Model of Data for Large Shared Databanks.” In all honesty, nothing has been the same since.

A programmer named Larry Ellison read the paper and started work on software that could put Dr. Codd's theories into practice. If you've been a resident of this planet over the past 20 years, you may know that Ellison's product and company took the name Oracle and that he is now one of the richest men in the world. His earliest product was designed for huge mainframe systems. Responding to market demands over the years, Oracle, and many other companies that have sprung up since, have designed systems with a variety of features geared toward a variety of