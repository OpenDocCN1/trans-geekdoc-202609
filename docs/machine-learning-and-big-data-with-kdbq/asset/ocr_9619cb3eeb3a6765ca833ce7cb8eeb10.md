# Preface

# xix

is the equivalent of @: in k. q is much more readable than k and most kdb+ developers write their code in q, not k.

The q programming language contains its own query syntax called q-sql1, which in some ways resembles the traditional SQL.

# MOTIVATION FOR THIS BOOK

q and kdb+ stand in a special ground – as well as overlapping – the purely technical world of software engineering and the world of data science. On the one hand, they can be used for building data services that communicate with each other, whether this is simply to expose a time series database – q excels at – or a Chain of Complex Event Processing (CEP) engines calculating analytics and signals in real-time. On the other hand, q's fast execution onised time series enables its application to data science, hypothesis testing, research, pattern recognition, and general statistical and machine learning, being the fields more traditionally focused on quantitative analysts.

In practice, the distinction between the two worlds can become blurry: they are both very interconnected. An idea cannot be validated without rigorous and fast statistical analysis and backing, where the algorithms and their parameters are well understood, avoiding black-box solutions. It is then natural to expand our model validation into the actual predictive analytics. This is facilitated by the reliability, resilience, and scalability of kdb+.

q's notation as a thought of expression enables it to succeed at both tasks; its roots, traceable from APL and lambda calculus (Church, 1941), the vector language, the fast columnar database, and its query language q a unique all-in-one tool.

Although notorious as a language which "cannot be googled" due to its short name and lack of documentation, q and kdb+ are nowadays well-documented from the programming language and infrastructural perspectives, with some excellent sources of material both at https://code.kx.com/ and in books, such as Boris (2015); Psaris (2015).

Moreover, kdb+ is widely used in the market as a time series database with real-time analytics, whereas a lot of the data science, statistical and machine learning (ML) work is done out of q, by extracting data into, interfacing with, Python or R.

The aim of this is to demonstrate that a lot of the power of q can be harnessed to deal with a lot of everyday data analysis, from data retrieval and data operations – specifically on large data sets – performing a range of statistical analysis with a few lines of code.

We move on to illustrate how we can quickly and productively apply ML algorithms on the data without having to leave our q instance, or necessarily trouble

> The word "fast" here is used in both senses of computational performance and rapid development, enabling the prototyping of ideas and rapid iteration of changes.