
- A dictionary entry consisting of: name, opcode, and definition.
- Argument requirements include the argument count and their expected data types.
- A short alias or symbol for some of the more frequently used words.
- Either a postfix or prefix operation (most words are postfix).

During run-time, _epop_ checks that argument requirements are satisfied, helping to prevent errors. A useful diagnostic tool in that regard is the SEE word. An example of what SEE displays is shown here for the XOR word:

```
XOR ' SEE
XOR opcode: 191
0.0 RG5 opcode: 1. argc: 0
GT opcode: 14. argc: 2
SWAP opcode: 23. argc: 2
0.0 RG5 opcode: 1. argc: 0
GT opcode: 14. argc: 2
ADD opcode: 8. argc: 2
1 RG5 opcode: 1. argc: 0
EQ opcode: 13. argc: 2
```

Occasionally, errors arise when two or more unbound asynchronous words compete for the same data. To avoid this and to force synchronization, insert the SYNC operator, aliased as ";;". For example:

```
epop> word1 ;; word2
```

## B.11 LOCAL NAMESPACES

The word *let* is used in various functional programming languages to limit a variable's effect to the scope of a function or code block.

In Forth, a local scope or namespace may be considered synonymous with a word definition and the present data stack. For this context we can use the word LET, which uses the data stack to store a variable. For example:

```
{ 5 } payload WORD
{ payload ' EXEC var LET } local WORD
local
.S
... Data Stack ...
```

| Address | Index | Value |
|---------|-------|-------|
| 1BF114081800 | 0 | var.v |

Then, using the word TEL (yes, LET backwards), we can retrieve the data from a variable on the data stack, such as:

```
TEL . CR
5
```

In contrast to local variables are global variables, which have application throughout a program. Global variables are set using the “ ! ” symbol, an alias for SETV, and evaluated using the “ @ ” symbol, an alias for GETV. For example:

```
5 x !
x @ . ( emits 5 )
```

As you can see, local variables as defined above are more complex than global variables. Local variables also require relatively more system resources, which is one reason Forth founder Chuck Moore tries to avoid their use.2

2. Source: https://www.ultratechnology.com/moore4th.htm

## B.12 EPOP WORD SUMMARY

More than two-hundred epop word definitions are described in the epop Syntax Reference, on the web at https://sherpa.systemgoats.com.

## Resources

DOI: [10.1201/9781032687759-C](https://doi.org/10.1201/9781032687759-C)

## C.1 ONLINE RESOURCES

Internet resources for this book can be found at [https://sherpa.systemgoats.com](https://sherpa.systemgoats.com). These resources include programming tutorials, examples, and the *epop* language reference. Access to the site requires a user name and password. Interested parties should email access requests to [epop@systemgoats.com](mailto:epop@systemgoats.com). (Please indicate if you are an instructor, as exercise solutions will be made available.)

## C.2 SOURCE CODE - ONLINE

Source code is online for the following programs:
dec2bin.epop, base2dec.epop, anybase.epop, 2scomplement.epop, linearsearch.epop, randomsearch.epop, selectionsort.epop, factorial.epop, ncr.epop, fibonacci.epop, makeprogram.epop, ascii.epop, benchtest.epop, dfsearch.epop, distance.epop, normalize.epop, zscores.epop, wtdmean.epop, correlation.epop, regression.epop

## Bibliography

- [1] B. Marion, “Discrete mathematics: Support of and preparation for the study of computer science,” Journal of Computing Sciences in Colleges, vol. 16, pp. 190–199, 2000. DOI: https://dl.acm.org/doi/10.5555/357697.357730.
- [2] D. Stanat and D. McAllister, Discrete Mathematics in Computer Science. Prentice Hall Englewood Cliffs, N.J., 1977, vol. 16, pp. 190–199 (Stanat & McAllister's text may be considered the first definitive textbook on discrete mathematics.)
- [3] L. Brodie, Thinking Forth. Punchy Publishing, 2004, ISBN: 0976458705. DOI: https://thinking-forth.sourceforge.net.
- [4] J. McCarthy, “History of lisp,” Special Interest Group on Programming Languages, vol. 13, issue 8, pp. 173–185, 1978, ISSN: 0362-1340. DOI: https://dl.acm.org/doi/10.1145/960118.808387.
- [5] R. Bellman, R. Corporation, and K. M. R. Collection, Dynamic Programming, ser. Rand Corporation research study. Princeton University Press, 1957. (The curse-of-dimensionality term was perhaps originated by Bellman in the context of dynamic programming.), ISBN: 9780691079516. [Online]. Available: https://books.google.com/books?id=wdtoPwAACAAJ.
- [6] J. Pope, “Keeping up with the quants (book review),” Foresight: The International Journal of Applied Forecasting, vol. 38, Fall issue, pp. 38–40, 2013. DOI: https://ideas.repec.org/a/for/ijafaa/y2013i31p38-40.html.
- [7] G. Polya, How To Solve It: A New Aspect of Mathematical Method. Princeton University Press (Reprint edition), 2014, ISBN: 069116407X.
- [8] V. A. Spraul, Think Like a Programmer: An Introduction to Creative Problem Solving. No Starch Press, 2012, ISBN: 1593274246.
- [9] P. Vickers, How to Think Like a Programmer: Problem Solving for the Bewildered. Cengage Learning, 2008, ISBN: 1408065827.
- [10] R. Chassell, An Introduction to Programming in Emacs Lisp. GNU Press, 2004. (See section 1.1.1 on page 5.) ISBN: 1-882114-43-4. DOI: https://www.gnu.org/software/emacs/manual/html_node/eintr/Lisp-Atoms.html.
- [11] FreeBSD Handbook. The FreeBSD Documentation Project, 2021. (Details for setting Unix file permissions are found in chapter section 3.4.) DOI: https://www.freebsdhandbook.com/basics/#permissions.
- [12] ARM, Getting started with arm assembly language, 2023. DOI: https://documentation-service.arm.com/static/64e7245d04d0d65e67136806.
- [13] B. Kahanwal, “Abstraction level taxonomy of programming language frameworks,” International Journal of Programming Languages and Applications, vol. 3.4, Oct. 2013. DOI: https://www.researchgate.net/publication/258499542_Abstraction_Level_Taxonomy_of_Programming_Language_Frameworks.
- [14] A. Ohori, “A curry-howard isomorphism for compilation and program execution,” in Typed Lambda Calculi and Applications, J.-Y. Girard, Ed., Berlin, Heidelberg: Springer Berlin Heidelberg, 1999, pp. 280–294, ISBN: 978-3-540-48959-7.
- [15] S. F. Bacon, The Advancement of Learning. 1605, vol. 8. (This quote of Sir Francis Bacon may describe a recursive function, wherein its self-reference occurs only until there is doubt.)
- [16] R. Bertrand, Introduction to Mathematical Philosophy. Macmillan, 1919, p. 6. DOI: https://archive.org/details/cu31924001598188.
- [17] G. Peano, Arithmetics Principia, Nova Methodo Exposita. unknown, 1889, pp. 23-29. DOI: https://github.com/mdnahas/Peano_Book/blob/master/Peano.pdf.
- [18] A. Church and J. Rosser, “Some properties of conversion,” Transactions of the American Mathematical Society, vol. 39, pp. 472–482, 1936. DOI: https://www.ams.org/journals/tran/1936-039-03/S0002-9947-1936-1501858-0/S0002-9947-1936-1501858-0.pdf.
- [19] D. Hoyt, Let Over Lambda—50 Years of Lisp. Lulu, 2008. (A good discussion about let-over-lambda can be found in chapter 2 of Hoyt's book.) ISBN: 978-1-4357-1275-1, ISBN: 978-1-4357-1275-1. DOI: https://letoverlambda.com.
- [20] G. Michaelson, An Introduction To Functional Programming Through Lambda Calculus. Dover, 2011. (A comprehensive coverage of lambda calculus, including syntax in Backus-Naur Form and programming language implementations in LISP and Standard ML.) ISBN: 978-0-486-47883-8.
- [21] R. Giegerich, C. Meyer, and P. Steffen, “A discipline of dynamic programming over sequence data,” Science of Computer Programming, vol. 51, no. 3, pp. 215–263, 2004, ISSN: 0167-6423. DOI: https://doi.org/10.1016/j.scico.2003.12.005. [Online]. Available: https://www.sciencedirect.com/science/article/pii/S0167642304000176.
- [22] C. Okasaki, “Purely functional random-access lists,” in Proceedings of the Seventh International Conference on Functional Programming Languages and Computer Architecture, ser. FPCA ‘95. (Perhaps the first use of Random Access List was by Okasaki in this paper.) La Jolla, California, USA: Association for Computing Machinery, 1995, pp. 86–95, ISBN: 0897917197. DOI: 10.1145/224164.224187. [Online]. Available: https://doi.org/10.1145/224164.224187.
