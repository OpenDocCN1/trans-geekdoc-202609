![](images/9780262370127.jpg)

![Cover: Introduction to Online Convex Optimization by Elad Hazan](images/9780262370127.jpg)

**Adaptive Computation and Machine Learning**

Francis Bach, Editor

Christopher Bishop, David Heckerman, Michael Jordan, and Michael Kearns, Associate Editors

A complete list of books published in the Adaptive Computation and Machine Learning series appears at the back of this book.

© 2022 Elad Hazan

This work is subject to a Creative Commons CC-BY-ND-NC license.

Subject to such license, all rights are reserved.

![](images/logo.png)

The MIT Press would like to thank the anonymous peer reviewers who provided comments on drafts of this book. The generous work of academic experts is essential for establishing the authority and quality of our publications. We acknowledge with gratitude the contributions of these otherwise uncredited readers.

Library of Congress Cataloging-in-Publication Data

Names: Hazan, Elad, 1975– author.

Title: Introduction to online convex optimization / Elad Hazan.

Description: Second edition. | Cambridge: The MIT Press, 2022. | Series: Adaptive computation and machine learning series | Includes bibliographical references and index.

Identifiers: LCCN 2021050689 | ISBN 9780262046985 (hardcover)

Subjects: LCSH: Mathematical optimization. | Convex domains.

Classification: LCC QA402.5.H297 2022 | DDC 519.7/6—dc23/eng/20211130

LC record available at [https://lccn.loc.gov/2021050689](https://lccn.loc.gov/2021050689)

d\_r0

To my family: Dana, Hadar, Yoav, Oded, and Deluca

> ![](images/epi.png)
> 
> “…you shall research and meditate therein day and night…”
> 
> *—Yehoshua 1:8*

# Preface

This book serves as an introduction to the expanding theory of online convex optimization (OCO). It was written as an advanced textbook to serve as a basis for a graduate course, and/or as a reference to researchers diving into this fascinating world at the intersection of optimization and machine learning.

Such a course was given at the Technion in 2010–2014, with slight variations from year to year, and later at Princeton University in 2015–2020. The core material in these courses is fully covered in this book, along with exercises that allow students to complete parts of proofs, or that were found illuminating and thought-provoking by those taking the course. Most of the material is given with examples of applications, which are interlaced throughout various topics. These include prediction from expert advice, portfolio selection, matrix completion and recommendation systems, and support vector machine (SVM) training.

Our hope is that this compendium of material and exercises will be useful to you: the researcher and/or educator.

## Placing This Book in the Machine Learning Library

The broad field of machine learning, as in the subdisciplines of online learning, boosting, regret minimization in games, universal prediction, and other related topics, have seen a plethora of introductory textbooks in recent years. With this note, we can hardly do justice to all of these, but perhaps point to the most related books on the topics of machine learning, learning in games, and optimization, whose intersection is our main focus.

The most closely related book, which served as an inspiration to the current book, and indeed an inspiration to the entire field of learning in games, is the wonderful text of Cesa-Bianchi and Lugosi (2006). From the literature on mathematical optimization theory, there are numerous introductory essays to convex optimization and convex analysis, to name only a few (Boyd and Vandenberghe 2004; Nesterov 2004; Nemirovski and Yudin 1983; Nemirovski 2004; Borwein and Lewis 2006; Rockafellar 1997). The author fondly recommends the text from which he has learned about mathematical optimization theory (Nemirovski 2004). The more broad texts on machine learning are too numerous to state here.

The primary purpose of this is to serve as an educational textbook for a *dedicated* course on OCO and the convex optimization approach to machine learning. OCO has already had enough impact to appear in several surveys and introductory texts (Hazan 2011; Shalev-Shwartz 2011; Rakhlin 2009; Rakhlin and Sridharan 2014). We hope this compilation of material and exercises will further enrich the literature.

## Book’s Structure

This book is intended to serve as a reference for a self-contained course for graduate students in computer science/electrical engineering/operations research/statistics and related fields. As such, its organization follows the structure of the course “Decision Analysis,” taught at the Technion, and later “Theoretical Machine Learning,” taught at Princeton University.

Each chapter should take one or two weeks of classes, depending on the depth and breadth of the intended course. Chapter 1 is designed to be a teaser for the field, and thus it is less rigorous than the rest of the book.

Roughly speaking, the book can be conceived of as three units. The first, from chapters 2 through 4, contains the basic definitions, framework, and core algorithms for OCO. Chapters 5 to 7 contain more advanced algorithms and in-depth analysis of the framework and its extensions to other computational and information access models. The rest of the book deals with more advanced algorithms, more difficult settings, and relationships to well-known machine learning paradigms.

This book can assist educators in designing a complete course on the topic of OCO, or it can serve as a component in a comprehensive course on machine learning. An accompanying manual of solutions to selected exercises given in the book is available for educators only.

## New in the Second Edition

The main additions to the second edition of this book include the following:

*   Expanded coverage of optimization in chapter 2, with a unified gradient descent analysis of the Polyak stepsize.
*   Expanded coverage of learning theory in chapter 9, with an introduction to compression and its use in generalization theory.
*   An expanded chapter 4, with discussion of the exponential weighted optimizer for exp-concave loss functions.
*   A revised chapter 5, with the addition of mirror descent analysis, as well as a revised section on adaptive gradient methods.
*   New chapter 10 on the notion of adaptive regret and algorithms for OCO with near-optimal adaptive regret bounds.
*   New chapter 11 on boosting and its relationship to OCO. Derivation of boosting algorithms from regret minimization.
*   New chapter 12 on online boosting.
*   New chapter 13 on Blackwell approachability and its strong connection to OCO.

In addition, numerous typos are fixed, exercises are corrected, and solutions to several questions have been made available in a separate manual for educators.

# Acknowledgments

## First Edition

First of all, I gratefully acknowledge the numerous contributions and insights from the students of the course “Decision Analysis,” given at the Technion during 2010–2014, as well as the students of “Theoretical Machine Learning,” a course taught at Princeton University during 2015–2016.

I would like to thank the friends, colleagues, and students who have contributed many suggestions and corrections. A partial list includes Sanjeev Arora, Shai Shalev-Shwartz, Aleksander Madry, Yoram Singer, Satyen Kale, Alon Gonen, Roi Livni, Gal Lavee, Maayan Harel, Daniel Khasabi, Shuang Liu, Jason Altschuler, Haipeng Luo, Zeyuan Allen-Zhu, Mehrdad Mahdavi, Jaehyun Park, Baris Ungun, Maria Gregori, Tengyu Ma, Kayla McCue, Esther Rolf, Jeremy Cohen, Daniel Suo, Lydia Liu, Fermi Ma, Mert Al, Amir Reza Asadi, Carl Gabel, Nati Srebro, Abbas Mehrabian, Chris Liaw, Nikhil Bansal, Naman Agarwal, Raunak Kumar, Zhize Li, Sheng Zhang, Swati Gupta, Xinyi Chen, Liang Zeng, and Kunal Mittal.

I also thank Udi Aharoni for his artwork and illustrations depicting algorithms in this book.

I am forever indebted to my teacher and mentor, Sanjeev Arora; without him, this book would not be possible.

Finally, I am grateful for the love and support of my wife and children: Dana, Hadar, Yoav, and Oded.

Elad Hazan  
Princeton University

## Second Edition

I am most thankful to my students and colleagues who have collaborated with me on research, some of which appears in the second edition of this book. Notably, that includes my collaborators on boosting methods, including Nataly Brukhim, Xinyi Chen, Shay Moran, Naman Agarwal, and Karan Singh.

Thanks to my students who helped me proof check new and existing sections: Edgar Minasyan, Paula Gradu, Karan Singh, Nataly Brukhim, Xinyi Chen, Naman Agarwal, and Udaya Ghai.

I am thankful to Shay Moran for explaining compression schemes and how they simplify generalization for boosting.

I gratefully acknowledge the help of Ahmed Farah, Charlie Cowen-Breen, and the students of “COS 597C: Computational Control Theory” for many helpful suggestions, corrections, and solutions to many of the problem sets.

I am very thankful to Wouter Koolen-Wijkstra for a helpful suggestion in the analysis of the Online Newton Step algorithm.

I thank the extremely helpful and rigorous reviewers of this book found by MIT Press, who gave fantastic suggestions and improved the final manuscript.

As in the first version (and even more so), I am grateful for the love and support of my wife and children: Dana, Hadar, Yoav, and Oded.

Elad Hazan  
Princeton University

# List of Figures

[**1.1**    Linear equalities and  
inequalities that define the flow polytope, which is the convex hull of all *u*\-*v* paths](#chapter_1.xhtml#fig1-1)

[**2.1**    The Pythagorean theorem](#chapter_2.xhtml#fig2-1)

[**2.2**    Optimality conditions: negative subgradient pointing outward](#chapter_2.xhtml#fig2-2)

[**2.3**    Iterates of the GD algorithm](#chapter_2.xhtml#fig2-3)

[**2.4**    The hinge loss function versus the 0/1 loss function](#chapter_2.xhtml#fig2-4)

[**3.1**    OGD: the iterate **x**[*t*+1] is derived by advancing **x**[*t*] in the direction of the current gradient ∇[*t*] and projecting back into 𝒦](#chapter_3.xhtml#fig3-1)

[**6.1**    The Minkowski set 𝒦[*δ*]](#chapter_6.xhtml#fig6-1)

[**7.1**    Direction of progression of the CG algorithm](#chapter_7.xhtml#fig7-1)

[**9.1**    Symmetric random walk: 12 trials of 200 steps. The black dotted lines show the functions ![](images/pgxvii-in-1.png)and ![](images/pgxvii-in-2.png), respectively](#chapter_9.xhtml#fig9-1)

[**10.1**  Illustration of the working set *S*[*t*]](#chapter_10.xhtml#fig10-1)

[**11.1**  Distinguishing zero versus 1 from a single pixel](#chapter_11.xhtml#fig11-1)

# List of Symbols

## General

![](images/pgxix-in-1.png)

## Geometry and Calculus

![](images/pgxix-in-2.png)

## Learning Theory

 
| 𝒳, 𝒴 || feature/label sets |
| --- | --- |
| 𝒟 || distribution over examples (**x***, y*) |
| --- | --- |
| ℋ || hypothesis class in 𝒳 ↦ *Y* |
| *h* || single hypothesis *h* ∈ℋ |
| *m* || training set size |
| error(*h*) || generalization error of hypothesis *h* ∈ℋ |

## Optimization

 
| **x** || vectors in the decision set |
| --- | --- |
| 𝒦 || decision set |
| --- | --- |
| ∇^(*k*)*f* || the *k*th differential of *f*; note ∇^(*k*)*f* ∈ ℝ^(*d*^(*k*)) |
| ∇^(−2)*f* || the inverse Hessian of *f* |
| ∇*f* || the gradient of *f* |
| ∇[*t*] || the gradient of *f* at point **x**[*t*] |
| **x**^(*⋆*) || the global or local optima of objective *f* |
| *h*[*t*] || objective value distance to optimality, *h*[*t*] = *f*(**x**[*t*]) − *f*(**x**^(*⋆*)) |
| *d*[*t*] || Euclidean distance to optimality *d*[*t*] = ∥**x**[*t*] −**x**^(*⋆*)∥ |
| *G* || upper bound on norm of subgradients |
| *D* || upper bound on Euclidean diameter |
| *D*[*p*]*, G*[*p*] || upper bound on the *p*\-norm of the subgradients/diameter |

## Regularization

 
| *R* || strongly convex and smooth regularization function |
| --- | --- |
| *B*[*R*](**x**||**y**) || *R*\-Bregman-divergence *R*(**x**) − *R*(**y**) −∇*R*(**y**)^⊤(**x** −**y**) |
| --- | --- |
| *G*[*R*] || upper bound on norm of (sub)gradients |
| *D*[*R*]² || squared *R* diameter max[**x**, **y**∈𝒦]{*R*(**x**) − *R*(**y**)} |
| ∥**x**∥[*A*]² || squared matrix norm **x**^⊤*A***x** |
| ∥**x**∥[**y**]² || local norm according to local regularization **x**^⊤∇²*R*(**y**)**x** |
| ∥**x**∥^(\*) || dual norm to ∥**x**∥ |

# 1 Introduction

This book considers *optimization as a process*. In many practical applications, the environment is so complex that it is not feasible to lay out a comprehensive theoretical model and use classical algorithmic theory and mathematical optimization. It is necessary, as well as beneficial, to take a robust approach by applying an optimization method that learns as more aspects of the problem are observed. This view of optimization as a process has become prominent in various fields, which has led to spectacular successes in modeling and systems that are now part of our daily lives.

The growing body of literature of machine learning, statistics, decision science, and mathematical optimization blurs the classical distinctions between deterministic modeling, stochastic modeling, and optimization methodology. We continue this trend in this book, studying a prominent optimization framework whose precise location in the mathematical sciences is unclear: the framework of *online convex optimization* (OCO), which was first defined in the machine learning literature (see section 1.4, later in this chapter). The metric of success is borrowed from game theory, and the framework is closely tied to statistical learning theory and convex optimization.

We embrace these fruitful connections and, on purpose, do not try to use any particular jargon in the discussion. Rather, this book will start with actual problems that can be modeled and solved via OCO. We will proceed to present rigorous definitions, backgrounds, and algorithms. Throughout, we provide connections to the literature in other fields. It is our hope that you, the reader, will contribute to our understanding of these connections from your domain of expertise, and expand the growing amount of literature on this fascinating subject.

## 1.1 The Online Convex Optimization Setting

In OCO, an online player iteratively makes decisions. At the time of each decision, the outcome or outcomes associated with it are unknown to the player.

After committing to a decision, the decision maker suffers a loss: every possible decision incurs a (possibly different) loss. These losses are unknown to the decision maker beforehand. The losses can be adversarially chosen, and even depend on the action taken by the decision maker.

Already at this point, several restrictions are necessary in order for this framework to make any sense at all:

*   The losses determined by an adversary should not be allowed to be unbounded.^([1](#chapter_1.xhtml#chapter1-1)) Otherwise, the adversary could keep decreasing the scale of the loss at each step and never allow the algorithm to recover from the loss of the first step. Thus, we assume that the losses lie in some bounded region.
*   The decision set must be somehow bounded and/or structured, though not necessarily finite.  
        To see why this is necessary, consider decision making with an infinite set of possible decisions. An adversary can assign high loss to all the strategies chosen by the player indefinitely, while setting apart some strategies with zero loss. This precludes any meaningful performance metric.

Surprisingly, interesting statements and algorithms can be derived with not much more than these two restrictions. The online convex optimization (OCO) framework models the decision set as a convex set in Euclidean space denoted as 𝒦⊆ ℝ^(*n*). The costs are modeled as bounded convex functions over 𝒦.

The OCO framework can be seen as a structured repeated game. The protocol of this learning framework is as follows.

At iteration *t*, the online player chooses **x**[*t*] ∈𝒦. After the player has committed to this choice, a convex cost function *f*[*t*] ∈ℱ: 𝒦 ↦ ℝ is revealed. Here, ℱ is the bounded family of cost functions available to the adversary. The cost incurred by the online player is *f*[*t*](**x**[*t*]), the value of the cost function for the choice **x**[*t*]. Let *T* denote the total number of game iterations.

What would make an algorithm a good OCO algorithm? As the framework is game-theoretic and adversarial in nature, the appropriate performance metric also comes from game theory: define the *regret* of the decision maker to be the difference between the total cost she has incurred and that of the best fixed decision in hindsight. In OCO, we are usually interested in an upper bound on the worst-case regret of an algorithm.

Let 𝒜 be an algorithm for OCO, which maps a certain game history to a decision in the decision set:

![](images/pg2.png)

We formally define the regret of 𝒜 after *T* iterations as

![](images/eq1-1.png)

If the algorithm is clear from the context, we henceforth omit the superscript and denote the algorithm’s decision at time *t* simply as **x**[*t*]. Intuitively, an algorithm performs well if its regret is sublinear as a function of *T* (i.e., Regret[*T*](𝒜) = *o*(*T*)), since this implies that on average, the algorithm performs as well as the best fixed strategy in hindsight.

The running time of an algorithm for OCO is defined to be the worst-case expected time to produce **x**[*t*], for an iteration *t* ∈ \[*T*\]^([2](#chapter_1.xhtml#chapter1-2)) in a *T*\-iteration repeated game. Typically, the running time will depend on *n* (the dimensionality of the decision set 𝒦), *T* (the total number of game iterations), and the parameters of the cost functions and underlying convex set.

## 1.2 Examples of Problems That Can Be Modeled via Online Convex Optimization

Perhaps the main reason that OCO has become a leading online learning framework in recent years is its powerful modeling capability: problems from diverse domains such as online routing, ad selection for search engines, and spam filtering can all be modeled as special cases. In this section, we briefly survey a few special cases and how they fit into the OCO framework.

### 1.2.1 Prediction from expert advice

Perhaps the most well known problem in prediction theory is the *experts problem*. The decision maker has to choose among the advice of *n* given experts. After making her choice, a loss between zero and 1 is incurred. This scenario is repeated iteratively, and at each iteration, the costs of the various experts are arbitrary (and possibly even adversarial, trying to mislead the decision maker). The goal of the decision maker is to do as well as the best expert in hindsight.

The OCO problem captures this as a special case: the set of decisions is the set of all distributions over *n* elements (experts); that is, the *n*\-dimensional simplex ![](images/pg3-in-1.png). Let the cost of the *i*th expert at iteration *t* be **g**[*t*](*i*), and let **g**[*t*] be the cost vector of all *n* experts. Then the cost function is the expected cost of choosing an expert according to distribution **x**, and it is given by the linear function ![](images/pg3-in-2.png).

Thus, prediction from expert advice is a special case of OCO, in which the decision set is the simplex and the cost functions are linear and bounded, in the *ℓ*[∞] norm, to be at most 1. The bound on the cost functions is derived from the bound on the elements of the cost vector **g**[*t*].

The fundamental importance of the experts problem in machine learning warrants special attention, and we shall return to it and analyze it in detail at the end of this chapter.

### 1.2.2 Online spam filtering

Consider an online spam-filtering system. Repeatedly, emails arrive in the system and are classified as spam or valid. Obviously, such a system has to cope with adversarially generated data and dynamically change with the varying input—a hallmark of the OCO model.

The linear variant of this model is captured by representing the emails as vectors according to the bag-of-words representation. Each email is represented as a vector **a** ∈ ℝ^(*d*), where *d* is the number of words in the dictionary. The entries of this vector are all zero, except for those coordinates that correspond to words appearing in the email, which are assigned the value 1.

To predict whether an email is spam, we learn a filter, such as a vector **x** ∈ ℝ^(*d*). Usually, a bound on the Euclidean norm of this vector is decided a priori and is a parameter of great importance in practice.

Classification of an email **a** ∈ ℝ^(*d*) by a filter **x** ∈ ℝ^(*d*) is given by the sign of the inner product between these two vectors—that is, ![](images/pg4-in-1.png)(with, for example, + 1 meaning valid and − 1 meaning spam).

In the OCO model of online spam filtering, the decision set is taken to be the set of all such norm-bounded linear filters (i.e., the Euclidean ball of a certain radius). The cost functions are determined according to a stream of incoming emails arriving into the system, and their labels (which may be known by the system, partially known, or not known at all). Let (**a***, b*) be an email/label pair. Then the corresponding cost function over filters is given by *f*(**x**) = *ℓ*(![](images/b-cap.png)*, b*). Here, ![](images/b-cap.png)is the classification given by the filter **x**, *b* is the true label, and *ℓ* is a convex loss function, such as the scaled square loss ![](images/pg4-in-2.png).

At this point, the reader may wonder: why use a square loss rather than any other function? The most natural choice is perhaps a loss of 1 if *b* = ![](images/b-cap.png)and zero otherwise.

To answer this question, notice first that if both *b* and ![](images/b-cap.png)are binary and in {−1, 1}, then the square loss is indeed 1 or zero. However, moving to a continuous function allows much more flexibility in the decision-making process. For example, we can allow the algorithm to return a number in the interval \[−1, 1\] depending on its confidence.

Another reason has to do with the algorithmic efficiency of finding a good solution. This will be the subject of future chapters.

### 1.2.3 Online shortest paths

In the online shortest-path problem, the decision maker is given a directed graph *G* = (*V, E*) and a source-sink pair *u, v* ∈ *V*. At each iteration *t* ∈ \[*T*\], the decision maker chooses a path *p*[*t*] ∈𝒫[*u,v*], where 𝒫[*u,v*] ⊆ *E*^(|*V*|) is the set of all *u*\-*v*\-paths in the graph. The adversary independently chooses weights (lengths) on the edges of the graph, given by a function from the edges to the real numbers **w**[*t*]: *E* ↦ ℝ, which can be represented as a vector **w**[*t*] ∈ ℝ^(*m*), where *m* = |*E*|. The decision maker suffers and observes a loss, which is the weighted length of the chosen path ![](images/pg5-in-1.png).

The discrete description of this problem as an experts problem, where we have an expert for each path, presents an efficiency challenge. There are potentially exponentially many paths in terms of the graph representation size.

Alternatively, the online shortest-path problem can be cast in the OCO framework as follows. Recall the standard description of the set of all distributions over paths (flows) in a graph as a convex set in ℝ^(*m*), with *O*(*m* + |*V*|) constraints ([figure 1.1](#chapter_1.xhtml#fig1-1)). Denote this flow polytope as 𝒦. The expected cost of a given flow **x** ∈𝒦 (distribution over paths) is then a linear function, given by ![](images/pg5-in-2.png), where, as defined previously, **w**[*t*](*e*) is the length of the edge *e* ∈ *E*. This inherently succinct formulation leads to computationally efficient algorithms.

![Figure 1.1 Linear equalities and inequalities that define the flow polytope, which is the convex hull of all u-v paths](images/figure1-1.png)

[Figure 1.1](#chapter_1.xhtml#rfig1-1)  
Linear equalities and inequalities that define the flow polytope, which is the convex hull of all *u*\-*v* paths

### 1.2.4 Portfolio selection

In this section, we consider a portfolio selection model that makes no statistical assumptions about the stock market (as opposed to the standard geometric Brownian motion model for stock prices), and is called the *universal portfolio selection* model.

At each iteration *t* ∈ \[*T*\], the decision maker chooses a distribution of her wealth over *n* assets **x**[*t*] ∈ Δ[*n*]. The adversary independently chooses market returns for the assets (i.e., a vector **r**[*t*] ∈ ℝ^(*n*) with strictly positive entries such that each coordinate **r**[*t*](*i*) is the price ratio for the *i*th asset between the iterations *t* and *t* + 1). The ratio between the wealth of the investor at iterations *t* + 1 and *t* is ![](images/pg6-in-1.png), and hence the gain in this setting is defined to be the logarithm of this change ratio in wealth ![](images/pg6-in-2.png). Notice that since **x***t* is the distribution of the investor’s wealth, even if **x**[*t*+1] = **x**[*t*], the investor may still need to trade in order to adjust for price changes.

The goal of regret minimization, which in this case corresponds to minimizing the difference of ![](images/pg6-in-3.png), has an intuitive interpretation. The first term is the logarithm of the wealth accumulated by the best possible in-hindsight distribution, **x**^(*⋆*). Since this distribution is fixed, it corresponds to a strategy of rebalancing the position after every trading period; hence, it is called a *constant rebalanced portfolio*. The second term is the logarithm of the wealth accumulated by the online decision maker. Hence, regret minimization corresponds to maximizing the ratio of the investor’s wealth to the wealth of the best benchmark from a pool of investing strategies.

A *universal portfolio selection algorithm* is defined to be one that, in this setting, attains regret converging to zero. Such an algorithm, albeit requiring exponential time, was first described by Cover (see section 1.4). The OCO framework has given rise to much more efficient algorithms based on Newton’s method. We shall return to study these in detail in chapter 4.

### 1.2.5 Matrix completion and recommendation systems

The prevalence of large-scale media delivery systems such as Netflix, Spotify, and many others, gives rise to very large-scale recommendation systems. One of the most popular and successful models for automated recommendation is the matrix completion model. In this mathematical model, recommendations are thought of as composing a matrix. The customers are represented by the rows, the various media are the columns, and at the entry corresponding to a particular user/media pair, we have a value scoring the preference of the user for that particular media.

For example, for the case of binary recommendations for music, we have a matrix *X* ∈{0, 1}^(*n*×*m*), where *n* is the number of persons considered, *m* is the number of songs in our library, and 0 and 1 signify dislike and like, respectively:

![](images/pg6.png)

In the online setting, for each iteration, the decision maker outputs a preference matrix *X*[*t*] ∈𝒦, where 𝒦⊆{0, 1}^(*n*×*m*) is a subset of all possible 0/1 matrices. An adversary then chooses a user/song pair (*i*[*t*]*, j*[*t*]) along with a “real” preference for this pair *y*[*t*] ∈{0, 1}. Thus, the loss experienced by the decision maker can be described by the convex loss function:

![](images/pg7.png)

The natural comparator in this scenario is a low-rank matrix, which corresponds to the intuitive assumption that preference is determined by few unknown factors. Regret with respect to this comparator means performing, on average, as few preference-prediction errors as the best low-rank matrix.

We return to this problem and explore efficient algorithms for it in chapter 7.

## 1.3 A Gentle Start: Learning from Expert Advice

Consider the following fundamental iterative decision making problem.

At each time step *t* = 1, 2*, …, T*, the decision maker faces a choice between two actions, *A* or *B* (i.e., buy or sell a certain stock). The decision maker has assistance in the form of *N* “experts” that offer their advice. After making a choice between the two actions, the decision maker receives feedback in the form of a loss associated with each decision. For simplicity, one of the actions receives a loss of zero (i.e., the “correct” decision) and the other a loss of 1.

We make the following elementary observations:

*   1.   A decision maker that chooses an action uniformly at random for each iteration, trivially attains a loss of ![](images/pg7-in-1.png)and is *correct* 50% of the time.
*   2.   In terms of the number of mistakes, no algorithm can do better in the worst case! In a later exercise, we will devise a randomized setting in which the expected number of mistakes of any algorithm is at least ![](images/pg7-in-2.png).

We are thus motivated to consider a *relative performance metric*: can the decision maker make as few mistakes as the best expert in hindsight? Theorem 1.1 shows that the answer in the worst case is negative for a deterministic decision maker.

**Theorem 1.1** *Let ![](images/pg7-in-3.png)denote the number of mistakes made by the best expert in hindsight. Then there does not exist a deterministic algorithm that can guarantee fewer than* 2*L mistakes.*

*Proof.* Assume that there are only two experts, and one always chooses option *A* while the other always chooses option *B*. Consider the setting in which an adversary always chooses the opposite of our prediction (she can do so, since our algorithm is deterministic). Then, the total number of mistakes the algorithm makes is *T*. However, the best expert makes no more than ![](images/pg7-in-4.png)mistakes (at every iteration, exactly one of the two experts is mistaken). Therefore, there is no algorithm that can always guarantee fewer than 2*L* mistakes.

☐

This observation motivates the design of random decision-making algorithms, and indeed, the OCO framework gracefully models decisions on a continuous probability space. Henceforth, we prove lemmas 1.1 and 1.2, which show the following:

**Theorem 1.2** *Let ![](images/pg8-in-1.png). Suppose the best expert makes L mistakes. Then:*

*   1.   *There is an efficient deterministic algorithm that can guarantee fewer than ![](images/pg8-in-2.png)mistakes;*
*   2.   *There is an efficient randomized algorithm for which the expected number of mistakes is at most ![](images/pg8-in-3.png).*

### 1.3.1 The weighted majority algorithm

The weighted majority (WM) algorithm is intuitive to describe: Each expert *i* is assigned a weight *W*[*t*](*i*) at every iteration *t*. Initially, we set *W*[1](*i*) = 1 for all experts *i* ∈ \[*N*\]. For all *t* ∈ \[*T*\], let *S*[*t*](*A*)*, S*[*t*](*B*) ⊆ \[*N*\] be the set of experts that choose *A* (and, respectively, *B*) at time *t*. Define

![](images/pg8-1.png)

and predict according to

![](images/pg8-2.png)

Next, update the weights *W*[*t*](*i*) as follows:

![](images/pg8-3.png)

where *ε* is a parameter of the algorithm that will affect its performance. This concludes the description of the WM algorithm. We proceed to bound the number of mistakes it makes.

**Lemma 1.1** *Denote by M*[*t*] *the number of mistakes the algorithm makes until time t, and by M*[*t*](*i*) *the number of mistakes made by expert i until time t. Then, for any expert i* ∈ \[*N*\]*, we have*

![](images/pg8-4.png)

We can optimize *ε* to minimize this bound. The expression on the right side is of the form *f*(*x*) = *ax* + *b/x*, which reaches its minimum at ![](images/pg8-in-4.png). Therefore, the bound is minimized at ![](images/pg8-in-5.png). Using this optimal value of *ε*, we get that for the best expert *i*^(*⋆*):

![](images/pg9-1.png)

Of course, this value of *ε*^(*⋆*) cannot be used in advance since we do not know which expert is the best one to choose ahead of time (and therefore we do not know the value of *M*[*T*](*i*^(*⋆*))). However, we shall see later that the same asymptotic bound can be obtained even without this prior knowledge.

Let us now prove lemma 1.1.

*Proof.* Let ![](images/pg9-in-1.png)for all *t* ∈ \[*T*\], and note that Φ[1] = *N*.

Notice that Φ[*t*+1] ≤ Φ[*t*]. However, on iterations in which the WM algorithm erred, we have

![](images/pg9-2.png)

the reason being that experts with at least half the total weight were wrong (or else WM would not have erred), and therefore

![](images/pg9-3.png)

From both observations,

![](images/pg9-4.png)

On the other hand, by definition, we have for any expert *i* that

![](images/pg9-5.png)

Since the value of *W*[*T*](*i*) is always less than the sum of all weights Φ[*T*], we conclude that

![](images/pg9-6.png)

Taking the logarithm of both sides, we get

![](images/pg9-7.png)

Next, we use the approximations

![](images/pg9-8.png)

which follow from the Taylor series of the logarithm function, to obtain

![](images/pg9-9.png)

and the lemma follows.

☐

### 1.3.2 Randomized weighted majority

In the randomized version of the WM algorithm, denoted as RWM, we choose expert *i* w.p. ![](images/pg10-in-1.png)at time *t*.

**Lemma 1.2** *Let M*[*t*] *denote the number of mistakes made by RWM until iteration t. Then, for any expert i* ∈ \[*N*\]*, we have*

![](images/pg10-1.png)

The proof of this lemma is very similar to lemma 1.1, where the factor of 2 is saved by the use of randomness.

*Proof.* As before, let ![](images/pg10-in-2.png)for all *t* ∈ \[*T*\], and note that Φ[1] = *N*. Let ![](images/pg10-in-3.png)be the indicator variable that equals 1 if the RWM algorithm makes a mistake on iteration *t*. Let *m*[*t*](*i*) equal 1 if the *i*th expert makes a mistake on iteration *t* and zero otherwise. Inspecting the sum of the weights, we get

![](images/pg10-2.png)

On the other hand, by definition, we have for any expert *i* that

![](images/pg10-3.png)

Since the value of *W*[*T*](*i*) is always less than the sum of all weights Φ[*T*], we conclude that

![](images/pg10-4.png)

Taking the logarithm of both sides, we get

![](images/pg10-5.png)

Next, we use the approximation

![](images/pg10-6.png)

to obtain

![](images/pg10-7.png)

and the lemma follows.

☐

### 1.3.3 Hedge

The RWM algorithm is in fact more general: instead of considering a discrete number of mistakes, we can consider measuring the performance of an expert by a nonnegative real number *ℓ*[*t*](*i*), which we refer to as the *loss* of the expert *i* at iteration *t*. The RWM algorithm guarantees that a decision maker following its advice will incur an average expected loss approaching that of the best expert in hindsight.

Historically, this was observed by a different and closely related algorithm called Hedge (see [algorithm 1.1](#chapter_1.xhtml#algo1-1)), whose total loss bound will be of interest to us later in the book.

![](images/Algorithm1-1.png)

Henceforth, denote in vector notation the expected loss of the algorithm as

![](images/pg11-1.png)

**Theorem 1.3** *Let* ![](images/pg11-in-1.png)*denote the N-dimensional vector of square losses (i.e.,* ![](images/pg11-in-2.png), *let ε >* 0*), and assume all losses to be nonnegative. The Hedge algorithm satisfies the following for any expert i*^(*⋆*) ∈ \[*N*\]*:*

![](images/pg11-2.png)

*Proof.* As before, let ![](images/pg11-in-3.png)for all *t* ∈ \[*T*\], and note that Φ[1] = *N*.

Inspecting the sum of weights:

![](images/pg11-3.png)

 

![](images/pg12-1.png)

On the other hand, by definition, for expert *i*^(*⋆*) we have that

![](images/pg12-2.png)

Since the value of *W*[*T*](*i*^(*⋆*)) is always less than the sum of all weights Φ[*t*], we conclude that

![](images/pg12-3.png)

Taking the logarithm of both sides, we get

![](images/pg12-4.png)

and the theorem follows by simplifying.

☐

## 1.4 Bibliographic Remarks

The OCO model was first defined by Zinkevich (2003) and has since become widely influential in the learning community and significantly extended since (for a thesis and surveys, see Hazan 2006, 2011; Shalev-Shwartz 2011).

The problem of prediction from expert advice and the WM algorithm were devised in Littlestone and Warmuth (1989, 1994). This seminal work was one of the first uses of the multiplicative updates method—a ubiquitous meta-algorithm in computation and learning, see Arora et al. (2012) for more details. The Hedge algorithm was introduced by Freund and Schapire (1997).

The universal portfolio selection model was put forth in Cover (1991), and it is one of the first examples of a worst-case online learning model. Cover gave an optimal-regret algorithm for universal portfolio selection that runs in exponential time. A polynomial time algorithm was given in Kalai and Vempala (2003), which was further sped up in (Agarwal et al. 2006; Hazan et al. 2007). Numerous extensions to the model also appeared in the literature, including addition of transaction costs (Blum and Kalai 1999) and relation to the geometric Brownian motion model for stock prices (Hazan and Kale 2009).

In their influential paper, Awerbuch and Kleinberg (2008) put forth the application of OCO to online routing. A great deal of work has been devoted since then to improve the initial bounds, and to generalize it into a complete framework for decision making with limited feedback. This framework is an extension of OCO called *bandit convex optimization (BCO)* . We defer further bibliographic remarks to chapter 6, which is devoted to the BCO framework.

## 1.5 Exercises

*   **1.**   (Attributed to Claude Shannon)  
    Construct market returns over two stocks for which the wealth accumulated over any single stock decreases exponentially, whereas the best constant rebalanced portfolio increases wealth exponentially. More precisely, construct two sequences of numbers in the range (0, ∞), that represent returns such that

**(a)** Investing in any of the individual stocks results in an exponential decrease in wealth. This means that the product of the prefix of numbers in each of these sequences decreases exponentially.

**(b)** Investing evenly on the two assets and rebalancing after every iteration increases wealth exponentially.

*   **2.   (a)** Consider an experts problem in which the losses are between zero and a positive real number *G >* 0. Give an algorithm that attains an expected loss upper-bounded by

![](images/pg13-1.png)

for the best constant *c* that you can. (The constant *c* should be independent of the number of game iterations *T* and the number of experts *N*. Assume that *T* is known in advance.)

**(b)** Suppose that the upper bound *G* is not known in advance. Give an algorithm whose performance is asymptotically as good as your algorithm in part (a), up to an additive and/or multiplicative constant that is independent of *T, N, G*. Prove your claim.

**3.** Consider an experts problem in which the losses can be negative and are real numbers in the range \[−1, 1\]. Give an algorithm with a regret guarantee of ![](images/pg13-in-1.png)and prove your claim.

## Notes

1.  [1](#chapter_1.xhtml#chapter1_1). Alternatively and equivalently, any performance metric for this setting should depend on the magnitude of the largest loss. This is the viewpoint taken later in the rest of this book.
    
2.  [2](#chapter_1.xhtml#chapter1_2). Here and henceforth, we denote as \[*n*\] the set of integers {1*, …, n*}.
    

# 2 Basic Concepts in Convex Optimization

In this chapter, we give a brief introduction to convex optimization and present some basic algorithms for solving convex mathematical programs. Although oﬄine convex optimization is not our main topic, it is useful to recall the basic definitions and results before we move on to online complex optimization (OCO). This will help in assessing the advantages and limitations of OCO. Furthermore, we describe some tools that will be our bread and butter later.

The material in this chapter is far from new. A broad and significantly more detailed literature exists, and the reader is referred to the bibliography at the end of this chapter for other good sources. We give here only the most elementary analysis and focus on the techniques that will be useful to us later.

## 2.1 Basic Definitions and Setup

The goal of this chapter is to minimize a continuous and convex function over a convex subset of Euclidean space. Henceforth, let 𝒦⊆ ℝ^(*d*) be a bounded convex and closed set in Euclidean space. We denote by *D* an upper bound on the diameter of 𝒦:

![](images/pg15-1.png)

A set 𝒦 is convex if for any **x**, **y** ∈𝒦, all the points on the line segment connecting **x** and **y** also belong to 𝒦. That is,

![](images/pg15-2.png)

A function *f*: 𝒦 ↦ ℝ is convex if for any **x**, **y** ∈𝒦,

![](images/pg15-3.png)

This inequality, and the generalizations thereof, are also known as *Jensen’s inequality*. Equivalently, if *f* is differentiable (i.e., its gradient ∇*f*(**x**) exists for all **x** ∈𝒦), then it is convex if and only if ∀**x**, **y** ∈𝒦:

 

![](images/pg16-1.png)

For convex and nondifferentiable functions *f*, the subgradient at **x** is *defined* to be any member of the set of vectors {∇*f*(**x**)} that satisfies this for all **y** ∈𝒦.

We denote by *G >* 0 an upper bound on the norm of the subgradients of *f* over 𝒦 (i.e., ∥∇*f*(**x**)∥≤ *G* for all **x** ∈𝒦). Such an upper bound implies that the function *f* is Lipschitz continuous with parameter *G*. That is, for all **x**, **y** ∈𝒦,

![](images/pg16-2.png)

The optimization and machine learning literature studies special types of convex functions that admit useful properties, which in turn allow more efficient optimization. Notably, we say that a function is *α*\-strongly convex if

![](images/pg16-3.png)

A function is *β*\-smooth if

![](images/pg16-4.png)

The latter condition is equivalent to a Lipschitz condition over the gradients. That is,

![](images/pg16-5.png)

If the function is twice differentiable and admits a second derivative, known as a *Hessian* for a function of several variables, these conditions are equivalent to the following condition on the Hessian, denoted as ∇²*f*(**x**):

![](images/pg16-6.png)

where *A* ≼ *B* if the matrix *B* − *A* is positive semidefinite (PSD).

When the function *f* is both *α*\-strongly convex and *β*\-smooth, we say that it is *γ*\-well-conditioned, where *γ* is the ratio between strong convexity and smoothness, also called the *condition number* of *f*:

![](images/pg16-7.png)

### 2.1.1 Projections onto convex sets

In the following algorithms, we shall use a projection onto a convex set, which is defined as the closest point in terms of Euclidean distance^([1](#chapter_2.xhtml#chapter2-1)) inside the convex set to a given point. Formally,

![](images/pg16-8.png)

When clear from the context, we shall remove the 𝒦 subscript. It is left as an exercise to the reader to prove that the projection of a given point over a closed, bounded, and convex set exists and is unique.

The computational complexity of projections is a subtle issue that depends heavily on the characterization of 𝒦 itself. Most generally, 𝒦 can be represented by a membership oracle—an efficient procedure that is capable of deciding whether a given **x** belongs to 𝒦 or not. In this case, projections can be computed in polynomial time. In certain special cases, projections can be computed very efficiently in near-linear time. The computational cost of projections, as well as optimization algorithms that avoid them altogether, are discussed in chapter 7.

A crucial property of projections that we shall make extensive use of is expressed by the Pythagorean theorem, which we state here for completeness.

![Figure 2.1 The Pythagorean theorem](images/figure2-1.png)

Figure 2.1  
The Pythagorean theorem

**Theorem 2.1 (Pythagoras, c. 500 BC)** *Let* 𝒦⊆ ℝ^(*d*) *be a convex set, with* **y** ∈ ℝ^(*d*) *and* **x** = Π[𝒦](**y**)*. Then for any* **z** ∈𝒦*, we have*

![](images/pg17-1.png)

We note that there exists a more general version of the Pythagorean theorem. Theorem 2.1 and the definition of projections are true and valid not only for Euclidean norms, but also for projections according to other distances that are not norms. In particular, an analog of the Pythagorean theorem remains valid with respect to Bregman divergences (see chapter 5).

### 2.1.2 Introduction to optimality conditions

The standard curriculum of high school mathematics contains the basic facts concerning when a function (usually in one dimension) attains a local optimum or saddle point. The generalization of these conditions to more than one dimension is called the *Karush-Kuhn-Tucker (KKT) conditions*, and the reader is referred to the bibliographic material at the end of this chapter for an in-depth, rigorous discussion of optimality conditions in general mathematical programming.

For our purposes, we describe only briefly and intuitively here the main facts that we will require henceforth. Naturally, we restrict ourselves to convex programming, and thus a local minimum of a convex function is also a global minimum (see the exercises at the end of this chapter). In general, there can be many points in which a function is minimized, and thus we refer to the *set* of minima of a given objective function, denoted as arg min[**x**∈ℝ^(*n*)]{*f*(**x**)}.^([2](#chapter_2.xhtml#chapter2-2))

The generalization of the fact that a minimum of a convex differentiable function on ℝ is a point in which its derivative is equal to zero is given by the multidimensional analog that its gradient is zero:

![](images/pg18-1.png)

We will require a slightly more general, but equally intuitive, fact for constrained optimization: at a minimum point of a constrained convex function, the inner product between the negative gradient and direction toward the interior of 𝒦 is nonpositive. This is depicted in [figure 2.2](#chapter_2.xhtml#fig2-2), which shows that −∇*f*(**x**^(*⋆*)) defines a supporting hyperplane to 𝒦. The intuition is that if the inner product were positive, one could improve the objective by moving in the direction of the projected negative gradient. This fact is stated formally in theorem 2.2.

![Figure 2.2 Optimality conditions: negative subgradient pointing outward](images/figure2-2.png)

[Figure 2.2](#chapter_2.xhtml#rfig2-2)  
Optimality conditions: negative subgradient pointing outward

**Theorem 2.2 (Karush-Kuhn-Tucker/KKT)** *Let* 𝒦⊆ ℝ^(*d*) *be a convex set,* **x**^(*⋆*) ∈ arg min[**x**∈𝒦]*f*(**x**)*. Then for any* **y** ∈𝒦 *we have*

![](images/pg18-2.png)

## 2.2 Gradient Descent

Gradient descent (GD) is the simplest and oldest of the optimization methods. It is an *iterative method*—the optimization procedure proceeds in iterations, each improving the objective value. The basic method amounts to iteratively moving the current point in the direction of the gradient, which is a linear time operation if the gradient is given explicitly (indeed, for many functions, computing the gradient at a certain point is a simple linear-time operation).

The basic template algorithm for unconstrained optimization is given in [algorithm 2.1](#chapter_2.xhtml#algo2-1), and a depiction of the iterates that it produces is given in [figure 2.3](#chapter_2.xhtml#fig2-3).

![Figure 2.3 Iterates of the GD algorithm](images/figure2-3.png)

[Figure 2.3](#chapter_2.xhtml#rfig2-3)  
Iterates of the GD algorithm

![](images/Algorithm2-1.png)

For a convex function, there always exists a choice of stepsizes that will cause GD to converge to the optimal solution. The rates of convergence, however, differ greatly and depend on the smoothness and strong convexity properties of the objective function. [Table 2.1](#chapter_2.xhtml#tab2-1) summarizes the convergence rates of GD variants for convex functions with different convexity parameters. The rates described omit the (usually small) constants in the bounds—we focus on asymptotic rates.

[Table 2.1](#chapter_2.xhtml#rtab2-1)  
Rates of convergence of first order (gradient-based) methods as a function of the number of iterations and the smoothness and strong-convexity of the objective

![](images/pg21-in-1.png)

Dependence on other parameters and constants (namely, the Lipchitz constant, diameter of constraint set and initial distance to the objective) is omitted. Acceleration for nonsmooth functions is not possible in general.

In this section, we address only the first row of [table 2.1](#chapter_2.xhtml#tab2-1). For accelerated methods and their analysis, see the references in section 2.6.

### 2.2.1 The Polyak stepsize

Luckily, there exists a simple choice of stepsizes that yields the optimal convergence rate, called the *Polyak stepsize*. It has the huge advantage of not depending on the strong convexity and/or the smoothness parameters of the objective function.

However, it does depend on the distance in function value to the optimality and gradient norm. While the latter can be efficiently estimated, the distance to optimality is not always available if *f*(**x**^(\*)) is not known ahead of time. This can be remedied, as referred to in the bibliography.

We henceforth denote the elements as follows:

*   1.   Distance to optimality in value: *h*[*t*] = *h*(**x**[*t*]) = *f*(**x**[*t*]) − *f*(**x**^(\*))
*   2.   Euclidean distance to optimality: *d*[*t*] = ∥**x**[*t*] −**x**^(\*)∥
*   3.   Current gradient norm ∥∇[*t*]∥ = ∥∇*f*(**x**[*t*])∥

With these notations, we can describe the algorithm precisely as shown in [algorithm 2.2](#chapter_2.xhtml#algo2-2).

![](images/Algorithm2-2.png)

To prove precise convergence bounds, assume ∥∇[*t*]∥≤ *G*, and define as follows:

![](images/pg21-1.png)

We can now state the main guarantee of GD with the Polyak stepsize:

**Theorem 2.3** *(GD with the Polyak Stepsize) [algorithm 2.2](#chapter_2.xhtml#algo2-2) guarantees the following after T steps:*

![](images/pg22-1.png)

### 2.2.2 Measuring distance to optimality

When analyzing convergence of gradient methods, it is useful to use potential functions in lieu of function distance to optimality, such as gradient norm and/or Euclidean distance. The following relationships in lemma 2.1 hold between these quantities.

**Lemma 2.1** *The following properties hold for α\-strongly convex functions and/or β\-smooth functions over Euclidean space* ℝ^(*d*)*:*

*   *1.   ![](images/pg22-in-1.png)*
*   *2.   ![](images/pg22-in-2.png)*
*   *3.   ![](images/pg22-in-3.png)*
*   *4.   ![](images/pg22-in-4.png)*

*Proof.* 1.   ![](images/pg22-in-5.png):

By strong convexity, we have

![](images/pg22-2.png)

where the last inequality follows since the gradient at the global optimum is zero.

*   2.   ![](images/pg22-in-6.png):
    
    By smoothness,
    

![](images/pg22-3.png)

where the last inequality follows since the gradient at the global optimum is zero.

*   3.   ![](images/pg22-in-7.png): Using smoothness, and let **x**[*t*+1] = **x**[*t*] − *η*∇[*t*] for ![](images/pg22-in-8.png):

 

![](images/pg23-1.png)

*   4.   ![](images/pg23-in-1.png):

We have, for any pair **x**, **y** ∈ ℝ^(*d*):

![](images/pg23-2.png)

In particular, taking **x** = **x**[*t*], **y** = **x**^(*⋆*), we get

![](images/eq2-1.png)

☐

### 2.2.3 Analysis of the Polyak stepsize

We are now ready to prove theorem 2.3, which directly follows from lemma 2.2.

**Lemma 2.2** *Suppose that a sequence* **x**[0]*, …***x**[*t*] *satisfies*

![](images/eq2-2.png)

*then, for* **x** *as defined in the algorithm, we have*

![](images/pg23-3.png)

*Proof.* The proof analyzes the following cases.

*   1.   For convex functions with gradient bounded by *G*,

![](images/pg23-4.png)

Summing up over *T* iterations, and using Cauchy-Schwartz on the *T*\-dimensional vectors of ![](images/pg24-in-1.png)and (*h*[1]*, …, h*[*T*]), we have

![](images/pg24-1.png)

*   2.   For smooth functions whose gradient is bounded by *G*, lemma 2.1 implies the following:

![](images/pg24-2.png)

*   3.   For strongly convex functions, lemma 2.1 implies the following:

![](images/pg24-3.png)

This implies that ![](images/pg24-in-4.png), which can be seen by induction.^([3](#chapter_2.xhtml#chapter2-3)) The proof is completed as follows:^([4](#chapter_2.xhtml#chapter2-4))

![](images/pg24-4.png)

Thus, there exists a *t* for which ![](images/pg24-in-5.png). Taking the square root completes the claim.

*   4.   For both strongly convex and smooth functions,

![](images/pg24-5.png)

Thus,

![](images/pg25-1.png)

This completes the proof of all cases.

☐

## 2.3 Constrained Gradient/Subgradient Descent

The vast majority of the problems considered in this text include constraints. Consider the examples given in section 1.2 of chapter 1: a path is a point in the flow polytope, a portfolio is a point in the simplex, and so on. In the language of optimization, we require **x** not only to minimize a certain objective function, but also to belong to a convex set 𝒦.

In this section, we describe and analyze constrained GD. Algorithmically, the change from the previous section is small: after updating the current point in the direction of the gradient, one may need to project back to the decision set. However, the analysis is somewhat more involved, and instructive for the later parts of this text.

### 2.3.1 Basic GD—linear convergence

[Algorithm 2.3](#chapter_2.xhtml#algo2-3) describes a template for GD over a constrained set. It is a template since the sequence of stepsizes {*η*[*t*]} is left as an input parameter, and the several variants of the algorithm differ on its choice.

![](images/Algorithm2-3.png)

As opposed to the unconstrained setting, here we require a precise setting of the learning rate to obtain the optimal convergence rate.

**Theorem 2.4** *For constrained minimization of γ\-well-conditioned functions and ![](images/pg25-in-1.png), [algorithm 2.3](#chapter_2.xhtml#algo2-3) converges as*

![](images/pg25-2.png)

*Proof.* By strong convexity, we have the following for every **x**, **x**[*t*] ∈𝒦 (where we denote ∇[*t*] = ∇*f*(**x**[*t*]) as before):

![](images/eq2-3.png)

Next, appealing to the algorithm’s definition and the choice ![](images/pg26-in-1.png), we have

![](images/eq2-4.png)

To see this, notice that

![](images/pg26-1.png)

Thus, we have

![](images/pg26-2.png)

The minimum can grow only if we take it over a subset of 𝒦. Thus we can restrict our attention to all points that are a convex combination of **x**[*t*] and **x**^(*⋆*), which we denote by the interval \[**x**[*t*], **x**^(*⋆*)\] = {(1 − *μ*)**x**[*t*] + *μ***x**^(*⋆*)*, μ* ∈ \[0, 1\]}, and write

![](images/pg26-3.png)

where the equality is by writing **x** as **x** = (1 − *μ*)**x**[*t*] + *μ***x**^(*⋆*). By strong convexity, we have for any **x**[*t*] and the minimizer **x**^(*⋆*):

![](images/pg26-4.png)

Thus, plugging this into equation ([2.5](#chapter_2.xhtml#eq2-5)), we get

![](images/pg27-1.png)

This gives the theorem statement by induction.

☐

## 2.4 Reductions to Nonsmooth and Nonstrongly Convex Functions

Section 2.3 dealt with *γ*\-well-conditioned functions, which may seem like a significant restriction over vanilla convexity. Indeed, many interesting convex functions are not strongly convex nor smooth, and as we have seen, the convergence rate of GD greatly differs for these functions. We have completed the picture for unconstrained optimization, and in this section, we complete it for a bounded set.

The literature on first-order methods is abundant, with specialized analyses that explore the convergence rate of GD for more general functions. In this discussion, we take a different approach: instead of analyzing variants of GD from scratch, we use reductions to derive near-optimal convergence rates for smooth functions that are not strongly convex, strongly convex functions that are not smooth, or general convex functions without any further restrictions.

While attaining suboptimal convergence bounds (by logarithmic factors), the advantage of this approach is twofold: first, the reduction method is very simple to state and analyze, and its analysis is significantly shorter than analyzing GD from scratch. Second, the reduction method is generic, and thus extends to the analysis of accelerated GD (or any other first-order method) along the same lines. We turn to these reductions next.

### 2.4.1 Reduction to smooth, nonstrongly convex functions

Our first reduction applies the GD algorithm to functions that are *β*\-smooth but not strongly convex.

The idea is to add a controlled amount of strong convexity to function *f*, and then apply the [algorithm 2.3](#chapter_2.xhtml#algo2-3) to optimize the new function. The solution is distorted by the added strong convexity, but a trade-off guarantees a meaningful convergence rate.

 ![](images/Algorithm2-4.png)

**Lemma 2.3** *For β\-smooth convex functions, [algorithm 2.4](#chapter_2.xhtml#algo2-4) with parameter ![](images/pg28-in-1.png)converges as*

![](images/pg28-1.png)

*Proof.* The function *g* is ![](images/alpha-tilde.png)\-strongly convex and (*β* + ![](images/alpha-tilde.png))-smooth (see exercises). Thus, it is ![](images/pg28-in-2.png)\-well-conditioned. Notice that

![](images/pg28-2.png)

Here, we denote ![](images/pg28-in-3.png). Since *g*(**x**) is ![](images/pg28-in-4.png)\-well-conditioned,

![](images/pg28-3.png)

where we ignore constants and terms depending on *D* and ![](images/pg28-in-5.png).

☐

Stronger convergence rates of ![](images/pg28-in-6.png)can be obtained by analyzing GD from scratch, and these are known to be tight. Thus, our reduction is suboptimal by a factor of *O*(log *T*), which we tolerate for the reasons stated at the beginning of this section.

### 2.4.2 Reduction to strongly convex, nonsmooth functions

Our reduction from nonsmooth functions to *γ*\-well-conditioned functions is similar in spirit to the one described in the previous subsection. However, whereas for strong convexity the obtained rates were off by a factor of log *T*, in this section we will also be off by factor of *d*, the dimension of the decision variable **x**, as compared to the standard analyses in convex optimization. For tight bounds, the reader is referred to the excellent reference books and surveys listed in section 2.6.

![](images/Algorithm2-5.png)

We apply the GD [algorithm 2.1](#chapter_2.xhtml#algo2-1) to a smoothed variant of the objective function. In contrast to the previous reduction, smoothing cannot be obtained by the simple addition of a smooth (or any other) function. Instead, we need a smoothing operation. The one we describe is particularly simple and amounts to taking a local integral of the function. More sophisticated, but less general, smoothing operators exist that are based on the Moreau-Yoshida regularization (see bibliographic section for more details).

Let *f* be *G*\-Lipschitz continuous and *α*\-strongly convex. Define for any *δ >* 0,

![](images/pg29-1.png)

where 𝔹 = {**x** ∈ ℝ^(*d*): ∥**x**∥≤ 1} is the Euclidean ball and **v** *∼* 𝔹 denotes a random variable drawn from the uniform distribution over 𝔹. When function *f* is clear from the context, we henceforth use the simpler notation ![](images/pg29-in-1.png).

We will prove that the function ![](images/pg29-in-2.png)is a smooth approximation to *f*: ℝ^(*d*) ↦ ℝ; that is, it is both smooth and close in value to *f*, as given in lemma 2.4.

**Lemma 2.4** ![](images/pg29-in-3.png)*has the following properties:*

*   *1.   If f is α\-strongly convex, then so is* ![](images/pg29-in-4.png)
*   *2.   *![](images/pg29-in-5.png)*is ![](images/pg29-in-6.png)\-smooth*
*   *3.   *![](images/pg29-in-7.png)*for all* **x** ∈𝒦.

Before proving this lemma, let us first complete the reduction. Using lemma 2.4 and the convergence for *γ*\-well-conditioned functions, the following approximation bound is obtained.

**Lemma 2.5** *For ![](images/pg29-in-8.png), [algorithm 2.5](#chapter_2.xhtml#algo2-5) converges as*

![](images/pg29-2.png)

Before proving this lemma, notice that the GD method is applied with gradients of the smoothed function ![](images/pg29-in-9.png)rather than gradients of the original objective *f*. In this section, we ignore the computational cost of computing such gradients given only access to gradients of *f*, which may be significant. Techniques for estimating these gradients are further explored in chapter 6.

*Proof.* Note that by lemma 2.4, the function ![](images/pg30-in-1.png)is *γ*\-well-conditioned for ![](images/pg30-in-2.png)

![](images/pg30-1.png)

We proceed to prove that ![](images/pg30-in-3.png)is indeed a good approximation to the original function.

*Proof of lemma 2.4*. First, since ![](images/pg30-in-4.png)is an average of *α*\-strongly convex functions, it is also *α*\-strongly convex. In order to prove smoothness, we will use Stokes’ theorem from calculus: For all **x** ∈ ℝ^(*d*) and for a vector random variable **v** that is uniformly distributed over the Euclidean sphere 𝕊 = {**y** ∈ ℝ^(*d*): ∥**y**∥ = 1},

![](images/eq2-5.png)

Recall that function *f* is *β*\-smooth if and only if for all **x**, **y** ∈𝒦, it holds that ∥∇*f*(**x**) −∇*f*(**y**)∥≤ *β*∥**x** −**y**∥. Now,

![](images/pg30-2.png)

This proves the second property of lemma 2.4. We proceed to show the third property—namely, that ![](images/pg30-in-5.png)is a good approximation to *f*:

![](images/pg30-3.png)

![](images/pg31-1.png)

We note that GD variants for *α*\-strongly convex functions, even without the smoothing approach used in our reduction, are known to converge quickly and without dependence on the dimension. We state the known algorithm and result in theorem 2.5 without proof (see the bibliography for references).

**Theorem 2.5** *Let f be α\-strongly convex, and let* **x**[1]*, …*, **x**[*t*] *be the iterates of [algorithm 2.3](#chapter_2.xhtml#algo2-3) applied to f with ![](images/pg31-in-1.png). Then*

![](images/pg31-2.png)

### 2.4.3 Reduction to general convex functions

One can apply both reductions simultaneously to obtain a rate of ![](images/pg31-in-2.png). While near-optimal in terms of the number of iterations, the weakness of this bound lies in its dependence on the dimension. In chapter 3, we shall show a rate of ![](images/pg31-in-3.png)as a direct consequence of a more general online convex optimization algorithm.

## 2.5 Example: Support Vector Machine Training

To illustrate the usfulness of the gradient descent method, let us describe an optimization problem that has gained much attention in machine learning and can be solved efficiently using the methods we have just analyzed.

A very basic and successful learning paradigm is the linear classification model. In this model, the learner is presented with positive and negative examples of a concept. Each example, denoted by **a**[*i*], is represented in Euclidean space by a *d*\-dimensional feature vector. For example, a common representation for emails in the spam-classification problem are binary vectors in Euclidean space, where the dimension of the space is the number of words in the language. The *i*th email is a vector **a**[*i*] whose entries are given as 1s for coordinates corresponding to words that appear in the email, and zero otherwise.^([5](#chapter_2.xhtml#chapter2-5)) In addition, each example has a label *b*[*i*] ∈{−1, + 1}, corresponding to whether the email has been labeled spam or not spam. The goal is to find a hyperplane separating the two classes of vectors: those with positive labels and those with negative labels. If such a hyperplane, which completely separates the training set according to the labels, does not exist, then the goal is to find a hyperplane that achieves a separation of the training set with the smallest number of mistakes.

Mathematically, given a set of *n* examples to train on, we seek **x** ∈ ℝ^(*d*), which minimizes the number of incorrectly classified examples; that is,

![](images/eq2-6.png)

where sign(*x*) ∈{−1, + 1} is the sign function, and *δ*(*z*) ∈{0, 1} is the indicator function that takes the value 1 if the condition *z* is satisfied and zero otherwise.

This optimization problem, which is at the heart of the linear classification formulation, is NP-hard, and in fact it is NP-hard to even approximate nontrivially.^([6](#chapter_2.xhtml#chapter2-6)) However, in the special case that a linear classifier (a hyperplane **x**) that classifies all the examples correctly exists, the problem is solvable in polynomial time via linear programming.

Various relaxations have been proposed to solve the more general case, when no perfect linear classifier exists. One of the most successful in practice is the support vector machine (SVM) formulation.

The soft margin SVM relaxation replaces the 0/1 loss in equation ([2.6](#chapter_2.xhtml#eq2-6)) with a convex loss function, called the *hinge loss*, given by

![](images/pg32-1.png)

In [figure 2.4](#chapter_2.xhtml#fig2-4), we depict how the hinge loss is a convex relaxation for the nonconvex 0/1 loss. Further, the SVM formulation adds to the loss minimization objective a term that regularizes the size of the elements in **x**. The reason and meaning of this additional term shall be addressed in later sections. For now, let us consider the SVM convex program:

![](images/eq2-7.png) ![](images/Algorithm2-6.png)![Figure 2.4 The hinge loss function versus the 0/1 loss function](images/figure2-4.png)

[Figure 2.4](#chapter_2.xhtml#rfig2-4)  
The hinge loss function versus the 0/1 loss function

This is an unconstrained nonsmooth and strongly convex program. It follows from theorems 2.3 and 2.5 that ![](images/pg33-in-1.png)iterations suffice to attain an *ε*\-approximate solution. We spell out the details of applying the subgradient descent algorithm to this formulation in [algorithm 2.6](#chapter_2.xhtml#algo2-6).

Notice that the learning rates are left unspecified, even though they can be explicitly set as in theorem 2.5 or by using the Polyak rate. The Polyak rate requires knowing the function value at optimality, although this can be relaxed (see bibliography).

A caveat of using GD for SVM is the requirement to compute the full gradient, which may require a full pass over the data for each iteration. We will see a significantly more efficient algorithm in the next chapter!

## 2.6 Bibliographic Remarks

The reader is referred to dedicated books on convex optimization for much more in-depth treatment of the topics surveyed in this background chapter. For background in convex analysis, see Borwein and Lewis (2006) and Rockafellar (1997). The classic textbook by Boyd and Vandenberghe (2004) gives a broad introduction to convex optimization with numerous applications; see also Boyd (2014). For detailed rigorous convergence proofs and in-depth analysis of first-order methods, see lecture notes by Nesterov (2004) and books by Nemirovski and Yudin (1983) and Nemirovski (2004), as well as more recent lecture notes and texts (Bubeck 2015; Hazan 2019). Theorem 2.5 is taken from Bubeck (2015) theorem 3.9.

The logarithmic overhead in the reductions of section 2.4 can be removed with more careful reduction and analysis; for details, see Allen-Zhu and Hazan (2016). A more sophisticated smoothing operator is the Moreau-Yoshida regularization: it avoids the dimension factor loss. However, it is sometimes less computationally efficient to work with (Parikh and Boyd 2014).

The Polyak learning rate is detailed in Polyak (1987). A recent exposition allows for obtaining the same optimal rate without knowledge of the optimal function value (Hazan and Kakade 2019).

Using linear separators and half-spaces to learn and separate data was considered in the very early days of artificial intelligence (Rosenblatt 1958; Minsky and Papert 1969). Notably, the Perceptron algorithm was one of the first learning algorithms, and it is closely related to GD. SVMs were introduced by Cortes and Vapnik (1995) and Boser, Guyon, and Vapnik (1992), see also Schölkopf and Smola (2002).

Learning half-spaces with the zero-one loss is computationally hard, and it is hard to even approximate it nontrivially (Daniely 2016). Proving that a problem is hard to approximate is at the forefront of computational complexity, and it also is based on novel characterizations of the complexity class NP (Arora and Barak 2009).

## 2.7 Exercises

*   **1.**   Prove that a differentiable function *f*(*x*): ℝ *→* ℝ is convex if and only if for any *x, y* ∈ℝ, it holds that *f*(*x*) − *f*(*y*) ≤ (*x* − *y*)*f*′(*x*).
*   **2.**   Recall that we say that a function *f* : ℝ^(*n*) *→* ℝ has a condition number *γ* = *α/β* over *K* ⊆ℝ^(*d*) if the following two inequalities hold for all **x**, **y** ∈𝒦:

**(a)** ![](images/pg34-in-1.png)

**(b)** ![](images/pg34-in-2.png)

    Prove that if *f* is twice differentiable and it holds that *β***I** ≽∇²*f*(**x**) ≽ *α***I** for any **x** ∈𝒦, then the condition number of *f* over 𝒦 is *α/β*.

*   **3.**   Prove the following statements:

**(a)** The sum of convex functions is convex.

**(b)** Let *f* be *α*[1]\-strongly convex and *g* be *α*[2]\-strongly convex. Then *f* + *g* is (*α*[1] + *α*[2])-strongly convex.

**(c)** Let *f* be *β*[1]\-smooth and *g* be *β*[2]\-smooth. Then *f* + *g* is (*β*[1] + *β*[2])-smooth.

*   **4.**   Let 𝒦⊆ℝ^(*d*) be bounded and closed. Prove that convexity of 𝒦 is a necessary and sufficient condition for all **x** ∈ℝ^(*d*) for Π [*K*](**x**) to be a singleton (i.e., for |Π [*K*](**x**)| = 1). To prove that this is a necessary condition, it is enough to provide a counterexample.
*   **5.**   Consider the *n*\-dimensional simplex

![](images/pg34-1.png)

Give an algorithm for computing the projection of a point **x** ∈ℝ^(*n*) onto the set Δ [*n*] (a near-linear time algorithm exists).

*   **6.**   Prove the following identity:

![](images/pg35-1.png)

*   **7.**   Let *f*(**x**): ℝ^(*n*) *→* ℝ be a convex differentiable function and 𝒦⊆ℝ^(*n*) be a convex set. Prove that **x**^(*⋆*) ∈𝒦 is a minimizer of *f* over 𝒦 if and only if for any **y** ∈𝒦, it holds that (**y** −**x**^(*⋆*))^⊤∇*f*(**x**^(*⋆*)) ≥ 0.
*   **8.**   \* Extending Nesterov’s accelerated GD algorithm:  
    Assume a black-box access to Nesterov’s algorithm that attains the rate of ![](images/pg35-in-1.png)for *γ*\-well-conditioned functions, as in [table 2.1](#chapter_2.xhtml#tab2-1). Apply a reduction to obtain the ![](images/pg35-in-2.png)rate for *β*\-smooth functions up to logarithmic factors.

## Notes

1.  [1](#chapter_2.xhtml#chapter2_1). We will discuss projections with respect to other distance notions in chapter 5.
    
2.  [2](#chapter_2.xhtml#chapter2_2). This notation stands for the arguments that minimize the expression inside the brakets, which is a subset in ℝ^(*d*).
    
3.  [3](#chapter_2.xhtml#chapter2_3). The fact that *a*[0] ≤ 1 follows from lemma 2.1. For *t* = 1, ![](images/pg191-in-1.png)since *a*[1] ≤ *a*[0](1 − *a*[0]) and 0 ≤ *a*[0] ≤ 1. For the induction step, ![](images/pg191-in-2.png).
    
4.  [4](#chapter_2.xhtml#chapter2_4). This assumes that *T* is even. *T* being odd leads to the same constants.
    
5.  [5](#chapter_2.xhtml#chapter2_5). Such a representation may seem naive at first, as it completely ignores the order of appearance and the context of the words. Extensions to capture these features are indeed studied in the natural language processing literature.
    
6.  [6](#chapter_2.xhtml#chapter2_6). See the bibliography for references that discuss these results.
    

# 3 First-Order Algorithms for Online Convex Optimization

In this chapter, we describe and analyze the simplest and most basic algorithms for online convex optimization (OCO; recall the definition of this model as introduced in chapter 1), which are also surprisingly useful and applicable in practice. We use the same notation introduced in section 2.1 in chapter 2. However, in contrast to the previous chapter, the goal of the algorithms introduced in this chapter is to minimize regret, rather than the optimization error (which is ill-defined in an online setting).

Recall the definition of regret in an OCO setting, as given in equation ([1.1](#chapter_1.xhtml#eq1-1)) in chapter 1, with subscripts, superscripts, and the supremum over the function class omitted when they are clear from the context:

![](images/pg37-1.png)

[Table 3.1](#chapter_3.xhtml#tab3-1) details known upper and lower bounds on the regret for various types of convex functions depending on the number of prediction iterations.

[Table 3.1](#chapter_3.xhtml#rtab3-1)  
Attainable asymptotic regret bounds for loss function classes

![](images/table3-1.png)

To compare regret to optimization error, it is useful to consider the average regret, or Regret*/T*. Let ![](images/pg37-in-1.png)be the average decision. If the values of function *f*[*t*] are all equal to a single function *f*: 𝒦 ↦ ℝ, then Jensen’s inequality implies that *f*(**x**[*T*]) converges to *f*(**x**^(*⋆*)) at a rate at most the average regret, since

![](images/pg37-2.png)

The reader may recall [Table 2.1](#chapter_2.xhtml#tab2-1) describing oﬄine convergence of first-order methods: as opposed to oﬄine optimization, smoothness does not improve asymptotic regret rates. However, exp-concavity, a weaker property than strong convexity, comes into play and gives improved regret rates.

This chapter will present algorithms and lower bounds that realize these known results for OCO. The property of exp-concavity and its applications, as well as logarithmic regret algorithms for exp-concave functions, are discussed in chapter 4.

## 3.1 Online Gradient Descent

Perhaps the simplest algorithm that applies to the most general setting of OCO is online gradient descent (OGD). This algorithm, which is based on standard gradient descent (GD) from oﬄine optimization, was introduced in its online form by Zinkevich (2003) (see section 3.5).

![](images/Algorithm3-1.png)

Pseudocode for the algorithm is given in [algorithm 3.1](#chapter_3.xhtml#algo3-1), and a conceptual illustration is given in [figure 3.1](#chapter_3.xhtml#fig3-1).

![Figure 3.1 OGD: the iterate xt+1 is derived by advancing xt in the direction of the current gradient ∇t and projecting back into 𝒦](images/figure3-1.png)

[Figure 3.1](#chapter_3.xhtml#rfig3-1)  
OGD: the iterate **x**[*t*+1] is derived by advancing **x**[*t*] in the direction of the current gradient ∇[*t*] and projecting back into 𝒦

In each iteration, the algorithm takes a step from the previous point in the direction of the gradient of the previous cost. This step may result in a point outside the underlying convex set. In such cases, the algorithm projects the point back to the convex set (i.e., finds its closest point in the convex set). Despite the fact that the next cost function may be completely different from the costs observed thus far, the regret attained by the algorithm is sublinear. This is formalized in theorem 3.1 (recall the definition of *G* and *D* from the previous chapter).

**Theorem 3.1** *OGD with stepsize ![](images/pg39-in-1.png)guarantees the following for all T* ≥ 1*:*

![](images/pg39-1.png)

*Proof.* Let ![](images/pg39-in-2.png). Define ![](images/pg39-in-3.png). By convexity,

![](images/eq3-1.png)

We first upper-bound ![](images/pg39-in-4.png)using the update rule for **x**[*t*+1] and theorem 2.1 in chapter 2 (the Pythagorean theorem):

![](images/eq3-2.png)

Hence,

![](images/eq3-3.png)

Summing equations ([3.1](#chapter_3.xhtml#eq3-1)) and ([3.3](#chapter_3.xhtml#eq3-3)) from *t* = 1 to *T*, and setting ![](images/pg40-in-1.png)(with ![](images/pg40-in-2.png)), we get the following:

![](images/pg40-1.png)

The last inequality follows since ![](images/pg40-in-3.png)and ![](images/pg40-in-4.png).

☐

The OGD algorithm is straightforward to implement, and updates take linear time given the gradient. However, there is a projection step that may take significantly longer, as discussed in section 2.1.1 in chapter 2 and chapter 7.

## 3.2 Lower Bounds

The previous section introduces and analyzes a very simple and natural approach to OCO. Before continuing our venture, it is worthwhile to consider whether the previous bound can be improved? We measure the performance of OCO algorithms both by regret and by computational efficiency. Therefore, we ask ourselves whether even simpler algorithms that attain tighter regret bounds exist.

The computational efficiency of OGD seemingly leaves little room for improvement, putting aside the projection step that it runs in linear time per iteration. What about obtaining better regret?

Perhaps surprisingly, the answer is negative: OGD attains, in the worst case, tight regret bounds up to small constant factors! This is formally given in theorem 3.2.

**Theorem 3.2** *Any algorithm for OCO incurs ![](images/pg41-in-1.png)regret in the worst case. This is true even if the cost functions are generated from a fixed stationary distribution.*

We give a sketch of the proof; filling in all the details is left as exercise 3 at the end of this chapter.

Consider an instance of OCO in which the convex set 𝒦 is the *n*\-dimensional hypercube:

![](images/pg41-1.png)

There are 2^(*n*) linear cost functions, one for each vertex **v** ∈{ *±* 1}^(*n*), defined as

![](images/pg41-2.png)

Notice that both the diameter of 𝒦 and the bound on the norm of the cost function gradients, denoted as G, are bounded by

![](images/pg41-3.png)

The cost functions in each iteration are chosen at random, with uniform probability, from the set {*f*[**v**], **v** ∈{ *±* 1}^(*n*)}. Denote by **v**[*t*] ∈{ *±* 1}^(*n*) the vertex chosen in iteration *t*, and denote *f*[*t*] = *f*[**v**[*t*]]. By uniformity and independence, for any *t* and **x**[*t*] chosen online, **E**[**v**[*t*]]\[*f*[*t*](**x**[*t*])\] = **E**[**v**[*t*]]\[**v**[*t*]^⊤**x**[*t*]\] = 0. However,

![](images/pg41-4.png)

The last equality is left as an exercise.

The facts given here nearly complete the proof of theorem 3.2; for more details, see exercise 3 at the end of this chapter.

## 3.3 Logarithmic Regret

At this point, the reader may wonder: We have introduced a seemingly sophisticated and obviously general framework for learning and prediction, as well as a linear-time algorithm for the most general case, complete with tight regret bounds, and done so with elementary proofs! Is this all that OCO has to offer?

There are two answers to this question:

*   1.   Simple is good: the philosophy behind OCO treats simplicity as a merit. The main reason OCO has taken the stage in online learning in recent years is the simplicity of its algorithms and their analysis, which allow for numerous variations and tweaks in their host applications.
*   2.   A very wide class of settings, which will be the subject of the next sections, admit more efficient algorithms, in terms of both regret and computational complexity.

In chapter 2 we surveyed optimization algorithms with convergence rates that vary greatly according to the convexity properties of the function to be optimized. Do the regret bounds in OCO vary as much as the convergence bounds in oﬄine convex optimization over different classes of convex cost functions?

Indeed, next we show that for important classes of loss functions significantly better regret bounds are possible.

### 3.3.1 Online gradient descent for strongly convex functions

The first algorithm that achieves regret logarithmic in the number of iterations is a twist on the OGD algorithm, changing only the stepsize. The following theorem establishes logarithmic bounds on the regret if the cost functions are strongly convex.

**Theorem 3.3** *For α\-strongly convex loss functions, OGD with stepsize ![](images/pg42-in-1.png)achieves the following guarantee for all T* ≥ 1*:*

![](images/pg42-1.png)

*Proof.* Let ![](images/pg42-in-2.png). Recall the definition of regret:

![](images/pg42-2.png)

Define ![](images/pg42-in-3.png). Applying the definition of *α*\-strong convexity to the pair of points {**x**[*t*], **x**^(\*)}, we have

![](images/eq3-4.png)

We proceed to upper-bound ![](images/pg42-in-4.png). Using the update rule for **x**[*t*+1] and theorem 2.1, we get

![](images/pg42-3.png)

Hence,

![](images/eq3-5.png)

Summing equation ([3.5](#chapter_3.xhtml#eq3-5)) from *t* = 1 to *T*, setting ![](images/pg43-in-1.png)(define ![](images/pg43-in-2.png)), and combining with equation ([3.4](#chapter_3.xhtml#eq3-4)), we have

![](images/pg43-1.png)

## 3.4 Application: Stochastic Gradient Descent

A special case of OCO is the well-studied setting of stochastic optimization. In stochastic optimization, the optimizer attempts to minimize a convex function over a convex domain as given by the mathematical program, as follows:

![](images/pg43-2.png)

However, unlike standard oﬄine optimization, the optimizer is given access to a noisy gradient oracle, defined by

![](images/pg43-3.png)

That is, given a point in the decision set, a noisy gradient oracle returns a random vector whose expectation is the gradient at the point and whose variance is bounded by *G*².

We will show that regret bounds for OCO translate to convergence rates for stochastic optimization. As a special case, consider the OGD algorithm, whose regret is bounded by

![](images/pg43-4.png)

Applying the OGD algorithm over a sequence of linear functions that are defined by the noisy gradient oracle at consecutive points, and finally returning the average of all points along the way, we obtain the stochastic gradient descent (SGD) algorithm, presented in [algorithm 3.2](#chapter_3.xhtml#algo3-2).

![](images/Algorithm3-2.png)

**Theorem 3.4** *[Algorithm 3.2](#chapter_3.xhtml#algo3-2) with stepsize ![](images/pg44-in-1.png)guarantees*

![](images/pg44-1.png)

*Proof.* For the analysis, we define the linear function ![](images/pg44-in-2.png). Using the regret guarantee of OGD, we have

![](images/pg44-2.png)

It is important to note that in this proof, we have used the fact that the regret bounds of OGD hold against an adaptive adversary. This need arises since the cost functions *f*[*t*] defined in [algorithm 3.2](#chapter_3.xhtml#algo3-2) depend on the choice of decision **x**[*t*] ∈𝒦.

In addition, the careful reader may notice that by plugging in different stepsizes (also called *learning rates*) and applying SGD to strongly convex functions, one can attain *Õ*(1*/T*) convergence rates, where the *Õ* notation hides logarithmic factors in *T*. Details of this derivation are left as exercise 1 at the end of the chapter.

### 3.4.1 Example: Stochastic gradient descent for support vector machine training

Recall the example of support vector machine (SVM) training from section 2.5 of chapter 2. The task of training an SVM over a given data set amounts to solving the following convex program (equation ([2.7](#chapter_2.xhtml#eq2-7))):

![](images/pg45-1.png)

Using the technique described in this chapter (namely, the OGD and SGD algorithms), we can devise a much faster algorithm than the one presented in the previous chapter. The idea is to generate an unbiased estimate for the gradient of the objective using a single example in the data set, and use it in lieu of the entire gradient. This is given formally in the SGD algorithm for SVM training, as presented in [algorithm 3.3](#chapter_3.xhtml#algo3-3).

![](images/Algorithm3-3.png)

It follows from theorem 3.4 that this algorithm, with appropriate parameters *η*[*t*], returns an *ε*\-approximate solution after ![](images/pg46-in-1.png)iterations. Furthermore, with a little more care and using theorem 3.3, a rate of ![](images/pg46-in-2.png)is obtained with parameters ![](images/pg46-in-3.png).

This matches the convergence rate of standard oﬄine gradient descent. However, observe that each iteration is significantly cheaper—only one example in the data set needs to be considered! That is the magic of SGD; we have matched the nearly optimal convergence rate of first-order methods using extremely cheap iterations. This makes it the method of choice in numerous applications.

## 3.5 Bibliographic Remarks

The OCO framework was introduced by Zinkevich (2003), where the OGD algorithm was also introduced and analyzed. Precursors to this algorithm, albeit for less general settings, were introduced and analyzed by Kivinen and Warmuth (1997). Logarithmic regret algorithms for OCO were introduced and analyzed by Hazan, Agarwal, and Kale (2007).

The SGD algorithm dates to Robbins and Monro (1951), where it was called “stochastic approximation.” The importance of SGD for machine learning was advocated for by Bottou (1998) and Bottou and Bousquet (2008). The body of literature on SGD is vast, and the reader is referred to Bubeck (2015) and Lan (2012).

Application of SGD to soft-margin SVM training was explored by Shalev-Shwartz et al. (2011). Tight convergence rates of SGD for strongly convex and nonsmooth functions were only recently obtained (Hazan and Kale 2011; Rakhlin, Shamir, and Sridharan 2012; Shamir and Zhang 2013).

## 3.6 Exercises

*   **1.**   Prove that for a strongly convex function, SGD can, with appropriate parameters *η*[*t*], converge as ![](images/pg46-in-4.png). Recall that the *Õ* notation hides logarithmic factors in the parameters, including *T*. You may assume that the gradient estimators have Euclidean norms bounded by constant *G*.
*   **2.**   ^(\*)Here, we show how to remove some a priori knowledge from the design of OCO algorithms.

**(a)** Design an OCO algorithm that attains the same asymptotic regret bound as OGD, up to logarithmic factors in *G* without knowing parameter *G* ahead of time.

**(b)** Do the same for the parameter *D*: Design an OCO algorithm that attains the same asymptotic regret bound as OGD, up to logarithmic factors in *D* without knowing parameter *D* ahead of time. This time, you may assume that *G* is known. You may assume that it is possible to compute projections onto 𝒦 without knowing its diameter.

*   **3.**   Here, we prove a tight lower bound on the regret of any algorithm for OCO.

**(a)** For any sequence of *T* fair coin tosses, let *N*[*h*] be the number of head outcomes and *N*[*t*] be the number of tails. Give an asymptotically tight upper and lower bound on **E**\[|*N*[*h*] −*N*[*t*]|\]. That is, give an order of growth of this random variable as a function of *T*, up to multiplicative and additive constants.

**(b)** Consider a two-expert problem, in which the losses are inversely correlated: either expert 1 incurs a loss of 1 and the second expert − 1, or vice versa. Use this fact to design a setting in which any experts algorithm incurs regret that asymptotically matches the upper bound.

**(c)** Consider the general OCO setting over a convex set 𝒦. Design a setting in which the cost functions have gradients whose norm is bounded by *G*, and obtain a lower bound on the regret as a function of *G*, the diameter 𝒦, and the number of game iterations.

**4.** Implement the SGD algorithm for SVM training. Apply it to the MNIST data set. Compare your results to the oﬄine GD algorithm from the previous chapter.

# 4 Second-Order Methods

The focus of this chapter is the application of universal portfolio selection, which was introduced in chapter 1. We begin with a detailed description of this application and then proceed to describe a new class of convex functions that model this problem. This new class of functions is more general than the class of strongly convex functions discussed in chapter 3. It allows for logarithmic regret algorithms, which are based on second-order methods from convex optimization. In contrast to first-order methods, which have been our focus thus far and relied on subgradients, second-order exploit information about the second derivative of the objective function.

## 4.1 Motivation: Universal Portfolio Selection

In this subsection, we give the formal definition of the universal portfolio selection problem that was informally described in section 1.2 of chapter 1.

### 4.1.1 Mainstream portfolio theory

Mainstream financial theory models stock prices via a stochastic process known as geometric Brownian motion (GBM). This model assumes that the fluctuations in the prices of stocks behave essentially as a random walk. It is perhaps easier to think about a price of an asset (stock) in terms of time segments, obtained via a discretization of time into equal segments. Thus, the logarithm of the price at segment *t* + 1, denoted as *l*[*t*+1], is given by the sum of the logarithm of the price at segment *t* and a Gaussian random variable with a particular mean and variance:

![](images/pg49-1.png)

This is only an informal way of thinking about GBM. The formal model is a continuous time process, similar to the discrete time stochastic process we have just described, obtained as the time intervals, means, and variances approach zero.

The GBM model gives rise to particular algorithms for portfolio selection (as well as more sophisticated applications, such as options pricing). Given the means and variances of stock prices over time of a set of assets, as well as their cross-correlations, a portfolio with a maximal expected gain (mean) for a specific risk (variance) threshold can be formulated.

The fundamental question is, of course, how one obtains the mean and variance parameters, not to mention the cross-correlations, of a given set of stocks. One accepted solution is to estimate these from historical data, such as by taking the recent history of stock prices.

### 4.1.2 Universal portfolio theory

The theory of universal portfolio selection is very different from the GBM model. The main difference is the lack of statistical assumptions about the stock market. The idea is to model investing as a repeated decision-making scenario, which fits nicely into our online convex optimization (OCO) framework, and to measure regret as a performance metric.

Consider the following scenario: at each iteration *t* ∈ \[*T*\], the decision maker chooses **x**[*t*], a distribution of her wealth over *n* assets, such that **x***t* ∈ Δ[*n*]. Here, ![](images/pg50-in-1.png)is the *n*\-dimensional simplex (i.e., the set of all distributions over *n* elements). An adversary independently chooses market returns for the assets (i.e., a vector **r**[*t*] ∈ ℝ[+]^(*n*) such that each coordinate **r**[*t*](*i*) is the price ratio for the *i*th asset between the iterations *t* and *t* + 1). For example, if the *i*th coordinate is the Google ticker symbol GOOG traded on the NASDAQ stock exchange, then

![](images/pg50-1.png)

How does the decision maker’s wealth change? Let *W*[*t*] be her total wealth at iteration *t*. Then, ignoring transaction costs, we have

![](images/pg50-2.png)

Over *T* iterations, the total wealth of the investor is given by

![](images/pg50-3.png)

The goal of the decision maker, to maximize the overall wealth gain *W*[*T*]/*W*[0], can be attained by maximizing the following more convenient logarithm of this quantity:

![](images/pg50-4.png)

This formulation is already very similar to our OCO setting, albeit phrased as a gain maximization rather than a loss minimization. Let

![](images/pg51-1.png)

The convex set is the *n*\-dimensional simplex 𝒦 = Δ[*n*], and the regret is defined as

![](images/pg51-2.png)

The functions *f*[*t*] are concave rather than convex, which is perfectly fine, as we are framing the problem as a maximization rather than a minimization. Note also that the regret is the negation of the usual regret notion (shown in equation 1.1 in chapter 1) that we have considered for minimization problems.

Since this is an OCO instance, we can use the online gradient descent (OGD) algorithm from the previous chapter to invest, which ensures ![](images/pg51-in-1.png)regret (see exercise 3). What guarantee do we attain in terms of investing? To answer this, in the next subsection, we reason about what **x**^(*⋆*) in the above expression may be.

### 4.1.3 Constant rebalancing portfolios

As **x**^(*⋆*) ∈𝒦 = Δ[*n*] is a point in the *n*\-dimensional simplex, consider the special case of **x**^(*⋆*) = **e**1; that is, the first standard basis vector (the vector that has zero in all coordinates except the first, which is set to 1). The term ![](images/pg51-in-2.png)becomes ![](images/pg51-in-3.png), or

![](images/pg51-3.png)

As *T* becomes large, any sublinear regret guarantee (e.g., the ![](images/pg51-in-4.png)regret guarantee achieved using OGD) achieves an average regret that approaches zero. In this context, this implies that the log-wealth gain achieved (in average over *T* rounds) is as good as that of the first stock. Since **x**^(*⋆*) can be taken to be any vector, sublinear regret guarantees average log-wealth growth that is as good as for any stock!

However, **x**^(*⋆*) can be significantly better, as shown in the following example. Consider a market of two stocks that fluctuate wildly. The first stock increases by 100 percent every even day and returns to its original price the following (odd) day. The second stock shows the opposite kind of behavior: it decreases by 50 percent on even days and goes back to its original price on odd days. Formally, we have

![](images/pg52-1.png)

Clearly, any investment in either of these stocks will not gain in the long run. However, the portfolio **x**^(*⋆*) = (0.5, 0.5) increases wealth by a factor of ![](images/pg52-in-1.png)daily! Such a mixed distribution is called a *fixed rebalanced portfolio*, as it needs to rebalance the proportion of total capital invested in each stock at each iteration in order to maintain this fixed distribution strategy.

Thus, vanishing average regret guarantees long-run growth as the best constant rebalanced portfolio in hindsight. Such a portfolio strategy is called *universal*. We have seen that the OGD algorithm gives essentially a universal algorithm with regret ![](images/pg52-in-2.png). Can we get better regret guarantees?

## 4.2 Exp-Concave Functions

For convenience, we return to considering losses of convex functions rather than gains of concave now functions, as in the application for portfolio selection. The two problems are equivalent: we simply replace the maximization of the concave ![](images/pg52-in-3.png)with the minimization of the convex ![](images/pg52-in-4.png).

In the previous chapter, we saw that the OGD algorithm with carefully chosen stepsizes can deliver logarithmic regret for strongly convex functions. However, the loss function for the OCO setting of portfolio selection, ![](images/pg52-in-5.png), is not strongly convex. Instead, the Hessian of this function is given by

![](images/pg52-2.png)

which is a rank one matrix. Recall that the Hessian of a twice-differentiable, strongly convex function is larger than a multiple of the identity matrix, is positive definite, and in particular has full rank. Thus, the loss function ![](images/pg52-in-6.png)is quite far from being strongly convex.

However, an important observation is that this Hessian is large in the direction of the gradient. This property is called *exp-concavity*. We proceed to define this property rigorously in definition 4.1 and show that it suffices to attain logarithmic regret.

**Definition 4.1** *A convex function f*: ℝ^(*n*) ↦ ℝ *is defined to be α\-exp-concave over* 𝒦⊆ ℝ^(*n*) *if the function g is concave, where g*: 𝒦 ↦ ℝ *is defined as*

![](images/pg52-3.png)

For the following discussion, recall the notation of section 2.1 in chapter 2, and in particular our convention over matrices that *A* ≽ *B* if and only if *A* − *B* is positive semidefinite (PSD). Exp-concavity implies strong convexity in the direction of the gradient. This reduces to the property expressed in lemma 4.1.

**Lemma 4.1** *A twice-differentiable function f*: ℝ^(*n*) ↦ ℝ *is α\-exp-concave at* **x** *if and only if*

![](images/pg53-1.png)

The proof of this lemma is given as a guided exercise at the end of this chapter. We prove a slightly stronger version of this in lemma 4.2.

**Lemma 4.2** *Let f*: 𝒦 *→* ℝ *be an α\-exp-concave function, and D, G denote the diameter of* 𝒦 *and a bound on the subgradients of f, respectively. The following holds for all ![](images/pg53-in-1.png)and all* **x**, **y** ∈𝒦*:*

![](images/pg53-2.png)

*Proof.* The composition of a concave and nondecreasing function with another concave function is concave (see the exercises at the end of this chapter). Therefore, since 2*γ* ≤ *α*, the composition of *g*(*x*) = *x*^(2*γ/α*) with *f*(**x**) = exp(−*αf*(**x**)) is concave. It follows that the function ![](images/pg53-in-2.png)is concave. Then, by the concavity of *h*(**x**),

![](images/pg53-3.png)

Simplifying gives

![](images/pg53-4.png)

Next, note that |2*γ*∇*f*(**y**)^⊤(**x** −**y**)| ≤ 2*γGD* ≤ 1, and that using the Taylor approximation, for *z* ≥−1, it holds that ![](images/pg53-in-3.png). Applying the inequality for *z* = 2*γ*∇*f*(**y**)^⊤(**x** −**y**) implies the lemma.

☐

## 4.3 Exponentially Weighted Online Convex Optimization

Before diving into efficient second-order methods, we will describe a simple algorithm based on the multiplicative updates method that gives logarithmic regret for exp-concave losses. [Algorithm (4.1)](#chapter_4.xhtml#algo4-1), called exponentially weighted online optimizer (EWOO), is a close relative to the Hedge algorithm (given in [algorithm 1.1](#chapter_1.xhtml#algo1-1)). Its regret guarantee is robust: it does not include a Lipschitz constant or a diameter bound. In addition, it is particularly simple to describe and analyze.

The downside of EWOO is its running time. A naive implementation would run in exponential time of the dimension. It is possible to given a randomized polynomial time implementation based on random sampling techniques, where the polynomial depends both on the dimension and the number of iterations (see section 4.5 for more details).

![](images/Algorithm4-1.png)

In the analysis that follows, it can be observed that choosing **x**[*t*] at random with density proportional to *w*[*t*](**x**), instead of just computing the entire integral, also guarantees our regret bounds on the expectation. This is the basis for the polynomial time implementation. We proceed to give the logarithmic regret bounds next.

**Theorem 4.1**

![](images/pg54-1.png)

*Proof.* Let *h*[*t*](**x**) = *e*^(−*αf*[*t*](**x**)). Since *f*[*t*] is *α*\-exp-concave, we have that *h*[*t*] is concave, and thus

![](images/pg54-2.png)

Hence, we have by telescoping product,

![](images/eq4-1.png)

By this definition of **x**^(*⋆*), we have **x**^(*⋆*) ∈ arg ![](images/pg54-in-1.png). Denote as *S*[*δ*] ⊂𝒦 the translated Minkowski set given by

![](images/pg54-3.png)

By concavity of *h*[*t*] and the fact that *h*[*t*] is nonnegative, we have that

![](images/pg55-1.png)

Hence,

![](images/pg55-2.png)

Finally, since *S*[*δ*] = (1 − *δ*)**x**^(*⋆*) + *δ*𝒦 is simply a rescaling of 𝒦 followed by a translation, and we are in *d* dimensions, vol(*S*[*δ*]) = vol(𝒦) ×*δ*^(*d*). Putting this together with equation ([4.1](#chapter_4.xhtml#eq4-1)), we have

![](images/pg55-3.png)

We can now simplify this expression by taking logarithms and changing sides:

![](images/pg55-4.png)

where the last step is choosing ![](images/pg55-in-1.png).

☐

## 4.4 The Online Newton Step Algorithm

Thus far, we have only considered first-order methods for regret minimization. In this section, we consider a quasi-Newton approach (i.e., an OCO algorithm that approximates the second derivative, or Hessian in more than one dimension). However, strictly speaking, the algorithm we analyze is also first order, in the sense that it only uses gradient information.

The algorithm we introduce and analyze, called the *online Newton step*, is detailed in [algorithm 4.2](#chapter_4.xhtml#algo4-2). At each iteration, this algorithm chooses a vector that is the projection of the sum of the vector chosen at the previous iteration and an additional vector. Whereas for the OGD algorithm this added vector was the gradient of the previous cost function, for the online Newton step this vector is different: it is reminiscent of the direction in which the Newton-Raphson method would proceed if it were an oﬄine optimization problem for the previous cost function. The Newton-Raphson algorithm would move in the direction of the vector that is the inverse Hessian times the gradient. In the online Newton step, this direction is ![](images/pg56-in-1.png), where the matrix *A*[*t*] is related to the Hessian, as will be shown in the following analysis.

Since adding a multiple of the Newton vector ![](images/pg56-in-2.png)to the current vector may result in a point outside the convex set, an additional projection step is required to obtain **x**[*t*], the decision at time *t*. This projection is different than the standard Euclidean projection used by OGD in section 3.1 of chapter 3. It is the projection according to the norm defined by the matrix *A*[*t*] rather than the Euclidean norm.

![](images/Algorithm4-2.png)

The advantage of the online Newton step algorithm is its logarithmic regret guarantee for exp-concave functions, as defined in section 4.3. Theorem 4.2 bounds the regret of the online Newton step.

**Theorem 4.2** *[Algorithm 4.2](#chapter_4.xhtml#algo4-2) with parameters ![](images/pg56-in-3.png)and T* ≥ 4 *guarantees*

![](images/pg56-1.png)

As a first step, we prove lemma 4.3.

**Lemma 4.3** *The regret of the online Newton step is bounded by*

![](images/pg56-2.png)

*Proof.* Let ![](images/pg56-in-4.png)be the best decision in hindsight. By lemma 4.2, we have for ![](images/pg56-in-5.png),

![](images/pg56-3.png)

where we define

![](images/pg57-1.png)

According to the update rule of the algorithm ![](images/pg57-in-1.png). Now, by the definition of **y**[*t*+1],

![](images/eq4-2.png)![](images/eq4-3.png)

Multiplying the transpose of equation ([4.2](#chapter_4.xhtml#eq4-2)) by equation ([4.3](#chapter_4.xhtml#eq4-3)), we get

![](images/eq4-4.png)

Since **x**[*t*+1] is the projection of **y**[*t*+1] in the norm induced by *A*[*t*], we have by the Pythagorean theorem (see section 2.1.1 in chapter 2)

![](images/pg57-2.png)

This inequality is the reason for using generalized projections as opposed to standard projections, which were used in the analysis of OGD (see equation ([3.2](#chapter_3.xhtml#eq3-2)) in chapter 3). This fact, together with equation ([4.4](#chapter_4.xhtml#eq4-4)), gives

![](images/pg57-3.png)

Now, summing up over *t* = 1 to *T*, we get

 

![](images/pg57-4.png)

![](images/pg58-1.png)

In the last inequality, we use the fact that ![](images/pg58-in-1.png), as well as the fact that matrix *A*[*T*] is PSD, and hence the last term before the inequality is negative. Thus,

![](images/pg58-2.png)

Using the algorithm parameters ![](images/pg58-in-2.png)and our notation for the diameter ∥**x**[1] −**x**^(*⋆*)∥² ≤ *D*², we have

![](images/pg58-3.png)

Since ![](images/pg58-in-3.png), we have ![](images/pg58-in-4.png). This concludes the proof.

☐

We can now prove theorem 4.2.

*Proof.* First, we show that the term ![](images/pg58-in-5.png)is upper-bounded by a telescoping sum. Notice that

![](images/pg58-4.png)

where for matrices *A, B* ∈ ℝ^(*n*×*n*) we denote by ![](images/pg58-in-6.png), which is equivalent to the inner product of these matrices as vectors in ℝ^(*n*²) .

For the real numbers *a, b* ∈ ℝ[+], the first-order Taylor expansion of the logarithm of *b* at *a* implies ![](images/pg58-in-7.png). An analogous fact holds for positive semidefinite matrices; that is, ![](images/pg58-in-8.png), where |*A*| denotes the determinant of matrix *A* (this is proved in lemma 4.4 later in this chapter). Using this fact, we have

![](images/pg58-5.png)

 

![](images/pg59-1.png)

Since ![](images/pg59-in-1.png)and ∥∇[*t*]∥≤ *G*, the largest eigenvalue of *A*[*T*] is at most *TG*² + *ε*. Hence, the determinant of *A*[*T*] can be bounded by |*A*[*T*]|≤ (*TG*² + *ε*)^(*n*); recalling that ![](images/pg59-in-2.png)and ![](images/pg59-in-3.png), for *T >* 4,

![](images/pg59-2.png)

Plugging into lemma 4.3, we obtain

![](images/pg59-3a.png)

which implies theorem 4.2 for *n >* 1*, T* ≥ 4.

☐

We still must prove the technical lemma for PSD matrices used here, which is lemma 4.4.

**Lemma 4.4** *Let A* ≽ *B* ≻ 0 *be positive definite matrices. Then*

![](images/pg59-3.png)

*Proof.* For any positive definite matrix *C*, denote by *λ*[1](*C*)*, …, λ*[*n*](*C*) its eigenvalues (which are positive):

![](images/pg59-4.png)

![](images/pg60-1.png)

 

In the last equality, we use the facts |*AB*| = |*A*||*B*| and ![](images/pg60-in-1.png)for positive definite matrices (see the exercises at the end of this chapter).

☐

Implementation and running time. The online Newton step algorithm requires *O*(*n*²) space to store matrix *A*[*t*]. Every iteration requires the computation of matrix ![](images/pg60-in-2.png), the current gradient, a matrix-vector product, and possibly a projection onto the underlying convex set 𝒦.

A naive implementation would require computing the inverse of the matrix *A*[*t*] on every iteration. However, if *A*[*t*] is invertible, the matrix inversion lemma (see bibliography) states that for invertible matrix *A* and vector **x**,

![](images/pg60-2.png)

Thus, given ![](images/pg60-in-3.png)and ∇[*t*] one can compute ![](images/pg60-in-4.png)in time *O*(*n*²) using only matrix-vector and vector-vector products.

The online Newton step algorithm also needs to make projections onto 𝒦, but of a slightly different nature than OGD and other OCO algorithms. The required projection, denoted as ![](images/pg60-in-5.png), is in the vector norm induced by matrix *A*[*t*] (namely, ![](images/pg60-in-6.png)). It is equivalent to finding the point **x** ∈𝒦 which minimizes (**x** −**y**)^⊤*A*[*t*](**x** −**y**), where **y** is the point being projected. This is a convex program that can be solved to any degree of accuracy in polynomial time.

Modulo the computation of generalized projections, the online Newton step algorithm can be implemented in time and space *O*(*n*²). In addition, the only information required is the gradient at each step (and the exp-concavity constant *α* of the loss functions).

## 4.5 Bibliographic Remarks

The GBM model for stock prices was suggested and studied as early as 1900 in the PhD thesis of Louis Bachelier (Bachelier 1900); see also Osborne (1959). It also was used in the Nobel Prize–winning work of Black and Scholes (1973) on options pricing. In a strong deviation from standard financial theory, Thomas Cover (1991) put forth the universal portfolio model, whose algorithmic theory was historically sketched in chapter 1. The EWOO algorithm was essentially given in Cover’s paper in the application of portfolio selection and logarithmic loss functions, and extended to exp-concave loss functions in Hazan et al. (2006). The randomized extension of Cover’s algorithm that runs in polynomial running time was explored by Kalai and Vempala (2003), and it naturally extends to EWOO.

Some bridges between classical portfolio theory and the universal model appear in Abernethy, Frongillo, and Wibisono (2012). Options pricing and its relation to regret minimization were recently also explored by DeMarzo, Kremer, and Mansour (2006).

Exp-concave functions have been considered in the context of prediction by Kivinen and Warmuth (1999); see also Cesa-Bianchi and Lugosi (2006). A more general condition than exp-concavity called *mixability* was used by Vovk (1990) to give a general multiplicative update algorithm (see also Foster et al. 2018). For a thorough discussion of various conditions that allow logarithmic regret in online learning, see van Erven et al. (2015).

For the square-loss, Azoury and Warmuth (2001) gave a specially tailored and near-optimal prediction algorithm. Logarithmic regret algorithms for OCO and the online Newton step algorithm were presented by Hazan, Agarwal, and Kale (2007).

Logarithmic regret algorithms were used to derive ![](images/pg61-in-1.png)\-convergent algorithms for nonsmooth convex optimization in the context of training support vector machines (SVMs) (Shalev-Shwartz et al. 2011). Building upon these results, tight convergence rates of SGD for strongly convex and nonsmooth functions were obtained (Hazan and Kale 2011).

The Sherman-Morrison formula, aka the matrix inversion lemma, takes the form of the inverse of a matrix after a rank-1 update (Riedel 1991).

## 4.6 Exercises

*   **1.**   For this question, assume that all functions are twice differentiable. Prove that exp-concave functions are a larger class than strongly convex and Lipschitz functions. That is, prove that a strongly convex function over a bounded domain that is also *G*\-Lipschitz is also exp-concave. Show that the converse is not necessarily true.
*   **2.**   Prove that a twice-differentiable function *f* is *α*\-exp-concave over 𝒦 if and only if for all **x** ∈𝒦,

![](images/pg61-1.png)

Hint: consider the Hessian of the function *e*^(−*αf*(**x**)), and use the fact that the Hessian of a convex function is always PSD.

*   **3.**   Write pseudocode for a portfolio selection algorithm based on OGD. That is, given a set of return vectors, spell out the exact constants and updates based upon the gradients of the reward functions. Derive the regret bound based on theorem 3.1. You may assume that the multiplicative change in price for any single asset is bounded, and use this quantity in your regret bound.  
    Do the same (pseudocode and regret bound) for the online Newton step algorithm applied to portfolio selection.
    
    Note: You are not required to give pseudocode for projections onto the simplex.
    
*   **4.**   Download stock prices from your favorite online finance website over a period of at least three years. Create a data set for testing portfolio selection algorithms by creating price-return vectors. Implement the OGD and online Newton step algorithms and benchmark them on your data.
*   **5.**   Prove that for positive definite matrices *A, B* ≻ 0, the following statement holds: |*AB*| = |*A*||*B*| and ![](images/pg62-in-1.png), where |*A*| denotes the determinant of *A*.
*   **6.**   Let *h*(*x*): ℝ ↦ ℝ be concave and nondecreasing, and let *g*(**x**): 𝒦 ↦ ℝ be concave. Prove that the function *f*(**x**) = *h*(*g*(**x**)) is concave.

# 5 Regularization

In the previous chapters, we have explored algorithms for online convex optimization (OCO) that are motivated by convex optimization. However, unlike convex optimization, the OCO framework optimizes the Regret performance metric. This distinction motivates a family of algorithms, called *Regularized Follow The Leader* (RFTL), which we introduce in this chapter.

In an OCO setting of regret minimization, the most straightforward approach for the online player is to use at any time the optimal decision (i.e., point in the convex set) in hindsight. Formally, let

![](images/pg63-1.png)

This flavor of strategy is known as *fictitious play* in economics, and has been named *Follow The Leader* (FTL) in machine learning. It is not hard to see that this simple strategy fails miserably in a worst-case scenario. That is, this strategy’s regret can be linear in the number of iterations, as the following example shows: Consider 𝒦 = \[−1, 1\], let ![](images/pg63-in-1.png), and let *f*[*τ*] for *τ* = 2*, …, T* alternate between − *x* or *x*. Thus,

![](images/pg63-2.png)

The FTL strategy will keep shifting between *x*[*t*] = −1 and *x*[*t*] = 1, always making the wrong choice.

The intuitive FTL strategy fails in this example because it is unstable. Can we modify the FTL strategy such that it won’t change decisions often, thereby causing it to attain low regret?

This question motivates the need for a general means of stabilizing the FTL method. Such a means is referred to as *regularization*.

## 5.1 Regularization Functions

In this chapter, we consider regularization functions, denoted as *R*: 𝒦 ↦ ℝ, which are strongly convex and smooth (recall the definitions given in section 2.1 in chapter 2).

Although it is not strictly necessary, we assume that the regularization functions in this chapter are twice differentiable over 𝒦 and, for all points **x** ∈ int(𝒦) in the interior of the decision set, have a Hessian ∇²*R*(**x**) that is, by the strong convexity of *R*, positive definite.

We denote the diameter of set 𝒦 relative to function *R* as

![](images/pg64-1.png)

Henceforth we use general norms and their dual. The dual norm to a norm ∥·∥ is given by the following definition:

![](images/pg64-2.png)

A positive definite matrix *A* gives rise to the matrix norm ![](images/pg64-in-1.png). The dual norm of a matrix norm is ![](images/pg64-in-2.png).

The generalized Cauchy-Schwarz theorem asserts **x**^⊤**y** ≤∥**x**∥∥**y**∥^(\*) and in particular for matrix norms, ![](images/pg64-in-3.png)(see the exercises at the end of this chapter).

In our derivations, we usually consider matrix norms with respect to ∇²*R*(**x**), the Hessian of the regularization function *R*(**x**), as well as the inverse Hessian, denoted as ∇^(−2)*R*(**x**). In such cases, we use the notation

![](images/pg64-3.png)

and, similarly,

![](images/pg64-4.png)

A crucial quantity in the analysis of OCO algorithms that use regularization is the remainder term of the Taylor approximation of the regularization function, and especially the remainder term of the first-order Taylor approximation. The difference between the value of the regularization function at **x** and the value of the first-order Taylor approximation is known as the *Bregman divergence*, given by definition 5.1.

**Definition 5.1** *Denote by B*[*R*](**x**||**y**) *the Bregman divergence with respect to the function R, defined as*

![](images/pg64-5.png)

For twice-differentiable functions, Taylor expansion and the mean-value theorem assert that the Bregman divergence is equal to the second derivative at an intermediate point (see the exercises). That is,

![](images/pg65-1.png)

for some point **z** ∈ \[**x**, **y**\], meaning that there exists some *α* ∈ \[0, 1\] such that **z** = *α***x** + (1 − *α*)**y**. Therefore, the Bregman divergence defines a local norm, which has a dual norm. We shall denote this norm by

![](images/pg65-2.png)

With this notation, we have

![](images/pg65-3.png)

In OCO, we commonly refer to the *Bregman divergence* between two consecutive decision points **x**[*t*] and **x**[*t*+1]. In such cases, the shorthand notation for the norm defined by the Bregman divergence with respect to *R* on the intermediate point in ![](images/pg65-in-1.png). The latter norm is called the *local norm* at iteration *t*. With this notation, we have ![](images/pg65-in-2.png).

Finally, we consider next the generalized projections that use the Bregman divergence as a distance instead of as a norm. Formally, the projection of a point **y** according to the Bregman divergence with respect to function *R* is given by

![](images/pg65-4.png)

## 5.2 The RFTL Algorithm and Its Analysis

Recall the caveat with straightforward use of FTL: as in the bad example, we have considered—namely that the predictions of FTL may vary wildly from one iteration to the next. This motivates the modification of the basic FTL strategy in order to stabilize the prediction. By adding a regularization term, we obtain the RFTL algorithm.

We proceed to formally describe the RFTL algorithmic template and analyze it here. The analysis gives asymptotically optimal regret bounds. However, we do not optimize the constants in the regret bounds to improve clarity of presentation.

Throughout this chapter, recall the notation of ∇[*t*] to denote the gradient of the current cost function at the current point:

![](images/pg65-5.png)

In the OCO setting, the regret of convex cost functions can be bounded by a linear function via the inequality ![](images/pg66-in-1.png). Thus, the overall regret (recall definition ([1.1](#chapter_1.xhtml#eq1-1)) in chapter 1) of an OCO algorithm can be bounded by

![](images/eq5-1.png)

### 5.2.1 Meta-algorithm definition

The generic RFTL meta-algorithm is defined in [algorithm 5.1](#chapter_5.xhtml#algo5-1). The regularization function *R* is assumed to be strongly convex, smooth, and twice differentiable.

![](images/Algorithm5-1.png)

### 5.2.2 The regret bound

**Theorem 5.1** *[Algorithm 5.1](#chapter_5.xhtml#algo5-1) attains for every* **u** ∈𝒦 *the following bound on the regret:*

![](images/pg66-1.png)

If an upper bound on the local norms is known (i.e., ![](images/pg66-in-2.png)for all times *t*), then we can further optimize over the choice of *η* to obtain

![](images/pg66-2.png)

To prove theorem 5.1, we first relate the regret to the “stability” in prediction. This is formally captured by lemma 5.1.^([1](#chapter_5.xhtml#chapter5-1))

**Lemma 5.1** *[Algorithm 5.1](#chapter_5.xhtml#algo5-1) guarantees the following regret bound:*

![](images/pg66-3.png)

*Proof.* For convenience of the derivations, define the functions

![](images/pg67-1.png)

By equation ([5.1](#chapter_5.xhtml#eq5-1)), it suffices to bound ![](images/pg67-in-1.png). As a first step, we prove the inequality expressed in lemma 5.2.

**Lemma 5.2** *For every* **u** ∈𝒦,

![](images/pg67-2.png)

*Proof.* By induction on *T*:

**Induction base:**  
By definition, we have that **x**1 = arg min[**x**∈𝒦]{*R*(**x**)}, and thus *g*[0](**u**) ≥ *g*[0](**x**1) for all **u**.

**Induction step:**  
Assume that for *T*, we have

![](images/pg67-3.png)

and let us prove the statement for *T* + 1. Since ![](images/pg67-in-2.png), we have

![](images/pg67-4.png)

where in the third line, we used the induction hypothesis for **u** = **x**[*T*]+2.

☐

We conclude that

![](images/pg67-5.png)

![](images/pg68-1.png)

*Proof of theorem 5.1*. Recall that *R*(**x**) is a convex function and 𝒦 is a convex set. Denote:

![](images/pg68-2.png)

By the Taylor expansion (with its explicit remainder term via the mean-value theorem) at **x**[*t*+1], and by the definition of the Bregman divergence,

![](images/pg68-3.png)

The inequality holds since **x**[*t*+1] is a minimum of Φ[*t*] over 𝒦, as in theorem 2.2. The last equality holds since the component ![](images/pg68-in-1.png)is linear and thus does not affect the Bregman divergence. Thus,

![](images/eq5-2.png)

To proceed, recall that the shorthand for the norm induced by the Bregman divergence with respect to *R* on point **x**[*t*], **x**[*t*+1] is ∥·∥[*t*] = ∥·∥[**x**[*t*], **x**[*t*+1]]. This is similarly true for the dual local norm, ![](images/pg68-in-2.png). With this notation, we have ![](images/pg68-in-3.png). By the generalized Cauchy-Schwarz inequality,

![](images/pg68-4.png)

After rearranging, we get

![](images/pg68-5.png)

Combining this inequality with lemma 5.1, we obtain the theorem statement.

☐

## 5.3 Online Mirror Descent

In the convex optimization literature, the term *mirror descent* refers to a general class of first-order methods generalizing gradient descent. Online mirror descent (OMD) is the online counterpart of this class of methods. This relationship is analogous to the relationship of online gradient descent (OGD) to traditional (oﬄine) gradient descent.

OMD is an iterative algorithm that computes the current decision using a simple gradient update rule and the previous decision, much as OGD does. The generality of the method stems from the update being carried out in a “dual” space, where the duality notion is defined by the choice of regularization: the gradient of the regularization function defines a mapping from ℝ^(*n*) onto itself, which is a vector field. The gradient updates are then carried out in this vector field.

For the RFTL algorithm, the intuition was straightforward—regularization was used to ensure stability of the decision. For OMD, regularization has an additional purpose: it transforms the space in which gradient updates are performed, which enables better bounds in terms of the geometry of the space.

The OMD algorithm comes in two flavors: an agile and a lazy version. The lazy version keeps track of a point in Euclidean space and projects onto the convex decision set 𝒦 only at decision time. In contrast, the agile version maintains a feasible point at all times, much as OGD does.

![](images/Algorithm5-2.png)

Both versions can be analyzed to give roughly the same regret bounds as the RFTL algorithm. In light of what we will see next, this is not surprising: for linear cost functions, the RFTL and lazy OMD algorithms are equivalent!

Thus, we get regret bounds for free in the lazy version. The agile version can be shown to attain similar regret bounds, and it is in fact superior in certain settings that require adaptivity. This issue is further explored in chapter 10. The analysis of the agile version is of independent interest, and we give it later in this chapter.

### 5.3.1 Equivalence of lazy OMD and RFTL

The lazy version of OMD and RFTL are identical for linear cost functions, as we show in lemma 5.3.

**Lemma 5.3** *Let f*[1]*, …, f*[*T*] *be linear cost functions. The lazy OMD and RFTL algorithms produce identical predictions:*

![](images/pg70-1.png)

*Proof.* First, observe that the unconstrained minimum

![](images/pg70-2.png)

satisfies 

![](images/pg70-3.png)

By definition, **y***t* also satisfies the previous equation, but since *R*(**x**) is strictly convex, there is only one solution for this equation, and thus ![](images/pg70-in-1.png). Hence,

![](images/pg70-4.png)

Since *R*(**y***t*) and ![](images/pg70-in-2.png)are independent of **x**, it follows that *B*[*R*](**x**||**y***t*) is minimized at the point **x** that minimizes ![](images/pg70-in-3.png)over 𝒦 which, in turn, implies that

![](images/pg70-5.png)

### 5.3.2 Regret bounds for mirror descent

In this subsection, we prove regret bounds for the agile version of the RFTL algorithm. The analysis is quite different than the one for the lazy version, and it is of independent interest.

**Theorem 5.2** *[Algorithm 5.2](#chapter_5.xhtml#algo5-2) attains, for every* **u** ∈𝒦*, the following bound on the regret:*

![](images/pg71-1.png)

If an upper bound on the local norms is known (i.e., ![](images/pg71-in-1.png)for all times *t*), then we can further optimize over the choice of *η* to obtain

![](images/pg71-2.png)

*Proof.* Since the functions **f**[*t*] are convex, for any **x**^(\*)∈ *K*,

![](images/pg71-3.png)

This property of Bregman divergences follows from the definition: for any vectors **x**, **y**, **z**,

![](images/pg71-4.png)

Combining both observations,

![](images/pg71-5.png)

where the last inequality follows from the generalized Pythagorean theorem, as **x**[*t*+1] is the projection with regard to the Bregman divergence of **y**[*t*+1] and **x**^(\*)∈ *K* is in the convex set. Summing over all iterations,

![](images/eq5-3.png)

We proceed to bound *B*[ℛ](**x**[*t*], **y**[*t*+1]). By the definition of Bregman divergence and the generalized Cauchy-Schwartz inequality,

![](images/pg72-1.png)

where the last inequality follows from (*a* − *b*)² ≥ 0. Thus, we have

![](images/pg72-2.png)

Using this inequality together with equation ([5.3](#chapter_5.xhtml#eq5-3)), and by nonnegativity of the Bregman divergence, we get

![](images/pg72-3.png)

by taking ![](images/pg72-in-1.png).

☐

## 5.4 Application and Special Cases

In this section, we illustrate the generality of the regularization technique: we show how to derive the two most important and famous online algorithms—the OGD algorithm and the exponentiated gradient (based on the multiplicative update method)—from the RFTL meta-algorithm.

Other important special cases of the RFTL meta-algorithm are derived with matrix-norm regularization—namely, the von Neumann entropy function, and the log-determinant function, as well as self-concordant barrier regularization—and we shall explore both in detail in chapter 6.

### 5.4.1 Deriving online gradient descent

To derive the OGD algorithm, we take ![](images/pg72-in-2.png)for an arbitrary **x**[0] ∈𝒦. Projection with respect to this divergence is the standard Euclidean projection (see the exercises at the end of this chapter), and in addition, ∇*R*(**x**) = **x** −**x**[0]. Hence, the update rules for [algorithm 5.2](#chapter_5.xhtml#algo5-2) become

![](images/pg72-4.png)

The latter algorithm is exactly OGD, as described in [algorithm 3.1](#chapter_3.xhtml#algo3-1) in chapter 3. However, both variants behave very differently, as explored in chapter 10 (see the exercises).

Theorem 5.1 gives us the following bound on the regret (where *D*[*R*], ∥·∥[*t*] are the diameter and local norm defined with respect to the regularizer *R*, as defined in the beginning of this chapter, and *D* is the Euclidean diameter, as defined in chapter 2):

![](images/pg73-1.png)

where the second inequality follows since for ![](images/pg73-in-1.png), the local norm ∥·∥[*t*] reduces to the Euclidean norm.

### 5.4.2 Deriving multiplicative updates

Let ![](images/pg73-in-2.png)be the negative entropy function, where log **x** is to be interpreted element-wise. Then ∇*R*(**x**) = **1** + log **x**, and hence the update rules for [algorithm 5.2](#chapter_5.xhtml#algo5-2) become

![](images/pg73-2.png)

With this choice of regularizer, a notable special case is the experts problem that we encountered in section 1.3 of chapter 1, for which the decision set 𝒦 is the *n*\-dimensional simplex ![](images/pg73-in-3.png). In this special case, the projection according to the negative entropy becomes scaling by the *ℓ*[1] norm (see the exercises), which implies that both update rules amount to the same algorithm:

![](images/pg73-3.png)

which is exactly the Hedge algorithm from chapter 1!

Theorem 5.2 gives us the following bound on the regret:

![](images/pg73-4.png)

If the costs per individual expert are in the range \[0, 1\], it can be shown that

![](images/pg73-5.png)

In addition, when *R* is the negative entropy function, the diameter over the simplex can be shown to be bounded by *D*²[*R*] ≤ log *n* (see the exercises), giving rise to the bound

![](images/pg73-6.png)

For an arbitrary range of costs, we obtain the exponentiated gradient algorithm described in [algorithm 5.3](#chapter_5.xhtml#algo5-3).

![](images/Algorithm5-3.png)

The regret achieved by the exponentiated gradient algorithm can be bounded using corollary 5.1 of theorem 5.1.

**Corollary 5.1** *The exponentiated gradient algorithm with gradients bounded by* ∥∇[*t*]∥[∞]≤ *G*[∞] *and parameter ![](images/pg74-in-1.png)has regret bounded by*

![](images/pg74-1.png)

## 5.5 Randomized Regularization

The connection between stability in decision making and low regret has motivated this discussion of regularization thus far. However, this stability need not be achieved only using strongly convex regularization functions. An alternative method to achieve stability in decisions is by introducing randomization into the algorithm. In fact, historically, this method preceded methods based on strongly convex regularization (see bibliography).

In this section, we first describe a deterministic algorithm for OCO that is easily amenable to speedup via randomization. We then give an efficient randomized algorithm for the special case of OCO with linear losses.

Oblivious versus adaptive adversaries. For simplicity, we consider a slightly restricted version of OCO. So far, we have not restricted the cost functions in any way, and they could depend on the choice of decision by the online learner. However, when dealing with randomized algorithms, this issue becomes a bit more subtle: can the cost functions depend on the randomness of the decision-making algorithm itself? Furthermore, when analyzing the regret, which is now a random variable, dependencies across different iterations require probabilistic machinery, which adds little to the fundamental understanding of randomized OCO algorithms. To avoid these complications, we make the following assumption throughout this section: the cost functions {**f**[*t*]} are adversarially chosen ahead of time and do not depend on the actual decisions of the online learner. This version of OCO is called the *oblivious* setting, to distinguish it from the *adaptive* setting.

### 5.5.1 Perturbation for convex losses

The prediction given in [algorithm 5.4](#chapter_5.xhtml#algo5-4), the Follow the Perturbed Leader (FPL) algorithm, is according to a version of the FTL algorithm, augmented with an additional component of randomization. It is a deterministic algorithm that computes the expected decision according to a random variable—namely, the minimizer over the decision set according to the sum of gradients of the cost functions and an additional random vector.

In practice, the expectation need not be computed exactly. Estimation (via random sampling) up to a precision that depends linearly on the number of iterations would suffice.

The algorithm accepts as input a distribution, with the probability density function (PDF) denoted as 𝒟, over vectors in *n*\-dimensional Euclidean space **n** ∈ ℝ^(*n*). For *σ, L* ∈ ℝ, we say that a distribution 𝒟 is (*σ, L*) = (*σ*[*a*]*, L*[*a*]) stable with respect to the norm ∥·∥[*a*] if

![](images/pg75-1.png)

and

![](images/pg75-2.png)

Here, **n** *∼* 𝒟 denotes a vector **n** ∈ ℝ^(*n*) sampled according to distribution 𝒟, and 𝒟(**n**) is the value of the PDF 𝒟 over **n**. The subscript *a* is omitted if it is clear from the context.

The first parameter, *σ*, is related to the variance of 𝒟, while the second, *L*, is a measure of the sensitivity of the distribution.^([2](#chapter_5.xhtml#chapter5-2)) For example, if 𝒟 is the uniform distribution over the hypercube \[0, 1\]^(*n*), then it holds that for the Euclidean norm

![](images/pg75-3a.png)

Reusing notation from previous chapters, denote by *D* = *D*[*a*] the diameter of the set 𝒦 according to the norm ∥·∥[*a*], and by ![](images/pg75-in-1.png)the diameter according to its dual norm. Similarly, denote by *G* = *G*[*a*] and ![](images/pg75-in-2.png)an upper bound on the norm (and dual norm) of the gradients.

**Theorem 5.3** *Let the distribution* 𝒟 *be* (*σ, L*)*\-stable with respect to norm* ∥·∥[*a*]*. The FPL algorithm attains the following bound on the regret:*

![](images/pg75-3.png)

![](images/Algorithm5-4.png)

We can further optimize over the choice of *η* to obtain

![](images/pg76-1.png)

*Proof.* Define the random function *g*[0] as

![](images/pg76-2.png)

It follows from lemma 5.2 applied to the functions ![](images/pg76-in-1.png)that

![](images/pg76-3.png)

and thus,

![](images/pg76-4.png)

Hence,

![](images/eq5-5.png)

We now argue that ∥**x***t* −**x***t*+1∥ = *O*(*η*). Let

![](images/pg77-1.png)

and hence **x**[*t*] = **E**[**n** *∼* 𝒟]\[*h*[*t*](**n**)\]. Recalling that 𝒟(**n**) denotes the value of the PDF 𝒟 over **n** ∈ ℝ^(*n*), we can write

![](images/pg77-2.png)

and

![](images/pg77-3.png)

Notice that **x**[*t*], **x**[*t*+1] may depend on each other. However, by linearity of expectation, we have that

![](images/pg77-4.png)

![](images/pg78-1.png)

Substituting this bound back into equation ([5.5](#chapter_5.xhtml#eq5-5)) we have

![](images/pg78-2.png)

For the choice of 𝒟 as the uniform distribution over the unit hypercube \[0, 1\]^(*n*), which has parameters ![](images/pg78-in-1.png)and *L*[2] ≤ 1 for the Euclidean norm, the optimal choice of *η* gives a regret bound of ![](images/pg78-in-2.png). This is a factor *n*^(1/4) worse than the OGD regret bound of theorem 3.1. For certain decision sets 𝒦, a better choice of distribution 𝒟 results in near-optimal regret bounds.

### 5.5.2 Perturbation for linear cost functions

The case of linear cost functions *f*[*t*](**x**) = **g**[*t*]^⊤**x** is of particular interest in the context of randomized regularization. Denote

![](images/pg78-3.png)

By linearity of expectation, we have that

![](images/pg78-4.png)

Thus, instead of computing **x**[*t*] precisely, we can sample a single vector **n**[0] *∼* 𝒟, and use it to compute ![](images/pg78-in-3.png), as illustrated in [algorithm 5.5](#chapter_5.xhtml#algo5-5).

![](images/Algorithm5-5.png)

By these arguments, we have that the expected regret for the random variables ![](images/x-cap.png)[*t*] is the same as that for **x**[*t*]. We obtain corollary 5.2.

**Corollary 5.2**

![](images/pg79-1.png)

The main advantage of this algorithm is computational: with a single linear optimization step over the decision set 𝒦 (which does not even have to be convex!), we attain near optimal expected regret bounds.

### 5.5.3 Follow-the-perturbed-leader for expert advice

An interesting special case (and in fact the first use of perturbation in decision making) is that of nonnegative linear cost functions over the unit *n*\-dimensional simplex with costs bounded by 1, or the problem of prediction of expert advice considered in chapter 1.

[Algorithm 5.5](#chapter_5.xhtml#algo5-5) applied to the probability simplex and, with exponentially distributed noise, is known as the “FPL for prediction from expert advice” method. We spell it out in [algorithm 5.6](#chapter_5.xhtml#algo5-6).

![](images/Algorithm5-6.png)

Notice that we take the perturbation to be distributed according to the one-sided negative exponential distribution (i.e., **n**(*i*) *∼ e*^(−*ηx*)), or more precisely,

![](images/pg79-2.png)

Corollary 5.2 gives regret bounds that are suboptimal for this special case; thus we give here an alternative analysis that gives tight bounds up to constants amounting to theorem 5.4.

**Theorem 5.4** *[Algorithm 5.6](#chapter_5.xhtml#algo5-6) outputs a sequence of predictions* ![](images/pg80-in-1.png)*such that*

![](images/pg80-1.png)

Notice that as a special case of theorem 5.4, choosing ![](images/pg80-in-2.png)yields a regret bound of

![](images/pg80-2.png)

which is equivalent, up to constant factors, to the guarantee given for the Hedge algorithm in theorem 1.3.

*Proof.* We start with the same analysis technique throughout this chapter: let **g**[0] = −**n**. It follows from lemma 5.2 applied to the functions ![](images/pg80-in-3.png)that

![](images/pg80-3.png)

and thus,

![](images/eq5-6.png)

where the second inequality follows by the generalized Cauchy-Schwarz inequality, and the last inequality follows since

![](images/pg80-4.png)

We proceed to bound ![](images/pg80-in-4.png), which is naturally bounded by the probability that ![](images/pg80-in-5.png)is not equal to ![](images/pg80-in-6.png)multiplied by the maximum value that **g**[*t*] can attain (i.e., its *ℓ*[∞] norm):

![](images/pg80-5.png)

Here, we have that ∥**g**[*t*]∥[∞]≤ 1 by the assumption that the losses are bounded by 1.

To bound the latter, notice that the probability that ![](images/pg80-in-7.png)is the leader at time *t* is the probability that −**n**(*i*[*t*]) *\> v* for some value *v* that depends on the entire loss sequence until now. On the other hand, given ![](images/x-cap.png)[*t*], we have that ![](images/pg81-in-1.png)remains the leader if −**n**(*i*[*t*]) *\> v* + **g**[*t*](*i*[*t*]), since it was a leader by a margin of more than the cost it will suffer. Thus,

![](images/pg81-1.png)

Substituting this bound back into equation ([5.6](#chapter_5.xhtml#eq5-6)), we have

![](images/pg81-2.png)

and simplifying this expression concludes the proof of the theorem.

☐

## 5.6 Adaptive Gradient Descent

Thus far, we have introduced regularization as a general methodology for deriving OCO algorithms. The main theorem of this chapter, theorem 5.1, bounds the regret of the RFTL algorithm for any strongly convex regularizer as

![](images/eq5-7.png)

In addition, we have seen how to derive the OGD and the multiplicative weights algorithms as special cases of the RFTL methodology. But are there other special cases of interest, besides these two basic algorithms, that warrant such general and abstract treatment?

There are surprisingly few cases of interest besides the Euclidean and Entropic regularizations and their matrix analogs.^([3](#chapter_5.xhtml#chapter5-3)) However, in this chapter, we will give some justification of the abstract treatment of regularization.

Our treatment is motivated by the following question: thus far, we have thought of *R* as a strongly convex function, but which strongly convex function should we choose in order to minimize regret? This is a deep and difficult question that has been considered in the optimization literature since its early history. Naturally, the optimal regularization should depend on both the convex underlying decision set, as well as the actual cost functions (see the exercises at the end of this chapter for a natural candidate of a regularization function that depends on the convex decision set).

We shall treat this question no differently than we treat other optimization problems throughout this manuscript itself: we’ll learn the optimal regularization online! That is, a regularizer that adapts to the sequence of cost functions and is in a sense the “optimal” regularization to use in hindsight. This gives rise to the AdaGrad (whose name stands for “Adaptive subGradient”) [algorithm 5.7](#chapter_5.xhtml#algo5-7), which explicitly optimizes over the regularization choice in line 5 to minimize the gradient norms, which is the dominant expression in equation ([5.7](#chapter_5.xhtml#eq5-7)).

![](images/Algorithm5-7.png)

AdaGrad comes in two versions: diagonal and full matrix, with the first being particularly efficient for implementing with negligible computational overhead over OGD. In the algorithm definition and throughout this chapter, the notation *A*^(−1) refers to the Moore-Penrose pseudoinverse of matrix *A*.

The computation in line 5 finds the regularization matrix *H*, which minimizes the norm of the gradients from within the positive semidefinite cone, with or without a diagonal constraint. This is closely related, as we shall see, to optimization with regard to two natural sets of matrices:

*   1.   ℋ[1] = {*H* = *diag*(*H*)*, H* ≽ 0 *, Tr*(*H*) ≤ 1}
*   2.   ℋ[2] = {*H* ≽ 0 *, Tr*(*H*) ≤ 1}

This results in a regularization matrix that is provably optimal in the sense given by lemma 5.4.

**Lemma 5.4** *For* ℋ[*i*] ∈{ℋ[1], ℋ[2]} *with the corresponding H*[*T*],

![](images/pg83-1.png)

Using this lemma, we show the regret of AdaGrad is at most a constant factor larger than the minimum regret of all RFTL algorithms with regularization functions whose Hessian is fixed and belongs to the class ℋ[*i*]. Furthermore, the regret of the diagonal version can be a factor ![](images/pg83-in-1.png)smaller than that of OGD for certain gradient geometries. The regret bound on AdaGrad is formally stated in theorem 5.5.

**Theorem 5.5** *Let* {**x**[*t*]} *be defined by [algorithm 5.7](#chapter_5.xhtml#algo5-7) with parameters η* = *D (full matrix) or η* = *D*[∞] *(diagonal). Then for any* **x**^(*⋆*) ∈𝒦,

![](images/pg83-2.png)

Before proceeding to the analysis, we consider when the regret bounds for AdaGrad improve upon those of OGD. One such case is when 𝒦 is the unit cube in *d*\-dimensional Euclidean space. This convex set has *D*[∞] = 1 and ![](images/pg83-in-2.png). Lemma 5.4 and theorems 5.1 and 5.5 imply that the regret of diagonal AdaGrad and OGD are bounded by

![](images/pg83-3.png)

The relationship between the two terms depends on the matrix *diag*(*G*[*T*]). If this matrix is sparse, then AdaGrad has a superior bound by at most a ![](images/pg83-in-3.png)factor. For other convex bodies, such as the Euclidean ball, and when matrix *G*[*T*] is dense, the regret of OGD can be a factor of ![](images/pg83-in-4.png)lower.

### 5.6.1 Analysis of adaptive regularization

We proceed with the proof of theorem 5.5. The first component is lemma 5.5, which generalizes the RFTL analysis to changing regularization.

**Lemma 5.5** *Let H*[0] = arg min[*H*≽0]{**Tr**(*H*)} = 0,

![](images/pg83-4.png)

*Proof.* By the definition of **y**[*t*+1],

![](images/pg84-1.png)

Multiplying the transpose of the first equation by the second, we get

![](images/eq5-8.png)

Since **x**[*t*+1] is the projection of **y**[*t*+1] in the norm induced by *H*[*t*], we have (see section 2.1.1 in chapter 2)

![](images/pg84-2.png)

This inequality is the reason for using generalized projections as opposed to standard projections, which were used in the analysis of OGD (see equation ([3.2](#chapter_3.xhtml#eq3-2)) in chapter 3). This fact, together with equation 5.8, gives

![](images/pg84-3.png)

Now, summing up over *t* = 1 to *T*, we get that

![](images/eq5-9.png)

In the last inequality, we use the definition *H*[0] = 0. We proceed to bound the first term. To this end, define the functions

![](images/pg84-4.png)

By definition, *H*[*t*] is the minimizer of ![](images/pg84-in-1.png)over ℋ. Therefore, using lemma 5.2, we have that

![](images/pg84-5.png)

We can now continue with the proof of theorem 5.5.

*Proof of theorem 5.5*. We bound both parts of lemma 5.5 with lemmas 5.6 and 5.7.

**Lemma 5.6** *For both the diagonal and full matrix versions of AdaGrad, the following holds:*

![](images/pg85-1.png)

**Lemma 5.7** *Let D*[∞] *denote the ℓ*[∞] *diameter of* 𝒦*, and D the Euclidean diameter. Then the following bounds hold:*

![](images/pg85-2.png)

Now combining lemma 5.5 with lemmas 5.6 and 5.7, and using ![](images/pg85-in-1.png)or ![](images/pg85-in-2.png)appropriately, we obtain the theorem.

☐

We proceed to complete the proof of lemmas 5.6 and 5.7.

*Proof of lemma 5.6*. The optimization problem of choosing *H*[*t*] in line 5 of [algorithm 5.7](#chapter_5.xhtml#algo5-7) has an explicit solution, given in the following proposition (whose proof is left as an exercise at the end of this chapter).

**Proposition 5.1** *Consider the following optimization problems, for A* ≽ 0*:*

![](images/pg85-3.png)

*Then the global optimizer to these problems is obtained at ![](images/pg85-in-3.png)and X* = *A*^(1/2)*, respectively. Over the set of diagonal matrices, the global optimizer is obtained at ![](images/pg85-in-4.png)and X* = **diag**(*A*)^(1/2)*, respectively.*

A direct corollary of this proposition gives lemma 5.4 as follows:

**Corollary 5.3**

![](images/pg85-4.png)

The remaining term from lemma 5.5 is the expression ![](images/pg85-in-5.png), which we proceed to bound.

*Proof of lemma 5.7*. By definition, *G*[*t*] ≽ *G*[*t*−1], and hence using proposition 5.1 and the definition of *H*[*t*] in line 5, we have that ![](images/pg86-in-1.png). Since for a diagonal matrix *H*, it holds that ![](images/pg86-in-2.png), we have

![](images/pg86-1.png)

Next, we consider the full-matrix case. By definition, *G*[*t*] ≽ *G*[*t*−1], and hence *H*[*t*] ≽ *H*[*t*−1]. Thus,

![](images/pg86-2.png)

## 5.7 Bibliographic Remarks

Regularization in the context of online learning was first studied by Grove, Littlestone, and Schuurmans (2001) and Kivinen and Warmuth (2001). The influential paper of Kalai and Vempala (2005) coined the term “follow-the-leader” (FTL) and introduced many of the techniques that followed in OCO. The latter paper studies random perturbation as a regularization and analyzes the FPL algorithm, following an early development by Hannan (1957) that was overlooked for many years.

In the context of OCO, the term “follow-the-regularized-leader” was coined in Shalev-Shwartz and Singer (2007) and Shalev-Shwartz (2007), and at roughly the same time, an essentially identical algorithm was called “RFTL” in Abernethy, Hazan, and Rakhlin (2008). The equivalence of RFTL and OMD was observed by Hazan and Kale (2008). The AdaGrad algorithm was introduced in Duchi, Hazan, and Singer (2010, 2011), its diagonal version was also discovered in parallel in McMahan and Streeter (2010). The analysis of AdaGrad presented in this chapter is due to Gupta, Koren, and Singer (2017).

Adaptive regularization has received significant attention due to its success in training deep neural networks, and notably in the development of adaptive algorithms that incorporate momentum and other heuristics, the most popular of which are AdaGrad, RMSprop (Tieleman and Hinton 2012), and Adam (Kingma and Ba 2014). For a survey of optimization for deep learning, see the comprehensive treatment by Goodfellow, Bengio, and Courville (2016).

There is a strong connection between randomized perturbation and deterministic regularization. In some scenarios, adding randomization can be thought of as a special case of deterministic, strongly convex regularization (Abernethy et al. 2014; Abernethy, Lee, and Tewari 2016).

## 5.8 Exercises

*   **1**.   This exercise concerns the notion of a dual norm.

**(a)** Show that the dual norm to a matrix norm given by *A* ≻ 0 corresponds to the matrix norm of *A*^(−1).

**(b)** Prove the generalized Cauchy-Schwarz inequality for any norm; that is,

![](images/pg87-1.png)

*   **2**.   Prove that the Bregman divergence is equal to the local norm at an intermediate point, that is,

![](images/pg87-2.png)

where **z** ∈ \[**x**, **y**\], and the interval \[**x**, **y**\] is defined as

![](images/pg87-3.png)

*   **3**.   Let ![](images/pg87-in-1.png)be the shifted Euclidean regularization function. Prove that the corresponding Bregman divergence is the Euclidean metric. Conclude that projections with respect to this divergence are standard Euclidean projections.
*   **4**.   Prove that the agile and lazy versions of the OMD meta-algorithm are different in the sense that they can produce different predictions over the same setting and cost functions. Show this for the case that the regularization is Euclidean and the decision set is the Euclidean ball.
*   **5**.   For this exercise, the decision set is the *n*\-dimensional simplex. Let *R*(**x**) = **x** log **x** be the negative entropy regularization function. Prove that the corresponding Bregman divergence is the relative entropy, and prove that the diameter *D*[*R*] of the *n*\-dimensional simplex with respect to this function is bounded by log *n*. Show that projections with respect to this divergence over the simplex amounts to scaling by the *ℓ*[1] norm.
*   **6**.   Prove that for the uniform distribution 𝒟 over the unit hypercube \[0, 1\]^(*n*), the parameters *σ, L* defined in section 5.5 of chapter 5 with respect to the Euclidean norm can be bounded as ![](images/pg88-in-1.png).
*   **7**.   Let 𝒟 be a one-sided, multidimensional exponential distribution, such that a vector **n** *∼* 𝒟 is distributed over each coordinate exponentially:

![](images/pg88-1.png)

Prove that

![](images/pg88-2.png)

(Hint: use the Chernoff bound.)  
Extra credit: Prove that **E**[**n** *∼* 𝒟]\[∥**n**∥[∞]\] = *H*[*n*], where *H*[*n*] is the *n*th harmonic number.

*   **8**.   ^(\*) A set 𝒦⊆ℝ^(*d*) is symmetric if **x** ∈𝒦 implies −**x** ∈𝒦. Symmetric sets give rise to a natural definition of a norm. Define the function ∥·∥[𝒦] : ℝ^(*d*) ↦ ℝ as

![](images/pg88-3.png)

Prove that ∥·∥[𝒦] is a norm if and only if 𝒦 is convex.

*   **9**.   ^(\*)\* Prove a lower bound of Ω(*T*) on the regret of the RFTL algorithm with ∥·∥ [𝒦] as a regularizer.
*   **10.** ^(\*) Prove that for positive definite matrices *A* ≽ *B* ≻ 0, the following statements hold:

**(a)** *A*^(1/2) ≽ *B*^(1/2)

**(b)** 2**Tr**((*A* − *B*)^(1/2)) + **Tr**(*A*^(−1/2)*B*) ≤ 2**Tr**(*A*^(1/2)).

*   **11.** ^(\*) Consider the following minimization problem, where *A* ≻ 0:

![](images/pg88-4.png)

Prove that its minimizer is given by *X* = *A*^(1/2)/**Tr**(*A*^(1/2)), and the minimum is obtained at **Tr**²(*A*^(1/2)).

## Notes

1.  [1](#chapter_5.xhtml#chapter5_1). Historically, lemma 5.1 is known as the *FTL-BTL*, which stands for “follow-the-leader versus be-the-leader.” BTL is a hypothetical algorithm that predicts **x**[*t*+1] at iteration *t*, where **x**[*t*] is the prediction made by FTL. These terms were coined by Kalai and Vempala (2005).
    
2.  [2](#chapter_5.xhtml#chapter5_2). In harmonic analysis of Boolean functions, a similar quantity is called *average sensitivity*.
    
3.  [3](#chapter_5.xhtml#chapter5_3). One such example is self-concordant barrier regularization, which we shall explore in the next chapter.
    

# 6 Bandit Convex Optimization

In many real-world scenarios, the feedback available to the decision maker is noisy, partial, or incomplete. Such is the case in online routing in data networks, in which an online decision maker iteratively chooses a path through a known network, and her loss is measured by the length (in time) of the path chosen. In data networks, the decision maker can measure the round-trip delay (RTD) of a packet through the network but rarely has access to the congestion pattern of the entire network.

Another useful example is that of online ad placement in web search. The decision maker iteratively chooses an ordered set of ads from an existing pool. Her reward is measured by the viewer’s response—if the user clicks a certain ad, a reward is generated according to the weight assigned to the particular ad. In this scenario, the search engine can inspect which ads were clicked through but cannot know whether different ads, had they been chosen to be displayed, would have been clicked through or not.

These examples can readily be modeled in the online convex optimization (OCO) framework, with the underlying sets being the convex hull of decisions. The pitfall of the general OCO model is the feedback; it is unrealistic to expect that the decision maker will have access to a gradient oracle at any point in the space for every iteration of the game.

## 6.1 The Bandit Convex Optimization Setting

The bandit convex optimization (BCO) model is virtually identical to the general OCO model explored in previous chapters, with the only difference being the feedback available to the decision maker.

To be more precise, the BCO framework can be seen as a structured, repeated game. The protocol of this learning framework is as follows: At iteration *t*, the online player chooses **x**[*t*] ∈𝒦. After committing to this choice, a convex cost function *f*[*t*] ∈ℱ: 𝒦 ↦ ℝ is revealed. Here, ℱ is the bounded family of cost functions available to the adversary. The cost incurred to the online player is the value of the cost function at the point that she committed to *f*[*t*](**x**[*t*]). As opposed to the OCO model, in which the decision maker has access to a gradient oracle for *f*[*t*] over 𝒦, in BCO, **the loss** *f*[*t*](**x**[*t*]) **is the only feedback available to the online player at iteration** *t***.** In particular, the decision maker does not know the loss that she would have had she chosen a different point **x** ∈𝒦 at iteration *t*.

As before, let *T* denote the total number of game iterations (i.e., predictions and their incurred loss). Let 𝒜 be an algorithm for BCO, which maps a certain game history to a decision in the decision set. We formally define the regret of 𝒜 that predicted *x*[1]*, …, x*[*T*] to be

![](images/pg90-1.png)

## 6.2 The Multiarmed Bandit (MAB) Problem

A classical model for decision making under uncertainty is the multiarmed bandit (MAB) model. This term nowadays refers to a multitude of different variants and subscenarios that are too large to survey. This section addresses what may be the simplest variant—the nonstochastic MAB problem—which is defined as follows.

Iteratively, a decision maker chooses between *n* actions *i*[*t*] ∈{1, 2*, …, n*}, while at the same time an adversary assigns each action a loss in the range \[0, 1\]. The decision maker receives the loss for *i*[*t*] and observes this loss and nothing else. The goal of the decision maker is to minimize her regret.

The reader undoubtedly observes that this setting is identical to the setting of prediction from expert advice, the only difference being the feedback available to the decision maker: whereas in the expert setting, the decision maker can observe the rewards or losses for all experts in retrospect, in the MAB setting, only the losses of the decisions actually chosen are known.

It is instructive to model this problem explicitly as a special case of BCO. Take the decision set to be the set of all distributions over *n* actions (i.e., 𝒦 = Δ[*n*] is the *n*\-dimensional simplex). The loss function is taken to be the linearization of the costs of the individual actions; that is,

![](images/pg90-2.png)

where *ℓ*[*t*](*i*) is the loss associated with the *i*th action at the *t*’th iteration. Thus, the cost functions are linear functions in the BCO model.

The MAB problem exhibits an exploration-exploitation trade-off: an efficient (low-regret) algorithm has to explore the value of the various actions in order to make the best decision. On the other hand, having gained sufficient information about the environment, a reasonable algorithm needs to exploit this action by picking the best action.

The simplest way to attain a MAB algorithm would be to separate exploration and exploitation. Such a method would proceed as follows:

*   1.   With some probability, explore the action space (i.e., by choosing an action uniformly at random). Use the feedback to construct an estimate of each action’s losses.
*   2.   Otherwise, use the estimates to apply a full-information experts algorithm as if the estimates are the true historical costs.

This simple scheme already gives a sublinear regret algorithm, presented in [algorithm 6.1](#chapter_6.xhtml#algo6-1).

![](images/Algorithm6-1.png)

**Theorem 6.1** *[Algorithm 6.1](#chapter_6.xhtml#algo6-1), with* 𝒜 *being the the online gradient descent (OGD) algorithm, guarantees the following regret bound:*

![](images/pg91-1.png)

*Proof.* For the random functions ![](images/pg92-in-1.png)defined in [algorithm 6.1](#chapter_6.xhtml#algo6-1), notice the following:

*   1.   ![](images/pg92-in-2.png).
*   2.   ![](images/pg92-in-3.png).

Therefore, the regret of the simple algorithm can be related to that of 𝒜 on the estimated functions.

On the other hand, the simple MAB algorithm does not always play out according to the distribution generated by 𝒜: with probability *δ*, it plays uniformly at random, which may lead to a regret of one on these exploration iterations. Let *S*[*t*] ⊆ \[*T*\] be those iterations in which *b*[*t*] = 1. This is captured by lemma 6.1.

**Lemma 6.1**

![](images/pg92-1.png)

*Proof.*

![](images/pg92-2.png)

We thus have

![](images/pg92-3.png)

![](images/pg93-1.png)

### 6.2.1 EXP3: Simultaneous exploration and exploitation

The simple algorithm given in [algorithm 6.1](#chapter_6.xhtml#algo6-1) can be improved by combining the exploration and exploitation steps. This gives a near-optimal regret algorithm, called EXP3, presented in [algorithm 6.2](#chapter_6.xhtml#algo6-2).

![](images/Algorithm6-2.png)

As opposed to the simple MAB algorithm, the EXP3 algorithm explores every iteration by always creating an unbiased estimator of the entire loss vector. This results in a possibly large magnitude of vectors ![](images/pg93-in-1.png)and a large gradient bound for use with OGD. However, the large-magnitude vectors are created with low probability (proportional to their magnitude), which allows a finer analysis.

Ultimately, the EXP3 algorithm attains a worst-case regret bound of ![](images/pg93-in-2.png), which is nearly optimal (up to a logarithmic term in the number of actions).

**Theorem 6.2** *[Algorithm 6.2](#chapter_6.xhtml#algo6-2) with nonnegative losses and ![](images/pg93-in-3.png)guarantees the following regret bound:*

![](images/pg93-3.png)

*Proof.* For the random losses ![](images/pg93-in-4.png)defined in [algorithm 6.2](#chapter_6.xhtml#algo6-2), notice that

![](images/pg93-4.png)

![](images/eq6-1.png)

Therefore, we have ![](images/pg94-in-1.png), and the expected regret with respect to function ![](images/pg94-in-2.png)is equal to that with respect to function {*f*[*t*]}. Thus, the regret with respect to ![](images/pg94-in-3.png)can be related to that of *ℓ*[*t*].

The EXP3 algorithm applies Hedge to the losses given by ![](images/pg94-in-3.png), which are all nonnegative and thus satisfy the conditions of theorem 1.3. Thus, the expected regret with respect to ![](images/pg94-in-3.png), can be bounded by

![](images/pg94-1.png)

We proceed to derive an algorithm for the more general setting of BCO that attains near-optimal regret.

## 6.3 A Reduction from Limited Information to Full Information

In this section, we derive a low-regret algorithm for the general setting of BCO. In fact, we shall describe a general technique for designing bandit algorithms, which is composed of two parts:

*   1.   A general technique for taking an OCO algorithm that uses only the gradients of the cost functions (formally defined later in this chapter), and applying it to a family of vector random variables with carefully chosen properties.
*   2.   Designing the random variables that allow the template reduction to produce meaningful regret guarantees.

We proceed to describe the two parts of this reduction, and in the remainder of this chapter, we describe two examples of using this reduction to design BCO algorithms.

### 6.3.1 Part 1: Using unbiased estimators

The key idea behind many of the efficient algorithms for BCO is the following: although we cannot calculate ∇*f*[*t*](**x**[*t*]) explicitly, it is possible to find an *observable* random variable **g**[*t*] that satisfies **E**\[**g**[*t*]\] ≈∇*f*[*t*](**x**[*t*]) = ∇[*t*]. Thus, **g**[*t*] can be seen as an estimator of the gradient. By substituting **g**[*t*] for ∇[*t*] in an OCO algorithm, we will show that many times, it retains its sublinear regret bound.

Formally, the family of regret minimization algorithms for which this reduction works is captured in definition 6.1.

**Definition 6.1** *(****first-order OCO algorithm****) Let* 𝒜 *be an OCO (deterministic) algorithm receiving an arbitrary sequence of differential loss functions f*[1]*, …, f*[*T*]*, and producing decisions* **x**[1] ←𝒜(∅), **x**[*t*] ←𝒜(*f*[1]*, …, f*[*t*−1]). 𝒜 *is called a* first-order online algorithm *if the following holds:*

*   *The family of loss functions* ℱ *is closed under addition of linear functions: if f* ∈ℱ *and* **u** ∈ ℝ^(*n*)*, then f* + **u**^⊤**x** ∈ℱ.
*   *Let* ![](images/pg95-in-1.png)*be the linear function* ![](images/pg95-in-2.png)*, then for every iteration t* ∈ \[*T*\]*:*

![](images/pg95-1.png)

We can now consider a formal reduction from any first-order online algorithm to a BCO algorithm as in [algorithm 6.3](#chapter_6.xhtml#algo6-3).

![](images/Algorithm6-3.png)

Perhaps surprisingly, under very mild conditions, the reduction given here guarantees the same regret bounds as the original first-order algorithm 𝒜[*t*] up to the magnitude of the estimated gradients. This is captured in lemma 6.2.

**Lemma 6.2** *Let* **u** *be a* fixed *point in* 𝒦*. Let f*[1]*, …, f*[*T*]: 𝒦→ ℝ *be a sequence of differentiable functions. Let* 𝒜 *be a first-order online algorithm that ensures a regret bound of the form* Regret[*T*](𝒜) ≤ *B*[𝒜](∇*f*[1](**x**[1])*, …*, ∇*f*[*T*](**x**[*T*])) *in the full information setting. Define the points* {**x**[*t*]} *as:* **x**[1] ←𝒜(∅), **x**[*t*] ←𝒜(**g**1*, …*, **g**[*t*]−1) *where each* **g***t is a vector valued random variable such that*

![](images/pg96-1.png)

*Then the following holds for all* **u** ∈𝒦*:*

![](images/pg96-2.png)

*Proof.* Define the functions *h*[*t*]: 𝒦→ ℝ as follows:

![](images/pg96-3.png)

Note that

![](images/pg96-4.png)

Therefore, deterministically applying a first-order method 𝒜 on the random functions *h*[*t*] is equivalent to applying 𝒜 on a stochastic first-order approximation of the deterministic functions *f*[*t*]. Thus, by the full-information regret bound of 𝒜, we have

![](images/eq6-2.png)

Also, note that

![](images/pg96-5.png)

where we used **E**\[***ξ***[*t*]|**x**[1]*, f*[1]*, …*, **x**[*t*]*, f*[*t*]\] = 0. Similarly, since **u** ∈𝒦 is fixed, **E**\[*h*[*t*](**u**)\] = *f*[*t*](**u**). Lemma 6.2 follows from taking the expectation of equation ([6.2](#chapter_6.xhtml#eq6-2)).

☐

### 6.3.2 Part 2: Pointwise gradient estimators

In subsection 6.3.2, we described how to convert a first-order algorithm for OCO to one that uses bandit information using specially tailored random variables. We now describe how to create these vector random variables.

Although we cannot calculate ∇*f*[*t*](**x**[*t*]) explicitly, it is possible to find an *observable* random variable **g**[*t*] that satisfies **E**\[**g**[*t*]\] ≈∇*f*[*t*], and serves as an estimator of the gradient.

The question is how to find an appropriate **g**[*t*], and to answer it, we begin with an example in a one-dimensional (1D) case.

**Example 6.1** *A 1D gradient estimate  
Recall the definition of the derivative:*

![](images/pg97-1.png)

*This shows that for a 1D derivative, two evaluations of f are required. Since in our problem we can perform only one evaluation, let us define g*(*x*) *as follows:*

![](images/eq6-3.png)

*It is clear that*

![](images/pg97-2.png)

*Thus,* ***in expectation****, for small δ*, *g*(*x*) *approximates f*′(*x*).

**6.3.2.1 The sphere-sampling estimator** We will now show how the gradient estimator (equation ([6.3](#chapter_6.xhtml#eq6-3))) can be extended to the multidimensional case. Let **x** ∈ ℝ^(*n*), and let *B*[*δ*] and *S*[*δ*] denote the *n*\-dimensional ball and sphere with radius *δ*:

![](images/pg97-3.png)

We define ![](images/pg97-in-1.png)to be a *δ*\-smoothed version of *f*(**x**):

![](images/eq6-4.png)

where **v** is drawn from a uniform distribution over the unit ball. This construction is very similar to the one used in lemma 2.4 in context of convergence analysis for convex optimization. However, our goal here is very different.

Note that when *f* is linear, we have ![](images/pg97-in-2.png). We shall address the scenario in which *f* is indeed linear as a special case, showing how to estimate the gradient of ![](images/pg97-in-3.png), which, under the assumption that *f* is linear, is also the gradient of *f*(**x**). Lemma 6.3 shows a simple relation between gradient ![](images/pg97-in-4.png)and a uniformly drawn unit vector.

**Lemma 6.3** *Fix δ >* 0*. Let* ![](images/pg98-in-1.png)*be as defined in equation* ([6.4](#chapter_6.xhtml#eq6-4))*, and let* **u** *be a uniformly drawn unit vector* **u** *∼* 𝕊*. Then*

![](images/pg98-1.png)

*Proof.* Using Stokes’ theorem from calculus, we have

![](images/eq6-5.png)

From equation ([6.4](#chapter_6.xhtml#eq6-4)), and by definition of expectation, we have

![](images/eq6-6.png)

where vol(*B*[*δ*]) is the volume of an *n*\-dimensional ball of radius *δ*. Similarly,

![](images/eq6-7.png)

Combining equations ([6.4](#chapter_6.xhtml#eq6-4)), ([6.5](#chapter_6.xhtml#eq6-5)), ([6.6](#chapter_6.xhtml#eq6-6)), and ([6.7](#chapter_6.xhtml#eq6-7)), and the fact that the ratio of the volume of a ball in *n* dimensions and the sphere of dimension *n* − 1 is vol[*n*]*B*[*δ*]/vol[*n*−1]*S*[*δ*] = *δ/n*, gives the desired result.

☐

Under the assumption that *f* is linear, lemma 6.3 suggests a simple estimator for the gradient ∇*f*. Draw a random unit vector **u**, and let ![](images/pg98-in-2.png).

**6.3.2.2 The ellipsoidal-sampling estimator** The sphere estimator discussed here is at times difficult to use: when the center of the sphere is very close to the boundary of the decision set, only a very small sphere can fit completely inside. This results in a gradient estimator with large variance.

In such cases, it is useful to consider ellipsoids rather than spheres. Luckily, the generalization to ellipsoidal sampling for gradient estimation is a simple corollary of the derivation given here.

**Corollary 6.1** *Consider a continuous function f*: ℝ^(*n*) → ℝ*, an invertible matrix A* ∈ ℝ^(*n*×*n*)*, and let* **v** *∼* 𝔹^(*n*) *and* **u** *∼* 𝕊^(*n*)*. Define the smoothed version of f with respect to A:*

![](images/pg98-2.png)

*Then the following holds:*

![](images/pg98-3.png)

 

![](images/pg99-1.png)

## 6.4 Online Gradient Descent without a Gradient

The simplest and historically earliest application of the BCO-to-OCO reduction outlined earlier in this chapter is the application of the OGD algorithm to the bandit setting. The FKM algorithm (named after its inventors; see section 6.6) is outlined in [algorithm 6.4](#chapter_6.xhtml#algo6-4).

For simplicity, we assume that set 𝒦 contains the unit ball centered at the zero vector, denoted as **0**. Denote ![](images/pg99-in-1.png). It is left as an exercise to show that 𝒦[*δ*] is convex for any 0 *< δ <* 1 and all balls of radius *δ* around points in 𝒦[*δ*] are contained in 𝒦.

We also assume, for simplicity, that the adversarially chosen cost functions are bounded by one over 𝒦 (i.e., that |**f**[*t*](**x**)|≤ 1 for all **x** ∈𝒦).

![](images/Algorithm6-4.png)

The FKM algorithm is an instantiation of the generic reduction from BCO to OCO with spherical gradient estimators over set 𝒦[*δ*]. It iteratively projects onto 𝒦[*δ*], to have enough space for spherical gradient estimation. This degrades its performance by a controlled quantity. The regret in [algorithm 6.4](#chapter_6.xhtml#algo6-4) is bounded as follows.

**Theorem 6.3** *[Algorithm 6.4](#chapter_6.xhtml#algo6-4), with parameters ![](images/pg99-in-2.png), guarantees the following expected regret bound:*

![](images/pg99-2.png)

![Figure 6.1 The Minkowski set 𝒦δ](images/figure6-1.png)

Figure 6.1  
The Minkowski set 𝒦[*δ*]

*Proof.* Recall the previous notation of ![](images/pg100-in-1.png). Denote

![](images/pg100-1.png)

Then, by properties of projections, we have ![](images/pg100-in-2.png), where *D* is the diameter of 𝒦. Thus, assuming that the cost function {*f*[*t*]} is *G*\-Lipschitz, we have

![](images/eq6-8.png)

Denote ![](images/pg100-in-3.png)for shorthand. We can now bound the regret by

![](images/pg100-2.png)

![](images/pg101-1.png)

## 6.5 Optimal Regret Algorithms for Bandit Linear Optimization

A special case of BCO that is of considerable interest is bandit linear optimization (BLO). This setting has linear cost functions and captures the network routing and placement examples discussed in the beginning of this chapter, as well as the nonstochastic MAB problem.

In this section, we give near-optimal regret bounds for BLO using techniques from interior point methods for convex optimization.

The generic OGD method of section 6.4 suffers from three pitfalls:

*   1.   The gradient estimators are biased and estimate the gradient of a smoothed version of the real cost function.
*   2.   The gradient estimators require enough wiggle room and are thus ill-defined on the boundary of the decision set.
*   3.   The gradient estimates have a potentially large magnitude, proportional to the distance from the boundary.

Fortunately, the first issue is nonexistent for linear functions—the gradient estimators turn out to be unbiased for linear functions. In the notation given in the previous chapters, we have for linear functions:

![](images/pg101-2.png)

Thus, lemma 6.3 gives us a stronger guarantee:

![](images/pg101-3.png)

To resolve the second and third issues, we use self-concordant barrier functions, a rather advanced technique from interior point methods for convex optimization.

### 6.5.1 Self-concordant barriers

Self-concordant barrier functions were devised in the context of interior point methods for optimization as a way of ensuring that the Newton method converges in polynomial time over bounded convex sets. In this brief introduction, we survey some of their beautiful properties that will allow us to derive an optimal regret algorithm for BLO.

**Definition 6.2** *Let* 𝒦∈ ℝ^(*n*) *be a convex set with a nonempty interior int*(𝒦)*. A function* ℛ: *int*(𝒦) → ℝ *is called ν\-self-concordant if the following are the case:*

*   *1.   *ℛ *is three times continuously differentiable and convex, and approaches infinity along any sequence of points approaching the boundary of* 𝒦.
*   *2.   For every* **h** ∈ ℝ^(*n*) *and* **x** ∈ *int*(𝒦)*, the following holds:*

![](images/pg102-1.png)

where the third-order differential is defined as

![](images/pg102-2.png)

The Hessian of a self-concordant barrier induces a local norm at every **x** ∈ int(𝒦), we denote this norm by ||·||[**x**] and its dual by ||·||[**x**]^(\*), which are defined in ∀**h** ∈ ℝ^(*n*) by

![](images/pg102-3.png)

We assume that ∇²ℛ(**x**) always has full rank. In BCO applications, this is easy to ensure by adding a fictitious quadratic function to the barrier, which does not affect the overall regret by more than a constant.

Let ℛ be a self-concordant barrier and **x** ∈ int(𝒦). The *Dikin ellipsoid* is

![](images/pg102-4.png)

That is, the ∥·∥[**x**]\-unit ball centered around **x**, is completely contained in 𝒦.

In the next analysis, we will need to bound ℛ(**y**) −ℛ(**x**) for **x**, **y** ∈ int(𝒦), for which lemma 6.4 is useful.

**Lemma 6.4** *Let* ℛ *be a ν\-self concordant function over* 𝒦*, then for all* **x**, **y** ∈ *int*(𝒦)*:*

![](images/pg103-1.png)

*where π*[**x**](**y**) = inf{*t* ≥ 0: **x** + *t*^(−1)(**y** −**x**) ∈𝒦}.

The function *π*[**x**](**y**) is called the *Minkowski function* for 𝒦, and its output is always in the interval \[0, 1\]. Moreover, as *y* approaches the boundary of 𝒦, then *π*[**x**](**y**) → 1.

Another important property of self-concordant functions is the relationship between a point and the optimum, and the norm of the gradient at the point, according to the local norm, as given by lemma 6.5.

**Lemma 6.5** *Let* **x** ∈ *int*(𝒦) *be such that ![](images/pg103-in-1.png), and let* **x**^(*⋆*) = arg min[**x**∈𝒦]ℛ(**x**)*. Then*

![](images/pg103-2.png)

### 6.5.2 A near-optimal algorithm

We have now set up all the necessary tools to derive a near-optimal BLO algorithm, as presented in [algorithm 6.5](#chapter_6.xhtml#algo6-5).

![](images/Algorithm6-5.png)

**Theorem 6.4** *For an appropriate choice of η, δ, the SCRIBLE algorithm guarantees*

![](images/pg103-3.png)

*Proof.* First, we note that **y**[*t*] ∈ 𝒦 never steps outside the decision set. The reason is that **x**[*t*] ∈𝒦 and **y**[*t*] lies in the Dikin ellipsoid centered at **x**[*t*].

Further, by corollary 6.1, we have

![](images/pg104-1.png)

where the latter equality follows since *f*[*t*] is linear, and thus its smoothed version is identical to itself.

A final observation is that line 6 in [algorithm 6.5](#chapter_6.xhtml#algo6-5) is an invocation of the Regularized Follow The Leader (RFTL) algorithm with the self-concordant barrier ℛ serving as a regularization function. The RFTL algorithm for linear functions is a first-order OCO algorithm, and thus lemma 6.2 applies.

We can now bound the regret by

![](images/pg104-2.png)

Here, we use our notation from chapter 5 for the local norm ![](images/pg104-in-1.png).

To bound the last expression, we use lemma 6.5, and the definition of **x***t*+1 = arg min[**x**∈𝒦]Φ[*t*](**x**), where ![](images/pg104-in-2.png)is a self-concordant barrier. Thus,

![](images/pg104-3.png)

since ∇Φ[*t*−1](**x**[*t*]) = 0 by definition of **x**[*t*]. Recall that to use lemma 6.5, we need ![](images/pg104-in-3.png), which is true by choice of *η*, and since

![](images/pg104-4.png)

Thus,

![](images/pg104-5.png)

It remains to bound the Bregman divergence with respect to **x**^(*⋆*), for which we use a similar technique as in the analysis of [algorithm 6.4](#chapter_6.xhtml#algo6-4), and to bound the regret with respect to ![](images/pg105-in-1.png), which is the projection of **x**^(*⋆*) onto 𝒦[*δ*]. Using equation ([6.8](#chapter_6.xhtml#eq6-8)), we can bound the overall regret by

![](images/pg105-1.png)

Taking ![](images/pg105-in-2.png)and ![](images/pg105-in-3.png), this bound implies our theorem.

☐

## 6.6 Bibliographic Remarks

The MAB problem goes back more than fifty years, to the work of Robbins (1952); see Bubeck and Cesa-Bianchi (2012) for a much more detailed history. The nonstochastic MAB problem and the EXP3 algorithm, as well as tight lower bounds, were given in a seminal paper by Auer, Cesa-Bianchi, Freund, and Schapire (2003). The logarithmic gap in attainable regret for nonstochastic MAB was resolved Audibert and Bubeck (2009).

BCO for the special case of linear cost functions and the flow polytope was introduced and studied by Awerbuch and Kleinberg (2008) in the context of online routing. The full-generality BCO setting was introduced by Flaxman, Kalai, and McMahan (2005), who gave the first efficient and low-regret algorithm for BCO. Tight bounds for BCO were obtained by Bubeck et al. (2015) for the 1D case, via an inefficient algorithm by Hazan and Li (2016), and finally with a polynomial time algorithm in Bubeck, Lee, and Eldan (2017).

The special case in which the cost functions are linear, BLO, has received significant attention. Dani, Hayes, and Kakade (2008) gave an optimal regret algorithm up to constants depending on the dimension. Abernethy, Hazan, and Rakhlin (2008) gave an efficient algorithm and introduced self-concordant barriers to the bandit setting. Self-concordant barrier functions were devised in the context of polynomial-time algorithms for convex optimization in the seminal work of Nesterov and Nemirovski (1994). Lower bounds for regret in the bandit linear optimization setting were studied by Shamir (2015).

In this chapter, we have considered the expected regret as a performance metric. Significant literature is devoted to high-probability guarantees on the regret. High-probability bounds for the MAB problem were given in Auer et al. (2003), and for bandit linear optimization in Abernethy and Rakhlin (2009). Other more refined metrics have been recently explored by Dekel, Tewari, and Arora (2012) and in the context of adaptive adversaries by Neu, Gy![](images/pg106-in-1a.png)rgy, Szepesvári, and Antos (2014), Yu and Mannor (2009), Even-Dar, Kakade, and Mansour (2009), Mannor and Shimkin (2003), and Yu, Mannor, and Shimkin (2009).

For a recent comprehensive text on bandit algorithms, see Lattimore and Szepesvári (2020).

## 6.7 Exercises

*   **1.**   Prove a lower bound on the regret of any algorithm for BCO: show that for the special case of BCO over the unit sphere, any online algorithm must incur a regret of ![](images/pg106-in-1.png).
*   **2.**   ^(\*)Strengthen the above bound: show that for the special case of BLO over the *d*\-dimensional unit simplex, with cost functions bounded in *ℓ*[∞] norm by 1, any online algorithm must incur a regret of ![](images/pg106-in-2.png)as *T →* ∞, up to logarithmic terms in *T*.
*   **3.**   Let 𝒦 be convex. Show that set 𝒦[*δ*] is convex.
*   **4.**   Let 𝒦 be convex and contain the unit ball centered at zero. Show that for any point **x** ∈𝒦[*δ*], the ball of radius *δ* centered at **x** is contained in 𝒦.
*   **5.**   Consider the BCO setting with *H*\-strongly convex functions, *H* is known a priori to the online learner. Show that in this case, we can attain a regret bound of *Õ*(*T*^(2/3)).  
    Hint: Recall that we can attain a regret bound of *O*(log *T*) in the full-information OCO with *H*\-strongly convex functions, and the notation *Õ*(·) hides constant and polylogarithmic terms.
*   **6.**   Consider the BCO setting with the following twist: at every iteration, the player is allowed to observe *two* evaluations of the function, as opposed to just one. That is, the player gives *x*[*t*]*, y*[*t*] and observes *f*[*t*](*x*[*t*])*, f*[*t*](*y*[*t*]). Regret is measured with regard to *x*[*t*], as usual:

![](images/pg106-1.png)

**(a)** Show how to construct a biased gradient estimator for *f*[*t*] with arbitrary small bias and *constant* variance that is independent of the bias.

**(b)** Show how to use the gradient estimator from question (a) to give an efficient algorithm for this setting that attains ![](images/pg106-in-3.png)regret.

# 7 Projection-Free Algorithms

In many computational and learning scenarios, the main bottleneck of optimization, both online and oﬄine, is the computation of projections onto the underlying decision set (see section 2.1.1 in chapter 2). In this chapter, we introduce projection-free methods for online convex optimization (OCO), which yield more efficient algorithms in these scenarios.

The motivating example throughout this chapter is the problem of matrix completion, which is a widely used and accepted model in the construction of recommendation systems. For matrix completion and related problems, projections amount to expensive linear algebraic operations, and avoiding them is crucial in big data applications.

We start with a detour into classical oﬄine convex optimization and describe the conditional gradient algorithm, also known as the Frank-Wolfe algorithm. Afterward, we describe problems for which linear optimization can be carried out much more efficiently than projections. We conclude with an OCO algorithm that eschews projections in favor of linear optimization, in much the same flavor as its oﬄine counterpart.

## 7.1 Review: Relevant Concepts from Linear Algebra

This chapter addresses rectangular matrices, which model applications such as recommendation systems naturally. Consider a matrix *X* ∈ ℝ^(*n*×*m*). A nonnegative number *σ* ∈ ℝ[+] is said to be a singular value for *X* if there are two vectors **u** ∈ ℝ^(*n*), **v** ∈ ℝ^(*m*) such that

![](images/pg107-1.png)

The vectors **u**, **v** are called the *left* and *right singular vectors*, respectively. The nonzero singular values are the square roots of the eigenvalues of the matrix *XX*^⊤ (and *X*^⊤*X*). Matrix *X* can be written as

![](images/pg108-1.png)

where *ρ* = min{*n, m*}, matrix *U* is an orthogonal basis of the left singular vectors of *X*, matrix *V* is an orthogonal basis of right singular vectors, and Σ is a diagonal matrix of singular values. This form is called the *singular value decomposition* for *X*.

The number of nonzero singular values for *X* is called its *rank*, which we denote by *k* ≤ *ρ*. The nuclear norm of *X* is defined as the *ℓ*[1] norm of its singular values, and it is denoted by

![](images/pg108-2.png)

It can be shown (see the exercises at the end of this chapter) that the nuclear norm is equal to the trace of the square root of the matrix times its transpose; that is,

![](images/pg108-3.png)

We denote by *A* ∙ *B* the inner product of two matrices as vectors in ℝ^(*n*×*m*); that is,

![](images/pg108-4.png)

## 7.2 Motivation: Recommender Systems

Media recommendations have changed significantly with the advent of the Internet and the rise of online media stores. The large amount of data collected allows efficient clustering and accurate prediction of users’ preferences for a variety of media. A well-known example is the so called Netflix challenge—a competition of automated tools for recommendations from a large data set of users’ motion picture preferences.

One of the most successful approaches for automated recommendation systems, as proved in the Netflix competition, is matrix completion. Perhaps the simplest version of the problem can be described as follows.

The entire data set of user-media preference pairs is thought of as a partially observed matrix. Thus, every person is represented by a row in the matrix and every column represents a media item (in this case a movie). For simplicity, let us think of the observations as binary—a person either likes or dislikes a particular movie. Thus, we have a matrix *M* ∈{0, 1, \*}^(*n*×*m*), where *n* is the number of persons considered, *m* is the number of movies in the library, and 0/1 and \* signify “dislike,” “like,” and “unknown,” respectively:

![](images/pg109-1.png)

The natural goal is to complete the matrix (i.e., correctly assign 0 or 1 to the unknown entries). As defined so far, the problem is ill posed since any completion would be equally good (or bad), and no restrictions have been placed on the completions.

The common restriction on completions is that the “true” matrix has a low rank. Recall that a matrix *X* ∈ ℝ^(*n*×*m*) has rank *k < ρ* = min{*n, m*} if and only if it can be written as

![](images/pg109-2.png)

The intuitive interpretation of this property is that each entry in *M* can be explained by only *k* numbers. In matrix completion, this means, intuitively, that there are only *k* factors that determine a person’s preference of movies, such as genre, director, actors, and so on.

Now the simplistic matrix completion problem can be well formulated, as in the following mathematical program. Denote by ∥·∥[*ob*] the Euclidean norm only on the observed (nonstarred) entries of *M*; that is,

![](images/pg109-3.png)

The mathematical program for matrix completion is given by

![](images/pg109-4.png)

Since the constraint over the rank of a matrix is nonconvex, it is standard to consider a relaxation that replaces the rank constraint by the nuclear norm. It is known that the nuclear norm is a lower bound on the matrix rank if the singular values are bounded by one (see the exercises at the end of this chapter). Thus, we arrive at the following convex program for matrix completion:

![](images/eq7-1.png)

We consider algorithms to solve this convex optimization problem next.

## 7.3 The Conditional Gradient Method

In this section, we return to the basics of convex optimization—minimization of a convex function, over a convex domain, as studied in chapter 2.

The conditional gradient (CG) method, or Frank-Wolfe algorithm, is a simple algorithm for minimizing a smooth convex function *f* over a convex set 𝒦⊆ ℝ^(*n*). The appeal of the method is that it is a first order interior point method—the iterates always lie inside the convex set, and thus no projections are needed, and the update step on each iteration simply requires to minimize a linear objective over the set. The basic method is given in [algorithm 7.1](#chapter_7.xhtml#algo7-1).

![](images/Algorithm7-1.png)

Note that in the CG method, the update to the iterate **x**[*t*] may be not be in the direction of the gradient, as **v**[*t*] is the result of a linear optimization procedure in the direction of the negative gradient. This is depicted in [figure 7.1](#chapter_7.xhtml#fig7-1).

![Figure 7.1 Direction of progression of the CG algorithm](images/figure7-1.png)

[Figure 7.1](#chapter_7.xhtml#rfig7-1)  
Direction of progression of the CG algorithm

Theorem 7.1 gives an essentially tight performance guarantee of this algorithm over smooth functions. Recall the notation from chapter 2: **x**^(*⋆*) denotes the global minimizer of *f* over 𝒦, *D* denotes the diameter of the set 𝒦, and *h*[*t*] = *f*(**x**[*t*]) − *f*(**x**^(*⋆*)) denotes the suboptimality of the objective value in iteration *t*.

**Theorem 7.1** *The CG algorithm applied to β\-smooth functions with stepsizes ![](images/pg110-in-1.png)attains the following convergence guarantee:*

![](images/pg110-1.png)

*Proof.* As done before in this manuscript, we denote ∇[*t*] = ∇*f*(**x**[*t*]). For any set of stepsizes, we have

![](images/pg110-2.png)

 ![](images/eq7-2.png)

We reached the recursion ![](images/pg111-in-1.png), and by lemma 7.1, we obtain

![](images/pg111-1.png)

**Lemma 7.1** *Let* {*h*[*t*]} *be a sequence that satisfies the recurence*

![](images/pg111-2.png)

*Then taking ![](images/pg111-in-2.png)implies* 

![](images/pg111-3.png)

*Proof.* This is proved by induction on *t*, as follows.

**Induction base.** For *t* = 1, we have

![](images/pg112-1.png)

**Induction step.**

![](images/pg112-2.png)

### 7.3.1 Example: Matrix completion via conditional gradient

As an example of an application for the CG algorithm, recall the mathematical program given in equation ([7.1](#chapter_7.xhtml#eq7-1)). The gradient of the objective function at point *X*^(*t*) is

![](images/eq7-3.png)

Over the set of bounded-nuclear norm matrices, the linear optimization of line 3 in [algorithm 7.1](#chapter_7.xhtml#algo7-1) becomes

![](images/pg112-3.png)

For simplicity, let’s consider square symmetric matrices, for which the nuclear norm is equivalent to the trace norm, and the optimization problem becomes

![](images/pg112-4.png)

It can be shown that this program is equivalent to the following (see the exercises at the end of the chapter):

![](images/pg112-5.png)

Hence, this is an eigenvector computation in disguise! Computing the largest eigenvector of a matrix takes linear time via the power method, which also applies more generally to computing the largest singular value of rectangular matrices. With this, step 3 of [algorithm 7.1](#chapter_7.xhtml#algo7-1), which amounts to equation ([7.1](#chapter_7.xhtml#eq7-1)), becomes computing *v*[max](−∇*f*(*X*^(*t*))), the largest eigenvector of −∇*f*(*X*^(*t*)). [Algorithm 7.1](#chapter_7.xhtml#algo7-1) takes on the modified form described in [algorithm 7.2](#chapter_7.xhtml#algo7-2).

![](images/Algorithm7-2.png)

Comparison to other gradient-based methods. How does this compare to previous convex optimization methods for solving the same matrix completion problem? As a convex program, we can apply gradient descent (GD), or even more advantageously in this setting, stochastic gradient descent (SGD), as in section 3.4 in chapter 3. Recall that the gradient of the objective function at point *X*^(*t*) takes the simple form in equation ([7.3](#chapter_7.xhtml#eq7-3)). A stochastic estimate for the gradient can be attained by observing just a single entry of the matrix *M*, and the update itself takes constant time as the gradient estimator is sparse. However, the projection step is significantly more difficult.

In this setting, the convex set 𝒦 is the set of bounded nuclear norm matrices. Projecting a matrix onto this set amounts to calculating the SVD of the matrix, which is similar in computational complexity to algorithms for matrix diagonalization or inversion. The best-known algorithms for matrix diagonalization are superlinear in the matrices’ size, and thus they are impractical for large data sets that are common in applications.

In contrast, the CG method does not require projections at all, and it replaces them with linear optimization steps over the convex set, which we have observed to amount to singular vector computations. The latter can be implemented to take linear time via the power method or the Lanczos algorithm (see bibliography).

Thus, the CG method allows optimization of equation ([7.1](#chapter_7.xhtml#eq7-1)) with a linear-time operation (eigenvector using the power method) per iteration, rather than a significantly more expensive computation (SVD) needed for GD.

## 7.4 Projections versus Linear Optimization

The CG (Frank-Wolfe) algorithm described before does not resort to projections. Rather, it computes a linear optimization problem of the form

![](images/eq7-4.png)

When is the CG method computationally preferable? The overall computational complexity of an iterative optimization algorithm is the product of the number of iterations and the computational cost per iteration. The CG method does not converge as well as the most efficient GD algorithms, meaning that it requires more iterations to produce a solution of a comparable level of accuracy. However, for many interesting scenarios the computational cost of a linear optimization step (equation ([7.4](#chapter_7.xhtml#eq7-4))) is *significantly* lower than that of a projection step.

Let us point out several examples of problems for which we have very efficient linear optimization algorithms, whereas our state-of-the-art algorithms for computing projections are significantly slower.

Recommendation systems and matrix prediction. In the example pointed out in section 7.3, known methods for projection onto the spectahedron, or more generally the bounded nuclear-norm ball, require singular value decompositions, which take superlinear time via our best-known methods. In contrast, the CG method requires maximal eigenvector computations that can be carried out in linear time via the power method (or the more sophisticated Lanczos algorithm).

Network routing and convex graph problems. Various routing and graph problems can be modeled as convex optimization problems over a convex set called the *flow polytope*.

Consider a directed acyclic graph with *m* edges, a source node marked *s*, and a target node marked *t*. Every path from *s* to *t* in the graph can be represented by its identifying vector, that is a vector in {0, 1}^(*m*) in which the entries that are set to 1 correspond to edges of the path. The flow polytope of the graph is the convex hull of all such identifying vectors of the simple paths from *s* to *t*. This polytope is also exactly the set of all unit *s*–*t* flows in the graph if we assume that each edge has a unit flow capacity (a flow is represented here as a vector in ℝ^(*m*), in which each entry is the amount of flow through the corresponding edge).

Since the flow polytope is just the convex hull of *s*–*t* paths in the graph, minimizing a linear objective over it amounts to finding a minimum weight path given weights for the edges. For the shortest path problem, we have very efficient combinatorial optimization algorithms (namely, Dijkstra’s algorithm).

Thus, applying the CG algorithm to solve *any* convex optimization problem over the flow polytope will require only iterative shortest-path computations.

Ranking and permutations. A common way to represent a permutation or ordering is by a permutation matrix. Such are square matrices over {0, 1}^(*n*×*n*) that contain exactly one entry in each row and column.

Doubly stochastic matrices are square, real-valued matrices with nonnegative entries, in which the sum of entries of each row and each column amounts to 1. The polytope that defines all doubly stochastic matrices is called the Birkhoff–von Neumann (BVN) polytope. The BVN theorem states that this polytope is the convex hull of exactly all *n* × *n* permutation matrices.

Since a permutation matrix corresponds to a perfect matching in a fully connected bipartite graph, linear minimization over this polytope corresponds to finding a minimum weight perfect matching in a bipartite graph.

Consider a convex optimization problem over the BVN polytope. The CG algorithm will iteratively solve a linear optimization problem over the BVN polytope, thus iteratively solving a minimum weight perfect matching in a bipartite graph problem, which is a well-studied combinatorial optimization problem for which we know there are efficient algorithms. In contrast, other gradient-based methods will require projections, which are quadratic optimization problems over the BVN polytope.

Matroid polytopes. A matroid is the pair (*E, I*), where *E* is a set of elements and *I* is a set of subsets of *E* called the *independent sets*, which satisfy various interesting proprieties that resemble the concept of linear independence in vector spaces. Matroids have been studied extensively in combinatorial optimization, and a key example of a matroid is the graphical matroid, in which the set *E* is the set of edges of a given graph and the set *I* is the set of all subsets of *E* that are cycle-free. In this case, *I* contains all the spanning trees of the graph. A subset *S* ∈ *I* could be represented by its identifying vector, which lies in {0, 1}^(|*E*|) and also gives rise to the matroid polytope, which is just the convex hull of all identifying vectors of sets in *I*. It can be shown that some matroid polytopes are defined by exponentially many linear inequalities (exponential in |*E*|), which makes optimization over them difficult.

On the other hand, linear optimization over matroid polytopes is easy using a simple, greedy procedure that runs in nearly linear time. Thus, the CG method serves as an efficient algorithm to solve any convex optimization problem over matroids iteratively using only a simple, greedy procedure.

## 7.5 The Online Conditional Gradient Algorithm

In this section, we give a projection-free algorithm for OCO based on the CG method, which is projection-free and thus carries the computational advantages of the CG method to the online setting.

It is tempting to apply the CG method in a straightforward fashion to the online appearance of functions in the OCO setting, such as the online conditional gradient (OGD) algorithm in section 3.1 of chapter 3. However, it can be shown that an approach that takes into account only the last cost function is doomed to fail. The reason is that the CG method takes into account the *direction* of the gradient and is insensitive to its *magnitude*.

Instead, we apply the CG algorithm step to the aggregate sum of all previous cost functions with added Euclidean regularization. The result is given formally in [algorithm 7.3](#chapter_7.xhtml#algo7-3).

![](images/Algorithm7-3.png)

We can prove the following regret bound for this algorithm. While this regret bound is suboptimal in light of the previous upper bounds that we have seen, its suboptimality is compensated for by the algorithm’s lower computational cost.

**Theorem 7.2** *[Algorithm 7.3](#chapter_7.xhtml#algo7-3) with parameters ![](images/pg116-in-1.png), attains the following guarantee:*

![](images/pg116-1.png)

As a first step in analyzing [algorithm 7.3](#chapter_7.xhtml#algo7-3), consider the following points:

![](images/pg116-2.png)

These are exactly the iterates of the Regularized Follow The Leader (RFTL) algorithm from chapter 5; namely, [algorithm 5.1](#chapter_5.xhtml#algo5-1) with the regularization *R*(**x**) = ∥**x** −**x**1∥² applied to cost functions with the following shift:

![](images/pg117-1.png)

The reason is that in [algorithm 7.3](#chapter_7.xhtml#algo7-3), ∇[*t*] refers to ∇*f*[*t*](**x**[*t*]), whereas in the RFTL algorithm, we have ![](images/pg117-in-1.png). Notice that for any point **x** ∈𝒦, we have ![](images/pg117-in-2.png). Thus, according to theorem 5.1, we have

![](images/eq7-5.png)

Using the previous notation, denote by ![](images/pg117-in-3.png), and by *h*[*t*] = *h*[*t*](**x**[*t*]). The main lemma required to proceed is lemma 7.2, which relates the iterates **x**[*t*] to the optimal point according to the aggregate function *F*[*t*].

**Lemma 7.2** *The iterates* **x**[*t*] *of [algorithm 7.3](#chapter_7.xhtml#algo7-3) satisfy, for all t* ≥ 1,

![](images/pg117-2.png)

*Proof.* As the function *F*[*t*] is 1-smooth, applying oﬄine Frank-Wolfe analysis, and in particular equation ([7.2](#chapter_7.xhtml#eq7-2)) to the function *F*[*t*] we obtain

![](images/pg117-3.png)

In addition, by the definition of *F*[*t*] and *h*[*t*], we have

![](images/pg117-4.png)

Since *F*[*t*] is 1-strongly convex, we have

![](images/pg117-5.png)

Thus,

![](images/pg118-1.png)

Here, we used the following derivation, which holds by the choice of parameters ![](images/pg118-in-1.png)and ![](images/pg118-in-2.png): since *η, G, h*[*t*] are all nonnegative, we have

![](images/eq7-6.png)

We now claim that theorem 7.2 follows inductively. The base of the induction holds since, for *t* = 1, the definition of *F*[1] implies

![](images/pg118-2.png)

Assuming that the bound is true for *t*, we now show that it holds for *t* + 1 as well:

![](images/pg118-3.png)

as required. The last inequality follows by the definition of *σ*[*t*] (see the exercises at the end of this chapter).

☐

We proceed to use lemma 7.2 to prove theorem 7.2.

*Proof of theorem 7.2*. By definition, the function *F*[*t*] is 1-strongly convex. Thus, we have, for ![](images/pg118-in-3.png),

![](images/pg119-1.png)

Let ![](images/pg119-in-1.png), and notice that this satisfies the constraint of lemma 7.2, which requires ![](images/pg119-in-2.png). In addition, *η <* 1 if *T* is large enough. Hence,

![](images/eq7-7.png)

Putting everything together, we obtain

![](images/pg119-2.png)

We thus obtain

![](images/pg119-3.png)

## 7.6 Bibliographic Remarks

The matrix completion model has been extremely popular since its inception in the context of recommendation systems (Srebro 2004; Rennie and Srebro 2005; Salakhutdinov and Srebro 2010; Lee et al. 2010; Candes and Recht 2009; Shamir and Shalev-Shwartz 2011).

The CG algorithm was devised in the seminal paper by Frank and Wolfe (1956). Due to the applicability of the Frank-Wolfe algorithm to large-scale constrained problems, it has been a method of choice in recent machine learning applications (Hazan 2008; Jaggi and Sulovský 2010; Lacoste-Julien et al. 2013; Jaggi 2013; Dudík, Harchaoui, and Malick 2012; Harchaoui et al. 2012; Hazan and Kale 2012; Shalev-Shwartz, Gonen, and Shamir 2011; Bach, Lacoste-Julien, and Obozinski 2012; Tewari, Ravikumar, and Dhillon 2011; Garber and Hazan 2011, 2013; Bellet et al. 2014). In the context of matrix completion and recommendation systems, several faster variants of the Frank-Wolfe method have been proposed (Garber 2016, Allen-Zhu et al. 2017).

The OCG algorithm is due to Hazan and Kale (2012). An optimal regret algorithm, attaining the ![](images/pg120-in-1.png)bound, for the special case of polyhedral sets was devised by Garber and Hazan (2013).

Recent works consider accelerating projection-free optimization using variance reduction (Lan and Zhou 2016; Hazan and Luo 2016), and projection-free algorithms with stochastic gradient oracles (Mokhtari, Hassani, and Karbasi 2018; Chen et al. 2018; Xie et al. 2019).

For an analysis of the running time of the power and Lanczos methods for computing eigenvectors, see Kuczyński and Woźniakowski (1992). For modern algorithms for fast computation of the singular value decomposition, see Allen-Zhu and Li (2016) and Musco and Musco (2015).

## 7.7 Exercises

*   **1.**   Prove that if the singular values are smaller than or equal to 1, then the nuclear norm is a lower bound on the rank. That is, show that

![](images/pg120-1.png)

*   **2.**   Prove that the trace is related to the nuclear norm via

![](images/pg120-2.png)

*   **3.**   Show that maximizing a linear function over the spectahedron can be reduced to a maximal eigenvector computation.

**(a)** Consider the the following mathematical program for a symmetric *C* ∈ℝ^(*d*×*d*):

![](images/pg120-3.png)

Prove that it has the same solution as the following mathematical program:

![](images/pg120-4.png)

**(b)** Show how to use eigenvector computations to maximize a general asymmetric linear functions over the spectahedron.

*   **4.**   Prove that for positive integers *t >* 0, any *c* ∈ \[0, 1\] and ![](images/pg121-in-1.png)it holds that

![](images/pg121-1.png)

*   **5.**   Download the MovieLens data set from the web. Implement an online recommendation system based on the matrix completion model: that is, implement the OCG and OGD algorithms for matrix completion. Benchmark your results.

# 8 Games, Duality, and Regret

In this chapter, we tie the material covered thus far to some of the most intriguing concepts in optimization and game theory. We shall use the existence of online convex optimization (OCO) algorithms with sublinear regret to prove two fundamental properties: convex duality in mathematical optimization and von Neumann’s minimax theorem in game theory.

Historically, the theory of games was developed by John von Neumann in the early 1930s. In an entirely different scientific pursuit, the theory of linear programming (LP) was advanced by George Dantzig a decade later. Dantzig describes in his memoir a notable meeting between him and von Neumann at Princeton University in 1947. In this meeting, according to Dantzig, after describing the geometric and algebraic versions of linear programming, von Neumann essentially formulated and proved linear programming duality:

I don’t want you to think I am pulling all this out of my sleeve at the spur of the moment like a magician. I have just recently completed a book with Oscar Morgenstern on the theory of games. What I am doing is conjecturing that the two problems are equivalent. The theory that I am outlining for your problem is an analogue to the one we have developed for games.^([1](#chapter_8.xhtml#chapter8-1))

At that time, the topic of discussion was not the existence and uniqueness of equilibrium in zero-sum games, which is captured by the minimax theorem. Both concepts were originally captured and proved using very different mathematical techniques: the minimax theorem was originally proved using machinery from mathematical topology, whereas linear programming duality was shown using convexity and geometric tools.

More than half a century later, Yoav Freund and Robert Schapire tied both concepts, which by then were known to be strongly related, to regret minimization. We shall follow their lead in this chapter, introducing the relevant concepts and giving concise proofs using the machinery developed earlier in this book.

The chapter can be read and understood if you have basic familiarity with linear programming and little or no background in game theory. We define linear programming and zero-sum games succinctly, barely enough to prove the duality theorem and the minimax theorem. Readers are referred to the numerous wonderful texts available on linear programming and game theory for a much more thorough introduction and definitions.

## 8.1 Linear Programming and Duality

Linear programming is a widely successful and practical convex optimization framework. Its numerous successes include the Nobel Prize given for its application to economics. It is a special case of the convex optimization problem from chapter 2, in which 𝒦 is a polyhedron (i.e., an intersection of a finite set of half-spaces) and the objective function is a linear function. Thus, a linear program can be described as follows, where (*A* ∈ ℝ^(*n*×*m*)):

![](images/pg124-1.png)

This formulation can be transformed into several forms via basic manipulations. For example, any LP can be transformed into an equivalent LP with the variables taking only nonnegative values. This can be accomplished by writing every variable *x* as *x* = *x*^+ − *x*^−, with *x*^+*, x*^− ≥ 0. It can be verified that this transformation leaves another LP, whose variables are nonnegative, and contains at most twice as many variables (see the exercises at the end of this chapter).

We are now ready to define a central notion in LP and state the duality theorem in theorem 8.1.

**Theorem 8.1** *Given the following linear program:*

![](images/pg124-2.png)

*its dual program is given by*

![](images/pg124-3.png)

*and the objectives of both problems are either equal or unbounded.*

Instead of studying duality directly, we now proceed to define zero-sum games and an analogous concept to duality.

## 8.2 Zero-Sum Games and Equilibria

The theory of games is an established research field in economic theory. We give here brief definitions of the main concepts studied in this chapter.

Let us start with an example of a zero-sum game we all know: rock-paper-scissors. In this game, each of two players chooses a strategy: either rock, scissors, or paper. The winner is determined according to [table 8.1](#chapter_8.xhtml#tab8-1), where − 1 denotes that the row player wins, 1 denotes that the column player wins, and 0 denotes a draw.

[Table 8.1](#chapter_8.xhtml#rtab8-1)  
Example of rock-paper-scissors, a zero-sum game in matrix representation

 
| \- || Scissors || Paper || Rock |
| --- | --- | --- | --- |
| Rock || − 1 || 1 || 0 |
| --- | --- | --- | --- |
| Paper || 1 || 0 || − 1 |
| Scissors || 0 || − 1 || 1 |

The rock-paper-scissors game is a zero-sum game since one can think of the numbers as losses for the row player (with loss of − 1 means a victory, 1 a loss, and 0 a draw), in which case the column player receives a loss that is exactly the negation of the loss of the row player. Thus, the sum of the losses that both players suffer is zero in every outcome of the game.

Notice that we termed one player as the “row player,” and the other as the “column player,” corresponding to the matrix losses. Such a matrix representation is given far more generally in definition 8.1.

**Definition 8.1** *A two-player zero-sum-game in normal form is given by matrix A* ∈ \[−1, 1\]^(*n*×*m*)*. The loss for the row player playing strategy i* ∈ \[*n*\] *is equal to the negative loss (reward) of the column player playing strategy j* ∈ \[*m*\]*, and it is equal to A*[*ij*].

The fact that the losses were defined in the range \[−1, 1\] is arbitrary, as the concept of main importance that we define next is invariant to scaling and shifting by a constant.

A central concept in game theory is equilibrium. There are many notions of equilibria. In two-player zero-sum games, a pure equilibrium is a pair of strategies (*i, j*) ∈ \[*n*\] × \[*m*\] with the following property: given that the column player plays *j*, there is no strategy that dominates *i* (i.e., every other strategy *k* ∈ \[*n*\] gives a higher or an equal loss to the row player). Equilibrium also requires that a symmetric property for strategy *j* holds (i.e., it is not dominated by any other strategy, given that the row player plays *i*).

It can be shown that some games do not have a pure equilibrium as defined here, such as rock-paper-scissors. However, we can extend the notion of a strategy to a *mixed* strategy—a distribution over pure strategies. The loss of a mixed strategy is the expected loss according to the distribution over pure strategies. More formally, if the row player chooses **x** ∈ Δ[*n*] and the column player chooses **y** ∈ Δ[*m*], then the expected loss of the row player (which is the negative reward to the column player) is given by

![](images/pg126-1.png)

We can now generalize the notion of equilibrium to mixed strategies. Given a row strategy **x**, it is dominated by ![](images/pg126-in-1.png)with respect to a column strategy **y** if and only if

![](images/pg126-2.png)

We say that **x** is dominant with respect to **y** if and only if it is not dominated by any other mixed strategy. A pair (**x**, **y**) is an equilibrium for game *A* if and only if both **x** and **y** are dominant with respect to each other. It is a good exercise for the reader at this point to find an equilibrium for rock-paper-scissors.

At this point, some natural questions arise: Is there always an equilibrium in a given zero-sum game? Can it be computed efficiently? Are there natural repeated game-playing strategies that reach it?

As we shall see, the answer to all these questions is the same: yes. Let us rephrase these questions in a different way. Consider the optimal row strategy; that is, a mixed strategy **x**, such that the expected loss is minimized, no matter what the column player does. The optimal strategy for the row player would be

![](images/pg126-3.png)

Notice that we use the notation **x**^(*⋆*) ∈ rather than **x**^(*⋆*) =, since in general the set of strategies attaining the minimal loss over worst-case column strategies can contain more than a single strategy. Similarly, the optimal strategy for the column player would be

![](images/pg126-4.png)

Playing these strategies, no matter what the column player does, the row player would pay no more than

![](images/pg126-5.png)

and the column player would earn at least

![](images/pg127-1.png)

With these definitions, we can state von Neumann’s famous minimax theorem, as theorem 8.2.

**Theorem 8.2** *In any zero-sum game, it holds that λ*[*R*] = *λ*[*C*].

Theorem 8.2 answers all these questions in the affirmative. The value *λ*^(*⋆*) = *λ*[*C*] = *λ*[*R*] is called the **value of the game**, and its existence and uniqueness imply that any **x**^(*⋆*) and **y**^(*⋆*) in the appropriate optimality sets amount to an equilibrium.

Next, we proceed to give a constructive proof of von Neumann’s theorem, which also yields an efficient algorithm as well as natural repeated game playing strategies that converge to it.

### 8.2.1 Equivalence of von Neumann theorem and LP duality

The von Neumann theorem is equivalent to the duality theorem of linear programming in a very strong sense, and each implies the other via simple reduction. Thus, it suffices to prove only von Neumann’s theorem to prove the duality theorem.

The first part of this equivalence is shown by representing a zero-sum game as a primal-dual linear program instance, as we do now.

Observe that the definition of an optimal row strategy and value is equivalent to the following LP:

![](images/pg127-2.png)

To see that the optimum of this *LP* is attained at *λ*[*R*], note that the constraint **x**^⊤*Ae*[*i*] ≤ *λ *∀*i* ∈ \[*m*\] is equivalent to the constraint ∀**y** ∈ Δ[*m*]. **x**^⊤*A***y** ≤ *λ*, since

![](images/pg127-3.png)

The dual program to this LP is given by

![](images/pg127-4.png)

By similar arguments, the dual program precisely defines *λ*[*C*] and **y**^(*⋆*). The duality theorem asserts that *λ*[*R*] = *λ*[*C*] = *λ*^(*⋆*), which gives von Neumann’s theorem.

The action in the other direction (i.e., showing that von Neumann’s theorem implies LP duality) is slightly more involved. Basically, one can convert any LP to the format of a zero-sum game. Special care is needed to ensure that the original LP is indeed feasible, as zero-sum games are always feasible and linear programs do not have to be. The details are left as an exercise at the end of this chapter.

## 8.3 Proof of von Neumann Theorem

In this section, we give a proof of von Neumann’s theorem using OCO algorithms with sublinear regret.

The first part of the theorem, which is also known as *weak duality* in the LP context, is rather straightforward.

**Direction 1 (*λ***[***R***] **≥*λ***[***C***]**):**

*Proof.*

![](images/pg128-1.png)

The second and main direction, known as *strong duality* in the LP context, requires the technology of OCO that we have proved thus far.

**Direction 2 (*λ***[***R***] **≤*λ***[***C***]**):**

*Proof.* We consider a repeated game defined by the *n* × *m* matrix *A*. For *t* = 1, 2*, …, T*, the row player provides the mixed strategy **x**[*t*] ∈ Δ[*n*], the column player plays the mixed strategy **y**[*t*] ∈ Δ[*m*], and the loss of the row player, which equals the reward of the column player, equals ![](images/pg128-in-1.png).

The row player generates the mixed strategies **x**[*t*] according to an OCO algorithm—specifically using the exponentiated gradient algorithm ([algorithm 5.3](#chapter_5.xhtml#algo5-3) from chapter 5). The convex decision set is taken to be the *n*\-dimensional simplex 𝒦 = Δ[*n*] = {**x** ∈ ℝ^(*n*) | **x**(*i*) ≥ 0, ∑ **x**(*i*) = 1}. The loss function at time *t* is given by

![](images/pg128-2.png)

Spelling out the exponentiated gradient strategy for this particular instance, we have

![](images/pg129-1.png)

Then, by appropriate choice of *η* and corollary 5.1, we have

![](images/eq8-1.png)

The column player plays her best response to the row player’s strategy; that is,

![](images/eq8-2.png)

Denote the average mixed strategies by

![](images/pg129-2.png)

Then, we have

![](images/pg129-3.png)

Thus, ![](images/pg129-in-1.png). As *T →* ∞, we obtain part 2 of theorem 8.2.

☐

Notice that besides the basic definitions, the only tool used in the proof is the existence of sublinear regret algorithms for OCO. The fact that the regret bounds for OCO algorithms were defined without restricting the cost functions, as well as that they can be adversarially chosen, is crucial for the proof. Function *f*[*t*] is defined according to **y**[*t*], which is chosen based on **x**[*t*]. Thus, the cost functions constructed are adversarially chosen after decision **x**[*t*] was made by the row player.

## 8.4 Approximating Linear Programs

The technique in section 8.3 not only proves the minimax theorem, and thus linear programming duality, but also entails an efficient algorithm. Using the equivalence of zero-sum games and linear programs, this efficient algorithm can be used to solve linear programming. We now spell out the details of this algorithm in the context of zero-sum games.

Consider [algorithm 8.1](#chapter_8.xhtml#algo8-1).

![](images/Algorithm8-1.png)

Almost immediately, we obtain from the previous derivation lemma 8.1.

**Lemma 8.1** *The returned vector* **x** *of [algorithm 8.1](#chapter_8.xhtml#algo8-1) is a ![](images/pg130-in-1.png)\-approximate solution to the zero-sum game and linear program it describes.*

*Proof.* Following the exact same steps of the previous derivation, we have

![](images/pg130-1.png)

Therefore, for each *i* ∈ \[*m*\]:

![](images/pg131-1.png)

Thus, to obtain an *ε*\-approximate solution, one would need ![](images/pg131-in-1.png)iterations, each involving a simple update procedure.

## 8.5 Bibliographic Remarks

Game theory was founded in the late 1920s and early 1930s, and its cornerstone was laid in the classic text *Theory of Games and Economic Behavior* by von Neumann and Morgenstern (1944).

Linear programming is a fundamental mathematical optimization and modeling tool dating to the 1940s and Kantorovich (1940) and Dantzig (1951). Duality for linear programming was conceived by von Neumann, as described by Dantzig in an interview (Albers, Reid, and Dantzig 1986). For an in-depth treatment of the theory of linear programming, there are numerous comprehensive texts (e.g., Bertsimas and Tsitsiklis 1997; Matousek and Gärtner 2007).

The beautiful connection between low-regret algorithms and solving zero-sum games was discovered by Freund and Schapire (1999). More general connections of convergence of low-regret algorithms to equilibria in games were studied by Hart and Mas-Colell (2000), and more recently by Even-Dar, Mansour, and Nadav (2009) and Roughgarden (2015).

Approximation algorithms that arise via simple Lagrangian relaxation techniques were pioneered by Plotkin, Shmoys, and Tardos (1995). See also Arora, Hazan, and Kale (2012) and more recent developments that give rise to sublinear time algorithms (Clarkson, Hazan, and Woodruff 2012; Hazan, Koren, and Srebro 2011).

## 8.6 Exercises

*   **1.**   Prove that equilibrium strategy pairs in zero-sum games are not unique. That is, construct a zero-sum game for which there is multiple equilibria.
*   **2.**   Prove a special case of Sion’s generalization to the minimax theorem. Let *f* : *X* ×*Y* ↦ ℝ be a real-valued function on *X* ×*Y*, where *X, Y* are bounded, closed, and convex sets in Euclidean space ℝ^(*d*). Let *f* be convex-concave; that is,

**(a)** For every **y** ∈ *Y*, the function *f*(·, **y**): *X* ↦ ℝ is convex.

**(b)** For every **x** ∈ *X*, the function *f*(**x**, ·): *Y* ↦ ℝ is concave.

Prove that

![](images/pg131-2.png)

*   **3.**   Read Adler’s exposition on the equivalence of linear programming and zero-sum games (Adler 2013). Explain how to convert a linear program to a zero-sum game.
*   **4.**   Consider a repeated zero-sum game over matrix *A* in which both players change their mixed strategies according to a low-regret algorithm over the linear cost/reward functions of the game. Prove that the average value of the game approaches that of an equilibrium of the game given by *A*.
*   **5.**   ^(\*) Write a semidefinite program as a zero-sum game. Write an algorithm for approximating the solution of a semidefinite program using OCO algorithms, and sketch an analysis of its correctness and performance bound.

## Note

1.  [1](#chapter_8.xhtml#chapter8_1). Gass (2006)
    

# 9 Learning Theory, Generalization, and Online Convex Optimization

In our treatment of online convex optimization (OCO) so far, we have only implicitly discussed learning theory. The framework of OCO was shown to capture applications such as online learning classifiers, prediction with expert advice, portfolio selection, and matrix completion, all of which have a learning aspect. We have introduced the metric of regret and gave efficient algorithms to minimize regret in various settings. We have also argued that minimizing regret is a meaningful approach for many online prediction problems. However, the relation to other theories of learning has not been discussed thus far.

In this chapter, we draw a formal and strong connection between OCO and the theory of statistical learning. We begin by giving the basic definitions of statistical learning theory and proceed to describe how the applications studied in this book relate to this model. We then continue to show how regret minimization in the setting of OCO gives rise to computationally efficient statistical learning algorithms.

## 9.1 Statistical Learning Theory

The theory of statistical learning addresses the problem of learning a concept from examples. A concept is a mapping from domain 𝒳 to labels 𝒴, denoted as *C*: 𝒳 ↦ 𝒴.

As an example, consider the problem of optical character recognition (OCR). In this setting, domain 𝒳 can be all *n* × *n* bitmap images, label set 𝒴 is the Latin (or other) alphabet, and concept *C* maps a bitmap into the character depicted in the image.

Statistical theory models the problem of learning a concept by allowing access to labeled examples from the target distribution. The learning algorithm has access to pairs, or samples, from an unknown distribution:

![](images/pg133-1.png)

The goal is to be able to predict *y* as a function of **x** (i.e., to **learn** a hypothesis, or a mapping from 𝒳 to 𝒴, denoted as *h*: 𝒳 ↦ 𝒴, with small error with respect to distribution 𝒟). In the case that the label set is binary 𝒴 = {0, 1}, or discrete such as in OCR, the *generalization error* of an hypothesis *h* with respect to distribution 𝒟 is given by

![](images/pg134-1.png)

More generally, the goal is to learn a hypothesis that minimizes the loss according to a (usually convex) loss function *ℓ*: 𝒴×𝒴 ↦ ℝ. In this case, the generalization error of a hypothesis is defined as

![](images/pg134-2.png)

We henceforth consider a learning algorithm 𝒜 that observes a sample from distribution 𝒟, denoted as *S ∼* 𝒟^(*m*) for a sample of *m* examples, *S* = {(**x**[1]*, y*[1])*, …*, (**x**[*m*]*, y*[*m*])}, and produces a hypothesis 𝒜(*S*): 𝒳 ↦ 𝒴 based on this sample.

The goal of statistical learning can thus be summarized as follows:

*Given access to independent and identically distributed samples from an arbitrary distribution over* 𝒳 × 𝒴 *corresponding to a certain concept, learn hypothesis h*: 𝒳 ↦ 𝒴*, which has an arbitrarily small generalization error with respect to a given loss function.*

### 9.1.1 Overfitting

In the problem of OCR, the task is to recognize a character from a given image in bitmap format. To model it in the statistical learning setting, domain 𝒳 is the set of all *n* × *n* bitmap images for some integer *n*. Label set 𝒴 is the Latin alphabet, and concept *C* maps a bitmap to the character depicted in the image.

Consider the naive algorithm that fits the perfect hypothesis for a given sample, in this case a set of bitmaps. Namely, 𝒜(*S*) is the hypothesis that correctly maps any given bitmap input **x**[*i*] to its correct label *y*[*i*], and maps all unseen bitmaps to the character 1.

Clearly, this hypothesis does a very poor job of generalizing from experience; all images that have not been observed yet will be classified without regard to their properties, which surely is an erroneous classification most of the time. However, the training set, or the observed examples, are perfectly classified by this hypothesis!

This disturbing phenomenon is called *overfitting*, a central concern in machine learning. Before continuing to add the components in learning theory necessary to prevent overfitting, we turn our attention to a formal statement of when overfitting can appear.

### 9.1.2 No free lunch?

Theorem 9.1 shows that learning, as stated in the goal of statistical learning theory, is impossible without restricting the hypothesis class being considered. For simplicity, we consider the zero-one loss in this subsection.

**Theorem 9.1 (no free lunch theorem)** *Consider any domain* 𝒳 *of size* |𝒳| = 2*m >* 4*, and any algorithm* 𝒜 *that outputs a hypothesis* 𝒜(*S*) *given a sample S of size m. Then there exists a concept C*: 𝒳 *→* {0, 1} *and a distribution* 𝒟 *such that:*

*   *The generalization error of concept C is zero.*
*   *With a probability of at least ![](images/pg135-in-1.png), the error of the hypothesis generated by* 𝒜 *is at least ![](images/pg135-in-2.png).*

The proof of this theorem is based on the probabilistic method, a useful technique for showing the existence of combinatorial objects by showing that the probability that they exist in some distributional setting is bounded away from zero. In our setting, instead of explicitly constructing concept *C* with the required properties, we show that it exists by a probabilistic argument.

*Proof.* We show that for any learning algorithm, there is some learning task (i.e., a “hard” concept) that it will not learn well. Formally, take 𝒟 to be the uniform distribution over 𝒳. Our proof strategy will be to show the following inequality, where we take a uniform distribution over all concepts 𝒳 ↦ {0, 1}:

![](images/pg135-1.png)

After showing this step, we will use Markov’s inequality to conclude the theorem.

We proceed by using the linearity property of expectations, which allows us to swap the order of expectations, and then conditioning on the event that **x** ∈ *S*:

![](images/pg135-2.png)

All the terms in this expression, especially the first term, are nonnegative and at least 0. Also, note that since the domain size is 2*m* and the sample has size |*S*|≤ *m*, we have ![](images/pg136-in-1.png). Finally, observe that ![](images/pg136-in-2.png)for all **x** ∉ *S* since we are given that the “true” concept *C* is chosen uniformly at random over all possible concepts. Hence, we get

![](images/pg136-1.png)

which is the intermediate step we wanted to show. The random variable **E**[*S ∼* 𝒟^(*m*)]\[error(𝒜(*S*))\] attains values in the range \[0, 1\]. Since its expectation is at least ![](images/pg136-in-3.png), the event that it attains a value of at least ![](images/pg136-in-4.png)is nonempty. Thus, there exists a concept such that

![](images/pg136-2.png)

where, as assumed beforehand, 𝒟 is the uniform distribution over 𝒳.

We now conclude with Markov’s inequality: since the expectation over the error is at least ![](images/pg136-in-4.png), the probability over examples such that the error of 𝒜 over a random sample is at least ![](images/pg135-in-1.png)is at least

![](images/pg136-3.png)

### 9.1.3 Examples of learning problems

The conclusion of theorem 9.1 is that the space of possible concepts being considered in a learning problem needs to be restricted for any meaningful guarantee. Thus, learning theory concerns itself with concept classes, also called *hypothesis classes*, which are sets of possible hypotheses from which one would like to learn. We denote the concept (hypothesis) class as ℋ = {*h*: 𝒳 ↦ 𝒴}.

Common examples of learning problems that can be formalized in this model and the corresponding definitions include the following:

*   Optimal character recognition: In this problem, domain 𝒳 consists of all *n*×*n* bitmap images for some integer *n*, label set 𝒴 is a certain alphabet, and concept *C* maps a bitmap image into the character depicted in it. A common finite hypothesis class for this problem is the set of all decision trees with bounded depth.
*   Text classification: In this problem, the domain is a subset of Euclidean space (i.e., 𝒳 ⊆ ℝ^(*d*)). Each document is represented in its bag-of-words representation, and *d* is the size of the dictionary. The label set 𝒴 is binary, where 1 indicates a certain classification or topic (e.g., “Economics”), and zero all the others.  
        A commonly used hypothesis class for this problem is the set of all bounded-norm vectors in Euclidean space ![](images/pg137-in-1.png)such that *h*[**w**](**x**) = **w**^⊤**x**. The loss function is chosen to be the hinge loss (i.e., *ℓ*(*ŷ, y*) = max{0, 1 −*ŷy*}).
*   Recommendation systems: Recall the OCO formulation of this problem in section 7.2 of chapter 7. A statistical learning formulation for this problem is very similar. The domain is a direct sum of two sets 𝒳 = 𝒳[1]⊕𝒳[2]. Here **x**[1] ∈𝒳[1] is a certain media item, and every person is an item **x**[2] ∈𝒳[2]. The label set 𝒴 is binary, where 1 indicates a positive sentiment for the person to the particular media item, and zero a negative sentiment.  
        A commonly considered hypothesis class for this problem is the set of all mappings 𝒳[1]×𝒳[2] ↦ 𝒴 that, when viewed as a matrix in ℝ^(|𝒳[1]|×|𝒳[2]|), have bounded algebraic rank.

### 9.1.4 Defining generalization and learnability

We are now ready to give the fundamental definition of statistical learning theory, called *probably approximately correct (PAC)* learning, in definition 9.1.

**Definition 9.1** *A hypothesis class* ℋ *is PAC learnable with respect to loss function ℓ*: 𝒴×𝒴 ↦ ℝ *if the following holds: There exists algorithm* 𝒜 *that accepts S*[*T*] = {(**x**[*t*]*, y*[*t*])*, t* ∈ \[*T*\]} *and returns hypothesis* 𝒜(*S*[*T*]) ∈ ℋ*, which satisfies the following: for any ε, δ >* 0*, there exists a sufficiently large natural number T* = *T*(*ε, δ*)*, such that for any distribution* 𝒟 *over pairs* (**x***, y*) *and T samples from this distribution, it holds that with a probability of at least* 1 − *δ*,

![](images/pg137-1.png)

Note a few remarks regarding this definition:

*   Set *S*[*T*] of samples from the underlying distribution is called the *training set*. The error in definition 9.1 is called the *generalization error*, as it describes the overall error of the concept as generalized from the observed training set. The behavior of the number of samples *T* as a function of the parameters *ε, δ* and the concept class is called the *sample complexity* of ℋ.
*   The definition of PAC learning says nothing about computational efficiency. Computational learning theory usually requires, in addition to definition 9.1, that the algorithm 𝒜 is efficient (i.e., polynomial running time with respect to ![](images/pg137-in-2.png)and the representation of the hypothesis class). The representation size for a discrete set of concepts is taken to be the logarithm of the number of hypotheses in ℋ, denoted as log |ℋ|.
*   If the hypothesis 𝒜(*S*[*T*]) returned by the learning algorithm belongs to the hypothesis class ℋ, as in definition 9.1, we say that ℋ is **properly learnable**. More generally, 𝒜 may return a hypothesis from a different hypothesis class, in which case we say that ℋ is **improperly learnable**.

The fact that the learning algorithm can learn up to *any* desired accuracy *ε >* 0 is called the **realizability assumption**, and it greatly reduces the generality of the definition. It amounts to requiring that a hypothesis with near-zero error belongs to the hypothesis class. In many cases, concepts are only approximately learnable by a given hypothesis class, or inherent noise in the problem prohibits realizability (see the exercises at the end of this chapter).

This issue is addressed in the definition of a more general learning concept, called **agnostic learning**, given in definition 9.2.

**Definition 9.2 (agnostic PAC learnability)** *The hypothesis class* ℋ *is agnostically PAC learnable with respect to loss function ℓ*: 𝒴×𝒴 ↦ ℝ *if the following holds: There exists an algorithm* 𝒜 *that accepts S*[*T*] = {(**x**[*t*]*, y*[*t*])*, t* ∈ \[*T*\]} *and returns hypothesis* 𝒜(*S*[*T*])*, which satisfies the following: for any ε, δ >* 0*, there exists a sufficiently large natural number T* = *T*(*ε, δ*) *such that for any distribution* 𝒟 *over pairs* (**x***, y*) *and T samples from this distribution, it holds that with a probability of at least* 1 − *δ*,

![](images/pg138-1.png)

With definitions 9.1 and 9.2, we can state the fundamental theorem of statistical learning theory for finite hypothesis classes, as in theorem 9.2.

**Theorem 9.2 (PAC learnability of finite hypothesis classes)** *Every finite concept class* ℋ *is agnostically PAC learnable with a sample complexity that is* poly(*ε, δ,* log |ℋ|).

In the following sections of this chapter, we prove theorem 9.2, and in fact a more general statement that also holds for certain infinite hypothesis classes. The complete characterization of which infinite hypothesis classes are learnable is a deep and fundamental question, whose complete answer was given by Vapnik and Chervonenkis (see section 9.4). The question of which (finite or infinite) hypothesis classes are **efficiently** PAC learnable, especially in the improper sense, is still at the forefront of learning theory today.

## 9.2 Agnostic Learning Using Online Convex Optimization

In this section, we show how to use OCO for agnostic PAC learning. Following the paradigm of this book, we describe and analyze a reduction from agnostic learning to OCO. The reduction is formally described in [algorithm 9.1](#chapter_9.xhtml#algo9-1).

![](images/Algorithm9-1.png)

For this reduction, we assumed that the concept (hypothesis) class is a convex subset of Euclidean space. A similar reduction can be carried out for discrete hypothesis classes (see the exercises at the end of this chapter). In fact, the technique we explore here will work for any hypothesis set ℋ that admits a low-regret algorithm, and it can be generalized to infinite hypothesis classes that are known to be learnable.

Let *h*^(*⋆*) = arg min[*h*∈ℋ]{error(*h*)} be the hypothesis in class ℋ that minimizes the generalization error. Using the assumption that 𝒜 guarantees sublinear regret, our simple reduction implies PAC learning, as given in theorem 9.3.

**Theorem 9.3** *Let* 𝒜 *be an OCO algorithm whose regret after T iterations is guaranteed to be bounded by* Regret[*T*](𝒜)*. Then for any δ >* 0*, with a probability of at least* 1 − *δ, it holds that*

![](images/pg139-1.png)

*In particular, for ![](images/pg139-in-1.png), where T*[*ε*](𝒜) *is the integer T such that ![](images/pg139-in-2.png), we have*

![](images/pg139-2.png)

How general is theorem 9.3? In the previous chapters, we have described and analyzed OCO algorithms with regret guarantees that behave asymptotically as ![](images/pg139-in-3.png)or better. This translates to sample complexity of ![](images/pg139-in-4.png)(see the exercises at the end of this chapter), which is known to be tight for certain scenarios.

To prove this theorem, we need some tools from probability theory, such as the concentration inequalities that we survey next.

### 9.2.1 Reminder: Measure concentration and martingales

Let us briefly discuss the notion of a martingale in probability theory. For intuition, it is useful to recall the simple random walk. Let *X*[*i*] be a Rademacher random variable that takes the following values:

![](images/pg140-1.png)

A simple symmetric random walk is described by the sum of such random variables, depicted in [figure 9.1](#chapter_9.xhtml#fig9-1). Let ![](images/pg140-in-3.png)be the position after *T* steps of this random walk. The expectation and variance of this random variable are **E**\[*X*\] = 0, Var(*X*) = *T*.

![Figure 9.1 Symmetric random walk: 12 trials of 200 steps. The black dotted lines show the functions  and , respectively.](images/figure9-1.png)

[Figure 9.1](#chapter_9.xhtml#rfig9-1)  
Symmetric random walk: 12 trials of 200 steps. The black dotted lines show the functions ![](images/pg140-in-1.png)and ![](images/pg140-in-2.png), respectively.

The phenomenon of measure concentration addresses the probability of a random variable to attain values within range of its standard deviation. For the random variable *X*, this probability is much higher than one would expect using only the first and second moments. Using only the variance, it follows from Chebychev’s inequality that

![](images/pg141-1.png)

However, the event that |*X*| is centered around ![](images/pg141-in-1.png)is in fact much tighter and can be bounded by the Hoeffding-Chernoff lemma as follows:

![](images/eq9-1.png)

Thus, deviating by a constant from the standard deviation decreases the probability exponentially rather than polynomially. This well-studied phenomenon generalizes to sums of weakly dependent random variables and martingales, which are important for our application.

**Definition 9.3** *A sequence of random variables X*[1]*, X*[2]*, … is called a* martingale *if it satisfies*

![](images/pg141-2.png)

A similar concentration phenomenon to the random walk sequence occurs in martingales. This is captured in theorem 9.4, Azuma’s inequality.

**Theorem 9.4 (Azuma’s inequality)** ![](images/pg141-in-2.png)*be a martingale of T random variables that satisfy* |*X*[*i*] − *X*[*i*+1]|≤ 1*. Then*

![](images/pg141-3.png)

By symmetry, Azuma’s inequality implies

![](images/eq9-2.png)

### 9.2.2 Analysis of the reduction

We are ready to prove the performance guarantee for the reduction in [algorithm 9.1](#chapter_9.xhtml#algo9-1). Assume for simplicity that the loss function *ℓ* is bounded in the interval \[0, 1\]; that is,

![](images/pg141-4.png)

*Proof of theorem 9.3*. We start by defining a sequence of random variables that form a martingale. Let

![](images/pg141-5.png)

Let us verify that {*X*[*t*]} is indeed a bounded martingale. Notice that by definition of error(*h*), we have

 

![](images/pg142-1.png)

Thus, by the definition of *Z*[*t*],

![](images/pg142-2.png)

In addition, by our assumption that the loss is bounded, we have

![](images/eq9-3.png)

Therefore, we can apply Azuma’s inequality to the martingale {*X*[*t*]}, or rather its consequence (exercise ([9.2](#chapter_9.xhtml#eq9-2))), and get

![](images/pg142-3.png)

Plugging in the definition of *X*[*T*], dividing by *T* and using ![](images/pg142-in-1.png):

![](images/eq9-4.png)

A similar martingale can be defined for *h*^(*⋆*) rather than *h*[*t*], and repeating the analogous definitions and applying Azuma’s inequality, we get

![](images/eq9-5.png)

For notational convenience, let us use the following notation:

![](images/pg142-4.png)

Next, observe that

![](images/pg142-5.png)

where in the last inequality, we have used the definition *f*[*t*](*h*) = *ℓ*(*h*(**x**[*t*])*, y*[*t*]). From this expression and equations ([9.4](#chapter_9.xhtml#eq9-4)) and ([9.5](#chapter_9.xhtml#eq9-5)), we get

 

![](images/pg143-1.png)

By convexity, we have that ![](images/pg143-in-1.png). Thus, with a probability of at least 1 − *δ*,

![](images/pg143-2.png)

## 9.3 Learning and Compression

Thus far, we have considered finite and certain infinite hypothesis classes and shown that they are efficiently learnable if there exists an efficient regret minimization algorithm for a corresponding OCO setting.

In this section, we describe yet another property that is sufficient for PAC learnability: the ability to compress the training set. This property is particularly easy to state and use, especially for infinite hypothesis classes. It does not, however, imply efficient algorithms.

Intuitively, if a learning algorithm is capable to express an hypothesis using a small fraction of the training set, we will show that it generalizes well to unseen data. For simplicity, we consider only learning problems that satisfy a variant of the realizablility assumption (i.e., the compression scheme generates a hypothesis that attains zero error).

More formally, we define the notion of a compression scheme for a given learning problem as follows. Definition 9.4 and theorem 9.5 henceforth can be generalized to allow for loss functions, but for simplicity, consider only the zero-one loss function in this section.

**Definition 9.4 (Compression Scheme)** *A distribution* 𝒟 *over* 𝒳×𝒴 *admits a compression scheme of size k, realized by an algorithm* 𝒜*, if the following holds. For any T > k, let S*[*T*] = {(**x**[*t*]*, y*[*t*])*, t* ∈ \[*T*\]} *be a sample from* 𝒟*. There exists an S*′ ⊆ *S*[*T*], |*S*′| = *k, such that the algorithm* 𝒜 *accepts the set of k examples S*′*, and returns a hypothesis* 𝒜(*S*′) ∈{𝒳 ↦ 𝒴}*, which satsifies*

![](images/pg144-1.png)

The main conclusion of this section is that a learning problem that admits a compression scheme of size *k* is PAC learnable, with sample complexity proportional to *k*. This is formally given in theorem 9.5.

**Theorem 9.5** *Let* 𝒟 *be a data distribution that admits a compression scheme of size k realized by algorithm* 𝒜*. Then with a probability of at least* 1 − *δ over the choice of a training set* |*S*[*T*]| = *T, it holds that*

![](images/pg144-2.png)

*Proof.* Denote by error[*S*](*h*) the error of an hypothesis *h* on a sample *S* of independent and identically distributed examples, where the sample is taken independent of *h*. Since the examples are chosen independently, the probability that a hypothesis with error(*h*) *\> ε* has error[*S*](*h*) = 0 is at most (1 − *ε*)^(|*S*|). Denote the event of *h* satisfying these two conditions as *h* ∈ bad.

Consider a compression scheme for distribution 𝒟 of size *k*, realized by 𝒜, and a sample of size |*S*[*T*]| = *T* ≫ *k*. By definition of a compression scheme, the hypothesis returned by 𝒜 is based on *k* examples chosen from the set *S*′⊆ *S*[*T*]. We can bound the probability of the event that error[*S*[*T*]](𝒜(*S*′)) = 0 and error(𝒜(*S*′)) *\> ε*, denoted as 𝒜(*S*′) ∈ bad, as follows:

![](images/pg144-3.png)

For ![](images/pg144-in-1.png), we have that

![](images/pg144-4.png)

Since the compression scheme is guaranteed to return a hypothesis such that error[*S*[*T*]](𝒜(*S*′)) = 0, this implies that with a probability of at least 1 − *δ*, the hypothesis 𝒜(*S*′) has error(𝒜(*S*′)) ≤ *ε*.

☐

An important example of the use of compression schemes to bound the generalization error is for the hypothesis class of hyperplanes in ℝ^(*d*). It is left as an exercise to show that this hypothesis class admits a compression scheme of size *d*.

## 9.4 Bibliographic Remarks

The foundations of statistical and computational learning theory were put forth in the seminal works of Vapnik (1998) and Valiant (1984), respectively. There are numerous comprehensive texts on statistical and computational learning theory, such as Kearns and Vazirani (1994) and Shalev-Shwartz and Ben-David (2014).

Reductions from the online to the statistical (aka “batch”) setting were initiated by Littlestone (1989). Tighter and more general bounds were explored in a number of other sources (Cesa-Bianchi, Conconi, and Gentile 2006; Cesa-Bianchi and Gentile 2008; Zhang 2005). The probabilistic method is attributed to Paul Erdos; see also Alon and Spencer (1992).

The relationship between compression and PAC learning was studied in the seminal work of Nick Littlestone and M. K. Warmuth (1986). For more on the relationship and historical connections between statistical learning and compression. More recently, Moran and Yehudayoff (2016) and David, Moran, and Yehudayoff (2016) show that compression is equivalent to learnability in general supervised learning tasks and give quantitative bounds for this relationship.

The use of compression for proving generalization error bounds has been applied by Hanneke, Kontorovich, and Sadigurschi (2019) for regression and by Gottlieb, Kontorovich, and Nisnevitch (2018) and Kontorovich, Sabato, and Weiss (2017) for nearest neighbor classification. Another application is the recent work of Bousquet et al. (2020), which gives optimal generalization error bounds for support vector machines (SVMs) using compression.

## 9.5 Exercises

*   **1.**   Strengthen theorem 9.1 to show the following: For any *ε >* 0, there exists a finite domain 𝒳, such that for any learning algorithm 𝒜 which, given a sample *S*, produces hypothesis 𝒜(*S*), there exists distribution *D* and concept *C* : *X* ↦ {0, 1} such that

**(a)** error(*C*) = 0

**(b)** ![](images/pg145-in-1.png)

*   **2.**   Let 𝒜 be an agnostic learning algorithm for the finite hypothesis class ℋ : 𝒳 ↦ 𝒴 and the zero-one loss. Consider any concept *C* : *X* ↦ *Y* that is realized by ℋ, and the concept *Ĉ* that is obtained by replacing the label associated with each domain entry *x* ∈ *X* randomly with probability *ε*[0] > 0 every time *x* is sampled independently. That is,

![](images/pg145-1.png)

    Prove that 𝒜 can *ε*\-approximate the concept *Ĉ*; that is, show that 𝒜 can be used to produce hypothesis *h*[𝒜] that has error

![](images/pg146-1.png)

with a probability of at least 1 −*δ* for every *ε, δ* with a sample complexity polynomial in ![](images/pg146-in-1.png).

*   **3.**   Prove equation ([9.3](#chapter_9.xhtml#eq9-3)).
*   **4.**   (Sample complexity of SVM)  
    Consider the class of hypothesis given by hyperplanes in Euclidean space with the bounded norm

![](images/pg146-2.png)

Give an algorithm to PAC-learn this class with respect to the hinge loss function using the reduction of [algorithm 9.1](#chapter_9.xhtml#algo9-1). Analyze the resulting computational and sample complexity.

*   **5.**   Show how to use a modification of [algorithm 9.1](#chapter_9.xhtml#algo9-1) to learn a finite (nonconvex) hypothesis class efficiently; that is, without enumerating over all hypotheses. For this question, success probability of ![](images/pg146-in-2.png)is sufficient.  
    Hint: Instead of returning *h*, consider returning a hypothesis at random.
*   **6.**   Consider the hypothesis class of all axis-aligned rectangles in the plane. That is, consider all hypotheses parameterized by four real numbers, *a*[*x*]*, b*[*x*]*, a*[*y*]*, b*[*y*], such that

![](images/pg146-3.png)

Prove that this hypothesis class admits a compression scheme of size 4.

*   **7.**   ^(\*)Consider the hypothesis class of all hyperplanes in ℝ^(*d*). This class is parameterized by all vectors in the unit sphere, such that

![](images/pg146-4.png)

Prove that this class has a compression scheme of size *d*.

# 10 Learning in Changing Environments

In online convex optimization (OCO), the decision maker iteratively makes a decision without knowledge of the future, and she pays a cost based on her decision and the observed outcome. The algorithms that we have studied thus far are designed to perform nearly as well as the best single decision in hindsight. The performance metric we have advocated for, the average *regret* of the online player, approaches zero as the number of game iterations grows.

In scenarios in which the outcomes are sampled from some unknown distribution, regret minimization algorithms effectively “learn” the environment and approach the optimal strategy. This was formalized in chapter 9. However, if the underlying distribution changes, no such claim can be made.

Consider, for example, the online shortest path problem we have studied in chapter 1. It is a well-observed fact that traffic in networks exhibits changing cyclic patterns. A commuter may choose one path from home to work on a weekday, but a completely different path on the weekend when traffic patterns are different. Another example is the stock market: in a bull market, the investor may want to purchase technology stocks, but in a bear market, perhaps he would shift investments to gold or government bonds.

When the environment undergoes many changes, standard regret may not be the best measure of performance. In changing environments, the OCO algorithms we have studied thus far for strongly convex or exp-concave loss functions exhibit undesirable “static” behavior and converge to a fixed solution.

In this chapter, we introduce and study a generalization of the concept of regret called *adaptive* regret, to allow for a changing prediction strategy. We start with examining the notion of adapting in the problem of prediction from expert advice. We then continue to the more challenging setting of OCO, and derive efficient algorithms for minimizing this more refined regret metric.

## 10.1 A Simple Start: Dynamic Regret

Before giving the main performance metric studied in this chapter, we consider the first natural approach: measuring regret with regard to any sequence of decisions. Clearly, in general it is impossible to compete with an arbitrary changing benchmark. However, it is possible to give a refined analysis that shows what happens to the regret of an OCO algorithm versus changing decisions.

More precisely, define the *dynamic regret* of an OCO algorithm with respect to a sequence **u**[1]*, …*, **u**[*T*] as

![](images/pg148-1.png)

To analyze dynamic regret, some measure of the complexity of the sequence **u**[1]*, …*, **u**[*T*] is necessary. Let 𝒫(**u**[1]*, …*, **u**[*T*]) be the path length of the comparison sequence, defined as

![](images/pg148-2.png)

It is natural to expect the regret to scale with the path length, as indeed theorem 10.1 shows. For a fixed comparator **u**[*t*] = **x**^(*⋆*), the path length is 1, and thus theorem 10.1 recovers the ![](images/pg148-in-1.png)standard regret bound. For simplicity, we assume that the time horizon *T* is known ahead of time, and so is the path length of the comparator sequence, although these limitations can be removed (see section 10.6 ).

**Theorem 10.1** *Online gradient descent (OGD; [algorithm 3.1](#chapter_3.xhtml#algo3-1)) with stepsize ![](images/pg148-in-2.png)guarantees the following dynamic regret bound:*

![](images/pg148-3.png)

*Proof.* Using our notation, and following the steps of the proof of theorem 3.1,

![](images/pg148-4.png)

Thus,

![](images/pg148-5.png)

Using convexity and summing this inequality across time, we get

![](images/pg149-1.png)

The theorem now follows by choice of *η*.

☐

This simple modification to the analysis of OGD naturally extends to online mirror descent, as well as to other notions of path distance of the comparison sequence.

We now turn to another metric of performance that requires more advanced methods than we have seen thus far. This metric can be shown to be more general than dynamic regret, in the sense that the bounds that we prove also imply low dynamic regret.

## 10.2 The Notion of Adaptive Regret

The main performance metric considered in this chapter is designed to measure the performance of a decision maker in a changing environment. It is formally given in definition 10.1.

**Definition 10.1** *The adaptive regret of an OCO algorithm* 𝒜 *is defined as the maximum regret it achieves over any contiguous time interval. Formally,*

![](images/pg149-2.png)

As opposed to standard regret, the power of this definition stems from the fact that the comparator is allowed to change. In fact, it is allowed to change indefinitely with every interval of time.

For an algorithm with low adaptive regret, as opposed to standard regret, how would its performance guarantee differ in a changing environment? Consider the problem of portfolio selection, for which time can be divided into disjoint segments with different characteristics: bear market in the first *T/*2 iterations and bull market in the last *T/*2 iterations. A standard sublinear regret algorithm is only required to converge to the average of both optimal portfolios, clearly an undesirable outcome. However, an algorithm with sublinear adaptive regret bounds would *necessarily* converge to the optimal portfolio in both intervals.

Not only does this definition make intuitive sense, but it generalizes other natural notions. For example, consider an OCO setting that can be divided into *k* intervals, such that in each a different comparator is optimal. Then an adaptive regret guarantee of AdaptiveRegret[*T*] = *o*(*T*) would translate to overall regret of *k* × AdaptiveRegret[*T/k*] compared to the best *k*\-shifting comparator.^([1](#chapter_10.xhtml#chapter10-1))

### 10.2.1 Weakly and strongly adaptive algorithms

The OGD algorithm over general convex losses, with stepsizes ![](images/pg150-in-1.png), attains an adaptive regret guarantee of

![](images/pg150-1.png)

and this bound is tight. This is a simple consequence of the analysis we have already seen in chapter 3, and left as an exercise. Unfortunately, this guarantee is meaningless for intervals of length ![](images/pg150-in-2.png).

Recall that for strongly convex loss functions, the OGD algorithm with the optimal learning rate schedule attains *O*(log *T*) regret. However, it does *not* attain any nontrivial adaptive regret guarantee: its adaptive regret can be as large as Ω(*T*), and this is also left as an exercise.

An OCO algorithm 𝒜 is said to be *strongly adaptive* if its adaptive regret can be bounded by its regret over the interval up to logarithmic terms in *T*. That is,

![](images/pg150-2.png)

The natural question is: are there algorithms that attain the optimal regret guarantee, and simultaneously the optimal adaptive regret guarantee? As we shall see, the answer is affirmative in a strong sense: we shall describe and analyze algorithms that are optimal in both metrics. Furthermore, these algorithms can be implemented with small computational overhead over the nonadaptive methods we have already studied.

## 10.3 Tracking the Best Expert

Consider the fundamental problem studied in chapter 1, prediction from expert advice, but with a small twist. Instead of a static best expert, consider the setting in which different experts are the “best expert” in different time intervals. More precisely, consider the situation in which time \[*T*\] can be divided into *k* disjoint intervals such that each admits a different “locally best” expert. Can we learn to track the best expert?

This tracking problem was historically the first motivation to study adaptivity in online learning. Indeed, as shown by Herbster and Warmuth (1998), there is a natural algorithm that attains optimal regret bounds.

The Fixed Share algorithm, described in [algorithm 10.1](#chapter_10.xhtml#algo10-1), is a variant of the Hedge algorithm ([algorithm 1.1](#chapter_1.xhtml#algo1-1)). On top of the familiar multiplicative updates, it adds a uniform exploration term whose purpose is to avoid the weight of any expert from becoming too small. This provably allows a regret bound that tracks the best expert in any interval.

![](images/Algorithm10-1.png)

In line with the notation we have used throughout this book, we denote decisions in a convex decision set by **x** ∈𝒦. An expert *i* suggests decision ![](images/pg151-in-1.png)and suffers loss according to a convex loss function denoted as ![](images/pg151-in-2.png). The main performance guarantee for the Fixed Share algorithm is given in theorem 10.2.

**Theorem 10.2** *Given a sequence of α\-exp-concave loss functions, the Fixed Share algorithm with ![](images/pg151-in-3.png)guarantees*

![](images/pg151-1.png)

Notice that this is a different guarantee than adaptive regret, as per definition 10.1, because the decision set is discrete. However, it is a crucial component in the adaptive algorithms we will explore in section 10.4.

As a direct conclusion from this theorem, it can be shown (see the exercises at the end of this chapter) that if the best expert changes *k* times in a sequence of length *T*, the overall regret compared to the best expert in every interval is bounded by

![](images/pg152-1.png)

To prove this theorem, we start with lemma 10.1, which is a fine-grained analysis of the multiplicative weights properties.

**Lemma 10.1** *For all* 1 ≤ *i < N*,

![](images/pg152-2.png)

*Proof.* Using the *α*\-exp concavity of *f*[*t*],

![](images/pg152-3.png)

Taking the natural logarithm,

![](images/pg152-4.png)

Hence,

![](images/pg152-5.png)

The proof is completed observing that

![](images/pg152-6.png)

Theorem 10.2 can now be derived as a corollary.

*Proof of theorem 10.2*. By summing up over the interval *I* = \[*r, s*\], and using the lower bound on *p*^(*i*)[*t*], we have

![](images/pg153-1.png)

## 10.4 Efficient Adaptive Regret for Online Convex Optimization

The Fixed Share algorithm described in section 10.3 is extremely practical and efficient for discrete sets of experts. However, to exploit the full power of OCO, we require an efficient algorithm for continuous decision sets.

Consider, for example, the problems of online portfolio selection and online shortest paths: naively applying the Fixed Share algorithm is computationally inefficient. Instead, we seek an algorithm that takes advantage of the efficient representation of these problems in the language of convex programming.

We present such a method, called *Follow the Leading History (FLH)* , in [algorithm 10.2](#chapter_10.xhtml#algo10-2). The basic idea is to think of different OCO algorithms starting at different time points as experts, and apply a version of Fixed Share to these experts.

The main performance guarantee is given in theorem 10.3.

**Theorem 10.3** *Let* 𝒜 *be an OCO algorithm for α\-exp-concave loss function with* Regret[*T*](𝒜)*. Then,*

![](images/pg153-2.png)

*In particular, taking* 𝒜 *≡ ONS guarantees*

![](images/pg153-3.png)

Notice that FLH invokes 𝒜 at iteration *t* at most *T* times. Hence its running time is bounded by *T* times that of 𝒜. This can still be prohibitive as the number of iterations grows large. In section 10.5, we show how the ideas from this algorithm can give rise to an efficient adaptive algorithm with only *O*(log *T*) computational overhead and slightly worse regret bounds.

![](images/Algorithm10-2.png)

The analysis of FLH is very similar to that of Fixed Share, with the main subtleties coming from the fact that time horizon *T* is not assumed to be known ahead of time, and thus the number of experts varies with time.

Instead of giving the full analysis, which is deferred to the exercises, we give a simplified version of FLH that does assume a priori knowledge of *T*, and whose analysis can be directly reduced to that of theorem 10.2.

![](images/Algorithm10-3.png)

The simplified version of FLH is given in [algorithm 10.3](#chapter_10.xhtml#algo10-3), and it guarantees the adaptive regret bound in theorem 10.4.

**Theorem 10.4** *[Algorithm 10.3](#chapter_10.xhtml#algo10-3) guarantees*

![](images/pg154-1.png)

*Proof.* Applying theorem 10.2 to the experts defined in [algorithm 10.3](#chapter_10.xhtml#algo10-3), guarantees for every interval in time *I* = \[*r, s*\], and by choice of *N*, for every *i* ≤ *s*,

![](images/pg155-1.png)

In particular, consider the sequence of predictions given by the *r*th expert, for which we have

![](images/pg155-2.png)

The theorem now follows since this holds for every iterval *I* ⊆ \[*T*\].

☐

## 10.5 Computationally Efficient Methods

In section 10.4, we studied adaptive regret and introduced and analyzed an algorithm that attains near-optimal adaptive regret bounds. However, FLH suffers from a significant computational and memory overhead: it requires maintaining *O*(*T*) copies of an OCO algorithm. This computational overhead, which is proportional to the number of iterations, can be prohibitive in many applications. In this section, our goal is to implement the algorithmic template of FLH efficiently, using little space.

To be more precise, henceforth we will denote the running time per iteration of algorithm 𝒜 as *V*[*t*](𝒜). Recall that at time *t*, FLH stores all predictions {**x**[*t*]^(*i*) | *i* ∈ \[*t*\]} and has to compute weights for all of them. This requires a running time of at least *O*(*V*[*t*](𝒜) · *t*).

The FLH2 algorithm, described in [algorithm 10.4](#chapter_10.xhtml#algo10-4), significantly cuts this running time so that it is only logarithmic in the current time iteration parameter *t*. To achieve this, FLH2 applies a pruning method to cut the number of active online algorithms from *t* to *O*(log *t*). However, its adaptive regret guarantee is slightly worse, suffering a multiplicative factor of *O*(log *T*) compared to FLH in theorem 10.5.

Before giving the exact details of this pruning method, we state the performance guarantee for FLH2 in theorem 10.5.

**Theorem 10.5** *Given an OCO algorithm* 𝒜 *with regret* Regret[*T*](𝒜) *and running time V*[*T*](*A*)*, algorithm FLH*2 *guarantees: V*[*T*](*FLH*2) ≤ *V* [*T*](𝒜)log *T and*

![](images/pg155-3.png)

The main conclusion from this theorem is obtained by using FLH2, with 𝒜 being the ONS algorithm from chapter 4. This gives adaptive regret of ![](images/pg156-in-1.png)and a running time that is polynomial in natural parameters of the problem and polylogarithmic in the number of iterations.

![](images/Algorithm10-4.png)

Before diving into the analysis, we explain the main new ingredient. At the heart of this algorithm is a new method for incorporating history. We will show that it suffices to store only *O*(log *t*) experts at time *t* rather than all *t* experts as in FLH.

At time *t*, there is a working set *S*[*t*] of experts. In FLH, this set can be thought of to contain *E*¹*, …, E*^(*t*), where each *E*^(*i*) is the algorithm 𝒜 starting from iteration *i*. For the next round, a new expert *E*^(*t*+1) is added to get *S*[*t*+1]. The complexity and regret of FLH is directly related to the cardinality of these sets.

The key to decreasing the size of set *S*[*t*] is to also *remove* (or *prune*) some experts. Once an expert is removed, it is never used again. The algorithm will perform the multiplicative update and mixing steps (steps 5 and 7 in [algorithm 10.4](#chapter_10.xhtml#algo10-4)) only on the working set of experts.

The problem of maintaining the set of active experts can be thought of as the following abstract data-streaming problem. Suppose that the integers 1, 2*, …* are being “processed” in a streaming fashion. At time *t*, we have “read” the positive integers up to *t* and maintain a very small subset of them in *S*[*t*]. At time *t*, we create *S*[*t*+1] from *S*[*t*]: we are allowed to add to *S*[*t*] only the integer *t* + 1, and remove some integers already in *S*[*t*]. Our aim is to maintain a set *S*[*t*] that satisfies the following:

*   1.   For every positive *s* ≤ *t*, \[*s,* (*s* + *t*)/2\] ∩ *S*[*t*] ≠ ∅.
*   2.   For all *t*, |*S*[*t*]| = *O*(log *T*).
*   3.   For all *t*, *S*[*t*+1]∖*S*[*t*] = {*t* + 1}.

The first property of set *S*[*t*] intuitively means that *S*[*t*] is “well spread out” in a logarithmic scale. This is depicted in [figure 10.1](#chapter_10.xhtml#fig10-1). The second property ensures computational efficiency.

![Figure 10.1 Illustration of the working set St](images/figure10-1.png)

[Figure 10.1](#chapter_10.xhtml#rfig10-1)  
Illustration of the working set *S*[*t*]

Indeed, the procedure “Prune” maintains *S*[*t*] with these exact properties, and is detailed after we prove theorem 10.5.

We proceed to prove the main theorem starting with an analog of lemma 10.1.

**Proposition 10.1** *The following holds for all i* ∈ *S*[*t*]*:*

*   1.   ![](images/pg157-in-1.png)
*   2.   ![](images/pg157-in-2.png)

*Proof.* Using the *α*\-exp concavity of *f*[*t*],

![](images/pg157-1.png)

Taking the natural logarithm,

![](images/pg157-2.png)

Hence,

![](images/pg157-3.png)

To complete the proof, we note the following two facts, which are analogous to the ones used in lemma 10.1:

*   1.   For 1 ≤ *i < t*, ![](images/pg158-in-1.png)
*   2.   ![](images/pg158-in-2.png)

Proving these facts is left as an exercise at the end of the chapter.

☐

Using this, we can prove lemma 10.2.

**Lemma 10.2** *Consider some time interval I* = \[*r, s*\]*. Suppose that E*^(*r*) *was in the working set S*[*t*]*, for all t* ∈ *I. Then the regret incurred in I is at most ![](images/pg158-in-3.png).*

*Proof.* Consider the regret in *I* with respect to expert *E*^(*r*):

![](images/pg158-1.png)

Since ![](images/pg158-in-4.png). This implies that the regret with regard to expert *E*^(*r*) is bounded by *α*^(−1) log(*s*). Since *E*^(*r*) has regret bounded by Regret[*I*](𝒜) ≤ Regret[*T*](𝒜) over *I*, the conclusion follows.

☐

Given the properties of *S*[*t*], we can show that in any interval, the regret incurred is small.

**Lemma 10.3** *For any interval I, the regret incurred by the FLH2 algorithm is at most ![](images/pg158-in-5.png).*

*Proof.* Let |*I*|∈ \[2^(*q*), 2^(*q*+1)), and write for simplicity ![](images/pg158-in-6.png). We will prove the following by induction on *q*:

**Base case:** For *q* = 0, the regret is bounded by

![](images/pg158-2.png)

**Induction step:** By the properties of *S*[*t*], there is an expert *E*^(*i*) in the pool such that *i* ∈ \[*r,* (*r* + *s*)/2\]. This expert *E*^(*i*) entered the pool at time *i* and stayed throughout \[*i, s*\]. By lemma 10.2, the algorithm incurs regret at most ![](images/pg159-in-1.png)in \[*i, s*\].

The interval \[*r, i* − 1\] has a maximum size of ![](images/pg159-in-2.png), and by induction, the algorithm has a regret of at most *R*[*T*] · *q* on this interval. This gives a total of *R*[*T*](*q* + 1) regret on *I*.

☐

We can now prove theorem 10.5.

*Proof of theorem 10.5*. The running time of FLH2 is bounded by |*S*[*t*]|·*V*[*T*](𝒜). Since |*S*[*t*]| = *O*(log *t*), we can bound the running time by *O*(*V*[*T*](𝒜)log *T*). This fact, together with lemma 10.3, completes the proof.

☐

### 10.5.1 The pruning method

We now explain the pruning procedure used to maintain set *S*[*t*] ⊆{1, 2*, …, t*}.

We specify the *lifetime* of integer *i* - if *i* = *r*2^(*k*), where *r* is odd, then the lifetime of *i* is 2^(*k*+2) + 1. Suppose that the lifetime of *i* is *m*. Then, for any time *t* ∈ \[*i, i* + *m*\], integer *i* is *alive* at *t*. Set *S*[*t*] is simply the set of all integers that are alive at time *t*. Obviously, at time *t*, the only integer added to *S*[*t*] is *t*, which immediately proves Property (3). We now prove the other properties.

*Proof.* (Property (1)) We need to show that some integer in \[*s,* (*s* + *t*)/2\] is alive at time *t*. This is trivially true when *t* − *s <* 2, since *t* − 1*, t* ∈ *S*[*t*]. Let 2^(*ℓ*) be the largest power of 2 such that 2^(*ℓ*) ≤ (*t* − *s*)/2. There is some integer *x* ∈ \[*s,* (*s*+*t*)/2\] such that 2^(*ℓ*)|*x*. The lifetime of *x* is larger than 2^(*ℓ*)×2+1 *\> t*−*s*, so *x* is alive at *t*.

☐

*Proof.* (Property (2)) For each 0 ≤ *k* ≤ ⌊log *t*⌋, let us count the number of integers of the form *r*2^(*k*) (*r* odd) alive at *t*. The lifetime of these integers is 2^(*k*+2) + 1. The only integers alive lie in the interval \[*t* − 2^(*k*+2) − 1*, t*\]. Since all these integers of this form are separated by gaps of a minimum size of 2^(*k*), there are at most a constant number of such integers alive at *t*. In total, the size of *S*[*t*] is *O*(log *t*).

☐

## 10.6 Bibliographic Remarks

Dynamic regret bounds for OGD were proposed by Zinkevich (2003), and further studied by Besbes, Gur, and Zeevi (2015). Zhang et al. (2018) showed that adaptive regret bounds imply dynamic regret bounds.

The study of learning in changing environments can be traced to the seminal work of Herbster and Warmuth (1998) in the context of tracking for the problem of prediction from expert advice. Their technique was later extended to tracking of experts from a small pool (Bousquet and Warmuth 2003).

The problem of tracking a large set of experts efficiently was studied using the Fixed Share algorithm in Singer (1998), Kozat and Singer (2007), and György, Linder, and Lugosi (2005).

The deviation from Fixed Share to the FLH algorithm and the notion of adaptive regret were introduced by Hazan and Seshadhri (2007). These techniques were the subject of later study and extensions (Adamskiy et al. 2016; Zhang, Liu, and Zhou 2019). Daniely, Gonen, and Shalev-Shwartz (2015) studied adaptive regret for weakly convex loss functions and introduced the term “strongly adaptive,” which differentiates weakly and strongly convex settings. They note that FLH is a strongly adaptive algorithm.

The use of an exponential look-back for prediction has its roots in information theory (Willems and Krom 1997; Shamir and Merhav 2006). Efficient methods for streaming, which were used in this chapter to maintain a small set of active experts, were studied in the streaming algorithms literature (Gopalan et al. 2007).

Adaptive regret algorithms were motivated by applications involving changing environments, such as the portfolio selection problem. More recently, they were applied for time series prediction (Anava et al. 2013) and the control of dynamical systems (Gradu, Hazan, and Minasyan 2020).

## 10.7 Exercises

*   **1.**   Consider an OCO setting that can be divided into *k* intervals, such that in each one, a different comparator is optimal. Let 𝒜 be an algorithm that has an adaptive regret guarantee of AdaptiveRegret[*T*](𝒜) = *o*(*T*). Prove that the regret of 𝒜 versus the best *k*\-shifting comparator is bounded by *k* × AdaptiveRegret[*T*].
*   **2.**   Prove that the OGD algorithm for convex functions, with stepsizes ![](images/pg160-in-1.png), has an adaptive regret guarantee of ![](images/pg160-in-2.png), and that this is tight. Prove that the lazy version of OGD, from chapter 5, behaves differently and has an adaptive regret bound of Ω(*T*).
*   **3.**   Prove that the OGD algorithm with stepsize ![](images/pg160-in-3.png)for strongly convex functions, has adaptive regret which is lower bounded by Ω(*T*).
*   **4.**   Consider the problem of prediction from expert advice with *α*\-exp-concave loss functions, where the best expert switches *k* times. That is, time can be divided into *k* segments *I*[1]*, …, I*[*k*], such that the best expert in each segment is different.  
    Show that the regret of the Fixed Share algorithm versus the best *k*\-switching expert (a strategy that is allowed to change experts *k* times) is bounded by

![](images/pg160-1.png)

*   **5.**   Spell out a choice of *δ* parameter for the Fixed Share algorithm that does not require knowing the number of iterations *T* in advance. Prove an analog of theorem 10.2 with your choice of *δ*.
*   **6.**   Complete the proof of theorem 10.3.
*   **7.**   Prove the following facts, used in the proof of proposition 10.1:

**(a)** For 1 ≤ *i < t*, ![](images/pg161-in-1.png)

**(b)** ![](images/pg161-in-2.png)

*   **8.**   Implement meta-algorithms FLH and FLH2 with the ONS algorithm, and apply the resulting method on the portfolio selection problem. Benchmark your results and compare them to ONS and OGD.

## Note

1.  [1](#chapter_10.xhtml#chapter10_1). In certain cases, this can be *k* × AdaptiveRegret[*T*], depending on the particular algorithm used.
    

# 11 Boosting and Regret

In this chapter, we consider a fundamental methodology of machine learning called *boosting*. In the statistical learning setting, roughly speaking, this term refers to the process of taking a set of rough rules of thumb and combining them into a more accurate predictor.

Consider, for example, the problem of optical character recognition (OCR) in its simplest form: given a set of bitmap images depicting handwritten postal code digits, classify those that contain the digit 1 from those of 0.

Seemingly, discerning the two digits seems a difficult task that must take into account different styles of handwriting, which are inconsistent even for the same person, label errors in the training data, and other elements. However, an inaccurate rule of thumb is rather easy to devise: in the bottom-left area of [figure 11.1](#chapter_11.xhtml#fig11-1) we’d expect many more dark bits for 1s than if the image depicts a 0. This is, of course, a rather inaccurate classifier. It does not consider the alignment of the digit, thickness of the handwriting, and numerous other factors. Nevertheless, as a rule of thumb, we’d expect better-than-random performance and some correlation with the ground truth. However, the inaccuracy of the crude single-bit predictor is compensated for by its simplicity. It is not hard to implement a classifier based upon this rule of thumb, which is very efficient indeed. The natural and fundamental question that now arises is: can several such rules of thumb be combined into a single, accurate, and efficient classifier?

![Figure 11.1 Distinguishing zero versus 1 from a single pixel](images/figure11-1.png)

[Figure 11.1](#chapter_11.xhtml#rfig11-1)  
Distinguishing zero versus 1 from a single pixel

In the rest of this chapter, we shall formalize this question in the statistical learning theory framework. We then proceed to use the technology developed in this book thus far (namely, regret minimization algorithms for online convex optimization (OCO)) to answer this question in the affirmative. Our development will be somewhat nonstandard: we’ll describe a black-box reduction from regret minimization to boosting. This allows any of the OCO methods previously discussed in this text to be used as the main component of a boosting algorithm.

## 11.1 The Problem of Boosting

Throughout this chapter, we use the notation and definitions of chapter 9 on learning theory and focus on statistical learnability rather than agnostic learnability. More formally, we take the so-called realizability assumption, which states that for a learning problem over hypothesis class ℋ, there exists some *h*^(*⋆*) ∈ℋ such that its generalization error is zero, or error(*h*^(*⋆*)) = 0.

Using the notations of chapter 10, we can state definition 11.1, a seemingly weaker notion than statistical learnability.

**Definition 11.1 (Weak learnability)** *The concept class* ℋ: 𝒳 ↦ 𝒴 *is said to be γ\-weakly-learnable if the following holds: There exists an algorithm* 𝒜 *that accepts S*[*m*] = {(**x***, y*)} *and returns an hypothesis in* 𝒜(*S*[*m*]) ∈ ℋ *that satisfies the statement that for any δ >* 0*, there exists m* = *m*(*δ*) *that is large enough such that for any distribution* 𝒟 *over pairs* (**x***, y*)*, for y* = *h*^(*⋆*)(**x**)*, and m samples from this distribution, it holds that with probability* 1 − *δ*,

![](images/pg164-1.png)

This is an apparent weakening of the definition of statistical learnability described in chapter 9: the error is not required to approach zero. The standard case of statistical learning in the context of boosting is called *strong learnability*. An algorithm that achieves weak learning is referred to as a *weak learner*, and we can refer to a *strong learner* as an algorithm that attains statistical learning (i.e., it allows for a generalization error arbitrarily close to zero for a certain concept class).

The central question of boosting can now be formalized: are weak learning and strong learning equivalent? In other words, is there an (efficient?) procedure that has access to a weak oracle for a concept class and returns a strong learner for the class?

Miraculously, the answer to this question is affirmative, and it gives rise to one of the most effective paradigms in machine learning.

## 11.2 Boosting by Online Convex Optimization

In this section, we describe a *reduction* from OCO to boosting. The template is similar to the one used in chapter 9: using one of the numerous algorithms for OCO that we have explored in this book, as well as access to a weak learner, we create a procedure for strong learning.

### 11.2.1 Simplification of the setting

Our derivation focuses on simplicity rather than generality. As such, we make the following assumptions:

*   1.   We restrict ourselves to the classical setting of binary classification. Boosting to real-valued losses is also possible, but it is outside the scope of this discussion. Thus, we assume the loss function to be the zero-one loss; that is:

![](images/pg165-1.png)

*   2.   We assume that the concept class is realizable (i.e., there exists an *h*^(*⋆*) ∈ ℋ such that error(*h*^(*⋆*)) = 0). There are results on boosting in the agnostic learning setting, which are surveyed in section 11.3.
*   3.   We denote the distribution over examples 𝒳 ×𝒴 = {(*x, y*)}, where *y* = *h*^(*⋆*)(**x**), as a point in Δ[𝒳]. That is, a point **p** ∈ Δ[𝒳] is a nonnegative vector that integrates to 1 over all examples. For simplicity, we think of 𝒳, 𝒴 as finite, and therefore **p** ∈ Δ[*m*] belongs to the *m*\-dimensional simplex (i.e., is a discrete distribution over *m* elements).
*   4.   We henceforth denote the weak learning algorithm by 𝒲, and denote by 𝒲(**p***, δ*) a call to the weak learning algorithm over distribution **p** that satisfies

![](images/pg165-2.png)

With these assumptions and definitions, we are ready to prove the main result: a reduction from weak learning to strong learning using an OCO algorithm with a sublinear regret bound. Essentially, our task would be to find a hypothesis that attains zero error on a given sample.

### 11.2.2 Algorithm and analysis

Pseudocode for the boosting algorithm is given in [algorithm 11.1](#chapter_11.xhtml#algo11-1). This reduction accepts as input a *γ*\-weak learner and treats it as a black box, returning a function that we’ll prove is a strong learner.

The reduction also accepts as input an OCO algorithm denoted as 𝒜^(*OCO*). The underlying decision set for the OCO algorithm is the *m*\-dimensional simplex, where *m* is the sample size. Thus, its decisions are distributions over examples. The cost functions are linear, and assign a value of zero or 1, depending on whether the current hypothesis errs on a particular example. Hence, the cost at a certain iteration is the expected error of the current hypothesis (chosen by the weak learner) over the distribution chosen by the low-regret algorithm.

![](images/Algorithm11-1.png)

It is important to note that the final hypothesis *h* that the algorithm outputs does not necessarily belong to ℋ, the initial hypothesis class we started with.

**Theorem 11.1** *[Algorithm 11.1](#chapter_11.xhtml#algo11-1) returns a hypothesis* *h* *such that with probability at least* 1 − *δ*,

![](images/pg166-1.png)

*Proof.* Given *h* ∈ℋ, we denote its empirical error on sample *S*, weighted by the distribution **p** ∈ *δ*[*m*], by

![](images/pg167-1.png)

Notice that by definition of **r**[*t*] we have **r**[*t*]^⊤**p**[*t*] = 1 − error[*S,* **p**[*t*]](*h*[*t*]). Since *h*[*t*] is the output of a *γ*\-weak-learner on the distribution **p**[*t*], we have for all *t* ∈ \[*T*\],

![](images/pg167-2.png)

This applies for each *t* separately, and by the union bound, we have

![](images/pg167-3.png)

Denote by *S*[*ϕ*] ⊆ *S* be the set of all misclassified examples by *h*. Let **p**^(\*) be the uniform distribution over *S*[*ϕ*]:

![](images/pg167-4.png)

Combining the previous two observations, we have, with a probability of at least 1 − *δ*, that

![](images/pg167-5.png)

![](images/pg168-1.png)

This is a contradiction. We conclude that a distribution **p**^(\*) cannot exist, and thus all examples in *S* are classified correctly.

☐

### 11.2.3 AdaBoost

A special case of the template reduction that we have described is obtained when the OCO algorithm is taken to be the multiplicative updates method that has been explored in this book.

Corollary 5.1 gives a bound of ![](images/pg168-in-1.png)on the regret of the exponentiated gradient algorithm in our context. This bounds *T* in [algorithm 11.1](#chapter_11.xhtml#algo11-1) by ![](images/pg168-in-2.png).

Closely related is the AdaBoost algorithm, which is one of the most useful and successful algorithms in machine learning at large (see bibliography). Unlike the boosting algorithm that we have analyzed, AdaBoost doesn’t have to know in advance the parameter *γ* of the weak learners. Pseudocode for the AdaBoost algorithm is given in [algorithm 11.2](#chapter_11.xhtml#algo11-2).

![](images/Algorithm11-2.png)

### 11.2.4 Completing the picture

In our discussion so far, we have focused only on the empirical error over a sample. To show generalization and complete the Boosting theorem, one must show that zero empirical error on a large enough sample implies an *ε* generalization error on the underlying distribution.

Notice that the hypothesis returned by the Boosting algorithms does not belong to the original concept class. This presents a challenge for certain methods of proving generalization error bounds that are based on measure concentration over a fixed hypothesis class.

Both issues are resolved using the implication that compression implies generalization, as given in theorem 9.5. We sketch the argument next, and the precise derivation is left as an exercise.

Roughly speaking, boosting [algorithm 11.1](#chapter_11.xhtml#algo11-1) runs on *m* examples for ![](images/pg169-in-1.png)rounds, returns a final hypothesis *h* that is the majority vote of *T* hypothesis, and classifies correctly all *m* examples of the training set.

Suppose that the weak learning algorithm has a sample complexity of size *k*(*γ, δ*): given *k* = *k*(*γ, δ*) examples, it returns a hypothesis with a maximum generalization error of ![](images/pg146-in-2.png)− *γ*, with probability of at least 1 − *δ*. Further, suppose that the original training set of *m* examples was sampled from distribution 𝒟.

Since *h* classifies the entire training set correctly, it follows that distribution 𝒟 has a compression scheme of size

![](images/pg169-1.png)

Therefore, using theorem 9.5, we have that

![](images/pg169-2.png)

Now one can obtain an arbitrary small generalization error by choosing *m* as a function of *k, δ, γ*. Notice that this argument makes an assumption only about the sample complexity of the weak learning algorithm rather than hypothesis class ℋ.

## 11.3 Bibliographic Remarks

The theoretical question of Boosting was posed and addressed by Schapire (1990) and Freund (1995). The AdaBoost algorithm was proposed in the seminal paper by Freund and Schapire (1997), which also contains the essential ingredients for the reduction from general low-regret algorithms to boosting.

Boosting has had significant impact on theoretical and practical data analysis as described by the statistician Leo Breiman (Olshen 2001). For a much more comprehensive survey of Boosting theory and applications, see Schapire and Freund (2012).

The theory for agnostic boosting is more recent, and several definitions and settings exist (Kalai, Mansour, and Verbin 2008; Kalai and Servedio 2005; Kanade and Kalai 2009; Feldman 2009; Ben-David, Long, and Mansour 2001). The most general of these is perhaps by Kanade and Kalai (2009). A unified framework for realizable and agnostic boosting, for both the statistical and online settings, is given by Brukhim et al. (2020).

The theory of boosting has been extended to real-valued learning via the theory of gradient boosting (Friedman 2002). More recently, it was extended to online learning (Leistner et al. 2009; Chen, Lin, and Lu 2012, 2014; Beygelzimer, Kale, and Luo 2015; Beygelzimer et al. 2015; Agarwal et al. 2019; Jung, Goetz, and Tewari 2017; Jung and Tewari 2018; Brukhim and Hazan 2020).

## 11.4 Exercises

*   **1.**   Describe a boosting algorithm based on the online gradient descent (OGD) algorithm. Give a bound on its running time.
*   **2.**   Download the MNIST data set from the web. Implement weak learners to differentiate a pair of digits of your choice according to a single bit. Implement AdaBoost and apply it to your weak learners. Summarize your results and conclusions.
*   **3.**   ^(\*) Consider the problem of *agnostic boosting*, in which the existence of a zero-error hypothesis is not assumed.

**(a)** Write an alternative definition of a weak learning algorithm for the agnostic setting.

**(b)** Write down a reasonable goal for a boosting algorithm.

**(c)** Write down an analog of theorem 11.1 for agnostic boosting (without proof).

*   **4.**   Compute the number of samples required to achieve a generalization error of *ε* using [algorithm 11.1](#chapter_11.xhtml#algo11-1) and a weak learning algorithm with the sample complexity bound *k*(*γ, δ*).

# 12 Online Boosting

This book considers online convex optimization (OCO) and learning, and it is a natural question to ask whether the technique of boosting has a counterpart in the online world? What is a “weak learner” in OCO, and how can one strengthen it? This is the subject of this chapter, and we shall see that boosting can be extremely powerful and useful in the OCO setting.

## 12.1 Motivation: Learning from a Huge Set of Experts

Recall the classical problem of prediction from expert advice from chapter 1. A learner iteratively makes decisions and gets a loss according to an arbitrarily chosen loss function. For its decision making, the learner is assisted by a pool of experts. Classical algorithms such as the Hedge algorithm ([algorithm 1.1](#chapter_1.xhtml#algo1-1)), guarantees a regret bound of ![](images/pg171-in-1.png), where *N* is the number of experts, and this is known to be tight.

However, in many problems of interest, the class of experts is too large to manipulate efficiently. This is particularly evident in contextual learning, as formally defined in this discussion, where the experts are *policies*—functions mapping contexts to action. In such instances, even if a regret bound of ![](images/pg171-in-2.png)is meaningful, the algorithms achieving this bound are computationally inefficient; their running time is linear in *N*. This linear dependence is unacceptable in many cases: the effective number of policies mapping context to action is exponential in a number of contexts.

The boosting approach to addressing this computational intractability is motivated by the observation that it is often possible to design simple rules of thumb that perform slightly better than random guesses. Analogous to the weak learning oracles from chapter 11, we propose that the learner has access to an online weak learner, a computationally cheap mechanism capable of guaranteeing multiplicatively approximate regret against a base hypotheses class.

In the rest of this chapter, we describe efficient algorithms that, when provided with weak learners, compete with the convex hull of the base hypotheses class with near-optimal regret.

### 12.1.1 Example: Boosting online binary classification

As a more precise example of the motivation we just surveyed, we formalize online boosting for binary prediction from expert advice. At iteration *t*, a set of experts denoted *h* ∈ℋ, observe a context **a**[*t*], and predict a binary outcome *h*(**a**[*t*]) ∈{−1, 1}. The loss of each expert is taken to be the binary loss, − *h*(**a**[*t*]) · *y*[*t*], for a true label *y*[*t*] ∈{−1, 1}. The Hedge algorithm from chapter 1 applies to this problem, and it guarantees a regret of ![](images/pg172-in-1.png)for a finite ℋ. However, the case in which ℋ is extremely large, maintaining the weights is prohibitive computationally.

A weak online learner 𝒲 in this setting is an algorithm that is guaranteed to attain at most a factor *γ* loss from the best expert in class, for some *γ* ∈ \[0, 1\], up to an additive sublinear regret term. Formally, for any sequence of contexts and labels {**a**[*t*]*, y*[*t*]},

![](images/pg172-1.png)

The online boosting question can now be phrased as follows: given access to a weak online learning algorithm 𝒲, can we design an efficient online algorithm 𝒜 that guarantees vanishing regret over ℋ? More formally, let

![](images/pg172-2.png)

Can we design an algorithm 𝒜 that has ![](images/pg172-in-2.png), without having explicit access to ℋ? As we will see, the answer to this question is affirmative in a strong sense: boosting does have an online analog that is a powerful technique in online learning. In section 12.2, we describe a more powerful notion of boosting that applies to the full generality of OCO. This in turn implies an affirmative answer to this question for online binary classification.

### 12.1.2 Example: Personalized article placement

In the problem of matching articles to visitors of a web page on the Internet, a number of articles are available to be placed on a given web page for a particular visitor. The goal of the decision maker (in this case the person placing the article) is to find the most relevant article that will maximize the probability of a visitor click.

It is usually the case that context is available, in the form of the user profile, preferences, surfing history, and other elements. This context is invaluable in terms of placing the most relevant article. Thus, the decision of the article-placer is to choose from a *policy*: a mapping from context to article.

The space of policies is significantly larger than the space of articles and the space of contexts: its size is the power of articles to the cardinality of contexts. This motivates the use of online learning algorithms whose computational complexity is independent of the number of experts.

The natural formulation of this problem is not binary prediction, but rather multiclass prediction. Formulating this problem in the language of OCO is left as an exercise.

## 12.2 The Contextual Learning Model

Boosting in the context of OCO is most useful for the contextual learning problem which we now describe.

Let us consider the familiar OCO setting over a general convex decision set 𝒦⊆ ℝ^(*d*), and adversarially chosen convex loss functions *f*[1]*, …, f*[*t*]: 𝒦 ↦ ℝ. Boosting is particularly important in settings that we have a very large number of possible experts that makes running one of the algorithms we have considered thus far infeasible. Concretely, suppose that we have access to a hypothesis class ℋ⊆{**a**} ↦ 𝒦, which given a sequence of contexts **a**[1]*, …*, **a**[*t*], produces a new point *h*(**a**[*t*+1]) ∈𝒦.

We have studied numerous methods that are capable of minimizing regret for this setting in this book, all of which assumed that we have access to set ℋ and depend on its diameter in some way.

To avoid this dependence, we consider an alternative access model to ℋ. A weak learner for the OCO setting is described in definition 12.1.

**Definition 12.1** *An online learning algorithm* 𝒲 *is a γ\-****weak OCO learner (WOCL)*** *for* ℋ *and γ* ∈ (0, 1)*, if for any sequence of contexts* {**a**[*t*]} *and* **linear** *loss functions f*[1]*, …, f*[*T*]*, for which* max[**x**∈𝒦]*f*[*t*](**x**) − min[**y**∈𝒦]*f*[*t*](**y**) ≤ 1,^([1](#chapter_12.xhtml#chapter12-1)) *we have*

![](images/eq12-1.png)

*where* **x** = ∫ [**x**∈𝒦]**x** *is the center of mass of* 𝒦.

This definition differs in two aspects from the types of regret minimization guarantees that we have seen thus far. First, the algorithm competes with a *γ*\-multiple of the best comparator in hindsight and is “weak” in this precise manner.

Second, a multiplicative guarantee is not invariant for a constant shift. This is the reason for the existence of an additional component, ![](images/pg174-in-1.png), in the regret bound. This can be thought of as the cost of a random or naive predictor. A weak learner must, at the very least, perform better than this naive and nonanticipating predictor!

Therefore, it is convenient to assume that the loss functions are shifted such that ![](images/pg174-in-2.png). Under this assumption, we can rephrase *γ*\-WOCL as

![](images/eq12-2.png)

## 12.3 The Extension Operator

The main difficulty is coping with the approximate guarantee that the weak OCO learner (WOCL) provides. Therefore, the algorithm we describe henceforth scales the predictions returned by the weak learner by a factor of ![](images/pg174-in-3.png). This means that the scaled decisions do not belong to the original decision set anymore and need to be projected back.

Here lies the main challenge. First, we assume that the loss functions *f* ∈ℱ are defined over all of ℝ^(*d*) to enable valid decisions outside of 𝒦. Second, we need to be able to project onto 𝒦 without increasing the cost. It can be seen that some natural families of functions (i.e., linear functions), do not admit any such projection. To remedy this situation, we define the extension operator of a function over a convex domain 𝒦 as follows.

First, denote the Euclidean distance function to set 𝒦 as (see also section 13.2 in chapter 13),

![](images/pg174-1.png)

**Definition 12.2 (**(𝒦*, κ, δ*)**\-extension)** *The extension operator over* 𝒦⊆ ℝ^(*d*) *is defined as*

![](images/pg174-2.png)

*where the smoothing operator S*[*δ*] *was defined as per lemma 2.4*.

The important takeaway from these operators is lemma 12.1, whose importance is crucial in the OCO boosting algorithm ([algorithm 12.1](#chapter_12.xhtml#algo12-1)), as it projects infeasible points that are obtained from the weak learners to the feasible domain.

**Lemma 12.1** *The* (𝒦*, κ, δ*)*\-extension of a function* ![](images/pg175-in-1.png)*satisfies the following:*

*   1.   *For every point* **x** ∈𝒦*, we have* ![](images/pg175-in-2.png).
*   2.   *The projection of a point, whose gradient is bounded by G, onto* 𝒦 *improves the* (𝒦*, κ, δ*)*\-extension function, for κ* = *G, value up to a small term:*

![](images/pg175-1.png)

*Proof.* Since **Dist**(**x**, 𝒦) = 0 for all *x* ∈𝒦, this follows immediately from lemma 2.4.

*   2.   Denote **x**[*π*] = ∏ [𝒦](**x**) for brevity. Then

![](images/pg175-2.png)

## 12.4 The Online Boosting Method

The online boosting algorithm described in this section is closely related to the online Frank-Wolfe algorithm from chapter 7. Not only does it boost WOCL to strong learning, but it gives an even stronger guarantee: low regret over the convex hull of the hypothesis class.

[Algorithm 12.1](#chapter_12.xhtml#algo12-1) efficiently converts a weak online learning algorithm to an OCO algorithm with vanishing regret in a black-box manner. The idea is to apply the weak learning algorithm to linear functions that are gradients of the loss. The algorithm then recursively applies another weak learner to the gradients of the residual loss, and so forth.

However, the Frank-Wolfe algorithm is not applied directly to the loss functions, but rather to a proxy loss defined using the extension operation in 12.2. Importantly, [algorithm 12.1](#chapter_12.xhtml#algo12-1) has a running time that is independent of |ℋ|.

Notice that if *γ* = 1, the algorithm still gives a significant advantage compared to the weak learner: the regret guarantee is versus the convex hull of ℋ, as compared to the best single hypothesis.

 ![](images/Algorithm12-1.png)

**Theorem 12.1 (Main)** *The predictions* **x**[*t*] *generated by [algorithm 12.1](#chapter_12.xhtml#algo12-1) with ![](images/pg176-in-1.png)satisfy*

![](images/pg176-1.png)

**Remark 1** It is possible to obtain tighter bounds by a factor of the dimension, as well as other constant terms, using a more sophisticated smoothing operator. References for these tighter results are given in section 12.5.

**Remark 2** The regret bound of theorem 12.1 is nearly as good as we could hope for. The first term approaches zero as the number of weak learners *N* grows. The second term is sublinear as the regret of the weak learner. It is scaled by a factor of ![](images/pg176-in-2.png), which we can expect due to the approximate guarantee of the weak learner.

Before proving the theorem, let us define some notations. The algorithm defines the extension of the loss functions as

![](images/pg176-2.png)

We apply the setting of *κ* = *G*, as required by lemma 12.1, and by lemma 2.4, ![](images/pg176-in-3.png)is ![](images/pg176-in-4.png)\-smooth. Also, denote by ![](images/pg176-in-5.png)the convex hull of set ℋ, and let

 

![](images/pg177-1.png)

be the best hypothesis in the convex hull of ℋ in hindsight (i.e., the best convex combination of hypothesis from ℋ). Notice that since the loss functions are generally convex and nonlinear, this convex combination is not necessarily a singleton. We define **x**[*t*]^(*⋆*) = *h*^(*⋆*)(**a**[*t*]) as the decisions of this hypothesis.

The main crux of the proof is given by lemma 12.2.

**Lemma 12.2** *For smoothed loss functions* ![](images/pg177-in-2.png)*that are β\-smooth and Ĝ Lipschitz, it holds that*

![](images/pg177-2.png)

*Proof.* Define for all *i* = 0, 1, 2*, …, N*,

![](images/pg177-3.png)

Recall that ![](images/pg177-in-2.png)is *β* smooth by this assumption. Therefore:

![](images/pg177-4.png)

By using the definition and linearity of *f*[*t*]^(*i*), we have

![](images/pg177-5.png)

Now, note the following equivalent restatement of the WOCL guarantee, which again utilizes the linearity of *f*[*t*]^(*i*) to conclude that linear loss on a convex combination of a set is equal to the same convex combination of the linear loss applied to individual elements:

![](images/pg178-1.png)

Using this expression and assuming that *h*^(*⋆*) ∈**CH**(ℋ), we have

![](images/pg178-2.png)

where the last inequality uses the convexity of ![](images/pg178-in-1.png), and we denote ![](images/pg178-in-2.png). We thus have the recurrence

![](images/pg178-3.png)

Denoting ![](images/pg178-in-3.png), we are left with

![](images/pg178-4.png)

This is a recursive relation that can be simplified by applying lemma 7.1 from chapter 7. By doing so, we obtain that ![](images/pg178-in-4.png).

☐

We are now ready to prove the main guarantee of [algorithm 12.1](#chapter_12.xhtml#algo12-1).

*Proof of theorem 12.1*. Using both parts of lemma 12.1 in succession, we have

![](images/pg178-5.png)

Next, recall from lemma 2.4 that ![](images/pg178-in-5.png)is ![](images/pg178-in-6.png)\-smooth. By applying lemma 12.2 and optimizing *δ*, we have

![](images/pg179-1.png)

where the last inequality is only to obtain a nicer expression.

It only remains to bound *Ĝ*, and we claim that *Ĝ* ≤ 2*G*. To see this, notice that the function **Dist**(**x**, 𝒦) is 1-Lipschitz, since

![](images/pg179-2.png)

Thus, by the definition of the extension operator and function ![](images/pg179-in-1.png), we have that ![](images/pg179-in-2.png).

☐

## 12.5 Bibliographic Remarks

The theory of boosting, which was surveyed in chapter 11, originally applied to binary classification problems. Boosting for real-valued regression was studied in the theory of gradient boosting by Friedman (2002).

Online boosting, for both the classification and regression settings, was studied much later (Leistner et al. 2009; Chen, Lin, and Lu 2012, 2014; Beygelzimer, Kale, and Luo 2015; Beygelzimer et al. 2015; Agarwal et al. 2019; Jung, Goetz, and Tewari 2017; Jung and Tewari 2018; Brukhim and Hazan 2020). The relationship to the Frank-Wolfe method was explicit in these works, and it also was studied by Freund, Grigas, and Mazumder (2017) and Wang et al. (2015). A framework that encapsulates both agnostic and realizable boosting, for both oﬄine and online settings, is given by Brukhim et al. (2020).

Boosting for the full OCO setting, with a multiplicative approximation and general convex decision set, was obtained by Hazan and Singh (2021). The latter also give tighter bounds by a factor of the dimension than those presented in this discussion using a more sophisticated smoothing technique known as the *Moreau-Yoshida regularization* (Beck 2017).

The contextual experts and bandits problems have been proposed by Langford and Zhang (2008) as a decision-making framework with a large number of policies. In the online setting, several works study the problem with an emphasis on efficient algorithms given access to an optimization oracle (Rakhlin and Sridharan 2016; Syrgkanis et al. 2016; Syrgkanis, Krishnamurthy, and Schapire 2016; Rakhlin and Sridharan 2016). For surveys on contextual bandit algorithms and applications of this model, see Zhou (2015) and Bouneffouf and Rish (2019).

## 12.6 Exercises

*   **1.**   Derive, from [algorithm 12.1](#chapter_12.xhtml#algo12-1), an algorithm for online binary classification. Spell out its regret guarantee.
*   **2.**   Formulate the online personalized article placement problem in the language of OCO (what is the decision set?). Define a weak learner in this context, as well as the final boosting guarantee from theorem 12.1.
*   **3.**   ^(\*) Define the Moreau-Yoshida regularization (or smoothing operator) as

![](images/pg180-1.png)

Prove that given any *G*\-Lipschitz *f*, the smoothed function ![](images/pg180-in-1.png)satisfies the following

**(a)** ![](images/pg180-in-2.png)is ![](images/pg180-in-3.png)\-smooth, and *G*\-Lispchitz.

**(b)** ![](images/pg180-in-4.png)for all **x** ∈ℝ^(*d*).

*   **4.**   ^(\*) Use the Moreau-Yoshida regularization to improve the bounds of theorem 12.1 by a factor of the dimension.

## Note

1.  [1](#chapter_12.xhtml#chapter12_1). The results henceforth hold with a different constant if we replace one by a different scaling.
    

# 13 Blackwell Approachability and Online Convex Optimization

The history of adversarial prediction started with the seminal works of the mathematicians David Blackwell and James Hannan. In most of the text thus far, we have presented the viewpoint of sequential prediction and loss minimization taken by Hannan. This was especially true in chapter 5, as the Follow the Perturbed Leader (FPL) algorithm dates to his work. In this chapter, we turn to a dual view of regret minimization, called *Blackwell approachability*. Approachability theory originated in the work of Blackwell, and it was discovered simultaneously to that of Hannan. A short historical account is surveyed in the bibliographic materials at the end of this chapter.

For decades, the relationship between regret minimization in general convex games and Blackwell approachability was not fully understood. The common thought was, in fact, that Blackwell approachability is a stronger notion. In this chapter, we show that approachability and online convex optimization (OCO) are equivalent in a strong sense: an algorithm for one task implies an algorithm for the other with no loss of computational efficiency.

As a side benefit of this equivalence, we deduce a proof of Blackwell’s approachability theorem using the existence of OCO algorithms. This proof applies to a more general version of approachabilty than general vector games, and it comes with rates of convergence that are borrowed from the OCO algorithms that we have already studied.

While previous chapters had a practical motivation and introduced methods for online learning, this chapter is purely theoretical and devoted to give an alternative viewpoint of OCO from a game theory perspective.

## 13.1 Vector-Valued Games and Approachability

John von Neumann’s minimax theorem, studied in chapter 8, establishes a central result in the theory of two-player zero-sum games by providing a prescription to both players. This prescription is in the form of a pair of optimal mixed strategies: each strategy attains the optimal worst-case value of the game without knowing the opponent’s strategy. However, the theorem fundamentally requires that both players have a utility function that can be expressed as a *scalar*.

In 1956, in response to von Neumann’s result, Blackwell posed an intriguing question: what guarantee can we hope to achieve when playing a two-player game with a *vector-valued payoff* ?

A vector-valued game is defined similarly to zero-sum games as described in definition 8.1, with reward/loss vectors replacing the scalar rewards/losses.

**Definition 13.1** *A two-player vector game is given by a set of n* × *m vectors* {**u**(*i, j*) ∈ ℝ^(*d*)}*. The reward vector for the row player playing strategy i* ∈ \[*n*\]*, and column player playing strategy j* ∈ \[*m*\]*, is given by the vector* **u**(*i, j*) ∈ ℝ^(*d*).

Similar to scalar games, we can define mixed strategies as distributions over pure strategies, and denote the expected reward vector for playing mixed strategies by

![](images/pg182-1.png)

We henceforth consider more general vector games than originally considered in the literature. The additional generality allows for an uncountable number of strategies for both players and allows the strategies to originate from bounded convex and closed sets in Euclidean space.

**Definition 13.2** *A generalized two-player vector game is given by a set of vectors* {**u** ∈ ℝ^(*d*)}*, and two bounded convex and closed decision sets* 𝒦[1], 𝒦[2]*. The reward vector for the row player playing strategy* **x** ∈ 𝒦[1]*, and column player playing strategy* **y** ∈𝒦[2]*, is given by the vector* **u**(**x**, **y**) ∈ ℝ^(*d*).

The goal of a zero-sum game is clear: to guarantee a certain loss/reward. What should be the vector game generalization? Blackwell proposed to ask, “Can we guarantee that our vector payoff lies in some closed convex set *S*?”

It is left as an exercise at the end of this chapter to show that an immediate analog of von Neumann’s theorem does not exist: there is no single mixed strategy that ensures that the vector payoff lies in a given set. However, this does not rule out an asymptotic notion, if we allow the game to repeat indefinitely, and ask whether there exists a strategy to ensure that the *average* reward vector lies in a certain set or at least approaches it in terms of Euclidean distance. This is exactly the solution concept that Blackwell proposed, as defined formally in definition 13.3.

Using the notation that we have used throughout this text, we denote the Euclidean distance to a bounded, closed and convex set *S* as

![](images/pg183-1.png)

**Definition 13.3** *Given a generalized vector game* 𝒦[1], 𝒦[2], {**u**(·, ·)}*, we say that a set S* ⊆ ℝ^(*d*) *is* **approachable** *if there exists an algorithm* 𝒜*, called an* **approachability algorithm***, that iteratively selects points* 𝒦[1] ∋ **x**[*t*] ← 𝒜(**y**[1], **y**[2]*, …*, **y**[*t*−1])*, such that, for any sequence* **y**[1], **y**[2]*, …*, **y**[*T*] ∈𝒦[2]*, we have*

![](images/pg183-2.png)

Under this notion, we can now allow the player to implement an adaptive strategy for a repeated version of the game, and we require that the average reward vector comes arbitrarily close to *S*. Blackwell’s theorem characterizes which sets in Euclidean space are approachable. We give it in generalized form in theorem 13.1.

**Theorem 13.1 (Blackwell’s approachability theorem)** *For any vector game* 𝒦[1], 𝒦[2], {**u**(·, ·)}*, the closed, bounded and convex set S* ⊆ ℝ^(*d*) *is approachable if and only if the following condition holds:*

![](images/pg183-3.png)

The approachability condition spelled out in this equation is both necessary and sufficient. The necessity of this condition is left as an exercise, and the more interesting implication is that any set that satisfies this condition is in fact approachable. Our reductions henceforth give an explicit proof of Blackwell’s theorem, and we leave it as an exercise to draw the explicit conclusion of theorem 13.1 from the first efficient reduction.

The relationship between Blackwell approachability in vector games and OCO may not be evident at this point. However, we proceed to show that the two notions are in fact algorithmically equivalent.

In the next section, we show that any algorithm for OCO can be efficiently converted to an approachability algorithm for vector games. Following this, we show the reverse as well: an approachability algorithm for vector games gives an OCO algorithm with no loss of efficiency!

## 13.2 From OCO to Approachability

In this section, we give an efficient reduction from OCO to approachability. Namely, assume that we have an OCO algorithm denoted as 𝒜, which attains sublinear regret. Our goal is to design a Blackwell approachability algorithm for a given vector game and a closed, bounded convex set *S*. Thus, the reduction in this section shows that OCO is a stronger notion than approachabiliy. This direction is perhaps the more surprising one, and was discovered more recently (see the sources listed in section 13.4 for an historical account of this development).

Since we are looking to approach a given set, it is natural to consider minimizing the distance of our reward vector to the set. Recall that we denote the Euclidean distance to a set as **Dist**(**w***, S*) = min[**x**∈*S*]∥**w**−**x**∥. The support function of the closed convex set *S* is given by

![](images/pg184-1.png)

Notice that this function is convex, since it is a maximum over linear functions.

**Lemma 13.1** *The distance to a set can be written as*

![](images/eq13-1.png)

*Proof.* Using the definition of the support function,

![](images/pg184-2.png)

Blackwell’s theorem characterizes approachable sets: it is necessary and sufficient to be able to find a best response **x** ∈𝒦[1], to any **y** ∈𝒦[2], such that **u**(**x**, **y**) ∈ *S*. To proceed with the reduction, we need an equivalent condition stated formally in lemma 13.2.

**Lemma 13.2** *For a generalized vector game* 𝒦[1], 𝒦[2], {**u**}*, the following conditions are equivalent:*

*   1.   *There exists a feasible best response,*

![](images/pg184-3.png)

*   2.   *For all* **w** ∈ ℝ^(*d*), ∥**w**∥≤ 1*, there exists* **x** ∈𝒦[1] *such that*

![](images/pg184-4.png)

*Proof.* Consider the scalar zero-sum game

![](images/pg185-1.png)

Blackwell’s theorem asserts that *λ* = 0 if and only if *S* is approachable. Using Sion’s generalization of the von Neumann minimax theorem from chapter 8, 

![](images/pg185-2.png)

Thus, the second statement of the lemma is satisfied if and only if *λ* = 0.

☐

As mentioned previously, the necessity of Blackwell’s condition is left as an exercise. To prove sufficiency, we assume that form 2 of Blackwell’s condition, as given in lemma 13.2, is satisfied. Formally, we henceforth assume that the vector game and set *S* are equipped with a best response oracle 𝒪, such that

![](images/eq13-2.png)

We proceed with the formal proof of sufficiency, constructively specified in [algorithm 13.1](#chapter_13.xhtml#algo13-1). Notice that in this reduction, function *f*[*t*] is concave, and the OCO algorithm is used for maximization.

![](images/Algorithm13-1.png)

**Theorem 13.2** *[Algorithm 13.1](#chapter_13.xhtml#algo13-1), with input OCO algorithm* 𝒜*, returns the vector ![](images/pg185-in-1.png), which approaches set S at a rate of*

![](images/pg185-3.png)

*Proof.* Notice that equation ([13.2](#chapter_13.xhtml#eq13-2)) implies that for **w**[*t*] as defined in the algorithm, we have

![](images/pg186-1.png)

This implies that for any *t*,

![](images/eq13-3.png)

Therefore, we have, using lemma 13.1,

![](images/pg186-2.png)

This theorem explicitly relates OCO to approachability, and since we have already proved the existence of efficient OCO algorithms in this book, it can be used to prove Blackwell’s theorem formally. Completing the details is left as an exercise at the end of this chapter.

## 13.3 From Approachability to OCO

In this section, we show the converse reduction: given an approachability algorithm, we design an OCO algorithm with no loss of computational efficiency. This direction was essentially shown by Blackwell for discrete decision problems, as described in more detail in section 13.4. We prove it here in the full generality of OCO.

Formally, given an approachability algorithm 𝒜, denote by **Dist**[*T*](𝒜) an upper bound on its rate of convergence to set *S* as a function of the number of iterations *T*. That is, for a given vector game, denote by ![](images/pg186-in-1.png)the average reward vector. Then 𝒜 guarantees

![](images/pg186-3.png)

Given an approachability algorithm 𝒜, we henceforth create an OCO algorithm with vanishing regret.

### 13.3.1 Cones and polar cones

Approachability is in a certain geometric sense a dual to OCO. To see this, we require several geometric notions, which are explicitly required for the reduction from approachability to OCO.

For a given convex set 𝒦⊆ ℝ^(*d*), we define its cone as the set of all vectors in 𝒦 multiplied by a nonnegative scalar:

![](images/pg187-1.png)

The notion of a convex cone is not strictly required for the proofs given here, but they are commonly used in the context of approachability. The polar set to a given set 𝒦⊆ ℝ^(*d*) is defined to be

![](images/pg187-2.png)

It is left as an exercise to prove that 𝒦⁰ is a convex set, and for cones, the polar to the polar is the original set.

Henceforth, we need the extension of a convex set defined as follows. Denote by 1 ⊕𝒦 as the direct sum of the scalar one and the set 𝒦 (i.e., all vectors of the form ![](images/pg187-in-1.png)for **x** ∈𝒦). Denote the bounded polar extension of set 𝒦 by

![](images/pg187-3.png)

That is, we take all points in the polar set to the direct sum 1 ⊕𝒦.

This definition of the polar set gives rise to the quantitative characterization given in lemma 13.3.

**Lemma 13.3** *Let* **y** ∈ ℝ^(*d*+1) *be such that* **Dist**(**y***, Q*(𝒦)) ≤ *ε. Then, denoting by D the diameter of* 𝒦,

![](images/pg187-4.png)

*Proof.* By definition of distance to a set, we have that **Dist**(**y***, Q*(𝒦)) ≤ *ε* implies the existence of a point **z** ∈ *Q*(𝒦), such that ∥**y**−**z**∥≤ *ε*. Thus, for all ![](images/pg187-in-2.png), we have

![](images/pg187-5.png)

### 13.3.2 The reduction

[Algorithm 13.2](#chapter_13.xhtml#algo13-2) takes as an input a Blackwell approachability algorithm that guarantees, under the necessary and sufficient condition, convergence to a given set. It also takes as an input a set 𝒦 for OCO.

The reduction considers a vector game with decision sets 𝒦, ℱ and an approachability set *S* = *Q*(𝒦), and generates a sequence of decisions that guarantee low regret, as we prove next.

Since this reduction creates the approachability set *S* as a function of 𝒦, we need to prove that indeed set *S* is approachable. We show this in the next subsection.

![](images/Algorithm13-2.png)

**Theorem 13.3** *The reduction defined in [algorithm 13.2](#chapter_13.xhtml#algo13-2), for any input algorithm* 𝒜*, produces an OLO algorithm* ℒ *such that*

![](images/pg188-1.png)

*Proof.* The approachability algorithm guarantees ![](images/pg188-in-1.png). Using the definition of *S* and lemma 13.3, we have

![](images/pg188-2.png)

where the second inequality holds because the first inequality holds for every ![](images/pg188-in-2.png), particularly for the vector 1 ⊕**x**^(*⋆*).

☐

### 13.3.3 Existence of a best response oracle

Notice that the reduction of this section from approachability to OCO does not require the best response oracle. However, Blackwell’s approachability theorem does require this oracle to be sufficient and necessary, and thus for the set *S* that we constructed to be approachable at all, such an oracle needs to exist. This is what we show next.

Consider the vector **u**[*t*] constructed in the reduction. A best response oracle finds, for every vector **y**, a vector **x** that guarantees **u**(**x**, **y**) ∈ *S*. In our case, this translates to the condition

![](images/pg189-1.png)

By definition of the polar set, this implies that for all ![](images/pg189-in-1.png), we have

![](images/pg189-2.png)

In other words, the best response oracle corresponds to a procedure that given *f*, finds a vector **x**^(*⋆*) such that

![](images/pg189-3.png)

Here is an optimization oracle for set 𝒦!

## 13.4 Bibliographic Remarks

David Blackwell’s celebrated approachability theorem was described in the mid-1950s (Blackwell 1956). The first no-regret algorithm for a discrete action setting was given in a seminal paper by James Hannan (1957) the next year. That same year, Blackwell pointed out that his approachability result leads, as a special case, to an algorithm with essentially the same low-regret guarantee proven by Hannan (Blackwell 1954). For Hannan’s account of events, see Gilliland, Ramamoorthi, and Hannan (2010).

Over the years, several other problems have been reduced to Blackwell approachability, including asymptotic calibration (Foster and Vohra 1998), online learning with global cost functions (Even-Dar et al. 2009) and others (Mannor and Shimkin 2008). Indeed, it has been presumed that approachability, while establishing the existence of a no-regret algorithm, is strictly more powerful than regret minimization; hence its utility in such a wide range of problems.

However, this was recently shown not to be the case. Abernethy, Bartlett, and Hazan (2011) showed that approachability is in fact equivalent to OCO. This result is the basis of the material presented in this chapter. One side of their reduction was simplified and generalized in Shimkin (2016).

## 13.5 Exercises

*   **1.**   Prove that von Neumann’s theorem does not hold for vector games; that is, give an example of a vector game such that there is no single mixed strategy ensuring that the vector payoff lies in a given set. Show that this is true even for approachable sets.
*   **2.**   Prove that the polar set of a given convex set 𝒦∈ℝ^(*d*) is convex.
*   **3.**   Prove that Blackwell’s condition is necessary; that is, prove that for set *S* to be approachable in a given vector game, there must exist an oracle 𝒪 such that

![](images/pg190-1.png)

*   **4.**   Complete the proof of Blackwell’s theorem using the first reduction in this chapter and the existence of OCO algorithms. That is, prove that for a given vector game, the existence of an oracle as per question 3, is sufficient for the set *S* ⊆ℝ^(*d*) to be approachable.

# References

*   Abernethy, Jacob, Peter L Bartlett, and Elad Hazan. 2011. “Blackwell Approachability and No-Regret Learning Are Equivalent.” *Proceedings of the 24th Annual Conference on Learning Theory,* 19: 27–46.
*   Abernethy, Jacob, Rafael M. Frongillo, and Andre Wibisono. 2012. “Minimax Option Pricing Meets Black-Scholes in the Limit.” *Proceedings of the Forty-fourth Annual ACM Symposium on Theory of Computing,* 1029–1040. ACM. [http://doi.acm.org/10](http://doi.acm.org/10.1145/2213977.2214070) [.1145/2213977.2214070](http://doi.acm.org/10.1145/2213977.2214070).
*   Abernethy, Jacob, Elad Hazan, and Alexander Rakhlin. 2008. “Competing in the Dark: An Efficient Algorithm for Bandit Linear Optimization.” *Proceedings of the 21st Annual Conference on Learning Theory,* 263–274.
*   Abernethy, Jacob, Chansoo Lee, Abhinav Sinha, and Ambuj Tewari. 2014. “Online Linear Optimization via Smoothing.” *Proceedings of the 27th Conference on Learning Theory,* 807–823.
*   Abernethy, Jacob, Chansoo Lee, and Ambuj Tewari. 2016. “Perturbation Techniques in Online Learning and Optimization.” In *Perturbations, Optimization, and Statistics,* edited by Tamir Hazan, George Papandreou, and Daniel Tarlow, 233–262. Neural Information Processing Series. MIT Press.
*   Abernethy, Jacob, and Alexander Rakhlin. 2009. “Beating the Adaptive Bandit with High Probability.” *Proceedings of the 22nd Annual Conference on Learning Theory.*
*   Adamskiy, Dmitry, Wouter M Koolen, Alexey Chernov, and Vladimir Vovk. 2016. “A Closer look at Adaptive Regret.” *Journal of Machine Learning Research* 17 (1): 706–726.
*   Adler, Ilan. 2013. “The Equivalence of Linear Programs and Zero-Sum Games.” *International Journal of Game Theory* 42 (1): 165–177.
*   Agarwal, Amit, Elad Hazan, Satyen Kale, and Robert E. Schapire. 2006. “Algorithms for Portfolio Management Based on the Newton Method.” *Proceedings of the 23rd International Conference on Machine Learning,* 9–16. ACM.
*   Agarwal, Naman, Nataly Brukhim, Elad Hazan, and Zhou Lu. 2019. “Boosting for Dynamical Systems.” *arXiv preprint arXiv:1906.08720.*
*   Albers, Donald J., Constance Reid, and George B. Dantzig. 1986. “An Interview with George B. Dantzig: The Father of Linear Programming.” *College Mathematics Journal* 17 (4): 292–314.
*   Allen-Zhu, Zeyuan, and Elad Hazan. 2016. “Optimal Black-Box Reductions Between Optimization Objectives.” *CoRR* abs/1603.05642.
*   Allen-Zhu, Zeyuan, Elad Hazan, Wei Hu, and Yuanzhi Li. 2017. “Linear Convergence of a Frank-Wolfe Type Algorithm over Trace-Norm Balls.” *Proceedings of the 31st International Conference on Neural Information Processing Systems,* 6192–6201.
*   Allen-Zhu, Zeyuan, and Yuanzhi Li. 2016. “LazySVD: Even Faster SVD Decomposition yet Without Agonizing Pain.” *Proceedings of the 30th International Conference on Neural Information Processing Systems,* 982–990.
*   Alon, Noga, and Joel Spencer. 1992. *The Probabilistic Method.* John Wiley.
*   Anava, Oren, Elad Hazan, Shie Mannor, and Ohad Shamir. 2013. “Online Learning for Time Series Prediction.” *In Conference on Learning Theory,* 172–184. PMLR.
*   Arora, Sanjeev, and Boaz Barak. 2009. *Computational Complexity: A Modern Approach.* Cambridge University Press.
*   Arora, Sanjeev, Elad Hazan, and Satyen Kale. 2012. “The Multiplicative Weights Update Method: A Meta-Algorithm and Applications.” *Theory of Computing* 8 (6): 121–164. doi:[10.4086/toc.2012.v008a006](http://dx.doi.org/10.4086/toc.2012.v008a006).
*   Audibert, Jean-Yves, and Sébastien Bubeck. 2009. “Minimax Policies for Adversarial and Stochastic Bandits.” *In COLT 2009—22nd Conference on Learning Theory, Montreal, Quebec, Canada, June 18–21, 2009.*
*   Auer, Peter, Nicolò Cesa-Bianchi, Yoav Freund, and Robert E. Schapire. 2003. “The Nonstochastic Multiarmed Bandit Problem.” *SIAM Journal of Computing* 32 (1): 48–77. [http://dx.doi.org/10.1137/S0097539701398375](http://dx.doi.org/10.1137/S0097539701398375).
*   Awerbuch, Baruch, and Robert Kleinberg. 2008. “Online Linear Optimization and Adaptive Routing.” *Journal of Computer and System Sciences* 74 (1): 97–114. [http://dx.doi.org/10.1016/j.jcss.2007.04.016](http://dx.doi.org/10.1016/j.jcss.2007.04.016).
*   Azoury, Katy S., and M. K. Warmuth. 2001. “Relative Loss Bounds for On-Line Density Estimation with the Exponential Family of Distributions.” *Machine Learning* 43, no. 3 (June): 211–246.
*   Bach, Francis, Simon Lacoste-Julien, and Guillaume Obozinski. 2012. “On the Equivalence Between Herding and Conditional Gradient Algorithms.” *Proceedings of the 29th International Conference on Machine Learning (ICML-12),* edited by John Langford and Joelle Pineau, 1359–1366. Omnipress.
*   Bachelier, Louis. 1900. “Théorie de la spéculation.” *Annales Scientifiques de l’École Normale Supérieure* 3 (17): 21–86.
*   Beck, Amir. 2017. *First-Order Methods in Optimization.* SIAM.
*   Bellet, Aurélien, Yingyu Liang, Alireza Bagheri Garakani, Maria-Florina Balcan, and Fei Sha. 2014. “Distributed Frank-Wolfe Algorithm: A Unified Framework for Communication-Efficient Sparse Learning.” *CoRR* abs/1404.2644.
*   Ben-David, Shai, Philip M. Long, and Yishay Mansour. 2001. “Agnostic Boosting.” *In International Conference on Computational Learning Theory,* 507–516. Springer.
*   Bertsimas, Dimitris, and John Tsitsiklis. 1997. *Introduction to Linear Optimization.* Athena Scientific.
*   Besbes, Omar, Yonatan Gur, and Assaf Zeevi. 2015. “Non-stationary Stochastic Optimization.” *Operations Research* 63 (5): 1227–1244.
*   Beygelzimer, Alina, Elad Hazan, Satyen Kale, and Haipeng Luo. 2015. “Online Gradient Boosting.” *In Advances in Neural Information Processing Systems,* 2458–2466.
*   Beygelzimer, Alina, Satyen Kale, and Haipeng Luo. 2015. “Optimal and Adaptive Algorithms for Online Boosting.” *International Conference on Machine Learning,* 2323–2331.
*   Black, Fischer, and Myron Scholes. 1973. “The Pricing of Options and Corporate Liabilities.” *Journal of Political Economy* 81 (3): 637–654.
*   Blackwell, D. 1954. “Controlled Random Walks.” *Proceedings of the International Congress of Mathematicians,* 3: 336–338.
*   Blackwell, D. 1956. “An Analog of the Minimax Theorem for Vector Payoffs.” *Pacific Journal of Mathematics* 6 (1): 1–8.
*   Blum, Avrim, and Adam Kalai. 1999. “Universal Portfolios with and Without Transaction Costs.” *Machine Learning* 35, no. 3 (June): 193–205. [http://dx.doi.org/10.1023/A:1007530728748](http://dx.doi.org/10.1023/A:1007530728748).
*   Borwein, J. M., and A. S. Lewis. 2006. *Convex Analysis and Nonlinear Optimization: Theory and Examples.* CMS Books in Mathematics. Springer. http://books.google.fr/books?id=TXWzqEkAa7IC.
*   Boser, Bernhard E., Isabelle M. Guyon, and Vladimir N. Vapnik. 1992. “A Training Algorithm for Optimal Margin Classifiers.” *Proceedings of the Fifth Annual Workshop on Computational Learning Theory,* 144–152.
*   Bottou, Léon. 1998. “Online Learning and Stochastic Approximations.” *On-line Learning in Neural Networks* 17 (9): 142.
*   Bottou, Léon, and Olivier Bousquet. 2008. “The Tradeoffs of Large-Scale Learning.” *Advances in Neural Information Processing Systems,* 161–168.
*   Bouneffouf, Djallel, and Irina Rish. 2019. “A Survey on Practical Applications of Multi-armed and Contextual Bandits.” *arXiv preprint arXiv:1904.10040.*
*   Bousquet, Olivier, Steve Hanneke, Shay Moran, and Nikita Zhivotovskiy. 2020. “Proper Learning, Helly Number, and an Optimal SVM Bound.” *In Conference on Learning Theory,* 582–609. PMLR.
*   Bousquet, Olivier, and Manfred K. Warmuth. 2003. “Tracking a Small Set of Experts by Mixing Past Posteriors.” *Journal of Machine Learning Research* 3: 363–396.
*   Boyd, Stephen. 2014. *Lecture Notes: Subgradient Methods,* January.
*   Boyd, S., and L. Vandenberghe. 2004. *Convex Optimization.* Cambridge University Press, March.
*   Brukhim, Nataly, Xinyi Chen, Elad Hazan, and Shay Moran. 2020. *Online Agnostic Boosting via Regret Minimization. arXiv*: 2003.01150 (cs.LG).
*   Brukhim, Nataly, and Elad Hazan. 2020. “Online Boosting with Bandit Feedback.” *arXiv preprint arXiv:2007.11975.*
*   Bubeck, Sébastien. 2015. “Convex Optimization: Algorithms and Complexity.” *Foundations and Trends in Machine Learning* 8 (3–4): 231–357.
*   Bubeck, Sébastien, and Nicoló Cesa-Bianchi. 2012. “Regret Analysis of Stochastic and Nonstochastic Multi-armed Bandit Problems.” *Foundations and Trends in Machine Learning* 5 (1): 1–122.
*   Bubeck, Sébastien, Ofer Dekel, Tomer Koren, and Yuval Peres. 2015. “Bandit Convex Optimization sqrt{T) Regret in One Dimension.” *In Conference on Learning Theory,* 266–278. PMLR.
*   Bubeck, Sébastien, Yin Tat Lee, and Ronen Eldan. 2017. “Kernel-Based Methods for Bandit Convex Optimization.” *Proceedings of the 49th Annual ACM SIGACT Symposium on Theory of Computing,* 72–85.
*   Candes, E., and B. Recht. 2009. “Exact Matrix Completion via Convex Optimization.” *Foundations of Computational Mathematics* 9 (6): 717–772.
*   Cesa-Bianchi, N., A. Conconi, and C. Gentile. 2006. “On the Generalization Ability of On-line Learning Algorithms.” *IEEE Transactions on Information Theory* 50, no. 9 (September): 2050–2057.
*   Cesa-Bianchi, N., and C. Gentile. 2008. “Improved Risk Tail Bounds for On-Line Algorithms.” *IEEE Transactions on Information Theory,* 54, no. 1 (January): 386–390.
*   Cesa-Bianchi, Nicoló, and Gábor Lugosi. 2006. *Prediction, Learning, and Games.* Cambridge University Press.
*   Chen, Lin, Christopher Harshaw, Hamed Hassani, and Amin Karbasi. 2018. “Projection-Free Online Optimization with Stochastic Gradient: From Convexity to Submodularity.” *International Conference on Machine Learning,* 814–823.
*   Chen, Shang-Tse, Hsuan-Tien Lin, and Chi-Jen Lu. 2012. “An Online Boosting Algorithm with Theoretical Justifications.” *Proceedings of the 29th International Coference on International Conference on Machine Learning,* 1873–1880.
*   Chen, Shang-Tse, Hsuan-Tien Lin, and Chi-Jen Lu. 2014. “Boosting with Online Binary Learners for the Multiclass Bandit Problem.” *International Conference on Machine Learning,* 342–350.
*   Clarkson, Kenneth L., Elad Hazan, and David P. Woodruff. 2012. “Sublinear Optimization for Machine Learning.” *Journal of the ACM* 59, no. 5 (November): 23:1–23:49.
*   Cortes, Corinna, and Vladimir Vapnik. 1995. “Support-Vector Networks.” *Machine Learning* 20 (3): 273–297.
*   Cover, Thomas. 1991. “Universal Portfolios.” *Mathematical Finance* 1 (1): 1–19.
*   Dani, Varsha, Thomas Hayes, and Sham Kakade. 2008. “The Price of Bandit Information for Online Optimization.” In *Advances in Neural Information Processing Systems 20,* edited by J. C. Platt, D. Koller, Y. Singer, and S. Roweis. MIT Press.
*   Daniely, Amit. 2016. “Complexity Theoretic Limitations on Learning Halfspaces.” *Proceedings of the Forty-Eighth Annual ACM Symposium on Theory of Computing,* 105–117.
*   Daniely, Amit, Alon Gonen, and Shai Shalev-Shwartz. 2015. “Strongly Adaptive Online Learning.” *In International Conference on Machine Learning,* 1405–1411. PMLR.
*   Dantzig, G. B. 1951. “Maximization of a Linear Function of Variables Subject to Linear Inequalities, “In *Activity Analysis of Production and Allocation*.” Wiley.
*   David, Ofir, Shay Moran, and Amir Yehudayoff. 2016. “On Statistical Learning via the Lens of Compression.” *arXiv preprint arXiv:1610.03592.*
*   Dekel, Ofer, Ambuj Tewari, and Raman Arora. 2012. “Online Bandit Learning Against an Adaptive Adversary: From Regret to Policy Regret.” *Proceedings of the 29th International Conference on Machine Learning, ICML 2012, Edinburgh, Scotland, UK, June 26–July 1, 2012.*
*   DeMarzo, Peter, Ilan Kremer, and Yishay Mansour. 2006. “Online Trading Algorithms and Robust Option Pricing.” *In STOC ’06: Proceedings of the Thirty-Eighth Annual ACM Symposium on Theory of Computing,* 477–486.
*   Duchi, John, Elad Hazan, and Yoram Singer. 2011. “Adaptive Subgradient Methods for Online Learning and Stochastic Optimization.” *Journal of Machine Learning Research* 12: 2121–2159.
*   Duchi, John C., Elad Hazan, and Yoram Singer. 2010. “Adaptive Subgradient Methods for Online Learning and Stochastic Optimization.” *In COLT 2010–The 23rd Conference on Learning Theory, Haifa, Israel, June 27–29, 2010,* 257–269.
*   Dudík, Miroslav, Zaïd Harchaoui, and Jérôme Malick. 2012. “Lifted Coordinate Descent for Learning with Trace-Norm Regularization.” *Journal of Machine Learning Research–Proceedings Track* 22: 327–336.
*   Even-Dar, E., S. Kakade, and Y. Mansour. 2009. “Online Markov Decision Processes.” *Mathematics of Operations Research* 34 (3): 726–736.
*   Even-Dar, E., R. Kleinberg, S. Mannor, and Y. Mansour. 2009. “Online Learning for Global Cost Functions.” *In 22nd Annual Conference on Learning Theory (COLT).*
*   Even-Dar, Eyal, Yishay Mansour, and Uri Nadav. 2009. “On the Convergence of Regret Minimization Dynamics in Concave Games.” *Proceedings of the Forty-first Annual ACM Symposium on Theory of Computing,* 523–532.
*   Feldman, Vitaly. 2009. “Distribution-Specific Agnostic Boosting.” *arXiv preprint arXiv:0909.2927.*
*   Flaxman, Abraham, Adam Tauman Kalai, and H. Brendan McMahan. 2005. “Online Convex Optimization in the Bandit Setting: Gradient Descent Without a Gradient.” *Proceedings of the 16th Annual ACM-SIAM Symposium on Discrete Algorithms,* 385–394.
*   Foster, D. P, and R. V. Vohra. 1998. “Asymptotic Calibration.” *Biometrika* 85 (2): 379.
*   Foster, Dylan J., Satyen Kale, Haipeng Luo, Mehryar Mohri, and Karthik Sridharan. 2018. “Logistic Regression: The Importance of Being Improper.” *In Conference on Learning Theory,* 167–208. PMLR.
*   Frank, M., and P. Wolfe. 1956. “An Algorithm for Quadratic Programming.” *Naval Research Logistics Quarterly* 3: 149–154.
*   Freund, Robert M., Paul Grigas, and Rahul Mazumder. 2017. “A New Perspective on Boosting in Linear Regression via Subgradient Optimization and Relatives.” *Annals of Statistics* 45 (6): 2328–2364.
*   Freund, Yoav. 1995. “Boosting a Weak Learning Algorithm by Majority.” *Information and Computation* 121 (2): 256–285.
*   Freund, Yoav, and Robert E. Schapire. 1997. “A Decision-Theoretic Generalization of On-line Learning and an Application to Boosting.” *Journal of Computer and System Sciences* 55, no. 1 (August): 119–139.
*   Freund, Yoav, and Robert E. Schapire. 1999. “Adaptive Game Playing Using Multiplicative Weights.” *Games and Economic Behavior* 29 (1–2): 79–103.
*   Friedman, Jerome H. 2002. “Stochastic Gradient Boosting.” *Computational Statistics & Data Analysis* 38 (4): 367–378.
*   Garber, Dan. 2016. “Faster Projection-Free Convex Optimization over the Spectrahedron.” *Proceedings of the 30th International Conference on Neural Information Processing Systems,* 874–882.
*   Garber, Dan, and Elad Hazan. 2011. “Approximating Semidefinite Programs in Sublinear Time.” *NIPS,* 1080–1088.
*   Garber, Dan, and Elad Hazan. 2013. “Playing Non-linear Games with Linear Oracles.” *FOCS,* 420–428.
*   Gass, Saul I. 2006. “IFORS’ Operational Research Hall of Fame: John von Neumann.” *International Transactions in Operational Research* 13 (1): 85–90.
*   Gilliland, Dennis, RV Ramamoorthi, and James Hannan. 2010. “A Conversation with James Hannan.” *Statistical Science:* 126–144.
*   Goodfellow, Ian, Yoshua Bengio, and Aaron Courville. 2016. *Deep Learning.* MIT Press.
*   Gopalan, Parikshit, T. S. Jayram, Robert Krauthgamer, and Ravi Kumar. 2007. “Estimating the Sortedness of a Data Stream.” *SODA,* 7: 318–327.
*   Gottlieb, Lee-Ad, Aryeh Kontorovich, and Pinhas Nisnevitch. 2018. “Near-optimal Sample Compression for Nearest Neighbors.” *IEEE Transactions on Information Theory* 64 (6): 4120–4128.
*   Gradu, Paula, Elad Hazan, and Edgar Minasyan. 2020. “Adaptive Regret for Control of Time-Varying Dynamics.” *arXiv preprint arXiv:2007.04393.*
*   Grove, A., N. Littlestone, and D. Schuurmans. 2001. “General Convergence Results for Linear Discriminant Updates.” *Machine Learning* 43 (3): 173–210.
*   Gupta, Vineet, Tomer Koren, and Yoram Singer. 2017. “A unified approach to adaptive regularization in online and stochastic optimization.” *arXiv preprint arXiv:1706.06569.*
*   György, András, Tamás Linder, and Gábor Lugosi. 2005. “Tracking the Best of Many Experts.” *Proceedings of the 18th Annual Conference on Learning Theory, COLT 2005,* 204–216. Springer.
*   Hannan, James. 1957. “Approximation to Bayes Risk in Repeated Play.” Edited by A. W. Tucker M. Dresher and P. Wolfe. *In Contributions to the Theory of Games, volume 3:* 97–139. Princeton University Press.
*   Hanneke, Steve, Aryeh Kontorovich, and Menachem Sadigurschi. 2019. “Sample Compression for Real-Valued Learners.” *In Algorithmic Learning Theory,* 466–488. PMLR.
*   Harchaoui, Zaïd, Matthijs Douze, Mattis Paulin, Miroslav Dudík, and Jérôme Malick. 2012. “Large-Scale Image Classification with Trace-Norm Regularization.” *CVPR,* 3386–3393.
*   Hart, Sergiu, and Andreu Mas-Colell. 2000. “A Simple Adaptive Procedure Leading to Correlated Equilibrium.” *Econometrica* 68 (5): 1127–1150.
*   Hazan, Elad. 2006. “Efficient Algorithms for Online Convex Optimization and Their Applications.” AAI3223851. PhD diss., Princeton University.
*   Hazan, Elad. 2008. “Sparse Approximate Solutions to Semidefinite Programs.” *LATIN,* 306–316.
*   Hazan, Elad. 2011. “A Survey: The Convex Optimization Approach to Regret Minimization.” In *Optimization for Machine Learning,* edited by Suvrit Sra, Sebastian Nowozin, and Stephen J. Wright, 287–302. MIT Press.
*   Hazan, Elad. 2019. “Lecture Notes: Optimization for Machine Learning.” *arXiv preprint arXiv:1909.03550.*
*   Hazan, Elad, Amit Agarwal, and Satyen Kale. 2007. “Logarithmic Regret Algorithms for Online Convex Optimization.” *Machine Learning,* 69 (2–3), 169–192.
*   Hazan, Elad, and Sham Kakade. 2019. “Revisiting the Polyak step size.” *arXiv preprint arXiv:1905.00313.*
*   Hazan, Elad, Adam Kalai, Satyen Kale, and Amit Agarwal. 2006. “Logarithmic Regret Algorithms for Online Convex Optimization.” *In COLT,* edited by Gábor Lugosi and Hans-Ulrich Simon, 4005: 499–513. Lecture Notes in Computer Science. Springer.
*   Hazan, Elad, and Satyen Kale. 2008. “Extracting Certainty from Uncertainty: Regret Bounded by Variation in Costs.” *In 21st Annual Conference on Learning Theory (COLT),* 57–68.
*   Hazan, Elad, and Satyen Kale. 2009. “On Stochastic and Worst-Case Models for Investing.” *In Proceedings of the 22nd International Conference on Neural Information Processing Systems,* 709–717. MIT Press.
*   Hazan, Elad, and Satyen Kale. 2011. “Beyond the Regret Minimization Barrier: An Optimal Algorithm for Stochastic Strongly-Convex Optimization.” *Journal of Machine Learning Research–Proceedings Track:* 421–436.
*   Hazan, Elad, and Satyen Kale. 2012. “Projection-Free Online Learning.” *In ICML.*
*   Hazan, Elad, Tomer Koren, and Nati Srebro. 2011. “Beating SGD: Learning SVMs in Sublinear Time.” *Advances in Neural Information Processing Systems,* 1233–1241.
*   Hazan, Elad, and Yuanzhi Li. 2016. “An Optimal Algorithm for Bandit Convex Optimization.” *arXiv preprint arXiv:1603.04350.*
*   Hazan, Elad, and Haipeng Luo. 2016. “Variance-Reduced and Projection-Free Stochastic Optimization.” *In International Conference on Machine Learning,* 1263–1271. PMLR.
*   Hazan, Elad, and Comandur Seshadhri. 2007. “Adaptive Algorithms for Online Decision Problems.” *Electronic Colloquium on Computational Complexity (ECCC).* 14. 088.
*   Hazan, Elad, and Karan Singh. 2021. *Boosting for Online Convex Optimization. arXiv*: 2102.09305 (cs.LG).
*   Herbster, Mark, and Manfred K. Warmuth. 1998. “Tracking the Best Expert.” *Machine Learning* 32 (2): 151–178. [http://dx.doi.org/10.1023/A:1007424614876](http://dx.doi.org/10.1023/A:1007424614876).
*   Jaggi, Martin. 2013. “Revisiting Frank-Wolfe: Projection-Free Sparse Convex Optimization.” *In ICML.*
*   Jaggi, Martin, and Marek Sulovský. 2010. “A Simple Algorithm for Nuclear Norm Regularized Problems.” *In Proceedings of the 27th International Conference on International Conference on Machine Learning,* 471–478.
*   Jung, Young Hun, Jack Goetz, and Ambuj Tewari. 2017. “Online multiclass boosting.” *Advances in Neural Information Processing Systems,* 919–928.
*   Jung, Young Hun, and Ambuj Tewari. 2018. “Online Boosting Algorithms for Multi-label Ranking.” *International Conference on Artificial Intelligence and Statistics,* 279–287.
*   Kalai, Adam Tauman, Yishay Mansour, and Elad Verbin. 2008. “On Agnostic Boosting and Parity Learning.” *Proceedings of the Fortieth Annual ACM Symposium on Theory of Computing,* 629–638.
*   Kalai, Adam Tauman, and Rocco A. Servedio. 2005. “Boosting in the Presence of Noise.” *Journal of Computer and System Sciences* 71 (3): 266–290. [https://doi.org/10.1016/j.jcss.2004.10.015](https://doi.org/10.1016/j.jcss.2004.10.015).
*   Kalai, Adam, and Santosh Vempala. 2003. “Efficient Algorithms for Universal Portfolios.” *Journal of Machine Learning Research* 3 (March): 423–440. [http://dl.acm.org/citation.cfm?id\=944919.944942](http://dl.acm.org/citation.cfm?id=944919.944942).
*   Kalai, Adam, and Santosh Vempala. 2005. “Efficient Algorithms for Online Decision Problems.” *Journal of Computer and System Sciences* 71 (3): 291–307.
*   Kanade, Varun, and Adam Kalai. 2009. “Potential-Based Agnostic Boosting.” *In Proceedings of the 22nd International Conference on Neural Information Processing Systems,* 880–888.
*   Kantorovich, L. V. 1940. “A New Method of Solving Some Classes of Extremal Problems.” *Doklady Akad Sci USSR* 28: 211–214.
*   Kearns, Michael J., and Umesh V. Vazirani. 1994. *An Introduction to Computational Learning Theory.* MIT Press.
*   Kingma, Diederik P., and Jimmy Ba. 2014. “Adam: A Method for Stochastic Optimization.” *arXiv preprint arXiv:1412.6980.*
*   Kivinen, Jyrki, and Manfred K. Warmuth. 1997. “Exponentiated Gradient Versus Gradient Descent for Linear Predictors.” *Information and Computation* 132 (1): 1–63.
*   Kivinen, Jyrki, and Manfred K. Warmuth. 2001. “Relative Loss Bounds for Multidimensional Regression Problems.” *Machine Learning* 45 (3): 301–329.
*   Kivinen, Jyrki, and Manfred K. Warmuth. 1999. “Averaging Expert Predictions.” In *Computational Learning Theory,* edited by Paul Fischer and HansUlrich Simon, 1572:153–167. Lecture Notes in Computer Science. Springer Berlin Heidelberg.
*   Kontorovich, Aryeh, Sivan Sabato, and Roi Weiss. 2017. “Nearest-Neighbor Sample Compression: Efficiency, Consistency, Infinite dimensions.” *Proceedings of the 31st International Conference on Neural Information Processing Systems,* 1572–1582.
*   Kozat, S. S., and A. C. Singer. 2007. “Universal Constant Rebalanced Portfolios with Switching.” *IEEE International Conference on Acoustics, Speech, and Signal Processing, (ICASSP),* 3: 1129–1132.
*   Kuczyński, Jacek, and Henryk Woźniakowski. 1992. “Estimating the Largest Eigenvalue by the Power and Lanczos Algorithms with a Random Start.” *SIAM Journal on Matrix Analysis and Applications* 13 (4): 1094–1122.
*   Lacoste-Julien, Simon, Martin Jaggi, Mark W. Schmidt, and Patrick Pletscher. 2013. “Block-Coordinate Frank-Wolfe Optimization for Structural SVMs.” *In Proceedings of the 30th International Conference on Machine Learning, ICML 2013, Atlanta, GA, June 16–21 2013,* 53–61.
*   Lan, Guanghui. 2012. “An Optimal Method for Stochastic Composite Optimization.” *Mathematical Programming* 133 (1–2): 365–397.
*   Lan, Guanghui, and Yi Zhou. 2016. “Conditional Gradient Sliding for Convex Optimization.” *SIAM Journal on Optimization* 26 (2): 1379–1409.
*   Langford, John, and Tong Zhang. 2008. “The Epoch-Greedy Algorithm for Multi-armed Bandits with Side Information.” *In Advances in Neural Information Processing Systems,* 817–824.
*   Lattimore, Tor, and Csaba Szepesvári. 2020. *Bandit Algorithms.* Cambridge University Press.
*   Lee, J., B. Recht, R. Salakhutdinov, N. Srebro, and J. A. Tropp. 2010. “Practical Large-Scale Optimization for Max-Norm Regularization.” *NIPS,* 1297–1305.
*   Leistner, Christian, Amir Saffari, Peter M. Roth, and Horst Bischof. 2009. “On Robustness of On-line Boosting—A Competitive Study.” *In IEEE 12th International Conference on Computer Vision Workshops, ICCV Workshops,* 1362–1369. IEEE.
*   Littlestone, Nick. 1989. “From On-line to Batch Learning.” *In Proceedings of the Second Annual Workshop on Computational Learning Theory,* 269–284. COLT ’89. Santa Cruz, California.
*   Littlestone, Nick, and Manfred K. Warmuth. 1986. “Relating Data Compression and Learnability.”
*   Littlestone, N., and M. Warmuth. 1989. “The Weighted Majority Algorithm.” *Proceedings of the 30th Annual Symposium on the Foundations of Computer Science,* 256–261.
*   Littlestone, Nick, and Manfred K. Warmuth. 1994. “The Weighted Majority Algorithm.” *Information and Computation* 108 (2): 212–261.
*   Mannor, S., and N. Shimkin. 2003. “The Empirical Bayes Envelope and Regret Minimization in Competitive Markov Decision Processes.” *Mathematics of Operations Research* 28 (2): 327–345.
*   Mannor, S., and N. Shimkin. 2008. “Regret Minimization in Repeated Matrix Games with Variable Stage Duration.” *Games and Economic Behavior* 63 (1): 227–258.
*   Matousek, Jiri, and Bernd Gärtner. 2007. *Understanding and Using Linear Programming.* Springer Science & Business Media.
*   McMahan, H. Brendan, and Matthew J. Streeter. 2010. “Adaptive Bound Optimization for Online Convex Optimization.” *In COLT 2010—The 23rd Conference on Learning Theory, Haifa, Israel, June 27–29, 2010,* 244–256.
*   Minsky, Marvin, and Seymour Papert. 1969. *Perceptrons: An Introduction to Computational Geometry.* MIT Press.
*   Mokhtari, Aryan, Hamed Hassani, and Amin Karbasi. 2018. “Stochastic Conditional Gradient Methods: From Convex Minimization to Submodular Maximization.” *arXiv preprint arXiv:1804.09554.*
*   Moran, Shay, and Amir Yehudayoff. 2016. “Sample Compression Schemes for VC Classes.” *Journal of the ACM* 63 (3): 1–10.
*   Musco, Cameron, and Christopher Musco. 2015. “Randomized Block Krylov Methods for Stronger and Faster Approximate Singular Value Decomposition.” *Proceedings of the 28th International Conference on Neural Information Processing Systems—Volume 1,* 1396–1404.
*   Nemirovski, A. S. 2004. *Interior Point Polynomial Time Methods in Convex Programming. Lecture Notes*, 42 (16): 3215–3224.
*   Nemirovski, Arkadi S., and David B. Yudin. 1983. *Problem Complexity and Method Efficiency in Optimization.* John Wiley UK/USA.
*   Nesterov, Y. 2004. *Introductory Lectures on Convex Optimization: A Basic Course.* Applied Optimization. Springer.
*   Nesterov, Y. E., and A. S. Nemirovski. 1994. *Interior Point Polynomial Algorithms in Convex Programming.* SIAM.
*   Neu, Gergely, András György, Csaba Szepesvári, and András Antos. 2014. “Online Markov Decision Processes Under Bandit Feedback.” *IEEE Transactions on Automatic Control* 59 (3): 676–691. [http://dx.doi.org/10.1109/TAC.2013.2292137](http://dx.doi.org/10.1109/TAC.2013.2292137).
*   Olshen, Richard. 2001. “A Conversation with Leo Breiman.” *Statistical Science* 16 (2): 184–198.
*   Osborne, M. F. M. 1959. “Brownian Motion in the Stock Market.” *Operations Research* 2: 145–173.
*   Parikh, Neal, and Stephen Boyd. 2014. “Proximal Algorithms.” *Foundations and Trends in Optimization* 1 (3): 127–239.
*   Plotkin, Serge A., David B. Shmoys, and Éva Tardos. 1995. “Fast Approximation Algorithms for Fractional Packing and Covering Problems.” *Mathematics of Operations Research* 20 (2): 257–301.
*   Polyak, Boris T. 1987. *Introduction to Optimization.* Optimization Software.
*   Rakhlin, Alexander. 2009. *Lecture Notes on Online Learning.* University of California at Berkeley.
*   Rakhlin, Alexander, Ohad Shamir, and Karthik Sridharan. 2012. “Making Gradient Descent Optimal for Strongly Convex Stochastic Optimization.” *In Proceedings of the 29th International Conference on International Conference on Machine Learning,* 1571–1578.
*   Rakhlin, Alexander, and Karthik Sridharan. 2014. *Theory of Statistical Learning and Sequential Prediction.* Lecture Notes. University of Pennsylvania.
*   Rakhlin, Alexander, and Karthik Sridharan. 2016. “BISTRO: An Efficient Relaxation-Based Method for Contextual Bandits.” *ICML,* 1977–1985.
*   Rennie, Jasson D. M., and Nathan Srebro. 2005. “Fast Maximum Margin Matrix Factorization for Collaborative Prediction.” *In Proceedings of the 22nd International Conference on Machine Learning,* 713–719. ACM. [http://doi.acm.org/10.1145](http://doi.acm.org/10.1145/1102351.1102441) [/1102351.1102441](http://doi.acm.org/10.1145/1102351.1102441).
*   Riedel, Kurt. 1991. “A Sherman-Morrison-Woodbury Identity for Rank Augmenting Matrices with Application to Centering.” *SIAM Journal on Mathematical Analysis* 12, no. 1 (January): 80–95.
*   Robbins, Herbert. 1952. “Some Aspects of the Sequential Design of Experiments.” *Bulletin of the American Mathematical Society* 58 (5): 527–535.
*   Robbins, Herbert, and Sutton Monro. 1951. “A Stochastic Approximation Method.” *Annals of Mathematical Statistics* 22, no. 3 (September): 400–407. [http://dx.doi.org/10.1214/aoms/1177729586](http://dx.doi.org/10.1214/aoms/1177729586).
*   Rockafellar, R. T. 1997. *Convex Analysis.* Princeton University Press. http://books.google.co.il/books?id=1TiOka9bx3sC.
*   Rosenblatt, Frank. 1958. “The Perceptron: A Probabilistic Model for Information Storage and Organization in the Brain.” *Psychological Review* 65 (6): 386.
*   Roughgarden, Tim. 2015. “Intrinsic Robustness of the Price of Anarchy.” *Journal of the ACM* 62, no. 5 (November): 32: 1–32:42.
*   Salakhutdinov, R., and N. Srebro. 2010. “Collaborative Filtering in a Non-Uniform World: Learning with the Weighted Trace Norm.” *NIPS,* 2056–2064.
*   Schapire, Robert E. 1990. “The Strength of Weak Learnability.” *Machine Learning* 5, no. 2 (July): 197–227.
*   Schapire, R. E., and Y. Freund. 2012. Adaptive computation and machine learning. MIT Press. http://books.google.co.uk/books?id=blSReLACtToC.
*   Schölkopf, Bernhard, and Alexander J. Smola. 2002. *Learning with Kernels: Support Vector Machines, Regularization, Optimization, and Beyond.* MIT Press.
*   Shalev-Shwartz, Shai. 2007. “Online Learning: Theory, Algorithms, and Applications.” PhD diss., Hebrew University of Jerusalem.
*   Shalev-Shwartz, Shai. 2011. “Online Learning and Online Convex Optimization.” *Foundations and Trends in Machine Learning* 4 (2): 107–194.
*   Shalev-Shwartz, Shai, and Shai Ben-David. 2014. *Understanding Machine Learning: From Theory to Algorithms.* Cambridge University Press. doi:[10.1017/CBO9781107298019](http://dx.doi.org/10.1017/CBO9781107298019).
*   Shalev-Shwartz, Shai, Alon Gonen, and Ohad Shamir. 2011. “Large-Scale Convex Minimization with a Low-Rank Constraint.” *ICML,* 329–336.
*   Shalev-Shwartz, Shai, and Yoram Singer. 2007. “A Primal-Dual Perspective of Online Learning Algorithms.” *Machine Learning* 69 (2–3): 115–142.
*   Shalev-Shwartz, Shai, Yoram Singer, Nathan Srebro, and Andrew Cotter. 2011. “Pegasos: Primal Estimated Sub-gradient Solver for SVM.” *Mathematical Programming* 127 (1): 3–30.
*   Shamir, G. I., and N. Merhav. 2006. “Low-Complexity Sequential Lossless Coding for Piecewise-Stationary Memoryless Sources.” *IEEE Transactions on Information Theory* 45, no. 5 (September): 1498–1519. [http://dx.doi.org/10.1109/18.771150](http://dx.doi.org/10.1109/18.771150).
*   Shamir, Ohad. 2015. “On the Complexity of Bandit Linear Optimization.” *In Conference on Learning Theory PMLR,* 1523–1551.
*   Shamir, O., and S. Shalev-Shwartz. 2011. “Collaborative Filtering with the Trace Norm: Learning, Bounding, and Transducing.” *JMLR—Proceedings Track* 19: 661–678.
*   Shamir, Ohad, and Tong Zhang. 2013. “Stochastic Gradient Descent for Non-smooth Optimization: Convergence Results and Optimal Averaging Schemes.” *In International Conference on Machine Learning,* 71–79. PMLR.
*   Shimkin, Nahum. 2016. “An Online Convex Optimization Approach to Blackwell’s Approachability.” *Journal of Machine Learning Research* 17 (1): 4434–4456.
*   Singer, Yoram. 1998. “Switching Portfolios.” *UAI,* 488–495.
*   Srebro, Nathan. 2004. “Learning with Matrix Factorizations.” PhD diss., Massachusetts Institute of Technology.
*   Syrgkanis, Vasilis, Akshay Krishnamurthy, and Robert Schapire. 2016. “Efficient Algorithms for Adversarial Contextual Learning.” *International Conference on Machine Learning,* 2159–2168.
*   Syrgkanis, Vasilis, Haipeng Luo, Akshay Krishnamurthy, and Robert E Schapire. 2016. “Improved Regret Bounds for Oracle-Based Adversarial Contextual Bandits.” *Advances in Neural Information Processing Systems,* 3135–3143.
*   Tewari, Ambuj, Pradeep D. Ravikumar, and Inderjit S. Dhillon. 2011. “Greedy Algorithms for Structurally Constrained High Dimensional Problems.” *NIPS,* 882–890.
*   Tieleman, Tijmen, and Geoffrey Hinton. 2012. “Lecture 6.5-rmsprop: Divide the Gradient by a Running Average of Its Recent Magnitude.” *COURSERA: Neural Networks for Machine Learning* 4 (2): 26–31.
*   Valiant, L. G. 1984. “A Theory of the Learnable.” *Communications of the ACM* 27, no. 11 (November): 1134–1142.
*   van Erven, Tim, Peter D. Grünwald, Nishant A. Mehta, Mark D. Reid, and Robert C. Williamson. 2015. “Fast Rates in Statistical and Online Learning.” *Journal of Machine Learning Research* 16 (54): 1793–1861.
*   Vapnik, Vladimir N. 1998. *Statistical Learning Theory.* Wiley-Interscience.
*   von Neumann, John, and Oskar Morgenstern. 1944. *Theory of Games and Economic Behavior.* Princeton University Press.
*   Vovk, Volodimir G. 1990. “Aggregating Strategies.” *Proc. of Computational Learning Theory, 1990.*
*   Wang, Chu, Yingfei Wang, and Robert Schapire. 2015. “Functional Frank-Wolfe Boosting for General Loss Functions.” *arXiv preprint arXiv:1510.02558.*
*   Willems, F. M. J., and M. Krom. 1997. “Live-and-Die Coding for Binary Piecewise I.I.D. Sources.” *Proceedings of the 1997 IEEE International Symposium on Information Theory,* 68.
*   Xie, Jiahao, Zebang Shen, Chao Zhang, Hui Qian, and Boyu Wang. 2019. “Stochastic Recursive Gradient-Based Methods for Projection-Free Online Learning.” *arXiv preprint arXiv:1910.09396.*
*   Yu, J. Y., S. Mannor, and N. Shimkin. 2009. “Markov Decision Processes with Arbitrary Reward Processes.” *Mathematics of Operations Research* 34 (3): 737–757.
*   Yu, Jia Yuan, and Shie Mannor. 2009. “Arbitrarily Modulated Markov Decision Processes.” *Proceedings of the 48th IEEE Conference on Decision and Control,* 2946–2953.
*   Zhang, Lijun, Tie-Yan Liu, and Zhi-Hua Zhou. 2019. “Adaptive Regret of Convex and Smooth Functions.” *arXiv preprint arXiv:1904.11681.*
*   Zhang, Lijun, Tianbao Yang, and Zhi-Hua Zhou. 2018. “Dynamic regret of strongly adaptive methods.” *In International Conference on Machine Learning,* 5882–5891. PMLR.
*   Zhang, Tong. 2005. “Data-Dependent Concentration Bounds for Sequential Prediction Algorithms.” *In Proceedings of the 18th Annual Conference on Learning Theory,* 173–187. COLT’05. Bertinoro, Italy.
*   Zhou, Li. 2015. “A Survey on Contextual Multi-armed Bandits.” *arXiv preprint arXiv:1508.03326.*
*   Zinkevich, Martin. 2003. “Online Convex Programming and Generalized Infinitesimal Gradient Ascent.” *Proceedings of the 20th International Conference on Machine Learning,* 928–936.

# Index

*Page numbers in italics indicate a figure and page numbers in bold indicate a table on the corresponding page*.

*   Abernethy, Jacob, [61](#chapter_4.xhtml#pg_61), [87](#chapter_5.xhtml#pg_87), [106](#chapter_6.xhtml#pg_106), [189](#chapter_13.xhtml#pg_189)
*   AdaBoost algorithm, [168](#chapter_11.xhtml#pg_168), [170](#chapter_11.xhtml#pg_170)
*   AdaGrad (Adaptive subGradient method) algorithm
*   analysis of, [81–86](#chapter_5.xhtml#pg_81)
*   bibliographic remarks on, [87](#chapter_5.xhtml#pg_87)
*   diagonal, [82–83](#chapter_5.xhtml#pg_82)
*   full matrix, [82–83](#chapter_5.xhtml#pg_82)
*   regret bounds for, [83](#chapter_5.xhtml#pg_83)
*   Adaptive adversaries, [74–75](#chapter_5.xhtml#pg_74)
*   Adaptive gradient descent, [81–87](#chapter_5.xhtml#pg_81)
*   bibliographic remarks on, [87](#chapter_5.xhtml#pg_87)
*   in deep neural network training, [87](#chapter_5.xhtml#pg_87)
*   diagonal, [82–83](#chapter_5.xhtml#pg_82)
*   full matrix, [82–83](#chapter_5.xhtml#pg_82)
*   regret bounds for, [83](#chapter_5.xhtml#pg_83)
*   Adaptive regret
*   bibliographic remarks on, [160](#chapter_10.xhtml#pg_160)
*   definition of, [147](#chapter_10.xhtml#pg_147), [149–150](#chapter_10.xhtml#pg_149)
*   efficient adaptive regret for OCO, [153–155](#chapter_10.xhtml#pg_153)
*   weakly versus strongly adaptive algorithms, [150](#chapter_10.xhtml#pg_150)
*   Agarwal, Amit, [12](#chapter_1.xhtml#pg_12), [46](#chapter_3.xhtml#pg_46), [61](#chapter_4.xhtml#pg_61)
*   Agile online mirror descent (OMD), [69–70](#chapter_5.xhtml#pg_69)
*   Agnostic boosting, [165](#chapter_11.xhtml#pg_165), [170](#chapter_11.xhtml#pg_170)
*   Agnostic probably approximately correct (PAC) learning, [138–140](#chapter_9.xhtml#pg_138)
*   concentration in, [140–141](#chapter_9.xhtml#pg_140)
*   definition of, [137–138](#chapter_9.xhtml#pg_137)
*   martingales in, [140–143](#chapter_9.xhtml#pg_140), [150–151](#chapter_10.xhtml#pg_150)
*   reduction to online convex optimization, [138–140](#chapter_9.xhtml#pg_138)
*   Algorithm code listings. *See also Individual algorithms*
*   AdaBoost, [168](#chapter_11.xhtml#pg_168)
*   AdaGrad, [82](#chapter_5.xhtml#pg_82)
*   boosting for online convex optimization, [176](#chapter_12.xhtml#pg_176)
*   conditional gradient, [110](#chapter_7.xhtml#pg_110)
*   conditional gradient for matrix completion, [113](#chapter_7.xhtml#pg_113)
*   conversion of approachability algorithm to online convex optimization algorithm, [188](#chapter_13.xhtml#pg_188)
*   EXP3, simple version, [93](#chapter_6.xhtml#pg_93)
*   Exponentially Weighted Online Optimizer, [54](#chapter_4.xhtml#pg_54), [60–61](#chapter_4.xhtml#pg_60)
*   exponentiated gradient, [74](#chapter_5.xhtml#pg_74)
*   Fixed Share, [151](#chapter_10.xhtml#pg_151)
*   FKM algorithm, [99](#chapter_6.xhtml#pg_99)
*   Follow the Leading History, [154](#chapter_10.xhtml#pg_154)
*   Follow the Leading History, FLH2, [156](#chapter_10.xhtml#pg_156)
*   Follow the Leading History, simple version, [154](#chapter_10.xhtml#pg_154)
*   follow-the-perturbed-leader for convex losses, [76](#chapter_5.xhtml#pg_76)
*   follow-the-perturbed-leader for linear losses, [78](#chapter_5.xhtml#pg_78)
*   follow-the-perturbed-leader for prediction from expert advice, [79](#chapter_5.xhtml#pg_79)
*   gradient descent, basic template algorithm for unconstrained optimization, [19](#chapter_2.xhtml#pg_19)
*   gradient descent, reduction to nonsmooth functions, [29](#chapter_2.xhtml#pg_29)
*   gradient descent, reduction to smooth, nonstrongly convex functions, [28](#chapter_2.xhtml#pg_28)
*   gradient descent over constrained set, [25](#chapter_2.xhtml#pg_25)
*   gradient descent with Polyak stepsize, [21](#chapter_2.xhtml#pg_21)
*   Hedge algorithm, [11](#chapter_1.xhtml#pg_11)
*   linear program, simple, [130](#chapter_8.xhtml#pg_130)
*   MAB algorithm, simple, [91](#chapter_6.xhtml#pg_91)
*   online conditional gradient, [116](#chapter_7.xhtml#pg_116)
*   online convex optimization to approachability reduction, [185](#chapter_13.xhtml#pg_185)
*   online gradient descent, [38](#chapter_3.xhtml#pg_38)
*   online mirror descent, [69](#chapter_5.xhtml#pg_69)
*   online Newton step, [58](#chapter_4.xhtml#pg_58)
*   reduction from agnostic learning to online convex optimization, [139](#chapter_9.xhtml#pg_139)
*   reduction from boosting to online convex optimization, [166](#chapter_11.xhtml#pg_166)
*   reduction to bandit feedback, [95](#chapter_6.xhtml#pg_95)
*   Regularized Follow The Leader, [66](#chapter_5.xhtml#pg_66)
*   SCRIBLE algorithm, [103](#chapter_6.xhtml#pg_103)
*   stochastic gradient descent, [44](#chapter_3.xhtml#pg_44)
*   stochastic gradient descent for SVM training, [45](#chapter_3.xhtml#pg_45)
*   SVM training via subgradient descent, [33](#chapter_2.xhtml#pg_33)
*   Allen-Zhu, Zeyuan, [33](#chapter_2.xhtml#pg_33), [120](#chapter_7.xhtml#pg_120)
*   Alon, Noga, [145](#chapter_9.xhtml#pg_145)
*   Antos. András, [106](#chapter_6.xhtml#pg_106)
*   Approachability, Blackwell, [181–189](#chapter_13.xhtml#pg_181)
*   applications of, [189](#chapter_13.xhtml#pg_189)
*   assumptions and definitions in, [181–183](#chapter_13.xhtml#pg_181)
*   best response oracle, [189](#chapter_13.xhtml#pg_189)
*   Blackwell’s approachability theorem, [183](#chapter_13.xhtml#pg_183)
*   cones and polar cones, [186–187](#chapter_13.xhtml#pg_186)
*   equivalence to online convex optimization, [189](#chapter_13.xhtml#pg_189)
*   Euclidean distance to set and, [184](#chapter_13.xhtml#pg_184)
*   exercises for, [190](#chapter_13.xhtml#pg_190)
*   generalization in, [182–183](#chapter_13.xhtml#pg_182)
*   history of, [189](#chapter_13.xhtml#pg_189)
*   reduction from online convex optimization to, [183–186](#chapter_13.xhtml#pg_183)
*   reduction to online convex optimization, [186–189](#chapter_13.xhtml#pg_186)
*   vector values games and, [181–183](#chapter_13.xhtml#pg_181)
*   Approximation, stochastic. *See* [Stochastic gradient descent (SGD)](#index.xhtml#ind18)
*   Approximation, Taylor, [53](#chapter_4.xhtml#pg_53), [64](#chapter_5.xhtml#pg_64)
*   Arora, Sanjeev, [12](#chapter_1.xhtml#pg_12), [106](#chapter_6.xhtml#pg_106), [131](#chapter_8.xhtml#pg_131)
*   Article placement, personalized, [172–173](#chapter_12.xhtml#pg_172)
*   Audibert, Jean-Yves, [105](#chapter_6.xhtml#pg_105)
*   Auer, Peter, [105](#chapter_6.xhtml#pg_105), [106](#chapter_6.xhtml#pg_106)
*   Automated recommendation systems
*   conditional gradient for, [112–113](#chapter_7.xhtml#pg_112)
*   learning theory and, [137](#chapter_9.xhtml#pg_137)
*   linear optimization algorithms for, [114](#chapter_7.xhtml#pg_114)
*   matrix completion problem for, [108–109](#chapter_7.xhtml#pg_108)
*   Average regret, [37–38](#chapter_3.xhtml#pg_37)
*   Average sensitivity, [191n2](#chapter_1.xhtml#chapter1-2)
*   Awerbuch, Baruch, [12](#chapter_1.xhtml#pg_12), [105](#chapter_6.xhtml#pg_105)
*   Azoury, Katy S., [61](#chapter_4.xhtml#pg_61)
*   Azuma’s inequality, [141–142](#chapter_9.xhtml#pg_141), [152](#chapter_10.xhtml#pg_152)

*   Bachelier, Louis, [60](#chapter_4.xhtml#pg_60)
*   Bag-of-words representation, [4](#chapter_1.xhtml#pg_4), [136](#chapter_9.xhtml#pg_136)
*   Bandit convex optimization (BCO), [12](#chapter_1.xhtml#pg_12), [89–105](#chapter_6.xhtml#pg_89)
*   bandit linear optimization, [101–105](#chapter_6.xhtml#pg_101)
*   exercises for, [106](#chapter_6.xhtml#pg_106)
*   FKM algorithm, [99–101](#chapter_6.xhtml#pg_99), *[100](#chapter_6.xhtml#fig6-1)*
*   multiarmed bandit problem, [90–94](#chapter_6.xhtml#pg_90), [105–106](#chapter_6.xhtml#pg_105)
*   online gradient descent without a gradient, [99–101](#chapter_6.xhtml#pg_99), *[100](#chapter_6.xhtml#fig6-1)*
*   overview of, [89–90](#chapter_6.xhtml#pg_89)
*   protocol of, [89–90](#chapter_6.xhtml#pg_89)
*   reduction from limited information to full information, [94–99](#chapter_6.xhtml#pg_94)
*   Bandit linear optimization (BLO), [101–105](#chapter_6.xhtml#pg_101)
*   bibliographic remarks on, [105–106](#chapter_6.xhtml#pg_105)
*   near-optimal algorithm, [103–105](#chapter_6.xhtml#pg_103)
*   SCRIBLE algorithm, [103–105](#chapter_6.xhtml#pg_103)
*   self-concordant barrier functions, [102–103](#chapter_6.xhtml#pg_102), [106](#chapter_6.xhtml#pg_106)
*   Bartlett, Peter L., [189](#chapter_13.xhtml#pg_189)
*   Basic gradient descent (GD), [25–27](#chapter_2.xhtml#pg_25)
*   Ben-David, Shai, [145](#chapter_9.xhtml#pg_145)
*   Bengio, Yoshua, [87](#chapter_5.xhtml#pg_87)
*   Besbes, Omar, [159](#chapter_10.xhtml#pg_159)
*   Best response oracle, [189](#chapter_13.xhtml#pg_189)
*   Be-the-leader (BTL) algorithm, [191n1](#chapter_1.xhtml#chapter1-1)
*   Bibliographic remarks
*   boosting, [169–170](#chapter_11.xhtml#pg_169)
*   convex optimization, [33–34](#chapter_2.xhtml#pg_33)
*   first-order algorithms, [46](#chapter_3.xhtml#pg_46)
*   game theory, [131](#chapter_8.xhtml#pg_131)
*   learning in changing environments, [159–160](#chapter_10.xhtml#pg_159)
*   linear programming, [131](#chapter_8.xhtml#pg_131)
*   online boosting, [179–180](#chapter_12.xhtml#pg_179)
*   online convex optimization framework, [12](#chapter_1.xhtml#pg_12)
*   projection-free algorithms, [119–120](#chapter_7.xhtml#pg_119)
*   regularization, [86–87](#chapter_5.xhtml#pg_86)
*   statistical learning theory, [145](#chapter_9.xhtml#pg_145)
*   zero-sum games, [131](#chapter_8.xhtml#pg_131)
*   Binary classification, online boosting of, [172](#chapter_12.xhtml#pg_172)
*   Birkhoff–von Neumann (BVN) polytope, [115](#chapter_7.xhtml#pg_115)
*   Black, Fischer, [60](#chapter_4.xhtml#pg_60)
*   Blackwell, David, [181](#chapter_13.xhtml#pg_181), [189](#chapter_13.xhtml#pg_189)
*   Blackwell approachability, [181–189](#chapter_13.xhtml#pg_181)
*   applications of, [189](#chapter_13.xhtml#pg_189)
*   assumptions and definitions in, [181–183](#chapter_13.xhtml#pg_181)
*   best response oracle, [189](#chapter_13.xhtml#pg_189)
*   Blackwell’s approachability theorem, [183](#chapter_13.xhtml#pg_183)
*   cones and polar cones, [186–187](#chapter_13.xhtml#pg_186)
*   equivalence to online convex optimization, [189](#chapter_13.xhtml#pg_189)
*   Euclidean distance to set and, [184](#chapter_13.xhtml#pg_184)
*   exercises for, [190](#chapter_13.xhtml#pg_190)
*   generalization in, [182–183](#chapter_13.xhtml#pg_182)
*   history of, [189](#chapter_13.xhtml#pg_189)
*   reduction from online convex optimization to, [183–186](#chapter_13.xhtml#pg_183)
*   reduction to online convex optimization, [186–189](#chapter_13.xhtml#pg_186)
*   vector values games and, [181–183](#chapter_13.xhtml#pg_181)
*   Boosting, [163–170](#chapter_11.xhtml#pg_163)
*   AdaBoost, [168](#chapter_11.xhtml#pg_168), [170](#chapter_11.xhtml#pg_170)
*   agnostic, [165](#chapter_11.xhtml#pg_165), [170](#chapter_11.xhtml#pg_170)
*   assumptions and definitions in, [165–166](#chapter_11.xhtml#pg_165)
*   bibliographic remarks on, [169–170](#chapter_11.xhtml#pg_169)
*   boosting algorithm, [166–169](#chapter_11.xhtml#pg_166)
*   definition of, [163–164](#chapter_11.xhtml#pg_163)
*   exercises for, [170](#chapter_11.xhtml#pg_170)
*   generalization of, [168–169](#chapter_11.xhtml#pg_168)
*   gradient, [170](#chapter_11.xhtml#pg_170)
*   online, [171–180](#chapter_12.xhtml#pg_171) (*see also* [online boosting](#index.xhtml#ind11))
*   optical character recognition example, [163–164](#chapter_11.xhtml#pg_163), *[164](#chapter_11.xhtml#fig11-1)*
*   strong learnability, [164–165](#chapter_11.xhtml#pg_164)
*   weak learnability, [164–165](#chapter_11.xhtml#pg_164)
*   Borwein, J.M., [33](#chapter_2.xhtml#pg_33)
*   Boser, Bernhard E., [34](#chapter_2.xhtml#pg_34)
*   Bottou, Léon, [46](#chapter_3.xhtml#pg_46)
*   Bouneffouf, Djallel, [180](#chapter_12.xhtml#pg_180)
*   Bousquet, Olivier, [46](#chapter_3.xhtml#pg_46), [145](#chapter_9.xhtml#pg_145)
*   Boyd, S., [33](#chapter_2.xhtml#pg_33)
*   Bregman divergence, [18](#chapter_2.xhtml#pg_18), [64–65](#chapter_5.xhtml#pg_64), [68](#chapter_5.xhtml#pg_68), [71–72](#chapter_5.xhtml#pg_71)
*   Breiman, Leo, [169](#chapter_11.xhtml#pg_169)
*   Brukhim, Nataly, [170](#chapter_11.xhtml#pg_170), [179](#chapter_12.xhtml#pg_179)
*   Bubeck, Sébastien, [33](#chapter_2.xhtml#pg_33), [46](#chapter_3.xhtml#pg_46), [105](#chapter_6.xhtml#pg_105)

*   Cauchy-Schwarz inequality, [64](#chapter_5.xhtml#pg_64), [68](#chapter_5.xhtml#pg_68), [72](#chapter_5.xhtml#pg_72), [76–77](#chapter_5.xhtml#pg_76), [80](#chapter_5.xhtml#pg_80), [104](#chapter_6.xhtml#pg_104), [117](#chapter_7.xhtml#pg_117)
*   Cesa-Bianchi, Nicolò, [61](#chapter_4.xhtml#pg_61), [105](#chapter_6.xhtml#pg_105)
*   Changing environments, learning in, [147–161](#chapter_10.xhtml#pg_147)
*   adaptive regret, [147](#chapter_10.xhtml#pg_147), [149–150](#chapter_10.xhtml#pg_149), [153–155](#chapter_10.xhtml#pg_153), [160](#chapter_10.xhtml#pg_160)
*   bibliographic remarks on, [159–160](#chapter_10.xhtml#pg_159)
*   computationally efficient methods, [155–159](#chapter_10.xhtml#pg_155)
*   dynamic regret, [148–149](#chapter_10.xhtml#pg_148)
*   exercises for, [160–161](#chapter_10.xhtml#pg_160)
*   Fixed Share algorithm, [151–153](#chapter_10.xhtml#pg_151), [160](#chapter_10.xhtml#pg_160)
*   FLH (Follow the Leading History) algorithm, [153–155](#chapter_10.xhtml#pg_153), [160](#chapter_10.xhtml#pg_160)
*   FLH2 algorithm, [155–159](#chapter_10.xhtml#pg_155)
*   overview of, [147](#chapter_10.xhtml#pg_147)
*   pruning method, [159](#chapter_10.xhtml#pg_159)
*   tracking the best expert in, [151–153](#chapter_10.xhtml#pg_151)
*   Chebychev’s inequality, [141](#chapter_9.xhtml#pg_141)
*   Chervonenkis, Alexey, [138](#chapter_9.xhtml#pg_138)
*   Classes, hypothesis, [136–137](#chapter_9.xhtml#pg_136). *See also* [Boosting](#index.xhtml#ind1)
*   Complexity, sample, [137–139](#chapter_9.xhtml#pg_137), [144](#chapter_9.xhtml#pg_144), [146](#chapter_9.xhtml#pg_146), [169](#chapter_11.xhtml#pg_169)
*   Compression, learning theory and, [143–144](#chapter_9.xhtml#pg_143)
*   Computationally efficient methods, [155–159](#chapter_10.xhtml#pg_155)
*   Concentration, in agnostic PAC learning, [141](#chapter_9.xhtml#pg_141)
*   Concepts, definition of, [133](#chapter_9.xhtml#pg_133). *See also* [Learning theory](#index.xhtml#ind9)
*   Conditional gradient (CG) method, [110–113](#chapter_7.xhtml#pg_110)
*   basic algorithm, [110–112](#chapter_7.xhtml#pg_110)
*   compared to other gradient-based methods, [113](#chapter_7.xhtml#pg_113)
*   conceptual illustration of, *[111](#chapter_7.xhtml#fig7-1)*
*   matrix completion example of, [112–113](#chapter_7.xhtml#pg_112)
*   online conditional gradient algorithm, [116–120](#chapter_7.xhtml#pg_116)
*   Condition number of*f*, [16](#chapter_2.xhtml#pg_16), [34](#chapter_2.xhtml#pg_34)
*   Conditions
*   Karush-Kuhn-Tucker (KKT), [18](#chapter_2.xhtml#pg_18)
*   optimality, [18](#chapter_2.xhtml#pg_18), *[19](#chapter_2.xhtml#fig2-3)*
*   Cones, [186–187](#chapter_13.xhtml#pg_186)
*   Constant rebalancing portfolios, [6](#chapter_1.xhtml#pg_6), [51–52](#chapter_4.xhtml#pg_51)
*   Constant variance, [106](#chapter_6.xhtml#pg_106)
*   Constrained gradient/subgradient descent, [25–27](#chapter_2.xhtml#pg_25)
*   Contextual learning model, [173–174](#chapter_12.xhtml#pg_173)
*   Convergence, linear, [25–27](#chapter_2.xhtml#pg_25)
*   Convergence rates, [20](#chapter_2.xhtml#pg_20), **[21](#chapter_2.xhtml#tab2-1)**
*   Convex cost functions. *See* [Cost functions](#index.xhtml#ind4)
*   Convexity of *f*, [44](#chapter_3.xhtml#pg_44)
*   Convex losses, perturbation for, [75–78](#chapter_5.xhtml#pg_75), [86](#chapter_5.xhtml#pg_86)
*   Convex loss function. *See also* [Strongly convex, nonsmooth functions](#index.xhtml#ind19)
*   Fixed Share algorithm, [151](#chapter_10.xhtml#pg_151)
*   Follow the Leading History algorithm, [153](#chapter_10.xhtml#pg_153)
*   hinge loss, [32](#chapter_2.xhtml#pg_32), *[32](#chapter_2.xhtml#fig2-4)*
*   matrix completion and recommendation systems, [7](#chapter_1.xhtml#pg_7)
*   online spam filtering, [4](#chapter_1.xhtml#pg_4)
*   statistical learning theory and, [134](#chapter_9.xhtml#pg_134)
*   Convex optimization, basic concepts in
*   bibliographic remarks on, [33–34](#chapter_2.xhtml#pg_33)
*   definitions and setup, [15–16](#chapter_2.xhtml#pg_15)
*   gradient descent. *See* [gradient descent (GD)](#index.xhtml#ind8)
*   optimality conditions, [18](#chapter_2.xhtml#pg_18), *[19](#chapter_2.xhtml#fig2-3)*
*   projections onto convex sets, [16–18](#chapter_2.xhtml#pg_16)
*   reduction to general convex functions, [31](#chapter_2.xhtml#pg_31)
*   reduction to smooth, nonstrongly convex functions, [27–28](#chapter_2.xhtml#pg_27)
*   reduction to strongly convex, nonsmooth functions, [28–31](#chapter_2.xhtml#pg_28)
*   support vector machine training example, [31–33](#chapter_2.xhtml#pg_31)
*   Convex sets
*   definition of, [15](#chapter_2.xhtml#pg_15)
*   projections onto, [16–18](#chapter_2.xhtml#pg_16)
*   Cortes, Corinna, [34](#chapter_2.xhtml#pg_34)
*   Cost functions
*   for adaptive gradient descent, [81–82](#chapter_5.xhtml#pg_81)
*   for bandit convex optimization, [89–90](#chapter_6.xhtml#pg_89)
*   for bandit linear optimization, [101](#chapter_6.xhtml#pg_101), [105](#chapter_6.xhtml#pg_105), [106](#chapter_6.xhtml#pg_106)
*   for Blackwell approachability, [188](#chapter_13.xhtml#pg_188), [189](#chapter_13.xhtml#pg_189)
*   for follow-the-perturbed-leader for prediction from expert advice, [78](#chapter_5.xhtml#pg_78)
*   for lazy-OMD algorithms, [70](#chapter_5.xhtml#pg_70)
*   for multiarmed bandit problem, [90](#chapter_6.xhtml#pg_90)
*   oblivious vs. adaptive adversaries and, [74–75](#chapter_5.xhtml#pg_74)
*   for online conditional gradient algorithm, [116–117](#chapter_7.xhtml#pg_116)
*   in online convex optimization framework, [2–3](#chapter_1.xhtml#pg_2)
*   for online gradient descent, [38](#chapter_3.xhtml#pg_38), [41–42](#chapter_3.xhtml#pg_41), [45](#chapter_3.xhtml#pg_45), [99–100](#chapter_6.xhtml#pg_99)
*   for online Newton step algorithm, [55](#chapter_4.xhtml#pg_55)
*   for online spam filtering model, [4](#chapter_1.xhtml#pg_4)
*   perturbation for, [78](#chapter_5.xhtml#pg_78)
*   for prediction from expert advice, [3–4](#chapter_1.xhtml#pg_3)
*   in proof of von Neumann’s theorem, [129–130](#chapter_8.xhtml#pg_129)
*   for reduction from boosting to online convex optimization, [166](#chapter_11.xhtml#pg_166)
*   for reduction from limited information to full information, [94](#chapter_6.xhtml#pg_94)
*   for Regularized Follow The Leader algorithm, [65–66](#chapter_5.xhtml#pg_65), [70](#chapter_5.xhtml#pg_70)
*   Courville, Aaron, [87](#chapter_5.xhtml#pg_87)
*   Cover, Thomas, [12](#chapter_1.xhtml#pg_12), [60](#chapter_4.xhtml#pg_60)

*   Dani, Varsha, [105](#chapter_6.xhtml#pg_105)
*   Daniely, Amit, [160](#chapter_10.xhtml#pg_160)
*   Dantzig, George B., [123](#chapter_8.xhtml#pg_123), [131](#chapter_8.xhtml#pg_131)
*   Data streaming, [156–157](#chapter_10.xhtml#pg_156), [160](#chapter_10.xhtml#pg_160)
*   David, Ofir, [145](#chapter_9.xhtml#pg_145)
*   Decision-making problems. *See also* [Portfolio selection](#index.xhtml#ind12); [Prediction from expert advice](#index.xhtml#ind13)
*   matrix completion and recommendation systems, [6–7](#chapter_1.xhtml#pg_6), [110–113](#chapter_7.xhtml#pg_110), [137](#chapter_9.xhtml#pg_137)
*   online shortest paths, [5](#chapter_1.xhtml#pg_5), *[5](#chapter_1.xhtml#fig1-1)*, [12](#chapter_1.xhtml#pg_12)
*   online spam filtering, [4](#chapter_1.xhtml#pg_4)
*   portfolio selection, [5–6](#chapter_1.xhtml#pg_5)
*   Deep neural networks, adaptive regularization in, [87](#chapter_5.xhtml#pg_87)
*   Dekel, Ofer, [106](#chapter_6.xhtml#pg_106)
*   DeMarzo, Peter, [61](#chapter_4.xhtml#pg_61)
*   Deterministic strongly convex regularization, [87](#chapter_5.xhtml#pg_87)
*   Diagonal AdaGrad (Adaptive subGradient method) algorithm, [81–86](#chapter_5.xhtml#pg_81)
*   Dijkstra’s algorithm, [115](#chapter_7.xhtml#pg_115)
*   Dikin ellipsoid, [102](#chapter_6.xhtml#pg_102), [103](#chapter_6.xhtml#pg_103)
*   Distance to optimality, measurement of, [21–23](#chapter_2.xhtml#pg_21), [174](#chapter_12.xhtml#pg_174), [182](#chapter_13.xhtml#pg_182)
*   Divergence, Bregman, [64–65](#chapter_5.xhtml#pg_64), [68](#chapter_5.xhtml#pg_68), [71–72](#chapter_5.xhtml#pg_71)
*   Duality
*   approximation of linear programs, [130–131](#chapter_8.xhtml#pg_130)
*   duality theorem, [124–125](#chapter_8.xhtml#pg_124)
*   strong, [128–130](#chapter_8.xhtml#pg_128)
*   von Neumann minimax theorem equivalence to, [127–128](#chapter_8.xhtml#pg_127)
*   weak, [128](#chapter_8.xhtml#pg_128)
*   Dual norms, in regularization functions, [64](#chapter_5.xhtml#pg_64)
*   Duchi, J. C., [87](#chapter_5.xhtml#pg_87)
*   Dynamic regret, [148–149](#chapter_10.xhtml#pg_148)

*   Efficient adaptive regret, [153–155](#chapter_10.xhtml#pg_153)
*   Efficiently learnable hypothesis classes, [143](#chapter_9.xhtml#pg_143)
*   Eigenvector computation, [113–114](#chapter_7.xhtml#pg_113), [120–121](#chapter_7.xhtml#pg_120). *See also* [Conditional gradient (CG) method](#index.xhtml#ind3)
*   Eldan, Ronen, [105](#chapter_6.xhtml#pg_105)
*   Ellipsoidal-sampling estimator, [98–99](#chapter_6.xhtml#pg_98)
*   Email, online spam filtering for, [4](#chapter_1.xhtml#pg_4)
*   Environments, changing. *See* [Changing environments, learning in](#index.xhtml#ind2)
*   Equilibria, zero-sum games and, [125–127](#chapter_8.xhtml#pg_125), **[125](#chapter_8.xhtml#tab8-1)**
*   Erdos, Paul, [145](#chapter_9.xhtml#pg_145)
*   Errors, generalization, [134–135](#chapter_9.xhtml#pg_134), [137](#chapter_9.xhtml#pg_137), [139](#chapter_9.xhtml#pg_139), [144](#chapter_9.xhtml#pg_144), [145](#chapter_9.xhtml#pg_145), [169](#chapter_11.xhtml#pg_169)
*   Estimators
*   ellipsoidal-sampling, [98–99](#chapter_6.xhtml#pg_98)
*   pointwise gradient, [96–97](#chapter_6.xhtml#pg_96)
*   sphere-sampling, [97–98](#chapter_6.xhtml#pg_97)
*   unbiased, [95–96](#chapter_6.xhtml#pg_95)
*   Euclidean distance to optimality, [21–23](#chapter_2.xhtml#pg_21), [174](#chapter_12.xhtml#pg_174), [182](#chapter_13.xhtml#pg_182)
*   Euclidean distance to set, [174](#chapter_12.xhtml#pg_174), [184](#chapter_13.xhtml#pg_184)
*   Even-Dar, E., [106](#chapter_6.xhtml#pg_106), [131](#chapter_8.xhtml#pg_131)
*   Exercises
*   bandit convex optimization, [106](#chapter_6.xhtml#pg_106)
*   basic concepts in convex optimization, [34–35](#chapter_2.xhtml#pg_34)
*   Blackwell approachability, [190](#chapter_13.xhtml#pg_190)
*   boosting, [170](#chapter_11.xhtml#pg_170)
*   experts problem, [13](#chapter_1.xhtml#pg_13)
*   first-order algorithms, [46–47](#chapter_3.xhtml#pg_46)
*   learning in changing environments, [160–161](#chapter_10.xhtml#pg_160)
*   learning theory, [145–146](#chapter_9.xhtml#pg_145)
*   online boosting, [180](#chapter_12.xhtml#pg_180)
*   projection-free algorithms, [120–121](#chapter_7.xhtml#pg_120)
*   regularization, [87–88](#chapter_5.xhtml#pg_87)
*   second-order methods, [61–62](#chapter_4.xhtml#pg_61)
*   statistical learning theory, [145–146](#chapter_9.xhtml#pg_145)
*   EXP3 algorithm, [93–94](#chapter_6.xhtml#pg_93), [105](#chapter_6.xhtml#pg_105)
*   Exp-concave functions, [52–53](#chapter_4.xhtml#pg_52), [61](#chapter_4.xhtml#pg_61)
*   Fixed Share algorithm, [151–153](#chapter_10.xhtml#pg_151), [160](#chapter_10.xhtml#pg_160)
*   FLH (Follow the Leading History) algorithm, [153–155](#chapter_10.xhtml#pg_153), [160](#chapter_10.xhtml#pg_160)
*   FLH2 algorithm, [155–159](#chapter_10.xhtml#pg_155)
*   regret rates, [37–38](#chapter_3.xhtml#pg_37)
*   Expectations, linearity property of, [135–136](#chapter_9.xhtml#pg_135)
*   Experts problem
*   bibliographic remarks on, [12](#chapter_1.xhtml#pg_12)
*   exercises for, [13](#chapter_1.xhtml#pg_13)
*   expected number of mistakes of any algorithm, [7–8](#chapter_1.xhtml#pg_7)
*   Hedge algorithm, [11–12](#chapter_1.xhtml#pg_11)
*   importance in machine learning, [3–4](#chapter_1.xhtml#pg_3)
*   large pool of experts in, [171–173](#chapter_12.xhtml#pg_171)
*   nature of problem, [3–4](#chapter_1.xhtml#pg_3)
*   perturbation for, [79–81](#chapter_5.xhtml#pg_79)
*   pruning experts, [159](#chapter_10.xhtml#pg_159)
*   randomized weighted majority algorithm, [10](#chapter_1.xhtml#pg_10)
*   relative performance metrics, [7–8](#chapter_1.xhtml#pg_7)
*   tracking the best expert, [151–153](#chapter_10.xhtml#pg_151)
*   weighted majority algorithm, [8–9](#chapter_1.xhtml#pg_8), [12](#chapter_1.xhtml#pg_12)
*   working set of experts in, [156–157](#chapter_10.xhtml#pg_156), *[157](#chapter_10.xhtml#fig10-1)*
*   Exploration-exploitation tradeoff, in multiarmed bandit (MAB) problem
*   separate exploration and exploitation, [90–93](#chapter_6.xhtml#pg_90)
*   simultaneous exploration and exploitation, [93–94](#chapter_6.xhtml#pg_93)
*   Exponentially Weighted Online Optimizer (EWOO), [53–55](#chapter_4.xhtml#pg_53), [60–61](#chapter_4.xhtml#pg_60)
*   Exponentiated gradient algorithm, [74](#chapter_5.xhtml#pg_74)
*   Extension operator, [174–175](#chapter_12.xhtml#pg_174)

*   Fictitious play, [63](#chapter_5.xhtml#pg_63)
*   Finite hypothesis classes, [138](#chapter_9.xhtml#pg_138)
*   First-order algorithms
*   bibliographic remarks on, [46](#chapter_3.xhtml#pg_46)
*   exercises for, [46–47](#chapter_3.xhtml#pg_46)
*   goal of, [37–38](#chapter_3.xhtml#pg_37)
*   logarithmic regret, [41–43](#chapter_3.xhtml#pg_41)
*   lower bounds, [40–41](#chapter_3.xhtml#pg_40)
*   online gradient descent, [38–40](#chapter_3.xhtml#pg_38), *[39](#chapter_3.xhtml#fig3-1)*
*   stochastic gradient descent, [43–46](#chapter_3.xhtml#pg_43)
*   Fixed rebalanced portfolios, [52](#chapter_4.xhtml#pg_52)
*   Fixed Share algorithm, [151–153](#chapter_10.xhtml#pg_151), [160](#chapter_10.xhtml#pg_160)
*   FKM algorithm, [99–101](#chapter_6.xhtml#pg_99), *[100](#chapter_6.xhtml#fig6-1)*
*   Flaxman, Abraham, [105](#chapter_6.xhtml#pg_105)
*   Flow polytope, [5](#chapter_1.xhtml#pg_5), *[5](#chapter_1.xhtml#fig1-1)*, [25](#chapter_2.xhtml#pg_25), [106](#chapter_6.xhtml#pg_106)
*   Follow the Leader (FTL) strategy, [63](#chapter_5.xhtml#pg_63), [86](#chapter_5.xhtml#pg_86)
*   Follow-the-leader versus be-the-leader (FTL-BTL), [191n1](#chapter_1.xhtml#chapter1-1)
*   Follow the Leading History
*   FLH algorithm, [153–155](#chapter_10.xhtml#pg_153), [160](#chapter_10.xhtml#pg_160)
*   FLH2 algorithm, [155–159](#chapter_10.xhtml#pg_155)
*   pruning method, [159](#chapter_10.xhtml#pg_159)
*   Follow-the-perturbed-leader
*   for convex losses, [75–78](#chapter_5.xhtml#pg_75), [86](#chapter_5.xhtml#pg_86)
*   for expert advice, [79–81](#chapter_5.xhtml#pg_79)
*   Frank, M., [119](#chapter_7.xhtml#pg_119)
*   Frank-Wolfe algorithm, [110–113](#chapter_7.xhtml#pg_110), [179](#chapter_12.xhtml#pg_179)
*   basic algorithm, [110–112](#chapter_7.xhtml#pg_110)
*   bibliographic remarks on, [119–120](#chapter_7.xhtml#pg_119)
*   comparison to other gradient-based methods, [113](#chapter_7.xhtml#pg_113)
*   conceptual illustration of, *[111](#chapter_7.xhtml#fig7-1)*
*   matrix completion example of, [112–113](#chapter_7.xhtml#pg_112)
*   online boosting method compared to, [175–179](#chapter_12.xhtml#pg_175)
*   Freund, Yoav, [12](#chapter_1.xhtml#pg_12), [105](#chapter_6.xhtml#pg_105), [123](#chapter_8.xhtml#pg_123), [131](#chapter_8.xhtml#pg_131), [169](#chapter_11.xhtml#pg_169), [179](#chapter_12.xhtml#pg_179)
*   Friedman, Jerome H., [179](#chapter_12.xhtml#pg_179)
*   Frongillo, Rafael M, [61](#chapter_4.xhtml#pg_61)
*   Full information, reduction from limited information to, [94–99](#chapter_6.xhtml#pg_94)
*   ellipsoidal-sampling estimator, [98–99](#chapter_6.xhtml#pg_98)
*   pointwise gradient estimators, [96–97](#chapter_6.xhtml#pg_96)
*   sphere-sampling estimator, [97–98](#chapter_6.xhtml#pg_97)
*   unbiased estimators, [95–96](#chapter_6.xhtml#pg_95)
*   Full matrix AdaGrad (Adaptive subGradient method) algorithm, [83](#chapter_5.xhtml#pg_83)
*   Functions, reductions to. *See also* [Smooth, nonstrongly convex functions](#index.xhtml#ind17); [Strongly convex, nonsmooth functions](#index.xhtml#ind19)
*   general convex functions, [31](#chapter_2.xhtml#pg_31)
*   smooth, nonstrongly convex functions, [27–28](#chapter_2.xhtml#pg_27)
*   strongly convex, nonsmooth functions, [28–31](#chapter_2.xhtml#pg_28)

*   Game theory. *See also* [Linear programming (LP) duality](#index.xhtml#ind10)
*   approximation of linear programs, [130–131](#chapter_8.xhtml#pg_130)
*   bibliographic remarks on, [131](#chapter_8.xhtml#pg_131)
*   equivalence of von Neumann theorem and LP duality, [127–128](#chapter_8.xhtml#pg_127)
*   history of, [123–124](#chapter_8.xhtml#pg_123)
*   von Neumann minimax theorem, [127–130](#chapter_8.xhtml#pg_127)
*   zero-sum games, [123–131](#chapter_8.xhtml#pg_123), **[125](#chapter_8.xhtml#tab8-1)**, [181–182](#chapter_13.xhtml#pg_181), [185](#chapter_13.xhtml#pg_185)
*   Garber, Dan, [120](#chapter_7.xhtml#pg_120)
*   General convex functions, reduction to, [31](#chapter_2.xhtml#pg_31)
*   Generalization error, [134–135](#chapter_9.xhtml#pg_134), [137](#chapter_9.xhtml#pg_137), [139](#chapter_9.xhtml#pg_139), [144](#chapter_9.xhtml#pg_144), [145](#chapter_9.xhtml#pg_145), [169](#chapter_11.xhtml#pg_169)
*   Geometric Brownian motion (GBM) model, [5](#chapter_1.xhtml#pg_5), [12](#chapter_1.xhtml#pg_12), [49](#chapter_4.xhtml#pg_49), [60](#chapter_4.xhtml#pg_60)
*   Gilliland, Dennis, [189](#chapter_13.xhtml#pg_189)
*   Gonen, Alon, [160](#chapter_10.xhtml#pg_160)
*   Goodfellow, Ian, [87](#chapter_5.xhtml#pg_87)
*   Gottlieb, Lee-Ad, [145](#chapter_9.xhtml#pg_145)
*   Gradient boosting, [170](#chapter_11.xhtml#pg_170)
*   Gradient descent (GD), [19–25](#chapter_2.xhtml#pg_19)
*   adaptive, [81–87](#chapter_5.xhtml#pg_81)
*   basic template algorithm for unconstrained optimization, [19–20](#chapter_2.xhtml#pg_19)
*   constrained, [25–27](#chapter_2.xhtml#pg_25)
*   convergence rates for, [20](#chapter_2.xhtml#pg_20), **[21](#chapter_2.xhtml#tab2-1)**
*   exponentiated gradient algorithm, [74](#chapter_5.xhtml#pg_74)
*   iterates of, *[20](#chapter_2.xhtml#tab2-1)*
*   online gradient descent, [38–43](#chapter_3.xhtml#pg_38), *[39](#chapter_3.xhtml#fig3-1)*, [72–73](#chapter_5.xhtml#pg_72)
*   online mirror descent, [69–72](#chapter_5.xhtml#pg_69)
*   stochastic, [43–46](#chapter_3.xhtml#pg_43)
*   subgradients, [16](#chapter_2.xhtml#pg_16), [25–27](#chapter_2.xhtml#pg_25), [31–33](#chapter_2.xhtml#pg_31)
*   success in training deep neural networks, [87](#chapter_5.xhtml#pg_87)
*   support vector machine (SVM) training example, [31–33](#chapter_2.xhtml#pg_31)
*   Grigas, Paul, [179](#chapter_12.xhtml#pg_179)
*   Grove, A., [86](#chapter_5.xhtml#pg_86)
*   Gupta, Vineet, [87](#chapter_5.xhtml#pg_87)
*   Gur, Yonatan, [159](#chapter_10.xhtml#pg_159)
*   Guyon, Isabelle M., [34](#chapter_2.xhtml#pg_34)
*   György, András, [106](#chapter_6.xhtml#pg_106), [160](#chapter_10.xhtml#pg_160)

*   Hannan, James, [86](#chapter_5.xhtml#pg_86), [181](#chapter_13.xhtml#pg_181), [189](#chapter_13.xhtml#pg_189)
*   Hanneke, Steve, [145](#chapter_9.xhtml#pg_145)
*   Hart, Sergiu, [131](#chapter_8.xhtml#pg_131)
*   Hayes, Thomas, [105](#chapter_6.xhtml#pg_105)
*   Hedge algorithm
*   EXP3 regret algorithm and, [94](#chapter_6.xhtml#pg_94)
*   experts problem and, [11–12](#chapter_1.xhtml#pg_11), [53](#chapter_4.xhtml#pg_53)
*   online boosting and, [171](#chapter_12.xhtml#pg_171), [172](#chapter_12.xhtml#pg_172)
*   Herbster, Mark, [159](#chapter_10.xhtml#pg_159)
*   Hessian, [16](#chapter_2.xhtml#pg_16), [52](#chapter_4.xhtml#pg_52), [64](#chapter_5.xhtml#pg_64), [102–103](#chapter_6.xhtml#pg_102) Hinge loss function, [32](#chapter_2.xhtml#pg_32), *[32](#chapter_2.xhtml#fig2-4)*
*   Hoeffding-Chernoff lemma, [141–142](#chapter_9.xhtml#pg_141)
*   Hypotheses. *See also* [Boosting](#index.xhtml#ind1)
*   efficiently learnable hypothesis classes, [143](#chapter_9.xhtml#pg_143)
*   finite, [138](#chapter_9.xhtml#pg_138)
*   learning problems and, [136–137](#chapter_9.xhtml#pg_136)
*   properly learnable versus improperly learnable, [138](#chapter_9.xhtml#pg_138)

*   Induction base
*   conditional gradient method, [112](#chapter_7.xhtml#pg_112)
*   Regularized Follow The Leader algorithm, [67](#chapter_5.xhtml#pg_67)
*   Induction step
*   conditional gradient method, [112](#chapter_7.xhtml#pg_112)
*   Regularized Follow The Leader algorithm, [67–68](#chapter_5.xhtml#pg_67)
*   Inequality
*   Azuma’s, [141–142](#chapter_9.xhtml#pg_141)
*   Cauchy-Schwarz, [64](#chapter_5.xhtml#pg_64), [68](#chapter_5.xhtml#pg_68), [72](#chapter_5.xhtml#pg_72), [76–77](#chapter_5.xhtml#pg_76), [80](#chapter_5.xhtml#pg_80), [104](#chapter_6.xhtml#pg_104), [117](#chapter_7.xhtml#pg_117)
*   Chebychev’s, [141](#chapter_9.xhtml#pg_141)
*   Jensen’s, [15](#chapter_2.xhtml#pg_15), [30](#chapter_2.xhtml#pg_30), [37](#chapter_3.xhtml#pg_37)
*   Markov’s, [135–136](#chapter_9.xhtml#pg_135)
*   Inverse Hessian, [55](#chapter_4.xhtml#pg_55), [64](#chapter_5.xhtml#pg_64)
*   Iterative algorithms, online mirror descent, [69–72](#chapter_5.xhtml#pg_69)
*   Iterative methods, [19](#chapter_2.xhtml#pg_19). *See also* [Gradient descent (GD)](#index.xhtml#ind8)

*   Jensen’s inequality, [15](#chapter_2.xhtml#pg_15), [30](#chapter_2.xhtml#pg_30), [37](#chapter_3.xhtml#pg_37)

*   Kakade, Sham, [105](#chapter_6.xhtml#pg_105), [106](#chapter_6.xhtml#pg_106)
*   Kalai, Adam, [12](#chapter_1.xhtml#pg_12), [61](#chapter_4.xhtml#pg_61), [86](#chapter_5.xhtml#pg_86), [105](#chapter_6.xhtml#pg_105), [169](#chapter_11.xhtml#pg_169), [191n1](#chapter_1.xhtml#chapter1-1)
*   Kale, Satyen, [12](#chapter_1.xhtml#pg_12), [46](#chapter_3.xhtml#pg_46), [61](#chapter_4.xhtml#pg_61), [87](#chapter_5.xhtml#pg_87), [120](#chapter_7.xhtml#pg_120), [131](#chapter_8.xhtml#pg_131)
*   Kanade, Varun, [169](#chapter_11.xhtml#pg_169)
*   Kantorovich, L.V., [131](#chapter_8.xhtml#pg_131)
*   Karush-Kuhn-Tucker (KKT) conditions, [18](#chapter_2.xhtml#pg_18)
*   Kearns, Michael J., [145](#chapter_9.xhtml#pg_145)
*   Kivinen, Jyrki, [46](#chapter_3.xhtml#pg_46), [61](#chapter_4.xhtml#pg_61), [86](#chapter_5.xhtml#pg_86)
*   KKT (Karush-Kuhn-Tucker) conditions, [18](#chapter_2.xhtml#pg_18)
*   Kleinberg, Robert, [12](#chapter_1.xhtml#pg_12), [105](#chapter_6.xhtml#pg_105)
*   Kontorovich, Aryeh, [145](#chapter_9.xhtml#pg_145)
*   Koren, Tomer, [87](#chapter_5.xhtml#pg_87)
*   Kozat, S.S., [160](#chapter_10.xhtml#pg_160)
*   Kremer, Ilan, [61](#chapter_4.xhtml#pg_61)
*   Kuczyński, Jacek, [120](#chapter_7.xhtml#pg_120)

*   Lagrangian relaxation techniques, [131](#chapter_8.xhtml#pg_131)
*   Lan, Guanghui, [46](#chapter_3.xhtml#pg_46)
*   Lanczos method, [120](#chapter_7.xhtml#pg_120)
*   Langford, John, [179](#chapter_12.xhtml#pg_179)
*   Lattimore, Tor, [106](#chapter_6.xhtml#pg_106)
*   Lazy online mirror descent (OMD), [69–70](#chapter_5.xhtml#pg_69)
*   Learning from expert advice. *See* [Experts problem](#index.xhtml#ind6)
*   Learning theory, [133–138](#chapter_9.xhtml#pg_133). *See also* [Changing environments, learning in](#index.xhtml#ind2); [Experts problem](#index.xhtml#ind6)
*   agnostic probably approximately correct learning, [137–143](#chapter_9.xhtml#pg_137)
*   bibliographic remarks on, [145](#chapter_9.xhtml#pg_145)
*   compression and, [143–144](#chapter_9.xhtml#pg_143)
*   concepts in, [133](#chapter_9.xhtml#pg_133)
*   contextual learning model, [173–174](#chapter_12.xhtml#pg_173)
*   efficiently learnable hypothesis classes, [143](#chapter_9.xhtml#pg_143)
*   exercises for, [145–146](#chapter_9.xhtml#pg_145)
*   finite hypothesis classes, [138](#chapter_9.xhtml#pg_138)
*   generalization error, [134–135](#chapter_9.xhtml#pg_134), [137](#chapter_9.xhtml#pg_137), [139](#chapter_9.xhtml#pg_139), [144](#chapter_9.xhtml#pg_144), [145](#chapter_9.xhtml#pg_145)
*   goal of, [134](#chapter_9.xhtml#pg_134)
*   hypothesis in, [136–137](#chapter_9.xhtml#pg_136)
*   learning problems in, [136–137](#chapter_9.xhtml#pg_136)
*   no free lunch theorem, [135–136](#chapter_9.xhtml#pg_135)
*   overfitting, [134–135](#chapter_9.xhtml#pg_134)
*   overview of, [133–134](#chapter_9.xhtml#pg_133)
*   probably approximately correct learning, [137–138](#chapter_9.xhtml#pg_137)
*   properly learnable versus improperly learnable hypotheses, [138](#chapter_9.xhtml#pg_138)
*   realizability assumption, [138](#chapter_9.xhtml#pg_138)
*   sample complexity, [137–139](#chapter_9.xhtml#pg_137), [144](#chapter_9.xhtml#pg_144), [146](#chapter_9.xhtml#pg_146), [169](#chapter_11.xhtml#pg_169)
*   strong learnability, [164–165](#chapter_11.xhtml#pg_164)
*   weak learnability, [164–165](#chapter_11.xhtml#pg_164)
*   Lee, Yin Tat, [105](#chapter_6.xhtml#pg_105)
*   Left singular vectors, [107](#chapter_7.xhtml#pg_107)
*   Lewis, A.S., [33](#chapter_2.xhtml#pg_33)
*   Li, Yuanzhi, [105](#chapter_6.xhtml#pg_105), [120](#chapter_7.xhtml#pg_120)
*   Lifetime of integers, [159](#chapter_10.xhtml#pg_159)
*   Limited information, reduction to full information, [94–99](#chapter_6.xhtml#pg_94)
*   ellipsoidal-sampling estimator, [98–99](#chapter_6.xhtml#pg_98)
*   pointwise gradient estimators, [96–97](#chapter_6.xhtml#pg_96)
*   sphere-sampling estimator, [97–98](#chapter_6.xhtml#pg_97)
*   unbiased estimators, [95–96](#chapter_6.xhtml#pg_95)
*   Linder, Tamás, [160](#chapter_10.xhtml#pg_160)
*   Linear algebra, relevant concepts from, [107–108](#chapter_7.xhtml#pg_107)
*   Linear classification model, [31–33](#chapter_2.xhtml#pg_31)
*   Linear convergence, [25–27](#chapter_2.xhtml#pg_25)
*   Linear cost functions. *See* [Cost functions](#index.xhtml#ind4)
*   Linearity property of expectations, [135–136](#chapter_9.xhtml#pg_135)
*   Linear optimization, projections versus, [114–115](#chapter_7.xhtml#pg_114)
*   Linear programming (LP) duality
*   approximation of linear programs, [130–131](#chapter_8.xhtml#pg_130)
*   bibliographic remarks on, [131](#chapter_8.xhtml#pg_131)
*   duality theorem, [124–125](#chapter_8.xhtml#pg_124)
*   history of, [123](#chapter_8.xhtml#pg_123)
*   strong duality, [128–130](#chapter_8.xhtml#pg_128)
*   von Neumann minimax theorem equivalence to, [127–128](#chapter_8.xhtml#pg_127)
*   weak duality, [128](#chapter_8.xhtml#pg_128)
*   Lipschitz conditions, [16](#chapter_2.xhtml#pg_16), [29](#chapter_2.xhtml#pg_29), [30–31](#chapter_2.xhtml#pg_30), [53–54](#chapter_4.xhtml#pg_53), [61](#chapter_4.xhtml#pg_61), [100](#chapter_6.xhtml#pg_100), [177](#chapter_12.xhtml#pg_177), [179](#chapter_12.xhtml#pg_179), [180](#chapter_12.xhtml#pg_180)
*   Littlestone, N., [12](#chapter_1.xhtml#pg_12), [86](#chapter_5.xhtml#pg_86), [145](#chapter_9.xhtml#pg_145)
*   Local norms, [65](#chapter_5.xhtml#pg_65), [68](#chapter_5.xhtml#pg_68), [73](#chapter_5.xhtml#pg_73), [87](#chapter_5.xhtml#pg_87), [102–104](#chapter_6.xhtml#pg_102)
*   Logarithmic regret, [38](#chapter_3.xhtml#pg_38), [41–43](#chapter_3.xhtml#pg_41), [46](#chapter_3.xhtml#pg_46), [49](#chapter_4.xhtml#pg_49), [52–56](#chapter_4.xhtml#pg_52), [61](#chapter_4.xhtml#pg_61)
*   Loss functions. *See also* [Exp-concave functions](#index.xhtml#ind5)
*   convex, [4](#chapter_1.xhtml#pg_4), [7](#chapter_1.xhtml#pg_7), [32](#chapter_2.xhtml#pg_32), [134](#chapter_9.xhtml#pg_134), [151](#chapter_10.xhtml#pg_151), [153](#chapter_10.xhtml#pg_153)
*   hinge, [32](#chapter_2.xhtml#pg_32), *[32](#chapter_2.xhtml#fig2-4)*, [137](#chapter_9.xhtml#pg_137)
*   scaled square loss, [4](#chapter_1.xhtml#pg_4)
*   zero-one, *[32](#chapter_2.xhtml#fig2-4)*, [34](#chapter_2.xhtml#pg_34), [134](#chapter_9.xhtml#pg_134), [143](#chapter_9.xhtml#pg_143), [165](#chapter_11.xhtml#pg_165)
*   Lower regret bounds, [37](#chapter_3.xhtml#pg_37), **[38](#chapter_3.xhtml#tab3-1)**, [40–41](#chapter_3.xhtml#pg_40)
*   Lugosi, Gábor, [61](#chapter_4.xhtml#pg_61), [160](#chapter_10.xhtml#pg_160)

*   Mainstream portfolio theory, [49–50](#chapter_4.xhtml#pg_49)
*   Mannor, S., [106](#chapter_6.xhtml#pg_106)
*   Mansour, Yishay, [61](#chapter_4.xhtml#pg_61), [106](#chapter_6.xhtml#pg_106), [131](#chapter_8.xhtml#pg_131)
*   Markov’s inequality, [135–136](#chapter_9.xhtml#pg_135)
*   Martingales, [140–143](#chapter_9.xhtml#pg_140)
*   Mas-Colell, Andreu, [131](#chapter_8.xhtml#pg_131)
*   Matrices
*   matrix inversion lemma, [61](#chapter_4.xhtml#pg_61)
*   matrix norm, [64](#chapter_5.xhtml#pg_64)
*   permutation, [115](#chapter_7.xhtml#pg_115)
*   positive semidefinite, [16](#chapter_2.xhtml#pg_16), [53](#chapter_4.xhtml#pg_53), [58–59](#chapter_4.xhtml#pg_58), [61](#chapter_4.xhtml#pg_61)
*   rectangular, [107–108](#chapter_7.xhtml#pg_107)
*   relevant concepts from linear algebra, [107–108](#chapter_7.xhtml#pg_107)
*   Matrix completion and recommendation systems, [6–7](#chapter_1.xhtml#pg_6), [108–109](#chapter_7.xhtml#pg_108)
*   conditional gradient for, [112–113](#chapter_7.xhtml#pg_112)
*   learning theory and, [137](#chapter_9.xhtml#pg_137)
*   linear optimization algorithms for, [114](#chapter_7.xhtml#pg_114)
*   Matroid polytopes, projections versus linear optimization for, [115](#chapter_7.xhtml#pg_115)
*   Mazumder, Rahul, [179](#chapter_12.xhtml#pg_179)
*   McMahan, H. Brendan, [87](#chapter_5.xhtml#pg_87), [105](#chapter_6.xhtml#pg_105)
*   Minimax theorem, [123](#chapter_8.xhtml#pg_123), [181–182](#chapter_13.xhtml#pg_181)
*   cost functions in, [129–130](#chapter_8.xhtml#pg_129)
*   equivalence to LP duality, [127–128](#chapter_8.xhtml#pg_127)
*   proof of, [128–130](#chapter_8.xhtml#pg_128)
*   Sion’s generalization of, [131](#chapter_8.xhtml#pg_131), [185](#chapter_13.xhtml#pg_185)
*   statement of, [127](#chapter_8.xhtml#pg_127)
*   Minimum of convex function, [18](#chapter_2.xhtml#pg_18)
*   Minkowski function, [103](#chapter_6.xhtml#pg_103)
*   Minkowski set, [54](#chapter_4.xhtml#pg_54), *[100](#chapter_6.xhtml#fig6-1)*
*   Mirror descent, online
*   agile version, [69–70](#chapter_5.xhtml#pg_69)
*   equivalence of lazy OMD and RFTL, [70](#chapter_5.xhtml#pg_70)
*   lazy version, [69–70](#chapter_5.xhtml#pg_69)
*   regret bounds for, [71–72](#chapter_5.xhtml#pg_71)
*   Regularized Follow The Leader (RFTL), [66](#chapter_5.xhtml#pg_66)
*   Mixability, [61](#chapter_4.xhtml#pg_61)
*   Monro, Sutton, [46](#chapter_3.xhtml#pg_46)
*   Moore-Penrose pseudoinverse, [82](#chapter_5.xhtml#pg_82)
*   Moran, Shaw, [145](#chapter_9.xhtml#pg_145)
*   Moreau-Yoshida regularization, [33–34](#chapter_2.xhtml#pg_33), [179](#chapter_12.xhtml#pg_179), [180](#chapter_12.xhtml#pg_180)
*   Morgenstern, Oskar, [123](#chapter_8.xhtml#pg_123), [131](#chapter_8.xhtml#pg_131)
*   Multiarmed bandit (MAB) problem
*   bandit convex optimization, [90–94](#chapter_6.xhtml#pg_90)
*   bibliographic remarks on, [105–106](#chapter_6.xhtml#pg_105)
*   definition of, [90](#chapter_6.xhtml#pg_90)
*   EXP3 regret algorithm, [93–94](#chapter_6.xhtml#pg_93), [105](#chapter_6.xhtml#pg_105)
*   simple MAB algorithm, [90–93](#chapter_6.xhtml#pg_90)
*   Multiplicative updates, [12](#chapter_1.xhtml#pg_12), [73–74](#chapter_5.xhtml#pg_73), [168](#chapter_11.xhtml#pg_168)
*   Musco, Cameron, [120](#chapter_7.xhtml#pg_120)
*   Musco, Christopher, [120](#chapter_7.xhtml#pg_120)

*   Nadav, Uri, [131](#chapter_8.xhtml#pg_131)
*   Naive predictors, [174](#chapter_12.xhtml#pg_174)
*   Natural language processing (NLP), [191n5](#chapter_2.xhtml#chapter2-5)
*   Near-optimal bandit linear optimization (BLO) algorithm, [103–105](#chapter_6.xhtml#pg_103)
*   Nemirovski, A. S., [33](#chapter_2.xhtml#pg_33), [105](#chapter_6.xhtml#pg_105)
*   Nesterov, Y. E., [33](#chapter_2.xhtml#pg_33), [105](#chapter_6.xhtml#pg_105)
*   Nesterov’s accelerated GD algorithm, [35](#chapter_2.xhtml#pg_35)
*   Netflix challenge, [6](#chapter_1.xhtml#pg_6), [108](#chapter_7.xhtml#pg_108)
*   Network routing problems, projections versus linear optimization for, [114–115](#chapter_7.xhtml#pg_114)
*   Neu, Gergely, [106](#chapter_6.xhtml#pg_106)
*   Newton-Raphson algorithm, [55](#chapter_4.xhtml#pg_55)
*   Nisnevitch, Pinhas, [145](#chapter_9.xhtml#pg_145)
*   No free lunch theorem, [135–136](#chapter_9.xhtml#pg_135)
*   Noisy gradient estimator, [44](#chapter_3.xhtml#pg_44)
*   Norms
*   local, [65](#chapter_5.xhtml#pg_65), [68](#chapter_5.xhtml#pg_68), [73](#chapter_5.xhtml#pg_73), [87](#chapter_5.xhtml#pg_87), [102–104](#chapter_6.xhtml#pg_102)
*   nuclear, [108–109](#chapter_7.xhtml#pg_108), [112–114](#chapter_7.xhtml#pg_112), [120](#chapter_7.xhtml#pg_120)
*   in regularization functions, [64](#chapter_5.xhtml#pg_64)
*   Nuclear norm, [108–109](#chapter_7.xhtml#pg_108), [112–114](#chapter_7.xhtml#pg_112), [120](#chapter_7.xhtml#pg_120)

*   Oblivious vs. adaptive adversaries, [74–75](#chapter_5.xhtml#pg_74)
*   Online binary classification, online boosting of, [172](#chapter_12.xhtml#pg_172)
*   Online boosting, [163–170](#chapter_11.xhtml#pg_163)
*   bibliographic remarks on, [179–180](#chapter_12.xhtml#pg_179)
*   of binary classification, [172](#chapter_12.xhtml#pg_172)
*   contextual learning model, [173–174](#chapter_12.xhtml#pg_173)
*   exercises for, [180](#chapter_12.xhtml#pg_180)
*   extension operator, [174–175](#chapter_12.xhtml#pg_174)
*   large pool of experts in, [171–173](#chapter_12.xhtml#pg_171)
*   motivation for, [171–173](#chapter_12.xhtml#pg_171)
*   online boosting method, [175–179](#chapter_12.xhtml#pg_175)
*   online weak learners in, [171–172](#chapter_12.xhtml#pg_171)
*   of personalized article placement, [172–173](#chapter_12.xhtml#pg_172)
*   policies and, [171](#chapter_12.xhtml#pg_171), [173](#chapter_12.xhtml#pg_173)
*   Online conditional gradient algorithm, [116–120](#chapter_7.xhtml#pg_116)
*   Online gradient descent (OGD), [38–40](#chapter_3.xhtml#pg_38)
*   conceptual illustration of, *[39](#chapter_3.xhtml#fig3-1)*
*   cost functions for, [38](#chapter_3.xhtml#pg_38), [41–42](#chapter_3.xhtml#pg_41), [45](#chapter_3.xhtml#pg_45), [99–100](#chapter_6.xhtml#pg_99)
*   deriving, [72–73](#chapter_5.xhtml#pg_72)
*   logarithmic regret, [38](#chapter_3.xhtml#pg_38), [41–43](#chapter_3.xhtml#pg_41), [46](#chapter_3.xhtml#pg_46), [49](#chapter_4.xhtml#pg_49), [52–56](#chapter_4.xhtml#pg_52), [61](#chapter_4.xhtml#pg_61)
*   regret bounds for, [40–41](#chapter_3.xhtml#pg_40)
*   for strongly convex functions, [42–43](#chapter_3.xhtml#pg_42)
*   Online mirror descent (OMD), [69–72](#chapter_5.xhtml#pg_69)
*   agile version, [69–70](#chapter_5.xhtml#pg_69)
*   equivalence of lazy OMD and RFTL, [70](#chapter_5.xhtml#pg_70)
*   lazy version, [69–70](#chapter_5.xhtml#pg_69)
*   regret bounds for, [71–72](#chapter_5.xhtml#pg_71)
*   Online Newton step algorithm, [55–60](#chapter_4.xhtml#pg_55), [61](#chapter_4.xhtml#pg_61)
*   Online shortest-path problem, [5](#chapter_1.xhtml#pg_5), *[5](#chapter_1.xhtml#fig1-1)*, [12](#chapter_1.xhtml#pg_12)
*   Online spam filtering model, [4](#chapter_1.xhtml#pg_4)
*   Operators, extension, [174–175](#chapter_12.xhtml#pg_174)
*   Optical character recognition (OCR), [133](#chapter_9.xhtml#pg_133). *See also* [Learning theory](#index.xhtml#ind9)
*   boosting in, [163–170](#chapter_11.xhtml#pg_163)
*   problem of, [163–164](#chapter_11.xhtml#pg_163), *[164](#chapter_11.xhtml#fig11-1)*
*   Optimality, distance to, [21–23](#chapter_2.xhtml#pg_21), [174](#chapter_12.xhtml#pg_174), [182](#chapter_13.xhtml#pg_182)
*   Optimality conditions, [18](#chapter_2.xhtml#pg_18), *[19](#chapter_2.xhtml#fig2-3)*
*   Optimization, as process, [1](#chapter_1.xhtml#pg_1)
*   Options pricing, [50](#chapter_4.xhtml#pg_50), [60–61](#chapter_4.xhtml#pg_60)
*   Osborne, M. F. M., [60](#chapter_4.xhtml#pg_60)
*   Overfitting, [134–135](#chapter_9.xhtml#pg_134)

*   Perceptron algorithm, [34](#chapter_2.xhtml#pg_34)
*   Permutation matrices, [115](#chapter_7.xhtml#pg_115)
*   Permutations, projections versus linear optimization for, [115](#chapter_7.xhtml#pg_115)
*   Personalized article placement, online boosting for, [172–173](#chapter_12.xhtml#pg_172)
*   Perturbation
*   for convex losses, [75–78](#chapter_5.xhtml#pg_75), [86](#chapter_5.xhtml#pg_86)
*   for cost functions, [78](#chapter_5.xhtml#pg_78)
*   for expert advice, [79–81](#chapter_5.xhtml#pg_79)
*   for linear cost functions, [78–79](#chapter_5.xhtml#pg_78)
*   Plotkin, Serge A., [131](#chapter_8.xhtml#pg_131)
*   Pointwise gradient estimators, [96–97](#chapter_6.xhtml#pg_96)
*   Polar cones, [186–187](#chapter_13.xhtml#pg_186)
*   Policies, [171](#chapter_12.xhtml#pg_171), [173](#chapter_12.xhtml#pg_173)
*   Polyak, Boris T., [34](#chapter_2.xhtml#pg_34)
*   Polyak learning rate, [33](#chapter_2.xhtml#pg_33), [34](#chapter_2.xhtml#pg_34)
*   Polyak stepsize, gradient descent with
*   algorithm for, [21](#chapter_2.xhtml#pg_21)
*   analysis of, [23–25](#chapter_2.xhtml#pg_23)
*   distance to optimality, [22–23](#chapter_2.xhtml#pg_22)
*   gradient descent with, [20–25](#chapter_2.xhtml#pg_20)
*   Polynomial time algorithm, [12](#chapter_1.xhtml#pg_12)
*   Portfolio selection, [5–6](#chapter_1.xhtml#pg_5), [12](#chapter_1.xhtml#pg_12)
*   constant rebalancing portfolios, [51–52](#chapter_4.xhtml#pg_51)
*   exercises for, [13](#chapter_1.xhtml#pg_13)
*   exp-concave functions, [52–53](#chapter_4.xhtml#pg_52)
*   exponentially weighted online convex optimization, [53–55](#chapter_4.xhtml#pg_53), [60–61](#chapter_4.xhtml#pg_60)
*   geometric Brownian motion (GBM) model, [5](#chapter_1.xhtml#pg_5), [49](#chapter_4.xhtml#pg_49), [61](#chapter_4.xhtml#pg_61)
*   mainstream portfolio theory, [49–50](#chapter_4.xhtml#pg_49)
*   online Newton step algorithm, [55–60](#chapter_4.xhtml#pg_55), [61](#chapter_4.xhtml#pg_61)
*   options pricing, [50](#chapter_4.xhtml#pg_50), [60–61](#chapter_4.xhtml#pg_60)
*   universal portfolio theory, [50–51](#chapter_4.xhtml#pg_50)
*   Positive semidefinite (PSD) matrices, [16](#chapter_2.xhtml#pg_16), [53](#chapter_4.xhtml#pg_53), [58–59](#chapter_4.xhtml#pg_58), [61](#chapter_4.xhtml#pg_61)
*   Prediction from expert advice
*   bibliographic remarks on, [12](#chapter_1.xhtml#pg_12)
*   cost functions for, [3–4](#chapter_1.xhtml#pg_3)
*   exercises for, [13](#chapter_1.xhtml#pg_13)
*   expected number of mistakes of any algorithm, [7–8](#chapter_1.xhtml#pg_7)
*   Hedge algorithm, [11–12](#chapter_1.xhtml#pg_11)
*   importance in machine learning, [3–4](#chapter_1.xhtml#pg_3)
*   large pool of experts in, [171–173](#chapter_12.xhtml#pg_171)
*   pruning experts, [159](#chapter_10.xhtml#pg_159)
*   randomized weighted majority algorithm, [10](#chapter_1.xhtml#pg_10)
*   relative performance metrics, [7–8](#chapter_1.xhtml#pg_7)
*   tracking the best expert, [151–153](#chapter_10.xhtml#pg_151)
*   weighted majority algorithm, [8–9](#chapter_1.xhtml#pg_8), [12](#chapter_1.xhtml#pg_12)
*   working set of experts in, [156–157](#chapter_10.xhtml#pg_156), *[157](#chapter_10.xhtml#fig10-1)*
*   Probability density function (PDF), [75](#chapter_5.xhtml#pg_75)
*   Probably approximately correct (PAC) learning, [137–143](#chapter_9.xhtml#pg_137)
*   agnostic PAC learnability, [138–140](#chapter_9.xhtml#pg_138)
*   concentration in, [140–141](#chapter_9.xhtml#pg_140)
*   definition of, [137–138](#chapter_9.xhtml#pg_137)
*   martingales in, [140–143](#chapter_9.xhtml#pg_140)
*   reduction to OCO, [138–140](#chapter_9.xhtml#pg_138)
*   Problems, modeling
*   matrix completion and recommendation systems, [6–7](#chapter_1.xhtml#pg_6), [108–109](#chapter_7.xhtml#pg_108), [112–114](#chapter_7.xhtml#pg_112)
*   online shortest paths, [5](#chapter_1.xhtml#pg_5), *[5](#chapter_1.xhtml#fig1-1)*, [12](#chapter_1.xhtml#pg_12)
*   online spam filtering, [4](#chapter_1.xhtml#pg_4)
*   prediction from expert advice, [3–4](#chapter_1.xhtml#pg_3), [12–13](#chapter_1.xhtml#pg_12), [171–173](#chapter_12.xhtml#pg_171)
*   universal portfolio selection model, [5–6](#chapter_1.xhtml#pg_5), [12–13](#chapter_1.xhtml#pg_12)
*   Process, optimization as, [1](#chapter_1.xhtml#pg_1)
*   Projection-free algorithms, [107–121](#chapter_7.xhtml#pg_107)
*   bibliographic remarks on, [119–120](#chapter_7.xhtml#pg_119)
*   conditional gradient method, [110–113](#chapter_7.xhtml#pg_110), *[111](#chapter_7.xhtml#fig7-1)*
*   exercises for, [120–121](#chapter_7.xhtml#pg_120)
*   for matrix completion and recommendation systems, [108–109](#chapter_7.xhtml#pg_108), [112–113](#chapter_7.xhtml#pg_112)
*   motivation for, [110–112](#chapter_7.xhtml#pg_110)
*   online conditional gradient algorithm, [116–120](#chapter_7.xhtml#pg_116)
*   projections versus linear optimization, [114–115](#chapter_7.xhtml#pg_114)
*   relevant concepts from linear algebra, [107–108](#chapter_7.xhtml#pg_107)
*   Projections. *See also* [Projection-free algorithms](#index.xhtml#ind14)
*   computational complexity of, [17](#chapter_2.xhtml#pg_17)
*   linear optimization versus, [114–115](#chapter_7.xhtml#pg_114)
*   onto convex sets, [16–18](#chapter_2.xhtml#pg_16)
*   Pythagorean theorem and, [17–18](#chapter_2.xhtml#pg_17), *[17](#chapter_2.xhtml#fig2-1)*
*   Properly learnable hypotheses, [138](#chapter_9.xhtml#pg_138)
*   Pruning experts, [159](#chapter_10.xhtml#pg_159)
*   Pythagorean theorem, [17–18](#chapter_2.xhtml#pg_17), *[17](#chapter_2.xhtml#fig2-1)*

*   Rademacher random variables, [140](#chapter_9.xhtml#pg_140)
*   Rakhlin, Alexander, [87](#chapter_5.xhtml#pg_87), [105](#chapter_6.xhtml#pg_105), [106](#chapter_6.xhtml#pg_106)
*   Ramamoorthi, RV, [189](#chapter_13.xhtml#pg_189)
*   Randomized regularization, [75–78](#chapter_5.xhtml#pg_75)
*   oblivious versus adaptive adversaries, [74–75](#chapter_5.xhtml#pg_74)
*   perturbation for convex losses, [75–78](#chapter_5.xhtml#pg_75), [86](#chapter_5.xhtml#pg_86)
*   perturbation for expert advice, [79–81](#chapter_5.xhtml#pg_79)
*   perturbation for linear cost functions, [78–79](#chapter_5.xhtml#pg_78)
*   Randomized weighted majority (RWM) algorithm, [10](#chapter_1.xhtml#pg_10)
*   Random walk model, [140–141](#chapter_9.xhtml#pg_140), *[140](#chapter_9.xhtml#fig9-1)*. *See also* [Geometric Brownian motion (GBM) model](#index.xhtml#ind7)
*   Rank, definition of, [108](#chapter_7.xhtml#pg_108)
*   Ranking, projections versus linear optimization for, [115](#chapter_7.xhtml#pg_115)
*   Realizability assumption, [138](#chapter_9.xhtml#pg_138), [164](#chapter_11.xhtml#pg_164)
*   Recommendation systems, [6–7](#chapter_1.xhtml#pg_6), [108–109](#chapter_7.xhtml#pg_108)
*   conditional gradient for, [110–113](#chapter_7.xhtml#pg_110)
*   learning theory and, [137](#chapter_9.xhtml#pg_137)
*   linear optimization algorithms for, [114](#chapter_7.xhtml#pg_114)
*   Reductions. *See also* [Boosting](#index.xhtml#ind1)
*   from agnostic PAC learnability to OCO, [138–140](#chapter_9.xhtml#pg_138)
*   from approachability to OCO, [186–189](#chapter_13.xhtml#pg_186)
*   boosting to OCO, [166](#chapter_11.xhtml#pg_166)
*   to general convex functions, [31](#chapter_2.xhtml#pg_31)
*   from limited information to full information, [94–99](#chapter_6.xhtml#pg_94)
*   from OCO to approachability, [183–186](#chapter_13.xhtml#pg_183)
*   overview of, [27](#chapter_2.xhtml#pg_27)
*   to smooth, nonstrongly convex functions, [27–28](#chapter_2.xhtml#pg_27)
*   to strongly convex, nonsmooth functions, [28–31](#chapter_2.xhtml#pg_28)
*   Regret. *See also* [Boosting](#index.xhtml#ind1); [Gradient descent (GD)](#index.xhtml#ind8); [Learning theory](#index.xhtml#ind9); [Regularization](#index.xhtml#ind16)
*   AdaGrad (Adaptive subGradient method) algorithm, [83](#chapter_5.xhtml#pg_83)
*   adaptive, [147](#chapter_10.xhtml#pg_147), [149–150](#chapter_10.xhtml#pg_149), [153–155](#chapter_10.xhtml#pg_153), [160](#chapter_10.xhtml#pg_160)
*   average, [37–38](#chapter_3.xhtml#pg_37)
*   bandit convex optimization, [89–101](#chapter_6.xhtml#pg_89)
*   bandit linear optimization, [101–105](#chapter_6.xhtml#pg_101)
*   Blackwell approachability, [181–189](#chapter_13.xhtml#pg_181)
*   boosting, [163–170](#chapter_11.xhtml#pg_163)
*   definition of, [2–3](#chapter_1.xhtml#pg_2), [37](#chapter_3.xhtml#pg_37), [147](#chapter_10.xhtml#pg_147)
*   dynamic, [148–149](#chapter_10.xhtml#pg_148)
*   EXP3 regret algorithm, [93–94](#chapter_6.xhtml#pg_93)
*   exp-concave functions, [52–53](#chapter_4.xhtml#pg_52)
*   exponentially weighted online convex optimization, [53–55](#chapter_4.xhtml#pg_53), [60–61](#chapter_4.xhtml#pg_60)
*   Follow the Leader strategy, [63](#chapter_5.xhtml#pg_63)
*   follow-the-perturbed-leader for prediction from expert advice, [79–81](#chapter_5.xhtml#pg_79)
*   linear programming duality and, [124–125](#chapter_8.xhtml#pg_124)
*   logarithmic, [38](#chapter_3.xhtml#pg_38), [41–43](#chapter_3.xhtml#pg_41), [46](#chapter_3.xhtml#pg_46), [49](#chapter_4.xhtml#pg_49), [52–56](#chapter_4.xhtml#pg_52), [61](#chapter_4.xhtml#pg_61)
*   lower bounds, [40–41](#chapter_3.xhtml#pg_40)
*   minimax theorem, [123](#chapter_8.xhtml#pg_123), [127–130](#chapter_8.xhtml#pg_127)
*   multiarmed bandit problem, [90–94](#chapter_6.xhtml#pg_90)
*   online boosting, [163–170](#chapter_11.xhtml#pg_163), [171–180](#chapter_12.xhtml#pg_171)
*   online conditional gradient algorithm, [116–119](#chapter_7.xhtml#pg_116)
*   online gradient descent, [40–41](#chapter_3.xhtml#pg_40)
*   online mirror descent, [71–72](#chapter_5.xhtml#pg_71)
*   online Newton step algorithm, [55–60](#chapter_4.xhtml#pg_55)
*   Regularized Follow The Leader algorithm, [66–68](#chapter_5.xhtml#pg_66)
*   universal portfolio selection model, [6](#chapter_1.xhtml#pg_6)
*   upper and lower bounds on, [37](#chapter_3.xhtml#pg_37), **[38](#chapter_3.xhtml#tab3-1)**
*   Regularization
*   adaptive gradient descent, [81–86](#chapter_5.xhtml#pg_81), [87](#chapter_5.xhtml#pg_87)
*   application and special cases, [72–74](#chapter_5.xhtml#pg_72)
*   bibliographic remarks on, [86–87](#chapter_5.xhtml#pg_86)
*   Bregman divergence and, [64–65](#chapter_5.xhtml#pg_64), [68](#chapter_5.xhtml#pg_68), [71–72](#chapter_5.xhtml#pg_71)
*   deterministic strongly convex, [87](#chapter_5.xhtml#pg_87)
*   exercises for, [87–88](#chapter_5.xhtml#pg_87)
*   follow-the-leader versus be-the-leader, [191n1](#chapter_1.xhtml#chapter1-1)
*   functions for, [64–65](#chapter_5.xhtml#pg_64)
*   Moreau-Yoshida, [179](#chapter_12.xhtml#pg_179), [180](#chapter_12.xhtml#pg_180)
*   multiplicative updates, [12](#chapter_1.xhtml#pg_12), [73–74](#chapter_5.xhtml#pg_73), [168](#chapter_11.xhtml#pg_168)
*   norms in, [64](#chapter_5.xhtml#pg_64)
*   online gradient descent, [72–73](#chapter_5.xhtml#pg_72)
*   online mirror descent, [69–72](#chapter_5.xhtml#pg_69)
*   randomized, [75–78](#chapter_5.xhtml#pg_75)
*   regularization functions, [64–65](#chapter_5.xhtml#pg_64)
*   Regularized Follow The Leader, [63](#chapter_5.xhtml#pg_63), [65–72](#chapter_5.xhtml#pg_65), [86–87](#chapter_5.xhtml#pg_86)
*   self-concordant barrier, [191n3](#chapter_2.xhtml#chapter2-3)
*   success in training deep neural networks, [87](#chapter_5.xhtml#pg_87)
*   Regularized Follow The Leader (RFTL) algorithm, [63](#chapter_5.xhtml#pg_63), [65–72](#chapter_5.xhtml#pg_65)
*   bibliographic remarks on, [86–87](#chapter_5.xhtml#pg_86)
*   cost functions for, [65–66](#chapter_5.xhtml#pg_65), [70](#chapter_5.xhtml#pg_70)
*   equivalence of lazy OMD and RFTL, [70](#chapter_5.xhtml#pg_70)
*   meta-algorithm definition, [66](#chapter_5.xhtml#pg_66)
*   regret bound, [66–68](#chapter_5.xhtml#pg_66)
*   Right singular vector, [107](#chapter_7.xhtml#pg_107)
*   Rish, Irina, [180](#chapter_12.xhtml#pg_180)
*   RMSprop, [87](#chapter_5.xhtml#pg_87)
*   Robbins, Herbert, [46](#chapter_3.xhtml#pg_46), [105](#chapter_6.xhtml#pg_105)
*   Rockafellar, R. T., [33](#chapter_2.xhtml#pg_33)
*   Roughgarden, Tim, [131](#chapter_8.xhtml#pg_131)
*   Running time, of algorithms, [3](#chapter_1.xhtml#pg_3)

*   Sabato, Sivan, [145](#chapter_9.xhtml#pg_145)
*   Sadigurschi, Menachem, [145](#chapter_9.xhtml#pg_145)
*   Sample complexity, [137–139](#chapter_9.xhtml#pg_137), [144](#chapter_9.xhtml#pg_144), [146](#chapter_9.xhtml#pg_146), [169](#chapter_11.xhtml#pg_169)
*   Scalar games, [182](#chapter_13.xhtml#pg_182). *See also* [Zero-sum games](#index.xhtml#ind20)
*   Scaled square loss, [4](#chapter_1.xhtml#pg_4)
*   Schapire, Robert E., [12](#chapter_1.xhtml#pg_12), [105](#chapter_6.xhtml#pg_105), [123](#chapter_8.xhtml#pg_123), [131](#chapter_8.xhtml#pg_131), [169](#chapter_11.xhtml#pg_169)
*   Scholes, Myron, [60](#chapter_4.xhtml#pg_60)
*   Schölkopf, Bernhard, [34](#chapter_2.xhtml#pg_34)
*   Schuurmans, D., [86](#chapter_5.xhtml#pg_86)
*   SCRIBLE algorithm, [103–105](#chapter_6.xhtml#pg_103)
*   Second-order methods
*   exercises for, [61–62](#chapter_4.xhtml#pg_61)
*   exp-concave functions, [52–53](#chapter_4.xhtml#pg_52), [61](#chapter_4.xhtml#pg_61)
*   exponentially weighted online convex optimization, [53–55](#chapter_4.xhtml#pg_53)
*   motivation for, [49–52](#chapter_4.xhtml#pg_49)
*   online Newton step algorithm, [55–60](#chapter_4.xhtml#pg_55)
*   universal portfolio selection problem, [49–52](#chapter_4.xhtml#pg_49), [61](#chapter_4.xhtml#pg_61)
*   Self-concordant barrier functions, [102–103](#chapter_6.xhtml#pg_102), [106](#chapter_6.xhtml#pg_106), [191n3](#chapter_2.xhtml#chapter2-3)
*   Sensitivity, average, [191n2](#chapter_1.xhtml#chapter1-2)
*   Seshadhri, Comandur, [160](#chapter_10.xhtml#pg_160)
*   Sets
*   convex, [15](#chapter_2.xhtml#pg_15), [16–18](#chapter_2.xhtml#pg_16)
*   Euclidean distance to, [174](#chapter_12.xhtml#pg_174), [184](#chapter_13.xhtml#pg_184)
*   projections onto, [16–18](#chapter_2.xhtml#pg_16)
*   Shalev-Shwartz, Shai, [46](#chapter_3.xhtml#pg_46), [86](#chapter_5.xhtml#pg_86), [145](#chapter_9.xhtml#pg_145), [160](#chapter_10.xhtml#pg_160)
*   Shannon, Claude, [13](#chapter_1.xhtml#pg_13)
*   Sherman-Morrison formula, [61](#chapter_4.xhtml#pg_61)
*   Shimkin, N., [106](#chapter_6.xhtml#pg_106)
*   Shmoys, David B., [131](#chapter_8.xhtml#pg_131)
*   Shortest-path problem model, [5](#chapter_1.xhtml#pg_5), *[5](#chapter_1.xhtml#fig1-1)*
*   Singer, Yoram, [87](#chapter_5.xhtml#pg_87), [160](#chapter_10.xhtml#pg_160)
*   Singh, Karan, [179](#chapter_12.xhtml#pg_179)
*   Singular value decomposition, [108](#chapter_7.xhtml#pg_108), [120](#chapter_7.xhtml#pg_120)
*   Sion’s generalization, [131](#chapter_8.xhtml#pg_131), [185](#chapter_13.xhtml#pg_185)
*   Smola, Alexander J., [34](#chapter_2.xhtml#pg_34)
*   Smooth, nonstrongly convex functions
*   conditional gradient algorithm applied to, [110–112](#chapter_7.xhtml#pg_110)
*   definition of, [16](#chapter_2.xhtml#pg_16)
*   distance to optimality, measurement of, [22–23](#chapter_2.xhtml#pg_22)
*   gradient descent, [19–25](#chapter_2.xhtml#pg_19)
*   Polyak stepsize analysis, [23–25](#chapter_2.xhtml#pg_23)
*   reduction to, [27–28](#chapter_2.xhtml#pg_27)
*   regret rates, [37–38](#chapter_3.xhtml#pg_37)
*   Spam filtering models, [4](#chapter_1.xhtml#pg_4)
*   Spencer, Joel, [145](#chapter_9.xhtml#pg_145)
*   Sphere-sampling estimator, [97–98](#chapter_6.xhtml#pg_97)
*   Spotify, [6](#chapter_1.xhtml#pg_6)
*   Statistical learning theory, [133–138](#chapter_9.xhtml#pg_133), [163](#chapter_11.xhtml#pg_163). *See also* [Changing environments, learning in](#index.xhtml#ind2)
*   agnostic probably approximately correct learning, [137–143](#chapter_9.xhtml#pg_137)
*   bibliographic remarks on, [145](#chapter_9.xhtml#pg_145)
*   compression and, [143–144](#chapter_9.xhtml#pg_143)
*   concepts in, [133](#chapter_9.xhtml#pg_133)
*   contextual learning model, [173–174](#chapter_12.xhtml#pg_173)
*   efficiently learnable hypothesis classes, [143](#chapter_9.xhtml#pg_143)
*   exercises for, [145–146](#chapter_9.xhtml#pg_145)
*   finite hypothesis classes, [138](#chapter_9.xhtml#pg_138)
*   generalization error, [134–135](#chapter_9.xhtml#pg_134), [137](#chapter_9.xhtml#pg_137), [139](#chapter_9.xhtml#pg_139), [144](#chapter_9.xhtml#pg_144), [145](#chapter_9.xhtml#pg_145), [164](#chapter_11.xhtml#pg_164)
*   goal of, [134](#chapter_9.xhtml#pg_134)
*   hypothesis in, [136–137](#chapter_9.xhtml#pg_136)
*   learning problems in, [136–137](#chapter_9.xhtml#pg_136)
*   no free lunch theorem, [135–136](#chapter_9.xhtml#pg_135)
*   overfitting, [134–135](#chapter_9.xhtml#pg_134)
*   overview of, [133–134](#chapter_9.xhtml#pg_133)
*   probably approximately correct learning, [137–138](#chapter_9.xhtml#pg_137)
*   properly learnable versus improperly learnable hypotheses, [138](#chapter_9.xhtml#pg_138)
*   realizability assumption, [138](#chapter_9.xhtml#pg_138), [164](#chapter_11.xhtml#pg_164)
*   sample complexity, [137–139](#chapter_9.xhtml#pg_137), [144](#chapter_9.xhtml#pg_144), [146](#chapter_9.xhtml#pg_146), [169](#chapter_11.xhtml#pg_169)
*   strong learnability, [164–165](#chapter_11.xhtml#pg_164)
*   weak learnability, [164–165](#chapter_11.xhtml#pg_164)
*   Stochastic approximation. *See* [Stochastic gradient descent (SGD)](#index.xhtml#ind18)
*   Stochastic gradient descent (SGD), [43–46](#chapter_3.xhtml#pg_43)
*   Stochastic optimization, [43–46](#chapter_3.xhtml#pg_43)
*   Stock prices. *See also* [Portfolio selection](#index.xhtml#ind12)
*   geometric Brownian motion model, [5](#chapter_1.xhtml#pg_5), [12](#chapter_1.xhtml#pg_12), [60](#chapter_4.xhtml#pg_60)
*   universal portfolio selection model, [12](#chapter_1.xhtml#pg_12)
*   Stokes’ theorem, [30](#chapter_2.xhtml#pg_30), [98](#chapter_6.xhtml#pg_98)
*   Streaming, [156–157](#chapter_10.xhtml#pg_156)
*   Streeter, Matthew J., [87](#chapter_5.xhtml#pg_87)
*   Strong duality, [128–130](#chapter_8.xhtml#pg_128)
*   Strong learnability, [164–165](#chapter_11.xhtml#pg_164)
*   Strongly adaptive algorithms, [150](#chapter_10.xhtml#pg_150)
*   Strongly convex, nonsmooth functions
*   definition of, [15–16](#chapter_2.xhtml#pg_15)
*   distance to optimality, measurement of, [22–23](#chapter_2.xhtml#pg_22)
*   gradient descent, [19–25](#chapter_2.xhtml#pg_19)
*   online gradient descent for, [42–43](#chapter_3.xhtml#pg_42)
*   Polyak stepsize analysis, [23–25](#chapter_2.xhtml#pg_23)
*   reduction to, [28–31](#chapter_2.xhtml#pg_28)
*   regret rates, [37–38](#chapter_3.xhtml#pg_37)
*   Subgradients
*   definition of, [16](#chapter_2.xhtml#pg_16)
*   subgradient descent, [16](#chapter_2.xhtml#pg_16), [25–27](#chapter_2.xhtml#pg_25), [31–33](#chapter_2.xhtml#pg_31)
*   Support vector machines (SVMs), [145](#chapter_9.xhtml#pg_145), [146](#chapter_9.xhtml#pg_146)
*   stochastic gradient descent, [43–46](#chapter_3.xhtml#pg_43)
*   subgradient descent, [31–33](#chapter_2.xhtml#pg_31)
*   Szepesvári, Csaba, [106](#chapter_6.xhtml#pg_106)

*   Taylor approximation, [53](#chapter_4.xhtml#pg_53), [64](#chapter_5.xhtml#pg_64)
*   Taylor expansion, [58](#chapter_4.xhtml#pg_58)
*   Tewari, Ambuj, [106](#chapter_6.xhtml#pg_106)
*   Text classification, learning theory and, [136–137](#chapter_9.xhtml#pg_136)
*   *Theory of Games and Economic Behavior* (Neumann and Morgenstern), [131](#chapter_8.xhtml#pg_131)
*   Tracking of best expert, [151–153](#chapter_10.xhtml#pg_151)
*   Twice-differentiable functions, [52–53](#chapter_4.xhtml#pg_52), [61](#chapter_4.xhtml#pg_61)

*   Unbiased estimators, [95–96](#chapter_6.xhtml#pg_95)
*   Universal portfolio selection problem, [5–6](#chapter_1.xhtml#pg_5), [12](#chapter_1.xhtml#pg_12), [60](#chapter_4.xhtml#pg_60)
*   bibliographic remarks on, [12](#chapter_1.xhtml#pg_12)
*   constant rebalancing portfolios, [51–52](#chapter_4.xhtml#pg_51)
*   exercises for, [13](#chapter_1.xhtml#pg_13)
*   exp-concave functions, [52–53](#chapter_4.xhtml#pg_52)
*   exponentially weighted online convex optimization, [53–55](#chapter_4.xhtml#pg_53), [60–61](#chapter_4.xhtml#pg_60)
*   mainstream portfolio theory compared to, [49–50](#chapter_4.xhtml#pg_49)
*   online Newton step algorithm, [55–60](#chapter_4.xhtml#pg_55), [61](#chapter_4.xhtml#pg_61)
*   polynomial time algorithm for, [12](#chapter_1.xhtml#pg_12)
*   universal portfolio theory, [50–51](#chapter_4.xhtml#pg_50)
*   Upper regret bounds, [37](#chapter_3.xhtml#pg_37), **[38](#chapter_3.xhtml#tab3-1)**

*   Valiant, L. G., [145](#chapter_9.xhtml#pg_145)
*   Vandenberghe, L., [33](#chapter_2.xhtml#pg_33)
*   Vapnik, Vladimir, [34](#chapter_2.xhtml#pg_34), [138](#chapter_9.xhtml#pg_138), [145](#chapter_9.xhtml#pg_145)
*   Variance, constant, [106](#chapter_6.xhtml#pg_106)
*   Vazirani, Umesh V., [145](#chapter_9.xhtml#pg_145)
*   Vectors, emails represented as, [4](#chapter_1.xhtml#pg_4)
*   Vector-valued games, Blackwell approachability in, [181–189](#chapter_13.xhtml#pg_181)
*   assumptions and definitions in, [181–183](#chapter_13.xhtml#pg_181)
*   Blackwell’s approachability theorem, [183](#chapter_13.xhtml#pg_183)
*   reduction from OCO to, [183–186](#chapter_13.xhtml#pg_183)
*   reduction to OCO, [186–189](#chapter_13.xhtml#pg_186)
*   Vempala, Santosh, [12](#chapter_1.xhtml#pg_12), [61](#chapter_4.xhtml#pg_61), [86](#chapter_5.xhtml#pg_86), [191n1](#chapter_1.xhtml#chapter1-1)
*   von Neumann, John, [123](#chapter_8.xhtml#pg_123), [131](#chapter_8.xhtml#pg_131), [181](#chapter_13.xhtml#pg_181)
*   von Neumann minimax theorem
*   cost functions in, [129–130](#chapter_8.xhtml#pg_129)
*   equivalence to LP duality, [127–128](#chapter_8.xhtml#pg_127)
*   proof of, [128–130](#chapter_8.xhtml#pg_128)
*   Sion’s generalization, [131](#chapter_8.xhtml#pg_131), [185](#chapter_13.xhtml#pg_185)
*   statement of, [127](#chapter_8.xhtml#pg_127)
*   Vovk, Volodimir G., [61](#chapter_4.xhtml#pg_61)

*   Wang, Chu, [179](#chapter_12.xhtml#pg_179)
*   Warmuth, M. K., [12](#chapter_1.xhtml#pg_12), [46](#chapter_3.xhtml#pg_46), [61](#chapter_4.xhtml#pg_61), [86](#chapter_5.xhtml#pg_86), [145](#chapter_9.xhtml#pg_145), [159](#chapter_10.xhtml#pg_159)
*   Weak duality, [128](#chapter_8.xhtml#pg_128)
*   Weak learnability, [164–165](#chapter_11.xhtml#pg_164)
*   Weakly adaptive algorithms, [150](#chapter_10.xhtml#pg_150)
*   Weak OCO learner (WOCL), boosting for. *See* [Online boosting](#index.xhtml#ind11)
*   Weighted majority (WM) algorithm, [8–9](#chapter_1.xhtml#pg_8), [12](#chapter_1.xhtml#pg_12). *See also* [Randomized weighted majority (RWM) algorithm](#index.xhtml#ind15)
*   Weiss, Roi, [145](#chapter_9.xhtml#pg_145)
*   Well-conditioned functions
*   definition of, [16](#chapter_2.xhtml#pg_16)
*   gradient descent, [25–27](#chapter_2.xhtml#pg_25)
*   Wibisono, Andre, [61](#chapter_4.xhtml#pg_61)
*   Wigderson, Avi, [145](#chapter_9.xhtml#pg_145)
*   Woźniakowski, Henryk, [120](#chapter_7.xhtml#pg_120)
*   Wolfe, P., [119](#chapter_7.xhtml#pg_119)

*   Yehudayoff, Amir, [145](#chapter_9.xhtml#pg_145)
*   Yu, J. Y., [106](#chapter_6.xhtml#pg_106)
*   Yudin, David B., [33](#chapter_2.xhtml#pg_33)

*   Zeevi, Assaf, [159](#chapter_10.xhtml#pg_159)
*   Zero-one loss function, *[32](#chapter_2.xhtml#fig2-4)*, [34](#chapter_2.xhtml#pg_34), [134](#chapter_9.xhtml#pg_134), [143](#chapter_9.xhtml#pg_143), [165](#chapter_11.xhtml#pg_165)
*   Zero-sum games
*   bibliographic remarks on, [131](#chapter_8.xhtml#pg_131)
*   equilibria and, [125–127](#chapter_8.xhtml#pg_125), **[125](#chapter_8.xhtml#tab8-1)**
*   goal of, [182](#chapter_13.xhtml#pg_182)
*   minimax theorem, [123](#chapter_8.xhtml#pg_123), [127–131](#chapter_8.xhtml#pg_127), [181–182](#chapter_13.xhtml#pg_181), [185](#chapter_13.xhtml#pg_185)
*   Zhang, Lijun, [159](#chapter_10.xhtml#pg_159)
*   Zhang, Tong, [179](#chapter_12.xhtml#pg_179)
*   Zhou, Zhi-Hua, [180](#chapter_12.xhtml#pg_180)
*   Zinkevich, Martin, [12](#chapter_1.xhtml#pg_12), [38](#chapter_3.xhtml#pg_38), [46](#chapter_3.xhtml#pg_46), [159](#chapter_10.xhtml#pg_159)

**Adaptive Computation and Machine Learning**

Francis Bach, Editor

Christopher Bishop, David Heckerman, Michael Jordan, and Michael Kearns, Associate Editors

*Bioinformatics: The Machine Learning Approach*, Pierre Baldi and Søren Brunak

*Reinforcement Learning: An Introduction*, Richard S. Sutton and Andrew G. Barto

*Graphical Models for Machine Learning and Digital Communication*, Brendan J. Frey

*Learning in Graphical Models*, Michael I. Jordan

*Causation, Prediction, and Search, second edition*, Peter Spirtes, ClarkGlymour, and Richard Scheines

*Principles of Data Mining*, David Hand, Heikki Mannila, and Padhraic Smyth

*Bioinformatics: The Machine Learning Approach, second edition*, Pierre Baldi and Søren Brunak

*Learning Kernel Classifiers: Theory and Algorithms*, Ralf Herbrich

*Learning with Kernels: Support Vector Machines, Regularization, Optimization, and Beyond*, Bernhard Schölkopf and Alexander J. Smola

*Introduction to Machine Learning*, Ethem Alpaydin

*Gaussian Processes for Machine Learning*, Carl Edward Rasmussen and Christopher K.I. Williams

*Semi-Supervised Learning*, Olivier Chapelle, Bernhard Schölkopf, and Alexander Zien, Eds.

*The Minimum Description Length Principle*, Peter D. Grünwald

*Introduction to Statistical Relational Learning*, Lise Getoor and Ben Taskar, Eds.

*Probabilistic Graphical Models: Principles and Techniques*, Daphne Koller and Nir Friedman

*Introduction to Machine Learning*, second edition, Ethem Alpaydin

*Machine Learning in Non-Stationary Environments: Introduction to Covariate Shift Adaptation*, Masashi Sugiyama and Motoaki Kawanabe

*Boosting: Foundations and Algorithms*, Robert E. Schapire and Yoav Freund

*Machine Learning: A Probabilistic Perspective*, Kevin P. Murphy

*Foundations of Machine Learning*, Mehryar Mohri, Afshin Rostami, and Ameet Talwalker

*Introduction to Machine Learning*, third edition, Ethem Alpaydin

*Deep Learning*, Ian Goodfellow, Yoshua Bengio, and Aaron Courville

*Elements of Causal Inference*, Jonas Peters, Dominik Janzing, and Bernhard Schölkopf

*Data Stream Mining*, Albert Bifet, Ricard Gavaldà, Geoffrey Holmes, and Bernhard Pfahringer

*Introduction to Online Convex Optimization*, Elad Hazan

*Machine Learning from Weak Supervision*, Masashi Sugiyama, Tomoya Sakai, Takashi Ishida, Gang Niu, Han Bao, and Nan Lu