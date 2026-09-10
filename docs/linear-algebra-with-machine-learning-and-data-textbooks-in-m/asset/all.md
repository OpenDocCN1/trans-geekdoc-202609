![](images/cover.jpg)

![Cover: Linear Algebra With Machine Learning and Data, Textbooks in Mathematics, written by Crista Arangala, published by CRC Press, Taylor and Francis Group, Boca Raton, London, New York, CRC Press is an imprint of the Taylor and Francis Group, an informa business, a Chapman and Hall book.](images/cover.jpg)

**Textbooks in Mathematics**

Series editors:

Al Boggess, Kenneth H. Rosen

**Transition to Advanced Mathematics**

*Danilo R. Diedrichs and Stephen Lovett*

**Modeling Change and Uncertainty**

Machine Learning and Other Techniques

*William P. Fox and Robert E. Burks*

**Abstract Algebra**

A First Course, Second Edition

*Stephen Lovett*

**Multiplicative Differential Calculus**

*Svetlin Georgiev, Khaled Zennir*

**Applied Differential Equations**

The Primary Course

*Vladimir A. Dobrushkin*

**Introduction to Computational Mathematics: An Outline**

*William C. Bauldry*

**Mathematical Modeling the Life Sciences**

Numerical Recipes in Python and MATLAB^™

*N. G. Cogan*

**Classical Analysis**

An Approach through Problems

*Hongwei Chen*

**Classical Vector Algebra**

*Vladimir Lepetic*

**Introduction to Number Theory**

Mark Hunacek

**Probability and Statistics for Engineering and the Sciences with Modeling using R**

*William P. Fox and Rodney X. Sturdivant*

**Computational Optimization: Success in Practice**

*Vladislav Bukshtynov*

**Computational Linear Algebra: with Applications and MATLAB**® **Computations**

*Robert E. White*

**Linear Algebra With Machine Learning and Data**

Crista Arangala

[https://www.routledge.com/Textbooks-in-Mathematics/book-series/CANDHTEXBOOMTH](https://www.routledge.com/Textbooks-in-Mathematics/book-series/CANDHTEXBOOMTH)

First edition published 2023

by CRC Press

6000 Broken Sound Parkway NW, Suite 300, Boca Raton, FL 33487-2742

and by CRC Press

4 Park Square, Milton Park, Abingdon, Oxon, OX14 4RN

*CRC Press is an imprint of Taylor & Francis Group, LLC*

© 2023 Taylor & Francis Group, LLC

Reasonable efforts have been made to publish reliable data and information, but the author and publisher cannot assume responsibility for the validity of all materials or the consequences of their use. The authors and publishers have attempted to trace the copyright holders of all material reproduced in this publication and apologize to copyright holders if permission to publish in this form has not been obtained. If any copyright material has not been acknowledged please write and let us know so we may rectify in any future reprint.

Except as permitted under U.S. Copyright Law, no part of this book may be reprinted, reproduced, transmitted, or utilized in any form by any electronic, mechanical, or other means, now known or hereafter invented, including photocopying, microfilming, and recording, or in any information storage or retrieval system, without written permission from the publishers.

For permission to photocopy or use material electronically from this work, access [www.copyright.com](https://www.copyright.com) or contact the Copyright Clearance Center, Inc. (CCC), 222 Rosewood Drive, Danvers, MA 01923, 978-750-8400. For works that are not available on CCC please contact [mpkbookspermissions@tandf.co.uk](mailto:mpkbookspermissions@tandf.co.uk)

*Trademark notice*: Product or corporate names may be trademarks or registered trademarks and are used only for identification and explanation without intent to infringe.

**Library of Congress Cataloging-in-Publication Data**

Names: Arangala, Crista, author.

Title: Linear algebra with machine learning and data / Crista Arangala.

Description: First edition. | Boca Raton : CRC Press, 2023. | Series: Textbooks in mathematics | Includes bibliographical references and index.

Identifiers: LCCN 2022047264 | ISBN 9780367458393 (hardback) | ISBN 9781032458649 (paperback) | ISBN 9781003025672 (ebook)

Subjects: LCSH: Algebras, Linear--Textbook. | Machine learning--Mathematics--Textbooks. | Data mining--Mathematics--Textbooks.

Classification: LCC QA184.2 .A73 2023 | DDC 518/.43--dc23/eng20230203

LC record available at [https://lccn.loc.gov/2022047264](https://lccn.loc.gov/2022047264)

ISBN: 978-0-367-45839-3 (hbk)

ISBN: 978-1-032-45864-9 (pbk)

ISBN: 978-1-003-02567-2 (ebk)

DOI: [10.1201/9781003025672](https://doi.org/10.1201/9781003025672)

Typeset in CMR10

by KnowledgeWorks Global Ltd.

*Publisher's note: This book has been prepared from camera-ready copy provided by the authors*.

# Acknowledgments

I want to thank the faculty of Elon University and in particular the Elon Mathematics and Statistics Department for always being on the edge of innovative teaching and embracing important initiatives around exposing students in data competency. Many students have also contributed to the success of this project through undergraduate research and classroom experiences. I wish to thank Amy Moore, Abby Weber, Matthew Davenport, Rachel Dietert, Katie Everitt, Lauren Hanchar, Mary Hermes, Xuan Huynh, Adam Jockle, Gautam Kotwal, Clayton McLamb, Maia Sirabian, Sarina Smith, William Tunis, Ashley Vann, and Parker Verlander.

In addition, I would like to recognize the support for this text from Elon University's Faculty Research and Development program.

# Preface

This text is meant to be used for a second course in applications of Linear Algebra to Data Analytics, with a supplemental chapter on Decision Trees and their applications in regression analysis. Throughout the text a basic knowledge of the concepts in a first Linear Algebra course is assumed; however, an overview of key concepts is presented in the Introduction and as needed throughout the text.

Knowledge of mathematical techniques related to data analytics, and exposure to interpretation of results within a data analytics context, are particularly valuable for students studying undergraduate mathematics. Each chapter of this text takes the reader through several relevant case studies using real world data. Some case study applications address gerrymandering issues, modeling the spread of disease, digital facial recognition, and racial inequities in higher education. Readers are encouraged to replicate results from the presented case studies. All data sets, as well as Python and R syntax, are provided to the reader through links to Github documentation. Following each chapter is a short exercise set in which students are encouraged to use technology to apply their expanding knowledge of linear algebra as it is applied to data analytics.

The text can be considered in two different but overlapping general data analytics categories: clustering and interpolation. [Chapters 1](#chapter1.xhtml) and [3](#chapter3.xhtml) focus on eigenvalues and singular values, as well as their associated vectors, that are of key importance in clustering techniques, such as Principal Component Analysis. [Chapters 4](#chapter4.xhtml) through [6](#chapter6.xhtml) focus on techniques specific to interpolation models. Integrated throughout this text, the reader will also find many machine learning techniques of interest, such as hidden Markov chains in [Chapter 2](#chapter2.xhtml), neural networks in [Chapter 5](#chapter5.xhtml), decision trees and forests in [Chapter 6](#chapter6.xhtml), and random matrices in [Chapter 7](#chapter7.xhtml).

# Introduction

In this introduction, we give an overview of background expectations. Also, for those who are looking to use this book for a first course in Mathematical Methods in Data Analytics, an overview of necessary Linear Algebra concepts is presented here and embedded throughout the text.

The entire text is focused on applications of Linear Algebra in Data Analytics, so we begin with a quick overview of matrix algebra. Matrix *A* has entry *a*[*i*, *j*] in row *i* and column *j*.

  
$$\\begin{array}{l} {A = \\left( \\begin{array}{lllll} a\_{1,1} & a\_{1,2} & a\_{1,3} & \\ldots & a\_{1,m} \\\\ a\_{2,1} & a\_{2,2} & a\_{2,3} & \\ldots & a\_{2,m} \\\\ \\vdots & \\ddots & \\ddots & \\ddots & \\vdots \\\\ a\_{n,1} & a\_{n,2} & a\_{n,3} & \\ldots & a\_{n,n} \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

The dimensions of *A* are *n* × *m*. A matrix is **square** if it has the same number of rows as it does columns.

Matrix addition is entry-wise. That is, that if *A* and *B* are matrices with the same dimensions, then (*A* + *B*)[*i*, *j*] = *a*[*i*, *j*] + *b*[*i*, *j*].

If one wishes to multiply each entry of a matrix by a constant, also called a scalar, this is referred to as scalar multiplication.

The transpose of *A*, denoted *A*^(*T*), is an *m* × *n* matrix where

  
$$\\begin{array}{r} {A\_{i,j}^{T} = A\_{j,i}.} \\\\ \\end{array}$$  

A matrix *A* is **symmetric** if *A* = *A*^(*T*).

The **Hadamard product**, also known as the entry-wise product, of two matrices of the same dimensions, *A* and *B*, is

  
$$\\begin{array}{r} {A{^\\circ}B,} \\\\ \\end{array}$$  

where the (*i*, *j*)^(th) entry of *A*^∘*B* is *a*[*i*, *j*]*b*[*i*, *j*].

In order to multiply a *m* × *n* matrix *A* on the right by a matrix *B*, the number of rows of *B* must be equal to the number of columns of matrix *A*. That is *B* must be a *n* × *p* matrix for some natural number *p*.

![](images/mathfm_14.jpg)

The entries of the product of *AB*

  
$$\\begin{array}{r} {AB\_{i,j} = {\\sum\\limits\_{k = 1}^{n}a\_{i,k}}b\_{k,j}.} \\\\ \\end{array}$$  

The **identity matrix**, *I*, is the a square matrix such that

  
$$\\begin{array}{r} {I\_{i,j} = 1\\text{~if~}i = j,\\text{~and~}0\\text{~otherwise}\\text{.~}} \\\\ \\end{array}$$  

If *A* is an *m* × *n* matrix and *I* is the *m* × *m* identity matrix then

  
$$\\begin{array}{r} {AI = IA = A.} \\\\ \\end{array}$$  

If *A* is a square matrix, we can also talk about the powers of *A*, where *A*² = *A* ⋅ *A* and exponential rules of matrices hold.

  
$$\\begin{aligned} A^{r + s} & {= A^{r} \\cdot A^{s}} \\\\ {(A^{r})}^{s} & {= A^{rs}} \\\\ \\end{aligned}$$  

In many applications of Linear Algebra, the goal of the problem is to solve for *x* in the system *A**x* = *b*, where *A* is an *n* × *n* matrix and *x* and *b* are *n* × 1 matrices, also called vectors in ℝ^𝕟.

If *A* is **invertible**, also called **non-singular**, then there exists a matrix *A*^( − 1) such that

  
$$\\begin{array}{r} {A^{- 1} \\cdot A = A \\cdot A^{- 1} = I} \\\\ \\end{array}$$  

If *A* is not invertible, then we say that *A* is **singular**.

A system of *m* equations in *n* variables

  
$$\\begin{aligned} {a\_{1,1}x\_{1} + a\_{1,2}x\_{2} + \\ldots + a\_{1,n}x\_{n}} & {= b\_{1}} \\\\ {a\_{2,1}x\_{1} + a\_{2,2}x\_{2} + \\ldots + a\_{2,n}x\_{n}} & {= b\_{2}} \\\\ & \\vdots \\\\ {a\_{m,1}x\_{1} + a\_{m,2}x\_{2} + \\ldots + a\_{m,n}x\_{n}} & {= b\_{m}} \\\\ \\end{aligned}$$  

can be written in the matrix form *A**x* = *b* where *A* is a *m* × *n* coefficient matrix and *x* and *b* are *m* × 1 matrices.

If *A* is square and invertible then the system *A**x* = *b* has exactly one solution, *x* = *A*^( − 1)*b*. If *A* is not square or is not invertible, then it is possible for the system have either no solutions or infinitely many solutions. It is also important to note that if $Ax = \\overset{\\rightarrow}{0}$ and *A* is invertible then the only solution is $x = \\overset{\\rightarrow}{0}$, also called the **trivial solution**.

The **determinant** of a square matrix *A* maps a matrix to a real number, |*A*|. There are a variety of techniques for calculating the determinant of a matrix, including cofactor expansion and formulas for small matrices such as 2 × 2 matrices.

  
$$\\begin{array}{l} {\\left| \\begin{array}{ll} a\_{1,1} & a\_{1,2} \\\\ a\_{2,1} & a\_{2,2} \\\\ \\end{array} \\right| = a\_{1,1}a\_{2,2} - a\_{1,2}a\_{2,1}.} \\\\ \\end{array}$$  

In order to perform **cofactor expansion** on a *n* × *n* matrix, *A*, where *n* > 2, choose a row, *i*, or column, *j* to expand on. Then

  
$$\\begin{array}{l} {\\left| A \\right| = \\sum\\limits\_{j = 1}^{n}{( - 1)}^{i + j}a\_{i,j}M\_{i,j} = \\sum\\limits\_{i = 1}^{n}{( - 1)}^{i + j}a\_{i,j}M\_{i,j},} \\\\ \\end{array}$$  

where *M*[*i*, *j*] is the (*i*, *j*)^(th) **minor** and is the determinant of the (*n* − 1) × (*n* − 1) submatrix of *A* created by deleting the *i*^(th) row and *j*^(th) column of *A*.

Most importantly, the fact that determining if a square matrix is invertible is equivalent to determining if |*A*| ≠ 0.

[Chapter 1](#chapter1.xhtml) focuses on the applications of Linear Algebra to Graph Theory, where powers of matrices, bases, eigenvalues, and eigenvectors are heavily implemented. Eigenvalues and eigenvectors will be reviewed in [Chapter 1](#chapter1.xhtml). A brief review of bases is presented here.

A set of vectors *S* = {*v*[1], *v*[2],…, *v*[*n*]} is called **linearly independent** if the equation

  
$$\\begin{array}{r} {k\_{1}v\_{1} + k\_{2}v\_{2} + \\ldots + k\_{n}v\_{n} = 0} \\\\ \\end{array}$$  

has only the trivial solution, *k*[1] = *k*[2] = … = *k*[*n*] = 0. If the set is not linearly independent, we called the set **linearly dependent**.

If *v*[1], *v*[2], …, *v*[*n*] are vectors in ℝ^(*n*) and are the columns of a matrix *A*, then

  
$$\\begin{array}{l} {A{= \\left( \\begin{array}{llll} | & | & \\ldots & | \\\\ | & | & \\ldots & | \\\\ v\_{1} & v\_{2} & \\ldots & v\_{n} \\\\ | & | & \\ldots & | \\\\ | & | & \\ldots & | \\\\ \\end{array} \\right)}} \\\\ {{A\\left( \\begin{array}{l} k\_{1} \\\\ k\_{2} \\\\ \\vdots \\\\ k\_{n} \\\\ \\end{array} \\right)}{= \\left( \\begin{array}{l} 0 \\\\ 0 \\\\ \\vdots \\\\ 0 \\\\ \\end{array} \\right).}} \\\\ \\end{array}$$  

has only the trivial solution if *A* is invertible.

If *S* = {*v*[1], *v*[2],…, *v*[*n*]}, *v*[*i*] ∈ ℝ^(*n*), then we say that *w* ∈ ℝ^(*n*) can be written as a **linear combination** of the vectors in *S* if there exists *k*[1], *k*[2], …, *k*[*n*] such that

  
$$\\begin{array}{r} {w = k\_{1}v\_{1} + k\_{2}v\_{2} + \\ldots + k\_{n}v\_{n}.} \\\\ \\end{array}$$  

We say that *S* **spans** ℝ^(*n*) if every vector *w* ∈ ℝ^(*n*) can be written as a linear combinations of the vectors in *S*.

If a set *S* is a set of *n* linearly independent vectors which spans ℝ^(*n*) then *S* is a **basis** for ℝ^(*n*).

The main focus of [Chapter 2](#chapter2.xhtml), Stochastic Processes, is Markov Chains. Some basic probability theory and knowledge of eigenvalues and eigenvectors would be particularly useful in this chapter. Related to probability theory, it is helpful for the reader to have some understanding of probability theory, particularly the relationship between joint and conditional probability. For a basic overview of probability theory, one can refer to [Section 5.1](#chapter5.xhtml#sec5_1) prior to reading [Chapter 2](#chapter2.xhtml). For the most part, one could read [Chapter 2](#chapter2.xhtml) independently of [Chapter 1](#chapter1.xhtml); however, the beginning stages of [Chapter 2](#chapter2.xhtml) do rely on basic knowledge of graph theory.

[Chapter 3](#chapter3.xhtml) focuses on the implementation of Singular Value Decomposition and Principal Component Analysis in the context of data science. A good understanding of eigenvalues and eigenvectors is instrumental in this chapter. An overview of inner product spaces and orthogonality is provided. This particular chapter also becomes fairly technology heavy with several exercises relying on R or Python knowledge. Again, [Chapter 3](#chapter3.xhtml) can be taught, for the most part, independently of the previous 2 chapters, although further chapters benefit from the knowledge of [Chapter 3](#chapter3.xhtml) material.

Both [Chapters 4](#chapter4.xhtml) and [5](#chapter5.xhtml) focus on predictive models. Where [Chapter 4](#chapter4.xhtml) focuses more on traditional interpolation techniques such as Chebyshev, Hermite, and Lagrange interpolation, [Chapter 5](#chapter5.xhtml) steps back and takes a quick look at probability theory and matrix calculus before connecting the material from [Chapter 4](#chapter4.xhtml) to machine learning and neural network techniques. In these sections, some knowledge of calculus is helpful, since there is a focus on optimizing cost functions. Again, a good understanding of technology is important in [Chapter 5](#chapter5.xhtml), as iterative methods become significantly important in neural network techniques.

[Chapter 6](#chapter6.xhtml) focuses on implementing the concepts of previous chapters in decision trees. Several different takes on decision trees will be presented in this chapter, including decision tree regression, Fourier transformations, and random forests.

Finally, many models are built around random matrices; the focus is on [Chapter 7](#chapter7.xhtml). The discussion in [Chapter 7](#chapter7.xhtml) relies heavily on probability theory, introduced in [Chapter 5](#chapter5.xhtml), and knowledge of eigenvalues and eigenvectors. In [Chapter 7](#chapter7.xhtml), the **Kroenecker product**, also called the **tensor product** is also used.

If *A* is an *m* × *n* matrix and *B* is a *p* × *q* matrix then the Kroenecker product,

  
$$\\begin{array}{l} {A \\otimes B = \\left( \\begin{array}{lll} {a\_{1,1}B} & \\ldots & {a\_{1,n}B} \\\\ \\vdots & & \\vdots \\\\ {a\_{m,1}B} & \\ldots & {a\_{m,n}B} \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

A matrix *A* is **skew-symmetric** if *A*^(*T*) =  − *A*. In [Chapter 7](#chapter7.xhtml), we specifically employ the Kronecker product of a skew-symmetric matrix with the identity matrix as is seen in [Example 0.6](#chapter101.xhtml#exam0_6).

Throughout the text, readers are encouraged to use a critical eye when it comes to ethics of data analytics. Additionally, when choosing a model, the reader should take into account the application in order to chose the most meaningful model in context.

# 1Graph Theory

DOI: [10.1201/9781003025672-1](https://doi.org/10.1201/9781003025672-1)

## 1.1 Basic Terminology

When studying data, data scientists are most concerned with the relationships or connections between the pieces of data in a network. In this chapter, we explore those networks in terms of graph theory and see how these ideas tie back to data science and linear algebra.

A **graph**, *G*, can be represented by a set of **vertices** or **nodes**, *V*, and a set of **edges**, *E*, where each edge in *E* connects two vertices in *V*.

The number of vertices in a graph, *G*, is called the **order** of the graph and is denoted by |*V*|. The number of edges in a graph, *G*, is called the **size** and is denoted by |*E*|.

An edge is said to be **incident** to vertices *v*[*i*] and *v*[*j*] if it connects the two vertices. We call vertices *v*[*i*] and *v*[*j*] **endpoints** of this edge.

Vertex *v*[*i*] is said to be **adjacent** to vertex *v*[*j*] if there is an edge incident to both vertex *v*[*i*] and vertex *v*[*j*]. The **degree** of a vertex is the number of incident edges to that vertex.

Notice that in the graph in [Figure 1.1](#chapter1.xhtml#fig1_1), |*V*| = 6 and |*E*| = 12. Vertex *v*[4] is adjacent to every other vertex while *v*[1] is adjacent to *v*[2], *v*[3], and *v*[4], and thus *d**e**g**r**e**e*(*v*[1]) = 3 and *d**e**g**r**e**e*(*v*[4]) = 5.

![Figure 1.1 |V| = 6,|E| = 12, degree (v\_{1}) = 3, and degree (v\_{4}) = 5.](images/fig1_1.jpg)

[Figure 1.1](#chapter1.xhtml#b1fig1_1) |*V*| = 6, |*E*| = 12, degree (*v*[1]) = 3, and degree (*v*[4]) = 5.

An edge with only one endpoint is called a **loop**.

Notice that if a vertex is adjacent to itself via a loop, that edge contributes two edges to the degree of that vertex. The handshaking theorem emphasizes that each edge is incident to two vertices, which may or may not be unique, and is counted twice when calculating the sum of the degrees of the graph.

If two or more edges have the same endpoints, then they are called **multiple edges**.

[Figure 1.2](#chapter1.xhtml#fig1_2) shows a graph with multiple edges between vertices *v*[1] and *v*[2] and a loop from vertex *v*[3] to itself. Vertex *v*[3] has a degree of 4, where the loop from *v*[3] to itself contributes two edges to the degree of *v*[3]. Vertices *v*[1] and *v*[2] both have a degree of 3. The multiple edges between *v*[1] and *v*[2] contribute 2 edges to the degree of both *v*[1] and *v*[2].

![Figure 1.2 Example of a graph with a loop and multiple edges.](images/fig1_2.jpg)

[Figure 1.2](#chapter1.xhtml#b1fig1_2) Example of a graph with a loop and multiple edges.

A **subgraph** of graph *G* is another graph containing a subset of vertices from *V* and all of the edges from *E* that connect pairs of vertices in the subset.

There are many subgraphs of the graph displayed in [Figure 1.1](#chapter1.xhtml#fig1_1); one example can be seen in [Figure 1.3](#chapter1.xhtml#fig1_3).

![Figure 1.3 Example of a subgraph of the graph in Figure 1.1.](images/fig1_3.jpg)

[Figure 1.3](#chapter1.xhtml#b1fig1_3) Example of a subgraph of the graph in [Figure 1.1](#chapter1.xhtml#fig1_1).

For each graph, there is a corresponding **adjacency matrix**, *A*, where

  
$$\\begin{array}{l} {A\_{i,j} = \\left\\{ \\begin{array}{ll} {1,} & {\\text{~if~vertex~}v\_{i}\\text{~is~adjacent~to~vertex~}v\_{j},} \\\\ {0,} & {\\text{~otherwise}\\text{.}} \\\\ \\end{array}~ \\right.} \\\\ \\end{array}$$  

Notice the loop in [Figure 1.4a](#chapter1.xhtml#fig1_4) from vertex *v*[1] to itself. This is represented in the adjacency matrix *A*, *a*[1, 1] = 1.

![Figure 1.4 a. Graph with a loop, b. Graph with no loops.](images/fig1_4.jpg)

[Figure 1.4](#chapter1.xhtml#b1fig1_4) a. Graph with a loop, b. Graph with no loops.

Note also that the vertex *v*[4] is not adjacent to any vertex in [Figure 1.4a](#chapter1.xhtml#fig1_4) and thus every entry of *A* in row 4 and column 4 has a value of 0.

[Figure 1.4b](#chapter1.xhtml#fig1_4) is an example of a graph with no loops in which all vertices are adjacent to at least one other vertex in the graph.

The corresponding adjacency matrices are

  
$$\\begin{array}{l} {A = \\left( \\begin{array}{llll} 1 & 1 & 1 & 0 \\\\ 1 & 0 & 1 & 0 \\\\ 1 & 1 & 0 & 0 \\\\ 0 & 0 & 0 & 0 \\\\ \\end{array} \\right)\\text{~and~}B = \\left( \\begin{array}{llll} 0 & 1 & 1 & 1 \\\\ 1 & 0 & 1 & 0 \\\\ 1 & 1 & 0 & 1 \\\\ 1 & 0 & 1 & 0 \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

A **path** from a vertex *v*[*i*] to a vertex *v*[*j*] is a sequence of incident edges that connect *v*[*i*] to *v*[*j*]. For example, in [Figure 1.4b](#chapter1.xhtml#fig1_4), *v*[1]*v*[2]*v*[3] is a two-step path between *v*[1] and *v*[3]. Note that a path is also a subgraph of the entire graph.

A **connected graph** is a graph in which there is a path between each pair of vertices.

[Figure 1.4b](#chapter1.xhtml#fig1_4) is an example of a graph that is connected while [Figure 1.4a](#chapter1.xhtml#fig1_4) is disconnected. As we noted earlier, the adjacency matrices affiliated with a disconnected graph contain at least one row and column of zeros.

A **tree graph** is a connected graph in which there is no path between a vertex and itself. Some examples of tree graphs and their corresponding adjacency matrices can be seen in [Figure 1.5](#chapter1.xhtml#fig1_5).

![Figure 1.5 Examples of tree graphs.](images/fig1_5.jpg)

[Figure 1.5](#chapter1.xhtml#b1fig1_5) Examples of tree graphs.

In this text, we will be focusing on **simple connected graphs**, those connected graphs without multiple edges and loops, unless otherwise noted.

All these adjacency matrices, *A*, presented thus far is **symmetric**, meaning that

  
$$\\begin{array}{r} {A = A^{T}.} \\\\ \\end{array}$$  

This is because the edges between each pair of vertices do not have a defined direction.

More formally, a simple connected graph is called **undirected** if, for each pair of adjacent vertices, *v*[*i*] and *v*[*j*], if *v*[*i*] is adjacent to *v*[*j*], then *v*[*j*] is also adjacent to *v*[*i*].

Each of the examples presented in [Figures 1.4](#chapter1.xhtml#fig1_4) and [1.5](#chapter1.xhtml#fig1_5) are undirected graphs. [Figure 1.6](#chapter1.xhtml#fig1_6) shows an example of a directed graph.

![Figure 1.6 Example of a directed graph.](images/fig1_6.jpg)

[Figure 1.6](#chapter1.xhtml#b1fig1_6) Example of a directed graph.

When presented with a directed graph, we talk about the **in-degree** and the **out-degree** of a vertex, where the in-degree is the number of edges coming into the vertex and the out-degree is the number of edges coming out of a vertex.

In [Figure 1.6](#chapter1.xhtml#fig1_6),

  
$$\\begin{array}{r} {\\text{in-degree}(v\_{2}) = 2\\text{~and~out-degree}(v\_{2}) = 1.} \\\\ \\end{array}$$  

Recall that vertex *v*[*i*] is said to be adjacent to vertex *v*[*j*] if there is an edge from *v*[*i*] to *v*[*j*]. So for example, in [Figure 1.6](#chapter1.xhtml#fig1_6), vertex *v*[1] is adjacent to vertex *v*[2]; however, vertex *v*[2] is not adjacent to vertex *v*[1].

The adjacency matrix associated with the graph in [Figure 1.6](#chapter1.xhtml#fig1_6) is

  
$$\\begin{array}{l} {A = \\left( \\begin{array}{llll} 0 & 1 & 0 & 0 \\\\ 0 & 0 & 0 & 1 \\\\ 0 & 1 & 0 & 0 \\\\ 1 & 0 & 0 & 0 \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

Notice that *A* is not a symmetric matrix due to the directed nature of the affiliated graph.

All of the examples thus far have been unweighted graphs; however, a graph's edges can have weights associated with them.

If *w*[*i**j*] is the **weight of the edge** between vertex *i* and vertex *j*, then the (*i*, *j*)^(th) entry in the adjacency matrix is *w*[*i**j*].

One venue in which graph theory has applications is in archeology and similar fields with artifacts that may share similar traits.

Imagine that there are four digs located near one another and that artifacts are found in each dig. The graph shown in [Figure 1.7](#chapter1.xhtml#fig1_7) shows the digs as vertices and the number of attributes that they share as weights on the edges; this is an example of a weighted graph.

![Figure 1.7 Example of a weighted graph.](images/fig1_7.jpg)

[Figure 1.7](#chapter1.xhtml#b1fig1_7) Example of a weighted graph.

Social networks have also been a hub of activity when it comes to graph theory.

It is the job of data scientists to look at data and make hypotheses about the future. Another area in which this is particularly applicable is *sports ranking*.

For example, in the first half of the SEC-East 2019 football season, Florida was winning the conference with a 4-1 record. **What if you wished to look at the teams' conference record part-way through the season to predict future rankings?**

Representing the existence of a head-to-head competition in terms of an adjacency matrix may not be the most useful in this case, as the entries of this matrix would be all ones. However, a matrix that could incorporate a win-lose structure as well as the score differential may be beneficial in studying the outcomes of this season.

For example, on September 9, 2019, Florida defeated Kentucky 29 to 21. One might choose to assign a weight of 8, the score differential, to the edge connecting Florida and Kentucky; however, you may want to also be able to indicate the direction of the win.

One way to do this is by using a **directed graph**, where an edge from *v*[*i*] to *v*[*j*] may exist without the existence of an edge from *v*[*j*] to *v*[*i*]. In this application, a directed edge from vertex *v*[*i*] to vertex *v*[*j*] would denote a victory for team *i*.

![Figure 1.9 Directed Graph for SEC-East Football Example.](images/fig1_9.jpg)

Figure 1.9 Directed Graph for SEC-East Football Example.

In the case of a directed graph, the adjacency matrix may not be symmetric. For example, since Florida defeated Kentucky, Florida is adjacent to Kentucky but Kentucky is not adjacent to Florida.

  
$$\\begin{array}{l} {A\_{SEC} = \\left( \\begin{array}{llllllll} & {FL} & {TN} & {KY} & {GA} & {MIZ} & {SC} & {VAN} \\\\ {FL} & 0 & 1 & 1 & 0 & 0 & 1 & 0 \\\\ {TN} & 0 & 0 & 0 & 0 & 0 & 1 & 0 \\\\ {KY} & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\\\ {GA} & 0 & 1 & 1 & 0 & 0 & 0 & 1 \\\\ {MIZ} & 0 & 0 & 0 & 0 & 0 & 1 & 0 \\\\ {SC} & 0 & 0 & 1 & 1 & 0 & 0 & 0 \\\\ {VAN} & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\\\ \\end{array} \\right)} \\\\ \\end{array}$$  

Directed graphs can also be used to visualize a **decision tree** or **neural network** based on raw input data and decision questions that lead to an output. More extensive theory and applications of these techniques can be found in [Chapters 6](#chapter6.xhtml) and [7](#chapter7.xhtml).

## 1.2 The Power of the Adjacency Matrix

In [Section 1.1](#chapter1.xhtml#sec1_1), the relationship between a graph and its corresponding adjacency matrix was discussed. In this section, we will explore some ways to use the adjacency matrix to make further conclusions about data.

Powers of the adjacency matrix can give insight into indirect relationships. The (*i*, *j*)^(th) entry of *A*^(*k*), where *k* is a positive integer, represents the number of paths of length exactly *k* between vertices *i* and *j*. Thus the (*i*, *j*)^(th) entry of

  
$$\\begin{array}{r} {\\sum\\limits\_{k = 0}^{n}A^{k}} \\\\ \\end{array}$$  

represents the number of paths of length *n* or less between vertices *i* and *j*.

Using similar techniques to explore the SEC-East example from [Section 1.1](#chapter1.xhtml#sec1_1), let's say that you wish to rank the SEC-East teams based on their record half way through the 2019 season. How would you determine the #1 football team in the SEC-East prior to the end of the regular season?

We will look further at techniques for sports ranking in [Section 1.6](#chapter1.xhtml#sec1_6) that not only incorporate win-lose but also the score differential of games.

## 1.3 Eigenvalues and Eigenvectors as Key Players

If *A* is a *n* × *n* square matrix and

  
$$\\begin{array}{r} {Ax = \\lambda x,} \\\\ \\end{array}$$  

*λ* is called an **eigenvalue** of *A* with corresponding **eigenvector** *x*, where *x* is an *n* × 1 vector.

Given a square matrix *A*, one way to find the eigenvalues for *A* is to find the **characteristic equation**

  
$$\\begin{array}{r} {|A - \\lambda I| = 0} \\\\ \\end{array}$$  

and to solve for all values of *λ*.

The **spectral radius** of a matrix *A*,

  
$$\\begin{array}{r} {\\rho(A) = max\_{1 \\leq i \\leq n}|\\lambda\_{i}|,} \\\\ \\end{array}$$  

where *λ*[*i*], 1 ≤ *i* ≤ *n*, are the eigenvalues of *A*.

In general, a *n* × *n* matrix *A* acts as a transformation, or function, on the vectors *v* ∈ ℝ^(*n*).

One of the most significant properties related to eigenvalues is that a matrix is singular if and only if at least of the eigenvalues of the matrix is equal to 0.

It can also be easily shown that if *λ* is an eigenvalue of *A* with a corresponding eigenvector *x*, then *λ*^(*k*) is an eigenvalue of *A*^(*k*) with a corresponding *x*.

Since there are many different eigenvectors that can serve as the basis vector associated with a given eigenvalue, it is helpful to establish a convention for which eigenvector we will focus on the discussion in this text. Unless otherwise noted, **unit eigenvectors** will be presented conventionally throughout the rest of the text.

Recall that a **unit vector**, *u*, has a norm ||*u*|| = 1, where

  
$$\\left\\| u \\right\\|\\begin{array}{l} {= \\sqrt{\\left\\langle {u,u} \\right\\rangle}} \\\\ \\end{array}$$  

and given a vector *v*,

  
$$\\begin{array}{l} \\frac{v}{\\left\\| v \\right\\|} \\\\ \\end{array}$$  

is a unit vector.

The unit eigenvector of *A* corresponding to *λ* = 5 is $\\left\\{ \\frac{1}{\\sqrt{5}},\\,\\frac{2}{\\sqrt{5}} \\right\\}$.

We will apply the concepts of eigenvalues and eigenvectors to another matrix that is important in data science, the **Laplacian matrix**. The Laplacian matrix, *L*, affiliated with an *n* × *n* adjacency matrix, *A*, is defined such that

  
$$\\begin{array}{l} {L\_{ij} = \\left\\{ \\begin{array}{ll} d\_{i} & {\\text{if~}i = j,} \\\\ {- A\_{ij}} & {\\text{if~}i \\neq j,} \\\\ \\end{array}~ \\right.} \\\\ \\end{array}$$  

where *d*[*i*] is the degree of vertex *i*.

The **normalized Laplacian matrix**, ℒ, is defined as ℒ = *T**L**T* such that *T* is a diagonal matrix with $T\_{ii} = \\frac{1}{\\sqrt{d\_{i}}}$.

The Laplacian matrix for simple weighted graphs is very similar to unweighted graphs. In a weighted graph, the entries of the adjacency matrix

  
$$\\begin{array}{l} {A\_{ij} = \\left\\{ \\begin{array}{ll} w\_{ij} & {\\text{when~vertex~}i\\text{~and~}j\\text{~are~adjacent}} \\\\ 0 & \\text{otherwise} \\\\ \\end{array}~ \\right.} \\\\ \\end{array}$$  

where *w*[*i**j*] is the weight of the edge that is incident to vertices *i* and *j*. The degree of vertex *i*, *d*[*i*] = ∑*w*[*i**j*].

Unlike the Laplacian matrices described thus far, the Laplacian matrix for a simple directed graph would not be a symmetric matrix. With this in mind, *d*[*i*] is equal to the outdegree of the vertex.

The Laplacian matrix has significant applications in **spectral graph theory**.

Spectral graph theory is related to clustering and ranking of vertices based on the study of eigenvalues and eigenvectors of the Laplacian matrix. We will focus our attention here on simple connected undirected graphs and their symmetric adjacency matrix counterparts.

The Laplacian matrix, *L*, associated with graph *G* will have *n* eigenvalues, *λ*[1] ≤ *λ*[2] ≤ … ≤ *λ*[*n*]. The eigenvectors associated with *λ*[*i*] = 0 are the indicators of the graph's connected components.

The second smallest eigenvalue, *λ*[2], is called the **algebraic connectivity of the graph** or the **Fiedler value** \[[12](#refbib.xhtml#refbib12)\], denoted *a*(*G*), and the corresponding eigenvector is called the **characteristic valuation** or **Fiedler vector**.

The Fiedler value represents the algebraic connectivity of the graph associated with the adjacency matrix. Note that *a*(*G*) > 0 if and only if *G* is connected, and the further the Fiedler value is from 0 the more connected the graph is.

Notice, in [Figure 1.14](#chapter1.xhtml#fig1_14), that the top graph is disconnected with two components and thus the Laplacian has an eigenvalue of zero multiplicity 2. A graph that is connected will have a Laplacian with an eigenvalue equal to zero of multiplicity 1, as seen in all but the top graph in [Figure 1.14](#chapter1.xhtml#fig1_14). As the graphs in [Figure 1.14](#chapter1.xhtml#fig1_14) get more connected, the Fiedler value increases.

![Figure 1.14 Examples of Graphs, their Laplacian, and Eigenvalues.](images/fig1_14.jpg)

[Figure 1.14](#chapter1.xhtml#b1fig1_14) Examples of Graphs, their Laplacian, and Eigenvalues.

It is also interesting to notice that a **complete graph** of *n* vertices, *K*[*n*], will have Laplacian with an eigenvalue equal to *n* multiplicity *n* − 1 and an eigenvalue equal to 0 multiplicity 1. The Fiedler value and vector of the normalized Laplacian matrix can be interpreted in a similar manner to that of the Laplacian matrix.

If one wishes to partition an undirected graph into two subgraphs, the Fiedler theorem defines a way to do so while minimizing the number of edges cut when doing so.

The *i*^(th) value in the Fiedler vector is called the **valuation** of vertex *i* in graph *G*.

In application, the Fiedler vector is particularly helpful in clustering data that is related to a weighted simple graph. Note that the adjacency matrix must be symmetric in order to apply this partitioning.

There are spectral clustering techniques that can be applied to non-symmetric Laplacian matrices such as that corresponding to the directed graph in [Example 1.9](#chapter1.xhtml#exam1_9). These techniques will be explored further in [Chapter 2](#chapter2.xhtml).

One technique is to use a symmetric matrix, such as the **Gramian matrix** *S* = *A**A*^(*T*) or *A* + *A*^(*T*), instead of the original adjacency matrix and the Laplacian matrix affiliated with that symmetric matrix.

We can use similar techniques when trying to cluster weighted and directed graphs.

So why does the Fiedler vector work in clustering data into two subgroups? We take a moment here to explore the theory behind this concept.

A **quadratic form** of a symmetric matrix *A* is a function on ℝ^(*n*) where *Q*[*A*](*x*) = *x*^(*T*)*A**x*, or

  
$$\\begin{array}{r} {Q\_{A}(x\_{1},x\_{2},x\_{3},\\ldots,x\_{n}) = {\\sum\\limits\_{i \\leq j}a\_{ij}}x\_{i}x\_{j}.} \\\\ \\end{array}$$  

A real symmetric *n* × *n* matrix, *A* is called

1.  **Positive definite** if *x*^(*T*)*A**x* > 0 for all *x* ∈ ℝ^(*n*),
    
2.  **Positive semidefinite** if *x*^(*T*)*A**x* ≥ 0 for all *x* ∈ ℝ^(*n*),
    
3.  **Negative definite** if *x*^(*T*)*A**x* < 0 for all *x* ∈ ℝ^(*n*),
    
4.  **Negative semidefinite** if *x*^(*T*)*A**x* ≤ 0 for all *x* ∈ ℝ^(*n*).
    

The Laplacian matrix, *L*, associated with a non-negative (real) symmetric matrix is a real positive semidefinite matrix and thus has all non-negative eigenvalues. In addition, *L*.*e* = 0, where $e = \\overset{\\rightarrow}{1}$ and since *G* is connected, *e* is the only solution to *x*^(*T*)*L**x* = 0.

Under the fixed point characterization of eigenvalues, *A**x* = *λ**x*, if |*λ*| < 1,

  
$$\\begin{array}{r} {lim\_{k\\rightarrow\\infty}A^{k}x = lim\_{k\\rightarrow\\infty}\\lambda^{k}x = \\overset{\\rightarrow}{0}.} \\\\ \\end{array}$$  

In application, *λ* = 1 is of particular interest as *A**x* = *x* the values of the corresponding eigenvector, *x*, remain fixed when multiplied by the matrix *A*. Similarly, if |*λ*| = 1, there exists a positive integer *k* such that

  
$$\\begin{array}{r} {A^{k}x = x} \\\\ \\end{array}$$  

and thus the values of *x* remain fixed when multiplied by the matrix *A*^(*k*). We call the eigenvector, *x*, the **steady state vector**.

Spectral clustering is dependent on the **Spectral Theorem** and another characterization of eigenvalues, the optimization characterization.

The optimization characterization of eigenvalues looks at the **Rayleigh Quotient**

  
$$\\begin{array}{r} {R(x) = \\frac{x^{T}Ax}{x^{T}x}.} \\\\ \\end{array}$$  

From [Theorem 4](#chapter1.xhtml#theo1_4), we can conclude that *λ*[1] minimizes *R*(*x*) and *λ*[*n*] maximizes *R*(*x*).

For the *n* × *n* Laplacian matrix, *L*, of a connected graph, *G*, with eigenvalues 0 = *λ*[1] < *λ*[2] ≤ … ≤ *λ*[*n*],

  
$$\\begin{array}{r} {\\lambda\_{2} = a(G) = min\_{x \\neq 0,||x|| = 1,x\\bot e}\\frac{x^{T}Lx}{x^{T}x}.} \\\\ \\end{array}$$  

Now if the main goal is to partition the vertices in a graph, *G*, into two subsets, *G*[1] and *G*[2], one might wish to do this without cutting through a large number of edges of the graph. We will measure how well we do this by defining the subset of vertices *V*[1] and the boundary of *V*[1],

  
$$\\begin{array}{r} {\\partial(V\_{1}) = \\left\\{ (v\_{1},\\, v\_{2}),\\, v\_{1} \\in V\_{1},\\, v\_{2} \\in V\\backslash V\_{2} \\right\\}.} \\\\ \\end{array}$$  

The **isoperimetric ratio** \[2,3\] of *V*[1], *θ*(*V*[1]), is defined as

  
$$\\begin{array}{r} {\\theta(V\_{1}) = \\frac{|\\partial(V\_{1})|}{|V\_{1}|}.} \\\\ \\end{array}$$  

The **isoperimetric number** of a graph, *θ*[*G*], is the minimum isoperimetric ratio over all sets of at most half of the vertices. That is

  
$$\\begin{array}{r} {\\theta\_{G} = \\min\_{|V\_{1}| \\leq \\frac{|V|}{2}}\\frac{|\\partial(V\_{1})|}{|V\_{1}||V\_{2}|}.} \\\\ \\end{array}$$  

## 1.4 CASE STUDY: Applications in Sport Ranking

There are several ways to incorporate the score differential of games into a sports ranking. We explore a few of these here.

In [Section 1.2](#chapter1.xhtml#sec1_2), we only incorporated a win-lose structure in the analysis of the SEC-East Conference ranking. Here we wish to rank the teams by incorporating sequences of both wins and losses. These paths could arbitrarily include a game where a team plays themselves, represented by a loop in a graph or one in a main diagonal entry of the adjacency matrix. For further analysis, we will use the adjacency matrix

  
$$\\begin{array}{r} {A\_{SEC\*} = A\_{SEC} + A\_{SEC}^{T} + I.} \\\\ \\end{array}$$  

We begin this exploration of sports ranking by introducing the vector $\\overset{\\rightarrow}{S}$, representing the net score for each team, where

  
$$\\begin{array}{r} {{\\overset{\\rightarrow}{S}}\_{i} = {\\sum\\limits\_{j = 1}^{n}\\frac{s\_{ij}}{n\_{i}}},} \\\\ \\end{array}$$  

*n*[*i*] represents the number of games played by team *i* and *s*[*i**j*] represents the point differential in the game between team *i* and team *j*, noting that if team *i* loses to team *j*, then *s*[*i**j*] is negative \[[19](#refbib.xhtml#refbib19)\]. From [Figure 1.18](#chapter1.xhtml#fig1_18),

![Figure 1.18 Weighted Directed Graph for SEC-East Football Example.](images/fig1_18.jpg)

[Figure 1.18](#chapter1.xhtml#b1fig1_18) Weighted Directed Graph for SEC-East Football Example.

  
$$\\begin{array}{l} {\\overset{\\rightarrow}{S} = \\left( \\begin{array}{l} \\frac{50}{3} \\\\ \\\\ \\frac{- 40}{3} \\\\ \\\\ {- 6} \\\\ \\\\ \\frac{70}{4} \\\\ \\\\ {- 3} \\\\ \\\\ {- 6} \\\\ \\\\ \\frac{- 17}{2} \\\\ \\end{array} \\right)\\begin{array}{l} {FL} \\\\ \\\\ {TN} \\\\ \\\\ {KY} \\\\ \\\\ {GA} \\\\ \\\\ {MIZ} \\\\ \\\\ {SC} \\\\ \\\\ {VAN} \\\\ \\end{array}.} \\\\ \\end{array}$$  

With the matrices *A*[*S**E**C*\*] and $\\overset{\\rightarrow}{S}$, we can represent generational rankings. First generational rankings from head-to-head matches can be expressed by

  
$$\\begin{array}{r} {A\_{SEC\*}^{0}\\overset{\\rightarrow}{S},} \\\\ \\end{array}$$  

ranking Georgia as #1, Florida as #2, and Missouri as #3.

However, we may wish to include 2^(nd) generation games. These are indirect relationships in a series of competitions, or tournaments, connected by one edge.

For example, in [Figure 1.18](#chapter1.xhtml#fig1_18), although Georgia did not play Missouri, we can say that there is a 2^(nd) generation game between these two teams since Georgia played Vanderbilt and Vanderbilt played Missouri. A ranking that includes 1^(st), 2^(nd), and 3^(rd) generation games can be found with

  
$$\\begin{aligned} & {\\overset{\\rightarrow}{S} + (A\_{SEC\*})\\overset{\\rightarrow}{S} + {(A\_{SEC\*})}^{2}\\overset{\\rightarrow}{S}} \\\\ & {\\text{\\quad\\quad} = \\left\\{ {39.2,\\, - 2.8,\\, - 10.3,\\, 30.7,\\, - 19,\\, - 8.8,\\, - 36.3} \\right\\}} \\\\ \\end{aligned}$$  

ranking Florida above Georgia, with Tennessee coming in third. Generalizing this idea, a ranking that includes the first *k* generation games can be found with

  
$$\\begin{array}{r} {{\\sum\\limits\_{n = 0}^{k}A\_{SEC\*}^{n}}\\overset{\\rightarrow}{S}.} \\\\ \\end{array}$$  

Another way to rank the teams is to incorporate the points scored for each team, defining

  
$$\\begin{array}{r} {A\_{ij} = \\frac{W\_{ij}}{(W\_{ij} + W\_{ji})}} \\\\ \\end{array}$$  

where *W*[*i**j*] is the score of team *i* in the game between teams *i* and *j*. The scores of the games are shown in [Figure 1.18](#chapter1.xhtml#fig1_18).

Table 1.2 2019 SEC-East Football Scores.

  
| FL(29)-KY(21) || FL(34)-TN(3) || FL(38)-SC(27) |
| --- | --- | --- |
| TN(14)-GA(43) || TN(41)-SC(21) || KY(7)-SC(24) |
| KY(0)-GA(21) || KY(29)-MIZ(7) || GA(30)-VAN(6) |
| GA(17)-SC(21) || MIZ(34)-SC(14) || MIZ(14)-VAN(21) |

The absolute value of the unit eigenvector

  
$$\\begin{array}{r} \\left\\{ 0.434,\\, 0.293,\\, 0.307,\\, 0.514,\\, 0.282,\\, 0.515,\\, 0.149 \\right\\} \\\\ \\end{array}$$  

corresponding to the largest eigenvalue with a norm equal to 1, in absolute value, associated with this scoring technique provides a ranking of South Carolina, Georgia, and then Florida. This ranking technique incorporates the team's relative score; however, it does not incorporate the notion of a closely fought game, a game won in overtime, or when a win occurs in the season.

In order to avoid having a team run up the score in a single game in order to greatly improve their team rankings, some mathematicians use a slightly different weighting system where

  
$$\\begin{array}{r} {A\_{ij} = h\\frac{W\_{ij} + 1}{(W\_{ij} + W\_{ji} + 2)}} \\\\ \\end{array}$$  

and *h* ∈ (0, 1\].

Wesley Colley developed a weighted system that is believed to deal with some of the issues seen in the previous technique. In the Colley Method \[[6](#refbib.xhtml#refbib6)\] of sports ranking, the entries of *C*, the **Colley matrix**, are defined as

  
$$\\begin{array}{l} {C\_{ij} = \\left\\{ \\begin{array}{ll} {2 + N\_{i}} & {\\text{w}heni = j} \\\\ {- n\_{ji}} & {\\text{w}heni \\neq j} \\\\ \\end{array}~ \\right.,} \\\\ \\end{array}$$  

where *N*[*i*] is the number of games played by team *i* and *n*[*j**i*] is the number of times team *i* has played team *j*. The goal of this ranking system is to solve for $\\overset{\\rightarrow}{r}$ in the linear system

  
$$\\begin{array}{r} {C\\overset{\\rightarrow}{r} = b\\text{~where~}b\_{i} = 1 + \\frac{1}{2}(w\_{i} - l\_{i}),} \\\\ \\end{array}$$  

*w*[*i*] is the number of wins for team *i* and *l*[*i*] is the number of losses for team *i*.

For the SEC-East Conference, the Colley Method, defined with the linear system *C**r* = *b*, with

  
$$\\begin{array}{l} {C = \\left( \\begin{array}{lllllll} 5 & {- 1} & {- 1} & 0 & 0 & {- 1} & 0 \\\\ {- 1} & 5 & 0 & {- 1} & 0 & {- 1} & 0 \\\\ {- 1} & 0 & 6 & {- 1} & {- 1} & {- 1} & 0 \\\\ 0 & {- 1} & {- 1} & 6 & 0 & {- 1} & {- 1} \\\\ 0 & 0 & {- 1} & 0 & 5 & {- 1} & {- 1} \\\\ {- 1} & {- 1} & {- 1} & {- 1} & {- 1} & 7 & 0 \\\\ 0 & 0 & 0 & {- 1} & {- 1} & 0 & 4 \\\\ \\end{array} \\right)} \\\\ \\end{array}$$  

and $b = \\left\\{ {\\frac{5}{2},\\frac{1}{2},0,2,\\frac{1}{2},\\frac{1}{2},1} \\right\\}$ produces a ranking vector,

  
$$\\begin{array}{r} {r = \\left\\{ 0.753,\\, 0.627,\\, 0.497,\\, 0.464,\\, 0.438,\\, 0.363,\\, 0.359 \\right\\}.} \\\\ \\end{array}$$  

Under this Colley method, Florida would be ranked #1 with Georgia and Vanderbilt 2^(nd) and 3^(rd) respectively.

This case study presents several different ways to use matrices to produce a ranking among sports teams. There is no single way to do a sport ranking, and are many other famous ranking systems such as Massey method and Ford's method \[[6](#refbib.xhtml#refbib6)\].

Some data used in this study can be found at 3. A larger data set of games from the NCAA Men's Division 1 2020 season can be found at GitHub links 4 and 5. Python and R code for this case study can be found at GitHub links 2 and 7 respectively.

## 1.5 CASE STUDY: Gerrymandering

Throughout American history, states have struggled with how to create voting districts in a non-partisan manner. As recent as 2019, states, such as North Carolina, have had congressional districts ruled unconstitutional due to partisan gerrymander \[[39](#refbib.xhtml#refbib39)\]. The 4^(th) Circuit Court of Appeals has made a clear statement that focuses on three steps to determine if a district has been gerrymandered, violating the Constitution.

A district should be in question if there is “(1) discriminatory intent, (2) discriminatory effects, and (3) a lack of justification for the discriminatory effects” \[[2](#refbib.xhtml#refbib2)\].

In order to think mathematically about how to develop fair districts, we must also know some rules around districting. First of all, districts are typically created using defined census areas, census blocks, census block groups, or census tracts. The former is the smallest and the later is the largest of the defined areas. Districts must also maintain three characteristics: equity, contiguity, and compactness \[[15](#refbib.xhtml#refbib15)\].

Equity is the principle that all districts have an equivalent number of voters. In an ideal situation, districts are compact if given any two points in the district the line segment between these points remains completely in the district. Keep in mind that census blocks, groups, and tracts are typically not compact and thus the inclusion of these objects, in total, may cause a district to fail this property. Failure to meet the property of compactness can become more of an issue when it occurs in an unnatural manner. Failure to meet compactness in the 2011 North Carolina Congressional redistricting map was voted unconstitutional, particularly around District 12, which can be seen in [Figure 1.19](#chapter1.xhtml#fig1_19).

![Figure 1.19 2011 North Carolina Congressional Redistricting Map \[26\].](images/fig1_19.jpg)

[Figure 1.19](#chapter1.xhtml#b1fig1_19) 2011 North Carolina Congressional Redistricting Map \[[26](#refbib.xhtml#refbib26)\].

Some of the issues with districting come down to determining adjacent census blocks. As you can see in [Figure 1.20](#chapter1.xhtml#fig1_20), adjacent census blocks may not have consecutive numbers. For example, census blocks 2003 and 2009 are adjacent.

![Figure 1.20 Sample of census blocks and block number in Charlotte, NC.](images/fig1_20.jpg)

[Figure 1.20](#chapter1.xhtml#b1fig1_20) Sample of census blocks and block number in Charlotte, NC.

Blocks are also clearly not adjacent by an entire edge or may be adjacent along multiple edges. The question then becomes, given that there are thousands of census blocks in a state, how do we determine if census blocks are adjacent, and how do we prioritize adjacencies that may be more important than others.

In this case study, we will focus on a very small section of [Figure 1.20](#chapter1.xhtml#fig1_20), census blocks 2000 through 2015. One way to think about this problem is to create a graph, and corresponding adjacency matrix, based on perimeter shared.

The edges in [Figure 1.21](#chapter1.xhtml#fig1_21) represent a shared edge between census blocks in [Figure 1.20](#chapter1.xhtml#fig1_20). The weight from vertex *i* to vertex *j*, representing the fraction of the boundary of census block *i* shared with census block *j*, is the (*i*, *j*)^(th) entry of adjacency matrix, *A*[*E*].

![Figure 1.21 Unweighted graph representation of sample census blocks.](images/fig1_21.jpg)

[Figure 1.21](#chapter1.xhtml#b1fig1_21) Unweighted graph representation of sample census blocks.

If entries of a given row sum to 1, this indicates that a census block is surrounded by other census blocks in the study (from 2000 to 2015). If entries of a given row do not sum to 1 then some part of the corresponding census block's boundary is not shared by any other census block in the study.

  
$$A\_{E} = \\begin{pmatrix} 0 & 0.06 & 0.08 & 0.05 & 0.1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 0.27 & 0 & 0.34 & 0 & 0.2 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0.19 & 0 & 0 & 0 \\\\ 0.24 & 0.24 & 0 & 0.44 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0.08 & 0 & 0 \\\\ 0.11 & 0 & 0.35 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0.2 & 0 & 0 \\\\ 0.28 & 0.13 & 0 & 0 & 0 & 0.14 & 0.15 & 0 & 0 & 0 & 0 & 0.14 & 0.16 & 0 & 0 & 0 \\\\ 0 & 0 & 0 & 0 & 0.19 & 0 & 0.31 & 0 & 0 & 0.19 & 0.31 & 0 & 0 & 0 & 0 & 0 \\\\ 0 & 0 & 0 & 0 & 0.2 & 0.3 & 0 & 0.2 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 0 & 0 & 0 & 0 & 0 & 0 & 0.21 & 0 & 0.21 & 0.58 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0.16 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 0 & 0 & 0 & 0 & 0 & 0.21 & 0 & 0.62 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 0 & 0 & 0 & 0 & 0 & 0.24 & 0 & 0 & 0 & 0 & 0 & 0.24 & 0 & 0 & 0.24 & 0 \\\\ 0 & 0 & 0 & 0 & 0.16 & 0 & 0 & 0 & 0 & 0 & 0.26 & 0 & 0.13 & 0.19 & 0 & 0.26 \\\\ 0 & 0.23 & 0 & 0 & 0.30 & 0 & 0 & 0 & 0 & 0 & 0 & 0.22 & 0 & 0.25 & 0 & 0 \\\\ 0 & 0 & 0.05 & 0.16 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0.12 & 0.09 & 0 & 0 & 0.17 \\\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0.25 & 0 & 0 & 0 & 0 & 0.2 \\\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0.26 & 0 & 0.27 & 0.21 & 0 \\\\ \\end{pmatrix}.$$  

In Chapter 1.6, a netscore vector was created in order to rank teams in the SEC-East Conference. A similar vector can be created for studying the census blocks. Let

  
$$\\begin{aligned} \\overset{\\rightarrow}{S\_{i}} & {= {\\sum\\limits\_{j = 1}^{16}A\_{E}}(i,j) = \\left\\{ 0.29,\\, 1,\\, 1,\\, 0.66,\\, 1,\\, 1,\\, 0.7,\\, 1,\\, 0.16,\\, 0.83,\\, 0.72,\\, 1,\\, 1, \\right.} \\\\ & {\\left. \\text{\\quad\\quad}0.59,\\, 0.45,\\, 0.74 \\right\\}.} \\\\ \\end{aligned}$$  

$\\overset{\\rightarrow}{S\_{i}}$ represents the percent of the boundary of census block *i* shared by other census blocks in the study. Notice that *A*[*E*] is not symmetric; however,

  
$$\\begin{aligned} A\_{E\*} & {= A\_{E} + A\_{E}^{T} + I\\,\\text{~is~symmetric}\\text{.}} \\\\ {\\overset{\\rightarrow}{S} + \\overset{\\rightarrow}{S}A\_{E\*}} & {= \\left\\{ 1.7,3.4,3.27,2.37,3.9,3.5,2.8,3.34,0.7,3.26,2.7,3.6, \\right.} \\\\ & \\left. \\text{\\quad\\quad}3.4,2.5,1.6,2.44 \\right\\} \\\\ \\end{aligned}$$  

represents a ranking of census blocks where the highest rank blocks have the most boundary shared in the study, census blocks 2004, 2011, 2005, 2012, and 2001.

Unfortunately, the above technique does not provide a clear way to incorporate adjacency into a way to partition the census blocks. We will look to find the Fiedler vector in order to aid us in accomplishing this goal.

If we create a binary adjacency matrix, A, based on whether a census block shares edges with other census blocks in [Figure 1.20](#chapter1.xhtml#fig1_20), the matrix

  
$$\\begin{array}{ll} A & {= \\left( \\begin{array}{llllllllllllllll} 0 & 1 & 1 & 1 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 1 & 0 & 1 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\\ 1 & 1 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\\\ 1 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\\\ 1 & 1 & 0 & 0 & 0 & 1 & 1 & 0 & 0 & 0 & 0 & 1 & 1 & 0 & 0 & 0 \\\\ 0 & 0 & 0 & 0 & 1 & 0 & 1 & 0 & 0 & 1 & 1 & 0 & 0 & 0 & 0 & 0 \\\\ 0 & 0 & 0 & 0 & 1 & 1 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 1 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 1 & 0 \\\\ 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 1 & 1 & 0 & 1 \\\\ 0 & 1 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 1 & 0 & 0 \\\\ 0 & 0 & 1 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 1 & 0 & 0 & 1 \\\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 1 \\\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 1 & 1 & 0 \\\\ \\end{array} \\right)} \\\\ \\end{array}$$  

and

  
$$\\begin{array}{ll} {I + A + A^{2}} & {= \\left( \\begin{array}{llllllllllllllll} 5 & 3 & 3 & 2 & 2 & 1 & 1 & 0 & 0 & 0 & 0 & 1 & 2 & 2 & 0 & 0 \\\\ 3 & 5 & 2 & 2 & 3 & 1 & 1 & 0 & 0 & 0 & 0 & 2 & 2 & 2 & 0 & 0 \\\\ 3 & 2 & 5 & 3 & 2 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 2 & 2 & 0 & 1 \\\\ 2 & 2 & 3 & 4 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 1 & 2 & 0 & 1 \\\\ 2 & 3 & 2 & 1 & 7 & 2 & 2 & 1 & 0 & 1 & 2 & 2 & 3 & 2 & 0 & 1 \\\\ 1 & 1 & 0 & 0 & 2 & 5 & 2 & 2 & 0 & 1 & 1 & 2 & 1 & 0 & 1 & 0 \\\\ 1 & 1 & 0 & 0 & 2 & 2 & 4 & 1 & 1 & 2 & 1 & 1 & 1 & 0 & 0 & 0 \\\\ 0 & 0 & 0 & 0 & 1 & 2 & 1 & 4 & 1 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 0 & 0 & 0 & 0 & 0 & 0 & 1 & 1 & 2 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 0 & 0 & 0 & 0 & 1 & 1 & 2 & 1 & 1 & 3 & 1 & 0 & 0 & 0 & 0 & 0 \\\\ 0 & 0 & 0 & 0 & 2 & 1 & 1 & 0 & 0 & 1 & 4 & 1 & 1 & 1 & 1 & 2 \\\\ 1 & 2 & 1 & 1 & 2 & 2 & 1 & 0 & 0 & 0 & 1 & 6 & 3 & 3 & 2 & 2 \\\\ 2 & 2 & 2 & 1 & 3 & 1 & 1 & 0 & 0 & 0 & 1 & 3 & 5 & 2 & 0 & 2 \\\\ 2 & 2 & 2 & 2 & 2 & 0 & 0 & 0 & 0 & 0 & 1 & 3 & 2 & 6 & 1 & 2 \\\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 1 & 2 & 0 & 1 & 3 & 1 \\\\ 0 & 0 & 1 & 1 & 1 & 0 & 0 & 0 & 0 & 0 & 2 & 2 & 2 & 2 & 1 & 4 \\\\ \\end{array} \\right)} \\\\ \\end{array}$$  

show that census blocks 2004 and 2011 have the most blocks adjacent to them in one or two steps, with the total of the rows of

  
$$\\begin{array}{r} {I + A + A^{2} = \\left\\{ 22,\\, 23,\\, 21,\\, 17,\\, 31,\\, 19,\\, 17,\\, 10,\\, 5,\\, 10,\\, 15,\\, 27,\\, 25,\\, 25,\\, 9,\\, 16 \\right\\}.} \\\\ \\end{array}$$  

One might wish to make sure that these two blocks are in separate districts. However, what if 2004 and 2011 were adjacent to one another?

The Laplacian of *A*,

  
$$\\begin{array}{l} {L = \\left( \\begin{array}{llllllllllllllll} 4 & {- 1} & {- 1} & {- 1} & {- 1} & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ {- 1} & 4 & {- 1} & 0 & {- 1} & 0 & 0 & 0 & 0 & 0 & 0 & 0 & {- 1} & 0 & 0 & 0 \\\\ {- 1} & {- 1} & 4 & {- 1} & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & {- 1} & 0 & 0 \\\\ {- 1} & 0 & {- 1} & 3 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & {- 1} & 0 & 0 \\\\ {- 1} & {- 1} & 0 & 0 & 6 & {- 1} & {- 1} & 0 & 0 & 0 & 0 & {- 1} & {- 1} & 0 & 0 & 0 \\\\ 0 & 0 & 0 & 0 & {- 1} & 4 & {- 1} & 0 & 0 & {- 1} & {- 1} & 0 & 0 & 0 & 0 & 0 \\\\ 0 & 0 & 0 & 0 & {- 1} & {- 1} & 3 & {- 1} & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 0 & 0 & 0 & 0 & 0 & 0 & {- 1} & 3 & {- 1} & {- 1} & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & {- 1} & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 0 & 0 & 0 & 0 & 0 & {- 1} & 0 & {- 1} & 0 & 2 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 0 & 0 & 0 & 0 & 0 & {- 1} & 0 & 0 & 0 & 0 & 3 & {- 1} & 0 & 0 & {- 1} & 0 \\\\ 0 & 0 & 0 & 0 & {- 1} & 0 & 0 & 0 & 0 & 0 & {- 1} & 5 & {- 1} & {- 1} & 0 & {- 1} \\\\ 0 & {- 1} & 0 & 0 & {- 1} & 0 & 0 & 0 & 0 & 0 & 0 & {- 1} & 4 & {- 1} & 0 & 0 \\\\ 0 & 0 & {- 1} & {- 1} & 0 & 0 & 0 & 0 & 0 & 0 & 0 & {- 1} & {- 1} & 5 & 0 & {- 1} \\\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & {- 1} & 0 & 0 & 0 & 2 & {- 1} \\\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & {- 1} & 0 & {- 1} & {- 1} & 3 \\\\ \\end{array} \\right)} \\\\ \\end{array}$$  

has unit Fiedler vector

  
$$\\begin{aligned} & \\left\\{ 0.17,0.16,0.2,0.2,0.06, - 0.1, - 0.17, - 0.43, - 0.64, - 0.31,0.07,0.14,0.15, \\right. \\\\ & {\\left. \\text{\\quad\\quad}0.18,0.15,0.18 \\right\\}.} \\\\ \\end{aligned}$$  

![Figure 1.22 Graphically representation of sample census blocks and partition.](images/fig1_22.jpg)

Figure 1.22 Graphically representation of sample census blocks and partition.

Based on the Fiedler vector, these census blocks can be partitioned into the two subgraphs, or districts,

  
$$\\begin{aligned} G\_{1} & {= \\left\\{ 2000,\\, 2001,\\, 2002,\\, 2003,\\, 2004,\\, 2010,\\, 2011,\\, 2012,\\, 2013,\\, 2014, \\right.} \\\\ & \\left. \\text{\\quad\\quad}2015,\\, 2016 \\right\\} \\\\ {\\text{and~}G\_{2}} & {= \\left\\{ 2005,\\, 2006,\\, 2007,\\, 2008,\\, 2009 \\right\\}.} \\\\ \\end{aligned}$$  

As described, Fiedler clustering would create two distinct clusters in a graph. However, this process can be repeated in order to create clusters within a subgraph \[[3](#refbib.xhtml#refbib3)\]. For example, perhaps it is essential to have three voting districts, let's create a Fiedler vector for *G*[1], so that we can divide *G*[1] into two clusters. The adjacency and Laplacian matrix corresponding to *G*[1] are

  
$$\\begin{array}{l} {A\_{1} = \\left( \\begin{array}{lllllllllll} 0 & 1 & 1 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 1 & 0 & 1 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\\\ 1 & 1 & 0 & 1 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\\\ 1 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 1 & 0 \\\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 1 & 1 & 0 & 1 \\\\ 0 & 1 & 0 & 0 & 0 & 0 & 1 & 0 & 1 & 0 & 0 \\\\ 0 & 0 & 1 & 1 & 0 & 0 & 1 & 1 & 0 & 0 & 1 \\\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 1 \\\\ 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 1 & 1 & 0 \\\\ \\end{array} \\right)\\text{~and~}} \\\\ \\end{array}$$  

  
$$\\begin{array}{l} {L\_{1} = \\left( \\begin{array}{lllllllllll} 4 & {- 1} & {- 1} & {- 1} & {- 1} & 0 & 0 & 0 & 0 & 0 & 0 \\\\ {- 1} & 4 & {- 1} & 0 & {- 1} & 0 & 0 & {- 1} & 0 & 0 & 0 \\\\ {- 1} & {- 1} & 4 & {- 1} & 0 & 0 & 0 & 0 & {- 1} & 0 & 0 \\\\ {- 1} & 0 & {- 1} & 3 & 0 & 0 & 0 & 0 & {- 1} & 0 & 0 \\\\ {- 1} & {- 1} & 0 & 0 & 4 & 0 & {- 1} & {- 1} & 0 & 0 & 0 \\\\ 0 & 0 & 0 & 0 & 0 & 2 & {- 1} & 0 & 0 & {- 1} & 0 \\\\ 0 & 0 & 0 & 0 & {- 1} & {- 1} & 5 & {- 1} & {- 1} & 0 & {- 1} \\\\ 0 & {- 1} & 0 & 0 & {- 1} & 0 & {- 1} & 4 & {- 1} & 0 & 0 \\\\ 0 & 0 & {- 1} & {- 1} & 0 & 0 & {- 1} & {- 1} & 5 & 0 & {- 1} \\\\ 0 & 0 & 0 & 0 & 0 & {- 1} & 0 & 0 & 0 & 2 & {- 1} \\\\ 0 & 0 & 0 & 0 & 0 & 0 & {- 1} & 0 & {- 1} & {- 1} & 3 \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

Eigenvalues of *L*[1] are {6.6, 6.4, 5.7, 5.2, 4.2, 4., 2.8, 2.3, 2.1, 0.7, 0}. The unit Fiedler vector, and thus the unit eigenvector corresponding to eigenvalue 0.7, is

  
$$\\begin{array}{r} {\\frac{1}{\\sqrt{1499}}\\left\\{ - 11,\\, - 10,\\, - 10,\\, - 10,\\, - 7,\\, 20,\\, 4,\\, - 5,\\, - 2,\\, 22,\\, 10 \\right\\}.} \\\\ \\end{array}$$  

Using this information, we can divide *G*[1] into two districts

  
$$\\begin{array}{r} {\\left\\{ 2000,\\, 2001,\\, 2002,\\, 2003,\\, 2004,\\, 2012,\\, 2013 \\right\\}\\text{~and~}\\left\\{ 2010,\\, 2011,\\, 2014,\\, 2015 \\right\\}.} \\\\ \\end{array}$$  

The three subgraph of *G* defined by with the Fiedler vector technique described in this case study can be seen in [Figure 1.23](#chapter1.xhtml#fig1_23).

![Figure 1.23 Subgraphs defined using Fiedler vectors.](images/fig1_23.jpg)

[Figure 1.23](#chapter1.xhtml#b1fig1_23) Subgraphs defined using Fiedler vectors.

Data related to the small weighted adjacency matrix for NC census blocks 2000-2015 and full information on the 2010 NC census blocks can be found at Github links 9 and 10. Python and R code for this case study can be found at GitHub links 6 and 8 respectively.

## 1.6 Exercises

*   Six students from Connected University are trying to figure out how they are connected to one another. They all have some connection to one another through the same online network platform. The adjacency matrix representing their connections to one another is
    
      
    $$\\begin{array}{l} {A = \\left( \\begin{array}{llllll} 0 & 1 & 0 & 1 & 0 & 0 \\\\ 1 & 0 & 1 & 1 & 0 & 1 \\\\ 0 & 1 & 0 & 0 & 1 & 0 \\\\ 1 & 1 & 0 & 0 & 1 & 0 \\\\ 0 & 0 & 1 & 1 & 0 & 1 \\\\ 0 & 1 & 0 & 0 & 1 & 0 \\\\ \\end{array} \\right)} \\\\ \\end{array}$$  
    
    1.  Kush is a student in the network whose network connections are represented in Row 1, or Column 1. Using the adjacency matrix, determine how many others are directly connected, through a 1-step path, to Kush in the network.
        
    2.  Using the adjacency matrix, determine how many others are directly connected, through a 2-step path, to Kush in the network.
        
    3.  Fiona is also a student in the network. Fiona's network connections are represented in Row 2, or Column 2 of the adjacency matrix. Using the adjacency matrix, determine how many 1-step or 2-step connections there between Kush and Fiona.
        
*   For the matrix
    
      
    $$\\begin{array}{l} {A = \\left( \\begin{array}{lll} 1 & 0 & 0 \\\\ 2 & 0 & 1 \\\\ 0 & 1 & 2 \\\\ \\end{array} \\right)} \\\\ \\end{array}$$  
    
    find the spectral radius, *ρ*(*A*).
    
*   A graph, *G*, is associated with the adjacency matrix
    
      
    $$\\begin{array}{l} {A = \\left( \\begin{array}{llll} 1 & 1 & 1 & 0 \\\\ 1 & 0 & 0 & 1 \\\\ 1 & 0 & 0 & 1 \\\\ 0 & 1 & 1 & 0 \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  
    
    Use the adjacency matrix to determine if *G* a simple connected graph.
    
*   For the following exercises, refer to graph *G* in [Figure 1.24](#chapter1.xhtml#fig1_24).
    
    1.  Find the adjacency matrix corresponding to *G*.
        
    2.  Find the Laplacian matrix associated with graph *G*.
        
    3.  Calculate the Fiedler value and Fiedler vector.
        
    4.  Use the Fiedler vector to cluster the graph into two subgraphs.
        
*   Using graph *G* displayed in [Figure 1.24](#chapter1.xhtml#fig1_24), calculate the isoperimetric number, *θ*[*G*], to argue how to cluster the *G* into two subgraphs.
    
    ![Figure 1.24 Figure for Exercises 4 and 5.](images/fig1_24.jpg)
    
    [Figure 1.24](#chapter1.xhtml#b1fig1_24) Figure for Exercises 4 and 5.
    
*   Wey and Blumstein \[[37](#refbib.xhtml#refbib37)\] studied the yellow-bellied marmot, a social ground dwelling rodent, and their network of social interactions in and around the Rocky Mountain Biological Laboratory in Colorado. Assume that the Marmot social network can be represented by the graph *G* found in [Figure 1.25](#chapter1.xhtml#fig1_25).
    
    1.  Find the adjacency matrix corresponding to *G*.
        
    2.  Let's assume that a marmot's social network can extend through friend marmots, leading us to explore powers of the adjacency matrix from part a. Determine if there is any marmot in the network that is connected to every other marmot through direct or two step relationships. Which marmots in the network are connected to every other marmot through direct, two-step, or three-step relationships?
        
    3.  Find the Laplacian matrix associated with *G*.
        
    4.  Determine the isoperimetric ratio *θ*(*V*) where
        
          
        $$\\begin{array}{r} {V = \\left\\{ v\_{1},\\, v\_{2},\\, v\_{3},\\, v\_{5},\\, v\_{6},\\, v\_{7} \\right\\}} \\\\ \\end{array}$$  
        
        affiliated with the clustering the graph *G* into the two subgraphs *G*[1] and *G*[2].
        
    5.  Find the Fiedler vector affiliated with *G*.
        
    6.  Use the Fiedler vector to cluster the marmot social network represented by *G* into two clusters.
        
    7.  Use your result in Part e. to cluster the marmot social network into four clusters. There are multiple answers to this question. Argue your solution based on Fiedler vectors of subgraphs of *G*.
        
*   If we knew more about the marmot social interactions regarding dominance and number of interactions, how might this affect how the relationships are represented in the graph presented in [Figure 1.25](#chapter1.xhtml#fig1_25).
    
    ![Figure 1.25 Marmot social network in Exercise 6.](images/fig1_25.jpg)
    
    [Figure 1.25](#chapter1.xhtml#b1fig1_25) Marmot social network in Exercise 6.
    
*   The weighted graph shown in [Figure 1.26](#chapter1.xhtml#fig1_26) displays the number of interactions between corresponding marmots in a week long period. Use this graph to answer the following questions.
    
    1.  Find the Laplacian matrix affiliated with the graph in [Figure 1.26](#chapter1.xhtml#fig1_26).
        
    2.  Find the Fiedler value and Fiedler vector related to the graph in [Figure 1.26](#chapter1.xhtml#fig1_26) and cluster the graph into two subgraphs using these values.
        
    
    ![Figure 1.26 Weighted marmot social network in Exercise 8.](images/fig1_26.jpg)
    
    [Figure 1.26](#chapter1.xhtml#b1fig1_26) Weighted marmot social network in Exercise 8.
    
*   A subpopulation of marmots is displaying a dominance behavior represented by the directed graph shown in [Figure 1.27](#chapter1.xhtml#fig1_27). The weight, *w*[*i**j*] on the edge from marmot *i* to marmot *j* represents the number of times that marmot *i* showed a dominance behavior over marmot *j*.
    
    1.  Use a score vector
        
          
        $$\\begin{array}{r} {\\overset{\\rightarrow}{S} = \\frac{s\_{ij}}{n\_{i}}} \\\\ \\end{array}$$  
        
        similar to that used in the sports ranking in [Section 1.6](#chapter1.xhtml#sec1_6), where *n*[*i*] represents the number of interactions with marmot *i* and *s*[*i**j*] represents the number of dominant interactions between marmots *i* and *j* noting that if marmot *j* is dominant over marmot *i* then *s*[*i**j*] is negative.
        
    2.  If *A* is the adjacency matrix representing the graph in [Figure 1.27](#chapter1.xhtml#fig1_27), use *A* + *I* and *S* to determine a ranking based on 1^(st) and 2^(nd) generation dominance.
        
        ![Figure 1.27 Weighted dominance interactions in Exercise 9.](images/fig1_27.jpg)
        
        [Figure 1.27](#chapter1.xhtml#b1fig1_27) Weighted dominance interactions in Exercise 9.
        
    3.  Use *A* + *I* and *S*, to determine a ranking based on 1^(st) through 3^(rd) generation dominance.
        
*   The Cinderella data from GitHub link 1 is a binary data set of traits in which 31 Cinderella tales from around the world contain. Use this data to answer the following questions.
    
    1.  Find the Gramian matrix, *S*.
        
    2.  What do the (1, 1) and (1, 2) entries represent in *S*?
        
    3.  Find the Fiedler vector related to the Gramian matrix, *S*, and use this information to cluster the Cinderella tales into two clusters.
        
*   Sports Ranking in [Section 1.6](#chapter1.xhtml#sec1_6) uses a weighted system where 2 or 3 − *s**t**e**p* wins between teams carry equal weight to direct head to head competition wins in order to create a ranking from
    
      
    $$\\begin{array}{r} {{\\sum\\limits\_{i = 0}^{n}A\_{SEC\*}^{i}}\\overset{\\rightarrow}{S}.} \\\\ \\end{array}$$  
    
    If instead, *N* − *s**t**e**p* wins carried a weight of $\\frac{1}{N}$ and thus the ranking would be
    
      
    $$\\begin{array}{r} {\\overset{\\rightarrow}{S} + {\\sum\\limits\_{i = 1}^{n}\\frac{1}{i}}A\_{SEC\*}^{i}\\overset{\\rightarrow}{S}.} \\\\ \\end{array}$$  
    
    determine the ranking of the teams in the tournament from Section with *n* = 4 and *n* = 5.
    

# 2Stochastic Processes

DOI: [10.1201/9781003025672-2](https://doi.org/10.1201/9781003025672-2)

The goal of this chapter is to use matrices to explore the behavior of systems as they change, or transition, throughout time. In order to do so, we begin by defining some properties of matrices that will allow us to employ some important theories, such as the *Perron-Frobenius Theorem*.

## Reducibility

A **permutation** is a change of ordering. So for example, if the numbers (1, 2, 3, 4) are rearranged, or permuted, to be read as (2, 1, 4, 3) we see that

  
$$\\begin{array}{r} \\left. 1\\rightarrow 2,\\, 2\\rightarrow 1,\\, 3\\rightarrow 4,\\,\\text{and~}4\\rightarrow 3. \\right. \\\\ \\end{array}$$  

We denote this permutation with the notation (12)(34). Similarly the permutation denoted by (1)(234) represents

  
$$\\begin{array}{r} \\left. 1\\rightarrow 1,\\, 2\\rightarrow 3,\\, 3\\rightarrow 4,\\,\\text{and~}4\\rightarrow 2 \\right. \\\\ \\end{array}$$  

and the ordering of the four numbers is (1, 3, 4, 2).

A **permutation matrix**, *P*, is a matrix in which the rows of the identity matrix of the same dimensions are permuted.

A *n* × *n* matrix *A* is called **reducible** if there exists a permutation matrix *P* such that

![](images/math2_17.jpg)

where *A*[11] is a *r* × *r* matrix and *A*[12] and *A*[22] are (*n* − *r*) × (*n* − *r*) matrices. If a matrix is not reducible then it is called **irreducible**.

Notice that a matrix *A* is reducible if and only if a permutation matrix can be found to put *A* into a block upper triangular form.

Notice that the graphs affiliated with the adjacency matrices *A*[1] and *A*[2] in [Example 2.2](#chapter2.xhtml#exam2_2), shown in [Figure 2.1](#chapter2.xhtml#fig2_1), are strongly connected while the graph affiliated with matrix *A*[3] is not strongly connected since there is not a path between vertices *v*[1] and *v*[3] or *v*[2] and *v*[4].

![Figure 2.1 Graphs affiliated with Example 2.2.](images/fig2_1.jpg)

[Figure 2.1](#chapter2.xhtml#b2fig2_1) Graphs affiliated with [Example 2.2](#chapter2.xhtml#exam2_2).

A square matrix, *A*, is said to be a **non-negative matrix**, denoted *A* ≥ 0, if all of its entries are non-negative, and a **positive matrix**, denoted *A* > 0, if all of its entries are positive.

A matrix, *A*, is said to be a **primitive matrix** if there exist integer *k* > 0 such that *A*^(*k*) is a positive matrix. A matrix is irreducible if for all (*i*, *j*) there exist a *k* such that *A*[*i*, *j*]^(*k*) > 0.

The following theorem, the Perron-Frobenius theorem, is fundamental in the study of discrete probabilistic behaviors, also called **stochastic processes**, in relation to eigenvalues and eigenvectors of irreducible matrices.

Perron is also credited with a slightly different theorem that relies on a matrix being primitive rather than irreducible.

In the case when a matrix is non-negative but not primitive or irreducible, then the multiplicity of *λ*[*P**F*] may be greater than 1.

Applying the Perron-Frobenius Theorem to the matrix *A* in [Example 2.3](#chapter2.xhtml#exam2_3), *λ*[*P**F*] = *ρ*(*A*) = 6 with corresponding unit eigenvector

  
$$\\begin{array}{r} {\\left\\{ {\\frac{2}{\\sqrt{229}},\\,\\frac{9}{\\sqrt{229}},\\,\\frac{12}{\\sqrt{229}}} \\right\\}.} \\\\ \\end{array}$$  

Similarly, the crime network matrix presented in [Figure 1.8](#chapter1.xhtml#fig1_8) is also irreducible with *λ*[*P**F*] = 4.032 and with a corresponding unit eigenvector

  
$$\\begin{array}{r} {\\left\\{ 0.267,\\, 0.305,\\, 0.163,\\, 0.285,\\, 0.353,\\, 0.324,\\, 0.272,\\, 0.348,\\, 0.322,\\, 0.447 \\right\\}.} \\\\ \\end{array}$$  

## 2.1 Markov Chain Basics

A **stochastic process** is a sequence of random variables indexed over time, either continuous or discrete. We consider here a discrete stochastic process referred to as a **Markov chain**, in which

  
$$\\begin{array}{r} {P(X\_{n} = x\_{n}|X\_{1} = x\_{1},\\,\\ldots,\\, X\_{n - 1} = x\_{n - 1}) = P(X\_{n} = x\_{n}|X\_{n - 1} = x\_{n - 1}).} \\\\ \\end{array}$$  

That is, that the probability of the current state is only dependent on the previous states; there have been no other states that have occurred over time. This property is referred to as the **memoryless property**.

A Markov chain has a corresponding **transition matrix**. The transition matrix, *M*, is a probability matrix, where *M*[*i*, *j*] is the probability of going from state *j* to state *i*,

  
$$\\begin{array}{r} {M\_{i,j} = P(X\_{n} = i,\\, X\_{n - 1} = j).} \\\\ \\end{array}$$  

There are a few ways that we can initially start to analyze the long-term behavior of the states given a transition matrix.

One way is to make an assumption about the initial value of each state, creating an initial vector, *π*. Then the long-term behavior can be found by applying powers of the transition matrix to *π*,

  
$$\\begin{array}{r} {lim\_{k\\rightarrow\\infty}\\, M^{k}\\pi.} \\\\ \\end{array}$$  

Using the general case of the Perron-Frobenius Theorem, we assume that the largest eigenvalue in magnitude *λ*[*P**F*] has a corresponding unit eigenvector *v*.

If *M* is an *n* × *n* transition matrix with entries *M*[*i*, *j*], then

  
$$\\begin{array}{r} {\\lambda\_{PF}v = Mv = {\\sum\\limits\_{j = 1}^{n}M\_{i,j}}v\_{j}.} \\\\ \\end{array}$$  

Thus $\\lambda\_{PF}vv^{T} = {\\sum\\limits\_{j = 1}^{n}M\_{i,j}} = 1$ and *λ*[*P**F*] = 1. In addition,

  
$$\\begin{array}{r} {lim\_{n\\rightarrow\\infty}\\, X\_{n} = lim\_{n\\rightarrow\\infty}\\, M^{n}v = lim\_{n\\rightarrow\\infty}\\,\\lambda\_{PF}^{n}v = v.} \\\\ \\end{array}$$  

The vector $\\frac{v}{\\sum\\limits\_{i}v\_{i}}$ will provide a percent vector for the long-run behavior of the Markov chain.

In general, if *X*[1], *X*[2], …, *X*[*n*] are the states in a Markov chain, then *X*[*i*] is an **absorbing state** if

  
$$\\begin{array}{r} {P(X\_{i} = x\_{i}|X\_{i - 1} = x\_{i}) = 1,} \\\\ \\end{array}$$  

otherwise the state is called a **transient state**.

If there are *q* transient states and *r* absorbing states, the states of a Markov chain can be renumbered, thus permuting the rows and columns of the transition matrix in order to put the transition matrix into the form

  
$$\\begin{array}{l} {\\left( \\begin{array}{ll} Q & 0 \\\\ R & I \\\\ \\end{array} \\right),} \\\\ \\end{array}$$  

where the *q* × *q* matrix *Q* represents the transition between transient states, the *r* × *r* matrix *I* represents absorption, the *q* × *r* matrix *R* represents the transition from a transient state to an absorbing state, and the *r* × *q* matrix 0 represents the lack of ability to move from an absorbing state to a transient state.

By putting the transition matrix into this form, we can employ another important matrix in the study of Markov chains, the **fundamental matrix**,

  
$$\\begin{array}{r} {N = {\\sum\\limits\_{n = 0}^{\\infty}Q^{n}}.} \\\\ \\end{array}$$  

Recall from your study of series that the Taylor series with center 0, also called the Maclaurin series, for the function $\\frac{1}{1 - x}$ is $\\sum\\limits\_{n = 0}^{\\infty}x^{n}$. Similarly, if a Markov chain has at least one absorbing state, then *I* − *Q* is invertible with inverse $N = {\\sum\\limits\_{n = 0}^{\\infty}Q^{n}}$.

The (*i*, *j*)^(th) entry of the fundamental matrix, *N*, represents the expected time that the Markov chain stays in state *X*[*j*] given that it starts in *X*[*i*].

## 2.2 Hidden Markov Models

Markov chains are extremely helpful when we wish to determine a sequence of events based on probabilities of observed behaviors. However, there are times when we wish to make predictions but these probabilities are not already clear or observed. In this case, we say that we have a **Hidden Markov Model, HMM**. We begin with an example,

The question posed in [Example 2.8](#chapter2.xhtml#exam2_8) is one of three common questions that are addressed by hidden Markov models. These questions fit into three general categories

1.  **The Likelihood Problem—determining the probability of an observation sequence given a model**.
    
2.  **The Decoding Problem—determining the most likely sequence of events given an observation sequence**.
    
3.  **The Learning Problem—determining the most likely model (with parameters) given the observation sequence.**
    

### 2.2.1 The Likelihood Problem

Because we will have to use prior information to make some inferences in a hidden markov model, a strong understanding of **Bayes Theorem** is essential.

Two events, *X*[1] and *X*[2], are **mutually exclusive** if

  
$$\\begin{array}{r} {X\_{1} \\cap X\_{2} = \\varnothing.} \\\\ \\end{array}$$  

Events *X*[1], *X*[2], …, *X*[*n*] are **exhaustive** if

  
$$\\begin{array}{r} {\\cup\_{i = 1}^{n}X\_{i} = S,} \\\\ \\end{array}$$  

where *S* is the set of all possible outcomes.

Like we saw in [Example 2.10](#chapter2.xhtml#exam2_10), finding the probability of an observation sequence given a model is a type of likelihood problem. The **Forward/Backward Algorithm** is an algorithm to solve this in general using hidden Markov models.

Now that we have used the Forward Algorithm to compute the probability of the joint observed states, we can use the **Backward Algorithm** to determine marginal probabilities *P*(*H*[*t*] = *k*|*O*).

### 2.2.2 The Decoding Problem

In solving the decoding problem with a HMM, we wish to find the most likely hidden sequence *H*^(\*) of occurring given an observation sequence, *O*. More specifically, the goal of decoding is to determine

  
$$\\begin{array}{r} {H^{\*} = argmax\_{H}P(H|O).} \\\\ \\end{array}$$  

Note that *a**r**g**m**a**x*[*H*]*P*(*H*|*O*) is the maximum probability of a hidden sequence, *H*, over all possible *H*^′*s*, given an observation sequence *O*.

We will employ both the Forward/Backward Algorithm and the **Viterbi Algorithm** in our investigation of the decoding problem.

**Applying the Forward/Backward Algorithm**

Define

  
$$\\begin{aligned} {\\gamma{(H\_{t})}^{k}} & {= P(H\_{t} = k|O,\\lambda)} \\\\ & {= \\frac{P(H\_{t} = k,O|\\lambda)}{P(O|\\lambda)}} \\\\ & {= \\frac{\\alpha{(H\_{t})}^{k}\\beta{(H\_{t})}^{k}}{P(O|\\lambda)}} \\\\ & {= \\frac{\\alpha{(H\_{t})}^{k}\\beta{(H\_{t})}^{k}}{\\alpha(H\_{n}) \\cdot \\beta(H\_{n})}} \\\\ \\end{aligned}$$  

Similar to the Forward/Backward Algorithm, the Viterbi Algorithm still requires knowledge of the the transition matrix, *T*, and the emissions matrix, *E*, as well as *π*, the initial probability distribution of the hidden random variables. We begin by thinking through the recursive idea of Viterbi Algorithm.

Assume that the observed sequence of random variables is *O*[1], *O*[2], …, *O*[*n*] and the hidden sequence of random variables is *H*[1], *H*[2], …, *H*[*n*].

An additional important fact is that the conditional probability *P*(*H*|*O*) is proportional to the joint probability *P*(*H*, *O*),

  
$$\\begin{array}{r} {P(H|O)P(O) = P(H,\\, O)} \\\\ \\end{array}$$  

and thus if we find the hidden sequence that maximizes the joint probability, *P*(*H*, *O*), this sequence will also maximize the conditional probability, *P*(*H*|*O*).

  
$$\\begin{aligned} H^{\*} & {= argmax\_{H\_{i},1 \\leq i \\leq n}P(H\_{i}|O\_{i})} \\\\ & {= argmax\_{H\_{i},1 \\leq i \\leq n}P(H\_{i},O\_{i})} \\\\ & {= argmax\_{H\_{i},1 \\leq i \\leq n - 1}P(O\_{i}|H\_{i})P(H\_{i}|H\_{i - 1})P(H\_{i - 1}|O\_{i - 1}).} \\\\ \\end{aligned}$$  

Thus if *p*[*i*] = *P*(*H*[*i*]|*O*[*i*]), then

  
$$\\begin{array}{r} {p\_{i} = H^{\*} = argmax\_{H\_{i},1 \\leq i \\leq n}{\\prod\\limits\_{i = 2}^{n - 1}P}(O\_{i}|H\_{i}){\\prod\\limits\_{i = 2}^{n}P}(H\_{i}|H\_{i - 1})p\_{1}.} \\\\ \\end{array}$$  

Kalu really wishes to find the hidden sequence that maximizes this likelihood. Revisiting the Viterbi Algorithm matrix and the recursive paths in [Figure 2.5](#chapter2.xhtml#fig2_5), choose the hidden states with the largest probabilities working backwards. Thus the most likely hidden sequence *M* is

  
$$\\begin{array}{r} {\\left\\{ \\text{Bullish},\\,\\text{Bullish},\\,\\text{Bullish} \\right\\}.} \\\\ \\end{array}$$  

The Viterbi Algorithm is a widely used algorithm. For those of you who use speech or hand writing recognition on your personal devices, the Viterbi Algorithm may be used to decipher what you are trying to communicate.

### 2.2.3 The Learning Problem

In both the likelihood and the decoding problems, the model was assumed and fixed. That is, we knew the initial probabilities, *π*, the transmission matrix, *T*, and emission matrix, *E*.

This final type of problem, the learning problem, requires an algorithm that will help determine the optimal model *λ* = (*T*, *E*, *π*). In this section, we will discuss the **Baum-Welch Algorithm**.

Given an initial sequence of observed states *O* = (*O*[1], *O*[2], …, *O*[*n*]), called the **training sequence**, and a hidden sequence *H* = (*H*[1], *H*[2], …, *H*[*n*]), the Baum-Welch Algorithm will find another hidden sequence *H*^′ such that

  
$$\\begin{array}{r} {P(O|H^{\\prime}) \\geq P(O|H).} \\\\ \\end{array}$$  

Ideally, we wish to find *H*^′ such that *P*(*O*|*H*^′) ≥ *P*(*O*|*H*) for all *H*, however, that is not guaranteed under the Baum-Welch Algorithm.

Note that

  
$$\\begin{array}{r} {{\\sum\\limits\_{t = 1}^{T - 1}\\gamma\_{t}}(i)} \\\\ \\end{array}$$  

is the expected number of transitions from *H*[*i*] and

  
$$\\begin{array}{r} {{\\sum\\limits\_{t = 1}^{T - 1}\\xi^{t}}(i)} \\\\ \\end{array}$$  

is the expected number of transitions from *H*[*i*] to *H*[*j*].

Let's put the Baum-Welch Algorithm in action through an example.

Baum-Welch Algorithm is just one method in a larger category of **Expectation Maximization algorithms** that are generally used in machine learning to produce advanced models. There are a variety of **g**radient methods like Baum-Welch Algorithm that have been developed with similar goals in mind.

## 2.3 CASE STUDY: Spread of Infectious Disease

In 2019, the world broke out into an international pandemic which led many to start to think more closely about the mathematics behind the spread of infectious diseases. Many diseases, like COVID-19, in simple terms would be modeled with SIR models, with humans in three categories, S (Susceptible), I (Infectious), and R (Recovered). There are more complex SIR models that provide for temporary immunity, quarantine, or even death.

We will explore a variety of these in this case study. In addition, most infectious disease models would implement a stochastic continuous-time Markov chain model; however, we will focus on discrete time models in this particular case study.

We begin with the basic SIR model. This model has the underlying assumption that birth and death occur at roughly the same rate throughout time. We will also assume that the time step in this model is days; however, parameters could be adjusted to accommodate for other units of time.

If the states of the Markov chain are *X*[1], *X*[2], …, and

  
$$\\begin{array}{r} {P(X\_{t} = R|X\_{t - 1} = R) = 1} \\\\ \\end{array}$$  

then recovery is an absorbing state which would happen in a case when immunity is guaranteed. As of May 2020, there were hopes that some temporary immunity existed but evidence from the outbreak in China showed that if it did exist it was fairly short lived.

We begin by assuming that social distancing is not in place and that there may be some partial immunity based on antibodies but that it is not guaranteed.

One example of a transition matrix,

  
$$\\begin{array}{l} {T = \\left( \\begin{array}{lll} S & I & R \\\\ 0.99998 & 0. & 0.0714286 \\\\ 0.00002 & 0.998 & 0. \\\\ 0. & 0.002 & 0.928571 \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

produces a spread of infection shown in [Figure 2.7](#chapter2.xhtml#fig2_7).

![Figure 2.7 Growth of disease under a simple discrete SIR model.](images/fig2_7.jpg)

[Figure 2.7](#chapter2.xhtml#b2fig2_7) Growth of disease under a simple discrete SIR model.

The **reproduction number**, *R*[0], is the expected number of secondary cases that one case would produce in an entire susceptible population.

A positive reproduction number is indicative of a possible probability of outbreak, while a negative *R*[0] indicates that an outbreak is not possible.

  
$$\\begin{array}{r} {R\_{0} = \\frac{\\text{infection~rate}}{\\text{the~expected~disease~length}}.} \\\\ \\end{array}$$  

In the simplest models, *R*[0] can be estimated by the rate of infection, *r*[0], and the estimated length of the infection, *L*, where

  
$$\\begin{array}{r} {R\_{0} \\approx 1 + r\_{0}L.} \\\\ \\end{array}$$  

Thus for the model shown in [Figure 2.7](#chapter2.xhtml#fig2_7), if we estimate *r*[0] ≈ .017 and *L* = 21 days then *R*[0] ≈ 1.357.

If instead, immunity is present and thus recovery acts as an absorbing state, one might see a behavior such as in [Figure 2.8](#chapter2.xhtml#fig2_8).

![Figure 2.8 Growth of disease under SIR model with immunity.](images/fig2_8.jpg)

[Figure 2.8](#chapter2.xhtml#b2fig2_8) Growth of disease under SIR model with immunity.

In this case, let's assume that the transition matrix is

  
$$\\begin{array}{l} {T = \\left( \\begin{array}{lll} S & I & R \\\\ 0.98 & 0 & 0 \\\\ 0.02 & 0.96 & 0 \\\\ 0 & 0.04 & 1 \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

Then the the expected time from susceptible to recovery can be found using

  
$$\\begin{array}{l} {N = {(I - Q)}^{- 1} = \\left( \\begin{array}{ll} 50 & 0. \\\\ 25 & 25 \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

Thus we should expect that a susceptible human will stay susceptible for 50 days and then stay infectious for 25 days before reaching a permanent recovery.

Let's expand our model of the epidemic to include one additional state, susceptible and social distancing (SS). We will assume that there are still susceptible individuals who are not social distancing (S); however, for those who social distance, the transmission to other individuals is much less likely, and those who are recovered make the decision to social distance in the future.

Using the transition matrix

  
$$\\begin{array}{l} {T = \\left( \\begin{array}{llll} S & {SS} & I & R \\\\ 0.9 & 0. & 0. & 0 \\\\ 0. & 0.99 & 0 & 0. \\\\ 0.1 & 0.01 & 0.96 & 0. \\\\ 0. & 0. & 0.04 & 1 \\\\ \\end{array} \\right)} \\\\ \\end{array}$$  

the behavior can be seen in [Figure 2.9](#chapter2.xhtml#fig2_9). In this model, a susceptible person who is not social distancing, will become infected within 10 days on average, where a susceptible person who is social distancing is expected to take about 100 days to get infected with the disease.

![Figure 2.9 Growth of disease under SIR model with Social Distancing.](images/fig2_9.jpg)

[Figure 2.9](#chapter2.xhtml#b2fig2_9) Growth of disease under SIR model with Social Distancing.

If we think of the model in terms of fertility, where fertility keeps track of the number of new cases produced, and transition, then the population can be described

  
$$\\begin{array}{r} {P = F + T,} \\\\ \\end{array}$$  

where *F* is a matrix representing the fertility among classes and *T* represents the transition between classes. If (*I* − *T*)^( − 1) exists, we can determine the net reproductive value, *n*, \[[7](#refbib.xhtml#refbib7)\]

  
$$\\begin{array}{r} {n = \\rho({(I - T)}^{- 1}F)} \\\\ \\end{array}$$  

and the exponential growth rate, *ρ*(*P*).

## 2.4 CASE STUDY: Text Analysis and Autocorrect

In [Chapter 3](#chapter3.xhtml), we will explore data compression techniques in order to do comparative analyses of text. Here we explore different ways that Markov chains can be applied to text analysis by looking at a small text analysis of Jane Austen's work.

There are over 13,000 unique word pairings in Jane Austen's texts, we explore just a few with the transition matrix.

  
$$\\begin{array}{l} {T = \\begin{array}{l} {miss} \\\\ {anne} \\\\ {poor} \\\\ {marianne} \\\\ {when} \\\\ {replied} \\\\ {with} \\\\ {felt} \\\\ {jane} \\\\ {appeared} \\\\ {cried} \\\\ {but} \\\\ \\end{array}\\left( \\begin{array}{llllllllllll} {miss} & {anne} & {poor} & {marianne} & {when} & {replied} & {with} & {felt} & {jane} & {appeared} & {cried} & {but} \\\\ 0 & 0 & 0.04 & 0 & 0.10 & 0 & 0 & 0 & 0.08 & 0 & 0.05 & 0.04 \\\\ 0.93 & 0 & 0.64 & 0 & 0 & 0.58 & 0 & 0 & 0 & 0 & 0.75 & 0.7 \\\\ 0 & 0 & 0 & 0 & 0.10 & 0 & 0 & 0 & 0 & 0 & 0 & 0.04 \\\\ 0.02 & 0 & 0.04 & 0 & 0.10 & 0.03 & 0.01 & 0.13 & 0 & 0 & 0.10 & 0.04 \\\\ 0.01 & 0.09 & 0 & 0.04 & 0 & 0 & 0.01 & 0.13 & 0.08 & 0.2 & 0.05 & 0.04 \\\\ 0 & 0.09 & 0 & 0.04 & 0.00 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 0 & 0.09 & 0.04 & 0.04 & 0.10 & 0.03 & 0 & 0.13 & 0 & 0.2 & 0.05 & 0.04 \\\\ 0 & 0.18 & 0 & 0.08 & 0 & 0 & 0 & 0 & 0.15 & 0 & 0 & 0.06 \\\\ 0.03 & 0 & 0.04 & 0.00 & 0.10 & 0.06 & 0.01 & 0 & 0 & 0 & 0 & 0.04 \\\\ 0 & 0 & 0 & 0.46 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 0 & 0.18 & 0 & 0.13 & 0 & 0 & 0 & 0 & 0.23 & 0 & 0 & 0 \\\\ 0 & 0.36 & 0.21 & 0.21 & 0.50 & 0.29 & 0.07 & 0.63 & 0.46 & 0.6 & 0 & 0 \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

For this small study, we will assume that the words in the transition matrix are the only ones present in Austen's work. Python and R syntax to find a database of word pairs to create a similar transition matrix for all of Austen's work similar can be found at Github links 11 and 12.

You should not be surprised to hear that a matrix with so many word choices as that which is actually in these works would produce a very **sparse matrix** with many entries equal to zero.

If we wished to create a random quote of 4 words from Jane Austen's likely transitions in *T* and we wanted the quote to start with *Marianne*, we might look at the adjacencies to *T*[4] since *Marianne* is represented in the 4^(th) row of *T*.

  
$$\\begin{array}{r} {\\left\\{ I,\\, T,\\, T^{2},\\, T^{3} \\right\\}.\\left\\{ 0,0,0,1,0,0,0,0,0,0,0,0 \\right\\}.} \\\\ \\end{array}$$  

  
$$\\begin{array}{l} {\\begin{array}{l} \\\\ {miss} \\\\ {Anne} \\\\ {poor} \\\\ {marianne} \\\\ {when} \\\\ {replied} \\\\ {with} \\\\ {felt} \\\\ {jane} \\\\ {appeared} \\\\ {cried} \\\\ {but} \\\\ \\end{array}\\left( \\begin{array}{llll} & & {Marianne} & \\\\ {\\, I} & T & T^{2} & T^{3} \\\\ 0 & 0 & 0.02 & 0.03 \\\\ 0 & 0 & 0.26 & 0.3 \\\\ 0 & 0 & 0.01 & 0.03 \\\\ 1 & 0 & 0.04 & 0.05 \\\\ 0 & 0.04 & 0.12 & 0.06 \\\\ 0 & 0.04 & 0 & 0.03 \\\\ 0 & 0.04 & 0.12 & 0.06 \\\\ 0 & 0.08 & 0.01 & 0.08 \\\\ 0 & 0 & 0.02 & 0.04 \\\\ 0 & 0.46 & 0 & 0.02 \\\\ 0 & 0.12 & 0 & 0.06 \\\\ 0 & 0.21 & 0.39 & 0.26 \\\\ \\end{array} \\right),} \\\\ \\end{array}$$  

seen in the columns of the matrix above. To generate our sentence, we may choose to run a simulation using these probabilities to choose our word sequence or choose the most likely sentence to occur based on these probabilities,

  
$$\\begin{array}{r} {Marianne\\, appeared\\, but\\, Anne.} \\\\ \\end{array}$$  

In more practical terms, as mentioned earlier in this chapter, hidden Markov models are regularly used in spoken and handwritten word recognition. Smartphones have built-in software to both suggest words and autocorrect words as you are typing a text.

We will take a deeper look into how hidden Markov chains can be applied to autocorrect or autocomplete in this case study. Suppose that the observed word set, the words that are in the text, that we wish to look at is

  
$$\\begin{array}{r} \\left\\{ heal,\\, hear,\\, here,\\, heel,\\, hele,\\, Hela \\right\\} \\\\ \\end{array}$$  

The language-correct software will choose the word that is most likely to occur, but may not choose until there is a dominant choice. For example, let's assume that the first two letters in the word are known to be *he* and that the transition matrix between letters is known to be

  
$$\\begin{array}{l} {T = \\begin{array}{l} a \\\\ e \\\\ l \\\\ r \\\\ \\end{array}\\left( \\begin{array}{llll} a & e & l & r \\\\ .10 & .29 & .33 & .21 \\\\ .17 & .18 & .40 & .36 \\\\ .28 & .21 & .27 & .29 \\\\ .45 & .32 & 0 & .14 \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

Like the Jane Austen example presented earlier, given that the first two letters in the word are *he* we will look at {*T*, *T*²}.{0,1,0,0}, presented in the columns in the matrix below, to determine the most likely choice for the last two letters in the word,

  
$$\\begin{array}{l} {\\begin{array}{l} a \\\\ e \\\\ l \\\\ r \\\\ \\end{array}\\left( \\begin{array}{ll} 0.29 & 0.22 \\\\ 0.18 & 0.28 \\\\ 0.21 & 0.27 \\\\ 0.32 & 0.23 \\\\ \\end{array} \\right),} \\\\ \\end{array}$$  

which is *here*.

Next, let's assume that you have typed a three letter word incorrect as *aer*. Your phone software determines that this word is incorrect since it is not in it's dictionary database, so the software chooses to autocorrect.

Your typed word provides the observation sequence

  
$$\\begin{array}{r} {O = \\left\\{ a,\\, e,\\, r \\right\\}.} \\\\ \\end{array}$$  

and we wish to determine the most likely hidden sequence. In this case, we will assume that the only possible hidden states are *a, e, l*, and *r*.

We assume that the initial probability is $\\pi = \\left\\{ \\frac{3}{4},\\,\\frac{1}{8},\\, 0,\\,\\frac{1}{8} \\right\\}$.

Using the Viterbi Algorithm, the most likely hidden sequence is *are*, which can be seen in [Figure 2.10](#chapter2.xhtml#fig2_10). The likelihood of the hidden sequence *are* in this situation is approximately .06%.

![Figure 2.10 Viterbi Algorithm Example for Autocorrect.](images/fig2_10.jpg)

[Figure 2.10](#chapter2.xhtml#b2fig2_10) Viterbi Algorithm Example for Autocorrect.

In order to access the bigram data used in this study, go to Github link 13.

## 2.5 CASE STUDY: Tweets and Time Series

In \[[16](#refbib.xhtml#refbib16)\] and \[[25](#refbib.xhtml#refbib25)\], the authors discuss how hidden Markov models can be used to predict stock market behavior. In this case study, we take a close look at a few different observation sequences for making such predictions.

We begin with an observation sequence described by states related to data on the S & P 500 index. Continuous Markov chains and continuous HMMs can be applied in this situation. Since we have not focused on continuous models, an altered discrete model is discussed here.

In this case study, an observation state, *O*[*t*], will be defined as a three-dimensional binary vector where

  
$$\\begin{array}{ll} O\_{t} & {= \\left( {O\_{t}^{(1)},\\mspace{6mu} O\_{t}^{(2)},\\mspace{6mu} O\_{t}^{(3)}} \\right)} \\\\ & {= \\left( {1 + \\left\\lfloor \\frac{close - open}{open} \\right\\rfloor,\\mspace{6mu} 1 + \\left\\lfloor \\frac{high - open}{open} \\right\\rfloor,\\mspace{6mu} 1 + \\left\\lfloor \\frac{low - open}{open} \\right\\rfloor} \\right),} \\\\ \\end{array}$$  

where open refers to the opening value of the S & P 500 index on day *t*, closing is the day *t* closing value, and high and low are the high and low values of day *t*.

Note that a trader is looking for increasing and decreasing behaviors and a 1 in *O*[*t*] would represent an increase, where a 0 would represent a decrease. These particular observation states will allow for a record of variation throughout time.

Since we wish to use trends to predict future values, we will assume a *d* = 2 day latency period. For simplicity, *d* is chosen to be small for this case study. Longer latency period could be selected and analyzed in a similar manner.

Thus a trader's problem becomes the following:

*Given the observation sequence* *O* = (*O*[1], *O*[2]) *and the model *λ*, predict general relationships between opening, closing, low, and high values on day 3*.

We will use the forward-backward method to determine the hidden sequence *H* = (*O*[2], *O*[3]). More particularly, we wish to determine

  
$$\\begin{aligned} H^{\*} & {= argmax\_{O\_{3}}P(O\_{3}|O,\\,\\lambda)} \\\\ & {= argmax\_{O\_{3}}P(O\_{1},\\, O\_{2},\\, O\_{3}|\\lambda).} \\\\ \\end{aligned}$$  

In this case study, we demonstrate with a small training set pulled from \[[13](#refbib.xhtml#refbib13)\] from May 2019, which can be seen in [Table 2.1](#chapter2.xhtml#tbl2_1). A larger data set for further study can be found at Github link 16.

[Table 2.1](#chapter2.xhtml#b2tbl2_1) Observation State, *O*, in May 2019 for S & P 500.

  
| Date, *t* || 5/1 || 5/2 || 5/3 || 5/6 || 5/7 || 5/8 || 5/9 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| (*O*[*t*]^((1)), *O*[*t*]^((2)), *O*[*t*]^((3))) || (0,1,0) || (0,1,0) || (1,1,1) || (1,1,0) || (0,1,0) || (0,1,0) || (1,1,0) |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Date, *t* || 5/10 || 5/13 || 5/14 || 5/15 || 5/16 || 5/17 || 5/20 |
| (*O*[*t*]^((1)), *O*[*t*]^((2)), *O*[*t*]^((3))) || (1,1,0) || (0,1,0) || (1,1,1) || (1,1,0) || (1,1,1) || (1,1,0) || (0,1,0) |
| Date, *t* || 5/21 || 5/22 || 5/23 || 5/24 || 5/28 || 5/29 || 5/30 |
| (*O*[*t*]^((1)), *O*[*t*]^((2)), *O*[*t*]^((3)) || (1,1,1) || (1,1,0) || (0,1,0) || (0,1,0) || (0,1,0) || (0,1,0) || (1,1,0) |

The probabilities for *O*[*t*], listed in [Table 2.2](#chapter2.xhtml#tbl2_2), are found using the data in [Table 2.1](#chapter2.xhtml#tbl2_1). Keep in mind that there are eight possible triplets for *O*[*t*]; however, only the states that were prevalent in the May 2019 ([Table 2.1](#chapter2.xhtml#tbl2_1)) data are presented here.

[Table 2.2](#chapter2.xhtml#b2tbl2_2) *P(O)*.

  
| *O* || (0,1,0) || (1,1,0) || (1,1,1) |
| --- | --- | --- | --- |
| *π* || .524 || .286 || .190 |
| --- | --- | --- | --- |

The transmission matrix

  
$$\\begin{array}{l} {T = \\left( \\begin{array}{llll} & {(0,1,0)} & {(1,1,0)} & {(1,1,1)} \\\\ {(0,1,0)} & .454 & .66 & 0 \\\\ {(1,1,0)} & .273 & .17 & 1 \\\\ {(1,1,1)} & .273 & .17 & 0 \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

Using this transmission matrix,

  
$$\\begin{array}{l} {T^{2} = \\left( \\begin{array}{llll} & {(0,1,0)} & {(1,1,0)} & {(1,1,1)} \\\\ {(0,1,0)} & 0.386 & 0.412 & 0.66 \\\\ {(1,1,0)} & 0.443 & 0.379 & 0.17 \\\\ {(1,1,1)} & 0.17 & 0.209 & 0.17 \\\\ \\end{array} \\right),} \\\\ \\end{array}$$  

If the trader observes that the *O*[5/29] = (0, 1, 0) but does not know the observation of *O*[5/30], then using *T*², the trader might guess that the behavior on May 31^(st) would be (1,1,0). This means that the closing and high values are larger than the opening, and that the low value is lower than the opening value on that day.

In addition, the distribution *P*(*O*[3]) can be determined

  
$$\\begin{array}{l} {T^{2}\\pi = P(O\_{3}) = \\left\\{ \\begin{array}{ll} .446 & {\\text{if~}O\_{3} = (0,1,0),} \\\\ .373 & {\\text{if~}O\_{3} = (1,1,0),} \\\\ .181 & {\\text{if~}O\_{3} = (1,1,1),} \\\\ 0 & {\\text{otherwise}.} \\\\ \\end{array}~ \\right.} \\\\ \\end{array}$$  

This tells the trader that the most probable observation given during the month of data is (0,1,0). The trader could use this information to simulate the behavior of the closing cost relative to the opening over a future period of time as well.

There are many ways that investors predict the future of their products, including stocks. Another way to do this is through sentiment analysis of tweets, reviews, and other types of posts. Similar to Rath and Kalu's analysis presented earlier in this chapter, studies have shown that the market can react to media statements from prominent leaders, such as presidential tweets \[[21](#refbib.xhtml#refbib21)\].

If a trader wishes to study the market from this perspective, they could scrape tweets from a variety of sights, such as that seen in \[[30](#refbib.xhtml#refbib30)\], and set up a word bank to search for words that resemble bearish or bullish market behavior.

For the following example, we pull 11 Trump tweets from roughly the beginning of 11 consecutive months, shown in [Table 2.3](#chapter2.xhtml#tbl2_3). Words that should be considered in a sentiment word bank are italicized. In addition, the opening of the S & P 500 index on each of the day of the tweet and the following trading day are shown in [Table 2.4](#chapter2.xhtml#tbl2_4).

[Table 2.3](#chapter2.xhtml#b2tbl2_3) 

  
| Date || Tweet || Sentiment |
| --- | --- | --- |
| 10/2/2019 || “All of this *impeachment* nonsense, which is going nowhere,is driving the Stock Market, and your 401K's, *down*.” || Bearish |
| --- | --- | --- |
| 11/1/2019 || “Stock Market *up* BIG!” || Bullish |
| 12/2/2019 || “U.S. Markets are *up* as much as 21%since the announcement of Tariffs” || Bullish |
| 1/9/2020 || “STOCK MARKET AT ALL-TIME *HIGH*! || Bullish |
| 2/4/2020 || “Market *up* big today on very *good* economic news || Bullish |
| 3/9/2020 || “…That, and the Fake News, is the reason for the market *drop*!” || Bearish |
| 4/8/2020 || “… Our Economy will *BOOM*, perhaps like never before!” || Bullish |
| 5/13/2020 || “When the so-called rich guys speak *negatively* about the market,you must always remember that some are betting big *against* it….” || Bearish |
| 6/5/2020 || “It's a *stupendous* number. It's joyous, let's call it like it is.” || Bullish |
| 7/21/2020 || “Vote for the Radical Left with their BIG *Tax Hikes*” || Bearish |
| 8/24/2020 || “Joe would end it all and close it all *down*.” || Bearish |

[Table 2.4](#chapter2.xhtml#b2tbl2_4) S & P 500 index behavior trends.

  
| Date || Opening || Date || Opening || Trend |
| --- | --- | --- | --- | --- |
| 10/2/2019 || 2924.78 || 10/3/2019 || 2885.37 || D |
| --- | --- | --- | --- | --- |
| 11/1/2019 || 3050.72 || 11/4/2019 || 3078.95 || U |
| 12/2/2019 || 3143.85 || 12/3/2019 || 3087.40 || D |
| 1/9/2020 || 3266.03 || 1/10/2019 || 3281.81 || U |
| 2/4/2020 || 3280.61 || 2/5/2020 || 3324.90 || U |
| 3/9/2020 || 2863.89 || 3/10/2020 || 2813.47 || D |
| 4/8/2020 || 2685 || 4/9/2020 || 2776.98 || U |
| 5/13/2020 || 2865.86 || 5/14/2020 || 2794.54 || D |
| 6/5/2020 || 3163.84 || 6/8/2020 || 3199.92 || U |
| 7/21/2020 || 3268.52 || 7/22/2020 || 3254.86 || D |
| 8/24/2020 || 3418.09 || 8/25/2020 || 3435.95 || U |

A larger dataset of Trump tweets about the stock market can be found at Github link 18.

In this example, we will use the sentiment of Trump tweets in order to predict the change from opening to closing behavior in the S & P 500 index. We will assume that stock behaviors are monthly; however, in a real-life model with a much larger data set, a similar analysis should be done with daily trends. The data from [Table 2.3](#chapter2.xhtml#tbl2_3) is used to create the transmission matrix

  
$$\\begin{array}{l} {T = \\begin{array}{l} {Up} \\\\ {Down} \\\\ \\end{array}\\left( \\begin{array}{ll} {Up} & {Down} \\\\ \\frac{1}{5} & 1 \\\\ \\frac{4}{5} & 0 \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

and the emission matrix

  
$$\\begin{array}{l} {E = \\begin{array}{l} {Bull} \\\\ {Bear} \\\\ \\end{array}\\left( \\begin{array}{ll} U & D \\\\ \\frac{5}{6} & \\frac{1}{5} \\\\ \\frac{1}{6} & \\frac{4}{5} \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

In addition,

  
$$\\begin{array}{r} {\\pi = (P(Up),\\, P(Down)) = \\left( {\\frac{6}{11},\\,\\frac{5}{11}} \\right).} \\\\ \\end{array}$$  

We begin by studying three month, or one quarter, trends and finding the most likely observation sequence

  
$$\\begin{array}{r} {O = (O\_{1},\\, O\_{2},\\, O\_{3}),} \\\\ \\end{array}$$  

where *O*[*i*] represents the sentiment in Trump's tweet at time *i* in the three month sequence and

  
$$\\begin{array}{r} {H = (H\_{1},\\, H\_{2},\\, H\_{3}),} \\\\ \\end{array}$$  

where *H*[*i*] represents the difference between closing and opening on the *i*^(th) month of the three month sequence. Notice that

  
$$\\begin{array}{r} {E \\cdot T \\cdot \\pi = (0.55697,\\, 0.44303)\\text{~and~}E \\cdot T^{2} \\cdot \\pi = (0.547758,\\, 0.452242)} \\\\ \\end{array}$$  

and thus the most likely scenario in that Trump's three month tweet sentiment will be

  
$$\\begin{array}{r} {\\text{(Bullish,~Bullish,~Bullish)}\\text{.}} \\\\ \\end{array}$$  

Additionally, the unit eigenvector, *v*, associated with *λ*[*P**F*], for *E*.*T*,

  
$$\\begin{array}{r} {v = (0.553097,\\, 0.446903).} \\\\ \\end{array}$$  

Thus, over a long period of time, it is much more likely that the monthly sentiment for Trump's tweets is Bullish, based on the given data.

More importantly, one might wish to know, if Trump's monthly tweets are of a certain observation sequence, such as (Bullish, Bullish, Bullish), what is happening in the market?

In this case Viterbi's Algorithm can be followed. A diagram of Viterbi's Algorithm can be found in [Figure 2.11](#chapter2.xhtml#fig2_11) which shows that if Trump's three month tweet sentiment is (Bullish, Bearish, Bullish) the most likely hidden sequence of the market is

  
$$\\begin{array}{r} {\\text{~(Up,~Down,~Up)~with~probability~}.2523.} \\\\ \\end{array}$$  

![Figure 2.11 Viterbi's Algorithm for three month marker trends based on tweets.](images/fig2_11.jpg)

[Figure 2.11](#chapter2.xhtml#b2fig2_11) Viterbi's Algorithm for three month marker trends based on tweets.

Finally, we wish to find the best model. We begin by assuming that

  
$$\\begin{array}{r} {O = (Bullish,\\, Bullish,\\, Bullish),} \\\\ \\end{array}$$  

the first three states in [Table 2.3](#chapter2.xhtml#tbl2_3), then

  
$$\\begin{aligned} {\\alpha{(H\_{1})}^{U}} & {= \\frac{5}{11},\\,\\,\\,\\,\\alpha{(H\_{1})}^{D} = \\frac{1}{11},} \\\\ {\\alpha{(H\_{2})}^{U}} & {= \\frac{1}{33},\\,\\,\\,\\,\\alpha{(H\_{2})}^{D} = \\frac{16}{55},} \\\\ {\\alpha{(H\_{3})}^{U}} & {= \\frac{49}{198},\\,\\,\\,\\alpha{(H\_{3})}^{D} = \\frac{4}{825},} \\\\ \\end{aligned}$$  

  
$$\\begin{aligned} {\\beta{(H\_{3})}^{U}} & {= 1,\\,\\,\\,\\,\\,\\beta{(H\_{3})}^{D} = 1,} \\\\ {\\beta{(H\_{2})}^{U}} & {= \\frac{9}{150},\\,\\,\\beta{(H\_{2})}^{D} = \\frac{5}{6},} \\\\ {\\beta{(H\_{1})}^{U}} & {= \\frac{2449}{4500},\\,\\beta{(H\_{1})}^{D} = \\frac{49}{900}.} \\\\ \\end{aligned}$$  

Note that these values tell us that

  
$$\\begin{array}{r} {P(O|\\lambda) = {\\sum\\limits\_{k}\\alpha}{(H\_{3})}^{k} = 0.2523.} \\\\ \\end{array}$$  

Using this information, we determine

  
$$\\begin{array}{r} {\\gamma{(H\_{1})}^{(U,D)} = \\left\\{ 0.98038431,\\, 0.01961569 \\right\\},} \\\\ \\end{array}$$  

  
$$\\begin{array}{r} {\\gamma{(H\_{2})}^{(U,D)} = \\left\\{ 0.03923139,\\, 0.96076861 \\right\\},} \\\\ \\end{array}$$  

  
$$\\begin{array}{r} {\\gamma{(H\_{3})}^{(U,D)} = \\left\\{ 0.98078463,\\, 0.01921537 \\right\\},} \\\\ \\end{array}$$  

  
$$\\begin{aligned} {\\xi\_{t}(i,j)} & {= P(H\_{t} = j,H\_{t + 1} = i|O,\\lambda)} \\\\ & {= \\alpha(H\_{i})E\_{H\_{t + 1},j}T\_{i,j}\\beta(H\_{t + 1})} \\\\ \\end{aligned}$$  

and the new model is *π*^(*n**e**w*) = {0.98038431, 0.01961569}.

  
$$\\begin{array}{l} {T^{new} = \\left( \\begin{array}{ll} 0.51020408 & 1 \\\\ 0.48979592 & 0 \\\\ \\end{array} \\right),\\, E^{new} = \\left( \\begin{array}{ll} 0.96153846 & 0.01960784 \\\\ 0.03846154 & 0.98039216 \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

Keep in mind that this is just one iteration of the Baum-Welch algorithm.

Python and R code related to this case study can be found at Github links 14 and 15, respectively.

## 2.6 Exercises

*   Determine which of the following matrices are primitive or irreducible.
    
      
    $$\\begin{array}{l} {A\_{1} = \\left( \\begin{array}{ll} 0 & 2 \\\\ 1 & 1 \\\\ \\end{array} \\right),\\, A\_{2} = \\left( \\begin{array}{ll} 2 & 0 \\\\ 1 & 1 \\\\ \\end{array} \\right)} \\\\ \\end{array}$$  
    
*   Assume that from the beginning of time, UNC, Duke, and NC State admitted only male students. Also assume that, at that time, 70 percent of the sons of UNC men went to UNC and the rest went to NC State, 50 percent of the sons of NC State men went to NC State, and the rest split evenly between UNC and Duke; and of the sons of Duke men, 80 percent went to Duke, 10 percent to UNC, and 10 percent to NC State.
    
    If this were still the case (and these were the only 3 universities), use the Perron-Frobenius Theorem to determine what percent of students would be at each institution long into the future.
    
*   If the students that attended Duke live in Raleigh, Chapel Hill, and Durham with probabilities 25%, 35%, and 40% respectively. While students that attend UNC live in Raleigh, Chapel Hill, and Durham with probabilities 30%, 60%, and 10%. Finally, the students that attend NC State live in Raleigh, Chapel Hill and Durham with probability 60%, 20%, and 20%. Those who are from Durham, Raleigh, and Chapel Hill, go to Duke (50%), UNC (20%), and NC State (30%).
    
    Determine the probability that a student goes to Duke given that they are from Durham.
    
*   An epidemic is beginning to become prevalent in two different countries, *A* and *B*. Citizens of those countries can be in one of three states, susceptible (S), infectious (I), or recovered (R). From our daily observations a few weeks into the outbreak, we note that the probabilities between the observed states of the infection among its citizens and the probabilities between the states of the infection.
    
    If the population of country *A* is twice as large as the population of country *B*, and we randomly sample four citizens from the combined countries, use hidden markov chains to determine the probability that they are from countries AABB given that their status is SIRS.
    
    ![](images/ufig2_1.jpg)
*   After thinking about [Example 2.14](#chapter2.xhtml#exam2_14), determine the following
    
    1.  *P*(*O*[1] = *S**a**d*)
        
    2.  *P*(*O*[1] = *S**a**d*, *O*[2] = *S**a**d*)
        
    3.  *P*(*O*[1] = *S**a**d*, *O*[2] = *S**a**d*, *O*[3] = *H**a**p**p**y*)
        
    4.  The maximum likelihood of the observation sequence {*S**a**d*, *S**a**d*, *H**a**p**p**y*} occurring.
        
    5.  The most likely hidden sequence given that Rath is {*S**a**d*, *S**a**d*, *H**a**p**p**y*}.
        
*   In the theme of attempting to find the best model, use the information from [Example 2.16](#chapter2.xhtml#exam2_16), apply the Baum-Welch Algorithm one additional time in order to find a new model *λ* = (*π*, *T*, *E*).
    
*   Doctors are trying to determine the original genetic making up of their patients given mutated DNA sequences collected from biopsied patients. You are given a mutated DNA sequence, **ATG** where, A (adenine), C (cytosine), G (guanine), and T (thymine). The transmission matrix, *T*, and emissions matrix, *E*, are as follows.
    
      
    $$\\begin{array}{l} {T = E = \\left( \\begin{array}{lllll} & A & C & G & T \\\\ A & .40 & .225 & .400 & .252 \\\\ C & .20 & .325 & .100 & .223 \\\\ G & .15 & .300 & .200 & .177 \\\\ T & .25 & .150 & .300 & .348 \\\\ \\end{array} \\right)} \\\\ \\end{array}$$  
    
    In addition, assume that the four state, A, C, G, and T, are equally likely. Determine the likelihood of the observation sequence **ATG** using the forward algorithm.
    
*   Using the information from Exercise 7 and the Forward/Backward algorithm, find the most likely original molecular structure of the genetic code with the four possible hidden state, A (adenine), C (cytosine), G (guanine), and T (thymine).
    

# 3SVD and PCA

DOI: [10.1201/9781003025672-3](https://doi.org/10.1201/9781003025672-3)

Like [Chapter 1](#chapter1.xhtml), this chapter on clustering techniques and their application to data science. [Chapter 1](#chapter1.xhtml) relies heavily on powers of matrices, eigenvalues, and eigenvectors, which are only relevant for square matrices. This chapter digs deeper into techniques that are more practical in terms, not imposing the limitation that matrices must be square.

We begin with an overview of vector and inner product spaces since orthogonality is pertinent in the discussion of further topics in the chapter.

## 3.1 Vector and Inner Product Spaces

A set of vectors, *V*, under defined vector addition and scalar multiplication is called a **vector space** if the following properties hold.

1.  *V* is closed under vector addition.
    
2.  *V* is closed under scalar multiplication.
    
3.  For all *u* and *v* in *V*, *u* + *v* = *v* + *u*.
    
4.  For all *u,v* and *w* in *V*,
    
      
    $$\\begin{array}{r} {(u + v) + w = u + (v + w).} \\\\ \\end{array}$$  
    
5.  There exists an unique additive identity in *V*.
    
6.  Every vector *u* ∈ *V* has an additive inverse  − *u* ∈ *V*.
    
7.  For each vector *u* ∈ *V*, 1 ⋅ *u* = *u*.
    
8.  For all *u* and *v* in *V* and scalar *k*, *k*(*u* + *v*) = *k**u* + *k**v*.
    
9.  For all *u* in *V* and scalars *k* and *l*, (*k* + *l*)*u* = *k**u* + *l**u*.
    
10.  For all *u* and *v* in *V* and scalar *k*, *k*(*l**u*) = (*k**l*)*u*.
     

An **inner product** on a set *V* is a function that maps order pairs (*x*, *y*) ∈ *V* × *V* to a number  < *x*, *y*\> while satisfying the following properties:

1.  For all *v* ∈ *V*,  < *v*, *v*\>  ≥ 0 and  < *v*, *v* >  = 0 if and only if $v = \\overset{\\rightarrow}{0}$.
    
2.  For all *u,v*, and *w* ∈ *V*,  < *u*, *v* + *w* >  =  < *u*, *v* >  +  < *u*, *w*\>.
    
3.  For all *u*, *v* ∈ *V* and scalars *k*,  < *k**u*, *v* >  =  < *u*, *k**v* >  = *k* < *u*, *v*\>.
    
4.  For all *u*, *v* ∈ *V*, $< u,v > = \\overline{<v,u>}$.
    

A vector space with a defined inner project is called an **inner product space**.

In an inner product space, *V*, a set of vectors is called **orthogonal** if for each pair of vectors *v* and *w* in *V*,

  
$$\\begin{array}{r} {< v,w > = 0.} \\\\ \\end{array}$$  

If a set of vectors in *V* is orthogonal and each vector is a unit vector, then the set is called **orthonormal**.

## 3.2 Singular Values

When studying data in which each data point has a large number of attributes, it may be helpful to be able to reduce or compress the number of attributes. That is, we may start with data points in ℝ^(*n*) and want to project the data points into ℝ^(*m*) where *n* > *m*.

In order to do so, it is important to reflect on which of the *n* attributes are significant to the data set. We begin this investigation with a review of some key linear algebra terms, linear independence, span, and basis, and an interpretation of the visual aspects of eigenvectors.

Recall that a set of vectors {*v*[1], *v*[2],…, *v*[*m*]} is **linearly independent** if and only if the system of equations

  
$$\\begin{array}{r} {k\_{1}v\_{1} + k\_{2}v\_{2} + \\cdots + k\_{m}v\_{m} = \\overset{\\rightarrow}{0}} \\\\ \\end{array}$$  

has only the trivial solution, *k*[1] = *k*[2] = ⋯ = *k*[*m*] = 0. Otherwise, we say that the set is **linearly dependent**. If the vectors *v*[1], *v*[2], …, *v*[*m*] ∈ ℝ^(*n*), then this system can be written as

  
$$\\begin{matrix} & {Ax = b} \\\\ {\\begin{pmatrix} v\_{1} & v\_{2} & \\cdots & v\_{m} \\\\ \\end{pmatrix}\\begin{pmatrix} k\_{1} \\\\ k\_{2} \\\\ \\vdots \\\\ k\_{m} \\\\ \\end{pmatrix}} & {= \\begin{pmatrix} 0 \\\\ 0 \\\\ \\vdots \\\\ 0 \\\\ \\end{pmatrix}.} \\\\ \\end{matrix}$$  

This is equivalent to saying that the matrix *A*, whose columns are *v*[1], *v*[2], …, *v*[*m*], is invertible.

If *w* is a vector in ℝ^(*n*) and there exists constant *k*[1], *k*[2], …, *k*[*m*] such

  
$$\\begin{array}{r} {w = k\_{1}v\_{1} + k\_{2}v\_{2} + \\cdots + k\_{m}v\_{m},} \\\\ \\end{array}$$  

we say that *w* can be written as a **linear combination** and is in the **span** of the vectors *v*[1], *v*[2], …, *v*[*m*].

The set *S* = {*v*[1], *v*[2],…, *v*[*m*]} is a **basis** for a vector space *V* if *S* is linearly dependent and if every vector in *V* is in the span of *S*.

Let *A* be an *n* × *n* matrix and *T*[*A*]:ℝ^(*n*)→ℝ^(*n*) be a linear transformation with standard matrix *A*, defined as *T*[*A*](*x*) = *A**x*. Then, based on the definition of an eigenvalue *λ*

  
$$\\begin{array}{r} {Ax = \\lambda x,} \\\\ \\end{array}$$  

any basis vector *x* for the eigenspace corresponding to the eigenvector *λ*, also called an eigenvector corresponding *λ*, will be dilated or contracted by a factor of *λ* under the transform *T*[*A*]; however, the direction of *x* will remain unchanged.

Recall that the **span** of a vector in ℝ² is any vector that lies on the same line as the original vector. Most vectors will not remain on their own span under a linear transformation such as *T*[*A*].

An example of a vector, it's span, and the vector under *T*[*A*](*x*) can be seen in [Figure 3.2](#chapter3.xhtml#fig3_2). Note that the eigenvectors of *A*, *x*[1] = {1,1} and *x*[2] = {1,0} will remain on in their span under *T*[*A*](*x*).

![Figure 3.2 An example of a vector, it's span, and the vector under T\_{A}(x).](images/fig3_2.jpg)

[Figure 3.2](#chapter3.xhtml#b3fig3_2) An example of a vector, it's span, and the vector under *T*[*A*](*x*).

We have seen the importance of eigenvalues and eigenvectors in application in [Chapters 1](#chapter1.xhtml) and [2](#chapter2.xhtml). If a matrix is not square, no such values can be determined. In this chapter, we will introduce **singular values**, the analogous values to eigenvalues for non-square matrices, and their importance in data science.

Notice in [Figure 3.1](#chapter3.xhtml#fig3_1) that the grid lines under transformation *T*[*A*](*x*) are no longer orthogonal. If the transformed grid lines remain orthogonal then we call this transformed grid an **orthogonal grid**.

## 3.3 Singular Value Decomposition

The term singular value relates to the distance of the given matrix to a singular matrix. We will explore the concept of singular values in the context of the **Singular Value Decomposition (SVD)** of a matrix.

The **orthogonal components** of a vector *v* in a *n*− dimensional vector space *W* are *v*[*w*] and *v*[*w*^⊥] where *v*[*w*] ∈ *W* and *v*[*w*^⊥] ∈ *W*^⊥ and *v* = *v*[*w*] + *v*[*w*^⊥].

Given an orthonormal basis {*v*[1], *v*[2],⋯, *v*[*n*]} for *W*,

  
$$\\begin{array}{r} {v\_{w} = Proj\_{W}(v) = < v\_{1},v > v\_{1} + < v\_{2},v > v\_{2} + \\cdots + < v\_{n},v > v\_{n}.} \\\\ \\end{array}$$  

Using the theory above, and the visualization from [Example 3.2](#chapter3.xhtml#exam3_2), for any vector *x* in ℝ², *x* = (*v*[1] ⋅ *x*)*v*[1] + (*v*[2] ⋅ *x*)*v*[2], where *v*[1] and *v*[2] are the standard basis vectors for ℝ². Thus,

  
$$\\begin{array}{r} {Ax = A(v\_{1} \\cdot x)v\_{1} + A(v\_{2} \\cdot x)v\_{2} = u\_{1}\\sigma\_{1}(v\_{1} \\cdot x) + u\_{2}\\sigma\_{2}(v\_{2} \\cdot x),} \\\\ \\end{array}$$  

where *σ*[*i*], 1 ≤ *i* ≤ *n* are the singular values of *A*.

Noting that for any two vectors *u* and *w* in ℝ², *u* ⋅ *w* = *u*^(*T*)*w*, we can say that

  
$$\\begin{array}{r} {Ax = u\_{1}\\sigma\_{1}(v\_{1}^{T}x) + u\_{2}\\sigma\_{2}(v\_{2}^{T}x).} \\\\ \\end{array}$$  

More generally, a *m* × *n* matrix *A*, can be decomposed into the product

  
$$\\begin{array}{r} {A = U\\Sigma V^{T}} \\\\ \\end{array}$$  

where *U* is a *m* × *m* orthogonal matrix whose columns form an orthonormal basis for ℝ^(*m*) and *V* is a *n* × *n* orthogonal matrix whose columns form an orthonormal basis for ℝ^(*n*) and *Σ*[*i**i*] = *σ*[*i*] and *σ*[*i**j*] = 0 otherwise.

Since the singular values of a matrix, *A*, are related to the eigenvalues of the symmetric matrix *A*^(*T*)*A*, the Gramian matrix, it is important to note the following property.

Recall from [Chapter 2](#chapter2.xhtml) that all symmetric matrices are orthogonally diagonalizable. Thus for any *m* × *n* matrices *A*, *S* = *A*^(*T*)*A* is a *n* × *n* symmetric matrix and we can find an orthogonal matrix *P* such that

  
$$\\begin{array}{r} {S = PDP^{T}.} \\\\ \\end{array}$$  

This shows an interesting alignment between eigenvalues of *S* and singular values of *A*. Assume that the eigenvalues of *S* are *λ*[1] ≥ *λ*[2] ≥ … ≥ *λ*[*n*] and the corresponding singular values of *A* are *σ*[1] ≥ *σ*[2] ≥ … ≥ *σ*[*n*]. Then,

  
$$\\begin{aligned} S & {= PDP^{T} = {\\sum\\limits\_{i = 1}^{n}\\lambda\_{i}}v\_{i}v\_{i}^{T}} \\\\ A & {= U\\Sigma V^{T} = {\\sum\\limits\_{i = 1}^{n}\\sigma\_{i}}u\_{i}v\_{i}^{T}.} \\\\ \\end{aligned}$$  

## 3.4 Compression of Data Using Principal Component Analysis (PCA)

In data science, you may wish to compare *m* records with *n* attributes in a variety of ways. There are many clustering techniques, but in all of these techniques the data scientist might also be interested in visualizing the data. In order to do this, one should consider how to transform their data from ℝ^(*n*) to ℝ² or ℝ³.

One way to think about this is that you are projecting your data from ℝ^(*n*) into another space, such as ℝ² or ℝ³.

![Figure 3.4 Example of a projection from {\\mathbb{R}}^{3} into {\\mathbb{R}}^{2}.](images/fig3_4.jpg)

Figure 3.4 Example of a projection from ℝ³ into ℝ².

We can do this using SVD by limiting the number of singular values used to reconstruct the original matrix.

Recall that if *A* is a *m* × *n* matrix then the singular value decomposition of *A* = *U**Σ**V*^(*T*) with singular values *σ*[1], *σ*[2]…, *σ*[*n*], Σ is a *m* × *n* matrix such that *Σ*[*i**i*] = *σ*[*i*].

If a data scientist wishes to transform the data from ℝ^(*n*) to ℝ^(*q*), then they could determine the *q* most dominant eigenvalues and define a *q* × *n* matrix *Σ̃* such that ${\\widetilde{\\sum}}\_{ii} = \\sigma\_{i}$.

In turn, matrix *Ũ* would then become a *m* × *q* matrix, where *Ũ*[*i*, *j*] = *U*[*i*, *j*] for 1 ≤ *i* ≤ *m*, 1 ≤ *j* ≤ *q*.

The rows of *Ũ* are vectors in ℝ^(*q*) and are the focus of investigation in Principal Component Analysis (PCA).

There are many reasons why a data scientist may apply PCA. [Example 3.8](#chapter3.xhtml#exam3_8) shows how PCA can be applied to the digital humanities, particularly related to literature analysis.

## 3.5 PCA, Covariance, and Correlation

When studying large data sets with many variables, we may wish to determine patterns in the data and if there are variables that have a strong correlation with one another. In this section, we will look at how PCA can be used to create a **covariance matrix** and **correlation matrix**.

The covariance matrix of a data set *A*, *C**o**v*(*A*), captures the variance and linear correlation in multivariate data. Covariance is a measure of how much *m* records of data, each with *N* attributes or pieces of information, change together.

Note that *C**o**v*(*A*)[*i*, *i*] represents the variance, *σ*[*i*]², in the *i*^(th) data record.

  
$$\\begin{array}{l} {Cov(A) = \\left( \\begin{array}{lllll} {\\sum\\frac{x\_{1}^{2}}{N}} & {\\sum\\frac{x\_{1}x\_{2}}{N}} & {\\sum\\frac{x\_{1}x\_{3}}{N}} & \\ldots & {\\sum\\frac{x\_{1}x\_{m}}{N}} \\\\ {\\sum\\frac{x\_{2}x\_{1}}{N}} & {\\sum\\frac{x\_{2}^{2}}{N}} & {\\sum\\frac{x\_{2}x\_{3}}{N}} & \\ldots & {\\sum\\frac{x\_{2}x\_{m}}{N}} \\\\ {\\sum\\frac{x\_{3}x\_{1}}{N}} & {\\sum\\frac{x\_{3}x\_{2}}{N}} & {\\sum\\frac{x\_{3}^{2}}{N}} & \\ldots & {\\sum\\frac{x\_{3}x\_{m}}{N}} \\\\ \\vdots & \\vdots & \\vdots & \\ddots & \\vdots \\\\ {\\sum\\frac{x\_{m}x\_{1}}{N}} & {\\sum\\frac{x\_{m}x\_{2}}{N}} & {\\sum\\frac{x\_{m}x\_{3}}{N}} & \\ldots & {\\sum\\frac{x\_{m}^{2}}{N}} \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

We begin with an example in just two variables to get a sense of how variance can be modeled using matrices.

Principal Component Analysis can be used to decompose the covariance matrix, limiting the singular values to the ones that are most significant.

The **correlation matrix** associated with a data set, *A*, *C**o**r*(*A*), is just a scaling of the covariance matrix,

  
$$\\begin{array}{r} {Cor{(A)}\_{i,j} = \\frac{Cov{(A)}\_{i,j}}{Cov{(A)}\_{i,i}Cov{(A)}\_{j,j}}} \\\\ \\end{array}$$  

for *i* ≠ *j* and *C**o**r*(*A*)[*i*, *j*] = 1 if *i* = *j*.

It is a good idea to consider using the correlation matrix to study your data, rather than the covariance matrix, if your variables are in scales of very different magnitudes.

These ideas can be expanded to multiple regression techniques using Principal Component Analysis, more commonly called **Principal Component Regression**.

Unlike [Example 3.9](#chapter3.xhtml#exam3_9), where there was only one dependent variable, *x*, and one independent variable, *y*, and *y* = *a**x* + *b* + *e*, with *e* representing the errors in the residuals, it is possible to use principal component regression in a more complex model with *k* independent variables. In this case, the model becomes

  
$$\\begin{array}{r} {y = Xb} \\\\ \\end{array}$$  

where *y* is an *n* × 1 vector, *X* is an *n* × *k* matrix.

Like [Example 3.9](#chapter3.xhtml#exam3_9), one should consider zero-centering or standardizing the data before finding the covariance and correlation matrices. The eigenvectors of the covariance matrix, typically stored in the matrix *U* in the singular value decomposition, give a means of understanding the direction of the data based on that variable. While the singular values, eigenvalues, of the covariance matrix give a sense of how much the data varies in that direction.

Because of the significance of the singular values in determining variance in the data, we must determine how many principal components, *p*, to include in the model. The best way to do this is by inspecting the correlation matrix and omitting small singular values of the correlation matrix, which typically have values significantly less than 1.

In determining a least square regression model with all *k* factors integrated into the model, we wish to determine *b*, where

  
$$\\begin{array}{r} {b = {(X^{T}X)}^{- 1}X^{T}y.} \\\\ \\end{array}$$  

In order to follow this procedure, *X* must be an orthogonal matrix, and thus *X*^(*T*)*X* is diagonal.

Unfortunately, most datasets are correlated and thus *X* is not an orthogonal matrix. This leads most data scientists to proceed with some sort of variable selection and thus replacing the *k* correlated variables of *X* with *p* uncorrelated variables, represented by an *n* × *p* matrix *X̃*.

The Principal Component Regression model *ŷ* = *X̃**b* can be determined by reducing the principal components used to *p* < *k* such that *X̃* = *Ũ* and

  
$$\\begin{array}{r} {b = {({\\widetilde{X}}^{T}\\widetilde{X})}^{- 1}{\\widetilde{X}}^{T}y.} \\\\ \\end{array}$$  

## 3.6 Linear Discriminant Analysis

Like Principal Component Analysis, **Linear Discriminant Analysis** (LDA) is used for dimension reduction. While PCA focuses on determining the principal component axes, those axes that maximize the variance of the data, Linear Discriminant Analysis also attempts to maximize the spread of the clusters or classes in the data.

Something to note is that many times with PCA the data may not be originally clustered into classes; however, it is necessary with LCA to originally be identifying classes in the data.

The idea behind Linear Discriminant Analysis is to choose a projection that will spread out the known classes while minimizing the scatter, or spread, within each class.

Imagine that you have two classes of data in ℝ² and you wish to project the data onto a line. If the classes are indeed unique, the choice of line on which you choose to project does make a difference in terms of between class spread.

For example, in [Figure 3.9](#chapter3.xhtml#fig3_9), the projection of the two classes of data, represented by circles and squares, onto the *x*\-axis and the line *y* = 2*x* do not do a great job of spreading out the two classes, whereas a projection onto the line *y* =  − *x*, seen in [Figure 3.10](#chapter3.xhtml#fig3_10), completely separates the two classes.

![Figure 3.9 Example of projection onto the x-axis and the line y = 2x.](images/fig3_9.jpg)

[Figure 3.9](#chapter3.xhtml#b3fig3_9) Example of projection onto the *x*\-axis and the line *y* = 2*x*.

![Figure 3.10 Example of projection onto the line y = - x.](images/fig3_10.jpg)

[Figure 3.10](#chapter3.xhtml#b3fig3_10) Example of projection onto the line *y* =  − *x*.

Let's assume that there are *n* classes, *C*[1], *C*[2], …, *C*[*n*], where the *i*^(th) class is of size *N*[*i*]. In addition, assume that each vector, *x*, representing an object, has *m* entries and that the line of projection will be represented by the unit vector *v*.

Then the

  
$$\\begin{array}{r} {\\text{~projection~of~}x\\text{~onto~}v = \\frac{< v,\\, x > v}{||v||^{2}}} \\\\ \\end{array}$$  

and the distance that *x* is from the origin is

  
$$\\begin{array}{r} {v^{T}x.} \\\\ \\end{array}$$  

Define *μ̃*[*i*] as the mean of the projections of vectors in classes *C*[*i*] onto the vector *v*. Thus

  
$$\\begin{array}{r} {{\\widetilde{\\mu}}\_{i} = {\\sum\\limits\_{x \\in C\_{i}}\\frac{v^{T}x}{N\_{i}}} = v^{T}{\\sum\\limits\_{x \\in C\_{i}}\\frac{x}{N\_{i}}} = v^{T}\\mu\_{i},} \\\\ \\end{array}$$  

where *μ*[*i*] is the mean of the vectors in class *C*[*i*].

Given two classes *C*[1] and *C*[2], we wish to choose a projection that maximizes

  
$$\\begin{array}{r} {|\\widetilde{\\mu\_{1}} - \\widetilde{\\mu\_{2}}|} \\\\ \\end{array}$$  

in order to maximize the spread of the classes; however, this does not minimize the spread within classes. The objective of Linear Discriminant Analysis is to find a vector *v* that takes each of these criteria into account. In order to do this, we will maximize the objective function

  
$$\\begin{aligned} {J(v)} & {= \\frac{{(\\widetilde{\\mu\_{1}} - \\widetilde{\\mu\_{2}})}^{2}}{{\\sum\\limits\_{x \\in C\_{1}}{(v^{T}x - \\widetilde{\\mu\_{1}})}^{2}} + {\\sum\\limits\_{x \\in C\_{2}}{(v^{T}x - \\widetilde{\\mu\_{2}})}^{2}}}} \\\\ & {= \\frac{{(v^{T}\\mu\_{1} - v^{T}\\mu\_{2})}^{2}}{{\\sum\\limits\_{x \\in C\_{1}}{(v^{T}x - \\widetilde{\\mu\_{1}})}^{2}} + {\\sum\\limits\_{x \\in C\_{2}}{(v^{T}x - \\widetilde{\\mu\_{2}})}^{2}}}.} \\\\ \\end{aligned}$$  

Define the within class scatter matrix,

  
$$\\begin{array}{r} {S\_{W} = {\\sum\\limits\_{i = 1}^{n}{\\sum\\limits\_{x \\in C\_{i}}{(x - \\mu\_{i}){(x - \\mu\_{i})}^{T}}}}} \\\\ \\end{array}$$  

and the between class scatter matrix as

  
$$\\begin{array}{r} {S\_{B} = (\\mu\_{1} - \\mu\_{2}){(\\mu\_{1} - \\mu\_{2})}^{T}.} \\\\ \\end{array}$$  

Then,

  
$$\\begin{array}{r} {J(v) = \\frac{v^{T}S\_{B}v}{v^{T}S\_{W}v}.} \\\\ \\end{array}$$  

In order to maximize *J*(*v*), we determine where $\\frac{\\partial J}{\\partial v} = 0$.

  
$$\\begin{array}{r} {\\frac{\\partial J}{\\partial v} = \\frac{(2S\_{B}v)(v^{T}S\_{W}v) - (2S\_{w}v)(v^{T}S\_{B}v)}{{(v^{T}S\_{W}v)}^{2}} = 0} \\\\ \\end{array}$$  

when (*S*[*B*]*v*)(*v*^(*T*)*S*[*W*]*v*) − (*S*[*W*]*v*)(*v*^(*T*)*S*[*B*]*v*) = 0.

That is, we wish to find *v* such that

  
$$\\begin{array}{r} {S\_{B}v - \\frac{(S\_{W}v)(v^{T}S\_{B}v)}{v^{T}S\_{W}v} = 0.} \\\\ \\end{array}$$  

If *S*[*W*] is invertible and $\\lambda = \\frac{(v^{T}S\_{B}v)}{v^{T}S\_{W}v}$, *S*[*W*]^( − 1)*S*[*B*]*v* = *λ**v* and *v* is the eigenvector associated with matrix *S*[*W*]^( − 1)*S*[*B*] and eigenvalue *λ*.

Another way to think about this, due to the definition of *S*[*B*], is that for any vector *v*, *S*[*B*]*v* points in the same direction as *μ*[1] − *μ*[2]. Therefore, we wish to determine *v* such that

  
$$\\begin{array}{r} {v = S\_{W}^{- 1}(\\mu\_{1} - \\mu\_{2}).} \\\\ \\end{array}$$  

The concepts described in this section can be generalized for a dataset with *n* classes.

1.  Find each class *C*[*i*], 2 ≤ *i* ≤ *n*, find the mean vector,
    
      
    $$\\begin{array}{r} {\\mu\_{i} = {\\sum\\limits\_{v \\in \\, C\_{i}}\\frac{v}{N\_{i}}}.} \\\\ \\end{array}$$  
    
2.  Construct the within class scatter vector *S*[*W*], where the entries of *S*[*W*] are
    
      
    $$\\begin{array}{r} {{\\sum\\limits\_{i = 1}^{n}{\\sum\\limits\_{x \\in C\_{i}}{(x - \\mu\_{i}){(x - \\mu\_{i})}^{T}}}}.} \\\\ \\end{array}$$  
    
3.  Construct the between-class scatter matrix *S*[*B*], where the entries of *S*[*B*] are
    
      
    $$\\begin{array}{r} {{\\sum\\limits\_{i = 1}^{n}N\_{i}}(\\mu\_{i} - \\mu),} \\\\ \\end{array}$$  
    
    where *μ* is the mean of all of the samples.
    
4.  Determine the eigenvector *v* of *S*[*W*]^( − 1)*S*[*B*].
    

## 3.7 CASE STUDY: Digital Humanities

Some digital humanists focus on semantics and words that are regularly used or used in a particular context. In this case study, we will focus on characteristics of different versions of a story that are present or absent in order to determine the story's origin.

The Star Husband Tale was a widely known tale among Native American tribes. The basic form of the Star Husband Tale \[[45](#refbib.xhtml#refbib45)\] tells of two girls who are sleeping out in the open during the night. While outside, they see two stars, and each girl makes a wish to be married to a star. When they awake, both have been transported to the heavens and are married to the stars as they wished. One of the star husbands is a young man, and the other is an older man. The girls at one point start digging in the heavens and make a hole, and they eventually lower themselves down to earth using a rope.

Dundes \[[9](#refbib.xhtml#refbib9)\] discusses narrative elements of 86 versions of the Star Husband Tale coming from 44 tribes, grouped into nine geographical zones: Eskimo, Mackenzie, North Pacific, California, Plateau, Plains, Southeast, Southwest, and Woodlands. In this case study, we will explore the 10 tales in the Woodlands tribe and some of their archetypes and subarchetypes. These archetypes and subarchetypes include how the girl(s) in the folktale travel to the upper world, taboos broken in the upper world, whether the girl(s) in the story dig a hole in the cloud, and how the girl(s) in the story travel home.

Data for a more in-depth study of the Star Husband Tale can be found at Github link 23. Python and R code for this case study can be found at GitHub links 19 and 21 respectively.

The rows of data matrix, *M*, represent the 10 Woodland tribes and columns represent the archetypes and subarchtypes. If the (*i*, *j*)^(th) entry of *M* is equal to 1 then archetype *j* is present in tribe *i*^′*s* tale.

  
$$\\begin{array}{l} {M = \\left( \\begin{array}{lllllllllllllllll} {Ojibawa1} & 1 & 0 & 0 & 0 & 0 & 1 & 0 & 1 & 1 & 0 & 0 & 0 & 1 & 0 & 0 & 1 \\\\ {Ojibawa2} & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 1 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 1 \\\\ {Ojibawa3} & 1 & 0 & 0 & 0 & 0 & 1 & 0 & 1 & 0 & 1 & 1 & 0 & 1 & 0 & 0 & 1 \\\\ {Ojibawa4} & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 1 \\\\ {Ojibawa5} & 1 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 1 & 1 & 0 & 1 & 1 & 0 & 0 \\\\ {MicMac1} & 1 & 1 & 1 & 0 & 1 & 0 & 1 & 0 & 0 & 1 & 0 & 1 & 1 & 0 & 0 & 1 \\\\ {MicMac2} & 1 & 1 & 1 & 1 & 1 & 0 & 0 & 0 & 0 & 1 & 0 & 1 & 1 & 0 & 0 & 1 \\\\ {MicMac3} & 1 & 1 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ {Passamaquody1} & 1 & 1 & 0 & 1 & 1 & 0 & 1 & 0 & 0 & 1 & 0 & 1 & 1 & 0 & 0 & 1 \\\\ {Passamaquody2} & 1 & 1 & 0 & 1 & 1 & 0 & 0 & 0 & 0 & 1 & 0 & 1 & 1 & 0 & 0 & 1 \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

Using only the two largest principal components of *M*, *σ*[1] = 6.37802 and *σ*[2] = 3.30583 the matrix

  
$$\\begin{array}{l} {\\widetilde{U} = \\left( \\begin{array}{ll} {- 0.24} & {- 0.47} \\\\ {- 0.17} & {- 0.4} \\\\ {- 0.31} & {- 0.49} \\\\ {- 0.13} & {- 0.08} \\\\ {- 0.23} & {- 0.36} \\\\ {- 0.43} & 0.24 \\\\ {- 0.44} & 0.26 \\\\ {- 0.14} & 0.13 \\\\ {- 0.43} & 0.25 \\\\ {- 0.41} & 0.2 \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

If we use the rows of *Ũ* as the coordinates of each of the tales/tribes, we can visualize the tales in ℝ². [Figure 3.13](#chapter3.xhtml#fig3_13) shows a visual representation of the these tales with the tribes labeled.

It is interesting to note that, for the most part, the tales from the five Ojibawa tribes and the tales for the Passamaquody tribes are close to one another in this visualization.

One can also compare the results with the actual physical location of the tribes in [Figure 3.12](#chapter3.xhtml#fig3_12), noting that it would be common for the Passamaquody tribes to share hunting grounds and thus stories with a nearby tribe such as a MicMac tribe.

![Figure 3.12 Location of Woodlands tribes.](images/fig3_12.jpg)

[Figure 3.12](#chapter3.xhtml#b3fig3_12) Location of Woodlands tribes.

![Figure 3.13 Visual representation of Woodland tribes using PCA.](images/fig3_13.jpg)

[Figure 3.13](#chapter3.xhtml#b3fig3_13) Visual representation of Woodland tribes using PCA.

## 3.8 CASE STUDY: Facial Recognition Using PCA and LDA

Law enforcement agents have to deal with the issue of facial recognition on a daily basis. Let's say that you are given a database of criminal pictures and a new photo. Your job is to determine which photo this new photo resembles the most.

In this case study, we will use PCA on the pixel data from each photo to cluster the photos; however, keep in mind that there are many factors that are important in facial recognition with which a human expert may do a better job. These include gender recognition, changes in hair features, and even the position that the photos are taken.

[Figure 3.14](#chapter3.xhtml#fig3_14) shows 10 head-shots of people that are in a line up. In a recent crime, the photo of two suspects was captured; however, the resolution of the photos is very poor. Their photos are numbers 5 and 10 in [Figure 3.14](#chapter3.xhtml#fig3_14).

![Figure 3.14 10 Head-shots for Facial Recognition Study \[14\].](images/fig3_14.jpg)

[Figure 3.14](#chapter3.xhtml#b3fig3_14) 10 Head-shots for Facial Recognition Study \[[14](#refbib.xhtml#refbib14)\].

Your job is to determine which of the people in the head-shots, 1-4 and 6-9, from [Figure 3.14](#chapter3.xhtml#fig3_14) closely resembles the suspects'; photos. If you are able to narrow your search down to subcategories, you could look at a smaller subset of photos to find your suspect.

The nine-byte representation of pixels in the middle of each of the 5 head-shots, 1-4, in [Figure 3.14](#chapter3.xhtml#fig3_14) can be found in the columns of matrix *A*. We will use a small version of the image data from the center of each photo for this case study, which can be found at GitHub link 24.

  
$$\\begin{array}{l} {A = \\left( \\begin{array}{lllll} 97 & 125 & 106 & 172 & 238 \\\\ 96 & 93 & 100 & 185 & 239 \\\\ 81 & 72 & 93 & 200 & 240 \\\\ 87 & 70 & 103 & 171 & 235 \\\\ 95 & 54 & 97 & 187 & 236 \\\\ 86 & 55 & 88 & 203 & 237 \\\\ 48 & 58 & 100 & 169 & 232 \\\\ 67 & 47 & 96 & 187 & 233 \\\\ 90 & 51 & 87 & 203 & 234 \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

Using the two largest principal components of *A*^(*T*)*A* to construct *Ũ*, we can visualize a representation of these photos in ℝ², seen in [Figure 3.15](#chapter3.xhtml#fig3_15), with the entries of the eigenvector associated with the largest principal component on the *x*\-axis and those associated with the second largest principal component on the *y*\-axis.

![Figure 3.15 Visualization of photos 1-5 base on PCA.](images/fig3_15.jpg)

[Figure 3.15](#chapter3.xhtml#b3fig3_15) Visualization of photos 1-5 base on PCA.

Unfortunately, if you are unable to narrow the group into subgroups initially, distinctive features may not be as easily detected by PCA, with only nine data pixels per picture. We see that the matrix, *B*, which includes nine data points for each of the 10 head-shots,

  
$$\\begin{array}{l} {B = \\left( \\begin{array}{llllllllll} 97 & 125 & 106 & 172 & 238 & 158 & 216 & 191 & 91 & 193 \\\\ 96 & 93 & 100 & 185 & 239 & 153 & 218 & 218 & 94 & 193 \\\\ 81 & 72 & 93 & 200 & 240 & 147 & 218 & 244 & 98 & 193 \\\\ 87 & 70 & 103 & 171 & 235 & 156 & 215 & 193 & 86 & 193 \\\\ 95 & 54 & 97 & 187 & 236 & 154 & 212 & 225 & 92 & 192 \\\\ 86 & 55 & 88 & 203 & 237 & 151 & 209 & 227 & 98 & 192 \\\\ 48 & 58 & 100 & 169 & 232 & 159 & 207 & 178 & 82 & 192 \\\\ 67 & 47 & 96 & 187 & 233 & 158 & 201 & 203 & 89 & 192 \\\\ 90 & 51 & 87 & 203 & 234 & 156 & 195 & 215 & 97 & 191 \\\\ \\end{array} \\right),} \\\\ \\end{array}$$  

one can see from [Figure 3.16](#chapter3.xhtml#fig3_16) that the #5 suspect no longer is closest in resemblance to Figures 1-4 in the lineup. However, if there were over 10000 pixels per suspect, as seen in [Figure 3.17](#chapter3.xhtml#fig3_17), more distinction between groups is recognized with PCA. This data can be found at GitHub link 25.

![Figure 3.16 PCA with only 9 pixels per suspect with data.](images/fig3_16.jpg)

[Figure 3.16](#chapter3.xhtml#b3fig3_16) PCA with only 9 pixels per suspect with data.

![Figure 3.17 PCA with over 10000 pixels per suspect.](images/fig3_17.jpg)

[Figure 3.17](#chapter3.xhtml#b3fig3_17) PCA with over 10000 pixels per suspect.

In this analysis, using PCA, you may not be able to make an assumption about which subgroup, 1-4 or 6-8, the two suspects belong to, nor can an assumption be made that there were two distinct subgroups, classes, among the dataset. However, if there is an understanding about how the 10 photos can be placed into two classes, a better way to analyze the photos may be with LDA.

When applying LDA, we begin by assuming that the first five columns of *B* fit into one class, *C*[1], and the last five into a second class, *C*[2]. With the larger data set, PCA is applied to both classes in order to project the classes into ℝ².

$S\_{w} = \\begin{pmatrix} 2 & 0 \\\\ 0 & 2 \\\\ \\end{pmatrix}$ and the mean vectors are

  
$$\\begin{array}{l} {{\\widetilde{\\mu}}\_{C\_{1}} = \\left( \\begin{array}{ll} {- 0.404322} & {- 0.433172} \\\\ {- 0.423223} & {- 0.419999} \\\\ {- 0.468211} & {- 0.0258423} \\\\ {- 0.423255} & 0.795089 \\\\ {- 0.508958} & 0.0559352 \\\\ \\end{array} \\right)\\text{~and~}{\\widetilde{\\mu}}\_{C\_{2}} = \\left( \\begin{array}{ll} {- 0.393657} & 0.00717916 \\\\ {- 0.494921} & {- 0.587535} \\\\ {- 0.433602} & {- 0.161582} \\\\ {- 0.437483} & 0.792504 \\\\ {- 0.469771} & 0.0240795 \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

Projecting onto the vector *v* = {0.0001464,−0.01026} produces [Figure 3.18](#chapter3.xhtml#fig3_18).

![Figure 3.18 Projecting classes onto v.](images/fig3_18.jpg)

[Figure 3.18](#chapter3.xhtml#b3fig3_18) Projecting classes onto *v*.

Notice that the two classes are not completely well defined, separated, with this projection; however, there are some clear distinctions between the classes.

Similar ideas can be applied to handwriting samples and other image recognition problems.

Python and R code related to this Case Study can be found at GitHub links 20 and 22 respectively.

## 3.9 Exercises

*   Define the transformation *T*[*A*]:ℝ²→ℝ² with standard matrix
    
      
    $$\\begin{array}{l} {A = \\left( \\begin{array}{ll} 1 & 3 \\\\ 2 & 4 \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  
    
    1.  Graph the standard basis vectors, *v*[1] = {1,0} and *v*[2] = {0,1}, transformed under *T*[*A*] and determine if the resulting vectors orthogonal.
        
    2.  Find an angle of rotation, *θ*, such *u*[1] and *u*[2] are orthogonal, where
        
          
        $$\\begin{array}{ll} u\_{1} & {= T\_{A}\\left( \\begin{array}{ll} {\\cos(\\theta)} & {- \\sin(\\theta)} \\\\ {\\sin(\\theta)} & {\\cos(\\theta)} \\\\ \\end{array} \\right)v\_{1},} \\\\ u\_{2} & {= T\_{A}\\left( \\begin{array}{ll} {\\cos(\\theta)} & {- \\sin(\\theta)} \\\\ {\\sin(\\theta)} & {\\cos(\\theta)} \\\\ \\end{array} \\right)v\_{2}.} \\\\ \\end{array}$$  
        
    3.  Use *u*[1] and *u*[2] to find the singular values of *A*.
        
    4.  Use *A**A*^(*T*) to find the singular values of *A*.
        
*   Find the singular values of
    
      
    $$\\begin{array}{l} {\\left( \\begin{array}{lll} 4 & 0 & 3 \\\\ 0 & 2 & 0 \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  
    
*   Find the singular values and eigenvalues of
    
      
    $$\\begin{array}{l} {\\left( \\begin{array}{lll} 1 & 2 & 3 \\\\ 2 & {- 1} & 0 \\\\ 3 & 0 & 4 \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  
    
*   Prove that if *A* is a square matrix then the eigenvalues of *A* are equal to the singular values of *A*.
    
*   Carl just got a new dog and is curious about its genetic makeup and the genetic relationship between many pure bred dogs. Matrix *A* shows a small portion of the genetic makeup (specifically haplotypes) of Carl's new dog and that of several pure bred dogs. The haplotype names in order of column (if you are interested are) A2, A11, A16, A17, A18, A19, B1A.
    
      
    $$\\begin{array}{l} {A = \\left( \\begin{array}{lllllll} 0 & 1 & 0 & 0 & 1 & 1 & 1 \\\\ 0 & 1 & 0 & 0 & 1 & 0 & 0 \\\\ 0 & 0 & 0 & 1 & 0 & 1 & 1 \\\\ 1 & 1 & 0 & 0 & 0 & 0 & 1 \\\\ 0 & 1 & 1 & 1 & 0 & 1 & 1 \\\\ 0 & 0 & 0 & 1 & 1 & 1 & 1 \\\\ \\end{array} \\right)\\begin{array}{l} {\\text{Car}l^{\\prime}\\text{sDog}} \\\\ \\text{Breed~1} \\\\ \\text{Breed~2} \\\\ \\text{Breed~3} \\\\ \\text{Breed~4} \\\\ \\text{Breed~5} \\\\ \\end{array}.} \\\\ \\end{array}$$  
    
    1.  Use PCA, limited to the two largest singular values, to plot a representation of these six dog types. Be sure to label all of the dog types on the graph.
        
    2.  Use your graph from part a. to argue which breed or breed(s) are closest genetically to Carl's dog.
        
*   [Table 3.4](#chapter3.xhtml#tbl3_4) shows Hectares of Palm Oil Plantations in Indonesia versus Sumatran Orangutan populations.
    
    [Table 3.4](#chapter3.xhtml#b3tbl3_4) Orangutan Population versus Palm Oil Plantations.
    
      
    | Year || Total Hectares of Palm Oil Plantations || Sumatran Orangutan Population in Indonesia || Population of Indonesia |
    | --- | --- | --- | --- |
    | 2000 || 4,158,077 || 13,500 || 211,513,823 |
    | --- | --- | --- | --- |
    | 2001 || 4,713,431 || 11,245 || 214,427,417 |
    | 2002 || 5,067,058 || 10,254 || 217,357,793 |
    | 2003 || 5,283,557 || 8,700 || 220,309,469 |
    | 2004 || 5,566,635 || 7,500 || 223,285,676 |
    | 2005 || 5,950,349 || 7,200 || 226,289,470 |
    | 2006 || 6,250,460 || 6,000 || 229,318,262 |
    
    1.  Use PCA to determine a linear model for to predict the orangutan population based on the number of hectares of palm oil plantations.
        
    2.  Use Principal Component Regression to determine a linear model to predict the orangutan population based on both the number of hectares of palm oil plantations and the population of Indonesia.
        
*   Data related to traits of 86 star husband tales can be found at Github link 23. Use Principal Component Analysis to visualize the 86 tales in ℝ² to determine how close the tales are one to one another.
    
*   Data related to 31 Cinderella tales can be found at GitHub link 1. Use Principal Component Analysis to visualize the Cinderella tales in ℝ² and determine how close the tales are to one another.
    
*   A list of 10 East Coast Colleges and Universities and their characteristics are listed in [Table 3.5](#chapter3.xhtml#tbl3_5).
    
    [Table 3.5](#chapter3.xhtml#b3tbl3_5) College and University Data.
    
      
    | Institution || Out of State Tuition || Number of Undergraduates || Acceptance Rate || Graduation Rate |
    | --- | --- | --- | --- | --- |
    | Bucknell University || 56092 || 4900 || .31 || .90 |
    | --- | --- | --- | --- | --- |
    | Davidson College || 51447 || 1843 || .20 || .93 |
    | Florida State University || 18786 || 32812 || .50 || .80 |
    | Georgia Tech University || 33020 || 16049 || .23 || .85 |
    | Lafayette College || 53630 || 2642 || .31 || .90 |
    | University of North Carolina || 35170 || 19117 || .24 || .90 |
    | University of Richmond || 52610 || 3227 || .33 || .88 |
    | University of Virginia || 49032 || 11786 || .27 || .93 |
    | Villanova University || 56730 || 10983 || .29 || .91 |
    | William and Mary University || 45272 || 6377 || .34 || .90 |
    
    1.  Standardize the data and use PCA to project each college and university into ℝ². Which school appears to be the closest to University of Virginia based on this graph?
        
    2.  Project the points from part a. onto the *x*\-axis, using this graph, which school appears to be the closest to University of Virginia.
        
    3.  Project the points from part a. onto the line $y = \\frac{1}{4}x - \\frac{1}{2}$, using this graph, which school appears to be the closest to University of Virginia. Recall that given two vectors *u* and *v*, the projection of *v* onto *u*
        
          
        $$\\begin{array}{r} {proj\_{u}v = \\frac{u \\cdot v}{v \\cdot v}u.} \\\\ \\end{array}$$  
        
    4.  If data scientists believe that the colleges represented in [Table 3.5](#chapter3.xhtml#tbl3_5) should be split into two groups, those with an undergraduate population below 10,000 and those below, determine *S*[*B*] and *S*[*W*].
        
    5.  Use your results from part d. and Linear Discriminant Analysis to determine the best vector to project the data onto in order to represent this grouping.
        
*   S & P 500 stock market data from February 2013 through February 2018 can be found at Github link 48.
    
      
    $$\\begin{array}{l} {Cov = \\left( \\begin{array}{lllllll} & \\text{AAL} & \\text{ABBV} & \\text{CBG} & \\text{DAL} & \\text{EQR} & \\text{UAL} \\\\ \\text{AAL} & 1. & 0.301441 & 0.458315 & 0.96228 & {- 0.297844} & 0.91458 \\\\ \\text{ABBV} & 0.301441 & 1. & 0.831858 & 0.307424 & {- 0.919188} & 0.262801 \\\\ \\text{CBG} & 0.458315 & 0.831858 & 1. & 0.377223 & {- 0.673998} & 0.351462 \\\\ \\text{DAL} & 0.96228 & 0.307424 & 0.377223 & 1. & {- 0.296989} & 0.900406 \\\\ \\text{EQR} & {- 0.297844} & {- 0.919188} & {- 0.673998} & {- 0.296989} & 1. & {- 0.400563} \\\\ \\text{UAL} & 0.91458 & 0.262801 & 0.351462 & 0.900406 & {- 0.400563} & 1. \\\\ \\end{array} \\right)} \\\\ \\end{array}$$  
    
    *Cov* is the covariance matrix for standardized data for six stocks over this period of time. Discuss how you can use the techniques from this chapter to visualize relationships between these stocks.
    

# 4Interpolation

DOI: [10.1201/9781003025672-4](https://doi.org/10.1201/9781003025672-4)

In [Chapter 3](#chapter3.xhtml), we took a look at one type of regression, using Linear Discriminant Analysis. In [Chapters 4](#chapter4.xhtml) and [5](#chapter5.xhtml), we will focus on mathematical learning techniques for creating regression models that optimize a given cost function.

In this chapter, we will assume that there is an unknown function, *f*(*x*), and that you have been provided the values of this function at *n* + 1 distinct points. These points, *x*[0] < *x*[1] < ⋯ < *x*[*n*], called the **interpolation points** can be equidistant or not.

Throughout the chapter, we will refer to the **interpolant** or the **interpolating function**, *f̂*(*x*), as the function chosen to model the given interpolation points.

There are several thoughts around what makes an ideal interpolating function. Ideally, given a large set of interpolation points, some of the interpolation points are chosen at random to serve as the **training set** of data used to develop the model, while the rest of the data is used as a **testing set** to test the accuracy of the model.

Many interpolants serve only to predict the value at the given interpolation points. The goal of this type of interpolation problem is to find a function, *f̂*(*x*), such that

  
$$\\begin{array}{r} {\\hat{f}(x\_{j}) = f(x\_{j})\\text{~for~all~}0 \\leq j \\leq n.} \\\\ \\end{array}$$  

Although very accurate at the given points, these models, such as the Lagrange interpolation functions, and the Hermitian interpolation functions lack flexibility when attempting to extrapolate or predict near the given points but not within the given set.

For more flexibility, learning systems integrate **regularization**, a technique for smoothing across the data. The neural network methods presented in [Chapter 5](#chapter5.xhtml) incorporate optimization techniques called gradient descent with regularization.

Keep in mind that there is not one solution for a best model. Throughout this chapter, we will be discussing advantages and disadvantages of each model. It is important that you analyze your model in context and determine the best model for the situation.

## 4.1 Lagrange Interpolation

A Lagrange interpolant, *P*(*x*), is an *n*^(*t**h*) degree polynomial passing through *n* + 1 known interpolation points, (*x*[0], *f*(*x*[0])), (*x*[1], *f*(*x*[1])), …, (*x*[*n*], *f*(*x*[*n*])) where *x*[0] < *x*[1] < ⋯ < *x*[*n*], with the additional constraint that

  
$$\\begin{array}{r} {P(x) = {\\sum\\limits\_{j = 0}^{n}P\_{j}}(x),} \\\\ \\end{array}$$  

where,

  
$$\\begin{array}{r} {P\_{j}(x) = {\\prod\\limits\_{k = 0,k \\neq j}^{n}f}(x\_{j})\\frac{x - x\_{k}}{x\_{j} - x\_{k}}.} \\\\ \\end{array}$$  

One can also think of the Lagrange interpolant in terms of Vandermonde determinants.

The **Vandermonde matrix**, *V*, is a square matrix of the form

  
$$\\begin{array}{l} {V = \\left( \\begin{array}{lllll} 1 & x\_{0} & x\_{0}^{2} & \\ldots & x\_{0}^{n} \\\\ 1 & x\_{1} & x\_{1}^{2} & \\ldots & x\_{1}^{n} \\\\ 1 & x\_{2} & x\_{2}^{2} & \\ldots & x\_{2}^{n} \\\\ \\vdots & \\vdots & \\vdots & \\vdots & \\\\ 1 & x\_{n} & x\_{n}^{2} & \\ldots & {x\_{n}^{n}.} \\\\ \\end{array} \\right)} \\\\ \\end{array}$$  

Notice that given *n* + 1 interpolation points, *x*[0], *x*[1], …, *x*[*n*], when creating a *n*^(th) degree Lagrange interpolating polynomial,

  
$$\\begin{array}{r} {P\_{j}(x) = {\\sum\\limits\_{j = 0}^{n}{( - 1)}^{j}}f(x\_{j})\\frac{|V\_{j}|}{|V^{\*}|},} \\\\ \\end{array}$$  

where

  
$$\\begin{array}{l} {V^{\*} = \\left( \\begin{array}{lllll} 1 & x\_{0} & x\_{0}^{2} & \\ldots & x\_{0}^{n} \\\\ 1 & x\_{1} & x\_{1}^{2} & \\ldots & x\_{1}^{n} \\\\ 1 & x\_{2} & x\_{2}^{2} & \\ldots & x\_{2}^{n} \\\\ \\vdots & \\ddots & \\ddots & \\ddots & \\vdots \\\\ 1 & x\_{n} & x\_{n}^{2} & \\ldots & x\_{n}^{n} \\\\ \\end{array} \\right),} \\\\ \\end{array}$$  

  
$$\\begin{array}{l} {V\_{0} = \\left( \\begin{array}{lllll} 1 & x & x^{2} & \\ldots & x^{n} \\\\ 1 & x\_{1} & x\_{1}^{2} & \\ldots & x\_{1}^{n} \\\\ 1 & x\_{2} & x\_{2}^{2} & \\ldots & x^{n} \\\\ \\vdots & \\ddots & \\ddots & \\ddots & \\vdots \\\\ 1 & x\_{n} & x\_{n}^{2} & \\ldots & x\_{n}^{n} \\\\ \\end{array} \\right),} \\\\ \\end{array}$$  

  
$$\\begin{array}{l} {V\_{1} = \\left( \\begin{array}{lllll} 1 & x & x^{2} & \\ldots & x^{n} \\\\ 1 & x\_{0} & x\_{0}^{2} & \\ldots & x\_{0}^{n} \\\\ 1 & x\_{2} & x\_{2}^{2} & \\ldots & x\_{2}^{n} \\\\ \\vdots & \\ddots & \\ddots & \\ddots & \\vdots \\\\ 1 & x\_{n} & x\_{n}^{2} & \\ldots & x\_{n}^{n} \\\\ \\end{array} \\right),} \\\\ \\end{array}$$  

and in general

  
$$\\begin{array}{l} {V\_{k} = \\left( \\begin{array}{lllll} 1 & x & x^{2} & \\ldots & x^{n} \\\\ 1 & x\_{0} & x\_{0}^{2} & \\ldots & x\_{0}^{n} \\\\ \\vdots & \\ddots & \\ddots & \\ddots & \\vdots \\\\ 1 & x\_{k - 1} & x\_{k - 1}^{2} & \\ldots & x\_{k - 1}^{n} \\\\ 1 & x\_{k + 1} & x\_{k + 1}^{2} & \\ldots & x\_{k + 1}^{n} \\\\ \\vdots & \\ddots & \\ddots & \\ddots & \\vdots \\\\ 1 & x\_{n} & x\_{n}^{2} & \\ldots & x\_{n}^{n} \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

Notice that in *V*[*k*] the *x*[*k*] is not included in the matrix.

## 4.2 Orthogonal Families of Polynomials

Several of the interpolation techniques presented in this chapter depend on special families of functions. This section focuses on the connection between these special families and linear algebra concepts.

In [Section 3.1](#chapter3.xhtml#sec3_1), we reviewed the concept of an inner product. We see those concepts applied here to families of functions.

There are a variety of families of orthogonal functions that are generated from matrices of special forms.

Square matrices of the form

  
$$\\begin{array}{l} \\left( \\begin{array}{lllllll} x & 1 & 0 & \\ldots & 0 & 0 & 0 \\\\ 1 & {2x} & 1 & 0 & \\ldots & 0 & 0 \\\\ 0 & 1 & {2x} & 1 & 0 & \\ldots & 0 \\\\ \\vdots & \\ddots & \\ddots & \\ddots & \\ddots & \\vdots & \\vdots \\\\ 0 & \\ldots & 0 & 0 & 0 & 1 & {2x} \\\\ \\end{array} \\right) \\\\ \\end{array}$$  

are a special type of **tridiagonal matrix**, whose determinants can be viewed recursively as

  
$$\\begin{array}{r} {T\_{n + 1}(x) = 2xT\_{n} - T\_{n - 1},} \\\\ \\end{array}$$  

*T*[0](*x*) = 1, *T*[1](*x*) = *x*,  and *T*[2](*x*) = 2*x*² − 1.

This family of polynomials is called the **Chebyshev polynomials** of the first kind and is orthogonal when we restrict to the domain to \[ − 1, 1\] with the defined inner product

  
$$\\begin{array}{r} {< f(x),\\, g(x) > = {\\int\_{- 1}^{1}{(1 - x^{2})}^{- 1/2}}f(x)g(x)dx.} \\\\ \\end{array}$$  

The Chebyshev polynomials of the first kind can also be defined by

  
$$T\_{n}(x) = {\\sum\\limits\_{m = 0}^{\\lfloor{n/2}\\rfloor}\\begin{pmatrix} n \\\\ {2m} \\\\ \\end{pmatrix}}x^{n - 2m}{(x^{2} - 1)}^{m}.$$  

Like the Chebyshev polynomials of the first kind, the **Hermite polynomials** are another family of orthogonal functions that can be generated by matrices of a special form. The Hermite polynomials are also an important family of functions that arise in probability theory.

To take a closer look at Hermite polynomials, we look at derivatives of the polynomial

  
$$\\begin{array}{r} {y = a\_{0} + a\_{1}x + \\ldots + a\_{n}x^{n}.} \\\\ \\end{array}$$  

If

  
$$\\begin{array}{l} {A = \\left( \\begin{array}{l} a\_{0} \\\\ a\_{1} \\\\ \\vdots \\\\ a\_{n} \\\\ \\end{array} \\right),} \\\\ \\end{array}$$  

![Figure 4.2 The first 5 Chebyshev polynomials of the first kind on \\lbrack - 1,\\, 1\\rbrack.](images/fig4_2.jpg)

Figure 4.2 The first 5 Chebyshev polynomials of the first kind on \[ − 1, 1\].

then we denote

  
$$\\begin{array}{l} {\\frac{dA}{dx} = \\left( \\begin{array}{l} a\_{1} \\\\ {2a\_{2}} \\\\ \\vdots \\\\ {na\_{n - 1}} \\\\ 0 \\\\ \\end{array} \\right)} \\\\ \\end{array}$$  

and

  
$$\\begin{array}{l} {\\frac{d^{2}A}{dx^{2}} = \\left( \\begin{array}{l} {2a\_{2}} \\\\ {6a\_{3}} \\\\ \\vdots \\\\ {n(n - 1)a\_{n - 2}} \\\\ 0 \\\\ 0 \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

Using these ideas, we introduce the first derivative operator of *A* as,

  
$$\\begin{array}{l} \\left. \\frac{d}{dx}\\rightarrow\\left( \\begin{array}{llllll} 0 & 1 & 0 & 0 & \\ldots & 0 \\\\ 0 & 0 & 2 & 0 & \\ldots & 0 \\\\ \\vdots & \\ddots & \\ddots & \\ddots & \\ddots & \\vdots \\\\ 0 & 0 & 0 & 0 & \\ldots & n \\\\ \\end{array} \\right), \\right. \\\\ \\end{array}$$  

the second derivative operator of *A* as

  
$$\\begin{array}{l} \\left. \\frac{d^{2}}{d^{2}x}\\rightarrow\\left( \\begin{array}{llllll} 0 & 0 & 2 & 0 & \\ldots & 0 \\\\ 0 & 0 & 0 & 6 & \\ldots & 0 \\\\ \\ddots & \\ddots & \\ddots & \\ddots & \\ddots & \\vdots \\\\ 0 & 0 & 0 & 0 & \\ldots & {n(n - 1)} \\\\ 0 & 0 & 0 & 0 & \\ldots & 0 \\\\ 0 & 0 & 0 & 0 & \\ldots & 0 \\\\ \\end{array} \\right), \\right. \\\\ \\end{array}$$  

and the *n* × *n* **Hermite differential operator** as

  
$$\\begin{array}{l} \\left. \\frac{d^{2}}{d^{2}x} - 2x\\frac{d}{dx}\\rightarrow\\left( \\begin{array}{llllll} 0 & 0 & 2 & 0 & \\ldots & 0 \\\\ 0 & {- 2} & 0 & 6 & \\ldots & 0 \\\\ 0 & 0 & {- 4} & 0 & \\ldots & 0 \\\\ \\ldots & \\vdots & \\vdots & \\vdots & \\vdots & \\ldots \\\\ 0 & 0 & 0 & 0 & \\ldots & {n(n - 1)} \\\\ 0 & 0 & 0 & 0 & \\ldots & 0 \\\\ 0 & 0 & 0 & 0 & \\ldots & {- 2n} \\\\ \\end{array} \\right). \\right. \\\\ \\end{array}$$  

If *λ*[0] ≥ *λ*[1] ≥ … ≥ *λ*[*n*] are the eigenvalues of the *n* × *n* differential operator $\\frac{d^{2}}{d^{2}x} - 2x\\frac{d}{dx}$ with corresponding eigenvectors *v*[0], *v*[1], …, *v*[*n*] then the coefficients of the *k*^(th) Hermite polynomial corresponds to the eigenvector *v*[2*k*].

![Figure 4.3 The first 5 Hermite polynomials on \\lbrack - 2,\\, 2\\rbrack.](images/fig4_3.jpg)

Figure 4.3 The first 5 Hermite polynomials on \[ − 2, 2\].

The Hermite polynomials can also be generated using the recursive definition

  
$$\\begin{array}{r} {H\_{n}(x) = xH\_{n - 1}(x) - nH\_{n - 2}(x),} \\\\ \\end{array}$$  

Under the inner product defined by

  
$$\\begin{array}{r} {< f(x),\\, g(x) > = {\\int\_{- \\infty}^{\\infty}e^{- x^{2}}}f(x)g(x)\\, dx,} \\\\ \\end{array}$$  

the Hermite polynomials, like the Chebyshev polynomials of the first kind, are an orthogonal set of functions.

Both the Chebyshev polynomials of the first kind and the Hermite polynomials are popular families of functions used for interpolating, or curve fitting, of data.

## 4.3 Newton's Divided Difference

[Section 4.1](#chapter4.xhtml#sec4_1) presents Lagrange interpolating polynomials which fit exactly to a given set of interpolating points. In fact, given an unknown function *f*(*x*) and *n* + 1 interpolating points, *x*[0] < *x*[1] < … < *x*[*n*], there is a unique polynomial *f̂*(*x*) such that

  
$$\\begin{array}{r} {\\hat{f}(x\_{j}) = f(x\_{j}),\\, 0 < j < n.} \\\\ \\end{array}$$  

In this section, we present several closed forms for the **Newton's interpolating polynomial**, *f̂*(*x*).

Let $\\hat{f\_{1}}(x) = a\_{0}$ and

  
$$\\begin{aligned} {\\hat{f\_{n}}(x)} & {= a\_{0} + a\_{1}(x - x\_{0}) + a\_{2}(x - x\_{0})(x - x\_{1}) + \\ldots + a\_{n}(x - x\_{0})(x - x\_{1})\\cdots} \\\\ & {\\text{\\quad\\quad}(x - x\_{n})} \\\\ & {= a\_{0} + {\\sum\\limits\_{j = 1}^{n}a\_{j}}{\\prod\\limits\_{i = 0}^{j - 1}{(x - x\_{i})}},} \\\\ \\end{aligned}$$  

where

  
$$\\begin{array}{r} {a\_{j} = \\frac{f(x\_{j}) - {\\hat{f}}\_{j - 1}(x\_{j})}{\\prod\\limits\_{i = 0}^{j - 1}{(x\_{j} - x\_{i})}}.} \\\\ \\end{array}$$  

You might have noticed that Newton's interpolating polynomials are defined recursively. That is, that the definition of the *n*^(th) degree polynomial, *f̂*[*n*](*x*), depends on *f̂*[1](*x*), …, *f̂*[*n* − 1](*x*).

We can also write Newton's interpolating polynomials, recursively, in terms of **Newton's divided differences**.

### 4.3.1 Newton's Interpolation via Divided Difference

The first **Newton's divided difference** between *x*[*i*] and *x*[*j*], denoted

  
$$\\begin{array}{r} {f\\lbrack x\_{i},x\_{j}\\rbrack,} \\\\ \\end{array}$$  

is the slope of the tangent line between (*x*[*i*], *f*(*x*[*i*])) and (*x*[*j*], *f*(*x*[*j*])),

  
$$\\begin{array}{r} {f\\lbrack x\_{i},x\_{j}\\rbrack = \\frac{f(x\_{i}) - f(x\_{j})}{x\_{i} - x\_{j}}.} \\\\ \\end{array}$$  

Similarly, *n* + 1 points *x*[0] < *x*[1] < … < *x*[*n*] can be used to find the second divided difference,

  
$$\\begin{array}{r} {f\\lbrack x\_{0},x\_{1},\\ldots,x\_{n}\\rbrack = \\frac{f\\lbrack x\_{0},x\_{1},\\ldots,x\_{n - 1}\\rbrack - f\\lbrack x\_{1},x\_{2},\\ldots,x\_{n}\\rbrack}{x\_{0} - x\_{n}}.} \\\\ \\end{array}$$  

Typically, Newton's divided differences are presented in a table similar to the one seen in [Table 4.1](#chapter4.xhtml#tbl4_1).

[Table 4.1](#chapter4.xhtml#b4tbl4_1) Divided Difference where *Δ**x* = 1.

  
| *f*\[*x*[0]\] = 3 ||  ||  ||  |
| --- | --- | --- | --- |
|  || *f*\[*x*[0], *x*[1]\] =  − 1 ||  ||  |
|  ||  || $f\\lbrack x\_{0},x\_{1},x\_{2}\\rbrack = \\frac{- 3 + 1}{2} = - 1$ ||  |
| *f*\[*x*[1]\] = 2 ||  ||  ||  |
|  || *f*\[*x*[1], *x*[2]\] =  − 3 ||  || $f\\lbrack x\_{0},x\_{1},x\_{2},x\_{3}\\rbrack = \\frac{4.5 + 1}{3}$ |
| *f*\[*x*[2]\] =  − 1 ||  ||  ||  |
|  ||  || $f\\lbrack x\_{1},x\_{2},x\_{3}\\rbrack = \\frac{6 + 3}{2} = 4.5$ ||  |
|  || *f*\[*x*[3], *x*[2]\] = 6 ||  ||  |
| *f*\[*x*[3]\] = 5 ||  ||  ||  |

Applying the concepts of divided difference, Newton's interpolating polynomials can be written as

  
$$\\begin{aligned} {\\hat{f\_{1}}(x)} & {= a\_{0} + a\_{1}(x - x\_{0}) = f(x\_{0}) + (x - x\_{0})f\\lbrack x\_{0},x\_{1}\\rbrack} \\\\ {\\hat{f\_{2}}(x)} & {= a\_{0} + (x - x\_{0})f\\lbrack x\_{0},x\_{1}\\rbrack + (x - x\_{0})(x - x\_{1})f\\lbrack x\_{0},x\_{1},x\_{2}\\rbrack} \\\\ {\\hat{f\_{3}}(x)} & {= a\_{0} + (x - x\_{0})f\\lbrack x\_{0},x\_{1}\\rbrack + (x - x\_{0})(x - x\_{1})f\\lbrack x\_{0},x\_{1},x\_{2}\\rbrack} \\\\ & {+ (x - x\_{0})(x - x\_{1})(x - x\_{2})f\\lbrack x\_{0},x\_{1},x\_{2},x\_{3}\\rbrack} \\\\ \\end{aligned}$$  

![Figure 4.4 Data with \\hat{f\_{1}}(x),\\,\\hat{f\_{2}}(x),\\,\\hat{f\_{3}}(x) from Example 4.5.](images/fig4_4.jpg)

Figure 4.4 Data with $\\hat{f\_{1}}(x),\\,\\hat{f\_{2}}(x),\\,\\hat{f\_{3}}(x)$ from [Example 4.5](#chapter4.xhtml#exam4_5).

Notice that the Newton's interpolating polynomials can be written as a linear system as well.

  
$$\\begin{array}{ll} & \\left( \\begin{array}{l} {\\hat{f\_{0}}(x)} \\\\ {\\hat{f\_{1}}(x)} \\\\ {\\hat{f\_{2}}(x)} \\\\ {\\hat{f\_{3}}(x)} \\\\ \\end{array} \\right) \\\\ & {= \\left( \\begin{array}{llll} 1 & 0 & 0 & 0 \\\\ 1 & {(x - x\_{0})} & 0 & 0 \\\\ 1 & {(x - x\_{0})} & {(x - x\_{0})(x - x\_{1})} & 0 \\\\ 1 & {(x - x\_{0})} & {(x - x\_{0})(x - x\_{1})} & {(x - x\_{0})(x - x\_{1})(x - x\_{2})} \\\\ \\end{array} \\right)} \\\\ & {\\text{\\quad\\quad}\\left( \\begin{array}{l} {f\\lbrack x\_{0}\\rbrack} \\\\ {f\\lbrack x\_{0},x\_{1}\\rbrack} \\\\ {f\\lbrack x\_{0},x\_{1},x\_{2}\\rbrack} \\\\ {f\\lbrack x\_{0},x\_{1},x\_{2},x\_{3}\\rbrack} \\\\ \\end{array} \\right)} \\\\ \\end{array}$$  

### 4.3.2 Newton's Interpolation via the Vandermonde Matrix

We can also write Newton's divided differences in terms of the Vandermonde matrix. In order to do so, we introduce the concept of LU-decomposition so that we can later decompose the Vandermonde matrix in this context.

Let *A* be a square matrix. If *A* can be written in terms of a lower triangular matrix, *L*, with diagonal entries equal to 1, and an upper triangular matrix, *U*, such that

  
$$\\begin{array}{r} {A = LU} \\\\ \\end{array}$$  

then we say that *A* has a **LU-decomposition**.

If a matrix *A* has a LU-decomposition, *L* and *U* can be determined by finding a sequence of matrices *L*[0], *L*[1], …, *L*[*k*], such that

  
$$\\begin{array}{r} {L\_{k} \\cdot \\cdot \\cdot L\_{1}L\_{0}A = U,} \\\\ \\end{array}$$  

where *L*[*i*] is a lower triangular elementary matrix, 0 ≤ *i* ≤ *k*. Then

  
$$\\begin{array}{r} {L = L\_{0}^{- 1}\\ldots L\_{k}^{- 1}.} \\\\ \\end{array}$$  

Note that *V* is a nonsingular matrix as long as *x*[*i*], 0 ≤ *i* ≤ *n* − 1 are unique. We wish to determine coefficients *a* = {*a*[0], *a*[1], …, *a*[*n*]} such that

  
$$\\begin{array}{r} {Va = \\hat{f}.} \\\\ \\end{array}$$  

We can use the *LU* decomposition of the Vandermonde matrix *V* to find the divided differences,

  
$$\\begin{array}{l} {f\\lbrack x\_{0},x\_{1},\\ldots,x\_{i}\\rbrack = U\_{i,i}^{- 1}L^{- 1}\\left( \\begin{array}{l} {f\\lbrack x\_{0}\\rbrack} \\\\ {f\\lbrack x\_{1}\\rbrack} \\\\ \\vdots \\\\ {f\\lbrack x\_{n}\\rbrack} \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

## 4.4 Chebyshev Interpolation

For the interpolating techniques presented in this chapter thus far, we have assumed that interpolating points are given. There are instances where you are able to choose the interpolating points or that equally spaced interpolating points can be transformed onto another set of points.

**Chebyshev interpolation** is a method when *n* interpolating points are located at the **Chebyshev nodes**, the roots of the *n*^(th) degree Chebyshev polynomial of the first kind, *T*[*n*](*x*),

  
$$\\begin{array}{r} {x\_{k} = cos\\left( \\frac{(2k + 1)\\pi}{2n} \\right),k = 0,\\, 1,\\, 2,\\,\\ldots,\\, n - 1.} \\\\ \\end{array}$$  

An *n*^(th)\-degree polynomial, *p*(*x*), interpolating a function *f*(*x*), can be written as the sum of Chebyshev polynomials of the first kind,

  
$$\\begin{array}{r} {p(x) = \\frac{1}{2}c\_{0}T\_{0}(x) + {\\sum\\limits\_{i = 1}^{n}c\_{i}}T\_{i}(x),} \\\\ \\end{array}$$  

where

  
$$\\begin{array}{r} {c\_{i} = \\frac{2}{n}{\\sum\\limits\_{k = 0}^{n}f}(x\_{k})T\_{i}(x\_{k}).} \\\\ \\end{array}$$  

![Figure 4.5 Example of Chebyshev interpolation of f(x) = \\frac{1}{1 + x^{2}}.](images/fig4_5.jpg)

Figure 4.5 Example of Chebyshev interpolation of $f(x) = \\frac{1}{1 + x^{2}}$.

It is important to note that Chebyshev interpolation is traditionally meant to be conducted on the interval \[ − 1, 1\] since the roots of the Chebyshev polynomials are on the unit circle. Thus, if you intended to use Chebyshev interpolation on an interval \[*a*, *b*\] you must first create a linear transformation

  
$$\\begin{array}{r} \\left. \\mathcal{T}:\\lbrack - 1,\\, 1\\rbrack\\rightarrow\\lbrack a,\\, b\\rbrack,\\text{~where~}u( - 1) = a\\text{~and~}u(1) = b. \\right. \\\\ \\end{array}$$  

If *u* = *α**x* + *β* then

  
$$\\begin{array}{r} {a = - \\alpha + \\beta,b = \\alpha + \\beta} \\\\ \\end{array}$$  

and $u = \\frac{b - a}{2}x + \\frac{b + a}{2}$.

![Figure 4.6 Example of Chebyshev interpolation of f(x) = e^{x} on \\lbrack - 1,\\, 3\\rbrack.](images/fig4_6.jpg)

Figure 4.6 Example of Chebyshev interpolation of *f*(*x*) = *e*^(*x*) on \[ − 1, 3\].

It may seem obscure to be able to choose interpolation points at the Chebyshev nodes; however, Chebyshev interpolation is used extensively in numerical analysis, particularly in creating filters, due to it's ability to minimize **Runge's phenomenon**.

Runge's phenomenon occurs with polynomial interpolants of high degree over a set of equally spaced interpolation points. Runge's phenomenon is when the interpolant matches the desired function or data extremely well in the middle of the interpolation interval and begins to oscillate at the edges of the interval. This phenomena should be considered when deciding to increase the degree of your polynomial interpolant. An example of Runge's phenomenon can be seen in [Figure 4.7](#chapter4.xhtml#fig4_7).

![Figure 4.7 Example of Runge's phenomenon with f(x) = \\frac{1}{1 + 25x^{2}} on \\lbrack - 1,\\, 1\\rbrack with 5th and 9th degree interpolants.](images/fig4_7.jpg)

[Figure 4.7](#chapter4.xhtml#b4fig4_7) Example of Runge's phenomenon with $f(x) = \\frac{1}{1 + 25x^{2}}$ on \[ − 1, 1\] with 5^(th) and 9^(th) degree interpolants.

## 4.5 Hermite Interpolation

Thus far we have been focusing on creating an interpolating function based just on interpolating points. **Hermite interpolation** constructs a interpolating function that involves both function and derivative values.

Like Lagrange interpolation, a hermite interpolating function, *h*(*x*), requires that, for an unknown function *f*(*x*), *h*(*x*) matches *f*(*x*) and its first *p* derivatives on a set of *n* + 1 data points.

That is,

  
$$\\begin{aligned} {h(x\_{i})} & {= f(x\_{i}),\\text{~for~}0 \\leq i \\leq n} \\\\ {h^{(k)}(x\_{i})} & {= f^{(k)}(x\_{i}),\\text{~for~}0 \\leq i \\leq n,0 \\leq k \\leq p.} \\\\ \\end{aligned}$$  

By definition *h*(*x*) has (*n* + 1)(*p* + 1) constraints imposed on it and thus we will be seeking a polynomial of (*n* + 1)(*p* + 1) − 1 degree to satisfy all of these requirements.

We begin with an example before making general statements around hermite polynomials.

If we wish to concern ourselves with exploring only those Hermite interpolating functions that satisfy conditions up through the first derivative, *h*(*x*[*i*]) = *f*(*x*[*i*]) and *h*^′(*x*[*i*]) = *f*^′(*x*[*i*]), we can write such Hermite interpolating functions in terms of Newton's divided difference if the known points (*x*[*i*], *f*^′(*x*[*i*])) are treated as interpolating points as well.

## 4.6 Least Squares Regression

This section focuses on determining interpolating polynomials satisfying

  
$$\\begin{array}{r} {{\\hat{f}}\_{n}(x) = {\\sum\\limits\_{i = 0}^{n}a\_{i}}x^{n},\\,\\hat{f}(x\_{j}) = f(x\_{j}),\\, 0 \\leq j \\leq n.} \\\\ \\end{array}$$  

that minimize the sum of squared errors, $SSE = {\\sum\\limits\_{j = 0}^{n}{(\\hat{f}(}}x\_{j}) - f(x\_{j}))^{2}$. The above system can be written as a system of linear equations,

  
$$\\begin{array}{l} {\\left( \\begin{array}{llll} 1 & x\_{0} & \\ldots & x\_{0}^{n} \\\\ 1 & x\_{1} & \\ldots & x\_{1}^{n} \\\\ \\vdots & \\vdots & \\vdots & \\vdots \\\\ 1 & x\_{n} & \\ldots & x\_{n}^{n} \\\\ \\end{array} \\right)\\left( \\begin{array}{l} a\_{0} \\\\ a\_{1} \\\\ \\vdots \\\\ a\_{n} \\\\ \\end{array} \\right) = \\left( \\begin{array}{l} {f(x\_{0})} \\\\ {f(x\_{1})} \\\\ \\vdots \\\\ {f(x\_{n})} \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

In order for this system to have a unique solution, the **Vandermonde determinant**

  
$$\\begin{array}{l} {\\left| \\begin{array}{llll} 1 & x\_{0} & \\ldots & x\_{0}^{n} \\\\ 1 & x\_{1} & \\ldots & x\_{1}^{n} \\\\ \\vdots & \\vdots & \\vdots & \\vdots \\\\ 1 & x\_{n} & \\ldots & x\_{n}^{n} \\\\ \\end{array} \\right| = {\\prod\\limits\_{i > j}{(x\_{i} - x\_{j})}} \\neq 0.} \\\\ \\end{array}$$  

Additionally, one might wish to fit an *m*^(th) degree interpolating polynomial to *n* + 1 given interpolating points, where *m* < *n* + 1.

In this case, the matrix

  
$$\\begin{array}{l} {A = \\left( \\begin{array}{llll} 1 & x\_{0} & \\ldots & x\_{0}^{m} \\\\ 1 & x\_{1} & \\ldots & x\_{1}^{m} \\\\ \\vdots & \\vdots & \\vdots & \\vdots \\\\ 1 & x\_{n} & \\ldots & x\_{n}^{m} \\\\ \\end{array} \\right)} \\\\ \\end{array}$$  

is not square, so is definitely not invertible. Fortunately, the system is still of the form *A**x* = *b*, where

  
$$\\begin{array}{l} {x = \\left( \\begin{array}{l} a\_{0} \\\\ a\_{1} \\\\ \\vdots \\\\ a\_{m} \\\\ \\end{array} \\right)\\text{~and~}b = \\left( \\begin{array}{l} {f\\left( x\_{0} \\right)} \\\\ {f\\left( x\_{1} \\right)} \\\\ \\vdots \\\\ {f\\left( x\_{n} \\right)} \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

Note that *A*^(*T*)*A* is an *m* × *m* matrix and *A*^(*T*)*A**x* = *A*^(*T*)*b*. Thus, we can solve for the coefficient vector

  
$$\\begin{array}{r} {x = {(A^{T}A)}^{- 1}A^{T}b.} \\\\ \\end{array}$$  

So how do we know that this solution for *x* is the solution that minimizes the SSE?

Recall that the entries of *b* are the values on the interpolation function. The residual errors,

  
$$\\begin{array}{r} {\\overset{\\rightarrow}{r} = proj\_{Ax}b.} \\\\ \\end{array}$$  

A visualization of this can be seen in [Figure 4.8](#chapter4.xhtml#fig4_8).

![Figure 4.8 An interpolant and the residuals.](images/fig4_8.jpg)

[Figure 4.8](#chapter4.xhtml#b4fig4_8) An interpolant and the residuals.

Recall from Linear Algebra that if *A**x* = *b*, then *b* is in the range of the linear transformation *Ax*, which also means that *b* is in the columnspace of *A*.

Additionally, $\\overset{\\rightarrow}{r}$ is orthogonal to the columnspace of *A*.

  
$$\\begin{aligned} \\overset{\\rightarrow}{r} & {= b - Ax} \\\\ {A^{T} \\cdot \\overset{\\rightarrow}{r}} & {= A^{T}(b - Ax) = 0.} \\\\ \\end{aligned}$$  

Solving for *x*, we see that

  
$$\\begin{aligned} {A^{T}b - A^{T}Ax} & {= 0,} \\\\ x & {= {(A^{T}A)}^{- 1}A^{T}b.} \\\\ \\end{aligned}$$  

[Example 4.13](#chapter4.xhtml#exam4_13) shows us how to apply the least squares regression technique in a real world example.

![Figure 4.9 Interpolating function for the data in Example 4.13.](images/fig4_9.jpg)

[Figure 4.9](#chapter4.xhtml#b4fig4_9) Interpolating function for the data in [Example 4.13](#chapter4.xhtml#exam4_13).

There are several ways to think about the error of an interpolant, although the goal of least square regression is to minimize the sum of the squared errors **SSE**,

  
$$\\begin{array}{r} {SSE = {(l\_{2}\\text{error})}^{2} = {\\sum\\limits\_{j = o}^{n}{(\\hat{f}(}}x\_{j}) - f(x\_{j}))^{2}.} \\\\ \\end{array}$$  

Additional errors to consider are the **absolute error**, which is equal to

  
$$\\begin{array}{r} {{\\sum\\limits\_{j = o}^{n}|}\\hat{f}(x\_{j}) - f(x\_{j})|,} \\\\ \\end{array}$$  

and the **relative *l*[2] error**, which is

  
$$\\begin{array}{r} {\\frac{\\sum\\limits\_{j = o}^{n}\\sqrt{{(\\hat{f}(x\_{j}) - f(x\_{j}))}^{2}}}{\\sum\\limits\_{j = o}^{n}\\sqrt{f{(x\_{j})}^{2}}}.} \\\\ \\end{array}$$  

[Table 4.4](#chapter4.xhtml#b4tbl4_4) Errors for [Example 4.13](#chapter4.xhtml#exam4_13).

  
|  || 39375.8 + 29806.7*x* + 3922.32*x*² || *e*^(10.96 + 0.32*x*) |
| --- | --- | --- |
| Absolute error || 51867.1 || 92759.8 |
| --- | --- | --- |
| *l*[2] error || 21311.5 || 41785.6 |
| Relative *l*[2] error || 0.0385 || 0.0755 |

## 4.7 CASE STUDY: Chebyshev Polynomials and Cryptography

There are many techniques for sending an encrypted code and decrypting that code. In this case study, we see a few different techniques related to linear algebra and discuss their qualities.

If Special Agents Rahasa and Siri agree to use Hamming encryption, Rahasa would then place her message into a 2 × *n* matrix. Rahasa begins by testing their communications with the message, “This is a test”, which translates to the matrix

  
$$\\begin{array}{l} {M = \\left( \\begin{array}{lllll} 20 & 9 & 1 & 5 & 20 \\\\ 8 & 19 & 20 & 19 & 20 \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

Notice that each letter is assigned its position in the alphabet, and if Rahasa has an odd number of letters in her message, then she just replicates the last letter. Rahasa then creates a 2 × 2 encryption matrix, *A*, which is invertible mod 29.

  
$$\\begin{array}{l} {A = \\left( \\begin{array}{ll} 1 & 2 \\\\ 3 & 4 \\\\ \\end{array} \\right)} \\\\ \\end{array}$$  

  
$$\\begin{array}{l} {A^{- 1}\\, mod\\, 29 \\equiv \\left( \\begin{array}{ll} 27 & 1 \\\\ 16 & 14 \\\\ \\end{array} \\right),} \\\\ \\end{array}$$  

and sends the encryption matrix *A* as well as the encrypted message affiliated with

  
$$\\begin{array}{l} {\\widetilde{M} = A.M\\, mod\\, 29 \\equiv \\left( \\begin{array}{lllll} 7 & 18 & 12 & 14 & 2 \\\\ 5 & 16 & 25 & 4 & 24 \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

*"GERPLYNDBX."*

Given *A* and the encrypted message, Siri can recreate *M̃* and determine *M* ≡ *A*^( − 1)*M̃* *m**o**d* 29 and the original matrix.

Unfortunately, Rahasa's message might be intercepted by a third party, special agent Gizli. In order to prevent this, Rahasa and Siri have decided to use a more secure method of transmitting their message, using **Public Key Cryptography**.

Public Key Cryptography allows users who do not share any secret key to securely communicate over a public channel.

There are several different public key algorithms. In this case study, we explore a public key algorithm based on chaos theory and Chebyshev polynomials.

In addition to being orthogonal polynomials, Chebyshev polynomials have the remarkable property that

  
$$\\begin{array}{r} {T\_{r}(T\_{s}(x)) = T\_{rs}(x) = T\_{s}(T\_{r}(x)),\\text{~for~all~}x.} \\\\ \\end{array}$$  

For any given prime number, *p*, it is still true that

  
$$\\begin{array}{r} {T\_{r}(T\_{s}(x))\\, mod\\, p \\equiv T\_{rs}(x)\\, mod\\, p \\equiv T\_{s}(T\_{r}(x))\\, mod\\, p,\\text{~for~all~}x.} \\\\ \\end{array}$$  

Additionally, for any value *k* and *x* ∈ \[ − 1, 1\],

  
$$\\begin{array}{r} {T\_{k}(x) = cos(k \\cdot arccos(x)).} \\\\ \\end{array}$$  

Rahasa may wish to use this fact or the recursive nature of Chebyshev polynomials to generate values for large Chebyshev polynomial values.

Recall that *T*[*n* + 1] = 2*x**T*[*n*](*x*) − *T*[*n* − 1](*x*), thus

  
$$\\begin{array}{ll} \\left( \\begin{array}{l} T\_{1} \\\\ T\_{2} \\\\ \\end{array} \\right) & {= \\left( \\begin{array}{ll} 0 & 1 \\\\ {- 1} & {2x} \\\\ \\end{array} \\right)\\left( \\begin{array}{l} T\_{0} \\\\ T\_{1} \\\\ \\end{array} \\right)} \\\\ \\left( \\begin{array}{l} T\_{n} \\\\ T\_{n + 1} \\\\ \\end{array} \\right) & {= \\left( \\begin{array}{ll} 0 & 1 \\\\ {- 1} & {2x} \\\\ \\end{array} \\right)\\left( \\begin{array}{l} T\_{n - 1} \\\\ T\_{n} \\\\ \\end{array} \\right)} \\\\ \\end{array}$$  

and more generally,

  
$$\\begin{array}{l} {\\left( \\begin{array}{l} T\_{n} \\\\ T\_{n + 1} \\\\ \\end{array} \\right) = \\left( \\begin{array}{ll} 0 & 1 \\\\ {- 1} & {2x} \\\\ \\end{array} \\right)^{n}\\left( \\begin{array}{l} T\_{0} \\\\ T\_{1} \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

To begin with, Rahasa generates a large prime number *s* and an integer *x* ∈ \[ − 1, 1\]. For this exercise, Rahasa chooses *s* = 2731 and *x* = .065. Rahasa's public key code is

  
$$\\begin{array}{r} {(x,\\, T\_{s}(x)) = (.065,\\, T\_{2731}(.065)) = (.065,\\, - 0.990181).} \\\\ \\end{array}$$  

Siri receives this information and chooses another prime number *r* = 1951 and calculates

  
$$\\begin{array}{r} {T\_{r}(x) = T\_{1951}(.065) = - 0.946032,} \\\\ \\end{array}$$  

which is then in turn shared with Siri. Now both Rahasa and Siri can calculate *T*[*r**s*](*x*),

  
$$\\begin{array}{r} {T\_{rs}(x) = T\_{1951}( - 0.990181) = T\_{2731}( - 0.946032) = 0.950496,} \\\\ \\end{array}$$  

even though Rahasa does not know *r* and Siri does not know *s*.

From here, Siri would like to determine *s* with the knowledge that

  
$$\\begin{array}{r} {T\_{s}(x) = cos(s \\cdot arccos(x)) = - 0.990181\\text{~and~}arccos(x) = 1.50575.} \\\\ \\end{array}$$  

Additionally, Siri knows that

  
$$\\begin{array}{r} {T\_{s}(T\_{r}(x)) = cos(s \\cdot arccos(T\_{r}(x)) = 0.950496\\text{~with~}arccos(T\_{r}(x)) = 2.81156.} \\\\ \\end{array}$$  

Thus the possible values for *s* are

  
$$\\begin{aligned} s & {= \\left\\{ \\frac{\\pm arccos(T\_{s}(x))}{arccos(x)} + \\frac{2\\pi k}{arccos(x)}|\\, k \\in {\\mathbb{Z}} \\right\\}} \\\\ & {\\approx \\left\\{ \\pm 1.99325 + 2\\pi k \\cdot 0.664121|\\, k \\in {\\mathbb{Z}} \\right\\}.} \\\\ \\end{aligned}$$  

And,

  
$$\\begin{aligned} s & {= \\left\\{ \\frac{\\pm arccos(T\_{rs}(x))}{arccos(T\_{r}(x))} + \\frac{2\\pi j}{arccos(T\_{r}(x))}|\\, j \\in {\\mathbb{Z}} \\right\\}} \\\\ & {\\approx \\left\\{ \\pm 0.112382 + 2\\pi j \\cdot 0.355674|\\, j \\in {\\mathbb{Z}} \\right\\}.} \\\\ \\end{aligned}$$  

Then Siri must determine prime numbers *u*[1] and *u*[2] such that

  
$$\\begin{array}{r} {1.99325 + 2\\pi k\_{1} \\cdot 0.664121 = u\_{1}\\text{~and~} - 1.99325 + 2\\pi k\_{2} \\cdot 0.664121 = u\_{2}} \\\\ \\end{array}$$  

  
$$\\begin{array}{r} {0.112381 + 2\\pi j\_{1} \\cdot 0.355675 = u\_{1}\\text{~and~} - 0.112381 + 2\\pi j\_{2} \\cdot 0.355675 = u\_{2}.} \\\\ \\end{array}$$  

With a quick search, Siri knows that there must be integers *k*[1] and *j*[2] such that

  
$$\\begin{array}{r} {1.99325 + 2\\pi k\_{1} \\cdot 0.664121 = - 0.112381 + 2\\pi j\_{2} \\cdot 0.355675\\text{~is~prime},} \\\\ \\end{array}$$  

determining that *k*[1] = 654 and *s* = 2731.

Then if Rahasa sends Siri the entire message,

  
$$\\begin{array}{l} {\\left( \\begin{array}{lllll} 51167940 & 941841 & 9 & 49485 & 51167940 \\\\ 522216 & 39590091 & 51167940 & 39590091 & 51167940 \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

Rahasa could find the Chebyshev polynomial *T*[2731](*x*) or *T*[5](*x*) = *T*[2731    *m**o**d* 5](*x*).

  
$$\\begin{array}{r} {T\_{5}(x) = 16x^{5} - 20x^{3} + 5x} \\\\ \\end{array}$$  

and solve *T*[5](*x*) = *M* for each encrypted number *M* in the message. For example,

  
$$\\begin{array}{r} {16x^{5} - 20x^{3} + 5x = 51167940,\\text{~when~}x \\approx 20.} \\\\ \\end{array}$$  

Python and R code related to this case study can be found at Github links 26 and 29.

## 4.8 CASE STUDY: Racial Disparities in Marijuana Arrests

According to ACLU, blacks are 3.6 more likely to be arrested for Marijuana possession than whites in America despite similar usage rates \[[1](#refbib.xhtml#refbib1)\]. Since the mid 1980s the United States has put in place aggressive law enforcement to tackle the war on drugs. The United States incarcerates more people than any other nation in the world, largely due to drug possession and usage. Unfortunately, this mass incarceration program, lead by misguided and harsh laws have lead to a systemic problem targeting people of color in America.

We begin by creating a Lagrange interpolation function to fit the Black Arrest Rates as a function of time using the data from [Table 4.5](#chapter4.xhtml#tbl4_5). We will assume that year 2010 is year 1.

[Table 4.5](#chapter4.xhtml#b4tbl4_5) Black and White Marijuana Arrest Rates per 100K (2010–2018)\[[1](#refbib.xhtml#refbib1)\].

  
| Year || Marijuana Possession Arrest Rate || Black Arrest Rate || White Arrest Rate |
| --- | --- | --- | --- |
| 2010 || 250.52 || 659.06 || 199.19 |
| --- | --- | --- | --- |
| 2011 || 229.69 || 624.43 || 178.43 |
| 2012 || 217.79 || 601.68 || 168.75 |
| 2013 || 253.51 || 625.68 || 212.55 |
| 2014 || 199.40 || 552.13 || 155.80 |
| 2015 || 174.06 || 459.89 || 138.90 |
| 2016 || 179.99 || 477.64 || 143.42 |
| 2017 || 207.44 || 560.08 || 160.60 |
| 2018 || 203.88 || 567.51 || 156.06 |

Matrices, *V*^(\*), *V*[0], *V*[1], …, and *V*[8] are created.

  
$$\\begin{array}{l} {V^{\*} = \\left( \\begin{array}{lllllllll} 1 & 1 & 1 & 1 & 1 & 1 & 1 & 1 & 1 \\\\ 1 & 2 & 4 & 8 & 16 & 32 & 64 & 128 & 256 \\\\ 1 & 3 & 9 & 27 & 81 & 243 & 729 & 2187 & 6561 \\\\ 1 & 4 & 16 & 64 & 256 & 1024 & 4096 & 16384 & 65536 \\\\ 1 & 5 & 25 & 125 & 625 & 3125 & 15625 & 78125 & 390625 \\\\ 1 & 6 & 36 & 216 & 1296 & 7776 & 46656 & 279936 & 1679616 \\\\ 1 & 7 & 49 & 343 & 2401 & 16807 & 117649 & 823543 & 5764801 \\\\ 1 & 8 & 64 & 512 & 4096 & 32768 & 262144 & 2097152 & 16777216 \\\\ 1 & 9 & 81 & 729 & 6561 & 59049 & 531441 & 4782969 & 43046721 \\\\ \\end{array} \\right)} \\\\ \\end{array}$$  

  
$$\\begin{array}{l} {V\_{0} = \\left( \\begin{array}{lllllllll} 1 & x & x^{2} & x^{3} & x^{4} & x^{5} & x^{6} & x^{7} & x^{8} \\\\ 1 & 2 & 4 & 8 & 16 & 32 & 64 & 128 & 256 \\\\ 1 & 3 & 9 & 27 & 81 & 243 & 729 & 2187 & 6561 \\\\ 1 & 4 & 16 & 64 & 256 & 1024 & 4096 & 16384 & 65536 \\\\ 1 & 5 & 25 & 125 & 625 & 3125 & 15625 & 78125 & 390625 \\\\ 1 & 6 & 36 & 216 & 1296 & 7776 & 46656 & 279936 & 1679616 \\\\ 1 & 7 & 49 & 343 & 2401 & 16807 & 117649 & 823543 & 5764801 \\\\ 1 & 8 & 64 & 512 & 4096 & 32768 & 262144 & 2097152 & 16777216 \\\\ 1 & 9 & 81 & 729 & 6561 & 59049 & 531441 & 4782969 & 43046721 \\\\ \\end{array} \\right)} \\\\ \\end{array}$$  

Recall that *V*[*i*] is created by removing the *i* + 1^(st) row of *V*^(\*) and adding the powers of *x* as the first row.

  
$$\\begin{aligned} {P(x)} & {= {\\sum\\limits\_{j = 0}^{n}{( - 1)}^{j}}y\_{j}\\frac{|V\_{j}|}{|V^{\*}|}} \\\\ & {= - 0.00425025x^{8} + 0.257217x^{7} - 6.03801x^{6} + 72.9773x^{5} - 497.339x^{4}} \\\\ & {+ 1944.47x^{3} - 4213.56x^{2} + 4541.35x - 1183.05.} \\\\ \\end{aligned}$$  

Perhaps we wish to integrate the Lagrange interpolant that we just created into the model, but we want to minimize Runge's phenomenon. Let's create a sixth-degree Chebyshev interpolant to this data using the function *P*(*x*), the Lagrange interpolant, as the function.

We first have to use a linear transformation to map the domain \[1, 9\] to \[ − 1, 1\],

  
$$\\begin{array}{r} {u = 4x + 5.} \\\\ \\end{array}$$  

Recall that

  
$$\\begin{array}{l} {T\_{n}(x) = \\left( \\begin{array}{ll} 0 & 1 \\\\ {- 1} & {2x} \\\\ \\end{array} \\right)^{n}\\left( \\begin{array}{ll} 1 & x \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

The roots of *T*[7](*x*) = 128*x*⁸ − 256*x*⁶ + 160*x*⁴ − 32*x*² + 1 are

  
$$\\begin{aligned} x\_{k} & {= cos\\left( \\frac{(2k + 1)\\pi}{16} \\right),k = 0,\\, 1,\\ldots,\\, 7,} \\\\ u\_{k} & {= \\frac{x\_{k} - 5}{4},\\, k = 0,\\, 1,\\ldots,\\, 7,} \\\\ c\_{0} & {= \\frac{1}{8}{\\sum\\limits\_{i = 0}^{6}P}(u\_{i}) \\cdot T\_{0}(x\_{i}) \\approx 583.06,} \\\\ c\_{k} & {= \\frac{2}{8}{\\sum\\limits\_{i = 0}^{6}P}(u\_{i}) \\cdot T\_{k}(x\_{i}),\\, k = 1,\\, 2,\\ldots,\\, 7.} \\\\ \\end{aligned}$$  

{*c*[1], *c*[2],…,*c*[7]} = {−66.62, 49.51, 25.94, 2.034, −27.85, −18.711, 22.30}.

  
$$\\begin{aligned} {p(x)} & {= {\\sum\\limits\_{i = 0}^{7}c\_{i}}T\_{i}\\left( \\frac{x - 5}{4} \\right)} \\\\ & {= 643.905 - 43.277x + 10.938x^{2} + 8.1211x^{3} - 4.8833x^{4} + 0.7772x^{5}} \\\\ & {\\text{\\quad\\quad} - 0.0383x^{6}} \\\\ \\end{aligned}$$  

![Figure 4.10 Lagrange interpolant, P(x), and Chebyshev interpolant, p(x), fitted to the data from Table 4.5.](images/fig4_10.jpg)

Figure 4.10 Lagrange interpolant, *P*(*x*), and Chebyshev interpolant, *p*(*x*), fitted to the data from [Table 4.5](#chapter4.xhtml#tbl4_5).

What questions would you start to ask in order to determine racial inequity related to marijuana arrests?

[Figure 4.11](#chapter4.xhtml#fig4_11) shows the yearly black arrest rates centered with bands of width 3 standard deviations as well as the yearly white arrest rates centered with bands of width 3 standard deviations relative to that data set. This shows that the two data set are extremely far from one another. One might consider following up this case study with a statistical hypothesis test.

![Figure 4.11 Data \\pm \\, 3\\sigma bands.](images/fig4_11.jpg)

[Figure 4.11](#chapter4.xhtml#b4fig4_11) Data ± 3*σ* bands.

Sample Python and R code for this case study can be found at Github links 27 and 30.

## 4.9 CASE STUDY: Interpolation in Higher Education Data

There are many issues that institutions of higher education face related to diversity, equity, and inclusion. Higher education is a key pathway to social mobility. Unfortunately, racial and ethnic disparities still exist in higher education enrollment and attainment \[[33](#refbib.xhtml#refbib33)\].

In this study, we take a closer look at how success in higher education can be related to tuition and mentorship.

The data found in [Table 4.6](#chapter4.xhtml#tbl4_6) is a subset of data provided by the American Council on Higher Education's Report focusing on Race and Ethnicity in Higher Education \[[18](#refbib.xhtml#refbib18)\].

 [Table 4.6](#chapter4.xhtml#b4tbl4_6) Success Indicators in Higher Education by Race. 

 
|  || *x*[1] || *x*[2] || *x*[3] || y |
| --- | --- | --- | --- | --- |
| Race and || 12^(th) Grade || Percent || Full time || Percent |
| Ethnicity || Math Proficiency || enrolled || faculty || graduating |
| Asian || 37.5 || 57.21 || 9.5 || 30.7 |
| --- | --- | --- | --- | --- |
| Black or African American || 6.83 || 36.33 || 5.7 || 15.3 |
| Hispanic or Latino || 11.25 || 38.32 || 4.8 || 12.2 |
| White || 28.21 || 41.86 || 72.6 || 23.75 |

In this study, we will look at how factors from [Table 4.6](#chapter4.xhtml#tbl4_6) can be used to predict graduation rate and future success.

Let

  
$$\\begin{array}{l} {A = \\left( \\begin{array}{llll} 1 & 37.5 & 57.21 & 9.5 \\\\ 1 & 6.83 & 36.33 & 5.7 \\\\ 1 & 11.25 & 38.32 & 4.8 \\\\ 1 & 28.21 & 41.86 & 72.6 \\\\ \\end{array} \\right)} \\\\ \\end{array}$$  

  
$$\\begin{array}{l} {{(A^{T}A)}^{- 1}A^{T}\\left( \\begin{array}{l} 30.7 \\\\ 15.3 \\\\ 12.16 \\\\ 23.75 \\\\ \\end{array} \\right) = \\left( \\begin{array}{l} {- 131.767} \\\\ {- 2.59432} \\\\ 4.44338 \\\\ 0.588323 \\\\ \\end{array} \\right)} \\\\ \\end{array}$$  

and

  
$$\\begin{aligned} \\hat{gradrate} & {= - 131.767 - 2.59432x\_{1} + 4.44338x\_{2} + 0.588323x\_{3}} \\\\ {SSE} & {= 9.4\\overset{˙}{1}0^{- 23}.} \\\\ \\end{aligned}$$  

Graduation is not always the only measure of success. A measure of success after graduation may take into account debt and the ability to pursue a career that gives a student the ability to pay back the debt from achieving their degree.

 

Table 4.7 Data related to borrowing for college.

 
| *x*[4] || *y*[2] |
| --- | --- |
| Percent borrowing to achieve degree || Ratio of Amount Still Owed to Amount Borrowed |
| 6.6 || 45.6 |
| --- | --- |
| 12 || 105.5 |
| 15 || 69.7 |
| 58.5 || 53.5 |

We wish to create a 3^(rd) degree Hermitian interpolant, *h*(*x*), using the percent borrowed to predict the ratio still owed to the amount borrowed, but we do not know any information about *h*^′(*x*).

One strategy is to estimate derivatives with slopes of secant lines between consecutive points. This strategy does make some assumptions and does a better job when consecutive points are close together. We will also assume that the derivative remains the same for the last two data points.

Table 4.8 Estimated *h*^′(*x*).

  
| *x*[4] || Approximate *h*^′(*x*[4]) |
| --- | --- |
| 6.6 || $\\frac{105.5 - 45.6}{12 - 6.6} = 11.0926$ |
| --- | --- |
| 12 || $\\frac{69.7 - 105.5}{15 - 12} = - 11.9333$ |
| 15 || $\\frac{53.5 - 69.7}{58.5 - 15} = - 0.372414$ |
| 58.5 ||  |

Here we employ the divided difference method.

[Table 4.9](#chapter6.xhtml#b4tbl4_9) Divided difference table.

  
| *z* || *f\[z\]* || *f*\[*z*[*i*], *z*[*i* + 1]\] || *f*\[*z*[*i*], *z*[*i* + 1], *z*[*i* + 2]\] |
| --- | --- | --- | --- |
| *z*[0] = 6.6 || 45.6 ||  ||  |
| --- | --- | --- | --- |
|  ||  || *f*\[*z*[0], *z*[1]\] = 11.0926 ||  |
| *z*[1] = 12 || 105.5 ||  ||  |
|  ||  ||  || $\\begin{matrix} {f\\lbrack z\_{0},z\_{1},z\_{2}\\rbrack\\,} & {= \\,} & \\frac{- 11.9333 - 11.0926}{15 - 6.6} \\\\ \\, & {= \\,} & {- 2.7411817} \\\\ \\end{matrix}$ |
|  ||  || *f*\[*z*[1], *z*[2]\] =  − 11.9333 ||  |
| *z*[2] = 15 || 69.7 ||  ||  |
|  ||  ||  || $\\begin{matrix} {f\\lbrack z\_{1},z\_{2},z\_{3}\\rbrack\\,} & {= \\,} & \\frac{- 0.372414 + 11.9333}{58.5 - 12} \\\\ \\, & {= \\,} & 0.248621 \\\\ \\end{matrix}$ |
|  ||  || *f*\[*z*[2], *z*[3]\] =  − 0.372414 ||  |
| *z*[3] = 58.5 || 53.5 ||  ||  |

  
$$\\begin{array}{r} {f\\lbrack z\_{0},z\_{1},z\_{2},z\_{3}\\rbrack = \\frac{0.248621 + 2.7411817}{58.5 - 6.6}.} \\\\ \\end{array}$$  

Then,

  
$$\\begin{aligned} {h(x)} & {= 45.6 + 11.0926(x - 6.6) - 2.7412(x - 6.6)(x - 12)} \\\\ & {\\text{\\quad\\quad} + 0.0576(x - 6.6)(x - 12)(x - 15)} \\\\ & {= 0.0576x^{3} - 4.67656x^{2} + 82.7112x - 313.143} \\\\ \\end{aligned}$$  

This small data set found in [Table 4.10](#chapter4.xhtml#tbl4_10), was constructed using five east coast schools identified as top institutions awarding degrees to minority students \[[22](#refbib.xhtml#refbib22)\] and seven additional east coast schools chosen at random.

The variables included in [Table 4.10](#chapter4.xhtml#tbl4_10) are in state tuition, total enrollment, minority enrollment, and graduation rates for the white and black (nonhispanic) populations at each of the institutions.

[Table 4.10](#chapter4.xhtml#b4tbl4_10) University and College Diversity Data.

  
|  || College || InState Tuition || Total Enrollment || Total Minority || Graduation Rate for Black Students in 2020 |
| --- | --- | --- | --- | --- | --- |
| 1 || Carnegie Mellon || 69883 || 12587 || 3392 || 80 |
| --- | --- | --- | --- | --- | --- |
| 2 || Clemson || 25802 || 21857 || 2849 || 63.4 |
| 3 || Florida State || 17332 || 41226 || 12238 || 72.5 |
| 4 || James Madison || 22108 || 20855 || 3574 || 74.1 |
| 5 || High Point || 49248 || 4399 || 668 || 74.3 |
| 6 || New England College || 52136 || 2399 || 638 || 19.2 |
| 7 || Old Dominion || 22492 || 24932 || 10059 || 53.14 |
| 8 || Providence College || 65090 || 4533 || 652 || 84.8 |
| 9 || Rutgers || 27680 || 48378 || 21656 || 79.86 |
| 10 || U. of CT || 28604 || 26541 || 6255 || 71.05 |
| 11 || U. of Penn || 71200 || 24806 || 7805 || 94.22 |
| 12 || William and Mary || 35636 || 8437 || 2135 || 88.18 |

We begin by exploring models that use the tuition and percent of enrolled minority students to predict the graduation rate of black students at an institution, using the data from [Table 4.10](#chapter4.xhtml#tbl4_10).

Using a least squares regression model, with *ŷ* = *g**r**a**d**u**a**t**i**o**n* *r**a**t**e*,

  
$$\\begin{aligned} \\hat{y} & {= 0.64419 + 1.997644 \\cdot 10^{- 6}(tuition)} \\\\ & {\\text{\\quad\\quad} - 0.036985(\\%\\, of\\, enrolled\\, minority\\, students).} \\\\ \\end{aligned}$$  

We can also normalize this data and use principal component analysis to see which schools in [Table 4.10](#chapter4.xhtml#tbl4_10) are similar. Python and R code for this case study can be found at Github links 28 and 31.

## 4.10 Exercises

*   [Table 4.11](#chapter4.xhtml#tbl4_11) shows some racial demographics related to Covid-19 deaths, as of February 2021, by state.
    
     [Table 4.11](#chapter4.xhtml#b4tbl4_11) Percent of Covid-19 cases by race. 
    
     
    | State || % of Population || % of Cases that are || % of Population || % of Cases that are |
    | --- | --- | --- | --- | --- |
    |  || that is white || from the white population || that is black || from the black population |
    | CA || .36 || .20 || .05 || .04 |
    | --- | --- | --- | --- | --- |
    | FL || .53 || .40 || .15 || .15 |
    | PA || .80 || .82 || .11 || .14 |
    | TX || .41 || .36 || .12 || .19 |
    | WA || .48 || .68 || .04 || .06 |
    
    1.  Use least squares regression to fit a 4^(th) degree polynomial to the data represented by % of the population that is white versus the % of cases from the white population.
        
    2.  Determine the SSE related to the model in part a.
        
    3.  Relative error can be a better expression of error relate to the size of the data. The relative *l*[2] error is
        
          
        $$\\begin{array}{r} {\\frac{\\sqrt{\\sum{(y - \\hat{y})}^{2}}}{\\sqrt{\\sum y^{2}}}.} \\\\ \\end{array}$$  
        
        Determine the relative *l*[2] error for the model in part a.
        
*   Use [Table 4.11](#chapter4.xhtml#tbl4_11) and Vandermonde determinants to create a 4^(th) degree Lagrange interpolation polynomial that matches the points represented by % of the population that is black versus the % of cases from the black population.
    
*   Given the data in [Table 4.11](#chapter4.xhtml#tbl4_11), and an additional data point {0, 0}, use the Vandermonde determinants to create a 5^(th) degree Lagrange interpolation polynomial that matches the points described in Problem 2.
    
*   Determine the 4^(th)\- and 5^(th)\-Chebyshev polynomials of the first kind and show that they are orthogonal under the inner product defined in this chapter for the set of Chebyshev polynomials.
    
*   The *n*^(th)\-degree Chebyshev polynomial of the second kind is defined as the determinant of *n* × *n* matrix of the form
    
      
    $$\\begin{array}{l} {\\left( \\begin{array}{lllllll} x & 1 & 0 & \\ldots & \\ldots & \\ldots & 0 \\\\ 1 & x & 1 & 0 & \\ldots & \\ldots & 0 \\\\ 0 & 1 & x & 1 & 0 & \\ldots & 0 \\\\ \\vdots & \\ddots & \\ddots & \\ddots & \\vdots & \\vdots & \\vdots \\\\ 0 & 0 & \\ldots & 0 & 1 & x & 1 \\\\ 0 & 0 & \\ldots & \\ldots & 0 & 1 & x \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  
    
    Determine the 3^(rd)\- and 4^(th)\-degree Chebyshev polynomials of the second kind and determine if they are orthogonal under the inner product defined in this chapter for the set of Chebyshev polynomials.
    
*   Show that Hermitian polynomials *H*[2](*x*) and *H*[3](*x*) are orthogonal functions.
    
*   Find the LU-decomposition for
    
      
    $$\\begin{array}{l} {\\left( \\begin{array}{lll} 1 & 1 & 2 \\\\ 1 & 2 & 5 \\\\ 1 & {- 1} & 3 \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  
    
*   [Table 4.3](#chapter4.xhtml#tbl4_3) shows data for the growth of COVID 19 over a period of months,
    
    1.  Create the Vandermonde matrix with the data from [Table 4.3](#chapter4.xhtml#tbl4_3).
        
    2.  Find the LU-decomposition of the Vandermonde matrix in part a.
        
    3.  Find *f*\[*x*[0]\], *f*\[*x*[0], *x*[1]\], *f*\[*x*[0], *x*[1], *x*[2]\], and *f*\[*x*[0], *x*[1], *x*[2], *x*[3]\] using the LU-decomposition from part b.
        
    4.  Use the divided differences from part c. to find a fifth degree Newton's interpolation polynomial to fit the data.
        
*   In addition to the data presented in [Table 4.3](#chapter4.xhtml#tbl4_3), the instantaneous growth rate is given in [Table 4.12](#chapter4.xhtml#tbl4_12). Use this information to construct a Hermite interpolant that matches both the data from [Table 4.3](#chapter4.xhtml#tbl4_3) and [Table 4.12](#chapter4.xhtml#tbl4_12).
    
    [Table 4.12](#chapter4.xhtml#b4tbl4_12) Growth rate of COVID 19 total cases in NC in 2020.
    
      
    | Date || July 1 || Aug. 1 || Sept. 1 || Oct. 1 || Nov. 1 || Dec 1 |
    | --- | --- | --- | --- | --- | --- | --- |
    | Growth rate || .9 || .4 || .25 || .3 || .35 || .5 |
    | --- | --- | --- | --- | --- | --- | --- |
    
*   One in 7 women and 1 in 25 men have been injured by an intimate partner \[[24](#refbib.xhtml#refbib24)\]. According to Evans et al. \[[10](#refbib.xhtml#refbib10)\], with personal mobility limited by COVID-19 stay at home orders, advocates expressed concern about a potential increase in intimate partner violence (IPV); however, call centers experienced up to a 50% decrease in calls in some regions \[[10](#refbib.xhtml#refbib10)\]. In this problem, we investigate the effects of COVID-19 on reported cases of IPV.
    
    1.  Create a least squares third degree polynomial interpolant for the data provided in [Table 4.13](#chapter4.xhtml#tbl4_13).
        
        [Table 4.13](#chapter4.xhtml#b4tbl4_13) Number of national contacts, calls, chats, and emails from concerned parties, in the first half of each year 2017–2020 (National Domestic Violence Hotline \[[23](#refbib.xhtml#refbib23)\]).
        
          
        | Year || 2016 || 2017 || 2018 || 2019 || 2020 |
        | --- | --- | --- | --- | --- | --- |
        | National contacts || 124712 || 106276 || 98954 || 156429 || 152415 |
        | --- | --- | --- | --- | --- | --- |
        
    2.  [Table 4.14](#chapter4.xhtml#tbl4_14) shows the rate of change of calls to the National Domestic Hotline from 2017–2020. Use this information together with the data in [Table 4.14](#chapter4.xhtml#tbl4_14) to create a Hermitian polynomial.
        
        [Table 4.14](#chapter4.xhtml#b4tbl4_14) Rate of change of calls to the National Domestic Hotline from 2017–2020.
        
          
        | Year || 2017 || 2018 || 2019 || 2020 |
        | --- | --- | --- | --- | --- |
        | Percent increase || \-.2 || \-.1 || .6 || \-.1 |
        | --- | --- | --- | --- | --- |
        
    3.  Use your polynomial from part b. to estimate the number of calls to the National Domestic Hotline midway through the year in 2021.
        
    4.  While making an estimate within the domain of the given data is called interpolation, making estimates outside of the domain of the given data is called **extrapolation**. Use the interpolant from part b. to estimate the number of calls in 2022.
        
    5.  Discuss what issues can arise from estimation through extrapolation.
        

# 5Optimization and Learning Techniques for Regression

DOI: [10.1201/9781003025672-5](https://doi.org/10.1201/9781003025672-5)

In this chapter, we look at algorithms that combine topics that we have touched on in previous chapters with machine learning. A common goal of many of these algorithms is the importance of optimizing, either minimizing or maximizing, a chosen function. These ideas require some basic knowledge of probability theory, differentiation, and integration, and thus we start with an overview of these topics.

## 5.1 Basics of Probability Theory

A **probability space** is defined by a sample space, 𝒮, a set of events, ℰ, and a probability measure 𝒫:ℰ→\[0,1\] where 𝒫(𝒮) = 1.

A **random variable**, *X*, is a function on the sample space. A **discrete random variable** is a random variable whose sample space is countable, finite, or infinite. A **continuous random variable** is one in which the sample space is uncountable.

If *X* is a discrete random variable,

  
𝒫(𝒳) = 𝒫(𝒳 = *x*)  

is called a **probability distribution function**.

For a discrete random variable, *X*, the **cumulative distribution function**,

  
$$\\begin{array}{r} {D(x) = P(X \\leq x\_{k}) = {\\sum\\limits\_{i = 1}^{k}P}(X = x\_{i}),} \\\\ \\end{array}$$  

where the sample space *S* = {*x*[1],*x*[2],…,*x*[*k*],…,*x*[*n*]}.

The **expected value**, or mean, of a discrete random variable, *X*,

  
$$\\begin{array}{r} {E(X) = {\\sum\\limits\_{i = 1}^{n}x\_{i}} \\cdot P(X = x\_{i}),} \\\\ \\end{array}$$  

and the variance of a discrete random variable,

  
$$\\begin{array}{r} {Var(X) = E(X^{2}) - {(E(X))}^{2} = {\\sum\\limits\_{i = 1}^{n}x\_{i}^{2}} \\cdot P(X = x\_{i}) - \\left( {{\\sum\\limits\_{i = 1}^{n}x\_{i}} \\cdot P(X = x\_{i})} \\right)^{2}.} \\\\ \\end{array}$$  

![Figure 5.1 Binomial Distribution representing the number of heads in 10 flips of a fair coin.](images/fig5_1.jpg)

[Figure 5.1](#chapter5.xhtml#b5fig5_1) Binomial Distribution representing the number of heads in 10 flips of a fair coin.

In general, if a random variable, *x*, has a binomial probability distribution, denoted *x* ∼ *B**i*(*n*, *p*) then

  
$$\\begin{array}{ll} {\\mathcal{P}(\\mathcal{X} = x)} & {= \\begin{cases} {\\left\\{ \\begin{array}{l} n \\\\ x \\\\ \\end{array} \\right.p^{x}{(1 - p)}^{n - x},} & {\\text{if~}x \\in \\left\\{ 1,\\mspace{6mu} 2,\\ldots,\\mspace{6mu} n \\right\\},} \\\\ {0,} & {\\text{otherwise},} \\\\ \\end{cases}} \\\\ {E(x)} & {= np,} \\\\ {Var(x)} & {= np(1 - p),} \\\\ \\end{array}$$  

where *p* represents the probability of success in the experiment and *n* represents the number of trials of the experiment.

Another discrete probability distribution of interest is the **Poisson Distribution**.

The Poisson distribution is a special type of Binomial Distribution that focuses on the average time between successes.

If the random variable *X* is the number of successes in a given time period and if *λ* is the average time between successes then *X* has a Poisson distribution, *X* ∼ *P**o**i**s*(*λ*), with *E*(*X*) = *λ* and *V**a**r*(*X*) = *λ*,

  
$$\\begin{array}{r} {P(X = x) = \\frac{\\lambda^{x}e^{- \\lambda}}{x!}.} \\\\ \\end{array}$$  

When you compare the shape of the curve in [Figures 5.1](#chapter5.xhtml#fig5_1) and [5.2](#chapter5.xhtml#fig5_2), you might notice that they are very similar.

![Figure 5.2 Poisson Distribution with \\lambda = 10.](images/fig5_2.jpg)

[Figure 5.2](#chapter5.xhtml#b5fig5_2) Poisson Distribution with *λ* = 10.

If in fact we let *λ* = *n**p*,

  
$$\\begin{aligned} {lim\_{n\\rightarrow\\infty}P(X = k)} & {= lim\_{n\\rightarrow\\infty}\\left( \\begin{array}{l} n \\\\ k \\\\ \\end{array} \\right)p^{k}{(1 - p)}^{n - k}} \\\\ & {= lim\_{n\\rightarrow\\infty}\\frac{n!}{(k!)(n - k)!}\\left( \\frac{\\lambda}{n} \\right)^{k}\\left( {1 - \\frac{\\lambda}{n}} \\right)^{n - k}} \\\\ & {= \\left( \\frac{\\lambda}{k!} \\right)^{k}lim\_{n\\rightarrow\\infty}\\frac{n!}{n^{k}(n - k)!}} \\\\ & {= \\left( \\frac{\\lambda}{k!} \\right)^{k}e^{k}} \\\\ \\end{aligned}$$  

We will also be looking at problems that involve **infinite probability spaces** and have continuous probability measures, called **probability density functions**.

If *X* is a continuous random variable with probability density function *P*(*X*) then *P*(*X*) is the derivative of the cumulative distribution function, *D*(*x*), where

  
$$\\begin{array}{r} {D(x) = P(X \\leq x) = {\\int\_{- \\infty}^{x}P}(t)dt.} \\\\ \\end{array}$$  

The expected value of a continuous random variable, *X*,

  
$$\\begin{array}{r} {E(X) = {\\int\_{- \\infty}^{x}t} \\cdot P(t)dt.} \\\\ \\end{array}$$  

It is important to note that for discrete random variable, we focus on the chance of *X* = *x*; however, if the random variable *X* is continuous we do not discuss the event that *X* = *x*, since ∫[*x*]^(*x*)*P*(*t*) *d**t* = 0.

A common continuous probability density functions is the **Gaussian distribution** with mean *μ* and variance *σ*², *N*(*μ*, *σ*²).

If *X* is a random variable and *X* ∼ *N*(*μ*, *σ*²), then

  
$$\\begin{array}{r} {P(X \\leq x) = {\\int\_{- \\infty}^{x}\\frac{1}{\\sqrt{2\\pi\\sigma^{2}}}}e^{\\frac{- {(t - \\mu)}^{2}}{2\\sigma^{2}}}\\, dt.} \\\\ \\end{array}$$  

Another continuous distribution of interest is the **Gamma distribution**. [Figure 5.3](#chapter5.xhtml#fig5_3) shows examples of each of these distributions.

![Figure 5.3 (Left) Gaussian distribution with parameters \\mu = 4,\\,\\sigma^{2} = 1 and (Right) Gamma distribution with parameters \\alpha = 2,\\,\\beta = 1.](images/fig5_3.jpg)

[Figure 5.3](#chapter5.xhtml#b5fig5_3) (Left) Gaussian distribution with parameters *μ* = 4, *σ*² = 1 and (Right) Gamma distribution with parameters *α* = 2, *β* = 1.

Many times we will also be looking at how multiple random variables interact and effect each others'; behavior.

If *X* and *Y* are two discrete random variables, the **joint distribution** of *X* and *Y*, denoted *f*[*X**Y*](*x*, *y*), is

  
$$\\begin{array}{r} {f\_{XY}(x,y) = P(X = x \\cap Y = y).} \\\\ \\end{array}$$  

If *X* and *Y* are continuous random variables, then

  
$$\\begin{array}{r} {f\_{XY}(x,y) = P(X \\leq x \\cap Y \\leq y).} \\\\ \\end{array}$$  

One can also look at **conditional probability distributions** where we explore the probability of a random variable *Y* occurring given that a random variable *X* has occurred.

  
$$\\begin{array}{r} {f\_{Y|X}(y|x) = P(Y = y|X = x) = \\frac{P(Y = y \\cap X = x)}{P(X = x)}} \\\\ \\end{array}$$  

for discrete random variables or for continuous random variables,

  
$$\\begin{array}{r} {f\_{Y|X}(y|x) = P(Y \\leq y|X \\leq x) = \\frac{P(Y \\leq y \\cap X \\leq x)}{P(X \\leq x)}.} \\\\ \\end{array}$$  

Two random variables, *X* and *Y*, are **independent** if

  
$$\\begin{array}{r} {P(X = x \\cap Y = y) = P(X = x)P(Y = y)} \\\\ \\end{array}$$  

and thus *P*(*Y* = *y*|*X* = *x*) = *P*(*Y*|*y*).

A set of random variables is called **independent and identical distributed (i.i.d.)** if each of the random variables in the set has the same probability distribution and they are mutually independent.

In general if *X*[1], *X*[2], …, *X*[*n*] are discrete random variables then the joint probability distribution function

  
$$\\begin{array}{r} {f(X\_{1},\\, X\_{2},\\ldots,\\, X\_{n}) = {\\sum\\limits\_{x\_{1},\\, x\_{2},\\ldots,\\, x\_{n}}P}(X\_{1} = x\_{1}) \\cdot \\, P(X\_{2} = x\_{2})\\cdots P(X\_{n} = x\_{n}),} \\\\ \\end{array}$$  

and if *X*[1], *X*[2], …, *X*[*n*] are continuous random variables then the joint probability distribution function

  
$$\\begin{aligned} & {f(X\_{1},\\, X\_{2},\\ldots,\\, X\_{n})} \\\\ & {\\text{\\quad\\quad} = {\\int\_{x\_{1},\\, x\_{2},\\ldots,\\, x\_{n}}P}(X\_{1} = x\_{1}) \\cdot \\, P(X\_{2} = x\_{2})\\cdots P(X\_{n} = x\_{n})dX\_{1}dX\_{2}\\ldots dX\_{n}.} \\\\ \\end{aligned}$$  

 [Table 5.1](#chapter5.xhtml#b5tbl5_1) Example of a discrete joint probability distribution. 

 
| Y |
| --- |
| X ||  || 0 || 1 || 2 |
| --- | --- | --- | --- | --- |
| 0 || $\\frac{1}{2}$ || 0 || 0 |
| 1 || $\\frac{1}{2}$ || $\\frac{1}{2}$ || 0 |
| 2 || 0 || $\\frac{1}{2}$ || $\\frac{1}{2}$ |
| 3 || 0 || 0 || $\\frac{1}{2}$ |

Now that we have introduced the basics of probability theory, we are ready to introduce you to some matrix calculus. Both probability theory and matrix calculus will be applied in [Chapters 5](#chapter5.xhtml) and [7](#chapter7.xhtml).

## 5.2 Introduction to Matrix Calculus

As we saw in the previous section, there are times in which integration must be employed in order to determine the cumulative distribution function from a probability density function. Additionally, since we are focusing on optimization in this chapter, it is important to understand certain topics related to differentiation with a focus toward how to apply these concept to matrices.

### 5.2.1 Matrix Differentiation

Given a scalar vector, $X = \\begin{pmatrix} x\_{1} \\\\ x\_{2} \\\\ \\vdots \\\\ x\_{n} \\\\ \\end{pmatrix}$ and function vector

  
$$\\begin{array}{l} {Y = \\left( \\begin{array}{l} {f\_{1}\\left( {x\_{1},x\_{2},\\cdots,x\_{n}} \\right)} \\\\ {f\_{2}\\left( {x\_{1},x\_{2},\\cdots,x\_{n}} \\right)} \\\\ \\vdots \\\\ {f\_{m}\\left( {x\_{1},x\_{2},\\cdots,x\_{n}} \\right)} \\\\ \\end{array} \\right),} \\\\ \\end{array}$$  

the derivative of *Y* with respect to a scalar, *x*[*i*], 1 ≤ *i* ≤ *n*, is

  
$$\\begin{array}{r} {\\frac{\\partial Y}{\\partial x\_{i}} = \\left( {\\frac{\\partial f\_{1}}{\\partial x\_{i}},\\frac{\\partial f\_{2}}{\\partial x\_{i}},\\ldots,\\frac{\\partial f\_{m}}{\\partial x\_{i}}} \\right)} \\\\ \\end{array}$$  

and the derivative of *Y* with respect to *X* is a matrix

  
$$\\begin{array}{l} {\\frac{\\partial Y}{\\partial X} = \\left( \\begin{array}{llll} \\frac{\\partial f\_{1}}{\\partial x\_{1}} & \\frac{\\partial f\_{1}}{\\partial x\_{2}} & \\ldots & \\frac{\\partial f\_{1}}{\\partial x\_{n}} \\\\ \\frac{\\partial f\_{2}}{\\partial x\_{1}} & \\frac{\\partial f\_{2}}{\\partial x\_{2}} & \\ldots & \\frac{\\partial f\_{2}}{\\partial x\_{n}} \\\\ \\vdots & \\ddots & \\ddots & \\vdots \\\\ \\frac{\\partial f\_{m}}{\\partial x\_{1}} & \\frac{\\partial f\_{m}}{\\partial x\_{2}} & \\ldots & \\frac{\\partial f\_{m}}{\\partial x\_{n}} \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

Given a transformation *Y* = *Y*(*X*), where *X* and *Y* are of the same dimension, the **Jacobian** is

  
$$\\begin{array}{r} {|J| = \\frac{\\partial Y}{\\partial X}} \\\\ \\end{array}$$  

If instead, *y* = *f*(*X*) is a scalar function of matrix

$X = \\begin{pmatrix} x\_{11} & x\_{12} & \\cdots & x\_{1n} \\\\ x\_{21} & x\_{22} & \\cdots & x\_{2n} \\\\ \\vdots & \\ddots & \\ddots & \\vdots \\\\ x\_{m1} & x\_{m2} & \\cdots & x\_{mn} \\\\ \\end{pmatrix}$, then

  
$$\\begin{array}{ll} {\\nabla y} & {= \\frac{\\partial y}{\\partial X} = \\left( \\begin{array}{llll} \\frac{\\partial y}{\\partial x\_{11}} & \\frac{\\partial y}{\\partial x\_{12}} & \\cdots & \\frac{\\partial y}{\\partial x\_{1n}} \\\\ \\frac{\\partial y}{\\partial x\_{21}} & \\frac{\\partial y}{\\partial x\_{22}} & \\cdots & \\frac{\\partial y}{\\partial x\_{2n}} \\\\ \\vdots & \\ddots & \\ddots & \\vdots \\\\ \\frac{\\partial y}{\\partial x\_{m1}} & \\frac{\\partial y}{\\partial x\_{m2}} & \\cdots & \\frac{\\partial y}{\\partial x\_{mn}} \\\\ \\end{array} \\right)} \\\\ & {= {\\sum\\limits\_{i,j}E}\\frac{\\partial y}{\\partial x\_{ij}},} \\\\ \\end{array}$$  

where *E*[*i*, *j*] = 1 and all other entries are zero and ∇*y* is called the **gradient matrix**.

The **Hessian matrix**, *H*[*y*], is a square matrix of second order partial derivatives.

  
$$\\begin{array}{l} {H\_{y} = \\left( \\begin{array}{llll} \\frac{\\partial^{2}y}{\\partial x\_{11}^{2}} & \\frac{\\partial^{2}y}{\\partial x\_{11}\\partial x\_{12}} & \\cdots & \\frac{\\partial^{2}y}{\\partial x\_{11}\\partial x\_{1n}} \\\\ \\frac{\\partial^{2}y}{\\partial x\_{22}\\partial x\_{21}} & \\frac{\\partial^{2}y}{\\partial x\_{22}^{2}} & \\cdots & \\frac{\\partial^{2}y}{\\partial x\_{22}\\partial x\_{2n}} \\\\ \\vdots & \\ddots & \\ddots & \\vdots \\\\ \\frac{\\partial^{2}y}{\\partial x\_{nn}\\partial x\_{n1}} & \\frac{\\partial^{2}y}{\\partial x\_{nn}\\partial x\_{n2}} & \\cdots & \\frac{\\partial^{2}y}{\\partial x\_{nn}^{2}} \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

If *y* = *f*(*X*) is a scalar function where *X* = (*x*[1], …, *x*[*n*]), we define the **ordinary differential** as

  
$$\\begin{array}{r} {df = {\\sum\\limits\_{i = 1}^{n}\\frac{\\partial f}{\\partial x\_{i}}}dx\_{i}.} \\\\ \\end{array}$$  

Whereas, if *X* = \[*x*[*i*, *j*]\] is an *m* × *n* matrix, then we define the **matrix differential** as

  
$$\\begin{array}{l} {dX = \\left( \\begin{array}{llll} {dx\_{11}} & {dx\_{12}} & \\cdots & {dx\_{1n}} \\\\ {dx\_{21}} & {dx\_{22}} & \\cdots & {dx\_{2n}} \\\\ \\vdots & \\ddots & \\ddots & \\vdots \\\\ {dx\_{m1}} & {dx\_{m2}} & \\cdots & {dx\_{mn}} \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

The matrix differential satisfies the properties of a linear operator,

  
$$\\begin{array}{r} {d(kX) = kdX,\\text{~and~}d(X + Y) = dX + dY,} \\\\ \\end{array}$$  

where *k* is a scalar and additionally satisfies the chain rule

  
$$\\begin{array}{r} {d(XY) = (d(X))Y + Xd(Y),} \\\\ \\end{array}$$  

if *X* and *Y* are product conforming matrices.

### 5.2.2 Matrix Integration

If *A* is a matrix of scalar functions and one wishes to integrate with respect to a scalar variable, *x*, then

  
$$\\begin{array}{r} {{\\int A}\\, dx = {\\int a\_{ij}}dx,} \\\\ \\end{array}$$  

however, if *f*(*x*) is a vector function then there are instances when one might want to perform a transformation *x* = *g*(*y*), then

  
$$\\begin{array}{r} {{\\int f}(x)dx = {\\int f}(g(y)) \\cdot |det(J(y))|dy,} \\\\ \\end{array}$$  

where |*d**e**t*(*J*(*y*))| is the absolute value of determinant of the Jacobian associated with the transformation *g*(*y*).

If *f*(*X*) is a matrix function and we wish to perform a matrix transformation *Y* = *g*(*X*), then

  
$$\\begin{array}{r} {{\\int f}(X)dx = {\\int f}(g^{- 1}(Y))|det(J)|dY.} \\\\ \\end{array}$$  

Another matrix of importance in the integration of matrices is the square **Vandermonde matrix**.

The Vandermonde matrix plays an important role in signal processing and distribution theory. In this chapter, this is applicable as we wish to find probability distributions and expected values for matrices.

For example, we may wish to determine the following integral, which is related to finding the joint probability distribution of normal distributions with mean *μ* and variance *σ*², *X*[*i*] ∼ *N*(*μ*, *σ*²), *i* = 1, 2, …, *n*,

  
$$\\begin{array}{r} {{\\int\_{- \\infty}^{\\infty}\\ldots}{\\int\_{- \\infty}^{\\infty}{\\int\_{- \\infty}^{\\infty}e^{- {(X\_{1} - \\mu)}^{T}\\Sigma^{- 1}(X\_{1} - \\mu)/2}}}\\, dX\_{1}dX\_{2}\\ldots dX\_{n},} \\\\ \\end{array}$$  

where

  
$$\\begin{array}{l} {\\Sigma = \\left( \\begin{array}{lllll} \\sigma\_{1}^{2} & {cov(X\_{1},X\_{2})} & {cov(X\_{1},X\_{3})} & \\ldots & {cov(X\_{1},X\_{n})} \\\\ {cov(X\_{1},X\_{2})} & \\sigma\_{2}^{2} & {cov(X\_{2},X\_{3})} & \\ldots & {cov(X\_{2},X\_{n})} \\\\ \\vdots & \\ddots & \\ddots & \\ddots & \\vdots \\\\ {cov(X\_{1},X\_{n})} & {cov(X\_{2},X\_{n})} & \\ldots & {cov(X\_{n - 1},X\_{n})} & \\sigma\_{n}^{2} \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

We may make the transformation *y*[*i**j*] = *x*[*i*, *j*] − *μ*[*i**j*], then the integral becomes

  
$$\\begin{array}{r} {{\\int\_{- \\infty}^{\\infty}\\ldots}{\\int\_{- \\infty}^{\\infty}{\\int\_{- \\infty}^{\\infty}e^{- {(Y)}^{T}\\Sigma^{- 1}(Y)/2}}}dY,} \\\\ \\end{array}$$  

however, if you make the transformation *Z* = *P*^( − 1)*Y* where *P*^(*T*)*Σ*^( − 1)*P* = *I*, then

  
$$\\begin{array}{r} {|det(J)| = |det(P)| = |\\Sigma|^{1/2}} \\\\ \\end{array}$$  

and the integral then becomes

  
$$\\begin{aligned} & {{\\int\_{- \\infty}^{\\infty}\\ldots}{\\int\_{- \\infty}^{\\infty}{\\int\_{- \\infty}^{\\infty}e^{- {(PZ)}^{T}\\Sigma^{- 1}(PZ)/2}}}|\\Sigma|^{1/2}dZ} \\\\ & {\\text{\\quad\\quad} = {\\int\_{- \\infty}^{\\infty}\\ldots}{\\int\_{- \\infty}^{\\infty}{\\int\_{- \\infty}^{\\infty}e^{- Z^{T}Z/2}}}|\\Sigma|^{1/2}dZ} \\\\ {= {(2\\pi)}^{n^{2}/2}|\\Sigma|^{1/2}.} & \\\\ \\end{aligned}$$  

Using the same transformation,

  
$$\\begin{array}{r} {{(2\\pi)}^{- mn/2}|\\Sigma|^{- 1/2}{\\int\_{\\mathbf{R}^{\\mathbf{mn}}}X}e^{- {(X - \\mu)}^{T}\\Sigma^{- 1}(X - \\mu)/2}dX = \\mu.} \\\\ \\end{array}$$  

## 5.3 Maximum Likelihood Estimation

In [Chapter 4](#chapter4.xhtml), many interpolation techniques are presented including Least Squares Regression. In this section, we take another look at least squares regression through a probabilistic lens.

Unlike many of the techniques presented which look to minimize a loss or cost function, the maximum likelihood technique for regression attempts to determine the interpolant with the maximum probability (or likelihood) of occurring.

We begin by assuming the interpolant is a linear function *ŷ* = *a*[0] + *a*[1]*x*. We wish to determine the likelihood of this function occurring, *L*(*a*[0], *a*[1]),

  
$$\\begin{array}{r} {L(a\_{0},\\, a\_{1}) = {\\prod\\limits\_{i = 1}^{n}p}(y\_{i}|\\, x\_{i},\\, a\_{0},\\, a\_{1}),} \\\\ \\end{array}$$  

where *p*(*y*[*i*]| *x*[*i*], *a*[0], *a*[1]) represents the conditional probability that *Y*[*i*] = *y*[*i*] given that *X*[*i*] = *x*[*i*] and the assumed interpolant *ŷ* = *a*[0] + *a*[1]*x*.

Assume that *Y*[*i*] ∼ *N*(*μ*, *s*²) are identically independent random variables. That is, for each *y*[*i*], where *i* = 1, …, *n*,

  
$$\\begin{array}{r} {p(y\_{i}|\\, x\_{i},\\, a\_{0},\\, a\_{1}) = \\frac{1}{\\sqrt{2\\pi s^{2}}}e^{- \\frac{{(y\_{i} - (a\_{0} + a\_{1}x\_{i}))}^{2}}{2s^{2}}}.} \\\\ \\end{array}$$  

Recall that since *Y*[1], *Y*[2], …, *Y*[*n*] are i.i.d. random variables, their joint probability distribution, which we will call *L*(*a*[0], *a*[1]) is

  
$$\\begin{array}{r} {{\\prod\\limits\_{i = 1}^{n}p}(y\_{i}|\\, x\_{i},\\, a\_{0},\\, a\_{1}).} \\\\ \\end{array}$$  

Before we take the derivative of *L*(*a*[0], *a*[1]), in order to find values for *a*[0] and *a*[1] that maximize *L*(*a*[0], *a*[1]), it is important to note that it is often more convenient to work with the **log-likelihood** function, *L**L*(*a*[0], *a*[1]), because you then end up taking derivatives of sums of functions rather than products of functions.

Recall that extremal values, maximums and minimums, can occur at critical points, where the derivative of a function is equal to 0.

  
$$\\begin{aligned} {LL(a\_{0},\\, a\_{1})} & {= \\log\\left( {{\\prod\\limits\_{i = 1}^{n}p}(y\_{i}|\\, x\_{i},\\, a\_{0},\\, a\_{1})} \\right)} \\\\ & {= {\\sum\\limits\_{i = 1}^{n}\\log}(p(y\_{i}|\\, x\_{i},\\, a\_{0},\\, a\_{1}))} \\\\ & {= {\\sum\\limits\_{i = 1}^{n}\\log}\\left( {\\frac{1}{\\sqrt{2\\pi s^{2}}}e^{- \\frac{{(y\_{i} - (a\_{0} + a\_{1}x\_{i}))}^{2}}{2s^{2}}}} \\right)} \\\\ & {= n\\log\\left( \\frac{1}{\\sqrt{2\\pi s^{2}}} \\right) - \\frac{1}{2s^{2}}{\\sum\\limits\_{i = 1}^{n}{(y\_{i} - (}}a\_{0} + a\_{1}x\_{i}))^{2}} \\\\ & {= - \\frac{n\\log(2\\pi)}{2} - 2n\\log(s) - \\frac{1}{2s^{2}}{\\sum\\limits\_{i = 1}^{n}{(y\_{i} - (}}a\_{0} + a\_{1}x\_{i}))^{2}.} \\\\ \\end{aligned}$$  

Determining values, *a*[0] and *a*[1], that maximize *L**L*(*a*[0], *a*[1]) is equivalent to determining values, *a*[0] and *a*[1], that maximize *L*(*a*[0], *a*[1]) since *l**o**g*(*x*) is an increasing function.

  
$$\\begin{array}{r} {\\frac{\\partial LL(a\_{0},a\_{1})}{\\partial a\_{1}} = - \\frac{1}{s^{2}}{\\sum\\limits\_{i = 1}^{n}x\_{i}}(y\_{i} - (a\_{0} + a\_{1}x\_{i})) = 0} \\\\ \\end{array}$$  

when

  
$$\\begin{aligned} a\_{1} & {= \\frac{{\\sum\\limits\_{i = 1}^{n}x\_{i}}y\_{i}}{\\sum\\limits\_{i = 1}^{n}x\_{i}}} \\\\ & {= \\frac{{\\sum\\limits\_{i = 1}^{n}{(x\_{i} - \\overline{x})}}(y\_{i} - \\overline{y})}{\\sum\\limits\_{i = 1}^{n}{(x\_{i} - \\overline{x})}^{2}}.} \\\\ \\end{aligned}$$  

Similarly,

  
$$\\begin{array}{r} {\\frac{\\partial LL(a\_{0},a\_{1})}{\\partial a\_{0}} = - \\frac{1}{s^{2}}{\\sum\\limits\_{i = 1}^{n}{(y\_{i} - (}}a\_{0} + a\_{1}x\_{i})) = 0} \\\\ \\end{array}$$  

when

  
$$\\begin{array}{r} {a\_{0} = \\frac{1}{n}{\\sum\\limits\_{i = 1}^{n}y\_{i}} - \\frac{a\_{1}}{n}{\\sum\\limits\_{i = 1}^{n}x\_{i}} = \\overline{y} - a\_{1}\\overline{x}.} \\\\ \\end{array}$$  

In matrix form,

  
$$\\begin{array}{l} {\\left( \\begin{array}{l} a\_{0} \\\\ a\_{1} \\\\ \\end{array} \\right) = {(X^{T}X)}^{- 1}X^{T}Y,} \\\\ \\end{array}$$  

where

  
$$\\begin{array}{l} {X = \\left( \\begin{array}{ll} 1 & x\_{1} \\\\ 1 & x\_{2} \\\\ \\vdots & \\vdots \\\\ 1 & x\_{n} \\\\ \\end{array} \\right)\\text{~and~}Y = \\left( \\begin{array}{l} y\_{1} \\\\ y\_{2} \\\\ \\vdots \\\\ y\_{n} \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

A **Poisson regression model**, or log-linear model assumes that the random variables, *Y*[*i*], are independent identically distributed Poisson random variables, *Y*[*i*] ∼ *P**o**i**s**s*(*λ*).

Since *λ* > 0, we can determine *l**o**g*(*λ*). We will assume that

  
$$\\begin{array}{r} {log(\\lambda) = a\_{0} + a\_{1}x.} \\\\ \\end{array}$$  

  
$$\\begin{aligned} {p(y\_{i}|x\_{i},a\_{0},a\_{1})} & {= {\\prod\\limits\_{i = 1}^{n}e^{- \\lambda}}\\frac{\\lambda^{y\_{i}}}{y\_{i}!}} \\\\ {LL(a\_{0},a\_{1})} & {= log\\left( {{\\prod\\limits\_{i = 1}^{n}e^{- \\lambda}}\\frac{\\lambda^{y\_{i}}}{y\_{i}!}} \\right)} \\\\ & {= {\\sum\\limits\_{i = 1}^{n} -}\\lambda + y\_{i} \\cdot log(\\lambda) - log(y\_{i}!)} \\\\ & {= {\\sum\\limits\_{i = 1}^{n} -}e^{(a\_{0} + a\_{1}x\_{i})} + y\_{i} \\cdot (a\_{0} + a\_{1}x\_{i}) - log(y\_{i}!).} \\\\ \\end{aligned}$$  

Taking partial derivatives,

  
$$\\begin{array}{r} {\\frac{\\partial LL(a\_{0},a\_{1})}{\\partial a\_{0}} = {\\sum\\limits\_{i = 1}^{n} -}e^{(a\_{0} + a\_{1}x\_{i})} + y\_{i} = 0.} \\\\ \\end{array}$$  

Similarly,

  
$$\\begin{array}{r} {\\frac{\\partial LL(a\_{0},a\_{1})}{\\partial a\_{1}} = {\\sum\\limits\_{i = 1}^{n} -}x\_{i}e^{(a\_{0} + a\_{1}x\_{i})} + x\_{i}y\_{i}.} \\\\ \\end{array}$$  

In matrix form,

  
$$\\begin{array}{l} {X = \\left( \\begin{array}{ll} 1 & x\_{1} \\\\ 1 & x\_{2} \\\\ \\vdots & \\vdots \\\\ 1 & x\_{n} \\\\ \\end{array} \\right),\\, Y = \\left( \\begin{array}{l} y\_{1} \\\\ y\_{2} \\\\ \\vdots \\\\ \\\\ y\_{n} \\\\ \\end{array} \\right),\\text{~and~}A = \\left( \\begin{array}{l} a\_{0} \\\\ a\_{1} \\\\ \\end{array} \\right),} \\\\ \\end{array}$$  

the gradient

  
$$\\begin{array}{r} {\\nabla LL(A) = X^{T}Y - X^{T}e^{XA}.} \\\\ \\end{array}$$  

There is not an algebraic solution to $\\frac{\\partial LL(a\_{0},a\_{1})}{\\partial a\_{0}} = 0$ and $\\frac{\\partial LL(a\_{0},a\_{1})}{\\partial a\_{1}} = 0$.

The numeric technique called the **Newton Raphson method** can be used to iteratively estimate the best choice for *a*[0] and *a*[1].

The Hessian matrix,

  
$$\\begin{array}{ll} {H\_{LL}(A)} & {= \\left( \\begin{array}{ll} \\frac{\\partial^{2}LL}{\\partial a\_{0}^{2}} & \\frac{\\partial^{2}LL}{\\partial a\_{0}\\partial a\_{1}} \\\\ & \\\\ {\\,\\frac{\\partial^{2}LL}{\\partial a\_{1}\\partial a\_{0}}} & \\frac{\\partial^{2}LL}{\\partial a\_{1}^{2}} \\\\ \\end{array} \\right)} \\\\ & \\\\ & {= \\left( \\begin{array}{ll} {\\sum\\limits\_{i = 1}^{n}e^{(a\_{0} + a\_{1}x\_{i})}} & {{\\sum\\limits\_{i = 1}^{n}x\_{i}}e^{(a\_{0} + a\_{1}x\_{i})}} \\\\ {{\\sum\\limits\_{i = 1}^{n}x\_{i}}e^{(a\_{0} + a\_{1}x\_{i})}} & {{\\sum\\limits\_{i = 1}^{n}x\_{i}^{2}}e^{(a\_{0} + a\_{1}x\_{i})}} \\\\ \\end{array} \\right)} \\\\ & \\\\ & {= X^{T}WX,} \\\\ \\end{array}$$  

where *W* is the diagonal matrix

  
$$\\begin{array}{l} {W = \\left( \\begin{array}{llllll} e^{(a\_{0} + a\_{1}x\_{1})} & 0 & 0 & \\ldots & 0 & \\\\ 0 & e^{(a\_{0} + a\_{1}x\_{2})} & 0 & \\ldots & 0 & \\\\ \\vdots & \\ddots & \\ddots & & \\ddots & \\vdots \\\\ 0 & 0 & 0 & \\ldots & e^{(a\_{0} + a\_{1}x\_{n})} & \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

Using the Hessian matrix, the *i*^(*t**h*) iterative estimate of *A*, *A*^((*i*)), is

  
$$\\begin{array}{r} {A^{(i)} = A^{(i - 1)} - H\_{LL}{(A^{(i - 1)})}^{- 1}\\nabla LL(A^{(i - 1)}).} \\\\ \\end{array}$$  

## 5.4 Gradient Descent Method

In [Section 4.6](#chapter4.xhtml#sec4_6), an interpolation technique, Least Squares Regression, is introduced with a goal to determine an interpolating polynomial satisfying

  
$$\\begin{array}{r} {{\\hat{f}}\_{n}(x) = {\\sum\\limits\_{i = 0}^{n}a\_{i}}x^{n},\\,\\hat{f}(x\_{j}) = f(x\_{j}),\\, 0 \\leq j \\leq n,} \\\\ \\end{array}$$  

that minimizes the sum of the squared error,

  
$$\\begin{array}{r} {SSE = {\\sum\\limits\_{j = 0}^{n}{(\\hat{f}(}}x\_{j}) - f(x\_{j}))^{2}.} \\\\ \\end{array}$$  

![Figure 5.5 A visualization of the sum of squared errors, SSE.](images/fig5_5.jpg)

Figure 5.5 A visualization of the sum of squared errors, SSE.

In this section, an iterative method is presented that attempts to minimize the sum of squared errors, SSE.

In previous sections of this chapter, we explore techniques that require that interpolants match the given data points. The technique presented in this section has more flexibility with the degree of the interpolating polynomials but may not match the data points.

Matching the data points can be an important quality; however, there are other behaviors of the data that are equally important to consider, such as minimizing a given **loss function**, which in this case is the SSE.

In [Figure 5.6](#chapter5.xhtml#fig5_6), a loss function is pictured. The **gradient** (also called the rate of change or first derivative) of the function is the rate at which the function is changing. Notice that at point a, the function is decreasing, thus the gradient is negative.

![Figure 5.6 Visualization of the gradient of a loss function.](images/fig5_6.jpg)

[Figure 5.6](#chapter5.xhtml#b5fig5_6) Visualization of the gradient of a loss function.

**If the function is decreasing then the gradient is negative.**

Similarly, notice that at point c in [Figure 5.6](#chapter5.xhtml#fig5_6), the function is changing in a positive direction. Most importantly, the rate at which the function is changing at a minimum (or maximum), the slope of the dashed line (on [Figure 5.6](#chapter5.xhtml#fig5_6)), is zero.

**If the function is increasing then the gradient is positive.**

**A function reaches an optimum value (either a minimum or maximum) when the gradient is zero.**

Thus, one can determine the values that minimize a function by calculating the **gradient** of the function and finding the values, also called **parameters**, that optimize the loss function.

If **SSE** is the loss function then we denote the gradient of SSE with respect to the coefficient *a*[*i*] as

  
$$\\begin{array}{r} {\\frac{\\partial SSE}{\\partial a\_{i}}.} \\\\ \\end{array}$$  

If $\\hat{y} = \\hat{f(x)} = a\_{0} + a\_{1}x + a\_{2}x^{2} + \\ldots a\_{n}x^{n}$, then

  
$$\\begin{aligned} {SSE} & {= {(y - (a\_{0} + a\_{1}x + a\_{2}x^{2} + \\ldots a\_{n}x^{n}))}^{2}} \\\\ \\frac{\\partial SSE}{\\partial a\_{0}} & {= - 2(y - (a\_{0} + a\_{1}x + a\_{2}x^{2} + \\ldots a\_{n}x^{n})) = - 2(y - \\hat{y})} \\\\ \\frac{\\partial SSE}{\\partial a\_{1}} & {= - 2x(y - (a\_{0} + a\_{1}x + a\_{2}x^{2} + \\ldots a\_{n}x^{n})) = - 2x(y - \\hat{y})} \\\\ & \\vdots \\\\ \\frac{\\partial SSE}{\\partial a\_{2}} & {= - 2x^{n}(y - \\hat{y}).} \\\\ \\end{aligned}$$  

The Gradient Descent Algorithm consists of

1.  Creating a interpolant, *ŷ* = *f̂*(*x*), using *n* interpolating points.
    
    The coefficients, *a*[*i*], 0 ≤ *i* ≤ *n*, that are determined are called the *weights* in this algorithm. Begin by making a good guess for each of the coefficients and choosing a loss function, such as SSE.
    
2.  For each coefficient, *a*[*i*], determine the gradient
    
      
    $$\\begin{array}{r} {\\frac{\\partial SSE}{\\partial a\_{i}} = {\\sum\\limits\_{j = 0}^{n}{(y\_{j} - \\hat{y\_{j}})}}{(x\_{j})}^{i}.} \\\\ \\end{array}$$  
    
3.  Adjust the weights taking into consideration a learning rate, *r*,
    
      
    $$\\begin{array}{r} {\\text{new~}a\_{i} = a\_{i} + r\\frac{\\partial SSE}{\\partial a\_{i}}.} \\\\ \\end{array}$$  
    
4.  Repeat Steps 2-4 to update the coefficients and approach a minimum *SSE*.
    

![Figure 5.8 Example 5.15 data and cubic interpolants for several iterations of gradient descent.](images/fig5_8.jpg)

[Figure 5.8](#chapter5.xhtml#b5fig5_8) Example 5.15 data and cubic interpolants for several iterations of gradient descent.

Gradient Descent methods can be written in terms of matrix system as well. If the interpolation function is an *n*^(th) degree polynomial

  
$$\\begin{array}{r} {\\hat{y} = a\_{0} + a\_{1}x + \\ldots + a\_{n}x^{n},} \\\\ \\end{array}$$  

then the SSE cost function can be written as

  
$$\\begin{array}{r} {SSE = {(XA - Y)}^{T}(XA - Y),\\text{~where~}} \\\\ \\end{array}$$  

  
$$\\begin{array}{l} {X = \\left( \\begin{array}{lllll} 1 & x\_{0} & x\_{0}^{2} & \\ldots & x\_{0}^{n} \\\\ 1 & x\_{1} & x\_{1}^{2} & \\ldots & x\_{1}^{n} \\\\ \\vdots & \\ddots & \\ddots & \\ddots & \\vdots \\\\ 1 & x\_{n} & x\_{n}^{2} & \\ldots & x\_{n}^{n} \\\\ \\end{array} \\right),\\, A = \\left( \\begin{array}{l} a\_{0} \\\\ a\_{1} \\\\ \\vdots \\\\ a\_{n} \\\\ \\end{array} \\right),} \\\\ \\end{array}$$  

  
$$\\begin{array}{l} {and\\, Y = \\left( \\begin{array}{l} y\_{0} \\\\ y\_{1} \\\\ \\vdots \\\\ y\_{n} \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

The gradients are

  
$$\\begin{array}{r} {\\frac{\\partial SSE}{\\partial A} = X^{T}(XA - Y),} \\\\ \\end{array}$$  

and if *r* is the learning rate then

  
$$\\begin{array}{r} {A\_{i}^{(j + 1)} = A\_{i}^{(j)} - r\\frac{\\partial SSE}{\\partial a\_{i}},} \\\\ \\end{array}$$  

where *A*[*i*]^((*j*)) is the *i*^(th) entry of the *j*^(th) iteration of *A*.

  
$$\\begin{array}{l} {\\left( \\begin{array}{l} \\frac{\\partial SSE}{\\partial a\_{0}} \\\\ \\\\ \\frac{\\partial SSE}{\\partial a\_{1}} \\\\ \\\\ \\frac{\\partial SSE}{\\partial a\_{2}} \\\\ \\\\ \\frac{\\partial SSE}{\\partial a\_{3}} \\\\ \\end{array} \\right) = \\left( \\begin{array}{l} 20 \\\\ 56 \\\\ 92 \\\\ 200 \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

Thus if the learning rate *r* = .01,

  
$$\\begin{array}{l} {A^{(1)} = \\left( \\begin{array}{llll} {- 4} & 7 & 7 & {- 4} \\\\ \\end{array} \\right) - .01\\left( \\begin{array}{l} 20 \\\\ 56 \\\\ 92 \\\\ 200 \\\\ \\end{array} \\right) = \\left( \\begin{array}{l} {- 4.2} \\\\ 6.44 \\\\ 6.08 \\\\ {- 6.} \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

As you can tell from [Examples 5.15](#chapter5.xhtml#exam5_15) and [5.16](#chapter5.xhtml#exam5_16), the Gradient Descent method can be computational expensive. That is, that for each iteration of the Gradient Descent method, computations have to be made on each data point.

In traditional gradient descent methods, the gradient (or derivative) of the loss function must be calculated for each interpolating point. This can be computationally hard. For example, in [Example 5.16](#chapter5.xhtml#exam5_16), there are only six data points with four partial derivatives in one iteration. After just four interactions, there are almost 100 calculations. If a dataset contained 10,000 points and one wished to use gradient descent to model the data with a cubic polynomials, each iteration would take 40,000 calculations.

**Stochastic Gradient Descent** is one way to make computational improvements to these methods. When employing Stochastic Gradient Descent, the gradient is calculated, on each iterative step, at a random point or small random set of points called a **mini-batch**.

Additionally, keep in mind that depending on the loss function, the gradient descent method is also not guaranteed to converge, so it is important to think carefully about both the learning rate, *r*, and the loss function that you are using. [Figure 5.9](#chapter5.xhtml#fig5_9) shows both an example in which the method converges and diverges.

![Figure 5.9 Examples of the gradient descent method converging (left) and diverging (right).](images/fig5_9.jpg)

[Figure 5.9](#chapter5.xhtml#b5fig5_9) Examples of the gradient descent method converging (left) and diverging (right).

The gradient descent method is just one method of neural network. In the next section, we explore the concepts of neural networks more broadly.

## 5.5 Introduction to Neural Networks

**Neural networks** are powerful tools in data science that focus on relationships in data. It is interesting to note that neural networks are based on the systems in the brain. In the brain, neurons receive information, or data, from other neurons. This system of neurons is connected by axons, where some neurons are more connected that other neurons to the network.

There are two general types of neural networks, **unsupervised neural networks** that try to predict an output given a set of input data and **supervised neural networks** where both the input data and output data is know. In a supervised neural network, the known output data can be used to determine the accuracy of the neural network.

In an unsupervised neural network, a neuron can be viewed as receiving a set of inputs, {*x*[1], *x*[2],…, *x*[*n*]}, to predict one output, *y*. Each input is associated with a weighted connection between it and the output. We will represent the matrix of weights as *W*. Data also naturally has bias or noise; we represent this bias with the vector *b*.

With just inputs and one output, the neural network, in its simplest form as it is visualized in [Figure 5.10](#chapter5.xhtml#fig5_10), is called a **perceptron**. The perceptron is not a very interesting case of a neural network as we can accomplish the same thing with the techniques provided in previous sections of this chapter, writing *y* = *W**X*, where *X* incorporates the inputs and the constant, bias, term.

![Figure 5.10 Visualization of a perceptron.](images/fig5_10.jpg)

[Figure 5.10](#chapter5.xhtml#b5fig5_10) Visualization of a perceptron.

If *W* = {*w*[1], *w*[2],…, *w*[*n*]} are the weights, then we can think of this as a linear combination of basis vectors, functions. For example, if *h*[1](*x*) = 1 and *h*[2](*x*) = *x*,

  
$$\\begin{array}{r} {\\hat{y} = w\_{1}h\_{1}(x) + w\_{2}h\_{2}(x)} \\\\ \\end{array}$$  

is a linear model. Similarly, if one wished to use a quadratic function as the model, then the basis vectors would be

  
$$\\begin{array}{r} {\\left\\{ 1,\\, x,\\, x^{2} \\right\\}.} \\\\ \\end{array}$$  

The concept of neural networks becomes much more interesting when there is a **hidden layer**, *S*, adding to the complexity between the input and output values.

Like the gradient descent method, we start with a random guess for *W* and adjust the weights iteratively.

In addition, an **activation function**, can be incorporated such that

  
$$\\begin{array}{r} {S = \\phi(WX),\\text{~and~}y = \\overline{W}S,} \\\\ \\end{array}$$  

$\\overline{W}$ is an updated weight matrix found after *S* is determined. There are a variety of activation techniques, which will be discussed in detail in [Sections 5.5.2](#chapter5.xhtml#sec5_5_2) and [5.5.3](#chapter5.xhtml#sec5_5_3).

We begin with a simple example based on a binary decision, and then we will see how this applies to the interpolation problem.

Machine learning works to adjust the weights and threshold in order to minimize errors. In addition, when using neural networks for an interpolation problem, typically a smoothing activation function, *ϕ*(*W**X*), is applied at each step.

### 5.5.1 The Learning Process

The most important aspect of neural networks is the ability to learn. In the context of interpolation, this can be interpreted such that at each step the weights, *w*[*i*], *i* = 1, …*n*, and ${\\overline{w}}\_{j},j = 1,\\ldots m$, are adjusted to minimize the error.

![Figure 5.11 Example of General Neural Network with Activation Function.](images/fig5_11.jpg)

Figure 5.11 Example of General Neural Network with Activation Function.

After applying the activation function, *ϕ*(*S*) = *ϕ*(*W**X*), the Gradient Descent method can be applied to find optimal weights that minimize the SSE or any other cost function.

When an activation function is applied with learning rate, *r*, and the SSE as the cost function,

  
$$\\begin{array}{r} {\\text{new~}w\_{i} = w\_{i} - r\\frac{\\partial SSE}{\\partial w\_{i}}.} \\\\ \\end{array}$$  

### 5.5.2 Sigmoid Activation Functions

There are many different activation functions that you can use for *ϕ*(*x*). The activation function, or transfer function, is the transformation function that creates the output nodes. Thus, the choice of activation function can have a large impact on the performance of the neural network.

Activation functions are typically differentiable. This is because, in a learning process integrating a technique such as gradient descent, occurs after the activation function is applied. We will introduce four possible activation functions here and show you how they perform.

Typical smoothing functions from **regularization** can be used for *ϕ*(*x*). The first activation function of interest is the **SoftMax function**, where

  
$$\\begin{array}{r} {\\phi(x\_{k}) = \\frac{e^{x\_{k}}}{\\sum\\limits\_{i = 1}^{n}e^{x\_{i}}},} \\\\ \\end{array}$$  

and the partial derivative of *ϕ*(*x*[*k*]) with respect to *x*[*k*] is

  
$$\\begin{array}{r} {\\frac{\\partial\\phi(x\_{k})}{\\partial x\_{k}} = \\frac{e^{x\_{k}}{\\sum\\limits\_{i = 1,i \\neq k}^{n}e^{x\_{i}}}}{{({\\sum\\limits\_{i = 1}^{n}e^{x\_{i}}})}^{2}}.} \\\\ \\end{array}$$  

Another common activation function is called the **logistic sigmoid neuron function**.

  
$$\\begin{array}{r} {\\phi(X) = \\frac{1}{1 + e^{- (WX)}}.} \\\\ \\end{array}$$  

The benefit of using the logistic sigmoid neuron function is that all output values will be between 0 and 1, and thus are good predictors related to probability.

[Figure 5.12](#chapter5.xhtml#fig5_12) gives you a general idea of how the sigmoid activation function acts within a neural network, and [Figure 5.13](#chapter5.xhtml#fig5_13) shows an example of a logistic sigmoid neuron function.

![Figure 5.12 Neural network with sigmoid activation function.](images/fig5_12.jpg)

[Figure 5.12](#chapter5.xhtml#b5fig5_12) Neural network with sigmoid activation function.

![Figure 5.13 Logistic function centered at x = 1.](images/fig5_13.jpg)

[Figure 5.13](#chapter5.xhtml#b5fig5_13) Logistic function centered at *x* = 1.

[Figure 5.14](#chapter5.xhtml#fig5_14) shows *S*, *ϕ*(*S*), and the original data. Notice that in Example 5.5.2, weights were imposed on both the original inputs, *X*, and the activation functions, whereas in Example 5.5.2, weights were imposed on only the inputs. Weights on inputs and/or activation functions can be used to best model scenarios.

![Figure 5.14 S,\\,\\phi(S).](images/fig5_14.jpg)

[Figure 5.14](#chapter5.xhtml#b5fig5_14) *S*, *ϕ*(*S*).

Another commonly used activation function is

  
$$\\begin{array}{r} {\\phi(x) = \\tanh(x),} \\\\ \\end{array}$$  

the **hyperbolic tangent** activation function.

![Figure 5.15 \\phi(x) = \\tanh(x) = \\frac{2}{1 + e^{- 2x}} - 1.](images/fig5_15.jpg)

Figure 5.15 $\\phi(x) = \\tanh(x) = \\frac{2}{1 + e^{- 2x}} - 1$.

In this case,

  
$$\\begin{array}{r} {\\phi^{\\prime}(x) = sech^{2}(x).} \\\\ \\end{array}$$  

If *Ŷ* = *ϕ*(*X**W*),

  
$$\\begin{array}{r} {\\frac{\\partial SSE}{\\partial W} = - 2X^{T}sech^{2}(XW){^\\circ}(Y - \\tanh(XW))} \\\\ \\end{array}$$  

If we choose an activation function like *ϕ*(*x*) = *t**a**n**h*(*x*), then we are allowing for output values to be both positive and negative and thus is usually used to distinguish between two classes of data.

![Figure 5.16 Data from Example 5.21 and Tanh(0.298689 + 0.461612x) on \\lbrack - 2,\\, 2\\rbrack.](images/fig5_16.jpg)

[Figure 5.16](#chapter5.xhtml#b5fig5_16) Data from Example 5.21 and *T**a**n**h*(0.298689 + 0.461612*x*) on \[ − 2, 2\].

Finally, one of the most widely used activation functions is the **rectified linear unit** function, **ReLU**. Defined as

  
$$\\begin{array}{l} {\\phi(x) = \\left\\{ \\begin{array}{ll} {0,} & {\\text{~if~}x < 0,} \\\\ {x,} & {\\text{~otherwise}.} \\\\ \\end{array}~ \\right.} \\\\ \\end{array}$$  

Notice that the ReLu activation function is not differentiable at *x* = 0 and

  
$$\\begin{array}{l} {\\phi^{\\prime}(x) = \\left\\{ \\begin{array}{ll} {0,} & {\\text{~if~}x < 0,} \\\\ \\text{undefined,} & {\\text{~if~}x = 0,} \\\\ {1,} & {\\text{~if~}x > 0.} \\\\ \\end{array}~ \\right.} \\\\ \\end{array}$$  

![Figure 5.17 ReLu activation function.](images/fig5_17.jpg)

Figure 5.17 ReLu activation function.

The ReLu activation function is the most commonly used activation function because of it's accuracy while remaining easy to use and train.

Additionally, the ReLu activation function is used to manage the interaction between input, dependent, variables.

For example, if there are two input variables, *x*[1] and *x*[2], an activation function *ϕ* acts on the input variables, *ϕ*(*w*[1]*x*[1] + *w*[2]*x*[2]). Let's assume that *w*[1] = *w*[2] = 1, then

  
$$\\begin{array}{l} {\\phi(w\_{1}x\_{1} + w\_{2}x\_{2}) = \\left\\{ \\begin{array}{ll} {0,} & {x\_{1} < |x\_{2}|} \\\\ {x\_{1} + x\_{2},} & {x\_{1} \\geq |x\_{2}|} \\\\ \\end{array}~ \\right..} \\\\ \\end{array}$$  

Note that if both *x*[1] > |*x*[2]| > 0 then both input variables contribute to the output.

For example, if *x*[1] = 10 and *x*[2] =  − 2 then *ϕ*(*w*[1]*x*[1] + *w*[2]*x*[2]) = 8. However, if either variable is a significantly larger negative number, then neither variable unduly influences the output. If *x*[1] = 10 and *x*[2] =  − 1000 then *ϕ*(*w*[1]*x*[1] + *w*[2]*x*[2]) = 0.

![Figure 5.18 Iterations of ReLu activation in Example 5.22.](images/fig5_18.jpg)

[Figure 5.18](#chapter5.xhtml#b5fig5_18) Iterations of ReLu activation in [Example 5.22](#chapter5.xhtml#exam5_22).

Next, let's see how to apply these ideas to a regression problem involving more than one input variable.

Table 5.3 Energy data \[[40](#refbib.xhtml#refbib40), [41](#refbib.xhtml#refbib41)\].

  
| Country || Normalized kwh of Energy consumed per person(2019) || Normalized % of Energy from Fossil Fuel(2019) || Normalized GDP per capita in USD(2019) |
| --- | --- | --- | --- |
| USA || 1.08354 || 0.525247 || 1.06688 |
| --- | --- | --- | --- |
| Brazil || \-0.826228 || 0.587071 || \-0.97821 |
| China || 0.616389 || \-1.49447 || 0.62683 |
| Sweden || \-0.873701 || 0.382148 || \-0.715505 |

There are a number of variations on the ReLu activation function that use a non-constant function when *x* < 0, these include the Leaky ReLu, the Parameterised ReLu, and the Exponential Linear Unit.

All of the problems using gradient descent methods thus far use *SSE* as the cost function. Although *SSE* is a popular cost function to use, it is important to note that there are other cost functions that can be employed.

Some of these functions are specific to categorical neural networks, such as the **cross-entropy cost function**, which will be used in [Section 5.6](#chapter5.xhtml#sec5_6).

### 5.5.3 Radial Activation Functions

The general form of a radial activation function is

  
$$\\begin{array}{r} {\\phi\\left( \\frac{{(x - c)}^{T}(x - c)}{r^{2}} \\right),} \\\\ \\end{array}$$  

where *c* is a centering parameter and *r* is a scalar radius. Notice that when using radial activation functions, the function *ϕ*(*x*) acts on ||*x* − *c*||.

[Figure 5.20](#chapter5.xhtml#fig5_20) shows some examples of radial activation functions.

![Figure 5.19 Visualization of implementation of radial activation functions.](images/fig5_19.jpg)

Figure 5.19 Visualization of implementation of radial activation functions.

![Figure 5.20 Examples of Radial Activation Functions.](images/fig5_20.jpg)

[Figure 5.20](#chapter5.xhtml#b5fig5_20) Examples of Radial Activation Functions.

One standard smoothing function, or **convolution** function, used in regularization is a Gaussian activation function, or **Gaussian kernel**,

  
$$\\begin{array}{r} {\\phi(x) = e^{(\\frac{- {(x - c\_{j})}^{T}(x - c\_{j})}{\\sigma^{2}})}.} \\\\ \\end{array}$$  

![Figure 5.21 Example of Gaussian kernel with radius 2 centered at 3.](images/fig5_21.jpg)

Figure 5.21 Example of Gaussian kernel with radius 2 centered at 3.

Table 5.4 Estimations of *w*[1] and *w*[2] in the iterative process with *r* = .03.

  
| Iteration || *w*[1] || *w*[2] || SSE || $r \\cdot \\frac{\\partial SSE}{\\partial w\_{1}}$ || $r \\cdot \\frac{\\partial SSE}{\\partial w\_{2}}$ |
| --- | --- | --- | --- | --- | --- |
| 0 || .5 || .5 || 0.074 || 0.0163 || 0.0042 |
| --- | --- | --- | --- | --- | --- |
| 1 || 0.4837 || 0.4958 || 0.0649 || 0.014 || 0.0039 |
| 2 || 0.4697 || 0.4919 || 0.0580 || 0.013 || 0.0037 |
| 3 || 0.4567 || 0.4882 || 0.0524 || 0.011 || 0.0034 |
| 4 || 0.4457 || 0.4848 || 0.0481 || 0.010 || 0.0032 |

![Figure 5.22 Iterations of a radial activation in Example 5.24.](images/fig5_22.jpg)

Figure 5.22 Iterations of a radial activation in [Example 5.24](#chapter5.xhtml#exam5_24).

[Example 5.24](#chapter5.xhtml#exam5_24) shows how to apply a Gaussian radial activation function when the centers and spreads of data are known. In most data situations, the centers are unknown. We will next revisit this data problem from the Case Study in 3.8.

In [Chapter 6](#chapter6.xhtml), we explore other iterative processes that are used for categorical decisions and regression analysis.

## 5.6 CASE STUDY: Handwriting Digit Recognition

The MNIST is a training set for handwritten digit recognition \[[44](#refbib.xhtml#refbib44)\]. This training set consists of 60000 examples in 10 categories, 0–9. In this example, we show a small example but encourage the reader to explore the larger dataset by implementing the R code found at Github link 34 or the Python code at Github link 32.

Assume that you have a handwritten digit such as the one pictured in [Figure 5.24](#chapter5.xhtml#fig5_24) and you wish to determine what digit the handwriting represents.

![Figure 5.24 Sample handwritten digit to identify.](images/fig5_24.jpg)

[Figure 5.24](#chapter5.xhtml#b5fig5_24) Sample handwritten digit to identify.

For this example, we will use a much smaller training set, pictured in [Figure 5.25](#chapter5.xhtml#fig5_25), of digits in five categories, 0–4, and attempt to determine the probability that each of these samples is the handwritten digit shown in [Figure 5.24](#chapter5.xhtml#fig5_24). This smaller training dataset can be found at Github link 36.

![Figure 5.25 Small sample of digits from the training database.](images/fig5_25.jpg)

[Figure 5.25](#chapter5.xhtml#b5fig5_25) Small sample of digits from the training database.

Begin by assuming initial weights for each of the 15 inputs in the sample training set. We have chosen to make each sample of training data equally likely and thus equal weights, which is not a necessary assumption.

  
$$\\begin{array}{r} {\\left\\{ w\_{1},w\_{2},\\ldots,w\_{15} \\right\\} = \\left\\{ \\frac{1}{15},\\,\\frac{1}{15},\\ldots,\\,\\frac{1}{15} \\right\\}} \\\\ \\end{array}$$  

such that *ŷ* = *w*[1]*x*[1] + *w*[2]*x*[2] + … + *w*[15]*x*[15] = *X**W*.

We then apply an activation function, *ϕ*(*x*). In this case, we employ a neural network analysis, with the hyperbolic tangent activation function and traditional SSE cost function.

Choosing a learning rate, *r*, for example *r* = .03 to determine

  
$$\\begin{aligned} \\frac{\\partial SSE}{\\partial W} & {= - 2X^{T}(\\phi^{\\prime}(XW){^\\circ}(Y - \\phi(XW))} \\\\ W^{(i + 1)} & {= W^{(i)} - r \\cdot \\frac{\\partial SSE}{\\partial W}.} \\\\ \\end{aligned}$$  

Additionally, if the weights, *w*, are a percent vector, set

  
$$\\begin{array}{r} {w\_{i} = \\frac{w\_{i}}{\\sum\\limits\_{i = 1}^{15}w\_{i}}.} \\\\ \\end{array}$$  

If

  
$$\\begin{array}{r} {\\phi(X) = tanh(x)\\text{~and~}\\phi^{\\prime}(x) = sech^{2}(x),} \\\\ \\end{array}$$  

then after twenty iterations of the learning algorithm,

  
$$\\begin{array}{l} {w = \\left( \\begin{array}{l} 0.08427255 \\\\ {- 0.00643189} \\\\ {- 0.02651266} \\\\ {\\mathbf{0}.\\mathbf{12066096}} \\\\ {- 0.00716325} \\\\ 0.03448799 \\\\ 0.00267105 \\\\ 0.08602818 \\\\ {\\mathbf{0}.\\mathbf{23687438}} \\\\ {- 0.0082189} \\\\ {- 0.01507112} \\\\ 0.06937072 \\\\ 0.13791523 \\\\ {\\mathbf{0}.\\mathbf{29641327}} \\\\ {- 0.0052965} \\\\ \\end{array} \\right),} \\\\ \\end{array}$$  

and thus it is most probable that our digit is *x*[4], *x*[9], or *x*[14]. Predicting that the given image is the digit 3.

![Figure 5.26 Diagram of the Neural Network Process.](images/fig5_26.jpg)

Figure 5.26 Diagram of the Neural Network Process.

Since we are dealing with choosing a category for our input image, we can also choose to employ the **categorical cross-entropy cost function**, instead of SSE.

  
$$\\begin{array}{r} {C(X) = - {\\sum\\limits\_{j = 1}^{n}y\_{j}} \\cdot log(\\phi(x\_{j}w\_{j})) = - Ylog(\\phi(XW))} \\\\ \\end{array}$$  

with partial derivatives,

  
$$\\begin{array}{r} {\\frac{\\partial C}{\\partial W} = - \\frac{X^{T}Y}{\\phi(XW)}\\phi^{\\prime}(XW).} \\\\ \\end{array}$$  

If the activation function is the softmax function, $\\phi(x\_{j}) = \\frac{e^{j}}{\\sum\\limits\_{k = 1}^{n}e\_{k}},$ then

  
$$\\begin{aligned} \\frac{\\partial C}{\\partial w\_{k}} & {= - {\\sum\\limits\_{j = 1}^{n}\\frac{y\_{j}}{\\phi(x\_{j}w\_{j})}}\\frac{\\partial\\phi(x\_{j}w\_{j})}{\\partial w\_{k}}} \\\\ & {= \\frac{- x\_{k}y\_{k}\\phi(x\_{k}w\_{k})(1 - \\phi(x\_{k}w\_{k}))}{\\phi(x\_{k}w\_{k})} + {\\sum\\limits\_{j \\neq k}^{n}\\frac{x\_{j}y\_{j}\\phi(x\_{j}w\_{j})\\phi(x\_{k}w\_{k})}{\\phi(x\_{j}w\_{j})}}} \\\\ \\end{aligned}$$  

  
$$\\begin{aligned} & {= - x\_{k}y\_{k}(1 - \\phi(x\_{k}w\_{k})) + {\\sum\\limits\_{j \\neq k}x\_{j}}y\_{j}\\phi(x\_{k}w\_{k})} \\\\ & {= - x\_{k}y\_{k} + {\\sum\\limits\_{j = 1}^{n}x\_{j}}y\_{j}\\phi(x\_{k}w\_{k}).} \\\\ \\end{aligned}$$  

We will choose *y* to be a vector where *y*[*k*] = 1 and *y*[*j*] = 0 for all *j* ≠ *k*, 1 ≤ *k* ≤ *n*. Thus,

  
$$\\begin{array}{r} {\\frac{\\partial C}{\\partial w\_{k}} = - x\_{k}y\_{k} + x\_{k}\\phi(x\_{k}w\_{k}) = x\_{k}( - y\_{k} + \\phi(x\_{k}w\_{k})).} \\\\ \\end{array}$$  

Cross-entropy is computed for each value of *k*, noting that the smaller the entropy the more similar the input is to *y*[*k*].

In this example, with the initial values for *W*,

  
$$\\begin{array}{r} {XW(0) = 0,\\, XW(1) = \\frac{1}{5},\\, XW(2) = \\frac{11}{3},\\text{~and~}{\\sum\\limits\_{j = 1}^{n}X}W(j) = \\frac{4568}{15}.} \\\\ \\end{array}$$  

Applying the softmax activation function,

  
$$\\begin{array}{r} {\\phi(XW)(0) = \\frac{15e^{0}}{4568},\\,\\phi(XW)(1) = \\frac{15e^{\\frac{1}{5}}}{4568},\\text{~and~}\\phi(XW)(1) = \\frac{15e^{\\frac{11}{3}}}{4568}.} \\\\ \\end{array}$$  

In this problem, we need to calculate the cross-entropy for all 15 images in the training set; however, if there were only these three images with *y*[1] = {1,0,0}, *y*[2] = {0,1,0}, and *y*[2] = {0,0,1}, the cross-entropy associated with *y*[1] would be

  
$$\\begin{array}{r} {C = 1 \\cdot log\\left( \\frac{15e^{0}}{4568} \\right) + 0 \\cdot log\\left( \\frac{15e^{\\frac{1}{5}}}{4568} \\right) + 0 \\cdot log\\left( \\frac{15e^{\\frac{11}{3}}}{4568} \\right) \\approx - 5.71878.} \\\\ \\end{array}$$  

Similarly, the cross-entropy associated with *y*[2] is

  
$$\\begin{array}{r} {C = 0 \\cdot log\\left( \\frac{15e^{0}}{4568} \\right) + 1 \\cdot log\\left( \\frac{15e^{.2}}{4568} \\right) + 0 \\cdot log\\left( \\frac{15e^{\\frac{11}{3}}}{4568} \\right) \\approx - 5.51878.} \\\\ \\end{array}$$  

and that associated with *y*[3] is

  
$$\\begin{array}{r} {C = 0 \\cdot log\\left( \\frac{15e^{0}}{4568} \\right) + 1 \\cdot log\\left( \\frac{15e^{.2}}{4568} \\right) + 0 \\cdot log\\left( \\frac{15e^{\\frac{11}{3}}}{4568} \\right) \\approx - 2.05211.} \\\\ \\end{array}$$  

then the image associated with *y*[3] is most similar to the input image *x*.

## 5.7 CASE STUDY: Poisson Regression and COVID Counts

Suppose that an experiment consists of counting the number of confirmed COVID-19 cases each day over a period of time, *T*.

Define *Y*[*t*] as the random variable representing the total number of newly confirmed positive cases on day *t*, where *t* = 1, 2, …, *T*. Thus the probability density function of *Y*[*t*] is

  
$$\\begin{array}{r} {L(Y\_{t}|\\, t,\\, a\_{0},\\, a\_{1}) = {\\prod\\limits\_{t = 1}^{T}\\frac{{(a\_{0} + a\_{1}t)}^{Y\_{t}}}{Y\_{t}!}}e^{- (a\_{0} + a\_{1}t)},} \\\\ \\end{array}$$  

where the mean

  
$$\\begin{array}{r} {E(Y\_{t}|\\, t,\\, a\_{0},\\, a\_{1}) = \\lambda = \\ln(a\_{0} + a\_{1}t).} \\\\ \\end{array}$$  

The data for this Case Study is from the open source data site provided by the Ontario government on over 500000 confirmed cases of COVID-19 in Ontario in 2020 and 2021 \[[27](#refbib.xhtml#refbib27)\]. For this case study, a small sample of this data is displayed. The reader is encouraged to explore this data set further.

Table 5.6 COVID-19 cases in Ontario, Canada in April 2020.

  
| Date || 4/13 || 4/14 || 4/15 || 4/16 || 4/17 || 4/18 || 4/19 || 4/20 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Count || 607 || 576 || 638 || 615 || 655 || 536 || 358 || 539 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Date || 4/21 || 4/22 || 4/23 || 4/24 || 4/25 || 4/26 || 4/27 || 4/28 |
| Count || 432 || 460 || 445 || 428 || 448 || 367 || 470 || 401 |

We will model a log-linear model to this data and start with an initial guess of the coefficients of *A*^((0)) = {5.5, .4}.

With this guess,

  
$$\\begin{array}{ll} {LL(A^{(0)})} & {= \\left\\{ - 372768.,\\, - 5.45396 \\times 10^{6} \\right\\}} \\\\ {H(A^{(0)})} & {= \\left( \\begin{array}{ll} 445954. & {6.2404 \\times 10^{6}} \\\\ {6.2404 \\times 10^{6}} & {8.98843 \\times 10^{7}} \\\\ \\end{array} \\right)} \\\\ A^{(1)} & {= \\left\\{ 5.03667,\\, 0.49285 \\right\\}} \\\\ \\end{array}$$  

In this case,

  
$$\\begin{array}{r} {\\lambda = 5.03667 + 0.49285t.} \\\\ \\end{array}$$  

This information can also be used to determine the *R*0 in mid April 2020 in Ontario, Canada.

## 5.8 Exercises

*   Given $y = \\begin{pmatrix} y\_{1} \\\\ y\_{2} \\\\ \\end{pmatrix}$ $x = \\begin{pmatrix} x\_{1} \\\\ x\_{2} \\\\ x\_{3} \\\\ \\end{pmatrix}$ where *y*[1] = *x*[1]² + *x*[2] and *y*[2] = 4*x*[2]² + *x*[3]³. Find the Jacobian of the transformation.
    
*   Given *f*(*x*, *y*, *z*) = sin (*x**y* + *y*²*z*) determine the Gradient matrix and the Hessian matrix.
    
*   If *f*(*X*) = 4*x*[1]² + 6*x*[1]*x*[2]³ and $X = \\begin{pmatrix} x\_{1} \\\\ x\_{2} \\\\ \\end{pmatrix}$, find the gradient matrix *G*.
    
*   Find the matrix differential *l**n*(|*X*|).
    
*   Find the matrix differential of *X*^(*T*).
    
*   If *Y*[*i*], 1 ≤ *i* ≤ *n* are independent identically distributed random variables with joint likelihood function
    
      
    $$\\begin{array}{r} {p(y\_{i}|\\, x\_{i},\\, a\_{0},\\, a\_{1}) = \\Pi\_{i = 1}^{n}\\frac{y\_{i} - (a\_{0} + a\_{1}x\_{i})}{24}e^{- \\frac{{(y\_{i} - (a\_{0} + a\_{1}x\_{i}))}^{2}}{2}},} \\\\ \\end{array}$$  
    
    1.  Determine *L**L* = *l**o**g*(*p*(*y*| *x*[1], *x*[2]).
        
    2.  Find $\\frac{\\partial LL}{\\partial a\_{0}}$.
        
    3.  Find $\\frac{\\partial LL}{\\partial a\_{1}}$.
        
*   If *f*(*X*) =  − *Y**l**o**g*(*X**W*) where *X* is a 2 × 2 matrix and $W = \\begin{pmatrix} a\_{0} \\\\ a\_{1} \\\\ \\end{pmatrix}$, determine
    
      
    $$\\begin{array}{r} {\\frac{\\partial f}{\\partial W}.} \\\\ \\end{array}$$  
    
*   SSE is a common loss function to use in gradient descent, another common loss function is the **absolute error**
    
      
    $$\\begin{array}{r} {{\\sum\\limits\_{i = 0}^{n}|}{\\hat{y}}\_{i} - y\_{i}| = {\\sum\\limits\_{i = 0}^{n}|}(a\_{0} + a\_{1}x\_{i}) - y\_{i}|.} \\\\ \\end{array}$$  
    
    if the interpolating function is *ŷ* = *a*[0] + *a*[1](*x*), determine
    
      
    $$\\begin{array}{r} {\\frac{\\partial|(a\_{0} + a\_{1}x\_{i}) - y\_{i}|}{\\partial a\_{0}}\\text{~and~}\\frac{\\partial|(a\_{0} + a\_{1}x\_{i}) - y\_{i}|}{\\partial a\_{1}}.} \\\\ \\end{array}$$  
    
    (Hint: Recall that |*f*(*x*)| = *f*(*x*) when *f*(*x*) ≥ 0 and |*f*(*x*)| =  − *f*(*x*) when *f*(*x*) < 0.)
    
*   Given the interpolation points {(−1, 3), (0, −4), (1, 5), (2, −6)} if the loss function, *L*(*x*), is the absolute error from Exercise 8, and the goal is to find a linear interpolating function *ŷ* = *a*[0] + *a*[1]*x*,
    
    1.  Complete the following table for initial guess *a*[0] = 5, *a*[1] =  − .5.
        
         
        | *y*[*i*] || $\\hat{y\_{i}} = a\_{0} + a\_{1}x\_{i}$ || $\\frac{\\partial L}{\\partial a\_{0}}$ || $\\frac{\\partial L}{\\partial a\_{1}}$ |
        | --- | --- | --- | --- |
        | 3 || 5.5 ||  || \-1 |
        | --- | --- | --- | --- |
        | \-4 || 5 || 1 ||  |
        | 5 || 4.5 ||  ||  |
        | 2 || 4 || 1 || \-6 |
        | Total ||  ||  ||  |
        
    2.  If the learning rate is *r* = .03, use the table from part a. to determine a new value for *a*[0] and *a*[1].
        
*   In Exercise 9, what happens if the initial guess is *a*[0] = 0, *a*[1] = 0.
    
*   [Table 4.3](#chapter4.xhtml#tbl4_3) shows the number of COVID-19 total cases in NC over a six month period in 2020.
    
    1.  Create a quadratic interpolant *f̂*(*x*) = *a*[0] + *a*[1]*x* + *a*[2]*x*² with initial guesses for the coefficients *a*[0] = 40000, *a*[1] = 30000, *a*[2] = 4000 and determine the SSE for this model.
        
    2.  Determine the gradients $\\frac{\\partial SSE}{\\partial a\_{i}}$, 0 ≤ *i* ≤ 2 from the model in part a.
        
    3.  Use the gradients from part b. and a learning rate *r* = .0003 to create a quadratic interpolant and calculate the SSE for the new model.
        
*   Given interpolating points {(0, 3), (1, 2), (2,−1), (3, 5)}, find a linear maximum likelihood interpolating function.
    
*   [Example 5.19](#chapter5.xhtml#exam5_19) uses the Softmax activation function to determine a model for COVID vaccine effectiveness probabilities. Let
    
      
    $$\\begin{array}{l} {X = \\left( \\begin{array}{ll} 1 & 0 \\\\ 1 & 1 \\\\ 1 & 2 \\\\ \\end{array} \\right)\\text{~and~}Y = \\left( \\begin{array}{l} 0 \\\\ .3 \\\\ .9 \\\\ \\end{array} \\right)} \\\\ \\end{array}$$  
    
    the effective probabilities for 0, 1, or 2 COVID vaccines.
    
    1.  Use a logistic sigmoid activation function with weights $W^{(0)} = \\begin{pmatrix} .1 \\\\ .9 \\\\ \\end{pmatrix}$ to determine estimated values for *Y*.
        
    2.  Find SSE for your model in part a.
        
    3.  Update your weights from part a. using one iteration of gradient descent and a learning rate of *r* = .03. Determine the SSE with your new weights.
        
    4.  Use a ReLU activation function with weights weights $W^{(0)} = \\begin{pmatrix} .1 \\\\ .9 \\\\ \\end{pmatrix}$ to determine estimated values for *Y*.
        
    5.  Find SSE for your model in part d.
        
    6.  Update your weights from part d. using one iteration of gradient descent and a learning rate of *r* = .01.
        
*   [Example 5.25](#chapter5.xhtml#exam5_25) uses a Gaussian activation function to estimate categories for facial recognition. Use the data given in [Example 5.25](#chapter5.xhtml#exam5_25), *W*^((0)) = {.1,\\.9} and the activation function
    
      
    $$\\begin{array}{r} {\\phi(X) = \\frac{w\_{1}}{{(X - \\mu\_{1})}^{T}(X - \\mu\_{1})} + \\frac{w\_{2}}{{(X - \\mu\_{2})}^{T}(X - \\mu\_{2})}} \\\\ \\end{array}$$  
    
    with the SSE cost function to determine which category most resembles the images represented by *f*[1] and *f*[2].
    

# 6Decision Trees and Random Forests

DOI: [10.1201/9781003025672-6](https://doi.org/10.1201/9781003025672-6)

While previous chapters focus on techniques for making a single decision or model, this chapter focuses on ways to make a series of decisions that can incorporate previous techniques in order to best categorize data.

## 6.1 Decision Trees

A **decision tree** is a recursive partitioning of choices represented by a tree graph. A decision tree is similar to a flow chart and can be applied in a variety of venues. The general form of a decision tree can be seen in [Figure 6.1](#chapter6.xhtml#fig6_1).

![Figure 6.1 General Form of a Decision Tree.](images/fig6_1.jpg)

[Figure 6.1](#chapter6.xhtml#b6fig6_1) General Form of a Decision Tree.

Let's begin with an example of a decision tree applied to a logic statement.

Typically decision trees are used for classification tasks and regression analysis. A **classification tree** is a decision tree where each node, or vertex, has a binary decision connected to it based on whether an attribute is present or not. The top node, also called the **root**, in a classification tree represents the presence of all possible attributes, and each **child** node that is a subdivision of the node above it, also called the **parent** node.

A child node may be a successor decision node or a final outcome, called the **leaf** node.

A decision tree can also be used to divide quantitative data into regions or clusters.

But not all decisions are created equally. [Figures 6.2](#chapter6.xhtml#fig6_2) and [6.5](#chapter6.xhtml#fig6_5) show two different decision trees for *A* ∩ (*B* ∪ *C*), which one do you prefer?

![Figure 6.5 Another decision tree for logic statement A \\cap (B \\cup C).](images/fig6_5.jpg)

[Figure 6.5](#chapter6.xhtml#b6fig6_5) Another decision tree for logic statement *A* ∩ (*B* ∪ *C*).

Given the choice, it is best to choose a root node to split a decision in a way that provides more clarity after the split.

A decision tree defined over a domain of categorical attributes can be converted into a discrete numerical function. Many times, data scientists will wish to determine such functions that establish criteria to measure the closeness of the data to the desired outcome. There are several standard criteria that are used.

In [Section 5.6](#chapter5.xhtml#sec5_6), cross-entropy was used in order to make decisions about handwritten digits. **Entropy** and the **Gini index** are some examples of splitting functions.

### Entropy

If *Y* is a random event, then the **uncertainty** of *Y* = *y* occurring can be measured by

  
$$\\begin{array}{r} {log\_{2}\\left( \\frac{1}{P(Y = y)} \\right) = - log\_{2}(P(Y = y)).} \\\\ \\end{array}$$  

![Figure 6.6 Uncertainty of a random event \\left. Y \\right.\\sim N(0,1).](images/fig6_6.jpg)

Figure 6.6 Uncertainty of a random event *Y* ∼ *N*(0, 1).

The **entropy** of a random event *Y* is the expected uncertainty. That is, if *Y* is a discrete random variable, then

  
$$\\begin{array}{l} {Entropy(Y) = E\\left( {- log\_{2}\\left( {P\\left( {Y = y} \\right)} \\right)} \\right) = - \\sum\\limits\_{y}P(Y = y)log\_{2}(P(Y = y))} \\\\ \\end{array}$$  

and if *Y* is a continuous random variable,

  
$$\\begin{array}{r} {Entropy(Y) = - {\\int\_{- \\infty}^{\\infty}P}(Y = y)log\_{2}(P(Y = y))\\, dy.} \\\\ \\end{array}$$  

For a dataset *S*, entropy, *E**n**t**r**o**p**y*(*S*), is a measure of homogeneity within the dataset.

If there are classes *C*[1], *C*[2], …, *C*[*n*] of data in *S* then

  
$$\\begin{array}{r} {Entropy(S) = {\\sum\\limits\_{C\_{i}} -}P(C\_{i})log\_{2}(P(C\_{i})).} \\\\ \\end{array}$$  

If the entropy related to a decision tree is 0 then the data is completely homogenous and if there is a clear 50-50 split in the data then the entropy will be equal to 1.

For example, in [Figure 6.7](#chapter6.xhtml#fig6_7), in the graph to the left, the line *L*[1], splits the two classes and thus, *E**n**t**r**o**p**y*(*S*) = 1. In the graph on the right, roughly half of each class is on either side of line *L*[1] and thus the entropy would lie somewhere between 0 and 1.

![Figure 6.7 Example of Linearly Separable and Non-Separable Data Sets.](images/fig6_7.jpg)

[Figure 6.7](#chapter6.xhtml#b6fig6_7) Example of Linearly Separable and Non-Separable Data Sets.

Another indicator of strong splits in decisions is the Gini Impurity measure.

### Gini Impurity

The idea behind the Gini Impurity measure is to determine the probability that the nodes are chosen in a way that a random sample of data is classified incorrectly.

  
$$\\begin{aligned} {Gini\\, Impurity} & {= {\\sum\\limits\_{i = 1}^{n}p\_{i}}(1 - p\_{i})} \\\\ & {= 1 - {\\sum\\limits\_{i = 1}^{n}p\_{i}^{2}}} \\\\ \\end{aligned}$$  

where *P* = (*p*[1], *p*[2], …, *p*[*n*]) and *p*[*i*] is the probability that an object is classified in class *i* = 1, 2, …, *n*.

For example, assume we randomly select 10 data points as in [Figure 6.8](#chapter6.xhtml#fig6_8), with two categories. If a decision criteria in Node 1 creates a split shown by Nodes 2 and 3, we can then see that the

  
$$\\begin{array}{r} {\\text{Gini~Impurity~of~Node}\\,\\, 2 = 1 - \\frac{3}{4}^{2} - \\frac{1}{4}^{2} = \\frac{3}{8}} \\\\ \\end{array}$$  

![Figure 6.8 Example of decision criteria splitting.](images/fig6_8.jpg)

[Figure 6.8](#chapter6.xhtml#b6fig6_8) Example of decision criteria splitting.

  
$$\\begin{array}{r} {\\text{whereas~the~Gini~Impurity~of~Node}\\, 3 = 1 - \\frac{1}{3}^{2} - \\frac{2}{3}^{2} = \\frac{4}{9}.} \\\\ \\end{array}$$  

The Gini Impurity ranges from 0 to 1 and the higher the value the more impure the nodes of the decision tree are. This measure is only used for measuring categorical data. Other measures must be used for quantitative or continuous data.

Another way to think about the Gini impurity measure is that if *P* is a probability matrix where *P*[*i*, *j*] = *p*[*i*] when *i* = *j* and *P*[*i*, *j*] = 0 otherwise. Then

  
$$\\begin{array}{r} {Gini\\, impurity = Tr(I - P^{2}).} \\\\ \\end{array}$$  

### 6.1.1 Decision Trees Regression

Typical linear regression models work to linearly separate data, whereas decision tree models work to separate data that is not linearly separable. A visualization of a linearly separable set of data versus one which is not linearly separable can be seen in [Figure 6.7](#chapter6.xhtml#fig6_7).

In this section, we will focus on (1) Decision Tree Linear Regression as a categorization problem and (2) Decision Trees as a regression model. Later, we will take a brief look at how one might combine these ideas with those explored in [Chapter 4](#chapter4.xhtml) to create even better models.

Since the data that will be the focus of decision tree linear regression is typically linearly non-separable, the mathematical algorithm discussed is recursive in nature, starting at the root of the tree.

When using decision trees to determine clustering or linear regression models, it is important to hold back a set of data for a test data set for learning purposes. We will follow the steps of this recursive algorithm with an example related to the data in [Figure 6.9](#chapter6.xhtml#fig6_9).

![Figure 6.9 Training set for decision tree categorization example.](images/fig6_9.jpg)

[Figure 6.9](#chapter6.xhtml#b6fig6_9) Training set for decision tree categorization example.

We begin with a trained decision tree with a root node containing our entire test data set and a splitting feature.

With a root node as seen in [Figure 6.10](#chapter6.xhtml#fig6_10), notice that we begin by including all of the data points. Under the root condition, in this case *x*[1] > 2, child nodes are included based on whether the root condition is True or False.

![Figure 6.10 Example decision tree for categorization example, using training data in Figure 6.9.](images/fig6_10.jpg)

[Figure 6.10](#chapter6.xhtml#b6fig6_10) Example decision tree for categorization example, using training data in [Figure 6.9](#chapter6.xhtml#fig6_9).

After this first decision, the right child node only has data from a single category. We call this node a **pure node**. Notice that the first child node on the right in [Figure 6.9](#chapter6.xhtml#fig6_9) is not a pure node.

If we are given some data not in this training set, for example, (2, 1) and (0.5, 3), then we can follow the decision tree to decide which category to place these data points.

Since all of the child nodes are pure, (2, 1)→  ● and (0.5, 3)→  shaded bullet figure here.

In this example, there were many choices for conditions to split the training data, we discuss now how we best choose these conditions.

One way to do so is with a **greedy algorithm** in which conditions are considered by brute force. Unfortunately, this algorithm may still not determine the best splitting as once a condition on a root is determined the algorithm does not go back up the tree.

The steps for the greedy algorithm include:

*   Setting a root condition that produces a Gini impurity close to 1 (In the above example, for *x*[1] > 2, the Gini impurity is 1)
    
*   For each possible splitting rule, calculate *IG*,
    
      
    $$\\begin{array}{r} {Information\\, Gain = Entropy(parent) - {\\sum\\limits\_{i}w\_{i}}Entropy(child).} \\\\ \\end{array}$$  
    
    For the data shown in [Figure 6.11](#chapter6.xhtml#fig6_11), with root condition *x*[1] > 2, the child conditions are shown in [Table 6.2](#chapter6.xhtml#tbl6_2).
    
*   Choose a new condition that maximizes the information gain, *IG*.
    
    A pure child will produce an entropy of 0. Ideally, we would choose a smaller grid and larger variety of conditions; however, with the choices presented in [Table 6.2](#chapter6.xhtml#tbl6_2), three pure child nodes exists.
    
    The best choice for the next condition from those presented in [Table 6.2](#chapter6.xhtml#tbl6_2) is *x*[1] > 4.
    
*   Repeat Steps 1-3.
    
    With a new parent node and condition *x*[1] > 4, focus on the region
    
      
    $$\\begin{array}{r} {0 \\leq x\_{0} \\leq 4,\\, 2 \\leq x\_{1} \\leq 4.} \\\\ \\end{array}$$  
    
    The entropy of this new parent node is 0.95.
    
    The condition *x*[0] > 1 and *x*[1] > 3 have an information gain of
    
      
    $$\\begin{aligned} & {0.95 - log\_{2}\\left( \\frac{3}{6} \\right) \\cdot \\frac{6}{8} = 1.95\\text{~and~}} \\\\ & {.95 - \\left( {\\frac{3}{5}log\_{2}\\left( \\frac{3}{5} \\right) + \\frac{2}{5}log\_{2}\\left( \\frac{2}{5} \\right)} \\right) \\cdot \\frac{5}{8} - \\left( {\\frac{1}{3}log\_{2}\\left( \\frac{1}{3} \\right) + \\frac{2}{3}log\_{2}\\left( \\frac{2}{3} \\right)} \\right) \\cdot \\frac{3}{8}} \\\\ & {= 2.13078} \\\\ \\end{aligned}$$  
    
    respectively.
    

![Figure 6.11 Example of decision splitting for categorization example, using training data in Figure 6.9.](images/fig6_11.jpg)

[Figure 6.11](#chapter6.xhtml#b6fig6_11) Example of decision splitting for categorization example, using training data in [Figure 6.9](#chapter6.xhtml#fig6_9).

[Table 6.2](#chapter6.xhtml#b6tbl6_2) Example initial splits and corresponding entropy and information gained based on training data in [Figure 6.9](#chapter6.xhtml#fig6_9).

  
| Condition || Split, *S*[1], *S*[2] || Entropy for *S*[1] || Entropy for *S*[2] || IG |
| --- | --- | --- | --- | --- |
| *x*[0] > 1 || (3,0), (7,3) || 0 ||  − .3*l**o**g*[2](.3) − .7*l**o**g*[2](.7)≈ 0.88 || $1 - \\frac{3}{13} \\cdot 0$$- \\frac{10}{13} \\cdot 0.88 \\approx$ 0.32 |
| --- | --- | --- | --- | --- |
| *x*[0] > 2 || (3,1), (7,2) || 0.81 || 0.76 || 0.225 |
| *x*[0] > 3 || (6,3), (4,0) || 0.92 || 0 || 0.36 |
| *x*[0] > 4 || (8,3), (2,0) || 0.85 || 0 || 0.28 |
| *x*[1] > 3 || (3,2), (7,1) || 0.97 || 0.54 || 0.295 |
| *x*[1] > 4 || (5,3), (5,0) || 0.95 || 0 || 0.41 |

A decision tree that employs constraints that focus on one variable, *x*[*i*], at a time and compares the variable to a threshold value *b*, such as *x*[0] > 4 or *x*[1] > 2, is called a **univariate decision tree**.

A decision tree that is developed from constraints that are linear combination of the variables, or attributes, and compares to a threshold value *b*, such as 2*x*[0] + 4*x*[1] > 6 and $\\frac{7}{4}x\_{0} - x\_{1} > 8$, is called an **oblique decision tree**.

An oblique decision tree has constraints of the form

  
$$\\begin{array}{r} {Ax > b.} \\\\ \\end{array}$$  

Thus far, our examples of decision tree algorithms focus on categorization or classification. Similar techniques can be used for regression purposes as well. When using these algorithms for regression purposes, we can envision the regression problem as a classification problem, or a combination of decision trees and linear regression techniques can be employed.

[Example 6.9](#chapter6.xhtml#exam6_9) shows how a regression problem can be transformed into a classification problem in order to use decision tree algorithms.

## 6.2 Regression Trees

In the previous section, decision trees were used to predict either a classification or dependent value with discrete outcomes. A **regression tree** uses similar techniques to predict dependent values which may take on continuous values.

In a regression tree, we create node constraints with restrictions on the domain in the same way that we would in a decision tree, creating subsets within the domain. Once these subsets are created a regression model is created within each subset.

A common practice is to let *ŷ* be equal to the average of the outcomes within each subset. Just as we begun the discussion of classification with decision trees with an example, we do the same with regression.

It may seem best to create such small partitions that each partition contains exactly one training point; however, this can lead to larger errors in your model. We call this issue **overfitting**.

If we validate a model, to see how well it does, with the entire data set, and realize that there is an overfitting mistake, then **pruning** the tree will be required. This requires eliminating some of the leaf layers in order to allow for less constraints related to partitioning the data.

In [Example 6.10](#chapter6.xhtml#exam6_10), constant functions were used to create a model within each subset of the domain; however, you might note that a linear function or other function fits the data better. In this case, shown in [Example 6.11](#chapter6.xhtml#exam6_11), subsets of the domain can still be determined in order to develop a decision tree; however, within these subdomains other regression techniques, such as those presented in [Chapters 4](#chapter4.xhtml) and [5](#chapter5.xhtml), may be employed.

![Figure 6.18 An Example of a Regression Tree Model for Poverty Rates in the U.S. (2001–2020) \[32\].](images/fig6_18.jpg)

[Figure 6.18](#chapter6.xhtml#b6fig6_18) An Example of a Regression Tree Model for Poverty Rates in the U.S. (2001–2020) \[[32](#refbib.xhtml#refbib32)\].

## 6.3 Random Decision Trees and Forests

Data scientists tend to be less interested in a single experiment that generates data and more interested in a model for a family of experiments of data. These families are called **ensembles**. In this section, we will take a look at ensembles of decision trees.

A **random forest** is a classification algorithm consisting of several decision trees. In data analytics, a random forest consists of choosing random samples of data, training sets, from a larger data set, in order to create a decision tree, each tree produces an outcome, and a final outcome is determined based on majority voting. This technique is a type of **bagging** technique.

So for example let's say that you choose four random training sets, with replacement, and create a decision tree to classify the data into one of four class as seen in [Figure 6.19](#chapter6.xhtml#fig6_19). Given data, not within the training set, these decision trees can be used to place the data into classes, where the final classification can be made based on a majority rules decision. An additional example of random forest implementation can be see in the Case Study in [Section 6.5](#chapter6.xhtml#sec6_5).

![Figure 6.19 Example Random Forest.](images/fig6_19.jpg)

[Figure 6.19](#chapter6.xhtml#b6fig6_19) Example Random Forest.

## 6.4 CASE STUDY: Entropy of Wordle

The goal of Wordle is to come up with a secret five letter word within six guesses. Whether your game of the day is Wordle, Quordle, or even Octordle, you may have a go to word or set of words as part of a personal strategy to find the word or words of the day. You might think to use many vowels and start your game off with the initial guess “adieu”, or introduce common letters and try an initial guess like “snort”, or finally you might be a risk taker and go for a word that has uncommon letters that you would like to eliminate like “zesty”.

Although the actual Wordle game uses colored green, yellow, and gray squares to represent particular qualities to the guess, the following colored squares will be used in this analysis

![](images/pg229_1.jpg)

There are roughly 13,000 five letter words that are acceptable in the Wordle game and about 15900 five-letter words found in the word bank at GitHub link 41.

So how can we use entropy to choose our words wisely? A player that chooses a word like **ZESTY** for the first guess and gets the Z correct and in the correct location reduces the word choice list to 1200. According to the Scrabble dictionary, roughly 9% of five-letter words start with the letter Z.

Thus if we chose to make a decision purely based on whether the first letter is a Z, the information gained by playing *ZESTY* with this outcome is

  
$$\\begin{array}{r} {IG = 1 - .09 \\cdot log\_{2}(.09) - .91 \\cdot log\_{2}(.91) \\approx 1.44.} \\\\ \\end{array}$$  

However, if one wishes to make a decision based on whether the Y was correct, it is important to note that there are 1254 five-letter words ending with Y. A decision made based on a correctly placed Y at the end of the word provides an

  
$$\\begin{array}{r} {IG = 1 - \\left( \\frac{1254}{13000} \\right) \\cdot log\_{2}\\left( \\frac{1254}{13000} \\right) - \\left( \\frac{11746}{13000} \\right) \\cdot log\_{2}\\left( \\frac{11746}{13000} \\right) \\approx 1.19.} \\\\ \\end{array}$$  

Notice that the larger the probability of an event occurring, the smaller the information gain if the event occurs. In order to pick the best guess, it is helpful to choose the word with the smallest entropy and thus largest information gained. In this case study, we show a simplified version of what one might do.

From a beginning guess word, such as *ZESTY*, one might wish to find the probability of each outcome occurring. [Figure 6.20](#chapter6.xhtml#fig6_20) shows the probability of a word ending with a certain letter. Notice that a five-letter word with the S occurring in the last spot is most likely and thus would produce the least information gained, while one ending in B or Z would provide a large information gain.

![Figure 6.20 Probability of a five-letter word ending in a certain letter.](images/fig6_20.jpg)

[Figure 6.20](#chapter6.xhtml#b6fig6_20) Probability of a five-letter word ending in a certain letter.

If you did not want to focus on just one letter of your guess when making decisions, you could look at the probability of outcomes occurring, such as in [Figure 6.21](#chapter6.xhtml#fig6_21). The overall distribution of outcomes for the guesses *ZESTY* and *TARES* can be seen in [Figure 6.22](#chapter6.xhtml#fig6_22).

![Figure 6.21 Probability of specific outcomes occurring with a guess of ZESTY.](images/fig6_21.jpg)

[Figure 6.21](#chapter6.xhtml#b6fig6_21) Probability of specific outcomes occurring with a guess of *ZESTY*.

![Figure 6.22 Probability Distribution for Outcomes Given the Guess ZESTY (TOP) and TARES (BOTTOM).](images/fig6_22.jpg)

[Figure 6.22](#chapter6.xhtml#b6fig6_22) Probability Distribution for Outcomes Given the Guess *ZESTY* (TOP) and *TARES* (BOTTOM).

Notice that the probability distribution for the guess *ZESTY* is taller and thinner than that for the guess *TARES*. The probability of an event occurring and the entropy associated with the event are inversely proportional. Thus the closer the distribution is to uniform, flat, the more information is provided by the guess.

We use the heights of the bars in the simplified probability distribution shown in [Figure 6.22](#chapter6.xhtml#fig6_22) as the probabilities for the entropy of the guess. Using the simplified distribution from Python code found at GitHub link 42, the entropy, or the expected information value, for the guesses *ZESTY* and *TARES* are approximately 2.6 and 3.24 respectively.

So if you did start your game with a guess of *ZESTY* and got an outcome of

![](images/ufig6_4.jpg)

what would your next guess be?

zapas, zapus, zarfs, ziffs, zills, zincs, zings, zoism, zooks, zooms, zoons, zoris, zulus, zunis

Python and R code for this case study can be found at Github link 37 and 39 respectively.

## 6.5 CASE STUDY: Bird Call Identification

Many times, species identification techniques require capture and release. A less invasive species identification technique is to record the calls of the species, in this case birds, and look for similarities. In this case study, we are given data from several bird calls, found at Github link 43, in order to develop a model for the classification of species of birds. In particular, we wish to identify the call of the Sri Lankan Junglefowl, the national bird of Sri Lanka, among other bird calls from Sri Lanka. A larger database of bird calls can be found at \[[43](#refbib.xhtml#refbib43)\].

It is important to note that, in reality, this type of data could consist of data blocks from very different times in the birds calling cycle. Therefore, one bird's call may just be a translated version of another's. Additionally, certain birds could be closer or calling louder, and thus the scale on the call may not be significant in the identification of the species.

What might be more important to observe is the dominant frequencies present in the call. In this case study, we discuss how to transform data into a frequency domain for this type of analysis.

Given a discrete data set {*y*[1], *y*[2],…, *y*[*n*]}, the **Discrete Fourier Transform** is defined as

  
$$\\begin{array}{r} {F\_{k} = {\\sum\\limits\_{j = 1}^{n - 1}y\_{j}}e^{\\frac{- 2\\pi i}{n}kj}.} \\\\ \\end{array}$$  

[Figure 6.24](#chapter6.xhtml#fig6_24) shows the frequency distribution for several Sri Lankan junglefowl calls. For more information about Fourier analysis see \[[28](#refbib.xhtml#refbib28)\].

![Figure 6.23 Visualization of soundwaves of two different Sri Lankan Junglefowl.](images/fig6_23.jpg)

[Figure 6.23](#chapter6.xhtml#b6fig6_23) Visualization of soundwaves of two different Sri Lankan Junglefowl.

![Figure 6.24 Visualization of Frequencies in Sri Lanka junglefowl calls from Figure 6.23.](images/fig6_24.jpg)

[Figure 6.24](#chapter6.xhtml#b6fig6_24) Visualization of Frequencies in Sri Lanka junglefowl calls from [Figure 6.23](#chapter6.xhtml#fig6_23).

From this, one might wish to study what the peak frequencies are, or the width between peak frequencies, among other characteristics.

If *p*[1] and *p*[2] are the two frequencies, 1K Hz as the units, occurring the most in the call, [Figure 6.25](#chapter6.xhtml#fig6_25) shows *p*[1] versus the absolute relative increase between *p*[1] and *p*[2],

![Figure 6.25 Visualization of four outcomes from different training data sets, jungle fowl denoted by ∘.](images/fig6_25.jpg)

[Figure 6.25](#chapter6.xhtml#b6fig6_25) Visualization of four outcomes from different training data sets, jungle fowl denoted by ∘.

  
$$\\begin{array}{r} {\\left| \\frac{p\_{1} - p\_{2}}{p\_{1}} \\right|.} \\\\ \\end{array}$$  

The dashed lines in [Figure 6.25](#chapter6.xhtml#fig6_25) might be considered as criteria for a decision tree. Given this information, a bird call with a peak frequency of 20K Hz and an absolute relative increase of 9Hz WOULD be identify as a Sri Lankan junglefowl while a bird call with a peak frequency of 25K Hz and an absolute relative increase of 30Hz WOULD NOT be identify as a Sri Lankan junglefowl.

Github links 38 and 40 provide Python and R code for this case study.

## 6.6 Exercises

*   Given the data in [Figure 6.26](#chapter6.xhtml#fig6_26) and root condition, *x* > 0,
    
    ![Figure 6.26 Data for Exercise 1.](images/fig6_26.jpg)
    
    [Figure 6.26](#chapter6.xhtml#b6fig6_26) Data for Exercise 1.
    
    1.  Find the entropy and information gained for the root criteria *x* > 0.
        
    2.  Determine a root condition that will create a pure child node.
        
    3.  Create a decision tree which maximizes information gain at each stage with the root node condition *x* > 0.
        
*   Spotify training data in [Table 6.6](#chapter6.xhtml#tbl6_6) shows loudness and acoustic factors for several songs. Use techniques presented in [Example 6.10](#chapter6.xhtml#exam6_10) to determine a regression tree.
    
    [Table 6.6](#chapter6.xhtml#b6tbl6_6) Spotify training data.
    
      
    | Loudness || Acousticness |
    | --- | --- |
    | \-8.078 || 0.000464 |
    | --- | --- |
    | \-4.234 || 0.00105 |
    | \-9.533 || 0.0612 |
    | \-6.36 || 0.112 |
    | \-7.734 || 0.0553 |
    | \-7.165 || 0.379 |
    
*   [Table 6.7](#chapter6.xhtml#tbl6_7) shows a training data set from a disease database based on burden by cause \[[41](#refbib.xhtml#refbib41)\].
    
    [Table 6.7](#chapter6.xhtml#b6tbl6_7) Training data set from a disease database.
    
      
    | Substance Abuse || Interpersonal Violence || Self-harm |
    | --- | --- | --- |
    | 1.17 || 2.29 || 0.56 |
    | --- | --- | --- |
    | 1.29 || 1.29 || 0.36 |
    | 0.48 || 1.81 || 2.98 |
    | 3.52 || 3.52 || 1.52 |
    | 0.26 || 0.16 || 0.35 |
    | 0.24 || 1.80 || 1.46 |
    | 0.60 || 0.22 || 0.38 |
    | 0.68 || 0.22 || 0.38 |
    | 2.43 || 1.15 || 0.63 |
    | 1.37 || 0.31 || 0.42 |
    | 0.73 || 0.24 || 0.41 |
    | 0.58 || 3.29 || 2.16 |
    
     
    | Country || Year || Self harm || Substance abuse disorders || Interpersonal violence |
    | --- | --- | --- | --- | --- |
    | Sri Lanka || 2019 || 3.47 || 1.091 || 0.87 |
    
    1.  Create a regression tree to model interpersonal violence versus self-harm.
        
    2.  If the self harm measure is placed into 3 categories, Category 1 (low, less than .5), Category 2 (medium, between .5 and 1), and Category 2 (high, above 2), create a graph of substance abuse versus interpersonal violence that also shows the category of self harm.
        
    3.  Use the graph in part b. to create a decision tree to categorize the self harm measure.
        
    4.  Use the decision tree in part c. to predict the category of self harm for Sri Lanka in 2019.
        
    5.  Discuss why a random forest model may produce better results than the single decision tree model from part c.
        
    6.  Using the dataset found at Github link 50, chose at least 5 random training sets. For each random training set, replicate steps b. through d. From this random forest algorithm again predict the category of self harm for Sri Lanka in 2019.
        

# 7Random Matrices and Covariance Estimate

DOI: [10.1201/9781003025672-7](https://doi.org/10.1201/9781003025672-7)

## 7.1 Introduction to Random Matrices

So far, we have used matrices with fixed values to model scenarios in data science. Here we will explore the idea of matrices whose entries are determined at random from a probability density function. Such a matrix is called a **random matrix** and each entry is consider to be a random variable.

For example, we can define a 3 × 3 matrix, *X*, with entries that are randomly distributed with a standard normal distribution, *N*(0, 1). One example of a random matrix, *X*, such that *X*[*i*, *j*] ∼ *N*(0, 1) is

  
$$\\begin{array}{l} {X = \\left( \\begin{array}{lll} 0.290226 & 0.91635 & 0.0998479 \\\\ 0.882873 & {- 0.615393} & {- 0.902417} \\\\ {- 0.0974429} & {- 0.855375} & {- 0.665516} \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

The matrix *X* is not symmetric; however, matrices such as *X**X*^(*T*) and *X* + *X*^(*T*) will always be symmetric matrices with real eigenvalues.

A *n* × *n* matrix, *M*, with entries *m*[*i*, *j*] is a called a **Wigner matrix** if the entries of *M*, *m*[*i*, *j*] for 1 ≤ *i* ≤ *j* ≤ *n*, are randomly i.i.d.

In this section, we will focus on random matrices whose entries come from a Gaussian distribution,

  
$$\\begin{array}{l} {X = \\left( \\begin{array}{lllll} X\_{1,1} & X\_{1,2} & X\_{1,3} & \\ldots & X\_{1,n} \\\\ X\_{2,1} & X\_{2,2} & X\_{2,3} & \\ldots & X\_{2,n} \\\\ X\_{3,1} & X\_{3,2} & X\_{3,3} & \\ldots & X\_{3,n} \\\\ \\vdots & \\ddots & \\ddots & \\ddots & \\vdots \\\\ X\_{m,1} & X\_{m,2} & X\_{m,3} & \\ldots & X\_{m,n} \\\\ \\end{array} \\right),} \\\\ \\end{array}$$  

where *X*[*i*, *j*] ∼ *N*(*μ*, *σ*²) are i.i.d, 1 ≤ *i* ≤ *m*, 1 ≤ *j* ≤ *n*.

Typically, random matrices of importance in application fall into three general categories based on whether their entries are real, complex, or quaternionic random variables. In this chapter, we will be focusing on these three types of random matrices and the behavior of their eigenvalues.

Before taking a deep dive into these three families of random matrices, we will explore the effects of randomness on the stability of algorithms in linear algebra.

## 7.2 Stability

We have learned that, in linear algebra, if a matrix *A* is an invertible matrix then the system *A**x* = *b* has a unique solution,

  
$$\\begin{array}{r} {x = A^{- 1}b.} \\\\ \\end{array}$$  

However, when dealing with a random matrix, *A* + *E*, such that *E*[*i*, *j*] ∼ *N*(*μ*, *σ*²), computational solutions may be incorrect or may not exist, typically due to round off error.

The **condition number** of a matrix, *A*, *κ*(*A*), is a number that represents how fast a solution, *x*, to the linear system *A**x* = *b* is changing with changes in *b*.

  
$$\\begin{array}{l} {\\kappa(A) = \\left\\{ \\begin{array}{ll} {||A|| \\cdot ||A^{- 1}||,} & {\\text{~if~}A\\,\\text{is~invertible~},} \\\\ {\\infty,} & {\\text{~otherwise}\\text{.}} \\\\ \\end{array}~ \\right.} \\\\ \\end{array}$$  

When dealing with a matrix with a higher condition number, the accuracy of results will be lower in solving problems related to the matrix. This includes the stability of the eigensystem of the matrix.

The **pseudospectrum** of a matrix *A* is the family of eigenvalues of *A* + *E*.

Typically data scientists deal with matrices that have errors, also called **noisy matrices**. Because of this, the pseudospectrum of noisy matrices are of particular interest.

![Figure 7.1 Visualization of a pseudospectrum.](images/fig7_1.jpg)

[Figure 7.1](#chapter7.xhtml#b7fig7_1) Visualization of a pseudospectrum.

![Figure 7.2 Visualization of a pseudospectrum, \\sigma^{2} = 0,\\text{\\textbackslash}.01,\\text{\\textbackslash}.25.](images/fig7_2.jpg)

[Figure 7.2](#chapter7.xhtml#b7fig7_2) Visualization of a pseudospectrum, *σ*² = 0, \\.01, \\.25.

Throughout the rest of this chapter, we take a look at families of random matrices and their respective eigenvalues.

## 7.3 Gaussian Orthogonal Ensemble

Models for a family of matrices of data are referred to as **matrix ensembles**.

Recall from [Chapter 5](#chapter5.xhtml), that if *X* and *Y* are i.i.d. random variables where *X*, *Y* ∼ *N*(*μ*, *σ*²) then the joint distribution of *X* and *Y*,

  
$$\\begin{array}{r} {\\left. f\_{XY}(x,y) \\right.\\sim N\\left( {\\mu,\\frac{\\sigma^{2}}{2}} \\right).} \\\\ \\end{array}$$  

In this section, we wish to look at the distribution of linear combinations of *X* and *Y*, such as *X* + *Y* or $\\frac{X}{2}$, where *X* and *Y* are random matrices, and the eigenvalues associated with them.

If *X* is a random matrix where *X*[*i*, *j*] ∼ *N*(0, 1), then

  
$$\\begin{array}{r} {H = \\frac{X + X^{T}}{2}} \\\\ \\end{array}$$  

is a symmetric random matrix, and the probability distribution of such a symmetric matrix is called the **Gaussian Orthogonal Ensemble (GOE)**.

The previous two lemmas tell us about the joint distribution of the elements of a GOE matrix. More interestingly, we will further explore the distribution of the eigenvalues and spacing of eigenvalues of random matrices from the GOE.

For a general 2 × 2 random matrix from the GOE,

  
$$\\begin{array}{l} {X = \\left( \\begin{array}{ll} X\_{1} & X\_{2} \\\\ X\_{2} & X\_{3} \\\\ \\end{array} \\right),} \\\\ \\end{array}$$  

where *X*[1],*X*[3] ∼ *N*(0, 1) and $\\left. X\_{2} \\right.\\sim N(0,\\,\\frac{1}{2})$ are i.i.d. The eigenvalues of *X* are

  
$$\\begin{array}{r} {\\frac{1}{2}Tr(X) \\pm \\sqrt{{(X\_{1} - X\_{3})}^{2} + 4X\_{2}^{2}}.} \\\\ \\end{array}$$  

Thus the mean of the eigenvalues is *X*[1] + *X*[3].

The probability density function of *X*[1]+*X*[3] ∼ *N*(0, 2), which can be seen in [Figure 7.3](#chapter7.xhtml#fig7_3).

![Figure 7.3 Distribution of mean of eigenvalues in 2 \\times 2 GOE.](images/fig7_3.jpg)

[Figure 7.3](#chapter7.xhtml#b7fig7_3) Distribution of mean of eigenvalues in 2 × 2 GOE.

![Figure 7.4 Distribution of eigenvalues of 100 \\times 100 GOE matrices, visualizing Wigner's Semicircle Law.](images/fig7_4.jpg)

[Figure 7.4](#chapter7.xhtml#b7fig7_4) Distribution of eigenvalues of 100 × 100 GOE matrices, visualizing Wigner's Semicircle Law.

The **Marchenko-Pastur Quarter-Circle Law** is the analogous property for the singular values of a matrix.

![Figure 7.5 Distribution of singular values of 100 \\times 100 GOE matrices, visualizing Marchenko-Pastur Quarter-Circle Law.](images/fig7_5.jpg)

Figure 7.5 Distribution of singular values of 100 × 100 GOE matrices, visualizing Marchenko-Pastur Quarter-Circle Law.

Scientists and data scientists are even more interested in the distribution of the spacing between the individual eigenvalues of a matrix. Wigner attempted to compare the spacing between heavy nuclei resonances and the spacing between eigenvalues of GOE matrices.

This theory, called **Wigner's surmise**, describes a phenomenon called ‘level repulsion’. In a spatially bound system, particles can only have discrete amounts of energy, which tend to cluster in a general sense.

In general, Wigner's surmise states that the probability density function of the eigenvalue spacings, *S*, of a random GOE matrix follows a Rayleigh distribution.

  
$$\\begin{array}{r} {p(s) = P(S = s) = \\frac{s^{2}}{k^{2}}e^{\\frac{- s^{2}}{2k^{2}}},} \\\\ \\end{array}$$  

where *k* is a scale parameter for the distribution.

Since the entries of such matrices are random variables and not fixed numbers, we must investigate techniques to theoretically determine the probability distribution of the eigenvalues.

We dig deeper into the theoretical aspects of Wigner's surmise for 2 × 2 GOE random matrices.

If we define a 2 × 2 random matrix from the GOE,

  
$$\\begin{array}{l} {X = \\left( \\begin{array}{ll} X\_{1} & X\_{2} \\\\ X\_{2} & X\_{3} \\\\ \\end{array} \\right),} \\\\ \\end{array}$$  

where *X*[1],*X*[3] ∼ *N*(0, 1) are i.i.d and $\\left. X\_{2} \\right.\\sim N(0,\\frac{1}{2})$, the eigenvalues of *X* are

  
$$\\begin{array}{r} {\\frac{1}{2}Tr(X) \\pm \\sqrt{{(X\_{1} - X\_{3})}^{2} + 4X\_{2}^{2}}.} \\\\ \\end{array}$$  

Let $s = \\lambda\_{1} - \\lambda\_{2} = \\sqrt{(X\_{1} - X\_{3}^{2}) + 4X\_{2}^{2}}$. The probability density function for *s*,

  
$$\\begin{aligned} {p(s)} & {= \\frac{1}{2\\pi^{3/2}}{\\int\_{- \\infty}^{\\infty}{\\int\_{- \\infty}^{\\infty}{\\int\_{- \\infty}^{\\infty}e^{\\frac{- (X\_{1}^{2} + 2X\_{2}^{2} + X\_{3}^{2})}{2}}}}}dX\_{1}dX\_{2}dX\_{3}} \\\\ & {\\text{\\quad\\quad}\\delta(d - \\sqrt{{(X\_{1} - X\_{3})}^{2} + 4X\_{2}^{2}}).} \\\\ \\end{aligned}$$  

A visualization of *p*(*s*) can be seen in [Figure 7.6](#chapter7.xhtml#fig7_6).

![Figure 7.6 Example distribution of Wigner Surmise with 2 \\times 2 GOE distribution.](images/fig7_6.jpg)

[Figure 7.6](#chapter7.xhtml#b7fig7_6) Example distribution of Wigner Surmise with 2 × 2 GOE distribution.

With a change of variables,

  
$$\\begin{aligned} {X\_{1} - X\_{3}} & {= r\\cos(\\theta),} \\\\ {X\_{1} + X\_{3}} & {= \\eta,} \\\\ X\_{2} & {= r\\sin(\\theta)/2,} \\\\ \\end{aligned}$$  

we get,

  
$$\\begin{array}{l} {J = \\left| \\begin{array}{lll} {\\cos(\\theta)/2} & {- r\\sin(\\theta)/2} & {1/2} \\\\ {- \\cos(\\theta)/2} & {r\\sin(\\theta)/2} & {1/2} \\\\ {\\sin(\\theta)/2} & {\\cos(\\theta)/2} & 0 \\\\ \\end{array} \\right| = - r/4,} \\\\ \\end{array}$$  

  
$$\\begin{array}{lll} {p\\left( s \\right)} & = & {\\frac{1}{8\\pi^{3/2}}\\int\_{0}^{\\infty}\\int\_{0}^{2\\pi}\\int\_{- \\infty}^{\\infty}e^{{({- \\frac{{(\\frac{r\\cos(\\theta) + \\eta}{2})}^{2} + {(\\frac{- r\\cos(\\theta) + \\eta}{2})}^{2} + \\frac{r^{2}\\sin^{2}(\\theta)}{2}}{2}})}r\\delta(d - r)d\\eta d\\theta dr}} \\\\ & = & {\\frac{1}{8\\pi^{3/2}}\\int\_{0}^{\\infty}rdr\\delta(s - r)\\int\_{0}^{2\\pi}d\\theta\\int\_{- \\infty}^{\\infty}e^{- \\frac{1}{2}{({r + \\frac{\\eta^{2}}{4}})}}d\\eta} \\\\ & = & {\\frac{s^{2}}{2}e^{- s^{2}/4}.} \\\\ \\end{array}$$  

## 7.4 Gaussian Unitary Ensemble

In this section, we consider random matrices with complex entries. Recall that if *z* = *a* + *i**b* then $\\overline{z} = a - ib$ is the **complex conjugate** of *z*. If *A* is a square matrix, then the entries of $\\overline{A}$ are the complex conjugate of each corresponding entry in *A*.

A square matrix, *A*, is called **Hermitian** if

  
$$\\begin{array}{r} {{\\overline{A}}^{T} = A.} \\\\ \\end{array}$$  

${\\overline{A}}^{T}$ is called the **conjugate transpose** of A.

An invertible square matrix, *A*, is **unitary** if

  
$$\\begin{array}{r} {{\\overline{A}}^{T} = A^{- 1}.} \\\\ \\end{array}$$  

Every Hermitian matrix, *H*, is diagonalizable with a unitary matrix, *U*, and the resulting diagonal matrix, *D*, will have real entries. That is if *H* is a Hermitian matrix then there exists a unitary matrix *U* such that

  
$$\\begin{array}{r} {D = U^{- 1}HU,} \\\\ \\end{array}$$  

where *D*[*i*, *i*] ∈ ℝ.

  
$$\\begin{array}{l} {H = \\left( \\begin{array}{ll} 1 & {2 + 3I} \\\\ {2 - 3I} & 4 \\\\ \\end{array} \\right)\\text{~and~}U = \\left( \\begin{array}{ll} {(2 - 3i)\\sqrt{\\frac{1}{26} - \\frac{3}{26\\sqrt{61}}}} & \\frac{\\sqrt{61} + 3}{\\sqrt{6\\sqrt{61} + 122}} \\\\ {( - 2 + 3i)\\sqrt{\\frac{1}{26} + \\frac{3}{26\\sqrt{61}}}} & \\frac{\\sqrt{61} - 3}{\\sqrt{122 - 6\\sqrt{61}}} \\\\ \\end{array} \\right)} \\\\ \\end{array}$$  

where the columns of *U* are the unit eigenvectors of *H*, then

  
$$\\begin{array}{l} {U^{- 1}HU = \\left( \\begin{array}{ll} {\\frac{1}{2}\\left( {\\sqrt{61} + 5} \\right)} & 0 \\\\ 0 & {\\frac{1}{2}\\left( {5 - \\sqrt{61}} \\right)} \\\\ \\end{array} \\right) = D.} \\\\ \\end{array}$$  

*U* is a unitary matrix and the main diagonal entries of *D* are the real eigenvalues of *H*.

Applying this idea with similar ideas to that in [Lemma 4](#chapter7.xhtml#lemm7_4), the probability density of a Hermitian matrix, *H*, is the same as that for *D* = *U*^( − 1)*H**U*, and thus is directly related to the probability density of the eigenvalues of *H*.

A random Hermitian matrix is a matrix in the **Gaussian Unitary Ensemble (GUE)** if *H*[*i*, *i*] ∼ *N*(0, 1) and the upper triangular entries $\\left. H\_{i,j} \\right.\\sim N\\left( {0,\\,\\frac{1}{2}} \\right) + iN\\left( {0,\\,\\frac{1}{2}} \\right)$, for 1 ≤ *i* ≤ *j* ≤ *n*. The standard GUE,

  
$$\\begin{array}{r} {H = \\frac{X + {\\overline{X}}^{T}}{2},} \\\\ \\end{array}$$  

where *X*[*i*, *i*] ∼ *N*(0, 1) and $\\left. X\_{i,j} \\right.\\sim\\mathbf{N}\\left( {\\mathbf{0},\\,\\frac{\\mathbf{1}}{\\mathbf{2}}} \\right) + i\\mathbf{N}\\left( {\\mathbf{0},\\,\\frac{\\mathbf{1}}{\\mathbf{2}}} \\right)$ for 1 ≤ *i* ≤ *j* ≤ *n*.

Like the Gaussian Orthogonal Ensemble, if we define a 2 × 2 random matrix from a GUE,

  
$$\\begin{array}{l} {X = \\left( \\begin{array}{ll} X\_{1} & {X\_{2} + X\_{3}i} \\\\ {X\_{2} - X\_{3}i} & X\_{4} \\\\ \\end{array} \\right),} \\\\ \\end{array}$$  

with i.i.d random variables *X*[1], *X*[4] ∼ *N*(0,1) and $\\left. X\_{2},\\, X\_{3} \\right.\\sim N\\left( {0,\\frac{1}{2}} \\right)$, the eigenvalues of *X* are

  
$$\\begin{array}{r} {\\frac{1}{2}Tr(X) \\pm \\sqrt{{(X\_{1} - X\_{4})}^{2} + 4{(X\_{2} + X\_{3}i)}^{2}},} \\\\ \\end{array}$$  

and the mean of the eigenvalues is $\\left. \\frac{1}{2}\\left( {X\_{1} + X\_{4}} \\right) \\right.\\sim N\\left( {0,\\frac{1}{2}} \\right)$.

The result presented in [Theorem 18](#chapter7.xhtml#theo7_18) is not necessarily true for all random matrices which are not GOE or GUE. [Figure 7.7](#chapter7.xhtml#fig7_7) shows the real versus imaginary part of the mean eigenvalue of a non-Hermitian, non-symmetric, random matrix.

![Figure 7.7 The Real vs Imaginary parts of the mean eigenvalue of a 2 \\times 2 Non-Hermitian Random Matrix.](images/fig7_7.jpg)

[Figure 7.7](#chapter7.xhtml#b7fig7_7) The Real vs Imaginary parts of the mean eigenvalue of a 2 × 2 Non-Hermitian Random Matrix.

The final ensemble of this chapter is the Gaussian Symplectic Ensemble, which focuses on random entries who are quaternion in nature.

## 7.5 Gaussian Symplectic Ensemble

A **quaternion** is a linear combination

  
$$\\begin{array}{r} {q = a \\cdot 1 + bi + cj + dk,} \\\\ \\end{array}$$  

where *a*, *b*, *c*, and *d* ∈ ℝ and *i*, *j*, and *k* are the quaternion units,

  
$$\\begin{array}{r} {i^{2} = j^{2} = k^{2} = i \\cdot j \\cdot k = - 1.} \\\\ \\end{array}$$  

The set of quaternions is denoted ℍ.

The complex conjugate for a quaternion, *q*, can also be defined

  
$$\\begin{array}{r} {\\overline{q} = a \\cdot 1 - bi - cj - dk.} \\\\ \\end{array}$$  

Similar to elements in ℂ^(*n*), if *q* = (*q*[1], *q*[2], …, *q*[*n*]) and *p* = (*p*[1], *p*[2], …, *p*[*n*]) are in ℍ^(*n*) then

  
$$\\begin{array}{r} {< p,\\, q > = {\\sum\\limits\_{i = 1}^{n}{\\overline{p}}\_{i}}q\_{i},} \\\\ \\end{array}$$  

and thus the norm of *q*,

  
$$\\begin{array}{r} {||q|| = q\\overline{q} = \\overline{q}q = a^{2} + b^{2} + c^{2} + d^{2}.} \\\\ \\end{array}$$  

A 2 × 2 matrix, *Q*, of the form

  
$$\\begin{array}{l} {Q = \\left( \\begin{array}{ll} z & w \\\\ {- \\overline{w}} & \\overline{z} \\\\ \\end{array} \\right),} \\\\ \\end{array}$$  

where *z* and *w* are complex numbers is called a **real quaternion** matrix. Just like the standard basis elements of the quaternions, are 1, *i*, *j* and *k*, as 2 × 2 matrices

  
$$\\begin{array}{l} {V\_{1} = \\left( \\begin{array}{ll} 1 & 0 \\\\ 0 & 1 \\\\ \\end{array} \\right),\\, V\_{2} = \\left( \\begin{array}{ll} i & 0 \\\\ 0 & {- i} \\\\ \\end{array} \\right),} \\\\ \\end{array}$$  

  
$$\\begin{array}{l} {V\_{3} = \\left( \\begin{array}{ll} 0 & 1 \\\\ {- 1} & 0 \\\\ \\end{array} \\right),\\text{~and~}V\_{4} = \\left( \\begin{array}{ll} 0 & i \\\\ i & 0 \\\\ \\end{array} \\right),} \\\\ \\end{array}$$  

can serve as a basis for the set of real quaternion matrices where

  
$$\\begin{array}{r} {Q = aV\_{1} + bV\_{2} + cV\_{3} + dV\_{4}.} \\\\ \\end{array}$$  

We will see how real quaternion matrices are related to the next ensemble presented, the Gaussian Symplectic Ensemble.

A matrix *A* is **skew-symmetric** if

  
$$\\begin{array}{r} {A^{T} = - A} \\\\ \\end{array}$$  

A **symplectic** matrix *M* is a 2*n* × 2*n* matrix such that if $S = \\begin{pmatrix} 0 & I\_{n} \\\\ {- I\_{n}} & 0 \\\\ \\end{pmatrix}$ is a real skew-symmetric matrix then

  
$$\\begin{array}{r} {M^{T}SM = S.} \\\\ \\end{array}$$  

If *X* is a 2*n* × 2*n* matrix with entries *X*[*i*, *j*] ∼ *N*(0, *σ*²) + *i**N*(0, *σ*²) and *X*[*i*, *j*] are i.i.d. then we define

  
$$\\begin{array}{r} {H = \\frac{X + {\\overline{X}}^{T} - S{(X + {\\overline{X}}^{T})}^{T}S}{4}} \\\\ \\end{array}$$  

as a **Gaussian Symplectic Ensemble (GSE)**, where $S = \\begin{pmatrix} 0 & {- 1} \\\\ 1 & 0 \\\\ \\end{pmatrix} \\otimes I\_{n}$.

We have seen three different types of matrix ensembles. You can find a deep dive into the joint distributions of elements of the GOE and that of the eigenvalues of the GOE in [Section 7.3](#chapter7.xhtml#sec7_3). In general if *β* = 1, 2, and 4, represent the GOE, GUE, and GSE, the joint distribution of the elements from a random matrix, *X*, are of the form

  
$$\\begin{array}{r} {\\frac{1}{2^{n/2}}\\frac{1}{\\pi^{n/2 + n(n - 1)\\beta/4}}e^{- ||X||\_{F}^{2}}} \\\\ \\end{array}$$  

where || ⋅ ||[*F*] represents the **Frobenius norm**,

  
$$\\begin{array}{r} {||X||\_{F}^{2} = {\\sum\\limits\_{i = 1}^{n}{\\sum\\limits\_{j = 1}^{n}|}}x\_{i,j}|^{2}.} \\\\ \\end{array}$$  

We now look at the importance of random matrices to a variety of applications.

## 7.6 Random Matrices and the Relationship to the Covariance

There are some particular random matrices of interest that we will explore in this section. We first define a real symmetric *m* × *m* random matrix

  
$$\\begin{array}{r} {M = XX^{T} = {\\sum\\limits\_{j = 1}^{n}X\_{j}}X\_{j}^{T}} \\\\ \\end{array}$$  

where *X* is a *m* × *n* random matrix, with columns *X*[*j*], 1 ≤ *j* ≤ *n*, are formed from independent samples of size *m* from i.i.d. random variables. The matrix *M* is called a **real Wishart matrix**. If these random variables are Gaussian each with mean 0 and covariance

  
$$\\begin{array}{r} {\\Sigma = {\\sum{(X - \\overline{X})}}{(X - \\overline{X})}^{T},} \\\\ \\end{array}$$  

then *M* is a **Gaussian Wishart matrix** and is denoted *W*[*p*](*n*, *Σ*), and has a probability distribution,

  
$$\\begin{array}{r} {f(M) = \\frac{1}{{(2\\pi)}^{mn/2}\\Gamma\_{p}(\\frac{n}{2})|\\Sigma|^{n/2}}|M|^{(n - p - 1)/2}e^{- \\frac{1}{2}Tr(\\Sigma^{- 1}M)}.} \\\\ \\end{array}$$  

Here *Γ*[*p*](*n*) is the multivariate gamma function.

  
$$\\begin{array}{r} {\\Gamma(x) = {\\int\_{0}^{\\infty}y^{x - 1}}e^{- y}dy.} \\\\ \\end{array}$$  

Notice that since *M* is symmetric, all of the eigenvalues, *λ*[1], *λ*[2], …, *λ*[*m*] of *M* are real.

In [Section 3.5](#chapter3.xhtml#sec3_5), we talked about the covariance and correlation matrices. Given a data set, *X*, the empirical covariance matrix can be found by finding

  
$$\\begin{array}{r} {XX^{T}.} \\\\ \\end{array}$$  

The empirical covariance matrix is different than the true, statistical, correlation matrix, *C*. If there are a large number of observation then, in fact, the empirical covariance matrix will be to the true covariance matrix.

## 7.7 CASE STUDY: Finance and Brownian Motion

In this case study, we will discuss how the covariance and correlation matrices relate to random matrices through a financial lens.

The unconditional probability distribution for any traded financial commodity (such as stocks, currencies, interest rates) is far from a Gaussian distribution. This unconditional probability distribution tends to follow a distribution similar to a **Rayleigh distribution** or more generally a **power law** distribution, called the **Tracy-Widom distribution**.

The general form of a Rayleigh probability density function is

  
$$\\begin{array}{r} {f(x) = \\frac{x}{\\sigma^{2}}e^{\\frac{- x^{2}}{2\\sigma^{2}}},\\, 0 \\leq x < \\infty,} \\\\ \\end{array}$$  

where $E(X) = \\sigma\\sqrt{\\frac{\\pi}{2}}$ and $Var(X) = \\left( \\frac{4 - \\pi}{2} \\right)\\sigma^{2}$.

Some examples of this probability distribution can be see in [Figure 7.8](#chapter7.xhtml#fig7_8).

![Figure 7.8 Examples of Rayleigh Distributions with different scaling factors.](images/fig7_8.jpg)

[Figure 7.8](#chapter7.xhtml#b7fig7_8) Examples of Rayleigh Distributions with different scaling factors.

The largest eigenvalue of a random Gaussian Ensemble matrix and its corresponding eigenvector can be interpreted as the collective response of the market to external factors, so it can be compared with the market index.

If *H* is a GUE random matrix, [Figure 7.9](#chapter7.xhtml#fig7_9) shows an example of what the distribution of maximum eigenvalues of *H* would look like.

![Figure 7.9 Distribution of maximum eigenvalues of a GUE matrix.](images/fig7_9.jpg)

[Figure 7.9](#chapter7.xhtml#b7fig7_9) Distribution of maximum eigenvalues of a GUE matrix.

Stocks have quite a bit of randomness in their volatility which can been seen in the three airline stock trends seen in [Figure 7.10](#chapter7.xhtml#fig7_10). [Table 7.1](#chapter7.xhtml#tbl7_1) shows a small subset of the data for these three airline stocks, where columns represent the trading days and rows for the different stocks. The stocks in this problem are correlated.

![Figure 7.10 American, Delta, and United Airline stock closing prices February 2013–February 2018.](images/fig7_10.jpg)

[Figure 7.10](#chapter7.xhtml#b7fig7_10) American, Delta, and United Airline stock closing prices February 2013–February 2018.

[Table 7.1](#chapter7.xhtml#b7tbl7_1) Sample of Closing Prices for Stocks (Feb 2013–Feb 2018).

  
| AAL || 14.75 || 14.46 || 14.27 || 14.66 || 13.99 || 14.5 |
| --- | --- | --- | --- | --- | --- | --- |
| ABBV || 36.25 || 35.85 || 35.42 || 35.27 || 36.57 || 37.58 |
| CBG || 24.19 || 24.13 || 24.26 || 24.5 || 24.7 || 24.28 |
| DAL || 14.62 || 14.69 || 14.5 || 14.78 || 14.24 || 14.45 |
| EQR || 55.44 || 56.46 || 57.49 || 57.65 || 57.56 || 57.51 |
| UAL || 26.31 || 26.51 || 25.89 || 26.19 || 25.87 || 26.37 |

We begin by manipulating the data in [Table 7.1](#chapter7.xhtml#tbl7_1), as we have done in other data sets throughout the text. Here we apply a logarithmic transformation of the daily returns, which can be seen in [Table 7.2](#chapter7.xhtml#tbl7_2).

[Table 7.2](#chapter7.xhtml#b7tbl7_2) Sample of Logarithmic Returns for Stocks (Feb 2013–Feb 2018).

  
| AAL || \-0.0198569 || \-0.0132268 || 0.0269633 || \-0.0467799 || 0.0358059 || \-0.0166902 |
| --- | --- | --- | --- | --- | --- | --- |
| ABBV || \-0.0110958 || \-0.0120669 || \-0.00424389 || 0.0361955 || 0.0272438 || 0.0161017 |
| CBG || \-0.00248344 || 0.00537302 || 0.00984421 || 0.00813013 || \-0.0171503 || 0.00902015 |
| DAL || 0.00477654 || \-0.0130183 || 0.0191263 || \-0.03722 || 0.0146395 || \-0.0104349 |
| EQR || 0.0182311 || 0.0180786 || 0.00277923 || \-0.00156236 || \-0.000869036 || 0.00121644 |
| UAL || 0.00757293 || \-0.0236652 || 0.0115209 || \-0.0122937 || 0.019143 || 0.0143075 |

First, we will calculate the **logarithmic returns** for consecutive trading days for each stock.

  
$$\\begin{array}{r} {\\log(return) = \\log\\left( \\frac{p\_{i}}{p\_{i - 1}} \\right),} \\\\ \\end{array}$$  

where *p*[*i*] represents the price index on trading day *i*. Then we normalize the trading data for each stock, subtracting the mean and dividing by the standard deviation.

![Figure 7.11 Logarithmic returns for American Airline stock February 2013–February 2018.](images/fig7_11.jpg)

Figure 7.11 Logarithmic returns for American Airline stock February 2013–February 2018.

In this case study, we will limit our study to small correlated data sets representing a 6 day period. A 6 × 6, *s**t**o**c**k* × *l**o**g*(*r**e**t**u**r**n*), matrix, *X*, can be defined from the data in [Table 7.2](#chapter7.xhtml#tbl7_2). Notice that this matrix uses the logarithmic returns of the 6 stocks over the first six day period, Day 1 through Day 6. A similar matrix can be created from Day 2 through Day 7 and in general in the stock price observations are taken for *M* days then the matrix will have *M* columns representing Day *i* through Day *i* + *M*.

For each *M* consecutive days, we can create the correlation matrix

  
$$\\begin{array}{r} {W = \\frac{XX^{T}}{M},} \\\\ \\end{array}$$  

and determine the eigenvalues of the correlation matrix *W*. Notice that *W* is a Wishart matrix.

[Figure 7.12](#chapter7.xhtml#fig7_12) shows the distribution of the largest eigenvalue of *W* using a larger dataset from the stocks in [Table 7.2](#chapter7.xhtml#tbl7_2) from February 2013 to February 2018, which can be found at Github link 48.

![Figure 7.12 Distribution of Largest Eigenvalues for the Correlation Matrix.](images/fig7_12.jpg)

[Figure 7.12](#chapter7.xhtml#b7fig7_12) Distribution of Largest Eigenvalues for the Correlation Matrix.

A covariance matrix relating the log returns over a 6 day period, can also help us understand the behaviors of stocks in Table 7.11.

We can also look at how the largest eigenvalues of *W* throughout time are related to the average covariance as well. Notice the behavior similarities in [Figure 7.13](#chapter7.xhtml#fig7_13).

![Figure 7.13 Average Covariance Vs Maximum Eigenvalue of Covariance Matrix.](images/fig7_13.jpg)

[Figure 7.13](#chapter7.xhtml#b7fig7_13) Average Covariance Vs Maximum Eigenvalue of Covariance Matrix.

In order to create a optimal portfolio, one might want to maximize the **Sharpe ratio** \[[38](#refbib.xhtml#refbib38)\],

  
$$\\begin{array}{r} {\\frac{\\text{Portfolio~return}}{\\text{Portfolio~risk}} = \\frac{W^{T}r(t)}{\\sqrt{W^{T}\\Sigma(t)W}},} \\\\ \\end{array}$$  

where *r*(*t*) is the expected returns for each asset and *Σ*(*t*) is the predicted covariance matrix for these returns. One might also wish to solely optimize the expected returns, *W*^(*T*)*r*(*t*).

[Figure 7.14](#chapter7.xhtml#fig7_14) shows where *W*^(*T*)*r*(*t*), and the Sharpe ratio, achieve their maximum throughout time. Notice that maximums occur roughly every 20 days.

![Figure 7.14 W^{T}r(t) throughout time.](images/fig7_14.jpg)

[Figure 7.14](#chapter7.xhtml#b7fig7_14) *W*^(*T*)*r*(*t*) throughout time.

Github links 44 and 46 provide Python and R syntax for this case study.

## 7.8 CASE STUDY: Random Matrices in Gene Interaction

In reality, genes do not act in isolation within the body but interact within a common cellular environment. This could be a dominant gene interaction, a complementary gene interaction, or a supplementary gene interaction. Scientists have known for some time that some genetic diseases result from mutations of a single gene. These diseases are called **monogenetic diseases**. **Multigenetic diseases** results from genetic mutations of more than one gene that interact with one another. This process is called **epistatis**. Knowledge about gene-gene interactions can give us a better understanding about hereditary diseases \[[29](#refbib.xhtml#refbib29)\].

There are many databases related to gene-gene interaction. For this case study, we use data from The Cancer Network Galaxy \[[5](#refbib.xhtml#refbib5)\], which focuses on gene-gene interaction related to cancer. The Cancer Network Galaxy has 256 data sets with 22,820 genes and their interactions represented. In this case study, we focus on one such data set focusing on mRNA expression of 131 cancer cell lines that can be found at Github link 49; however, a larger model incorporating multiple data sets is encouraged for future study.

[Figure 7.15](#chapter7.xhtml#fig7_15) shows a graphical depiction of a subgraph of interactions between genes in the dataset.

![Figure 7.15 Visualization of a small subset of gene-gene interactions in the Cancer Network Galaxy.](images/fig7_15.jpg)

[Figure 7.15](#chapter7.xhtml#b7fig7_15) Visualization of a small subset of gene-gene interactions in the Cancer Network Galaxy.

For this case study, assume that there are *n* genetic makers, *G*[1], *G*[2], …, *G*[*n*] measured on *m* subjects. In the provided data set there is an identified parent gene and child gene. A relationship matrix *M* is created such that if parent gene *G*[*i*] is related to child gene *G*[*j*] then *M*[*i*, *j*] = 1.

Otherwise *M*[*i*, *j*] = 0. Note that the matrix *M* is a sparse matrix with many entries equal to 0. Also notice that the matrix *M* may not be symmetric.

We define the sample correlation matrix

  
$$\\begin{array}{r} {W = \\frac{1}{n - 1}MM^{T}.} \\\\ \\end{array}$$  

In addition, if *λ*[*i*] and *λ*[*j*] are consecutive eigenvalues of *W*, [Figure 7.16](#chapter7.xhtml#fig7_16) shows the distribution of the spacing between consecutive eigenvalues.

![Figure 7.16 Distribution of Eigenvalue Spacing for the Gene-Gene Interaction Correlation Matrix.](images/fig7_16.jpg)

[Figure 7.16](#chapter7.xhtml#b7fig7_16) Distribution of Eigenvalue Spacing for the Gene-Gene Interaction Correlation Matrix.

Notice that the distribution seen in [Figure 7.16](#chapter7.xhtml#fig7_16) follows a Rayleigh distribution similar to that seen with the Wigner Surmise. One can also see that the distribution of the eigenvalues of the gene-gene interaction covariance matrix follows a more symmetric distribution in [Figure 7.17](#chapter7.xhtml#fig7_17). If more data from \[[5](#refbib.xhtml#refbib5)\] were integrated, we would begin to see Wigner's Semicircle Law displayed.

![Figure 7.17 Distribution of Eigenvalues of Gene-Gene Interaction Correlation Matrix.](images/fig7_17.jpg)

[Figure 7.17](#chapter7.xhtml#b7fig7_17) Distribution of Eigenvalues of Gene-Gene Interaction Correlation Matrix.

In order to further study gene-gene interaction relationship to random matrices, you may consult Github links 45 and 47 for Python and R coding suggestions.

## 7.9 Exercises

*   Find the condition number of $A = \\begin{pmatrix} {- 0.1} & {- 1} \\\\ 0 & 1 \\\\ \\end{pmatrix}$.
    
*   Verify that the Bauer-Fike Theorem holds for
    
      
    $$\\begin{array}{l} {A = \\left( \\begin{array}{ll} {4 + i} & 0 \\\\ {3 + i} & 1 \\\\ \\end{array} \\right)\\text{~and~}E = \\left( \\begin{array}{ll} {- 0.1} & 0.8 \\\\ {- 0.01} & 0 \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  
    
    Recall that $|a + bi| = \\sqrt{a^{2} + b^{2}}$.
    
*   (Coding) The following commands can be used to visualize the pseudospectrum of a matrix *A* using Python.
    
    import numpy as np
    
    import matplotlib.pyplot as plt
    
    from scipy.linalg import svdvals, schur
    
    Graph the pseudospectrum of
    
      
    $$\\begin{array}{l} {A = \\left( \\begin{array}{ll} {- 0.1} & {- 1} \\\\ 0 & 1 \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  
    
*   1.  If *H* is a 4 × 4 GOE find the probability distribution of the mean eigenvalues.
        
    2.  (Coding) Write code to generate 10000 4 × 4 GOE matrices and calculate the mean of the eigenvalues of each GOE. Use these values to plot the probability distribution of the mean eigenvalues and compare it to your answer in part a.
        
*   Determine which of the follow matrices are Hermitian.
    
    1.  $\\begin{pmatrix} {4 - 2i} & {- 8 + 12i} \\\\ {- 8 + 12i} & {36 - 16i} \\\\ \\end{pmatrix}$
        
    2.  $\\begin{pmatrix} 1 & {1 + i} \\\\ {1 - i} & 1 \\\\ \\end{pmatrix}$
        
    3.  $\\begin{pmatrix} 1 & 2 \\\\ 2 & 3 \\\\ \\end{pmatrix}$
        
*   Let $A = \\begin{pmatrix} \\frac{1 + i}{2} & {- \\frac{1 + i}{2}} \\\\ & \\\\ {\\,\\frac{1}{\\sqrt{2}}} & \\frac{1}{\\sqrt{2}} \\\\ \\end{pmatrix}$. Determine if *A* is a unitary matrix.
    
*   (Coding) Using either Python or R, generate a population of *N* = 100 people that have all the same initial value *V* = 1000. Write a loop, where the time step represents trading periods, and keep track of each person's value under the following conditions.
    
    1.  Random trading with one person at each time step, total value between the two traders is shared equally between the traders.
        
    2.  Random trading with one person at each time step, total value between the two traders is shared where the percent split is also generated randomly.
        
    3.  Each person is given a random initial value between *V* = 100 and *V* = 1000. Random trading with one person at each step. The person of greater value gets 75% of the total value between the two traders and the lesser get 25%.
        
    4.  Create a probability histogram representing the values of the population members in parts a. through c. and estimate the distribution for each part.
        
    5.  For part c., create a matrix, *M*, where the rows represent the population members and the columns represent the individual values throughout time. Use your matrix *M* to create a correlation matrix.
        
    6.  Create a probability histogram representing the eigenvalues of the correlation matrix in part e. and estimate the distribution.
        
*   (Coding) Create code in Python or R to generate the average condition number of a 2 × 2 GOE matrix, *A*, and the average error in a system *A**x* = *b*.
    

# 8Sample Solutions to Exercises

DOI: [10.1201/9781003025672-8](https://doi.org/10.1201/9781003025672-8)

## 8.1 Chapter 1

*   1.  ${\\sum\\limits\_{j = 2}^{6}A\_{1,j}} = 2$
        
    2.  *A*[1, *j*]² ≠ 0 for *i* = 2, 3, 4, 5, 6 so Kush has connections with all of the other 5 in 2 steps.
        
    3.  *A*[1, 2] + *A*[1, 2]² = 2
        
    
*   $\\rho(A) = 1 + \\sqrt{2}.$
    
*   The graph is not a simple connected graph since it contains a loop.
    
    ![](images/ufig8_1.jpg)
*   1.  $A = \\begin{pmatrix} 0 & 1 & 0 & 0 & 0 & 0 & 1 & 1 & 0 & 0 \\\\ 1 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 0 & 1 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 0 & 0 & 1 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\\\ 0 & 0 & 0 & 1 & 0 & 1 & 0 & 0 & 0 & 0 \\\\ 0 & 0 & 0 & 0 & 1 & 0 & 1 & 0 & 0 & 0 \\\\ 1 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\\\ 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 1 \\\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 1 \\\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 1 & 0 \\\\ \\end{pmatrix}$
        
    2.  $L = \\begin{pmatrix} 3 & {- 1} & 0 & 0 & 0 & 0 & {- 1} & {- 1} & 0 & 0 \\\\ {- 1} & 2 & {- 1} & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 0 & {- 1} & 2 & {- 1} & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 0 & 0 & {- 1} & 2 & {- 1} & 0 & 0 & 0 & 0 & 0 \\\\ 0 & 0 & 0 & {- 1} & 2 & {- 1} & 0 & 0 & 0 & 0 \\\\ 0 & 0 & 0 & 0 & {- 1} & 2 & {- 1} & 0 & 0 & 0 \\\\ {- 1} & 0 & 0 & 0 & 0 & {- 1} & 2 & 0 & 0 & 0 \\\\ {- 1} & 0 & 0 & 0 & 0 & 0 & 0 & 3 & {- 1} & {- 1} \\\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & {- 1} & 2 & {- 1} \\\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & {- 1} & {- 1} & 2 \\\\ \\end{pmatrix}$
        
    3.  The Fiedler value is 0.0.237487 and the unit Fiedler vector is
        
          
        $$\\begin{aligned} & \\left\\{ 0.05213, - 0.1147, - 0.2543, - 0.3335, - 0.3335, - 0.2543, \\right. \\\\ & {\\left. \\text{\\quad\\quad} - 0.1147,0.3734,0.4898,0.4898 \\right\\}.} \\\\ \\end{aligned}$$  
        
    4.  Using the Fiedler vector from part c, we can cluster the vertices into two subgroups *V*[1] = {2,3,4,5,6,7} and *V*[2] = {1,8,9,10}.
        
    
*   If *V*[2] = {1,8,9,10} and *V*[1] = {2,3,4,5,6,7} the number of cut edges is 2 and $\\theta(V\_{2}) = \\frac{2}{4 \\cdot 6}$; however, if *V*[2] = {8,9,10} and *V*[1] = {1,2,3,4,5,6,7} then the number of cuts is 1 and $\\theta(V\_{2}) = \\frac{1}{3 \\cdot 7}$. Thus the isoperimetric ratio is $\\theta(G) = \\frac{1}{21}$.
    
*   1.  $A = \\begin{pmatrix} 0 & 1 & 1 & 0 & 1 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 1 & 0 & 1 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 1 & 1 & 0 & 0 & 1 & 1 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 1 & 1 & 1 & 0 & 0 & 0 & 1 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 1 & 0 & 1 & 1 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 0 & 0 & 1 & 0 & 1 & 0 & 0 & 0 & 1 & 1 & 1 & 0 & 1 & 1 & 0 \\\\ 0 & 0 & 0 & 0 & 1 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 1 & 0 & 1 & 0 & 0 \\\\ 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 & 1 & 1 & 0 \\\\ 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 1 & 0 & 0 & 0 & 1 & 0 & 1 \\\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 1 & 1 \\\\ 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 1 & 1 & 1 & 1 & 0 & 1 & 0 \\\\ 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 & 1 & 0 & 1 & 1 & 0 & 1 \\\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 1 & 0 & 1 & 0 \\\\ \\end{pmatrix}.$
        
    2.  Calculating *I* + *A* + *A*² we can see that no marmot is connected to every other marmot directly or through a two step relationship, however, this calculation shows that marmot 7 is related to every other marmot except for marmot 4 either directly or through a two step relationship. Adding three step relationships allows for marmot 7 to be related to every other marmot in the madness.
        
    3.  $L = \\begin{pmatrix} 4 & {- 1} & {- 1} & 0 & {- 1} & {- 1} & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ {- 1} & 3 & {- 1} & 0 & {- 1} & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ {- 1} & {- 1} & 5 & 0 & {- 1} & {- 1} & {- 1} & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 0 & 0 & 0 & 1 & 0 & {- 1} & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ {- 1} & {- 1} & {- 1} & 0 & 5 & 0 & {- 1} & {- 1} & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ {- 1} & 0 & {- 1} & {- 1} & 0 & 4 & 0 & {- 1} & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 0 & 0 & {- 1} & 0 & {- 1} & 0 & 7 & 0 & {- 1} & {- 1} & {- 1} & 0 & {- 1} & {- 1} & 0 \\\\ 0 & 0 & 0 & 0 & {- 1} & {- 1} & 0 & 2 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 0 & 0 & 0 & 0 & 0 & 0 & {- 1} & 0 & 3 & 0 & {- 1} & 0 & {- 1} & 0 & 0 \\\\ 0 & 0 & 0 & 0 & 0 & 0 & {- 1} & 0 & 0 & 3 & 0 & 0 & {- 1} & {- 1} & 0 \\\\ 0 & 0 & 0 & 0 & 0 & 0 & {- 1} & 0 & {- 1} & 0 & 4 & 0 & {- 1} & 0 & {- 1} \\\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 3 & {- 1} & {- 1} & {- 1} \\\\ 0 & 0 & 0 & 0 & 0 & 0 & {- 1} & 0 & {- 1} & {- 1} & {- 1} & {- 1} & 6 & {- 1} & 0 \\\\ 0 & 0 & 0 & 0 & 0 & 0 & {- 1} & 0 & 0 & {- 1} & 0 & {- 1} & {- 1} & 5 & {- 1} \\\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & {- 1} & {- 1} & 0 & {- 1} & 3 \\\\ \\end{pmatrix}.$
        
    4.  If *V*[1] = {*v*[1],*v*[2],*v*[3],*v*[5],*v*[6],*v*[7]} then the number of graph cuts is 8 and the isometric ratio is $\\frac{4}{27}$.
        
    5.  A unit Fiedler vector is approximately {−0.237,−0.216,−0.173,−0.459,−0.169,−0.314,0.122,−0.287,0.22,0.225,0.234,0.286,0.235,0.246,0.285}.
        
    6.  Using the result from part d., a cluster of marmots would be *V*[1] = {*v*[1],*v*[2],*v*[3],*v*[4],*v*[5],*v*[6],*v*[8]} and *V*[2] = {*v*[7],*v*[9],*v*[10],*v*[11],*v*[12],*v*[13],*v*[14],*v*[15]}.
        
    7.  Using *V*[1] and *V*[2] from part e., we further divide these sets of vertices into subsets using similar analysis. The adjacency matrices associated with *V*[1] and *V*[2] respectively are
        
          
        $$\\begin{array}{l} {A\_{1} = \\left( \\begin{array}{lllllll} 0 & 1 & 1 & 0 & 1 & 1 & 0 \\\\ 1 & 0 & 1 & 0 & 1 & 0 & 0 \\\\ 1 & 1 & 0 & 0 & 1 & 1 & 0 \\\\ 0 & 0 & 0 & 0 & 0 & 1 & 0 \\\\ 1 & 1 & 1 & 0 & 0 & 0 & 1 \\\\ 1 & 0 & 1 & 1 & 0 & 0 & 1 \\\\ 0 & 0 & 0 & 0 & 1 & 1 & 0 \\\\ \\end{array} \\right)} \\\\ \\end{array}$$  
        
          
        $$\\begin{array}{l} {\\text{and~}A\_{2} = \\left( \\begin{array}{llllllll} 0 & 1 & 1 & 1 & 0 & 1 & 1 & 0 \\\\ 1 & 0 & 0 & 1 & 0 & 1 & 0 & 0 \\\\ 1 & 0 & 0 & 0 & 0 & 1 & 1 & 0 \\\\ 1 & 1 & 0 & 0 & 0 & 1 & 0 & 1 \\\\ 0 & 0 & 0 & 0 & 0 & 1 & 1 & 1 \\\\ 1 & 1 & 1 & 1 & 1 & 0 & 1 & 0 \\\\ 1 & 0 & 1 & 0 & 1 & 1 & 0 & 1 \\\\ 0 & 0 & 0 & 1 & 1 & 0 & 1 & 0 \\\\ \\end{array} \\right)} \\\\ \\end{array}$$  
        
        with row/column 7 of *A*[1] representing marmot 8 and row/column 1 of *A*[2] representing marmot 7. Finding the Fiedler vector for each of the Laplacian matrices associated with *A*[1] and *A*[2] yield a clustering of
        
          
        $$\\begin{array}{r} {\\left\\{ v\_{1},v\_{2},v\_{3},v\_{5},v\_{8} \\right\\},\\left\\{ v\_{4},v\_{5} \\right\\},\\left\\{ v\_{7},v\_{9},v\_{10},v\_{11},v\_{13} \\right\\},\\left\\{ v\_{12},v\_{14},v\_{15} \\right\\}.} \\\\ \\end{array}$$  
        
    
*   With more knowledge about the marmot interactions, the graph may be a directed graph related to the direction of dominance or could be a weighted graph where the weights are representative of the number of interactions or dominant behaviors that took place.
    
*   1.  $L = \\begin{pmatrix} 29 & {- 10} & {- 3} & 0 & {- 6} & {- 10} & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ {- 10} & 20 & {- 6} & 0 & {- 4} & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ {- 3} & {- 6} & 40 & 0 & {- 3} & {- 15} & {- 13} & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 0 & 0 & 0 & 13 & 0 & {- 13} & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ {- 6} & {- 4} & {- 3} & 0 & 21 & 0 & {- 1} & {- 7} & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ {- 10} & 0 & {- 15} & {- 13} & 0 & 51 & 0 & {- 13} & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 0 & 0 & {- 13} & 0 & {- 1} & 0 & 43 & 0 & {- 5} & {- 5} & {- 5} & 0 & {- 9} & {- 5} & 0 \\\\ 0 & 0 & 0 & 0 & {- 7} & {- 13} & 0 & 20 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\\\ 0 & 0 & 0 & 0 & 0 & 0 & {- 5} & 0 & 24 & 0 & {- 11} & 0 & {- 8} & 0 & 0 \\\\ 0 & 0 & 0 & 0 & 0 & 0 & {- 5} & 0 & 0 & 14 & 0 & 0 & {- 6} & {- 3} & 0 \\\\ 0 & 0 & 0 & 0 & 0 & 0 & {- 5} & 0 & {- 11} & 0 & 37 & 0 & {- 11} & 0 & {- 10} \\\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 42 & {- 15} & {- 12} & {- 15} \\\\ 0 & 0 & 0 & 0 & 0 & 0 & {- 9} & 0 & {- 8} & {- 6} & {- 11} & {- 15} & 59 & {- 10} & 0 \\\\ 0 & 0 & 0 & 0 & 0 & 0 & {- 5} & 0 & 0 & {- 3} & 0 & {- 12} & {- 10} & 44 & {- 14} \\\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & {- 10} & {- 15} & 0 & {- 14} & 39 \\\\ \\end{pmatrix}$.
        
    2.  The Fiedler value is 2.38721 and a unit Fiedler vector is approximately {−0.27,−0.26,−0.2,−0.35,−0.18,−0.29,−0.02,−0.29,0.28,0.28,0.27,0.27,0.23,0.25,0.28}.
        
    3.  Based on the Fiedler vector, two clusters could be *V*[1] = {*v*[1],*v*[2],*v*[3],*v*[4],*v*[5],*v*[6],*v*[7],*v*[8]} and *V*[2] = {*v*[9],*v*[10],*v*[11],*v*[12],*v*[13],*v*[14],*v*[15]}.
        
    
*   1.  *S* = {−0.333,−1.,1.,−0.19,0.231,−0.487}.
        
    2.  With ranking vector {−0.626,−2.678,1.553,−0.484,0.451,−0.744}, marmot 12 is most dominant, with marmot 14 being 2^(nd) and marmot 10, 3^(rd).
        
    3.  With ranking vector {−0.993,−4.905,1.777,−1.974,0.381,−1.905}, marmot 12 is most dominant, with marmot 14 being 2^(nd) and marmot 10, 3^(rd).
        
    
*   1.  If *A* is the binary *s**t**o**r**y* × *a**t**t**r**i**b**u**t**e* matrix. The gramian matrix *S* = *A**A*^(*T*).
        
    2.  A (1, 1) entry of 3 shows that story 1 has 3 attributes present. A (1, 2) entry of 1 says that stories 1 and 2 share 1 attribute in common.
        
    3.  *V*[1] = {1,3,4,5,6,7,8,15,16,17,18,19,20,21,22,23,24,26,31} and *V*[2] = {2,9,10,11,12,13,14,25,27,28,29,30}
        
    
*   For *n* = 4 the ranking is (FL, GA, TN, SC, KY, MIZ, VAN) and for *n* = 5 the ranking is (FL, TN, SC, KY, GA, VAN, MIZ)
    

## 8.2 Chapter 2

*   *A*[1] is primitive and *A*[2] is neither primitive nor irreducible.
    
*   With transition matrix
    
      
    $$\\begin{array}{l} {T = \\left( \\begin{array}{lll} .8 & 0 & .25 \\\\ .1 & .7 & .25 \\\\ .1 & .3 & .5 \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  
    
    In the long run, 35.7% are at Duke, 35.7% are at UNC and 28.6% are at NC State.
    
*   *P*(*D**u**k**e*|*D**u**r**h**a**m*)
    
    $= \\frac{P(Durham|Duke)P(Duke)}{P(Durham|Duke)P(Duke) + P(Durham|UNC)P(UNC) + P(Durham|NCState)P(NCState)}$
    
    $= \\frac{.4\*.5}{.4\*.5 + .1\*.2 + .2\*.3} \\approx .71$
    
*   $T = \\begin{pmatrix} .75 & 0 & .7 \\\\ .25 & .8 & 0 \\\\ 0 & .2 & .3 \\\\ \\end{pmatrix}$ and $E = \\begin{pmatrix} .4 & .5 & .1 \\\\ \\end{pmatrix}$.
    
    1.  *P*(*O*[1] = *S**a**d*) = 0.2955
        
    2.  *P*(*O*[1] = *S**a**d*, *O*[2] = *S**a**d*) = 0.10275
        
    3.  *P*(*O*[1] = *S**a**d*, *O*[2] = *S**a**d*, *O*[3] = *H**a**p**p**y*) = 0.0646725
        
    4.  $\\frac{.0261}{P(\\left\\{ Sad,\\, Sad,\\, Happy \\right\\})} = 0.403572$
        
    5.  {*B**u**l**l*,*B**u**l**l*,*B**u**l**l*}
        
    
*   ![Figure 8.1 Recursive decisions in a Viterbi Algorithm Matrix for Exercise 5.](images/fig8_1.jpg)
    
    Figure 8.1 Recursive decisions in a Viterbi Algorithm Matrix for Exercise 5.
    
*   From [Example 2.16](#chapter2.xhtml#exam2_16), *π* = {.91,.09} and
    
      
    $$\\begin{array}{l} {T = \\left( \\begin{array}{ll} 0.74914 & 0.52723 \\\\ 0.25086 & 0.47277 \\\\ \\end{array} \\right),E = \\left( \\begin{array}{ll} 0.678328 & 0.3725 \\\\ 0.321672 & 0.6275 \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  
    
    So
    
     
    | *α*(*H*[1]) = {0.6170,0.0337} || *β*(*H*[1]) = {0.0649,0.0527} |
    | --- | --- |
    | *α*(*H*[2]) = {0.1544,0.1071} || *β*(*H*[2]) = {0.2303,0.0555} |
    | --- | --- |
    | *α*(*H*[3]) = {0.1168,0.0333} || *β*(*H*[3]) = {0.3692,0.1193} |
    | *α*(*H*[4]) = {0.0713,0.0168} || *β*(*H*[4]) = {0.3984,0.4663} |
    | *α*(*H*[5]) = {0.02,0.0162} || *β*(*H*[5]) = {1,1} |
    
    and the new model is *λ* with *π*^(*n**e**w*) = {0.957557,0.0424426}
    
      
    $$\\begin{array}{l} {T^{new} = \\left( \\begin{array}{ll} 0.730663 & 1.11403 \\\\ 0.17552 & 0.563931 \\\\ \\end{array} \\right),E^{new} = \\left( \\begin{array}{ll} 0.653434 & 0.367311 \\\\ 0.346566 & 0.632689 \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  
    
*   *α*(*H*[1]) = {0.1,0.05625,0.1,0.063}, *α*(*H*[2]) = {0.0271,0.0093,0.0189, 0.0297}, and *α*(*H*[3]) = {0.0042,0.0051,0.0032,0.0043}. *P*(*O*|*λ*) = 0.017
    
*   *γ*(*H*[1]) = {0.3633,0.0846,0.29,0.2622}, *γ*(*H*[2]) = {0.3145,0.121, 0.2067,0.3578} and *γ*(*H*[3]) = {0.25,0.3036,0.1905,0.256}. So the most likely hidden sequence is **ATC**.
    

## 8.3 Chapter 3

*   1.  The transformed vectors will be {1,2} and {3,4}. These vectors are not orthogonal.
        
    2.  *θ* ≈ 0.9569 ± 2*π**n*, 2.5277 ± 2*π**n*, 4.0985 ± 2*π**n*, 5.6693 ± 2*π**n*, for *n* ∈ **Z**.
        
    3.  Using *θ* = 0.9569, *u*[1] = {2.21088,4.99781} and *u*[2] = {0.334681,−0.148053}. The singular values are *σ*[1] = ||*u*[1]|| = 5.46499 and *σ*[2] = ||*u*[2]|| = 0.365966.
        
    4.  $AA^{T} = \\begin{pmatrix} 5 & 11 \\\\ 11 & 25 \\\\ \\end{pmatrix}$ has eigenvalues $15 \\pm \\sqrt{221}$. Thus the singular values of *A* are $\\sqrt{15 \\pm \\sqrt{221}}$.
        
    
*   The singular values are 2 and 5.
    
*   The singular values and eigenvalues are 6.0216, 2.69854, and 0.676943.
    
*   The singular values of *A* are the square root of the eigenvalues of *A*^(*T*)*A*. Let *λ* be an eigenvalue of *A*, then *λ* is also an eigenvalue of *A*^(*T*). If *v* is the eigenvector corresponding to eigenvalue *λ*, then *A*^(*T*)*A**x* = *λ**A*^(*T*)*x* = *λ*²*x*. Thus *λ* is a singular value of *A*.
    
*   1.    
        $$\\begin{array}{l} {U = \\left( \\begin{array}{ll} 0.476971 & {- 0.34947} \\\\ 0.187933 & {- 0.548739} \\\\ 0.389186 & 0.476451 \\\\ 0.281154 & {- 0.48811} \\\\ 0.533879 & 0.153706 \\\\ 0.470786 & 0.296436 \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  
        
        A graph would use the rows of *U* and the (*x*, *y*) point for each type of dog.
        
    2.  Breed 4 is closest to Carl's dog.
        
    
*   1.  If the data is normalized, PCA on the covariance matrix produces the model
        
          
        $$\\begin{aligned} \\frac{\\hat{population} - 9199.86}{2619.25} & {= - 0.707107\\frac{hectares - (5.28422\*10^{6})}{718594}} \\\\ & {\\quad + 0.707107} \\\\ \\end{aligned}$$  
        
        or
        
          
        $$\\begin{array}{r} {\\hat{population} = - 0.00257738(hectares) + 24671.4.} \\\\ \\end{array}$$  
        
    
*   See GitHub links 19 and 21.
    
*   Notice that there are really three distinct clusters in [Figure 8.2](#chapter8.xhtml#fig8_2) of stories based on the attributes that are present.
    
*   1.  [Figure 8.3](#chapter8.xhtml#fig8_3)
        
    2.  William  & Mary
        
    3.  University of Richmond
        
    4.    
        $$\\begin{array}{l} {S\_{w} = \\left( \\begin{array}{ll} 26.9399 & 1.15269 \\\\ 1.15269 & 4.27101 \\\\ \\end{array} \\right),S\_{b} = \\left( \\begin{array}{ll} 0.372925 & {- 0.461075} \\\\ {- 0.461075} & 0.570062 \\\\ \\end{array} \\right)} \\\\ \\end{array}$$  
        
    5.  {−0.0305852,0.185033}
        
    
    ![Figure 8.2 Visualization for Exercise 8 (Chapter 3).](images/fig8_2.jpg)
    
    [Figure 8.2](#chapter8.xhtml#b8fig8_2) Visualization for Exercise 8 ([Chapter 3](#chapter3.xhtml)).
    
    ![Figure 8.3 Visualization for Exercise 9a (Chapter 3).](images/fig8_3.jpg)
    
    [Figure 8.3](#chapter8.xhtml#b8fig8_3) Visualization for Exercise 9a ([Chapter 3](#chapter3.xhtml)).
    

## 8.4 Chapter 4

*   1. *f̂*(*x*) = 11255.1 − 957.206*x* + 29.7221*x*² − 0.396603*x*³ + 0.00191023*x*⁴
    
*   2. $P\_{4}(x) = \\frac{- 168x^{4} + 5321x^{3} - 54372x^{2} + 208279x - 205260}{9240}$
    
*   3. $P\_{5}(x) = \\frac{1}{120}( - 51522x^{5} + 897185x^{4} - 5520160x^{3} + 14609515x^{2} - 9915458x$  + 7828080)
    
*   4. *T*[4](*x*) = 1 − 8*x*² + 8*x*⁴ and *T*[5](*x*) = 5*x* − 20*x*³ + 16*x*⁵.
    
      
    $$\\begin{array}{r} {{\\int\_{- 1}^{1}{(1 - x^{2})}^{- 1/2}}T\_{4}(x)T\_{5}(x) = 0.} \\\\ \\end{array}$$  
    
*   5. *U*[3](*x*) = *x*³ − 2*x* and $\\begin{array}{l} {U\_{4}(x) = 1 - 3x^{2} + x^{4}.} \\\\ {\\int\_{- 1}^{1}(^{1 - x^{2}) - 1/2}U\_{3}(x)U\_{4}(x)dx = 0.} \\\\ \\end{array}$
    
*   6. ∫[ − ∞]^∞(2*x*)(4*x*² − 2)*e*^( − *x*²/2)*d**x* = 0
    
*   7. $L = \\begin{pmatrix} 1 & 0 & 0 \\\\ 1 & 1 & 0 \\\\ 1 & {- 2} & 1 \\\\ \\end{pmatrix},U = \\begin{pmatrix} 1 & 1 & 2 \\\\ 0 & 1 & 3 \\\\ 0 & 0 & 7 \\\\ \\end{pmatrix}$
    
*   8. 
    1.  $\\begin{pmatrix} 1 & 1 & 1 & 1 & 1 & 1 \\\\ 1 & 2 & 4 & 8 & 16 & 32 \\\\ 1 & 3 & 9 & 27 & 81 & 243 \\\\ 1 & 4 & 16 & 64 & 256 & 1024 \\\\ 1 & 5 & 25 & 125 & 625 & 3125 \\\\ 1 & 6 & 36 & 216 & 1296 & 7776 \\\\ \\end{pmatrix}$
        
    2.  $L = \\begin{pmatrix} 1 & 0 & 0 & 0 & 0 & 0 \\\\ 1 & 1 & 0 & 0 & 0 & 0 \\\\ 1 & 2 & 1 & 0 & 0 & 0 \\\\ 1 & 3 & 3 & 1 & 0 & 0 \\\\ 1 & 4 & 6 & 4 & 1 & 0 \\\\ 1 & 5 & 10 & 10 & 5 & 1 \\\\ \\end{pmatrix},U = \\begin{pmatrix} 1 & 1 & 1 & 1 & 1 & 1 \\\\ 0 & 1 & 3 & 7 & 15 & 31 \\\\ 0 & 0 & 2 & 12 & 50 & 180 \\\\ 0 & 0 & 0 & 6 & 60 & 390 \\\\ 0 & 0 & 0 & 0 & 24 & 360 \\\\ 0 & 0 & 0 & 0 & 0 & 120 \\\\ \\end{pmatrix}.$
        
    3.  $\\left\\{ {65397,59438, - 5990,\\frac{2569}{3},\\frac{24871}{24}, - \\frac{8587}{20}} \\right\\}$
        
    4.  $\\frac{1}{120}( - 51522x^{5} + 897185x^{4} - 5520160x^{3} + 14609515x^{2} - 9915458x$  + 7828080)
        
*   10. 
    1.  If *t* = 0 in year 2016, then
        
          
        $$\\begin{array}{r} {\\hat{f(x)} = - \\frac{24201x^{3}}{4} + \\frac{300931x^{2}}{7} - \\frac{1910463x}{28} + \\frac{8909809}{70}.} \\\\ \\end{array}$$  
        
    2.  Approximate derivatives
        
          
        $$\\begin{aligned} & \\left\\{ \\left\\{ 2016, - 18436 \\right\\},\\left\\{ 2017, - 18436 \\right\\},\\left\\{ 2018, - 7322 \\right\\},\\left\\{ 2019,57475 \\right\\}, \\right. \\\\ & {\\left\\{ 2020, - 4014 \\right\\}\\}.} \\\\ \\end{aligned}$$  
        

## 8.5 Chapter 5

*     
    $$\\begin{array}{l} \\left( \\begin{array}{lll} {2x\_{1}} & 1 & 0 \\\\ 0 & {8x\_{2}} & {3x\_{3}^{2}} \\\\ \\end{array} \\right) \\\\ \\end{array}$$  
    
*   ∇*f* = {*y*cos(*x**y*+*y*²*z*),(*x*+2*y**z*)cos(*x**y*+*y*²*z*),*y*²cos(*x**y*+*y*²*z*)}
    
      
    $$\\begin{aligned} \\frac{\\partial^{2}f}{\\partial x^{2}} & {= - y^{2}\\sin(xy + y^{2}z)} \\\\ \\frac{\\partial^{2}f}{\\partial y^{2}} & {= 2z\\cos(xy + y^{2}z) - {(x + 2yz)}^{2}\\sin(xy + y^{2}z)} \\\\ \\frac{\\partial^{2}f}{\\partial z^{2}} & {= - y^{4}\\sin(xy + y^{2}z)} \\\\ \\frac{\\partial^{2}f}{\\partial y\\partial x} & {= \\frac{\\partial^{2}f}{\\partial x\\partial y} = \\cos(xy + y^{2}z) - y(x + 2yz)\\sin(xy + y^{2}z)} \\\\ \\frac{\\partial^{2}f}{\\partial y\\partial z} & {= \\frac{\\partial^{2}f}{\\partial z\\partial y} = 2y\\cos(xy + y^{2}z) - y^{2}(x + 2yz)\\sin(xy + y^{2}z)} \\\\ \\frac{\\partial^{2}f}{\\partial z\\partial x} & {= \\frac{\\partial^{2}f}{\\partial x\\partial z} = - y^{3}\\sin(xy + y^{2}z)} \\\\ \\end{aligned}$$  
    
*   ∇*f* = {8*x*[1]+6*x*[2]³,18*x*[1]*x*[2]²}.
    
*   *d*(*l**n*(|*X*|) = *t**r*(*X*^( − 1)*d**X*)
    
*   *d**X*^(*T*) = (*d**X*)^(*T*)
    
*   1.    
        $$\\begin{array}{r} {LL = {\\sum\\limits\_{i = 1}^{n}l}og(y\_{i} - (a\_{0} + a\_{1}x\_{i})) - log(24) - \\frac{{(y\_{i} - (a\_{0} + a\_{1}x\_{i}))}^{2}}{2}} \\\\ \\end{array}$$  
        
    2.    
        $$\\begin{array}{r} {\\frac{\\partial LL}{\\partial a\_{0}} = {\\sum\\limits\_{i = 1}^{n}\\frac{- 1}{y\_{i} - (a\_{0} + a\_{1}x\_{i})}} - (y\_{i} - (a\_{0} + a\_{1}x\_{i}))} \\\\ \\end{array}$$  
        
    3.    
        $$\\begin{array}{r} {\\frac{\\partial LL}{\\partial a\_{1}} = {\\sum\\limits\_{i = 1}^{n}\\frac{- x\_{i}}{y\_{i} - (a\_{0} + a\_{1}x\_{i})}} - x\_{i}(y\_{i} - (a\_{0} + a\_{1}x\_{i}))} \\\\ \\end{array}$$  
        
    
*   Since *XA* not necessarily invertible, we create (*X**A*)^(*T*)(*X**A*),
    
      
    $$\\begin{array}{r} {\\frac{\\partial f}{\\partial a\_{0}} = {(XA)}^{T}{({(XA)}^{T}(XA))}^{- 1}Y.} \\\\ \\end{array}$$  
    
*     
    $$\\begin{array}{l} {\\frac{\\partial|a\_{0} + a\_{1}x\_{i} - y\_{1}|}{\\partial a\_{0}} = \\left\\{ \\begin{array}{ll} 1 & {\\text{~if~}a\_{0} + a\_{1}x\_{i} \\geq 0,} \\\\ {- 1} & {\\text{~if~}a\_{0} + a\_{1}x\_{i} < 0.} \\\\ \\end{array}~ \\right.} \\\\ \\end{array}$$  
    
      
    $$\\begin{array}{l} {\\frac{\\partial|a\_{0} + a\_{1}x\_{i} - y\_{1}|}{\\partial a\_{1}} = \\left\\{ \\begin{array}{ll} x\_{i} & {\\text{~if~}a\_{0} + a\_{1}x\_{i} \\geq 0,} \\\\ {- x\_{i}} & {\\text{~if~}a\_{0} + a\_{1}x\_{i} < 0.} \\\\ \\end{array}~ \\right.} \\\\ \\end{array}$$  
    
*   1.  See [Table 8.1](#chapter8.xhtml#tbl8_1).
        
        [Table 8.1](#chapter8.xhtml#b8tbl8_1) Gradient descent table for Exercise 9a ([Chapter 5](#chapter5.xhtml)).
        
          
        | *y*[*i*] || $\\hat{y\_{i}} = a\_{0} + a\_{1}x\_{i}$ || $\\frac{\\partial L}{\\partial a\_{0}}$ || $\\frac{\\partial L}{\\partial a\_{1}}$ |
        | --- | --- | --- | --- |
        | 3 || 5.5 || 1 || \-1 |
        | --- | --- | --- | --- |
        | \-4 || 5 || 1 || 0 |
        | 5 || 4.5 || \-1 || \-1 |
        | 2 || 4 || 1 || \-6 |
        | Total ||  || 2 || \-8 |
        
    2.  *a*[0] = 5 − .03(2) = 4.94, *a*[1] =  − .5 − .03(8) =  − .74.
        
    
*   See [Table 8.2](#chapter8.xhtml#tbl8_2). With a learning rate of. 03, *a*[0] = 0 − .03( − 2) = .06, *a*[1] = 0 − .03( − 2) = .06.
    
    [Table 8.2](#chapter8.xhtml#b8tbl8_2) Gradient descent table for Exercise 9b ([Chapter 5](#chapter5.xhtml)).
    
      
    | *y*[*i*] || $\\hat{y\_{i}} = a\_{0} + a\_{1}x\_{i}$ || $\\frac{\\partial L}{\\partial a\_{0}}$ || $\\frac{\\partial L}{\\partial a\_{1}}$ |
    | --- | --- | --- | --- |
    | 3 || 0 || \-1 || 1 |
    | --- | --- | --- | --- |
    | \-4 || 0 || 1 || 0 |
    | 5 || 0 || \-1 || \-1 |
    | 2 || 0 || \-1 || \-2 |
    | Total ||  || \-2 || \-2 |
    
*   1.  *S**S**E* = 500783828
        
    2.  Using the quadratic interpolating function, we get gradient [Table 8.3](#chapter8.xhtml#tbl8_3).
        
         
        
        [Table 8.3](#chapter8.xhtml#b8tbl8_3) Gradient descent table for Exercise 11b ([Chapter 5](#chapter5.xhtml)).
        
         
        | *   With a learning rate of $r = .0003,\\hat{f(x)} = 39991.1 + 29961.x + 3808.73x^{2}$ and *S**S**E* = 4.63776 × 10⁸
            
        *   $\\hat{y} = \\frac{9}{5} + \\frac{3}{10}x$
            
        *   1.  $\\frac{1}{1 + e^{- XW}} = \\frac{1}{1 + e^{.1 + .9x}}$
                
            2.  *S**S**E* = 0.462321
                
            3.  Gradients are {0.424522,0.155872}, *W*^((1)) = {0.0872644,0.895324} and *S**S**E* = 0.456202.
                
            4.  *R**e**L**U*(*X**W*) = *X**W* = {0.1,1.,1.9} since all values *XW* are positive.
                
            5.  *S**S**E* = 1.5
                
            6.  Gradients are {3.6,5.4} and *W* = {0.064,0.846}.
                
            
        
        ## 8.6 Chapter 6
        
        *   1.  *e**n**t**r**o**p**y* ≈ .52, $IG = 1 - \\frac{7}{10} \\cdot .52 \\approx .36$.
                
            2.  One example is *y* >  − .2.
                
            
        *   One example is that *ŷ* = 0.038988,  when *x* <  − 7.4495 and *ŷ* = 0.164017,  when *x* ≥  − 7.4495
            
        *   1.  See [Figure 8.4](#chapter8.xhtml#fig8_4).
                
            2.  Sample root criteria *x* > 1.5 and child *y* > 1.5
                
            3.  With root criteria *x* > 1.5 and child *y* > 1.5, Sri Lanka is predicted to have a low substance abuse measure in 2019. If one takes the average of the training data in this region the value is 0.383333.
                
            
        
        ![Figure 8.4 Visualization for Exercise 3b (Chapter 6).](images/fig8_4.jpg)
        
        [Figure 8.4](#chapter8.xhtml#b8fig8_4) Visualization for Exercise 3b ([Chapter 6](#chapter6.xhtml)).
        
        ## 8.7 Chapter 7
        
        *   1. *κ*(*A*) = 20.0501.
            
        *   5. Matrices a and c are Hermitian.
            
        *   6. If $r\_{1} = \\left\\{ \\frac{1 + i}{2}, - \\frac{1 + i}{2} \\right\\}$ and $r\_{2} = \\left\\{ \\frac{1}{\\sqrt{2}},\\frac{1}{\\sqrt{2}} \\right\\}$. Then ||*r*[1]|| = ||*r*[2]|| = 1 and *r*[1].*r*[2] = 0. Similarly $c\_{1} = \\left\\{ \\frac{1 + i}{2},\\frac{1}{\\sqrt{2}} \\right\\}$ and $c\_{2} = \\left\\{ - \\frac{1 + i}{2},\\frac{1}{\\sqrt{2}} \\right\\}$ then ||*c*[1]|| = ||*c*[2]|| = 1 but *c*[1].*c*[2] ≠ 0.
            
        *   7. (Sample Python Code, below, and Sample distribution in [Figure 8.5](#chapter8.xhtml#fig8_5))
            
            import matplotlib.pyplot as plt
            
            import numpy as np
            
            import random
            
            values= random.sample(range(100, 1000), 500)
            
            data = np.zeros((500,365))
            
            tdata =np.transpose(data)
            
            for time in range(0,365):
            
            for i in range(0,100):
            
            trade=random.sample(range(0,500),2)
            
            if values\[trade\[0\]\]>=values\[trade\[1\]\]:
            
            values\[trade\[0\]\]=.75\*total
            
            values\[trade\[1\]\]=.25\*total
            
            else:
            
            values\[trade\[0\]\]=.25\*total
            
            values\[trade\[1\]\]=.75\*total
            
            tdata\[time\]=values data=np.transpose(tdata)
            
            evalues=np.linalg.eig(np.dot(data,tdata))
            
            plt.hist(values, bins=10, density=True, color = “gray”’,edgecolor =
            
            ‘black’)
            
            ![Figure 8.5 Distribution of values.](images/fig8_5.jpg)
            
            [Figure 8.5](#chapter8.xhtml#b8fig8_5) Distribution of values.
            
        
        # Github Links
        
        1.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/cinderellastories.csv](https://github.com)
            
        2.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/pythonchapter1.py](https://github.com)
            
        3.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/project1sports.csv](https://github.com)
            
        4.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/ncaamens2020a.csv](https://github.com)
            
        5.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/ncaamens2020b.csv](https://github.com)
            
        6.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/pythonchapter1b.py](https://github.com)
            
        7.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/rchapter1.R](https://github.com)
            
        8.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/rchapter1b.R](https://github.com)
            
        9.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/weightedcensussmall.csv](https://github.com)
            
        10.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/censusall.csv](https://github.com)
             
        11.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/pythonchapter2b.py](https://github.com)
             
        12.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/rchapter2b.R](https://github.com)
             
        13.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/bigram.csv](https://github.com)
             
        14.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/pythonchapter2c.py](https://github.com)
             
        15.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/rchapter2c.R](https://github.com)
             
        16.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/s\_n\_p\_data1920.csv](https://github.com)
             
        17.  [https://raw.githubusercontent.com/rfordatascience/tidytuesday/master/data/2020/2020-01-21/spotify\_songs.csv](https://raw.githubusercontent.com)
             
        18.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/tweets.csv](https://github.com)
             
        19.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/pythonchapter3a.py](https://github.com)
             
        20.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/pythonchapter3b.py](https://github.com)
             
        21.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/rchapter3a.R](https://github.com)
             
        22.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/rchapter3b.R](https://github.com)
             
        23.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/starhusbandbook.csv](https://github.com)
             
        24.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/faces.csv](https://github.com)
             
        25.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/fullfaces.csv](https://github.com)
             
        26.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/pythonchapter4a.py](https://github.com)
             
        27.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/pythonchapter4b.py](https://github.com)
             
        28.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/pythonchapter4c.py](https://github.com)
             
        29.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/rchapter4a.R](https://github.com)
             
        30.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/rchapter4b.R](https://github.com)
             
        31.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/rchapter4c.R](https://github.com)
             
        32.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/pythonchapter5a.py](https://github.com)
             
        33.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/pythonchapter5b.py](https://github.com)
             
        34.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/rchapter5a.R](https://github.com)
             
        35.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/rchapter5b.R](https://github.com)
             
        36.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/digits.csv](https://github.com)
             
        37.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/pythonchapter6a.py](https://github.com)
             
        38.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/pythonchapter6b.py](https://github.com)
             
        39.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/rchapter6a.R](https://github.com)
             
        40.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/rchapter6b.R](https://github.com)
             
        41.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/wordle.py](https://github.com)
             
        42.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/words.csv](https://github.com)
             
        43.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/birdcallsupdated.zip](https://github.com)
             
        44.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/pythonchapter7a.py](https://github.com)
             
        45.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/pythonchapter7b.py](https://github.com)
             
        46.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/rchapter7a.R](https://github.com)
             
        47.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/rchapter7b.R](https://github.com)
             
        48.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/stockreturn.zip](https://github.com)
             
        49.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/GSE13598.txt](https://github.com)
             
        50.  [https://github.com/ccoles1/LinearAlgebra\_datasets/blob/master/diseasedatabase.csv](https://github.com)
             
        
        # Bibliography
        
        1.  [\[1\]](#chapter4.xhtml#b4refbib1) ACLU. *Extreme Racial Disparities Persist in Marijuana Arrests*. Retrieved from [https://graphics.aclu.org/marijuana-arrest-report/](https://graphics.aclu.org).
        2.  [\[2\]](#chapter1.xhtml#b1refbib2) Barnett, N. (2018). *NC Case Could Slay Dragon of Partisan Gerrymandering*. News and Observer.
        3.  [\[3\]](#chapter1.xhtml#b1refbib3) Benson-Putnins, D., Bonfardin, M., Magnoni, M. E., Martin, D. (2011). *Spectral Clustering and Visualization: a Novel Clustering of Fisher's Iris Data Set*. SIAM Undergraduate Research Online, 4, 1–15.
        4.  [\[4\]](#chapter2.xhtml#b2refbib4) Boyle, M. (2015). Notes on the Perron-Frobenius Theory of Nonnegative Matrices. Dept. of Mathematics, University of Maryland, College Park, MD. USA, Retrieved from [http://www.math.umd.edu/mboyle/courses/475sp05/spec.pdf](http://www.math.umd.edu).
        5.  [\[5\]](#chapter7.xhtml#b7refbib5) The Cancer Network Galaxy. Database of Cancer Gene Networks from Public Gene Expression Data. Retrieved from [https://tcng.hgc.jp/](https://tcng.hgc.jp)
        6.  [\[6\]](#chapter1.xhtml#b1refbib6) Chartier, T., Kreutzer, E., Langville, A., Pedings, K. (2010). *Bracketology: How Can Math Help?*. Mathematics and Sports, 43(67), 55–70.
        7.  [\[7\]](#chapter2.xhtml#b2refbib7) Cushing, J. M., Yicang, Z. (1994). *The Net Reproductive Value and Stability in Matrix Population Models*. Natural Resource Modeling, 8(4), 297–333.
        8.  \[8\] De Abreu, N. M. M. (2007). *Old and New Results on Algebraic Connectivity of Graphs*. Linear algebra and its applications, 423(1), 53–73.
        9.  [\[9\]](#chapter3.xhtml#b3refbib9) Dundes, A. (editor). (1965). Introduction to Stith Thompson's “The star husband tale”. pp. 414–415. Prentice-Hall. Englewood Cliffs, NJ.
        10.  [\[10\]](#chapter4.xhtml#b4refbib10) Evans, M. L., Lindauer, M., Farrell, M. E. (2020). *A Pandemic within a Pandemic—Intimate Partner Violence during Covid-19*. New England journal of medicine, 383(24), 2302–2304.
        11.  \[11\] Fernendez, J. (2018). *Judges Rule N.C.'s 2016 Congressional Districts Partisan Gerrymander*. Winston-Salem Journal.
        12.  [\[12\]](#chapter1.xhtml#b1refbib12) Fiedler, M. (1975). *A Property of Eigenvectors of Nonnegative Symmetric Matrices and its Application to Graph Theory*. Czechoslovak Mathematical Journal, 25(4), 619–633.
        13.  [\[13\]](#chapter2.xhtml#b2refbib13) Yahoo! Finance. Retrieved from [finance.yahoo.com](http://finance.yahoo.com)
        14.  [\[14\]](#chapter3.xhtml#b3refbib14) Free Images. Retrieved from [https://www.freeimages.com/search/face](https://www.freeimages.com)
        15.  [\[15\]](#chapter1.xhtml#b1refbib15) Gillman, R. (2002). *Geometry and Gerrymandering*. Math Horizons, 10(1), 10–12.
        16.  [\[16\]](#chapter2.xhtml#b2refbib16) Gupta, A. and Dhingra, B. (2012). *Stock Market Prediction using Hidden Markov Models*. In 2012 Students Conference on Engineering and Systems (pp. 1–4). IEEE.
        17.  [\[17\]](#chapter3.xhtml#b3refbib17) Heiner, H.A. (Ed.). (2012). Cinderella Tales from Around the World: Fairy Tales, Myths, Legends and Other Tales with Cinderellas. SurLaLune Press.
        18.  [\[18\]](#chapter4.xhtml#b4refbib18) American Council on Education. Data Tables. Retrieved from [https://www.equityinhighered.org/data-tables/](https://www.equityinhighered.org).
        19.  [\[19\]](#chapter1.xhtml#b1refbib19) Keener, J. P. (1993).*The Perron–Frobenius Theorem and the Ranking of Football Teams*.SIAM review, 35(1), 80–93.
        20.  \[20\] Kershenbaum, A. (2014). *Entropy Rate as a Measure of Animal Vocal Complexity*.Bioacoustics, 23(3), 195–208.
        21.  [\[21\]](#chapter2.xhtml#b2refbib21) Liu, E. (2019) *Yes, Trump's Tweets Move the Stock Market. But Not for Long*. Barron's. Retrieved from [https://www.barrons.com/articles/donald-trump-twitter-stock-market-51567803655](https://www.barrons.com)
        22.  [\[22\]](#chapter4.xhtml#b4refbib22) Minters, M. (2018) *Diverse: Issues In Higher Education Names Top 100 Degree Producers*. Diverse Issues in Higher Education. Retrieved from [https://diverseeducation.com/article/120916/](https://diverseeducation.com)
        23.  [\[23\]](#chapter4.xhtml#b4refbib23) National Domestic Hotline. *Impact and State Reports*. Retrieved from [https://www.thehotline.org/stakeholders/impact-and-state-reports/](https://www.thehotline.org)
        24.  [\[24\]](#chapter4.xhtml#b4refbib24) National Coalition Against Domestic Violence (NCADV). (2021). *COVID-19 and Domestic Violence* Retrieved from [https://ncadv.org/covid-19-and-domestic-violence](https://ncadv.org)
        25.  [\[25\]](#chapter2.xhtml#b2refbib25) Nguyen, N. (2018). *Hidden Markov Model for Stock Trading*. International Journal of Financial Studies, 6(2), 36.
        26.  [\[26\]](#chapter1.xhtml#b1refbib26) North Carolina General Assembly. *2011 Redistricting Reference Data*. Retrieved from [https://www.ncleg.gov/Redistricting/BaseData2011](https://www.ncleg.gov)
        27.  [\[27\]](#chapter5.xhtml#b5refbib27) Ontario (2020) Ontario Government. (2020). Confirmed Positive Cases of COVID-19 in Ontario. \[Data file\]. Retrieved from [https://data.ontario.ca/dataset/f4112442-bdc8-45d2-be3c-12efae72fb27/resource/455fd63b-603d-4608-8216-7d8647f43350/download/conposcovidloc.csv](https://data.ontario.ca).
        28.  [\[28\]](#chapter6.xhtml#b6refbib28) Pierce, J. R. (2012). An Introduction to Information Theory: Symbols, Signals and Noise. Courier Corporation.
        29.  [\[29\]](#chapter7.xhtml#b7refbib29) Ralston, A. (2008). *Gene Interaction and Disease*. Nature Education 1(1), 16.
        30.  [\[30\]](#chapter2.xhtml#b2refbib30) Trump Twitter Archive V2. (n.d.). Retrieved from [https://www.thetrumparchive.com/](https://www.thetrumparchive.com)
        31.  [\[31\]](#chapter1.xhtml#b1refbib31) Slininger, B. (2013). *Fiedlers Theory of Spectral Graph Partitioning*. Dosegljivo: [https://citeseerx.ist.psu.edu/document?repid=rep1&type=pdf&doi=beeee28a9c52287ac9a20868d067d1ed20788036](https://citeseerx.ist.psu.edu).
        32.  [\[32\]](#chapter6.xhtml#b6refbib32) Statista. Poverty Rates in the United States 1990-2020. Retrieved from [https://www.statista.com/statistics/200463/us-poverty-rate-since-1990/](https://www.statista.com)
        33.  [\[33\]](#chapter4.xhtml#b4refbib33) US Department of Education. (2016). Advancing diversity and inclusion in higher education. Retrieved from [https://www2.ed.gov/rschstat/research/pubs/advancing-diversity-inclusion.pdf](https://www2.ed.gov)
        34.  \[34\] Urschel, J. C., Zikatanov, L. T. (2014). *Spectral Bisection of Graphs and Connectedness.*Linear Algebra and its Applications, 449, 1–16.
        35.  [\[35\]](#chapter3.xhtml#b3refbib35) Violence Policy Center. (2018). State Firearm Death Rates, Ranked by Rate, 2018. It sources the National Center for Injury Prevention and Control of the Centers for Disease Control and Prevention. Retrieved from [http://vpc.org/state-firearm-death-rates-ranked-by-rate-2018/](http://vpc.org)
        36.  \[36\] Von Luxburg, U. (2007). *A Tutorial on Spectral Clustering*. Statistics and Computing, 17(4), 395–416.
        37.  [\[37\]](#chapter1.xhtml#b1refbib37) Wey, T. W., Blumstein, D. T. (2010). *Social Cohesion in Yellow-Bellied Marmots is Established through Age and Kin Structuring*. Animal Behaviour, 79(6), 1343–1352.
        38.  [\[38\]](#chapter7.xhtml#b7refbib38) Wilson, A. G., Ghahramani, Z. (2010). *Generalised Wishart processes.* arXiv preprint arXiv:1101.0240.
        39.  [\[39\]](#chapter1.xhtml#b1refbib39) Wines, W. (2019). *State Court Bars Using North Carolina House Map in 2020 Elections*. New York Times. Retrieved from [https://www.nytimes.com/2019/10/28/us/north-carolina-gerrymander-maps.html](https://www.nytimes.com).
        40.  [\[40\]](#chapter5.xhtml#b5refbib40) Ritchie, H. and Roser M. (n.d.). “Our World in Data”. Retrieved from [https://ourworldindata.org/energy#energy-country-profiles](https://ourworldindata.org)
        41.  [\[41\]](#chapter5.xhtml#b5refbib41) The World Bank, GDP (U.S.D) Data. (n.d.) Retrieved from [https://data.worldbank.org](https://data.worldbank.org)
        42.  [\[42\]](#chapter3.xhtml#b3refbib42) World Population Review. (n.d.) Retrieved from [https://worldpopulationreview.com/states/gun-ownership-by-state/](https://worldpopulationreview.com)
        43.  [\[43\]](#chapter6.xhtml#b6refbib43) xeno-canto, Sharing Bird Songs From around the World. (n.d.) Retrieved from [https://xeno-canto.org/](https://xeno-canto.org)
        44.  [\[44\]](#chapter5.xhtml#b5refbib44) LaCunn, Y., Cortes, C., and Burges, C. (n.d.) “The MNIST Database for handwritten digits”. Retrieved from [http://yann.lecun.com/exdb/mnist/](http://yann.lecun.com)
        45.  [\[45\]](#chapter3.xhtml#b3refbib45) Young, F.W. (1978). *Folktales and Social Structure: a Comparison of Three Analyses of the Star-Husband Tale*. J. Amer. Folklore 91(360), 691–699.
        
        # Index
        
        *   *l*[2] error, [142](#chapter4.xhtml#p142)
        
        *   absolute error, [142](#chapter4.xhtml#p142)
        *   absorbing state, [50](#chapter2.xhtml#p50)
        *   activation function, [182](#chapter5.xhtml#p182)
        *   adjacency matrix, [2](#chapter1.xhtml#p2)
        *   adjacent vertices, [1](#chapter1.xhtml#p1)
        *   algebraic connectivity, [18](#chapter1.xhtml#p18)
        
        *   back propagation, [185](#chapter5.xhtml#p185)
        *   bagging, [228](#chapter6.xhtml#p228)
        *   basis, [xvii](#chapter101.xhtml#pxvii)
        *   Baum-Welch Algorithm, [63](#chapter2.xhtml#p63)
        *   Bayes Theorem, [53](#chapter2.xhtml#p53)
        *   Binomial Distribution, [158](#chapter5.xhtml#p158)
        
        *   characteristic equation, [12](#chapter1.xhtml#p12)
        *   characteristic valuation, [18](#chapter1.xhtml#p18)
        *   Chebyshev interpolation, [132](#chapter4.xhtml#p132)
        *   Chebyshev nodes, [132](#chapter4.xhtml#p132)
        *   Chebyshev polynomials, [122](#chapter4.xhtml#p122), [144](#chapter4.xhtml#p144)
        *   child node, [209](#chapter6.xhtml#p209)
        *   classification tree, [209](#chapter6.xhtml#p209)
        *   cofactor expansion, [xv](#chapter101.xhtml#pxv)
        *   Colley matrix, [29](#chapter1.xhtml#p29)
        *   columnspace, [140](#chapter4.xhtml#p140)
        *   complex conjugate, [248](#chapter7.xhtml#p248)
        *   condition number, [238](#chapter7.xhtml#p238)
        *   conditional probability distribution, [161](#chapter5.xhtml#p161)
        *   conjugate transpose, [248](#chapter7.xhtml#p248)
        *   connected graph, [4](#chapter1.xhtml#p4)
        *   continuous random variable, [157](#chapter5.xhtml#p157)
        *   correlation matrix, [95](#chapter3.xhtml#p95), [99](#chapter3.xhtml#p99), [255](#chapter7.xhtml#p255)
        *   covariance matrix, [95](#chapter3.xhtml#p95)
        *   cross-entropy function, [194](#chapter5.xhtml#p194), [202](#chapter5.xhtml#p202)
        *   cumulative distribution function, [157](#chapter5.xhtml#p157)
        
        *   decision tree, [9](#chapter1.xhtml#p9), [209](#chapter6.xhtml#p209)
        *   degree of a vertex, [1](#chapter1.xhtml#p1)
        *   determinant, [xv](#chapter101.xhtml#pxv)
        *   directed graph, [8](#chapter1.xhtml#p8)
        *   Discrete Fourier Transform, [232](#chapter6.xhtml#p232)
        *   discrete random variable, [157](#chapter5.xhtml#p157)
        *   divided difference, [126](#chapter4.xhtml#p126), [138](#chapter4.xhtml#p138)
        
        *   edge, [1](#chapter1.xhtml#p1)
        *   eigenvalue, [12](#chapter1.xhtml#p12), [88](#chapter3.xhtml#p88)
        *   eigenvector, [12](#chapter1.xhtml#p12), [88](#chapter3.xhtml#p88)
        *   emissions probabilities, [52](#chapter2.xhtml#p52)
        *   endpoints, [1](#chapter1.xhtml#p1)
        *   ensemble, [228](#chapter6.xhtml#p228)
        *   entropy, [211](#chapter6.xhtml#p211), [212](#chapter6.xhtml#p212)
        *   Expectation Maximization, [67](#chapter2.xhtml#p67)
        *   expected value, [157](#chapter5.xhtml#p157)
        *   extrapolation, [156](#chapter4.xhtml#p156)
        
        *   Fiedler value, [18](#chapter1.xhtml#p18)
        *   Fiedler vector, [18](#chapter1.xhtml#p18)
        *   Fiedler's Theorem, [18](#chapter1.xhtml#p18)
        *   finite probability space, [158](#chapter5.xhtml#p158)
        *   Forward/Backward Algorithm, [54](#chapter2.xhtml#p54), [60](#chapter2.xhtml#p60)
        *   Frobenius norm, [254](#chapter7.xhtml#p254)
        *   fundamental matrix, [50](#chapter2.xhtml#p50)
        
        *   Gamma distribution, [160](#chapter5.xhtml#p160)
        *   Gaussian distribution, [160](#chapter5.xhtml#p160)
        *   Gaussian Orthogonal Ensemble, [243](#chapter7.xhtml#p243)
        *   Gaussian Symplectic Ensemble, [253](#chapter7.xhtml#p253)
        *   Gaussian Unitary Ensemble, [250](#chapter7.xhtml#p250)
        *   Gini impurity, [215](#chapter6.xhtml#p215)
        *   Gini index, [211](#chapter6.xhtml#p211)
        *   gradient, [174](#chapter5.xhtml#p174), [176](#chapter5.xhtml#p176)
        *   gradient descent, [183](#chapter5.xhtml#p183), [185](#chapter5.xhtml#p185)
        *   Gradient Descent Algorithm, [176](#chapter5.xhtml#p176)
        *   gradient matrix, [165](#chapter5.xhtml#p165)
        *   gradient methods, [67](#chapter2.xhtml#p67)
        *   Gramian matrix, [21](#chapter1.xhtml#p21), [91](#chapter3.xhtml#p91)
        *   graph, [1](#chapter1.xhtml#p1)
        *   graph order, [1](#chapter1.xhtml#p1)
        *   graph size, [1](#chapter1.xhtml#p1)
        
        *   Hadamard product, [xiii](#chapter101.xhtml#pxiii)
        *   Hermite differential operator, [124](#chapter4.xhtml#p124)
        *   Hermite interpolation, [137](#chapter4.xhtml#p137)
        *   Hermite polynomials, [122](#chapter4.xhtml#p122)
        *   Hermitian, [248](#chapter7.xhtml#p248)
        *   Hessian matrix, [165](#chapter5.xhtml#p165)
        *   hidden layer, [182](#chapter5.xhtml#p182)
        *   hidden markov model, [51](#chapter2.xhtml#p51)
        *   hyperbolic tangent, [188](#chapter5.xhtml#p188)
        
        *   identity matrix, [xiv](#chapter101.xhtml#pxiv)
        *   indicent, [1](#chapter1.xhtml#p1)
        *   inner product space, [86](#chapter3.xhtml#p86)
        *   inner project, [86](#chapter3.xhtml#p86)
        *   interpolant, [117](#chapter4.xhtml#p117)
        *   interpolating function, [117](#chapter4.xhtml#p117)
        *   interpolation points, [117](#chapter4.xhtml#p117)
        *   invertible, [xiv](#chapter101.xhtml#pxiv)
        *   irreducible, [49](#chapter2.xhtml#p49)
        *   isoperimetric number, [25](#chapter1.xhtml#p25)
        *   isoperimetric ratio, [25](#chapter1.xhtml#p25)
        
        *   Jacobian, [163](#chapter5.xhtml#p163)
        *   joint distribution, [160](#chapter5.xhtml#p160)
        
        *   Kroenecker product, [xviii](#chapter101.xhtml#pxviii)
        
        *   Laplacian matrix, [14](#chapter1.xhtml#p14)
        *   leaf, [209](#chapter6.xhtml#p209)
        *   least squares regression, [168](#chapter5.xhtml#p168)
        *   linear combination, [xvi](#chapter101.xhtml#pxvi), [87](#chapter3.xhtml#p87)
        *   Linear Discriminant Analysis, [102](#chapter3.xhtml#p102)
        *   linear transformation, [140](#chapter4.xhtml#p140)
        *   linearly independent, [xvi](#chapter101.xhtml#pxvi), [87](#chapter3.xhtml#p87)
        *   log-linear model, [171](#chapter5.xhtml#p171)
        *   logarithmic returns, [258](#chapter7.xhtml#p258)
        *   loop, [1](#chapter1.xhtml#p1)
        *   LU-decomposition, [129](#chapter4.xhtml#p129)
        
        *   Maclaurin series, [50](#chapter2.xhtml#p50)
        *   Marchenko-Pastur Quarter-Circle Law, [245](#chapter7.xhtml#p245)
        *   Markov chain, [48](#chapter2.xhtml#p48)
        *   matrix differential, [166](#chapter5.xhtml#p166)
        *   matrix ensemble, [242](#chapter7.xhtml#p242)
        *   maximum likelihood, [168](#chapter5.xhtml#p168)
        *   memoryless property, [48](#chapter2.xhtml#p48)
        *   minor, [xv](#chapter101.xhtml#pxv)
        *   multiple edges, [2](#chapter1.xhtml#p2)
        *   mutually exclusive, [53](#chapter2.xhtml#p53)
        
        *   negative definite, [23](#chapter1.xhtml#p23)
        *   negative semidefinite, [23](#chapter1.xhtml#p23)
        *   neural network, [9](#chapter1.xhtml#p9)
        *   Newton Raphson method, [172](#chapter5.xhtml#p172)
        *   Newton's interpolating polynomial, [126](#chapter4.xhtml#p126)
        *   nodes, [1](#chapter1.xhtml#p1)
        *   non-singular, [xiv](#chapter101.xhtml#pxiv)
        *   normalized Laplacian matrix, [14](#chapter1.xhtml#p14)
        
        *   oblique decision tree, [220](#chapter6.xhtml#p220)
        *   orthogonal, [86](#chapter3.xhtml#p86)
        *   orthogonal components, [90](#chapter3.xhtml#p90)
        *   orthogonal grid, [89](#chapter3.xhtml#p89)
        *   orthonormal, [86](#chapter3.xhtml#p86)
        *   overfitting, [226](#chapter6.xhtml#p226)
        
        *   parent node, [209](#chapter6.xhtml#p209)
        *   path, [3](#chapter1.xhtml#p3)
        *   perceptron, [181](#chapter5.xhtml#p181)
        *   permutation, [43](#chapter2.xhtml#p43)
        *   permutation matrix, [43](#chapter2.xhtml#p43)
        *   Perron Theorem, [47](#chapter2.xhtml#p47)
        *   Perron-Frobenius Theorem, [47](#chapter2.xhtml#p47), [49](#chapter2.xhtml#p49)
        *   Poisson distribution, [158](#chapter5.xhtml#p158)
        *   Poisson regression, [171](#chapter5.xhtml#p171)
        *   positive definite, [23](#chapter1.xhtml#p23)
        *   positive semidefinite, [23](#chapter1.xhtml#p23)
        *   power law, [256](#chapter7.xhtml#p256)
        *   Principal Component Analysis, [92](#chapter3.xhtml#p92)
        *   Principal Component Regression, [99](#chapter3.xhtml#p99)
        *   probability density function, [160](#chapter5.xhtml#p160)
        *   probability distribution function, [157](#chapter5.xhtml#p157)
        *   probability space, [157](#chapter5.xhtml#p157)
        *   pruning, [226](#chapter6.xhtml#p226)
        *   pseudospectrum, [240](#chapter7.xhtml#p240)
        *   Public Key Cryptography, [144](#chapter4.xhtml#p144)
        *   pure node, [217](#chapter6.xhtml#p217)
        
        *   quadratic form, [22](#chapter1.xhtml#p22)
        *   quaternion, [252](#chapter7.xhtml#p252)
        
        *   radial functions, [194](#chapter5.xhtml#p194)
        *   random forest, [228](#chapter6.xhtml#p228)
        *   random matrix, [237](#chapter7.xhtml#p237)
        *   random variable, [157](#chapter5.xhtml#p157)
        *   Rayleigh distribution, [256](#chapter7.xhtml#p256)
        *   Rayleigh Quotient, [24](#chapter1.xhtml#p24)
        *   Rayleigh-Ritz Theorem, [24](#chapter1.xhtml#p24)
        *   real quaternion, [252](#chapter7.xhtml#p252)
        *   rectified linear unit, [191](#chapter5.xhtml#p191)
        *   regression tree, [224](#chapter6.xhtml#p224)
        *   regularization, [117](#chapter4.xhtml#p117), [184](#chapter5.xhtml#p184)
        *   reproduction number, [69](#chapter2.xhtml#p69)
        *   root, [209](#chapter6.xhtml#p209)
        *   Runge's phenomenon, [135](#chapter4.xhtml#p135)
        
        *   Sharpe ratio, [259](#chapter7.xhtml#p259)
        *   sigmoid neuron function, [186](#chapter5.xhtml#p186)
        *   simple connected graph, [4](#chapter1.xhtml#p4)
        *   singular, [xiv](#chapter101.xhtml#pxiv)
        *   Singular Value Decomposition, [90](#chapter3.xhtml#p90)
        *   singular values, [89](#chapter3.xhtml#p89)
        *   skew-symmetric, [xix](#chapter101.xhtml#pxix), [252](#chapter7.xhtml#p252)
        *   SoftMax function, [184](#chapter5.xhtml#p184)
        *   span, [xvi](#chapter101.xhtml#pxvi), [87](#chapter3.xhtml#p87), [88](#chapter3.xhtml#p88)
        *   sparse matrix, [72](#chapter2.xhtml#p72)
        *   spectral graph theory, [16](#chapter1.xhtml#p16)
        *   spectral radius, [47](#chapter2.xhtml#p47)
        *   Spectral Theorem, [23](#chapter1.xhtml#p23)
        *   sports ranking, [8](#chapter1.xhtml#p8)
        *   SSE, [142](#chapter4.xhtml#p142), [174](#chapter5.xhtml#p174)
        *   standardize, [97](#chapter3.xhtml#p97)
        *   steady state vector, [23](#chapter1.xhtml#p23)
        *   Stochastic Gradient Descent, [180](#chapter5.xhtml#p180)
        *   stochastic process, [46](#chapter2.xhtml#p46), [48](#chapter2.xhtml#p48)
        *   strongly-connected, [45](#chapter2.xhtml#p45)
        *   subgraph, [2](#chapter1.xhtml#p2)
        *   supervised neural networks, [181](#chapter5.xhtml#p181)
        *   symmetric, [xiii](#chapter101.xhtml#pxiii), [4](#chapter1.xhtml#p4)
        *   symplectic, [253](#chapter7.xhtml#p253)
        
        *   Taylor series, [50](#chapter2.xhtml#p50)
        *   tensor product, [xviii](#chapter101.xhtml#pxviii)
        *   testing set, [117](#chapter4.xhtml#p117)
        *   Toeplitz matrix, [241](#chapter7.xhtml#p241)
        *   Tracy-Widom distribution, [256](#chapter7.xhtml#p256)
        *   training sequence, [63](#chapter2.xhtml#p63)
        *   training set, [117](#chapter4.xhtml#p117)
        *   transient state, [50](#chapter2.xhtml#p50)
        *   Transition matrix, [48](#chapter2.xhtml#p48)
        *   tree graph, [4](#chapter1.xhtml#p4), [209](#chapter6.xhtml#p209)
        *   tridiagonal matrix, [121](#chapter4.xhtml#p121)
        *   trivial solution, [xv](#chapter101.xhtml#pxv)
        
        *   uncertainty, [211](#chapter6.xhtml#p211)
        *   undirected graph, [4](#chapter1.xhtml#p4)
        *   unit vector, [14](#chapter1.xhtml#p14), [86](#chapter3.xhtml#p86)
        *   unitary, [249](#chapter7.xhtml#p249)
        *   univariate decision tree, [220](#chapter6.xhtml#p220)
        *   unsupervised neural networks, [181](#chapter5.xhtml#p181)
        
        *   valuation, [18](#chapter1.xhtml#p18)
        *   Vandermonde determinant, [118](#chapter4.xhtml#p118), [139](#chapter4.xhtml#p139)
        *   Vandermonde matrix, [118](#chapter4.xhtml#p118), [167](#chapter5.xhtml#p167)
        *   vector space, [85](#chapter3.xhtml#p85)
        *   vertex, [1](#chapter1.xhtml#p1)
        *   Viterbi Algorithm, [60](#chapter2.xhtml#p60)
        
        *   weighted graph, [5](#chapter1.xhtml#p5)
        *   Wigner matrix, [237](#chapter7.xhtml#p237)
        *   Wigner's Semicircle Law, [244](#chapter7.xhtml#p244)
        *   Wigner's surmise, [246](#chapter7.xhtml#p246)
        *   Wishart matrix, [255](#chapter7.xhtml#p255)
        
        *   zero-centering, [97](#chapter3.xhtml#p97)
        
         |
        | --- |