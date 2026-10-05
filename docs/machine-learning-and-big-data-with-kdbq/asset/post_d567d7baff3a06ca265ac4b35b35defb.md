
## xviii PREFACE

Iverson and Falkoff then focused on the implementation of the programming language. An implementation on System/360 was made available at IBM in 1966 and released to the outside world in 1968.

In 1980, Iverson moved to I. P. Sharp Associates (IPSA), a Canadian software firm based in Calgary. There was then joined by Roger K. W. Hui (b. 1953) and Arthur Whitney (b. 1957). The three of them continued to work on APL, adding new ideas to the programming language. Hui, whose family emigrated to Canada from Hong Kong in 1966, was first exposed to APL at the University of Alberta. Whitney had a background in mathematics and had worked at APL at the University of Toronto and Stanford. He met Iverson for the first time before he joined APL, at the age of 11, in 1969. Iverson became his father's friend at Harvard. Whitney's family then lived in Alberta but visited him in house in Mount Kees. Iverson introduced Whitney to programming and APL.

In 1988, Whitney joined Morgan Stanley, who helped develop A+, an APL-like language with a smaller set of primitives functions optimized for processing large volumes of time series data. Unlike APL, A+ allowed functions to work up to nine formal parameters, used semicolons to separate statements (a single state could be split into multiple lines), used the last statement of a function as its result, and the so-called dependencies which functioned as global variables. The programming language is now available, http://aplus.dev/. Programs can also download the kap code, which includes the special characters used by APL and A+.

One summer in 1989, Whitney visited Iverson at Kiln Farm and produced "one on page and in afternoon" Hui (1992) – an interpreter fragment for the AT&T J81 computer. Hui wrote this fragment and on its basis developed an interpreter for APL variant, J. Unlike APL and A+, J used the ASCII character set. It included advanced features, such as support for parallel MIMD operations. Whitney's original fragment appears under the name Incabulum in an appendix in Hui's book, See Hui (1992)². Other ideas that Whitney found were into J: orienting primitives on the leading axes, using prefix rather than suffix for agreement, and total array ordering (Hui, 2006, 1995). Ken Iverson, his son, Eric Iverson, and Hui ended up working in a company called Soft in the 1990s–2000s.

Whitney met Morgan Stanley in 1993 and coined Kx Systems. On its basis he developed a k in-memory time set database called k. K Systems was under an exclusive agreement with UBS. It expired in 1996 and kx became generally available. ksql was added in 1998 as a layer on top of k. Some developers regard it as part of the k language. ksql includes SQL-like constructs, such as select. kdb+ was released in June 2003. This was more or less a total reward of kdb for 64-bit systems based on the 4th version of k and q, a macro language layer (a query language, the name on) defined in terms of k. Both q and k compile the same code which is executed in the kdb+ interpreter. For example type in q

> ¹It is also available online: http://code.software.com/Wiki/Eays/Incabulum.

## Preface

## xix

is the equivalent of @: in k. q is much more readable than k and most kdb+ developers write their code in q, not k.

The q programming language contains its own query syntax called q-sql, which in some ways resembles the traditional SQL.

## MOTIVATION FOR THIS BOOK

q and kdb+ stand in a special ground – as well as overlapping – the purely technical world of software engineering and the world of data science. On the one hand, they can be used for building data services that communicate with each other, whether this is simply to expose a time series database – q excels at – or a Chain of Complex Event Processing (CEP) engines calculating analytics and signals in real-time. On the other hand, q's fast execution onised time series enables its application to data science, hypothesis testing, research, pattern recognition, and general statistical and machine learning, being the fields more traditionally focused on quantitative analysts.

In practice, the distinction between the two worlds can become blurry: they are both very interconnected. An idea cannot be validated without rigorous and fast statistical analysis and backing, where the algorithms and their parameters are well understood, avoiding black-box solutions. It is then natural to expand our model validation into the actual predictive analytics. This is facilitated by the reliability, resilience, and scalability of kdb+.

q's notation as a thought of expression enables it to succeed at both tasks; its roots, traceable from APL and lambda calculus (Church, 1941), the vector language, the fast columnar database, and its query language q a unique all-in-one tool.

Although notorious as a language which "cannot be googled" due to its short name and lack of documentation, q and kdb+ are nowadays well-documented from the programming language and infrastructural perspectives, with some excellent sources of material both at https://code.kx.com/ and in books, such as Boris (2015); Psaris (2015).

Moreover, kdb+ is widely used in the market as a time series database with real-time analytics, whereas a lot of the data science, statistical and machine learning
