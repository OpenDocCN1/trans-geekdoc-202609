   

# **Artificial Intelligence**

A Modern Approach

*Third Edition*

![pub](images/00001.jpg)

FORSYTH & PONCE *Computer Vision: A Modern Approach*

GRAHAM ANSI *Common Lisp*

JURAFSKY & MARTIN *Speech and Language Processing, 2nd ed.*

NEAPOLITAN *Learning Bayesian Networks*

RUSSELL & NORVIG *Artificial Intelligence: A Modern Approach, 3rd ed.*

# **Artificial Intelligence**

A Modern Approach

*Third Edition*

Stuart J. Russell and Peter Norvig  
  

*Contributing writers*:

Ernest Davis

Douglas D. Edwards

David Forsyth

Nicholas J. Hay

Jitendra M. Malik

Vibhu Mittal

Mehran Sahami

Sebastian Thrun

![pub](images/00002.jpg)

Vice President and Editorial Director, ECS: Marcia J. Horton  
Editor-in-Chief: Michael Hirsch  
Executive Editor: Tracy Dunkelberger  
Assistant Editor: Melinda Haggerty  
Editorial Assistant: Allison Michael  
Vice President, Production: Vince O’Brien  
Senior Managing Editor: Scott Disanno  
Production Editor: Jane Bonnell  
Senior Operations Supervisor: Alan Fischer  
Operations Specialist: Lisa McDowell  
Marketing Manager: Erin Davis  
Marketing Assistant: Mack Patterson  
Cover Designers: Kirsten Sims and Geoffrey Cassar  
Cover Images: Stan Honda/Getty, Library of Congress, NASA, National Museum of Rome,  
Peter Norvig, Ian Parker, Shutterstock, Time Life/Getty  
Interior Designers: Stuart Russell and Peter Norvig  
Copy Editor: Mary Lou Nohr  
Art Editor: Greg Dulles  
Media Editor: Daniel Sandin  
Media Project Manager: Danielle Leone

**Copyright © 2010, 2003, 1995 by Pearson Education, Inc.,**  
**Upper Saddle River, New Jersey 07458.**

All rights reserved. Manufactured in the United States of America. This publication is protected by Copyright and permissions should be obtained from the publisher prior to any prohibited reproduction, storage in a retrieval system, or transmission in any form or by any means, electronic, mechanical, photocopying, recording, or likewise. To obtain permission(*s*) to use materials from this work, please submit a written request to Pearson Higher Education, Permissions Department, 1 Lake Street, Upper Saddle River, NJ 07458.

The author and publisher of this book have used their best efforts in preparing this book. These efforts include the development, research, and testing of the theories and programs to determine their effectiveness. The author and publisher make no warranty of any kind, expressed or implied, with regard to these programs or the documentation contained in this book. The author and publisher shall not be liable in any event for incidental or consequential damages in connection with, or arising out of, the furnishing, performance, or use of these programs.

**Library of Congress Cataloging-in-Publication Data on File**

![pub1](images/00003.jpg)

*For Loy, Gordon, Lucy, George, and Isaac* — S.J.R.

*For Kris, Isabella, and Juliet* — P.N.

## **Preface**

**Artificial Intelligence** (AI) is a big field, and this is a big book. We have tried to explore the full breadth of the field, which encompasses logic, probability, and continuous mathematics; perception, reasoning, learning, and action; and everything from microelectronic devices to robotic planetary explorers. The book is also big because we go into some depth.

The subtitle of this book is “A Modern Approach.” The intended meaning of this rather empty phrase is that we have tried to synthesize what is now known into a common framework, rather than trying to explain each subfield of AI in its own historical context. We apologize to those whose subfields are, as a result, less recognizable.

### **New to this edition**

This edition captures the changes in AI that have taken place since the last edition in 2003. There have been important applications of AI technology, such as the widespread deployment of practical speech recognition, machine translation, autonomous vehicles, and household robotics. There have been algorithmic landmarks, such as the solution of the game of checkers. And there has been a great deal of theoretical progress, particularly in areas such as probabilistic reasoning, machine learning, and computer vision. Most important from our point of view is the continued evolution in how we think about the field, and thus how we organize the book. The major changes are as follows:

> • We place more emphasis on partially observable and nondeterministic environments, especially in the nonprobabilistic settings of search and planning. The concepts of *belief state* (*a* set of possible worlds) and *state estimation* (maintaining the belief state) are introduced in these settings; later in the book, we add probabilities.

> • In addition to discussing the types of environments and types of agents, we now cover in more depth the types of *representations* that an agent can use. We distinguish among *atomic* representations (in which each state of the world is treated as a black box), *factored* representations (in which a state is a set of attribute/value pairs), and *structured* representations (in which the world consists of objects and relations between them).

> • Our coverage of planning goes into more depth on contingent planning in partially observable environments and includes a new approach to hierarchical planning.

> • We have added new material on first-order probabilistic models, including *open-universe* models for cases where there is uncertainty as to what objects exist.

> • We have completely rewritten the introductory machine-learning chapter, stressing a wider variety of more modern learning algorithms and placing them on a firmer theoretical footing.

> • We have expanded coverage of Web search and information extraction, and of techniques for learning from very large data sets.

> • 20% of the citations in this edition are to works published after 2003.

> • We estimate that about 20% of the material is brand new. The remaining 80% reflects older work but has been largely rewritten to present a more unified picture of the field.

### **Overview of the book**

The main unifying theme is the idea of an **intelligent agent**. We define AI as the study of agents that receive percepts from the environment and perform actions. Each such agent implements a function that maps percept sequences to actions, and we cover different ways to represent these functions, such as reactive agents, real-time planners, and decision-theoretic systems. We explain the role of learning as extending the reach of the designer into unknown environments, and we show how that role constrains agent design, favoring explicit knowledge representation and reasoning. We treat robotics and vision not as independently defined problems, but as occurring in the service of achieving goals. We stress the importance of the task environment in determining the appropriate agent design.

Our primary aim is to convey the *ideas* that have emerged over the past fifty years of AI research and the past two millennia of related work. We have tried to avoid excessive formality in the presentation of these ideas while retaining precision. We have included pseudocode algorithms to make the key ideas concrete; our pseudocode is described in Appendix B.

This book is primarily intended for use in an undergraduate course or course sequence. The book has 27 chapters, each requiring about a week’s worth of lectures, so working through the whole book requires a two-semester sequence. A one-semester course can use selected chapters to suit the interests of the instructor and students. The book can also be used in a graduate-level course (perhaps with the addition of some of the primary sources suggested in the bibliographical notes). Sample syllabi are available at the book’s Web site, `aima.cs.berkeley.edu`. The only prerequisite is familiarity with basic concepts of computer science (algorithms, data structures, complexity) at a sophomore level. Freshman calculus and linear algebra are useful for some of the topics; the required mathematical background is supplied in Appendix A.

Exercises are given at the end of each chapter. Exercises requiring significant programming are marked with a **keyboard** icon. These exercises can best be solved by taking advantage of the code repository at `aima.cs.berkeley.edu`. Some of them are large enough to be considered term projects. A number of exercises require some investigation of the literature; these are marked with a **book** icon.

![equ](images/00004.jpg)

![equ](images/00005.jpg)

Throughout the book, important points are marked with a *pointing* icon. We have included an extensive index of around 6,000 items to make it easy to find things in the book. Wherever a **new term** is first defined, it is also marked in the margin.

![equ](images/00006.jpg)

* * *

NEW TERM

* * *

### **About the Web site**

`aima.cs.berkeley.edu`, the Web site for the book, contains

> • implementations of the algorithms in the book in several programming languages,

> • a list of over 1000 schools that have used the book, many with links to online course materials and syllabi,

> • an annotated list of over 800 links to sites around the Web with useful AI content,

> • a chapter-by-chapter list of supplementary material and links,

> • instructions on how to join a discussion group for the book,

> • instructions on how to contact the authors with questions or comments,

> • instructions on how to report errors in the book, in the likely event that some exist, and

> • slides and other materials for instructors.

### **About the cover**

The cover depicts the final position from the decisive game 6 of the 1997 match between chess champion Garry Kasparov and program DEEP BLUE. Kasparov, playing Black, was forced to resign, making this the first time a computer had beaten a world champion in a chess match. Kasparov is shown at the top. To his left is the Asimo humanoid robot and to his right is Thomas Bayes (1702–1761), whose ideas about probability as a measure of belief underlie much of modern AI technology. Below that we see a Mars Exploration Rover, a robot that landed on Mars in 2004 and has been exploring the planet ever since. To the right is Alan Turing (1912–1954), whose fundamental work defined the fields of computer science in general and artificial intelligence in particular. At the bottom is Shakey (1966–1972), the first robot to combine perception, world-modeling, planning, and learning. With Shakey is project leader Charles Rosen (1917–2002). At the bottom right is Aristotle (384 B.C.–322 B.C.), who pioneered the study of logic; his work was state of the art until the 19th century (copy of a bust by Lysippos). At the bottom left, lightly screened behind the authors’names, is a planning algorithm by Aristotle from *De Motu Animalium* in the original Greek. Behind the title is a portion of the CPSC Bayesian network for medical diagnosis (Pradhan *et al*., 1994). Behind the chess board is part of a Bayesian logic model for detecting nuclear explosions from seismic signals.

Credits: Stan Honda/Getty (Kasparaov), Library of Congress (Bayes), NASA (Mars rover), National Museum of Rome (Aristotle), Peter Norvig (book), Ian Parker (Berkeley skyline), Shutterstock (Asimo, Chess pieces), Time Life/Getty (Shakey, Turing).

### **Acknowledgments**

This book would not have been possible without the many contributors whose names did not make it to the cover. Jitendra Malik and David Forsyth wrote [Chapter 24](#index_split_015.html#filepos3631932) (computer vision) and Sebastian Thrun wrote [Chapter 25](#index_split_015.html#filepos3777962) (robotics). Vibhu Mittal wrote part of [Chapter 22](#index_split_015.html#filepos3374172) (natural language). Nick Hay, Mehran Sahami, and Ernest Davis wrote some of the exercises. Zoran Duric (George Mason), Thomas C. Henderson (Utah), Leon Reznik (RIT), Michael Gourley (Central Oklahoma) and Ernest Davis (NYU) reviewed the manuscript and made helpful suggestions. We thank Ernie Davis in particular for his tireless ability to read multiple drafts and help improve the book. Nick Hay whipped the bibliography into shape and on deadline stayed up to 5:30 AM writing code to make the book better. Jon Barron formatted and improved the diagrams in this edition, while Tim Huang, Mark Paskin, and Cynthia Bruyns helped with diagrams and algorithms in previous editions. Ravi Mohan and Ciaran O’Reilly wrote and maintain the Java code examples on the Web site. John Canny wrote the robotics chapter for the first edition and Douglas Edwards researched the historical notes. Tracy Dunkelberger, Allison Michael, Scott Disanno, and Jane Bonnell at Pearson tried their best to keep us on schedule and made many helpful suggestions. Most helpful of all has been Julie Sussman, P.P.A., who read every chapter and provided extensive improvements. In previous editions we had proofreaders who would tell us when we left out a comma and said *which* when we meant *that*; Julie told us when we left out a minus sign and said x[*i*] when we meant x[*j*]. For every typo or confusing explanation that remains in the book, rest assured that Julie has fixed at least five. She persevered even when a power failure forced her to work by lantern light rather than LCD glow.

**Stuart would like to thank** his parents for their support and encouragement and his wife, Loy Sheflott, for her endless patience and boundless wisdom. He hopes that Gordon, Lucy, George, and Isaac will soon be reading this book after they have forgiven him for working so long on it. RUGS (Russell’s Unusual Group of Students) have been unusually helpful, as always.

**Peter would like to thank** his parents (Torsten and Gerda) for getting him started, and his wife (Kris), children (Bella and Juliet), colleagues, and friends for encouraging and tolerating him through the long hours of writing and longer hours of rewriting.

**We both thank** the librarians at Berkeley, Stanford, and NASA and the developers of CiteSeer, Wikipedia, and Google, who have revolutionized the way we do research. We can’t acknowledge all the people who have used the book and made suggestions, but we would like to note the especially helpful comments of Gagan Aggarwal, Eyal Amir, Ion Androutsopoulos, Krzysztof Apt, Warren Haley Armstrong, Ellery Aziel, Jeff Van Baalen, Darius Bacon, Brian Baker, Shumeet Baluja, Don Barker, Tony Barrett, James Newton Bass, Don Beal, Howard Beck, Wolfgang Bibel, John Binder, Larry Bookman, David R. Boxall, Ronen Brafman, John Bresina, Gerhard Brewka, Selmer Bringsjord, Carla Brodley, Chris Brown, Emma Brunskill, Wilhelm Burger, Lauren Burka, Carlos Bustamante, Joao Cachopo, Murray Campbell, Norman Carver, Emmanuel Castro, Anil Chakravarthy, Dan Chisarick, Berthe Choueiry, Roberto Cipolla, David Cohen, James Coleman, Julie Ann Comparini, Corinna Cortes, Gary Cottrell, Ernest Davis, Tom Dean, Rina Dechter, Tom Dietterich, Peter Drake, Chuck Dyer, Doug Edwards, Robert Egginton, Asma’a El-Budrawy, Barbara Engelhardt, Kutluhan Erol, Oren Etzioni, Hana Filip, Douglas Fisher, Jeffrey Forbes, Ken Ford, Eric Fosler-Lussier, John Fosler, Jeremy Frank, Alex Franz, Bob Futrelle, Marek Galecki, Stefan Gerberding, Stuart Gill, Sabine Glesner, Seth Golub, Gosta Grahne, Russ Greiner, Eric Grimson, Barbara Grosz, Larry Hall, Steve Hanks, Othar Hansson, Ernst Heinz, Jim Hendler, Christoph Herrmann, Paul Hilfinger, Robert Holte, Vasant Honavar, Tim Huang, Seth Hutchinson, Joost Jacob, Mark Jelasity, Magnus Johansson, Istvan Jonyer, Dan Jurafsky, Leslie Kaelbling, Keiji Kanazawa, Surekha Kasibhatla, Simon Kasif, Henry Kautz, Gernot Kerschbaumer, Max Khesin, Richard Kirby, Dan Klein, Kevin Knight, Roland Koenig, Sven Koenig, Daphne Koller, Rich Korf, Benjamin Kuipers, James Kurien, John Lafferty, John Laird, Gus Lars-son, John Lazzaro, Jon LeBlanc, Jason Leatherman, Frank Lee, Jon Lehto, Edward Lim, Phil Long, Pierre Louveaux, Don Loveland, Sridhar Mahadevan, Tony Mancill, Jim Martin, Andy Mayer, John McCarthy, David McGrane, Jay Mendelsohn, Risto Miikkulanien, Brian Milch, Steve Minton, Vibhu Mittal, Mehryar Mohri, Leora Morgenstern, Stephen Muggleton, Kevin Murphy, Ron Musick, Sung Myaeng, Eric Nadeau, Lee Naish, Pandu Nayak, Bernhard Nebel, Stuart Nelson, XuanLong Nguyen, Nils Nilsson, Illah Nourbakhsh, Ali Nouri, Arthur Nunes-Harwitt, Steve Omohundro, David Page, David Palmer, David Parkes, Ron Parr, Mark Paskin, Tony Passera, Amit Patel, Michael Pazzani, Fernando Pereira, Joseph Perla, Wim Pijls, Ira Pohl, Martha Pollack, David Poole, Bruce Porter, Malcolm Pradhan, Bill Pringle, Lorraine Prior, Greg Provan, William Rapaport, Deepak Ravichandran, Ioannis Refanidis, Philip Resnik, Francesca Rossi, Sam Roweis, Richard Russell, Jonathan Schaeffer, Richard Scherl, Hinrich Schuetze, Lars Schuster, Bart Selman, Soheil Shams, Stuart Shapiro, Jude Shavlik, Yoram Singer, Satinder Singh, Daniel Sleator, David Smith, Bryan So, Robert Sproull, Lynn Stein, Larry Stephens, Andreas Stolcke, Paul Stradling, Devika Subramanian, Marek Suchenek, Rich Sutton, Jonathan Tash, Austin Tate, Bas Terwijn, Olivier Teytaud, Michael Thielscher, William Thompson, Sebastian Thrun, Eric Tiedemann, Mark Torrance, Randall Upham, Paul Utgoff, Peter van Beek, Hal Varian, Paulina Varshavskaya, Sunil Vemuri, Vandi Verma, Ubbo Visser, Jim Waldo, Toby Walsh, Bonnie Webber, Dan Weld, Michael Wellman, Kamin Whitehouse, Michael Dean White, Brian Williams, David Wolfe, Jason Wolfe, Bill Woods, Alden Wright, Jay Yagnik, Mark Yasuda, Richard Yen, Eliezer Yudkowsky, Weixiong Zhang, Ming Zhao, Shlomo Zilberstein, and our esteemed colleague Anonymous Reviewer.

## **About the Authors**

**Stuart Russell** was born in 1962 in Portsmouth, England. He received his B.A. with first-class honours in physics from Oxford University in 1982, and his Ph.D. in computer science from Stanford in 1986. He then joined the faculty of the University of California at Berkeley, where he is a professor of computer science, director of the Center for Intelligent Systems, and holder of the Smith–Zadeh Chair in Engineering. In 1990, he received the Presidential Young Investigator Award of the National Science Foundation, and in 1995 he was cowinner of the Computers and Thought Award. He was a 1996 Miller Professor of the University of California and was appointed to a Chancellor’s Professorship in 2000. In 1998, he gave the Forsythe Memorial Lectures at Stanford University. He is a Fellow and former Executive Council member of the American Association for Artificial Intelligence. He has published over 100 papers on a wide range of topics in artificial intelligence. His other books include *The Use of Knowledge in Analogy and Induction* and (with Eric Wefald) *Do the Right Thing: Studies in Limited Rationality.*

**Peter Norvig** is currently Director of Research at Google, Inc., and was the director responsible for the core Web search algorithms from 2002 to 2005. He is a Fellow of the American Association for Artificial Intelligence and the Association for Computing Machinery. Previously, he was head of the Computational Sciences Division at NASA Ames Research Center, where he oversaw NASA’s research and development in artificial intelligence and robotics, and chief scientist at Junglee, where he helped develop one of the first Internet information extraction services. He received a B.S. in applied mathematics from Brown University and a Ph.D. in computer science from the University of California at Berkeley. He received the Distinguished Alumni and Engineering Innovation awards from Berkeley and the Exceptional Achievement Medal from NASA. He has been a professor at the University of Southern California and a research faculty member at Berkeley. His other books are *Paradigms of AI Programming: Case Studies in Common Lisp* and *Verbmobil: A Translation System for Face-to-Face Dialog* and *Intelligent Help Systems for UNIX*.

## Contents

> **[I Artificial Intelligence](#index_split_008.html#filepos57346)**

> **[1 Introduction](#index_split_000.html#filepos57382)**

> [1.1 What Is AI?](#index_split_000.html#filepos59526)

> [1.2 The Foundations of Artificial Intelligence](#index_split_000.html#filepos74420)

> [1.3 The History of Artificial Intelligence](#index_split_000.html#filepos119432)

> [1.4 TheState ofthe Art](#index_split_000.html#filepos167956)

> [1.5 Summary, Bibliographical and Historical Notes, Exercises](#index_split_000.html#filepos173408)

> **[2 Intelligent Agents](#index_split_000.html#filepos187684)**

> [2.1 Agents and Environments](#index_split_000.html#filepos189297)

> [2.2 Good Behavior: The Concept of Rationality](#index_split_000.html#filepos195864)

> [2.3 TheNature of Environments](#index_split_000.html#filepos209973)

> [2.4 TheStructure of Agents](#index_split_000.html#filepos233909)

> [2.5 Summary, Bibliographical and Historical Notes, Exercises](#index_split_000.html#filepos279877)

> **[II Problem-solving](#index_split_010.html#filepos301649)**

> **[3 Solving Problems by Searching](#index_split_000.html#filepos301685)**

> [3.1 Problem-Solving Agents](#index_split_000.html#filepos304624)

> [3.2 Example Problems](#index_split_000.html#filepos323738)

> [3.3 Searching forSolutions](#index_split_000.html#filepos345175)

> [3.4 Uninformed Search Strategies](#index_split_000.html#filepos367450)

> [3.5 Informed (Heuristic) Search Strategies](#index_split_000.html#filepos401935)

> [3.6 Heuristic Functions](#index_split_000.html#filepos439536)

> [3.7 Summary, Bibliographical and Historical Notes, Exercises](#index_split_000.html#filepos461423)

> **[4 Beyond Classical Search](#index_split_000.html#filepos513290)**

> [4.1 Local Search Algorithms and Optimization Problems](#index_split_000.html#filepos515228)

> [4.2 Local Search in Continuous Spaces](#index_split_000.html#filepos545962)

> [4.3 Searching with Nondeterministic Actions](#index_split_000.html#filepos561013)

> [4.4 Searching with PartialObservations](#index_split_000.html#filepos575701)

> [4.5 Online Search Agents and Unknown Environments](#index_split_000.html#filepos605406)

> [4.6 Summary, Bibliographical and Historical Notes, Exercises](#index_split_000.html#filepos626971)

> **[5 Adversarial Search](#index_split_000.html#filepos660071)**

> [5.1 Games](#index_split_000.html#filepos660424)

> [5.2 Optimal Decisions inGames](#index_split_000.html#filepos670270)

> [5.3 Alpha–Beta Pruning](#index_split_000.html#filepos683038)

> [5.4 Imperfect Real-TimeDecisions](#index_split_000.html#filepos694564)

> [5.5 Stochastic Games](#index_split_000.html#filepos717429)

> [5.6 Partially Observable Games](#index_split_000.html#filepos727487)

> [5.7 State-of-the-Art Game Programs](#index_split_000.html#filepos744950)

> [5.8 Alternative Approaches](#index_split_000.html#filepos757873)

> [5.9 Summary, Bibliographical and Historical Notes, Exercises](#index_split_000.html#filepos764400)

> **[6 Constraint Satisfaction Problems](#index_split_000.html#filepos813005)**

> [6.1 Defining Constraint Satisfaction Problems](#index_split_000.html#filepos814885)

> [6.2 Constraint Propagation: Inference inCSPs](#index_split_000.html#filepos837717)

> [6.3 Backtracking Search forCSPs](#index_split_000.html#filepos863258)

> [6.4 Local Search forCSPs](#index_split_000.html#filepos889433)

> [6.5 TheStructure ofProblems](#index_split_000.html#filepos895328)

> [6.6 Summary, Bibliographical and Historical Notes, Exercises](#index_split_000.html#filepos910972)

> **[III Knowledge, reasoning, and planning](#index_split_014.html#filepos939343)**

> **[7 Logical Agents](#index_split_000.html#filepos939379)**

> [7.1 Knowledge-Based Agents](#index_split_000.html#filepos943668)

> [7.2 TheWumpus World](#index_split_000.html#filepos950662)

> [7.3 Logic](#index_split_000.html#filepos961559)

> [7.4 Propositional Logic: A Very Simple Logic](#index_split_000.html#filepos975576)

> [7.5 Propositional Theorem Proving](#index_split_000.html#filepos997899)

> [7.6 Effective Propositional Model Checking](#index_split_000.html#filepos1045666)

> [7.7 Agents Based on Propositional Logic](#index_split_000.html#filepos1065123)

> [7.8 Summary, Bibliographical and Historical Notes, Exercises](#index_split_000.html#filepos1100099)

> **[8 First-Order Logic](#index_split_000.html#filepos1149778)**

> [8.1 Representation Revisited](#index_split_000.html#filepos1151373)

> [8.2 Syntax and Semantics of First-Order Logic](#index_split_000.html#filepos1172048)

> [8.3 Using First-Order Logic](#index_split_000.html#filepos1212170)

> [8.4 Knowledge Engineering inFirst-Order Logic](#index_split_000.html#filepos1240132)

> [8.5 Summary, Bibliographical and Historical Notes, Exercises](#index_split_000.html#filepos1262123)

> **[9 Inference in First-Order Logic](#index_split_015.html#filepos1300686)**

> [9.1 Propositional vs. First-Order Inference](#index_split_015.html#filepos1302407)

> [9.2 Unification and Lifting](#index_split_015.html#filepos1312580)

> [9.3 ForwardChaining](#index_split_015.html#filepos1331309)

> [9.4 Backward Chaining](#index_split_015.html#filepos1358569)

> [9.5 Resolution](#index_split_015.html#filepos1390064)

> [9.6 Summary, Bibliographical and Historical Notes, Exercises](#index_split_015.html#filepos1434686)

> **[10 Classical Planning](#index_split_015.html#filepos1477055)**

> [10.1 Definition of Classical Planning](#index_split_015.html#filepos1479162)

> [10.2 Algorithms forPlanning asState-Space Search](#index_split_015.html#filepos1502190)

> [10.3 Planning Graphs](#index_split_015.html#filepos1526840)

>  [10.4 Other Classical Planning Approaches](#index_split_015.html#filepos1561140)

> [10.5 Analysis ofPlanning Approaches](#index_split_015.html#filepos1578979)

> [10.6 Summary, Bibliographical and Historical Notes, Exercises](#index_split_015.html#filepos1583287)

> **[11 Planning and Acting in the Real World](#index_split_015.html#filepos1612250)**

> [11.1 Time,Schedules, and Resources](#index_split_015.html#filepos1613898)

> [11.2 Hierarchical Planning](#index_split_015.html#filepos1629823)

> [11.3 Planning and Acting in Nondeterministic Domains](#index_split_015.html#filepos1663823)

> [11.4 Multiagent Planning](#index_split_015.html#filepos1705027)

> [11.5 Summary, Bibliographical and Historical Notes, Exercises](#index_split_015.html#filepos1725336)

> **[12 Knowledge Representation](#index_split_015.html#filepos1750417)**

> [12.1 Ontological Engineering](#index_split_015.html#filepos1752097)

> [12.2 Categories and Objects](#index_split_015.html#filepos1760995)

> [12.3 Events](#index_split_015.html#filepos1786001)

> [12.4 Mental Events and Mental Objects](#index_split_015.html#filepos1798883)

> [12.5 Reasoning Systems forCategories](#index_split_015.html#filepos1812960)

> [12.6 Reasoning with Default Information](#index_split_015.html#filepos1828298)

> [12.7 The Internet Shopping World](#index_split_015.html#filepos1847912)

> [12.8 Summary, Bibliographical and Historical Notes, Exercises](#index_split_015.html#filepos1864671)

> **[IV Uncertain knowledge and reasoning](#index_split_015.html#filepos1915678)**

> **[13 Quantifying Uncertainty](#index_split_015.html#filepos1915714)**

> [13.1 Acting under Uncertainty](#index_split_015.html#filepos1916022)

> [13.2 Basic Probability Notation](#index_split_015.html#filepos1932204)

> [13.3 Inference Using Full Joint Distributions](#index_split_015.html#filepos1960284)

> [13.4 Independence](#index_split_015.html#filepos1973193)

> [13.5 Bayes’ Rule and ItsUse](#index_split_015.html#filepos1978817)

> [13.6 TheWumpus World Revisited](#index_split_015.html#filepos1994740)

> [13.7 Summary, Bibliographical and Historical Notes, Exercises](#index_split_015.html#filepos2004818)

> **[14 Probabilistic Reasoning](#index_split_015.html#filepos2036437)**

> [14.1 Representing Knowledge in an Uncertain Domain](#index_split_015.html#filepos2037896)

> [14.2 TheSemantics of Bayesian Networks](#index_split_015.html#filepos2046868)

> [14.3 Efficient Representation of Conditional Distributions](#index_split_015.html#filepos2067276)

> [14.4 Exact Inference inBayesian Networks](#index_split_015.html#filepos2082333)

> [14.5 Approximate Inference in Bayesian Networks](#index_split_015.html#filepos2108681)

> [14.6 Relational and First-Order Probability Models](#index_split_015.html#filepos2142569)

> [14.7 Other Approaches toUncertain Reasoning](#index_split_015.html#filepos2170328)

> [14.8 Summary, Bibliographical and Historical Notes, Exercises](#index_split_015.html#filepos2193360)

> **[15 Probabilistic Reasoning over Time](#index_split_015.html#filepos2253296)**

> [15.1 Timeand Uncertainty](#index_split_015.html#filepos2255972)

> [15.2 Inference inTemporal Models](#index_split_015.html#filepos2271869)

> [15.3 Hidden Markov Models](#index_split_015.html#filepos2303086)

> [15.4 Kalman Filters](#index_split_015.html#filepos2322629)

> [15.5 Dynamic Bayesian Networks](#index_split_015.html#filepos2347644)

> [15.6 Keeping Track ofMany Objects](#index_split_015.html#filepos2381766)

> [15.7 Summary, Bibliographical and Historical Notes, Exercises](#index_split_015.html#filepos2393669)

> **[16 Making Simple Decisions](#index_split_015.html#filepos2423989)**

> [16.1 Combining Beliefs and Desires under Uncertainty](#index_split_015.html#filepos2425965)

> [16.2 The Basis of Utility Theory](#index_split_015.html#filepos2430976)

> [16.3 Utility Functions](#index_split_015.html#filepos2443064)

> [16.4 Multiattribute Utility Functions](#index_split_015.html#filepos2471492)

> [16.5 Decision Networks](#index_split_015.html#filepos2489486)

> [16.6 TheValue ofInformation](#index_split_015.html#filepos2497710)

> [16.7 Decision-Theoretic Expert Systems](#index_split_015.html#filepos2514710)

> [16.8 Summary, Bibliographical and Historical Notes, Exercises](#index_split_015.html#filepos2524762)

> **[17 Making Complex Decisions](#index_split_015.html#filepos2562268)**

> [17.1 Sequential Decision Problems](#index_split_015.html#filepos2564585)

> [17.2 Value Iteration](#index_split_015.html#filepos2589617)

> [17.3 Policy Iteration](#index_split_015.html#filepos2605479)

> [17.4 Partially Observable MDPs](#index_split_015.html#filepos2612205)

> [17.5 Decisions with Multiple Agents: Game Theory](#index_split_015.html#filepos2641741)

> [17.6 Mechanism Design](#index_split_015.html#filepos2693600)

> [17.7 Summary, Bibliographical and Historical Notes, Exercises](#index_split_015.html#filepos2718821)

> **[V Learning](#index_split_015.html#filepos2752984)**

> **[18 Learning from Examples](#index_split_015.html#filepos2753020)**

> [18.1 FormsofLearning](#index_split_015.html#filepos2755523)

> [18.2 Supervised Learning](#index_split_015.html#filepos2763522)

> [18.3 Learning Decision Trees](#index_split_015.html#filepos2773434)

> [18.4 Evaluating and Choosing the Best Hypothesis](#index_split_015.html#filepos2809870)

> [18.5 TheTheory of Learning](#index_split_015.html#filepos2832545)

> [18.6 Regression and Classification with Linear Models](#index_split_015.html#filepos2848469)

> [18.7 Artificial Neural Networks](#index_split_015.html#filepos2883871)

> [18.8 Nonparametric Models](#index_split_015.html#filepos2915290)

> [18.9 Support Vector Machines](#index_split_015.html#filepos2941759)

> [18.10 Ensemble Learning](#index_split_015.html#filepos2957814)

> [18.11 Practical Machine Learning](#index_split_015.html#filepos2974811)

> [18.12 Summary, Bibliographical and Historical Notes, Exercises](#index_split_015.html#filepos2987762)

> **[19 Knowledge in Learning](#index_split_015.html#filepos3033423)**

> [19.1 ALogical Formulation ofLearning](#index_split_015.html#filepos3034798)

>  [19.2 Knowledge in Learning](#index_split_015.html#filepos3066600)

> [19.3 Explanation-Based Learning](#index_split_015.html#filepos3079688)

> [19.4 Learning Using Relevance Information](#index_split_015.html#filepos3094950)

> [19.5 Inductive Logic Programming](#index_split_015.html#filepos3106297)

> [19.6 Summary, Bibliographical and Historical Notes, Exercises](#index_split_015.html#filepos3139152)

> **[20 Learning Probabilistic Models](#index_split_015.html#filepos3158034)**

> [20.1 Statistical Learning](#index_split_015.html#filepos3159740)

> [20.2 Learning withComplete Data](#index_split_015.html#filepos3173403)

> [20.3 Learning withHidden Variables: TheEMAlgorithm](#index_split_015.html#filepos3208378)

> [20.4 Summary, Bibliographical and Historical Notes, Exercises](#index_split_015.html#filepos3240410)

> **[21 Reinforcement Learning](#index_split_015.html#filepos3262268)**

> [21.1 Introduction](#index_split_015.html#filepos3262557)

> [21.2 Passive Reinforcement Learning](#index_split_015.html#filepos3270122)

> [21.3 ActiveReinforcement Learning](#index_split_015.html#filepos3293365)

> [21.4 Generalization inReinforcement Learning](#index_split_015.html#filepos3316083)

> [21.5 Policy Search](#index_split_015.html#filepos3327643)

> [21.6 Applications of Reinforcement Learning](#index_split_015.html#filepos3338180)

> [21.7 Summary, Bibliographical and Historical Notes, Exercises](#index_split_015.html#filepos3346082)

> **[VI Communicating, perceiving, and acting](#index_split_015.html#filepos3374136)**

> **[22 Natural Language Processing](#index_split_015.html#filepos3374172)**

> [22.1 Language Models](#index_split_015.html#filepos3376404)

> [22.2 Text Classification](#index_split_015.html#filepos3395285)

> [22.3 Information Retrieval](#index_split_015.html#filepos3404559)

> [22.4 Information Extraction](#index_split_015.html#filepos3430699)

> [22.5 Summary, Bibliographical and Historical Notes, Exercises](#index_split_015.html#filepos3464966)

> **[23 Natural Language for Communication](#index_split_015.html#filepos3484309)**

> [23.1 Phrase Structure Grammars](#index_split_015.html#filepos3485868)

> [23.2 Syntactic Analysis (Parsing).](#index_split_015.html#filepos3499417)

> [23.3 Augmented Grammarsand Semantic Interpretation](#index_split_015.html#filepos3516473)

> [23.4 Machine Translation](#index_split_015.html#filepos3552675)

> [23.5 Speech Recognition](#index_split_015.html#filepos3576952)

> [23.6 Summary, Bibliographical and Historical Notes, Exercises](#index_split_015.html#filepos3597598)

> **[24 Perception](#index_split_015.html#filepos3631932)**

> [24.1 Image Formation](#index_split_015.html#filepos3638349)

> [24.2 Early Image-Processing Operations](#index_split_015.html#filepos3659517)

> [24.3 Object Recognition by Appearance](#index_split_015.html#filepos3682637)

> [24.4 Reconstructing the 3D World](#index_split_015.html#filepos3698370)

> [24.5 Object Recognition from Structural Information](#index_split_015.html#filepos3731331)

>  [24.6 Using Vision](#index_split_015.html#filepos3743787)

> [24.7 Summary, Bibliographical and Historical Notes, Exercises](#index_split_015.html#filepos3758983)

> **[25 Robotics](#index_split_015.html#filepos3777962)**

> [25.1 Introduction](#index_split_015.html#filepos3778219)

> [25.2 Robot Hardware](#index_split_015.html#filepos3785284)

> [25.3 Robotic Perception](#index_split_015.html#filepos3803908)

> [25.4 Planning toMove](#index_split_015.html#filepos3828107)

> [25.5 Planning Uncertain Movements](#index_split_015.html#filepos3852926)

> [25.6 Moving](#index_split_015.html#filepos3865983)

> [25.7 Robotic Software Architectures](#index_split_015.html#filepos3888157)

> [25.8 Application Domains](#index_split_015.html#filepos3900754)

> [25.9 Summary, Bibliographical and Historical Notes, Exercises](#index_split_015.html#filepos3912049)

> **[VII Conclusions](#index_split_015.html#filepos3949385)**

> **[26 Philosophical Foundations](#index_split_015.html#filepos3949421)**

> [26.1 Weak AI: Can Machines Act Intelligently?](#index_split_015.html#filepos3951057)

> [26.2 Strong AI: CanMachines Really Think?](#index_split_015.html#filepos3974175)

> [26.3 The Ethics and Risks of Developing Artificial Intelligence](#index_split_015.html#filepos4008318)

> [26.4 Summary, Bibliographical and Historical Notes, Exercises](#index_split_015.html#filepos4034485)

> **[27 AI: The Present and Future](#index_split_015.html#filepos4049026)**

> [27.1 Agent Components](#index_split_015.html#filepos4051305)

> [27.2 Agent Architectures](#index_split_015.html#filepos4061517)

> [27.3 AreWeGoing inthe Right Direction?](#index_split_015.html#filepos4067811)

> [27.4 What If AI Does Succeed?](#index_split_015.html#filepos4077137)

> **[A Mathematical background](#index_split_015.html#filepos4081264)**

> [A.1 Complexity Analysis and *O*()Notation](#index_split_015.html#filepos4081395)

> [A.2 Vectors, Matrices, and Linear Algebra](#index_split_015.html#filepos4092089)

> [A.3 Probability Distributions](#index_split_015.html#filepos4099913)

> **[B Notes on Languages and Algorithms](#index_split_015.html#filepos4111033)**

> [B.1 Defining Languages with Backus–Naur Form (BNF)](#index_split_015.html#filepos4111174)

> [B.2 Describing Algorithms with Pseudocode](#index_split_015.html#filepos4115418)

> [B.3 Online Help](#index_split_015.html#filepos4120373)

> **[Bibliography](#index_split_015.html#filepos4121102)**

> **[Index](#index_split_015.html#filepos4555736)**

## **1 INTRODUCTION**

> *In which we try to explain why we consider artificial intelligence to be a subject most worthy of study, and in which we try to decide what exactly it is, this being a good thing to decide before embarking.*

We call ourselves *Homo sapiens*—man the wise—because our **intelligence** is so important to us. For thousands of years, we have tried to understand *how we think*; that is, how a mere handful of matter can perceive, understand, predict, and manipulate a world far larger and more complicated than itself. The field of **artificial intelligence**, or AI, goes further still: it attempts not just to understand but also to *build* intelligent entities.

* * *

INTELLIGENCE

* * *

* * *

ARTIFICIAL INTELLIGENCE

* * *

AI is one of the newest fields in science and engineering. Work started in earnest soon after World War II, and the name itself was coined in 1956. Along with molecular biology, AI is regularly cited as the “field I would most like to be in” by scientists in other disciplines. A student in physics might reasonably feel that all the good ideas have already been taken by Galileo, Newton, Einstein, and the rest. AI, on the other hand, still has openings for several full-time Einsteins and Edisons.

AI currently encompasses a huge variety of subfields, ranging from the general (learning and perception) to the specific, such as playing chess, proving mathematical theorems, writing poetry, driving a car on a crowded street, and diagnosing diseases. AI is relevant to any intellectual task; it is truly a universal field.

### 1.1 WHAT IS AI?

We have claimed that AI is exciting, but we have not said what it *is*. In [Figure 1.1](#index_split_008.html#filepos61002) we see eight definitions of AI, laid out along two dimensions. The definitions on top are concerned with *thought processes* and *reasoning*, whereas the ones on the bottom address *behavior*. The definitions on the left measure success in terms of fidelity to *human* performance, whereas the ones on the right measure against an *ideal* performance measure, called **rationality**. A system is rational if it does the “right thing,” given what it knows.

* * *

RATIONALITY

* * *

Historically, all four approaches to AI have been followed, each by different people with different methods. A human-centered approach must be in part an empirical science, involving observations and hypotheses about human behavior. A rationalist[¹](#index_split_015.html#filepos5563253) approach involves a combination of mathematics and engineering. The various group have both disparaged and helped each other. Let us look at the four approaches in more detail.

> ![table](images/00007.jpg)

> **Figure 1.1** Some definitions of artificial intelligence, organized into four categories.

#### **1.1.1 Acting humanly: The Turing Test approach**

The **Turing Test**, proposed by Alan Turing (1950), was designed to provide a satisfactory operational definition of intelligence. A computer passes the test if a human interrogator, after posing some written questions, cannot tell whether the written responses come from a person or from a computer. [Chapter 26](#index_split_015.html#filepos3949421) discusses the details of the test and whether a computer would really be intelligent if it passed. For now, we note that programming a computer to pass a rigorously applied test provides plenty to work on. The computer would need to possess the following capabilities:

* * *

TURING TEST

* * *

> • **natural language processing** to enable it to communicate successfully in English;

* * *

NATURAL LANGUAGE PROCESSING

* * *

> • **knowledge representation** to store what it knows or hears;

* * *

KNOWLEDGE REPRESENTATION

* * *

> • **automated reasoning** to use the stored information to answer questions and to draw new conclusions;

* * *

AUTOMATED REASONING

* * *

> • **machine learning** to adapt to new circumstances and to detect and extrapolate patterns.

* * *

MACHINE LEARNING

* * *

Turing’s test deliberately avoided direct physical interaction between the interrogator and the computer, because *physical* simulation of a person is unnecessary for intelligence. However, the so-called **total Turing Test** includes a video signal so that the interrogator can test the subject’s perceptual abilities, as well as the opportunity for the interrogator to pass physical objects “through the hatch.” To pass the total Turing Test, the computer will need

* * *

TOTAL TURING TEST

* * *

> • **computer vision** to perceive objects, and

* * *

COMPUTER VISION

* * *

> • **robotics** to manipulate objects and move about.

* * *

ROBOTICS

* * *

These six disciplines compose most of AI, and Turing deserves credit for designing a test that remains relevant 60 years later. Yet AI researchers have devoted little effort to passing the Turing Test, believing that it is more important to study the underlying principles of intelligence than to duplicate an exemplar. The quest for “artificial flight” succeeded when the Wright brothers and others stopped imitating birds and started using wind tunnels and learning about aerodynamics. Aeronautical engineering texts do not define the goal of their field as making “machines that fly so exactly like pigeons that they can fool even other pigeons.”

#### **1.1.2 Thinking humanly: The cognitive modeling approach**

If we are going to say that a given program thinks like a human, we must have some way of determining how humans think. We need to get *inside* the actual workings of human minds. There are three ways to do this: through introspection—trying to catch our own thoughts as they go by; through psychological experiments—observing a person in action; and through brain imaging—observing the brain in action. Once we have a sufficiently precise theory of the mind, it becomes possible to express the theory as a computer program. If the program’s input–output behavior matches corresponding human behavior, that is evidence that some of the program’s mechanisms could also be operating in humans. For example, Allen Newell and Herbert Simon, who developed GPS, the “General Problem Solver” (Newell and Simon, 1961), were not content merely to have their program solve problems correctly. They were more concerned with comparing the trace of its reasoning steps to traces of human subjects solving the same problems. The interdisciplinary field of **cognitive science** brings together computer models from AI and experimental techniques from psychology to construct precise and testable theories of the human mind.

* * *

COGNITIVE SCIENCE

* * *

Cognitive science is a fascinating field in itself, worthy of several textbooks and at least one encyclopedia (Wilson and Keil, 1999). We will occasionally comment on similarities or differences between AI techniques and human cognition. Real cognitive science, however, is necessarily based on experimental investigation of actual humans or animals. We will leave that for other books, as we assume the reader has only a computer for experimentation.

In the early days of AI there was often confusion between the approaches: an author would argue that an algorithm performs well on a task and that it is *therefore* a good model of human performance, or vice versa. Modern authors separate the two kinds of claims; this distinction has allowed both AI and cognitive science to develop more rapidly. The two fields continue to fertilize each other, most notably in computer vision, which incorporates neurophysiological evidence into computational models.

#### **1.1.3 Thinking rationally: The “laws of thought” approach**

The Greek philosopher Aristotle was one of the first to attempt to codify “right thinking,” that is, irrefutable reasoning processes. His **syllogisms** provided patterns for argument structures that always yielded correct conclusions when given correct premises—for example, “Socrates is a man; all men are mortal; therefore, Socrates is mortal.” These laws of thought were supposed to govern the operation of the mind; their study initiated the field called **logic**.

* * *

SYLLOGISM

* * *

* * *

LOGIC

* * *

Logicians in the 19th century developed a precise notation for statements about all kinds of objects in the world and the relations among them. (Contrast this with ordinary arithmetic notation, which provides only for statements about *numbers*.) By 1965, programs existed that could, in principle, solve *any* solvable problem described in logical notation. (Although if no solution exists, the program might loop forever.) The so-called **logicist** tradition within artificial intelligence hopes to build on such programs to create intelligent systems.

* * *

LOGICIST

* * *

There are two main obstacles to this approach. First, it is not easy to take informal knowledge and state it in the formal terms required by logical notation, particularly when the knowledge is less than 100% certain. Second, there is a big difference between solving a problem “in principle” and solving it in practice. Even problems with just a few hundred facts can exhaust the computational resources of any computer unless it has some guidance as to which reasoning steps to try first. Although both of these obstacles apply to *any* attempt to build computational reasoning systems, they appeared first in the logicist tradition.

#### **1.1.4 Acting rationally: The rational agent approach**

An **agent** is just something that acts (*agent* comes from the Latin *agere*, to do). Of course, all computer programs do something, but computer agents are expected to do more: operate autonomously, perceive their environment, persist over a prolonged time period, adapt to change, and create and pursue goals. A **rational agent** is one that acts so as to achieve the best outcome or, when there is uncertainty, the best expected outcome.

* * *

AGENT

* * *

* * *

RATIONAL AGENT

* * *

In the “laws of thought” approach to AI, the emphasis was on correct inferences. Making correct inferences is sometimes *part* of being a rational agent, because one way to act rationally is to reason logically to the conclusion that a given action will achieve one’s goals and then to act on that conclusion. On the other hand, correct inference is not *all* of rationality; in some situations, there is no provably correct thing to do, but something must still be done. There are also ways of acting rationally that cannot be said to involve inference. For example, recoiling from a hot stove is a reflex action that is usually more successful than a slower action taken after careful deliberation.

All the skills needed for the Turing Test also allow an agent to act rationally. Knowledge representation and reasoning enable agents to reach good decisions. We need to be able to generate comprehensible sentences in natural language to get by in a complex society. We need learning not only for erudition, but also because it improves our ability to generate effective behavior.

The rational-agent approach has two advantages over the other approaches. First, it is more general than the “laws of thought” approach because correct inference is just one of several possible mechanisms for achieving rationality. Second, it is more amenable to scientific development than are approaches based on human behavior or human thought. The standard of rationality is mathematically well defined and completely general, and can be “unpacked” to generate agent designs that provably achieve it. Human behavior, on the other hand, is well adapted for one specific environment and is defined by, well, the sum total of all the things that humans do. *This book therefore concentrates on general principles of rational agents and on components for constructing them.* We will see that despite the apparent simplicity with which the problem can be stated, an enormous variety of issues come up when we try to solve it. [Chapter 2](#index_split_000.html#filepos187684) outlines some of these issues in more detail.

![hand](images/00006.jpg)

One important point to keep in mind: We will see before too long that achieving perfect rationality—always doing the right thing—is not feasible in complicated environments. The computational demands are just too high. For most of the book, however, we will adopt the working hypothesis that perfect rationality is a good starting point for analysis. It simplifies the problem and provides the appropriate setting for most of the foundational material in the field. [Chapters 5](#index_split_000.html#filepos660071) and [17](#index_split_015.html#filepos2562268) deal explicitly with the issue of **limited rationality**—acting appropriately when there is not enough time to do all the computations one might like.

* * *

LIMITED RATIONALITY

* * *

### 1.2 THE FOUNDATIONS OF ARTIFICIAL INTELLIGENCE

In this section, we provide a brief history of the disciplines that contributed ideas, viewpoints, and techniques to AI. Like any history, this one is forced to concentrate on a small number of people, events, and ideas and to ignore others that also were important. We organize the history around a series of questions. We certainly would not wish to give the impression that these questions are the only ones the disciplines address or that the disciplines have all been working toward AI as their ultimate fruition.

#### **1.2.1 Philosophy**

> • Can formal rules be used to draw valid conclusions?

> • How does the mind arise from a physical brain?

> • Where does knowledge come from?

> • How does knowledge lead to action?

Aristotle (384–322 B.C.), whose bust appears on the front cover of this book, was the first to formulate a precise set of laws governing the rational part of the mind. He developed an informal system of syllogisms for proper reasoning, which in principle allowed one to generate conclusions mechanically, given initial premises. Much later, Ramon Lull (d. 1315) had the idea that useful reasoning could actually be carried out by a mechanical artifact. Thomas Hobbes (1588–1679) proposed that reasoning was like numerical computation, that “we add and subtract in our silent thoughts.” The automation of computation itself was already well under way. Around 1500, Leonardo da Vinci (1452–1519) designed but did not build a mechanical calculator; recent reconstructions have shown the design to be functional. The first known calculating machine was constructed around 1623 by the German scientist Wilhelm Schickard (1592–1635), although the Pascaline, built in 1642 by Blaise Pascal (1623–1662), is more famous. Pascal wrote that “the arithmetical machine produces effects which appear nearer to thought than all the actions of animals.” Gottfried Wilhelm Leibniz (1646–1716) built a mechanical device intended to carry out operations on concepts rather than numbers, but its scope was rather limited. Leibniz did surpass Pascal by building a calculator that could add, subtract, multiply, and take roots, whereas the Pascaline could only add and subtract. Some speculated that machines might not just do calculations but actually be able to think and act on their own. In his 1651 book *Leviathan*, Thomas Hobbes suggested the idea of an “artificial animal,” arguing “For what is the heart but a spring; and the nerves, but so many strings; and the joints, but so many wheels.”

It’s one thing to say that the mind operates, at least in part, according to logical rules, and to build physical systems that emulate some of those rules; it’s another to say that the mind itself *is* such a physical system. René Descartes (1596–1650) gave the first clear discussion of the distinction between mind and matter and of the problems that arise. One problem with a purely physical conception of the mind is that it seems to leave little room for free will: if the mind is governed entirely by physical laws, then it has no more free will than a rock “deciding” to fall toward the center of the earth. Descartes was a strong advocate of the power of reasoning in understanding the world, a philosophy now called **rationalism**, and one that counts Aristotle and Leibnitz as members. But Descartes was also a proponent of **dualism**. He held that there is a part of the human mind (or soul or spirit) that is outside of nature, exempt from physical laws. Animals, on the other hand, did not possess this dual quality; they could be treated as machines. An alternative to dualism is **materialism**, which holds that the brain’s operation according to the laws of physics *constitutes* the mind. Free will is simply the way that the perception of available choices appears to the choosing entity.

* * *

RATIONALISM

* * *

* * *

DUALISM

* * *

* * *

MATERIALISM

* * *

Given a physical mind that manipulates knowledge, the next problem is to establish the source of knowledge. The **empiricism** movement, starting with Francis Bacon’s (1561–1626) *Novum Organum*,[²](#index_split_015.html#filepos5563819) is characterized by a dictum of John Locke (1632–1704): “Nothing is in the understanding, which was not first in the senses.” David Hume’s (1711–1776) *A Treatise of Human Nature* (Hume, 1739) proposed what is now known as the principle of **induction**: that general rules are acquired by exposure to repeated associations between their elements. Building on the work of Ludwig Wittgenstein (1889–1951) and Bertrand Russell (1872–1970), the famous Vienna Circle, led by Rudolf Carnap (1891–1970), developed the doctrine of **logical positivism**. This doctrine holds that all knowledge can be characterized by logical theories connected, ultimately, to **observation sentences** that correspond to sensory inputs; thus logical positivism combines rationalism and empiricism.[³](#index_split_015.html#filepos5564100) The **confirmation theory** of Carnap and Carl Hempel (1905–1997) attempted to analyze the acquisition of knowl edge from experience. Carnap’s book *The Logical Structure of the World* (1928) defined an explicit computational procedure for extracting knowledge from elementary experiences. It was probably the first theory of mind as a computational process.

* * *

EMPIRICISM

* * *

* * *

INDUCTION

* * *

* * *

LOGICAL POSITIVISM

* * *

* * *

OBSERVATION SENTENCES

* * *

* * *

CONFIRMATION THEORY

* * *

The final element in the philosophical picture of the mind is the connection between knowledge and action. This question is vital to AI because intelligence requires action as well as reasoning. Moreover, only by understanding how actions are justified can we understand how to build an agent whose actions are justifiable (or rational). Aristotle argued (in *De Motu Animalium*) that actions are justified by a logical connection between goals and knowledge of the action’s outcome (the last part of this extract also appears on the front cover of this book, in the original Greek):

> But how does it happen that thinking is sometimes accompanied by action and sometimes not, sometimes by motion, and sometimes not? It looks as if almost the same thing happens as in the case of reasoning and making inferences about unchanging objects. But in that case the end is a speculative proposition… whereas here the conclusion which results from the two premises is an action…. I need covering; a cloak is a covering. I need a cloak. What I need, I have to make; I need a cloak. I have to make a cloak. And the conclusion, the “I have to make a cloak,” is an action.

In the *Nicomachean Ethics* (Book III. 3, 1112b), Aristotle further elaborates on this topic, suggesting an algorithm:

> We deliberate not about ends, but about means. For a doctor does not deliberate whether he shall heal, nor an orator whether he shall persuade,… They assume the end and consider how and by what means it is attained, and if it seems easily and best produced thereby; while if it is achieved by one means only they consider *how* it will be achieved by this and by what means *this* will be achieved, till they come to the first cause,… and what is last in the order of analysis seems to be first in the order of becoming. And if we come on an impossibility, we give up the search, e.g., if we need money and this cannot be got; but if a thing appears possible we try to do it.

Aristotle’s algorithm was implemented 2300 years later by Newell and Simon in their GPS program. We would now call it a regression planning system (see [Chapter 10](#index_split_015.html#filepos1477055)).

Goal-based analysis is useful, but does not say what to do when several actions will achieve the goal or when no action will achieve it completely. Antoine Arnauld (1612–1694) correctly described a quantitative formula for deciding what action to take in cases like this (see [Chapter 16](#index_split_015.html#filepos2423989)). John Stuart Mill’s (1806–1873) book *Utilitarianism* (Mill, 1863) promoted the idea of rational decision criteria in all spheres of human activity. The more formal theory of decisions is discussed in the following section.

#### **1.2.2 Mathematics**

> • What are the formal rules to draw valid conclusions?

> • What can be computed?

> • How do we reason with uncertain information?

Philosophers staked out some of the fundamental ideas of AI, but the leap to a formal science required a level of mathematical formalization in three fundamental areas: logic, computation, and probability.

The idea of formal logic can be traced back to the philosophers of ancient Greece, but its mathematical development really began with the work of George Boole (1815–1864), who worked out the details of propositional, or Boolean, logic (Boole, 1847). In 1879, Gottlob Frege (1848–1925) extended Boole’s logic to include objects and relations, creating the first-order logic that is used today.[⁴](#index_split_015.html#filepos5564466) Alfred Tarski (1902–1983) introduced a theory of reference that shows how to relate the objects in a logic to objects in the real world.

The next step was to determine the limits of what could be done with logic and computation. The first nontrivial **algorithm** is thought to be Euclid’s algorithm for computing greatest common divisors. The word *algorithm* (and the idea of studying them) comes from al-Khowarazmi, a Persian mathematician of the 9th century, whose writings also introduced Arabic numerals and algebra to Europe. Boole and others discussed algorithms for logical deduction, and, by the late 19th century, efforts were under way to formalize general mathematical reasoning as logical deduction. In 1930, Kurt Gödel (1906–1978) showed that there exists an effective procedure to prove any true statement in the first-order logic of Frege and Russell, but that first-order logic could not capture the principle of mathematical induction needed to characterize the natural numbers. In 1931, Gödel showed that limits on deduction do exist. His **incompleteness theorem** showed that in any formal theory as strong as Peano arithmetic (the elementary theory of natural numbers), there are true statements that are undecidable in the sense that they have no proof within the theory.

* * *

ALGORITHM

* * *

* * *

INCOMPLETENESS THEOREM

* * *

This fundamental result can also be interpreted as showing that some functions on the integers cannot be represented by an algorithm—that is, they cannot be computed. This motivated Alan Turing (1912–1954) to try to characterize exactly which functions *are* **computable**—capable of being computed. This notion is actually slightly problematic because the notion of a computation or effective procedure really cannot be given a formal definition. However, the Church–Turing thesis, which states that the Turing machine (Turing, 1936) is capable of computing any computable function, is generally accepted as providing a sufficient definition. Turing also showed that there were some functions that no Turing machine can compute. For example, no machine can tell *in general* whether a given program will return an answer on a given input or run forever.

* * *

COMPUTABLE

* * *

Although decidability and computability are important to an understanding of computation, the notion of **tractability** has had an even greater impact. Roughly speaking, a problem is called intractable if the time required to solve instances of the problem grows exponentially with the size of the instances. The distinction between polynomial and exponential growth in complexity was first emphasized in the mid-1960s (Cobham, 1964; Edmonds, 1965). It is important because exponential growth means that even moderately large instances cannot be solved in any reasonable time. Therefore, one should strive to divide the overall problem of generating intelligent behavior into tractable subproblems rather than intractable ones.

* * *

TRACTABILITY

* * *

How can one recognize an intractable problem? The theory of **NP-completeness**, pioneered by Steven Cook (1971) and Richard Karp (1972), provides a method. Cook and Karp showed the existence of large classes of canonical combinatorial search and reasoning problems that are NP-complete. Any problem class to which the class of NP-complete problems can be reduced is likely to be intractable. (Although it has not been proved that NP-complete problems are necessarily intractable, most theoreticians believe it.) These results contrast with the optimism with which the popular press greeted the first computers—“Electronic Super-Brains” that were “Faster than Einstein!” Despite the increasing speed of computers, careful use of resources will characterize intelligent systems. Put crudely, the world is an *extremely* large problem instance! Work in AI has helped explain why some instances of NP-complete problems are hard, yet others are easy (Cheeseman **et al.**, 1991).

* * *

NP-COMPLETENESS

* * *

Besides logic and computation, the third great contribution of mathematics to AI is the theory of **probability**. The Italian Gerolamo Cardano (1501–1576) first framed the idea of probability, describing it in terms of the possible outcomes of gambling events. In 1654, Blaise Pascal (1623–1662), in a letter to Pierre Fermat (1601–1665), showed how to predict the future of an unfinished gambling game and assign average payoffs to the gamblers. Probability quickly became an invaluable part of all the quantitative sciences, helping to deal with uncertain measurements and incomplete theories. James Bernoulli (1654–1705), Pierre Laplace (1749–1827), and others advanced the theory and introduced new statistical methods. Thomas Bayes (1702–1761), who appears on the front cover of this book, proposed a rule for updating probabilities in the light of new evidence. Bayes’ rule underlies most modern approaches to uncertain reasoning in AI systems.

* * *

PROBABILITY

* * *

#### **1.2.3 Economics**

> • How should we make decisions so as to maximize payoff?

> • How should we do this when others may not go along?

> • How should we do this when the payoff may be far in the future?

The science of economics got its start in 1776, when Scottish philosopher Adam Smith (1723–1790) published *An Inquiry into the Nature and Causes of the Wealth of Nations*. While the ancient Greeks and others had made contributions to economic thought, Smith was the first to treat it as a science, using the idea that economies can be thought of as consisting of individual agents maximizing their own economic well-being. Most people think of economics as being about money, but economists will say that they are really studying how people make choices that lead to preferred outcomes. When McDonald’s offers a hamburger for a dollar, they are asserting that they would prefer the dollar and hoping that customers will prefer the hamburger. The mathematical treatment of “preferred outcomes” or **utility** was first formalized by Léon Walras (pronounced “Valrasse”) (1834-1910) and was improved by Frank Ramsey (1931) and later by John von Neumann and Oskar Morgenstern in their book *The Theory of Games and Economic Behavior* (1944).

* * *

UTILITY

* * *

**Decision theory**, which combines probability theory with utility theory, provides a formal and complete framework for decisions (economic or otherwise) made under uncertainty—that is, in cases where probabilistic descriptions appropriately capture the decision maker’s environment. This is suitable for “large” economies where each agent need pay no attention to the actions of other agents as individuals. For “small” economies, the situation is much more like a **game**: the actions of one player can significantly affect the utility of another (either positively or negatively). Von Neumann and Morgenstern’s development of **game theory** (see also Luce and Raiffa, 1957) included the surprising result that, for some games, a rational agent should adopt policies that are (or least appear to be) randomized. Unlike decision theory, game theory does not offer an unambiguous prescription for selecting actions.

* * *

DECISION THEORY

* * *

* * *

GAME THEORY

* * *

For the most part, economists did not address the third question listed above, namely, how to make rational decisions when payoffs from actions are not immediate but instead result from several actions taken *in sequence*. This topic was pursued in the field of **operations research**, which emerged in World War II from efforts in Britain to optimize radar installations, and later found civilian applications in complex management decisions. The work of Richard Bellman (1957) formalized a class of sequential decision problems called **Markov decision processes**, which we study in [Chapters 17](#index_split_015.html#filepos2562268) and [21](#index_split_015.html#filepos3262268).

* * *

OPERATIONS RESEARCH

* * *

Work in economics and operations research has contributed much to our notion of rational agents, yet for many years AI research developed along entirely separate paths. One reason was the apparent complexity of making rational decisions. The pioneering AI researcher Herbert Simon (1916–2001) won the Nobel Prize in economics in 1978 for his early work showing that models based on **satisficing**—making decisions that are “good enough,”rather than laboriously calculating an optimal decision—gave a better description of actual human behavior (Simon, 1947). Since the 1990s, there has been a resurgence of interest in decision-theoretic techniques for agent systems (Wellman, 1995).

* * *

SATISFICING

* * *

#### **1.2.4 Neuroscience**

> • How do brains process information?

**Neuroscience** is the study of the nervous system, particularly the brain. Although the exact way in which the brain enables thought is one of the great mysteries of science, the fact that it *does* enable thought has been appreciated for thousands of years because of the evidence that strong blows to the head can lead to mental incapacitation. It has also long been known that human brains are somehow different; in about 335 B.C. Aristotle wrote, “Of all the animals, man has the largest brain in proportion to his size.”[⁵](#index_split_015.html#filepos5564718) Still, it was not until the middle of the 18th century that the brain was widely recognized as the seat of consciousness. Before then, candidate locations included the heart and the spleen.

* * *

NEUROSCIENCE

* * *

Paul Broca’s (1824–1880) study of aphasia (speech deficit) in brain-damaged patients in 1861 demonstrated the existence of localized areas of the brain responsible for specific cognitive functions. In particular, he showed that speech production was localized to the portion of the left hemisphere now called Broca’s area.[⁶](#index_split_015.html#filepos5564945) By that time, it was known that the brain consisted of nerve cells, or **neurons**, but it was not until 1873 that Camillo Golgi (1843–1926) developed a staining technique allowing the observation of individual neurons in the brain (see [Figure 1.2](#index_split_008.html#filepos99125)). This technique was used by Santiago Ramon y Cajal (1852–1934) in his pioneering studies of the brain’s neuronal structures.[⁷](#index_split_015.html#filepos5565113) Nicolas Rashevsky (1936, 1938) was the first to apply mathematical models to the study of the nervous sytem.

* * *

NEURON

* * *

> 11![image](images/00008.jpg)

> **Figure 1.2** The parts of a nerve cell or neuron. Each neuron consists of a cell body, or soma, that contains a cell nucleus. Branching out from the cell body are a number of fibers called dendrites and a single long fiber called the axon. The axon stretches out for a long distance, much longer than the scale in this diagram indicates. Typically, an axon is 1 cm long (100 times the diameter of the cell body), but can reach up to 1 meter. A neuron makes connections with 10 to 100,000 other neurons at junctions called synapses. Signals are propagated from neuron to neuron by a complicated electrochemical reaction. The signals control brain activity in the short term and also enable long-term changes in the connectivity of neurons. These mechanisms are thought to form the basis for learning in the brain. Most information processing goes on in the cerebral cortex, the outer layer of the brain. The basic organizational unit appears to be a column of tissue about 0.5 mm in diameter, containing about 20,000 neurons and extending the full depth of the cortex about 4 mm in humans).

We now have some data on the mapping between areas of the brain and the parts of the body that they control or from which they receive sensory input. Such mappings are able to change radically over the course of a few weeks, and some animals seem to have multiple maps. Moreover, we do not fully understand how other areas can take over functions when one area is damaged. There is almost no theory on how an individual memory is stored.

The measurement of intact brain activity began in 1929 with the invention by Hans Berger of the electroencephalograph (EEG). The recent development of functional magnetic resonance imaging (fMRI) (Ogawa **et al.**, 1990; Cabeza and Nyberg, 2001) is giving neuroscientists unprecedentedly detailed images of brain activity, enabling measurements that correspond in interesting ways to ongoing cognitive processes. These are augmented by advances in single-cell recording of neuron activity. Individual neurons can be stimulated electrically, chemically, or even optically (Han and Boyden, 2007), allowing neuronal input–output relationships to be mapped. Despite these advances, we are still a long way from understanding how cognitive processes actually work.

![hand](images/00006.jpg)

The truly amazing conclusion is that *a collection of simple cells can lead to thought, action, and consciousness* or, in the pithy words of John Searle (1992), *brains cause minds*. The only real alternative theory is mysticism: that minds operate in some mystical realm that is beyond physical science.

> ![table](images/00009.jpg)

> **Figure 1.3** A crude comparison of the raw computational resources available to the IBM BLUE GENE supercomputer, a typical personal computer of 2008, and the human brain. The brain’s numbers are essentially fixed, whereas the supercomputer’s numbers have been increasing by a factor of 10 every 5 years or so, allowing it to achieve rough parity with the brain. The personal computer lags behind on all metrics except cycle time.

Brains and digital computers have somewhat different properties. [Figure 1.3](#index_split_008.html#filepos102243) shows that computers have a cycle time that is a million times faster than a brain. The brain makes up for that with far more storage and interconnection than even a high-end personal computer, although the largest supercomputers have a capacity that is similar to the brain’s. (It should be noted, however, that the brain does not seem to use all of its neurons simultaneously.) Futurists make much of these numbers, pointing to an approaching **singularity** at which computers reach a superhuman level of performance (Vinge, 1993; Kurzweil, 2005), but the raw comparisons are not especially informative. Even with a computer of virtually unlimited capacity, we still would not know how to achieve the brain’s level of intelligence.

* * *

SINGULARITY

* * *

#### **1.2.5 Psychology**

> • How do humans and animals think and act?

The origins of scientific psychology are usually traced to the work of the German physicist Hermann von Helmholtz (1821–1894) and his student Wilhelm Wundt (1832–1920). Helmholtz applied the scientific method to the study of human vision, and his *Handbook of Physiological Optics* is even now described as “the single most important treatise on the physics and physiology of human vision” (Nalwa, 1993, p.15). In 1879, Wundt opened the first laboratory of experimental psychology, at the University of Leipzig. Wundt insisted on carefully controlled experiments in which his workers would perform a perceptual or associative task while introspecting on their thought processes. The careful controls went a long way toward making psychology a science, but the subjective nature of the data made it unlikely that an experimenter would ever disconfirm his or her own theories. Biologists studying animal behavior, on the other hand, lacked introspective data and developed an objective methodology, as described by H. S. Jennings (1906) in his influential work *Behavior of the Lower Organisms*. Applying this viewpoint to humans, the **behaviorism** movement, led by John Watson (1878–1958), rejected *any* theory involving mental processes on the grounds that introspection could not provide reliable evidence. Behaviorists insisted on studying only objective measures of the percepts (or *stimulus*) given to an animal and its resulting actions (or *response*). Behaviorism discovered a lot about rats and pigeons but had less success at understanding humans.

* * *

BEHAVIORISM

* * *

**Cognitive psychology**, which views the brain as an information-processing device, can be traced back at least to the works of William James (1842–1910). Helmholtz also insisted that perception involved a form of unconscious logical inference. The cognitive viewpoint was largely eclipsed by behaviorism in the United States, but at Cambridge’s Applied Psychology Unit, directed by Frederic Bartlett (1886–1969), cognitive modeling was able to flourish. *The Nature of Explanation*, by Bartlett’s student and successor Kenneth Craik (1943), forcefully reestablished the legitimacy of such “mental” terms as beliefs and goals, arguing that they are just as scientific as, say, using pressure and temperature to talk about gases, despite their being made of molecules that have neither. Craik specified the three key steps of a knowledge-based agent: (1) the stimulus must be translated into an internal representation, (2) the representation is manipulated by cognitive processes to derive new internal representations, and (3) these are in turn retranslated back into action. He clearly explained why this was a good design for an agent:

> If the organism carries a “small-scale model” of external reality and of its own possible actions within its head, it is able to try out various alternatives, conclude which is the best of them, react to future situations before they arise, utilize the knowledge of past events in dealing with the present and future, and in every way to react in a much fuller, safer, and more competent manner to the emergencies which face it. (Craik, 1943)

* * *

COGNITIVE PSYCHOLOGY

* * *

After Craik’s death in a bicycle accident in 1945, his work was continued by Donald Broad-bent, whose book *Perception and Communication* (1958) was one of the first works to model psychological phenomena as information processing. Meanwhile, in the United States, the development of computer modeling led to the creation of the field of **cognitive science**. The field can be said to have started at a workshop in September 1956 at MIT. (We shall see that this is just two months after the conference at which AI itself was “born.”) At the workshop, George Miller presented *The Magic Number Seven*, Noam Chomsky presented *Three Models of Language*, and Allen Newell and Herbert Simon presented *The Logic Theory Machine*. These three influential papers showed how computer models could be used to address the psychology of memory, language, and logical thinking, respectively. It is now a common (although far from universal) view among psychologists that “a cognitive theory should be like a computer program” (Anderson, 1980); that is, it should describe a detailed information-processing mechanism whereby some cognitive function might be implemented.

#### **1.2.6 Computer engineering**

> • How can we build an efficient computer?

For artificial intelligence to succeed, we need two things: intelligence and an artifact. The computer has been the artifact of choice. The modern digital electronic computer was invented independently and almost simultaneously by scientists in three countries embattled in World War II. The first *operational* computer was the electromechanical Heath Robinson,[⁸](#index_split_015.html#filepos5565519) built in 1940 by Alan Turing’s team for a single purpose: deciphering German messages. In 1943, the same group developed the Colossus, a powerful general-purpose machine based on vacuum tubes.[⁹](#index_split_015.html#filepos5565780) The first operational *programmable* computer was the Z-3, the invention of Konrad Zuse in Germany in 1941. Zuse also invented floating-point numbers and the first high-level programming language, Plankalkül. The first *electronic* computer, the ABC, was assembled by John Atanasoff and his student Clifford Berry between 1940 and 1942 at Iowa State University. Atanasoff’s research received little support or recognition; it was the ENIAC, developed as part of a secret military project at the University of Pennsylvania by a team including John Mauchly and John Eckert, that proved to be the most influential forerunner of modern computers.

Since that time, each generation of computer hardware has brought an increase in speed and capacity and a decrease in price. Performance doubled every 18 months or so until around 2005, when power dissipation problems led manufacturers to start multiplying the number of CPU cores rather than the clock speed. Current expectations are that future increases in power will come from massive parallelism—a curious convergence with the properties of the brain.

Of course, there were calculating devices before the electronic computer. The earliest automated machines, dating from the 17th century, were discussed [on page 6](#index_split_008.html#filepos76881). The first *programmable* machine was a loom, devised in 1805 by Joseph Marie Jacquard (1752–1834), that used punched cards to store instructions for the pattern to be woven. In the mid-19th century, Charles Babbage (1792–1871) designed two machines, neither of which he completed. The Difference Engine was intended to compute mathematical tables for engineering and scientific projects. It was finally built and shown to work in 1991 at the Science Museum in London (Swade, 2000). Babbage’s Analytical Engine was far more ambitious: it included addressable memory, stored programs, and conditional jumps and was the first artifact capable of universal computation. Babbage’s colleague Ada Lovelace, daughter of the poet Lord Byron, was perhaps the world’s first programmer. (The programming language Ada is named after her.) She wrote programs for the unfinished Analytical Engine and even speculated that the machine could play chess or compose music.

AI also owes a debt to the software side of computer science, which has supplied the operating systems, programming languages, and tools needed to write modern programs (and papers about them). But this is one area where the debt has been repaid: work in AI has pioneered many ideas that have made their way back to mainstream computer science, including time sharing, interactive interpreters, personal computers with windows and mice, rapid development environments, the linked list data type, automatic storage management, and key concepts of symbolic, functional, declarative, and object-oriented programming.

#### **1.2.7 Control theory and cybernetics**

> • How can artifacts operate under their own control?

Ktesibios of Alexandria (c. 250 B.C.) built the first self-controlling machine: a water clock with a regulator that maintained a constant flow rate. This invention changed the definition of what an artifact could do. Previously, only living things could modify their behavior in response to changes in the environment. Other examples of self-regulating feedback control systems include the steam engine governor, created by James Watt (1736–1819), and the thermostat, invented by Cornelis Drebbel (1572–1633), who also invented the submarine. The mathematical theory of stable feedback systems was developed in the 19th century.

The central figure in the creation of what is now called **control theory** was Norbert Wiener (1894–1964). Wiener was a brilliant mathematician who worked with Bertrand Russell, among others, before developing an interest in biological and mechanical control systems and their connection to cognition. Like Craik (who also used control systems as psychological models), Wiener and his colleagues Arturo Rosenblueth and Julian Bigelow challenged the behaviorist orthodoxy (Rosenblueth **et al.**, 1943). They viewed purposive behavior as arising from a regulatory mechanism trying to minimize “error”—the difference between current state and goal state. In the late 1940s, Wiener, along with Warren McCulloch, Walter Pitts, and John von Neumann, organized a series of influential conferences that explored the new mathematical and computational models of cognition. Wiener’s book *Cybernetics* (1948) became a bestseller and awoke the public to the possibility of artificially intelligent machines. Meanwhile, in Britain, W. Ross Ashby (Ashby, 1940) pioneered similar ideas. Ashby, Alan Turing, Grey Walter, and others formed the Ratio Club for “those who had Wiener’s ideas before Wiener’s book appeared.” Ashby’s *Design for a Brain* (1948, 1952) elaborated on his idea that intelligence could be created by the use of **homeostatic** devices containing appropriate feedback loops to achieve stable adaptive behavior.

* * *

CONTROL THEORY

* * *

* * *

CYBERNETICS

* * *

* * *

HOMEOSTATIC

* * *

Modern control theory, especially the branch known as stochastic optimal control, has as its goal the design of systems that maximize an **objective function** over time. This roughly matches our view of AI: designing systems that behave optimally. Why, then, are AI and control theory two different fields, despite the close connections among their founders? The answer lies in the close coupling between the mathematical techniques that were familiar to the participants and the corresponding sets of problems that were encompassed in each world view. Calculus and matrix algebra, the tools of control theory, lend themselves to systems that are describable by fixed sets of continuous variables, whereas AI was founded in part as a way to escape from the these perceived limitations. The tools of logical inference and computation allowed AI researchers to consider problems such as language, vision, and planning that fell completely outside the control theorist’s purview.

* * *

OBJECTIVE FUNCTION

* * *

#### **1.2.8 Linguistics**

> • How does language relate to thought?

In 1957, B. F. Skinner published *Verbal Behavior*. This was a comprehensive, detailed account of the behaviorist approach to language learning, written by the foremost expert in the field. But curiously, a review of the book became as well known as the book itself, and served to almost kill off interest in behaviorism. The author of the review was the linguist Noam Chomsky, who had just published a book on his own theory, *Syntactic Structures*. Chomsky pointed out that the behaviorist theory did not address the notion of creativity in language—it did not explain how a child could understand and make up sentences that he or she had never heard before. Chomsky’s theory—based on syntactic models going back to the Indian linguist Panini (c. 350 B.C.)—could explain this, and unlike previous theories, it was formal enough that it could in principle be programmed.

Modern linguistics and AI, then, were “born” at about the same time, and grew up together, intersecting in a hybrid field called **computational linguistics** or **natural language processing**. The problem of understanding language soon turned out to be considerably more complex than it seemed in 1957. Understanding language requires an understanding of the subject matter and context, not just an understanding of the structure of sentences. This might seem obvious, but it was not widely appreciated until the 1960s. Much of the early work in **knowledge representation** (the study of how to put knowledge into a form that a computer can reason with) was tied to language and informed by research in linguistics, which was connected in turn to decades of work on the philosophical analysis of language.

* * *

COMPUTATIONAL LINGUISTICS

* * *

### 1.3 THE HISTORY OF ARTIFICIAL INTELLIGENCE

With the background material behind us, we are ready to cover the development of AI itself.

#### **1.3.1 The gestation of artificial intelligence (1943–1955)**

The first work that is now generally recognized as AI was done by Warren McCulloch and Walter Pitts (1943). They drew on three sources: knowledge of the basic physiology and function of neurons in the brain; a formal analysis of propositional logic due to Russell and Whitehead; and Turing’s theory of computation. They proposed a model of artificial neurons in which each neuron is characterized as being “on” or “off,” with a switch to “on” occurring in response to stimulation by a sufficient number of neighboring neurons. The state of a neuron was conceived of as “factually equivalent to a proposition which proposed its adequate stimulus.” They showed, for example, that any computable function could be computed by some network of connected neurons, and that all the logical connectives (and, or, not, etc.) could be implemented by simple net structures. McCulloch and Pitts also suggested that suitably defined networks could learn. Donald Hebb (1949) demonstrated a simple updating rule for modifying the connection strengths between neurons. His rule, now called **Hebbian learning**, remains an influential model to this day.

* * *

HEBBIAN LEARNING

* * *

Two undergraduate students at Harvard, Marvin Minsky and Dean Edmonds, built the first neural network computer in 1950. The SNARC, as it was called, used 3000 vacuum tubes and a surplus automatic pilot mechanism from a B-24 bomber to simulate a network of 40 neurons. Later, at Princeton, Minsky studied universal computation in neural networks. His Ph.D. committee was skeptical about whether this kind of work should be considered mathematics, but von Neumann reportedly said, “If it isn’t now, it will be someday.” Minsky was later to prove influential theorems showing the limitations of neural network research.

There were a number of early examples of work that can be characterized as AI, but Alan Turing’s vision was perhaps the most influential. He gave lectures on the topic as early as 1947 at the London Mathematical Society and articulated a persuasive agenda in his 1950 article “Computing Machinery and Intelligence.” Therein, he introduced the Turing Test, machine learning, genetic algorithms, and reinforcement learning. He proposed the *Child Programme* idea, explaining “Instead of trying to produce a programme to simulate the adult mind, why not rather try to produce one which simulated the child’s?”

#### **1.3.2 The birth of artificial intelligence (1956)**

Princeton was home to another influential figure in AI, John McCarthy. After receiving his PhD there in 1951 and working for two years as an instructor, McCarthy moved to Stanford and then to Dartmouth College, which was to become the official birthplace of the field. McCarthy convinced Minsky, Claude Shannon, and Nathaniel Rochester to help him bring together U.S. researchers interested in automata theory, neural nets, and the study of intelligence. They organized a two-month workshop at Dartmouth in the summer of 1956. The proposal states:[^(10)](#index_split_015.html#filepos5566099)

> We propose that a 2 month, 10 man study of artificial intelligence be carried out during the summer of 1956 at Dartmouth College in Hanover, New Hampshire. The study is to proceed on the basis of the conjecture that every aspect of learning or any other feature of intelligence can in principle be so precisely described that a machine can be made to simulate it. An attempt will be made to find how to make machines use language, form abstractions and concepts, solve kinds of problems now reserved for humans, and improve themselves. We think that a significant advance can be made in one or more of these problems if a carefully selected group of scientists work on it together for a summer.

There were 10 attendees in all, including Trenchard More from Princeton, Arthur Samuel from IBM, and Ray Solomonoff and Oliver Selfridge from MIT.

Two researchers from Carnegie Tech,[^(11)](#index_split_015.html#filepos5566688) Allen Newell and Herbert Simon, rather stole the show. Although the others had ideas and in some cases programs for particular applications such as checkers, Newell and Simon already had a reasoning program, the Logic Theorist (LT), about which Simon claimed, “We have invented a computer program capable of thinking non-numerically, and thereby solved the venerable mind–body problem.”[^(12)](#index_split_015.html#filepos5566835) Soon after the workshop, the program was able to prove most of the theorems in [Chapter 2](#index_split_000.html#filepos187684) of Russell and Whitehead’s *Principia Mathematica*. Russell was reportedly delighted when Simon showed him that the program had come up with a proof for one theorem that was shorter than the one in *Principia*. The editors of the *Journal of Symbolic Logic* were less impressed; they rejected a paper coauthored by Newell, Simon, and Logic Theorist.

The Dartmouth workshop did not lead to any new breakthroughs, but it did introduce all the major figures to each other. For the next 20 years, the field would be dominated by these people and their students and colleagues at MIT, CMU, Stanford, and IBM.

Looking at the proposal for the Dartmouth workshop (McCarthy **et al.**, 1955), we can see why it was necessary for AI to become a separate field. Why couldn’t all the work done in AI have taken place under the name of control theory or operations research or decision theory, which, after all, have objectives similar to those of AI? Or why isn’t AI a branch of mathematics? The first answer is that AI from the start embraced the idea of duplicating human faculties such as creativity, self-improvement, and language use. None of the other fields were addressing these issues. The second answer is methodology. AI is the only one of these fields that is clearly a branch of computer science (although operations research does share an emphasis on computer simulations), and AI is the only field to attempt to build machines that will function autonomously in complex, changing environments.

#### **1.3.3 Early enthusiasm, great expectations (1952–1969)**

The early years of AI were full of successes—in a limited way. Given the primitive computers and programming tools of the time and the fact that only a few years earlier computers were seen as things that could do arithmetic and no more, it was astonishing whenever a computer did anything remotely clever. The intellectual establishment, by and large, preferred to believe that “a machine can never do *X*.” (See [Chapter 26](#index_split_015.html#filepos3949421) for a long list of *X*’s gathered by Turing.) AI researchers naturally responded by demonstrating one *X* after another. John McCarthy referred to this period as the “Look, Ma, no hands!” era.

Newell and Simon’s early success was followed up with the General Problem Solver, or GPS. Unlike Logic Theorist, this program was designed from the start to imitate human problem-solving protocols. Within the limited class of puzzles it could handle, it turned out that the order in which the program considered subgoals and possible actions was similar to that in which humans approached the same problems. Thus, GPS was probably the first program to embody the “thinking humanly” approach. The success of GPS and subsequent programs as models of cognition led Newell and Simon (1976) to formulate the famous **physical symbol system** hypothesis, which states that “a physical symbol system has the necessary and sufficient means for general intelligent action.” What they meant is that any system (human or machine) exhibiting intelligence must operate by manipulating data structures composed of symbols. We will see later that this hypothesis has been challenged from many directions.

* * *

PHYSICAL SYMBOL SYSTEM

* * *

At IBM, Nathaniel Rochester and his colleagues produced some of the first AI programs. Herbert Gelernter (1959) constructed the Geometry Theorem Prover, which was able to prove theorems that many students of mathematics would find quite tricky. Starting in 1952, Arthur Samuel wrote a series of programs for checkers (draughts) that eventually learned to play at a strong amateur level. Along the way, he disproved the idea that computers can do only what they are told to: his program quickly learned to play a better game than its creator. The program was demonstrated on television in February 1956, creating a strong impression. Like Turing, Samuel had trouble finding computer time. Working at night, he used machines that were still on the testing floor at IBM’s manufacturing plant. [Chapter 5](#index_split_000.html#filepos660071) covers game playing, and [Chapter 21](#index_split_015.html#filepos3262268) explains the learning techniques used by Samuel.

John McCarthy moved from Dartmouth to MIT and there made three crucial contributions in one historic year: 1958. In MIT AI Lab Memo No. 1, McCarthy defined the high-level language **Lisp**, which was to become the dominant AI programming language for the next 30 years. With Lisp, McCarthy had the tool he needed, but access to scarce and expensive computing resources was also a serious problem. In response, he and others at MIT invented time sharing. Also in 1958, McCarthy published a paper entitled *Programs with Common Sense*, in which he described the Advice Taker, a hypothetical program that can be seen as the first complete AI system. Like the Logic Theorist and Geometry Theorem Prover, McCarthy’s program was designed to use knowledge to search for solutions to problems. But unlike the others, it was to embody general knowledge of the world. For example, he showed how some simple axioms would enable the program to generate a plan to drive to the airport. The program was also designed to accept new axioms in the normal course of operation, thereby allowing it to achieve competence in new areas *without being reprogrammed*. The Advice Taker thus embodied the central principles of knowledge representation and reasoning: that it is useful to have a formal, explicit representation of the world and its workings and to be able to manipulate that representation with deductive processes. It is remarkable how much of the 1958 paper remains relevant today.

* * *

LISP

* * *

1958 also marked the year that Marvin Minsky moved to MIT. His initial collaboration with McCarthy did not last, however. McCarthy stressed representation and reasoning in formal logic, whereas Minsky was more interested in getting programs to work and eventually developed an anti-logic outlook. In 1963, McCarthy started the AI lab at Stanford. His plan to use logic to build the ultimate Advice Taker was advanced by J. A. Robinson’s discovery in 1965 of the resolution method (a complete theorem-proving algorithm for first-order logic; see [Chapter 9](#index_split_015.html#filepos1300686)). Work at Stanford emphasized general-purpose methods for logical reasoning. Applications of logic included Cordell Green’s question-answering and planning systems (Green, 1969b) and the Shakey robotics project at the Stanford Research Institute (SRI). The latter project, discussed further in [Chapter 25](#index_split_015.html#filepos3777962), was the first to demonstrate the complete integration of logical reasoning and physical activity.

Minsky supervised a series of students who chose limited problems that appeared to require intelligence to solve. These limited domains became known as **microworlds**. James Slagle’s SAINT program (1963) was able to solve closed-form calculus integration problems typical of first-year college courses. Tom Evans’s ANALOGY program (1968) solved geometric analogy problems that appear in IQ tests. Daniel Bobrow’s STUDENT program (1967) solved algebra story problems, such as the following:

> If the number of customers Tom gets is twice the square of 20 percent of the number of advertisements he runs, and the number of advertisements he runs is 45, what is the number of customers Tom gets?

* * *

MICROWORLD

* * *

> ![image](images/00010.jpg)

> **Figure 1.4** A scene from the blocks world. SHRDLU (Winograd, 1972) has just completed the command “Find a block which is taller than the one you are holding and put it in the box.”

The most famous microworld was the blocks world, which consists of a set of solid blocks placed on a tabletop (or more often, a simulation of a tabletop), as shown in [Figure 1.4](#index_split_008.html#filepos133721). A typical task in this world is to rearrange the blocks in a certain way, using a robot hand that can pick up one block at a time. The blocks world was home to the vision project of David Huffman (1971), the vision and constraint-propagation work of David Waltz (1975), the learning theory of Patrick Winston (1970), the natural-language-understanding program of Terry Winograd (1972), and the planner of Scott Fahlman (1974).

Early work building on the neural networks of McCulloch and Pitts also flourished. The work of Winograd and Cowan (1963) showed how a large number of elements could collectively represent an individual concept, with a corresponding increase in robustness and parallelism. Hebb’s learning methods were enhanced by Bernie Widrow (Widrow and Hoff, 1960; Widrow, 1962), who called his networks **adalines**, and by Frank Rosenblatt (1962) with his **perceptrons**. The **perceptron convergence theorem** (Block **et al.**, 1962) says that the learning algorithm can adjust the connection strengths of a perceptron to match any input data, provided such a match exists. These topics are covered in [Chapter 20](#index_split_015.html#filepos3158034).

#### **1.3.4 A dose of reality (1966–1973)**

From the beginning, AI researchers were not shy about making predictions of their coming successes. The following statement by Herbert Simon in 1957 is often quoted:

> It is not my aim to surprise or shock you—but the simplest way I can summarize is to say that there are now in the world machines that think, that learn and that create. Moreover, their ability to do these things is going to increase rapidly until—in a visible future—the range of problems they can handle will be coextensive with the range to which the human mind has been applied.

Terms such as “visible future” can be interpreted in various ways, but Simon also made more concrete predictions: that within 10 years a computer would be chess champion, and a significant mathematical theorem would be proved by machine. These predictions came true (or approximately true) within 40 years rather than 10. Simon’s overconfidence was due to the promising performance of early AI systems on simple examples. In almost all cases, however, these early systems turned out to fail miserably when tried out on wider selections of problems and on more difficult problems.

The first kind of difficulty arose because most early programs knew nothing of their subject matter; they succeeded by means of simple syntactic manipulations. A typical story occurred in early machine translation efforts, which were generously funded by the U.S. National Research Council in an attempt to speed up the translation of Russian scientific papers in the wake of the Sputnik launch in 1957. It was thought initially that simple syntactic transformations based on the grammars of Russian and English, and word replacement from an electronic dictionary, would suffice to preserve the exact meanings of sentences. The fact is that accurate translation requires background knowledge in order to resolve ambiguity and establish the content of the sentence. The famous retranslation of “the spirit is willing but the flesh is weak” as “the vodka is good but the meat is rotten” illustrates the difficulties encountered. In 1966, a report by an advisory committee found that “there has been no machine translation of general scientific text, and none is in immediate prospect.” All U.S. government funding for academic translation projects was canceled. Today, machine translation is an imperfect but widely used tool for technical, commercial, government, and Internet documents.

The second kind of difficulty was the intractability of many of the problems that AI was attempting to solve. Most of the early AI programs solved problems by trying out different combinations of steps until the solution was found. This strategy worked initially because microworlds contained very few objects and hence very few possible actions and very short solution sequences. Before the theory of computational complexity was developed, it was widely thought that “scaling up” to larger problems was simply a matter of faster hardware and larger memories. The optimism that accompanied the development of resolution theorem proving, for example, was soon dampened when researchers failed to prove theorems involving more than a few dozen facts. *The fact that a program can find a solution in principle does not mean that the program contains any of the mechanisms needed to find it in practice.*

![hand](images/00006.jpg)

The illusion of unlimited computational power was not confined to problem-solving programs. Early experiments in **machine evolution** (now called **genetic algorithms**) (Friedberg, 1958; Friedberg **et al.**, 1959) were based on the undoubtedly correct belief that by making an appropriate series of small mutations to a machine-code program, one can generate a program with good performance for any particular task. The idea, then, was to try random mutations with a selection process to preserve mutations that seemed useful. Despite thousands of hours of CPU time, almost no progress was demonstrated. Modern genetic algorithms use better representations and have shown more success.

* * *

MACHINE EVOLUTION

* * *

* * *

GENETIC ALGORITHM

* * *

Failure to come to grips with the “combinatorial explosion” was one of the main criticisms of AI contained in the Lighthill report (Lighthill, 1973), which formed the basis for the decision by the British government to end support for AI research in all but two universities. (Oral tradition paints a somewhat different and more colorful picture, with political ambitions and personal animosities whose description is beside the point.)

A third difficulty arose because of some fundamental limitations on the basic structures being used to generate intelligent behavior. For example, Minsky and Papert’s book *Perceptrons* (1969) proved that, although perceptrons (a simple form of neural network) could be shown to learn anything they were capable of representing, they could represent very little. In particular, a two-input perceptron (restricted to be simpler than the form Rosenblatt originally studied) could not be trained to recognize when its two inputs were different. Although their results did not apply to more complex, multilayer networks, research funding for neural-net research soon dwindled to almost nothing. Ironically, the new back-propagation learning algorithms for multilayer networks that were to cause an enormous resurgence in neural-net research in the late 1980s were actually discovered first in 1969 (Bryson and Ho, 1969).

#### **1.3.5 Knowledge-based systems: The key to power? (1969–1979)**

The picture of problem solving that had arisen during the first decade of AI research was of a general-purpose search mechanism trying to string together elementary reasoning steps to find complete solutions. Such approaches have been called **weak methods** because, although general, they do not scale up to large or difficult problem instances. The alternative to weak methods is to use more powerful, domain-specific knowledge that allows larger reasoning steps and can more easily handle typically occurring cases in narrow areas of expertise. One might say that to solve a hard problem, you have to almost know the answer already.

* * *

WEAK METHOD

* * *

The DENDRAL program (Buchanan **et al.**, 1969) was an early example of this approach. It was developed at Stanford, where Ed Feigenbaum (a former student of Herbert Simon), Bruce Buchanan (a philosopher turned computer scientist), and Joshua Lederberg (a Nobel laureate geneticist) teamed up to solve the problem of inferring molecular structure from the information provided by a mass spectrometer. The input to the program consists of the elementary formula of the molecule (e.g., C[6]H[13]NO[2]) and the mass spectrum giving the masses of the various fragments of the molecule generated when it is bombarded by an electron beam. For example, the mass spectrum might contain a peak at *m* = 15, corresponding to the mass of a methyl (CH[3]) fragment.

The naive version of the program generated all possible structures consistent with the formula, and then predicted what mass spectrum would be observed for each, comparing this with the actual spectrum. As one might expect, this is intractable for even moderate-sized molecules. The DENDRAL researchers consulted analytical chemists and found that they worked by looking for well-known patterns of peaks in the spectrum that suggested common substructures in the molecule. For example, the following rule is used to recognize a ketone (C=O) subgroup (which weighs 28):

> **if** there are two peaks at *x*[1] and *x*[2] such that

> (*a*) *x*[1] + *x*[2] = *M* + 28 (*M* is the mass of the whole molecule);

> (*b*) *x*[1] − 28 is a high peak;

> (*c*) *x*[2] − 28 is a high peak;

> (*d*) At least one of *x*[1] and *x*[2] is high.

> **then** there is a ketone subgroup

Recognizing that the molecule contains a particular substructure reduces the number of possible candidates enormously. DENDRAL was powerful because

> All the relevant theoretical knowledge to solve these problems has been mapped over from its general form in the \[spectrum prediction component\] (“first principles”) to efficient special forms (“cookbook recipes”). (Feigenbaum **et al.**, 1971)

The significance of DENDRAL was that it was the first successful *knowledge-intensive* system: its expertise derived from large numbers of special-purpose rules. Later systems also incorporated the main theme of McCarthy’s Advice Taker approach—the clean separation of the knowledge (in the form of rules) from the reasoning component.

With this lesson in mind, Feigenbaum and others at Stanford began the Heuristic Programming Project (HPP) to investigate the extent to which the new methodology of **expert systems** could be applied to other areas of human expertise. The next major effort was in the area of medical diagnosis. Feigenbaum, Buchanan, and Dr. Edward Shortliffe developed MYCIN to diagnose blood infections. With about 450 rules, MYCIN was able to perform as well as some experts, and considerably better than junior doctors. It also contained two major differences from DENDRAL. First, unlike the DENDRAL rules, no general theoretical model existed from which the MYCIN rules could be deduced. They had to be acquired from extensive interviewing of experts, who in turn acquired them from textbooks, other experts, and direct experience of cases. Second, the rules had to reflect the uncertainty associated with medical knowledge. MYCIN incorporated a calculus of uncertainty called **certainty factors** (see [Chapter 14](#index_split_015.html#filepos2036437)), which seemed (at the time) to fit well with how doctors assessed the impact of evidence on the diagnosis.

* * *

EXPERT SYSTEMS

* * *

* * *

CERTAINTY FACTOR

* * *

The importance of domain knowledge was also apparent in the area of understanding natural language. Although Winograd’s SHRDLU system for understanding natural language had engendered a good deal of excitement, its dependence on syntactic analysis caused some of the same problems as occurred in the early machine translation work. It was able to overcome ambiguity and understand pronoun references, but this was mainly because it was designed specifically for one area—the blocks world. Several researchers, including Eugene Charniak, a fellow graduate student of Winograd’s at MIT, suggested that robust language understanding would require general knowledge about the world and a general method for using that knowledge.

At Yale, linguist-turned-AI-researcher Roger Schank emphasized this point, claiming, “There is no such thing as syntax,” which upset a lot of linguists but did serve to start a useful discussion. Schank and his students built a series of programs (Schank and Abelson, 1977;Wilensky, 1978; Schank and Riesbeck, 1981; Dyer, 1983) that all had the task of understanding natural language. The emphasis, however, was less on language *per se* and more on the problems of representing and reasoning with the knowledge required for language understanding. The problems included representing stereotypical situations (Cullingford, 1981), describing human memory organization (Rieger, 1976; Kolodner, 1983), and understanding plans and goals (Wilensky, 1983).

The widespread growth of applications to real-world problems caused a concurrent increase in the demands for workable knowledge representation schemes. A large number of different representation and reasoning languages were developed. Some were based on logic—for example, the Prolog language became popular in Europe, and the PLANNER family in the United States. Others, following Minsky’s idea of **frames** (1975), adopted a more structured approach, assembling facts about particular object and event types and arranging the types into a large taxonomic hierarchy analogous to a biological taxonomy.

* * *

FRAMES

* * *

#### **1.3.6 AI becomes an industry (1980–present)**

The first successful commercial expert system, R1, began operation at the Digital Equipment Corporation (McDermott, 1982). The program helped configure orders for new computer systems; by 1986, it was saving the company an estimated $40 million a year. By 1988, DEC’s AI group had 40 expert systems deployed, with more on the way. DuPont had 100 in use and 500 in development, saving an estimated $10 million a year. Nearly every major U.S. corporation had its own AI group and was either using or investigating expert systems.

In 1981, the Japanese announced the “Fifth Generation” project, a 10-year plan to build intelligent computers running Prolog. In response, the United States formed the Microelectronics and Computer Technology Corporation (MCC) as a research consortium designed to assure national competitiveness. In both cases, AI was part of a broad effort, including chip design and human-interface research. In Britain, the Alvey report reinstated the funding that was cut by the Lighthill report.[^(13)](#index_split_015.html#filepos5567227) In all three countries, however, the projects never met their ambitious goals.

Overall, the AI industry boomed from a few million dollars in 1980 to billions of dollars in 1988, including hundreds of companies building expert systems, vision systems, robots, and software and hardware specialized for these purposes. Soon after that came a period called the “AI Winter,” in which many companies fell by the wayside as they failed to deliver on extravagant promises.

#### **1.3.7 The return of neural networks (1986–present)**

In the mid-1980s at least four different groups reinvented the **back-propagation** learning algorithm first found in 1969 by Bryson and Ho. The algorithm was applied to many learning problems in computer science and psychology, and the widespread dissemination of the results in the collection *Parallel Distributed Processing* (Rumelhart and McClelland, 1986) caused great excitement.

* * *

BACK-PROPAGATION

* * *

These so-called **connectionist** models of intelligent systems were seen by some as direct competitors both to the symbolic models promoted by Newell and Simon and to the logicist approach of McCarthy and others (Smolensky, 1988). It might seem obvious that at some level humans manipulate symbols—in fact, Terrence Deacon’s book *The Symbolic* *Species* (1997) suggests that this is the *defining characteristic* of humans—but the most ardent connectionists questioned whether symbol manipulation had any real explanatory role in detailed models of cognition. This question remains unanswered, but the current view is that connectionist and symbolic approaches are complementary, not competing. As occurred with the separation of AI and cognitive science, modern neural network research has bifurcated into two fields, one concerned with creating effective network architectures and algorithms and understanding their mathematical properties, the other concerned with careful modeling of the empirical properties of actual neurons and ensembles of neurons.

* * *

CONNECTIONIST

* * *

#### **1.3.8 AI adopts the scientific method (1987–present)**

Recent years have seen a revolution in both the content and the methodology of work in artificial intelligence.[^(14)](#index_split_015.html#filepos5567495) It is now more common to build on existing theories than to propose brand-new ones, to base claims on rigorous theorems or hard experimental evidence rather than on intuition, and to show relevance to real-world applications rather than toy examples.

AI was founded in part as a rebellion against the limitations of existing fields like control theory and statistics, but now it is embracing those fields. As David McAllester (1998) put it:

> In the early period of AI it seemed plausible that new forms of symbolic computation, e.g., frames and semantic networks, made much of classical theory obsolete. This led to a form of isolationism in which AI became largely separated from the rest of computer science. This isolationism is currently being abandoned. There is a recognition that machine learning should not be isolated from information theory, that uncertain reasoning should not be isolated from stochastic modeling, that search should not be isolated from classical optimization and control, and that automated reasoning should not be isolated from formal methods and static analysis.

In terms of methodology, AI has finally come firmly under the scientific method. To be accepted, hypotheses must be subjected to rigorous empirical experiments, and the results must be analyzed statistically for their importance (Cohen, 1995). It is now possible to replicate experiments by using shared repositories of test data and code.

The field of speech recognition illustrates the pattern. In the 1970s, a wide variety of different architectures and approaches were tried. Many of these were rather *ad hoc* and fragile, and were demonstrated on only a few specially selected examples. In recent years, approaches based on **hidden Markov models** (HMMs) have come to dominate the area. Two aspects of HMMs are relevant. First, they are based on a rigorous mathematical theory. This has allowed speech researchers to build on several decades of mathematical results developed in other fields. Second, they are generated by a process of training on a large corpus of real speech data. This ensures that the performance is robust, and in rigorous blind tests the HMMs have been improving their scores steadily. Speech technology and the related field of handwritten character recognition are already making the transition to widespread industrial and consumer applications. Note that there is no scientific claim that humans use HMMs to recognize speech; rather, HMMs provide a mathematical framework for understanding the problem and support the engineering claim that they work well in practice.

* * *

HIDDEN MARKOV MODELS

* * *

Machine translation follows the same course as speech recognition. In the 1950s there was initial enthusiasm for an approach based on sequences of words, with models learned according to the principles of information theory. That approach fell out of favor in the 1960s, but returned in the late 1990s and now dominates the field.

Neural networks also fit this trend. Much of the work on neural nets in the 1980s was done in an attempt to scope out what could be done and to learn how neural nets differ from “traditional” techniques. Using improved methodology and theoretical frameworks, the field arrived at an understanding in which neural nets can now be compared with corresponding techniques from statistics, pattern recognition, and machine learning, and the most promising technique can be applied to each application. As a result of these developments, so-called **data mining** technology has spawned a vigorous new industry.

* * *

DATA MINING

* * *

Judea Pearl’s (1988) *Probabilistic Reasoning in Intelligent Systems* led to a new acceptance of probability and decision theory in AI, following a resurgence of interest epitomized by Peter Cheeseman’s (1985) article “In Defense of Probability.” The **Bayesian network** formalism was invented to allow efficient representation of, and rigorous reasoning with, uncertain knowledge. This approach largely overcomes many problems of the probabilistic reasoning systems of the 1960s and 1970s; it now dominates AI research on uncertain reasoning and expert systems. The approach allows for learning from experience, and it combines the best of classical AI and neural nets. Work by Judea Pearl (1982a) and by Eric Horvitz and David Heckerman (Horvitz and Heckerman, 1986; Horvitz **et al.**, 1986) promoted the idea of *normative* expert systems: ones that act rationally according to the laws of decision theory and do not try to imitate the thought steps of human experts. The Windows^(TM) operating system includes several normative diagnostic expert systems for correcting problems. [Chapters 13](#index_split_015.html#filepos1915714) to [16](#index_split_015.html#filepos2423989) cover this area.

* * *

BAYESIAN NETWORK

* * *

Similar gentle revolutions have occurred in robotics, computer vision, and knowledge representation. A better understanding of the problems and their complexity properties, combined with increased mathematical sophistication, has led to workable research agendas and robust methods. Although increased formalization and specialization led fields such as vision and robotics to become somewhat isolated from “mainstream” AI in the 1990s, this trend has reversed in recent years as tools from machine learning in particular have proved effective for many problems. The process of reintegration is already yielding significant benefits

#### **1.3.9 The emergence of intelligent agents (1995–present)**

Perhaps encouraged by the progress in solving the subproblems of AI, researchers have also started to look at the “whole agent” problem again. The work of Allen Newell, John Laird, and Paul Rosenbloom on SOAR (Newell, 1990; Laird **et al.**, 1987) is the best-known example of a complete agent architecture. One of the most important environments for intelligent agents is the Internet. AI systems have become so common in Web-based applications that the “-bot” suffix has entered everyday language. Moreover, AI technologies underlie many Internet tools, such as search engines, recommender systems, and Web site aggregators.

One consequence of trying to build complete agents is the realization that the previously isolated subfields of AI might need to be reorganized somewhat when their results are to be tied together. In particular, it is now widely appreciated that sensory systems (vision, sonar, speech recognition, etc.) cannot deliver perfectly reliable information about the environment. Hence, reasoning and planning systems must be able to handle uncertainty. A second major consequence of the agent perspective is that AI has been drawn into much closer contact with other fields, such as control theory and economics, that also deal with agents. Recent progress in the control of robotic cars has derived from a mixture of approaches ranging from better sensors, control-theoretic integration of sensing, localization and mapping, as well as a degree of high-level planning.

Despite these successes, some influential founders of AI, including John McCarthy (2007), Marvin Minsky (2007), Nils Nilsson (1995, 2005) and Patrick Winston (Beal and Winston, 2009), have expressed discontent with the progress of AI. They think that AI should put less emphasis on creating ever-improved versions of applications that are good at a specific task, such as driving a car, playing chess, or recognizing speech. Instead, they believe AI should return to its roots of striving for, in Simon’s words, “machines that think, that learn and that create.” They call the effort **human-level AI** or HLAI; their first symposium was in 2004 (Minsky **et al.**, 2004). The effort will require very large knowledge bases; Hendler **et al.** (1995) discuss where these knowledge bases might come from.

* * *

HUMAN-LEVEL AI

* * *

A related idea is the subfield of **Artificial General Intelligence** or AGI (Goertzel and Pennachin, 2007), which held its first conference and organized the *Journal of Artificial General Intelligence* in 2008. AGI looks for a universal algorithm for learning and acting in any environment, and has its roots in the work of Ray Solomonoff (1964), one of the attendees of the original 1956 Dartmouth conference. Guaranteeing that what we create is really **Friendly AI** is also a concern (Yudkowsky, 2008; Omohundro, 2008), one we will return to in [Chapter 26](#index_split_015.html#filepos3949421).

* * *

ARTIFICIAL GENERAL INTELLIGENCE

* * *

* * *

FRIENDLY AI

* * *

#### **1.3.10 The availability of very large data sets (2001–present)**

Throughout the 60-year history of computer science, the emphasis has been on the *algorithm* as the main subject of study. But some recent work in AI suggests that for many problems, it makes more sense to worry about the *data* and be less picky about what algorithm to apply. This is true because of the increasing availability of very large data sources: for example, trillions of words of English and billions of images from the Web (Kilgarriff and Grefenstette, 2006); or billions of base pairs of genomic sequences (Collins **et al.**, 2003).

One influential paper in this line was Yarowsky’s (1995) work on word-sense disambiguation: given the use of the word “plant” in a sentence, does that refer to flora or factory? Previous approaches to the problem had relied on human-labeled examples combined with machine learning algorithms. Yarowsky showed that the task can be done, with accuracy above 96%, with no labeled examples at all. Instead, given a very large corpus of unannotated text and just the dictionary definitions of the two senses—“works, industrial plant” and “flora, plant life”—one can label examples in the corpus, and from there **bootstrap** to learn new patterns that help label new examples. Banko and Brill (2001) show that techniques like this perform even better as the amount of available text goes from a million words to a billion and that the increase in performance from using more data exceeds any difference in algorithm choice; a mediocre algorithm with 100 million words of unlabeled training data outperforms the best known algorithm with 1 million words.

As another example, Hays and Efros (2007) discuss the problem of filling in holes in a photograph. Suppose you use Photoshop to mask out an ex-friend from a group photo, but now you need to fill in the masked area with something that matches the background. Hays and Efros defined an algorithm that searches through a collection of photos to find something that will match. They found the performance of their algorithm was poor when they used a collection of only ten thousand photos, but crossed a threshold into excellent performance when they grew the collection to two million photos.

Work like this suggests that the “knowledge bottleneck” in AI—the problem of how to express all the knowledge that a system needs—may be solved in many applications by learning methods rather than hand-coded knowledge engineering, provided the learning algorithms have enough data to go on (Halevy **et al.**, 2009). Reporters have noticed the surge of new applications and have written that “AI Winter” may be yielding to a new Spring (Havenstein, 2005). As Kurzweil (2005) writes, “today, many thousands of AI applications are deeply embedded in the infrastructure of every industry.”

### 1.4 THE STATE OF THE ART

What can AI do today? A concise answer is difficult because there are so many activities in so many subfields. Here we sample a few applications; others appear throughout the book.

**Robotic vehicles**: A driverless robotic car named STANLEY sped through the rough terrain of the Mojave dessert at 22 mph, finishing the 132-mile course first to win the 2005 DARPA Grand Challenge. STANLEY is a Volkswagen Touareg outfitted with cameras, radar, and laser rangefinders to sense the environment and onboard software to command the steering, braking, and acceleration (Thrun, 2006). The following year CMU’s BOSS won the Urban Challenge, safely driving in traffic through the streets of a closed Air Force base, obeying traffic rules and avoiding pedestrians and other vehicles.

**Speech recognition**: A traveler calling United Airlines to book a flight can have the entire conversation guided by an automated speech recognition and dialog management system.

**Autonomous planning and scheduling**: A hundred million miles from Earth, NASA’s Remote Agent program became the first onboard autonomous planning program to control the scheduling of operations for a spacecraft (Jonsson **et al.**, 2000). REMOTE AGENT generated plans from high-level goals specified from the ground and monitored the execution of those plans—detecting, diagnosing, and recovering from problems as they occurred. Successor program MAPGEN (Al-Chang **et al.**, 2004) plans the daily operations for NASA’s Mars Exploration Rovers, and MEXAR2 (Cesta **et al.**, 2007) did mission planning—both logistics and science planning—for the European Space Agency’s Mars Express mission in 2008.

**Game playing**: IBM’s DEEP BLUE became the first computer program to defeat the world champion in a chess match when it bested Garry Kasparov by a score of 3.5 to 2.5 in an exhibition match (Goodman and Keene, 1997). Kasparov said that he felt a “new kind of intelligence” across the board from him. *Newsweek* magazine described the match as “The brain’s last stand.” The value of IBM’s stock increased by $18 billion. Human champions studied Kasparov’s loss and were able to draw a few matches in subsequent years, but the most recent human-computer matches have been won convincingly by the computer.

**Spam fighting**: Each day, learning algorithms classify over a billion messages as spam, saving the recipient from having to waste time deleting what, for many users, could comprise 80% or 90% of all messages, if not classified away by algorithms. Because the spammers are continually updating their tactics, it is difficult for a static programmed approach to keep up, and learning algorithms work best (Sahami **et al.**, 1998; Goodman and Heckerman, 2004).

**Logistics planning**: During the Persian Gulf crisis of 1991, U.S. forces deployed a Dynamic Analysis and Replanning Tool, DART (Cross and Walker, 1994), to do automated logistics planning and scheduling for transportation. This involved up to 50,000 vehicles, cargo, and people at a time, and had to account for starting points, destinations, routes, and conflict resolution among all parameters. The AI planning techniques generated in hours a plan that would have taken weeks with older methods. The Defense Advanced Research Project Agency (DARPA) stated that this single application more than paid back DARPA’s 30-year investment in AI.

**Robotics**: The iRobot Corporation has sold over two million Roomba robotic vacuum cleaners for home use. The company also deploys the more rugged PackBot to Iraq and Afghanistan, where it is used to handle hazardous materials, clear explosives, and identify the location of snipers.

**Machine Translation**: A computer program automatically translates from Arabic to English, allowing an English speaker to see the headline “Ardogan Confirms That Turkey Would Not Accept Any Pressure, Urging Them to Recognize Cyprus.” The program uses a statistical model built from examples of Arabic-to-English translations and from examples of English text totaling two trillion words (Brants **et al.**, 2007). None of the computer scientists on the team speak Arabic, but they do understand statistics and machine learning algorithms.

These are just a few examples of artificial intelligence systems that exist today. Not magic or science fiction—but rather science, engineering, and mathematics, to which this book provides an introduction.

### 1.5 SUMMARY

This chapter defines AI and establishes the cultural background against which it has developed. Some of the important points are as follows:

> • Different people approach AI with different goals in mind. Two important questions to ask are: Are you concerned with thinking or behavior? Do you want to model humans or work from an ideal standard?

> • In this book, we adopt the view that intelligence is concerned mainly with **rational action**. Ideally, an **intelligent agent** takes the best possible action in a situation. We study the problem of building agents that are intelligent in this sense.

> • Philosophers (going back to 400 B.C.) made AI conceivable by considering the ideas that the mind is in some ways like a machine, that it operates on knowledge encoded in some internal language, and that thought can be used to choose what actions to take.

> • Mathematicians provided the tools to manipulate statements of logical certainty as well as uncertain, probabilistic statements. They also set the groundwork for understanding computation and reasoning about algorithms.

> • Economists formalized the problem of making decisions that maximize the expected outcome to the decision maker.

> • Neuroscientists discovered some facts about how the brain works and the ways in which it is similar to and different from computers.

> • Psychologists adopted the idea that humans and animals can be considered information-processing machines. Linguists showed that language use fits into this model.

> • Computer engineers provided the ever-more-powerful machines that make AI applications possible.

> • Control theory deals with designing devices that act optimally on the basis of feedback from the environment. Initially, the mathematical tools of control theory were quite different from AI, but the fields are coming closer together.

> • The history of AI has had cycles of success, misplaced optimism, and resulting cutbacks in enthusiasm and funding. There have also been cycles of introducing new creative approaches and systematically refining the best ones.

> • AI has advanced more rapidly in the past decade because of greater use of the scientific method in experimenting with and comparing approaches.

> • Recent progress in understanding the theoretical basis for intelligence has gone hand in hand with improvements in the capabilities of real systems. The subfields of AI have become more integrated, and AI has found common ground with other disciplines.

### BIBLIOGRAPHICAL AND HISTORICAL NOTES

The methodological status of artificial intelligence is investigated in *The Sciences of the Artificial*, by Herb Simon (1981), which discusses research areas concerned with complex artifacts. It explains how AI can be viewed as both science and mathematics. Cohen (1995) gives an overview of experimental methodology within AI.

The Turing Test (Turing, 1950) is discussed by Shieber (1994), who severely criticizes the usefulness of its instantiation in the Loebner Prize competition, and by Ford and Hayes (1995), who argue that the test itself is not helpful for AI. Bringsjord (2008) gives advice for a Turing Test judge. Shieber (2004) and Epstein **et al.** (2008) collect a number of essays on the Turing Test. *Artificial Intelligence: The Very Idea*, by John Haugeland (1985), gives a readable account of the philosophical and practical problems of AI. Significant early papers in AI are anthologized in the collections by Webber and Nilsson (1981) and by Luger (1995). The *Encyclopedia of AI* (Shapiro, 1992) contains survey articles on almost every topic in AI, as does Wikipedia. These articles usually provide a good entry point into the research literature on each topic. An insightful and comprehensive history of AI is given by Nils Nillson (2009), one of the early pioneers of the field.

The most recent work appears in the proceedings of the major AI conferences: the biennial International Joint Conference on AI (IJCAI), the annual European Conference on AI (ECAI), and the National Conference on AI, more often known as AAAI, after its sponsoring organization. The major journals for general AI are *Artificial Intelligence*, *Computational Intelligence*, the *IEEE Transactions on Pattern Analysis and Machine Intelligence*, *IEEE Intelligent Systems*, and the electronic *Journal of Artificial Intelligence Research*. Therearealso many conferences and journals devoted to specific areas, which we cover in the appropriate chapters. The main professional societies for AI are the American Association for Artificial Intelligence (AAAI), the ACM Special Interest Group in Artificial Intelligence (SIGART), and the Society for Artificial Intelligence and Simulation of Behaviour (AISB). AAAI’s *AI Magazine* contains many topical and tutorial articles, and its Web site, `aaai.org`, contains news, tutorials, and background information.

### EXERCISES

These exercises are intended to stimulate discussion, and some might be set as term projects. Alternatively, preliminary attempts can be made now, and these attempts can be reviewed after the completion of the book.

**1.1** Define in your own words: (a) intelligence, (b) artificial intelligence, (c) agent, (d) rationality, (e) logical reasoning.

**1.2** Read Turing’s original paper on AI (Turing, 1950). In the paper, he discusses several objections to his proposed enterprise and his test for intelligence. Which objections still carry weight? Are his refutations valid? Can you think of new objections arising from developments since he wrote the paper? In the paper, he predicts that, by the year 2000, a computer will have a 30% chance of passing a five-minute Turing Test with an unskilled interrogator. What chance do you think a computer would have today? In another 50 years?

![book](images/00005.jpg)

**1.3** Are reflex actions (such as flinching from a hot stove) rational? Are they intelligent?

**1.4** Suppose we extend Evans’s ANALOGY program so that it can score 200 on a standard IQ test. Would we then have a program more intelligent than a human? Explain.

**1.5** The neural structure of the sea slug *Aplysia* has been widely studied (first by Nobel Laureate Eric Kandel) because it has only about 20,000 neurons, most of them large and easily manipulated. Assuming that the cycle time for an *Aplysia* neuron is roughly the same as for a human neuron, how does the computational power, in terms of memory updates per second, compare with the high-end computer described in [Figure 1.3](#index_split_008.html#filepos102243)?

**1.6** How could introspection—reporting on one’s inner thoughts—be inaccurate? Could I be wrong about what I’m thinking? Discuss.

**1.7** To what extent are the following computer systems instances of artificial intelligence:

> • Supermarket bar code scanners.

> • Web search engines.

> • Voice-activated telephone menus.

> • Internet routing algorithms that respond dynamically to the state of the network.

**1.8** Many of the computational models of cognitive activities that have been proposed involve quite complex mathematical operations, such as convolving an image with a Gaussian or finding a minimum of the entropy function. Most humans (and certainly all animals) never learn this kind of mathematics at all, almost no one learns it before college, and almost no one can compute the convolution of a function with a Gaussian in their head. What sense does it make to say that the “vision system” is doing this kind of mathematics, whereas the actual person has no idea how to do it?

**1.9** Why would evolution tend to result in systems that act rationally? What goals are such systems designed to achieve?

**1.10** Is AI a science, or is it engineering? Or neither or both? Explain.

**1.11** “Surely computers cannot be intelligent—they can do only what their programmers tell them.” Is the latter statement true, and does it imply the former?

**1.12** “Surely animals cannot be intelligent—they can do only what their genes tell them.”Is the latter statement true, and does it imply the former?

**1.13** “Surely animals, humans, and computers cannot be intelligent—they can do only what their constituent atoms are told to do by the laws of physics.” Is the latter statement true, and does it imply the former?

**1.14** Examine the AI literature to discover whether the following tasks can currently be solved by computers:

> **a**. Playing a decent game of table tennis (Ping-Pong).

> **b**. Driving in the center of Cairo, Egypt.

> **c**. Driving in Victorville, California.

> **d**. Buying a week’s worth of groceries at the market.

> **e**. Buying a week’s worth of groceries on the Web.

> **f**. Playing a decent game of bridge at a competitive level.

> **g**. Discovering and proving new mathematical theorems.

> **h**. Writing an intentionally funny story.

> **i**. Giving competent legal advice in a specialized area of law.

> **j**. Translating spoken English into spoken Swedish in real time.

> **k**. Performing a complex surgical operation.

![book](images/00005.jpg)

For the currently infeasible tasks, try to find out what the difficulties are and predict when, if ever, they will be overcome.

**1.15** Various subfields of AI have held contests by defining a standard task and inviting researchers to do their best. Examples include the DARPA Grand Challenge for robotic cars, The International Planning Competition, the Robocup robotic soccer league, the TREC information retrieval event, and contests in machine translation, speech recognition. Investigate five of these contests, and describe the progress made over the years. To what degree have the contests advanced toe state of the art in AI? Do what degree do they hurt the field by drawing energy away from new ideas?

## **2 INTELLIGENT AGENTS**

> *In which we discuss the nature of agents, perfect or otherwise, the diversity of environments, and the resulting menagerie of agent types.*

[Chapter 1](#index_split_000.html#filepos57382) identified the concept of **rational agents** as central to our approach to artificial intelligence. In this chapter, we make this notion more concrete. We will see that the concept of rationality can be applied to a wide variety of agents operating in any imaginable environment. Our plan in this book is to use this concept to develop a small set of design principles for building successful agents—systems that can reasonably be called **intelligent**.

We begin by examining agents, environments, and the coupling between them. The observation that some agents behave better than others leads naturally to the idea of a rational agent—one that behaves as well as possible. How well an agent can behave depends on the nature of the environment; some environments are more difficult than others. We give a crude categorization of environments and show how properties of an environment influence the design of suitable agents for that environment. We describe a number of basic “skeleton”agent designs, which we flesh out in the rest of the book.

### 2.1 AGENTS AND ENVIRONMENTS

An **agent** is anything that can be viewed as perceiving its **environment** through **sensors** and acting upon that environment through **actuators**. This simple idea is illustrated in [Figure 2.1](#index_split_009.html#filepos191665). A human agent has eyes, ears, and other organs for sensors and hands, legs, vocal tract, and so on for actuators. A robotic agent might have cameras and infrared range finders for sensors and various motors for actuators. A software agent receives keystrokes, file contents, and network packets as sensory inputs and acts on the environment by displaying on the screen, writing files, and sending network packets.

* * *

ENVIRONMENT

* * *

* * *

SENSOR

* * *

* * *

ACTUATOR

* * *

We use the term **percept** to refer to the agent’s perceptual inputs at any given instant. An agent’s **percept sequence** is the complete history of everything the agent has ever perceived. In general, *an agent’s choice of action at any given instant can depend on the entire percept sequence observed to date, but not on anything it hasn’t perceived.* By specifying the agent’s choice of action for every possible percept sequence, we have said more or less everything there is to say about the agent. Mathematically speaking, we say that an agent’s behavior is described by the **agent function** that maps any given percept sequence to an action.

![hand](images/00006.jpg)

* * *

PERCEPT

* * *

* * *

PERCEPT SEQUENCE

* * *

* * *

AGENT FUNCTION

* * *

> ![image](images/00011.jpg)

> **Figure 2.1** Agents interact with environments through sensors and actuators.

We can imagine *tabulating* the agent function that describes any given agent; for most agents, this would be a very large table—infinite, in fact, unless we place a bound on the length of percept sequences we want to consider. Given an agent to experiment with, we can, in principle, construct this table by trying out all possible percept sequences and recording which actions the agent does in response.[¹](#index_split_015.html#filepos5568128) The table is, of course, an *external* characterization of the agent. *Internally*, the agent function for an artificial agent will be implemented by an **agent program**. It is important to keep these two ideas distinct. The agent function is an abstract mathematical description; the agent program is a concrete implementation, running within some physical system.

* * *

AGENT PROGRAM

* * *

To illustrate these ideas, we use a very simple example—the vacuum-cleaner world shown in [Figure 2.2](#index_split_009.html#filepos194440). This world is so simple that we can describe everything that happens; it’s also a made-up world, so we can invent many variations. This particular world has just two locations: squares *A* and *B*. The vacuum agent perceives which square it is in and whether there is dirt in the square. It can choose to move left, move right, suck up the dirt, or do nothing. One very simple agent function is the following: if the current square is dirty, then suck; otherwise, move to the other square. A partial tabulation of this agent function is shown in [Figure 2.3](#index_split_009.html#filepos194730) and an agent program that implements it appears in [Figure 2.8](#index_split_009.html#filepos241136) [on page 48](#index_split_009.html#filepos240713).

![hand](images/00006.jpg)

Looking at [Figure 2.3](#index_split_009.html#filepos194730), we see that various vacuum-world agents can be defined simply by filling in the right-hand column in various ways. The obvious question, then, is this: *What is the right way to fill out the table?* In other words, what makes an agent good or bad, intelligent or stupid? We answer these questions in the next section.

> ![image](images/00012.jpg)

> **Figure 2.2** A vacuum-cleaner world with just two locations.

> ![image](images/00013.jpg)

> **Figure 2.3** Partial tabulation of a simple agent function for the vacuum-cleaner world shown in [Figure 2.2](#index_split_009.html#filepos194440).

Before closing this section, we should emphasize that the notion of an agent is meant to be a tool for analyzing systems, not an absolute characterization that divides the world into agents and non-agents. One could view a hand-held calculator as an agent that chooses the action of displaying “4” when given the percept sequence “2 + 2 =,” but such an analysis would hardly aid our understanding of the calculator. In a sense, all areas of engineering can be seen as designing artifacts that interact with the world; AI operates at (what the authors consider to be) the most interesting end of the spectrum, where the artifacts have significant computational resources and the task environment requires nontrivial decision making.

### 2.2 GOOD BEHAVIOR: THE CONCEPT OF RATIONALITY

A **rational agent** is one that does the right thing—conceptually speaking, every entry in the table for the agent function is filled out correctly. Obviously, doing the right thing is better than doing the wrong thing, but what does it mean to do the right thing?

* * *

RATIONAL AGENT

* * *

We answer this age-old question in an age-old way: by considering the *consequences* of the agent’s behavior. When an agent is plunked down in an environment, it generates a sequence of actions according to the percepts it receives. This sequence of actions causes the environment to go through a sequence of states. If the sequence is desirable, then the agent has performed well. This notion of desirability is captured by a **performance measure** that evaluates any given sequence of environment states.

* * *

PERFORMANCE MEASURE

* * *

Notice that we said *environment* states, not *agent* states. If we define success in terms of agent’s opinion of its own performance, an agent could achieve perfect rationality simply by deluding itself that its performance was perfect. Human agents in particular are notorious for “sour grapes”—believing they did not really want something (e.g., a Nobel Prize) after not getting it.

Obviously, there is not one fixed performance measure for all tasks and agents; typically, a designer will devise one appropriate to the circumstances. This is not as easy as it sounds. Consider, for example, the vacuum-cleaner agent from the preceding section. We might propose to measure performance by the amount of dirt cleaned up in a single eight-hour shift. With a rational agent, of course, what you ask for is what you get. A rational agent can maximize this performance measure by cleaning up the dirt, then dumping it all on the floor, then cleaning it up again, and so on. A more suitable performance measure would reward the agent for having a clean floor. For example, one point could be awarded for each clean square at each time step (perhaps with a penalty for electricity consumed and noise generated). *As a general rule, it is better to design performance measures according to what one actually wants in the environment, rather than according to how one thinks the agent should behave.*

![hand](images/00006.jpg)

Even when the obvious pitfalls are avoided, there remain some knotty issues to untangle. For example, the notion of “clean floor” in the preceding paragraph is based on average cleanliness over time. Yet the same average cleanliness can be achieved by two different agents, one of which does a mediocre job all the time while the other cleans energetically but takes long breaks. Which is preferable might seem to be a fine point of janitorial science, but in fact it is a deep philosophical question with far-reaching implications. Which is better—a reckless life of highs and lows, or a safe but humdrum existence? Which is better—an economy where everyone lives in moderate poverty, or one in which some live in plenty while others are very poor? We leave these questions as an exercise for the diligent reader.

#### **2.2.1 Rationality**

What is rational at any given time depends on four things:

> • The performance measure that defines the criterion of success.

> • The agent’s prior knowledge of the environment.

> • The actions that the agent can perform.

> • The agent’s percept sequence to date.

* * *

DEFINITION OF A RATIONAL AGENT

* * *

![hand](images/00006.jpg)

This leads to a **definition of a rational agent**:

> *For each possible percept sequence, a rational agent should select an action that is expected to maximize its performance measure, given the evidence provided by the percept sequence and whatever built-in knowledge the agent has.*

Consider the simple vacuum-cleaner agent that cleans a square if it is dirty and moves to the other square if not; this is the agent function tabulated in [Figure 2.3](#index_split_009.html#filepos194730). Is this a rational agent? That depends! First, we need to say what the performance measure is, what is known about the environment, and what sensors and actuators the agent has. Let us assume the following:

> • The performance measure awards one point for each clean square at each time step, over a “lifetime” of 1000 time steps.

> • The “geography” of the environment is known *a priori* ([Figure 2.2](#index_split_009.html#filepos194440)) but the dirt distribution and the initial location of the agent are not. Clean squares stay clean and sucking cleans the current square. The *Left* and *Right* actions move the agent left and right except when this would take the agent outside the environment, in which case the agent remains where it is.

> • The only available actions are *Left*, *Right*, and *Suck*.

> • The agent correctly perceives its location and whether that location contains dirt.

We claim that *under these circumstances* the agent is indeed rational; its expected performance is at least as high as any other agent’s. Exercise 2.2 asks you to prove this.

One can see easily that the same agent would be irrational under different circumstances. For example, once all the dirt is cleaned up, the agent will oscillate needlessly back and forth; if the performance measure includes a penalty of one point for each movement left or right, the agent will fare poorly. A better agent for this case would do nothing once it is sure that all the squares are clean. If clean squares can become dirty again, the agent should occasionally check and re-clean them if needed. If the geography of the environment is unknown, the agent will need to explore it rather than stick to squares *A* and *B*. Exercise 2.2 asks you to design agents for these cases.

#### **2.2.2 Omniscience, learning, and autonomy**

We need to be careful to distinguish between rationality and **omniscience**. An omniscient agent knows the *actual* outcome of its actions and can act accordingly; but omniscience is impossible in reality. Consider the following example: I am walking along the Champs Elysées one day and I see an old friend across the street. There is no traffic nearby and I’m not otherwise engaged, so, being rational, I start to cross the street. Meanwhile, at 33,000 feet, a cargo door falls off a passing airliner,[²](#index_split_015.html#filepos5568514) and before I make it to the other side of the street I am flattened. Was I irrational to cross the street? It is unlikely that my obituary would read “Idiot attempts to cross street.”

* * *

OMNISCIENCE

* * *

This example shows that rationality is not the same as perfection. Rationality maximizes *expected* performance, while perfection maximizes *actual* performance. Retreating from a requirement of perfection is not just a question of being fair to agents. The point is that if we expect an agent to do what turns out to be the best action after the fact, it will be impossible to design an agent to fulfill this specification—unless we improve the performance of crystal balls or time machines.

Our definition of rationality does not require omniscience, then, because the rational choice depends only on the percept sequence *to date*. We must also ensure that we haven’t inadvertently allowed the agent to engage in decidedly underintelligent activities. For example, if an agent does not look both ways before crossing a busy road, then its percept sequence will not tell it that there is a large truck approaching at high speed. Does our definition of rationality say that it’s now OK to cross the road? Far from it! First, it would not be rational to cross the road given this uninformative percept sequence: the risk of accident from crossing without looking is too great. Second, a rational agent should choose the “looking” action before stepping into the street, because looking helps maximize the expected performance. Doing actions *in order to modify future percepts*—sometimes called **information gathering**—is an important part of rationality and is covered in depth in [Chapter 16](#index_split_015.html#filepos2423989). A second example of information gathering is provided by the **exploration** that must be undertaken by a vacuum-cleaning agent in an initially unknown environment.

* * *

INFORMATION GATHERING

* * *

* * *

EXPLORATION

* * *

Our definition requires a rational agent not only to gather information but also to **learn** as much as possible from what it perceives. The agent’s initial configuration could reflect some prior knowledge of the environment, but as the agent gains experience this may be modified and augmented. There are extreme cases in which the environment is completely known *a priori*. In such cases, the agent need not perceive or learn; it simply acts correctly. Of course, such agents are fragile. Consider the lowly dung beetle. After digging its nest and laying its eggs, it fetches a ball of dung from a nearby heap to plug the entrance. If the ball of dung is removed from its grasp *en route*, the beetle continues its task and pantomimes plugging the nest with the nonexistent dung ball, never noticing that it is missing. Evolution has built an assumption into the beetle’s behavior, and when it is violated, unsuccessful behavior results. Slightly more intelligent is the sphex wasp. The female sphex will dig a burrow, go out and sting a caterpillar and drag it to the burrow, enter the burrow again to check all is well, drag the caterpillar inside, and lay its eggs. The caterpillar serves as a food source when the eggs hatch. So far so good, but if an entomologist moves the caterpillar a few inches away while the sphex is doing the check, it will revert to the “drag” step of its plan and will continue the plan without modification, even after dozens of caterpillar-moving interventions. The sphex is unable to learn that its innate plan is failing, and thus will not change it.

* * *

LEARNING

* * *

To the extent that an agent relies on the prior knowledge of its designer rather than on its own percepts, we say that the agent lacks **autonomy**. A rational agent should be autonomous—it should learn what it can to compensate for partial or incorrect prior knowledge. For example, a vacuum-cleaning agent that learns to foresee where and when additional dirt will appear will do better than one that does not. As a practical matter, one seldom requires complete autonomy from the start: when the agent has had little or no experience, it would have to act randomly unless the designer gave some assistance. So, just as evolution provides animals with enough built-in reflexes to survive long enough to learn for themselves, it would be reasonable to provide an artificial intelligent agent with some initial knowledge as well as an ability to learn. After sufficient experience of its environment, the behavior of a rational agent can become effectively *independent* of its prior knowledge. Hence, the incorporation of learning allows one to design a single rational agent that will succeed in a vast variety of environments.

* * *

AUTONOMY

* * *

### 2.3 THE NATURE OF ENVIRONMENTS

Now that we have a definition of rationality, we are almost ready to think about building rational agents. First, however, we must think about **task environments**, which are essentially the “problems” to which rational agents are the “solutions.” We begin by showing how to specify a task environment, illustrating the process with a number of examples. We then show that task environments come in a variety of flavors. The flavor of the task environment directly affects the appropriate design for the agent program.

* * *

TASK ENVIRONMENT

* * *

#### **2.3.1 Specifying the task environment**

In our discussion of the rationality of the simple vacuum-cleaner agent, we had to specify the performance measure, the environment, and the agent’s actuators and sensors. We group all these under the heading of the **task environment**. For the acronymically minded, we call this the **PEAS** (**P**erformance, **E**nvironment, **A**ctuators, **S**ensors) description. In designing an agent, the first step must always be to specify the task environment as fully as possible.

* * *

PEAS

* * *

The vacuum world was a simple example; let us consider a more complex problem: an automated taxi driver. We should point out, before the reader becomes alarmed, that a fully automated taxi is currently somewhat beyond the capabilities of existing technology. ([page 28](#index_split_008.html#filepos166159) describes an existing driving robot.) The full driving task is extremely *open-ended*. There is no limit to the novel combinations of circumstances that can arise—another reason we chose it as a focus for discussion. [Figure 2.4](#index_split_009.html#filepos212464) summarizes the PEAS description for the taxi’s task environment. We discuss each element in more detail in the following paragraphs.

> ![image](images/00014.jpg)

> **Figure 2.4** PEAS description of the task environment for an automated taxi.

First, what is the **performance measure** to which we would like our automated driver to aspire? Desirable qualities include getting to the correct destination; minimizing fuel consumption and wear and tear; minimizing the trip time or cost; minimizing violations of traffic laws and disturbances to other drivers; maximizing safety and passenger comfort; maximizing profits. Obviously, some of these goals conflict, so tradeoffs will be required.

Next, what is the driving **environment** that the taxi will face? Any taxi driver must deal with a variety of roads, ranging from rural lanes and urban alleys to 12-lane freeways. The roads contain other traffic, pedestrians, stray animals, road works, police cars, puddles, and potholes. The taxi must also interact with potential and actual passengers. There are also some optional choices. The taxi might need to operate in Southern California, where snow is seldom a problem, or in Alaska, where it seldom is not. It could always be driving on the right, or we might want it to be flexible enough to drive on the left when in Britain or Japan. Obviously, the more restricted the environment, the easier the design problem.

The **actuators** for an automated taxi include those available to a human driver: control over the engine through the accelerator and control over steering and braking. In addition, it will need output to a display screen or voice synthesizer to talk back to the passengers, and perhaps some way to communicate with other vehicles, politely or otherwise.

The basic **sensors** for the taxi will include one or more controllable video cameras so that it can see the road; it might augment these with infrared or sonar sensors to detect distances to other cars and obstacles. To avoid speeding tickets, the taxi should have a speedometer, and to control the vehicle properly, especially on curves, it should have an accelerometer. To determine the mechanical state of the vehicle, it will need the usual array of engine, fuel, and electrical system sensors. Like many human drivers, it might want a global positioning system (GPS) so that it doesn’t get lost. Finally, it will need a keyboard or microphone for the passenger to request a destination.

In [Figure 2.5](#index_split_009.html#filepos218211), we have sketched the basic PEAS elements for a number of additional agent types. Further examples appear in Exercise 2.4. It may come as a surprise to some readers that our list of agent types includes some programs that operate in the entirely artificial environment defined by keyboard input and character output on a screen. “Surely,” one might say, “this is not a real environment, is it?” In fact, what matters is not the distinction between “real” and “artificial” environments, but the complexity of the relationship among the behavior of the agent, the percept sequence generated by the environment, and the performance measure. Some “real” environments are actually quite simple. For example, a robot designed to inspect parts as they come by on a conveyor belt can make use of a number of simplifying assumptions: that the lighting is always just so, that the only thing on the conveyor belt will be parts of a kind that it knows about, and that only two actions (accept or reject) are possible.

In contrast, some **software agents** (or software robots or **softbots**) exist in rich, unlimited domains. Imagine a softbot Web site operator designed to scan Internet news sources and show the interesting items to its users, while selling advertising space to generate revenue. To do well, that operator will need some natural language processing abilities, it will need to learn what each user and advertiser is interested in, and it will need to change its plans dynamically—for example, when the connection for one news source goes down or when a new one comes online. The Internet is an environment whose complexity rivals that of the physical world and whose inhabitants include many artificial and human agents.

* * *

SOFTWARE AGENT

* * *

* * *

SOFTBOT

* * *

#### **2.3.2 Properties of task environments**

The range of task environments that might arise in AI is obviously vast. We can, however, identify a fairly small number of dimensions along which task environments can be categorized. These dimensions determine, to a large extent, the appropriate agent design and the applicability of each of the principal families of techniques for agent implementation. First, we list the dimensions, then we analyze several task environments to illustrate the ideas. The definitions here are informal; later chapters provide more precise statements and examples of each kind of environment.

> ![image](images/00015.jpg)

> **Figure 2.5** Examples of agent types and their PEAS descriptions.

**Fully observable** vs. **partially observable**: If an agent’s sensors give it access to the complete state of the environment at each point in time, then we say that the task environment is fully observable. A task environment is effectively fully observable if the sensors detect all aspects that are *relevant* to the choice of action; relevance, in turn, depends on the performance measure. Fully observable environments are convenient because the agent need not maintain any internal state to keep track of the world. An environment might be partially observable because of noisy and inaccurate sensors or because parts of the state are simply missing from the sensor data—for example, a vacuum agent with only a local dirt sensor cannot tell whether there is dirt in other squares, and an automated taxi cannot see what other drivers are thinking. If the agent has no sensors at all then the environment is **unobservable**. One might think that in such cases the agent’s plight is hopeless, but, as we discuss in [Chapter 4](#index_split_000.html#filepos513290), the agent’s goals may still be achievable, sometimes with certainty.

* * *

FULLY OBSERVABLE

* * *

* * *

PARTIALLY OBSERVABLE

* * *

* * *

UNOBSERVABLE

* * *

**Single agent** vs. **multiagent**: The distinction between single-agent and multiagent environments may seem simple enough. For example, an agent solving a crossword puzzle by itself is clearly in a single-agent environment, whereas an agent playing chess is in a two-agent environment. There are, however, some subtle issues. First, we have described how an entity *may* be viewed as an agent, but we have not explained which entities *must* be viewed as agents. Does an agent *A* (the taxi driver for example) have to treat an object *B* (another vehicle) as an agent, or can it be treated merely as an object behaving according to the laws of physics, analogous to waves at the beach or leaves blowing in the wind? The key distinction is whether *B*’s behavior is best described as maximizing a performance measure whose value depends on agent *A*’s behavior. For example, in chess, the opponent entity *B* is trying to maximize its performance measure, which, by the rules of chess, minimizes agent *A*’s performance measure. Thus, chess is a **competitive** multiagent environment. In the taxi-driving environment, on the other hand, avoiding collisions maximizes the performance measure of all agents, so it is a partially **cooperative** multiagent environment. It is also partially competitive because, for example, only one car can occupy a parking space. The agent-design problems in multiagent environments are often quite different from those in single-agent environments; for example, **communication** often emerges as a rational behavior in multiagent environments; in some competitive environments, **randomized behavior** is rational because it avoids the pitfalls of predictability.

* * *

SINGLE AGENT

* * *

* * *

MULTIAGENT

* * *

* * *

COMPETITIVE

* * *

* * *

COOPERATIVE

* * *

**Deterministic** vs. **stochastic**. If the next state of the environment is completely determined by the current state and the action executed by the agent, then we say the environment is deterministic; otherwise, it is stochastic. In principle, an agent need not worry about uncertainty in a fully observable, deterministic environment. (In our definition, we ignore uncertainty that arises purely from the actions of other agents in a multiagent environment; thus, a game can be deterministic even though each agent may be unable to predict the actions of the others.) If the environment is partially observable, however, then it could *appear* to be stochastic. Most real situations are so complex that it is impossible to keep track of all the unobserved aspects; for practical purposes, they must be treated as stochastic. Taxi driving is clearly stochastic in this sense, because one can never predict the behavior of traffic exactly; moreover, one’s tires blow out and one’s engine seizes up without warning. The vacuum world as we described it is deterministic, but variations can include stochastic elements such as randomly appearing dirt and an unreliable suction mechanism (Exercise 2.13). We say an environment is **uncertain** if it is not fully observable or not deterministic. One final note: our use of the word “stochastic” generally implies that uncertainty about outcomes is quantified in terms of probabilities; a **nondeterministic** environment is one in which actions are characterized by their *possible* outcomes, but no probabilities are attached to them. Nondeterministic environment descriptions are usually associated with performance measures that require the agent to succeed for *all possible* outcomes of its actions.

* * *

DETERMINISTIC

* * *

* * *

STOCHASTIC

* * *

* * *

UNCERTAIN

* * *

* * *

NONDETERMINISTIC

* * *

**Episodic** vs. **sequential**: In an episodic task environment, the agent’s experience is divided into atomic episodes. In each episode the agent receives a percept and then performs a single action. Crucially, the next episode does not depend on the actions taken in previous episodes. Many classification tasks are episodic. For example, an agent that has to spot defective parts on an assembly line bases each decision on the current part, regardless of previous decisions; moreover, the current decision doesn’t affect whether the next part is defective. In sequential environments, on the other hand, the current decision could affect all future decisions.[³](#index_split_015.html#filepos5568746) Chess and taxi driving are sequential: in both cases, short-term actions can have long-term consequences. Episodic environments are much simpler than sequential environments because the agent does not need to think ahead.

* * *

EPISODIC

* * *

* * *

SEQUENTIAL

* * *

**Static** vs. **dynamic**: If the environment can change while an agent is deliberating, then we say the environment is dynamic for that agent; otherwise, it is static. Static environments are easy to deal with because the agent need not keep looking at the world while it is deciding on an action, nor need it worry about the passage of time. Dynamic environments, on the other hand, are continuously asking the agent what it wants to do; if it hasn’t decided yet, that counts as deciding to do nothing. If the environment itself does not change with the passage of time but the agent’s performance score does, then we say the environment is **semidynamic**. Taxi driving is clearly dynamic: the other cars and the taxi itself keep moving while the driving algorithm dithers about what to do next. Chess, when played with a clock, is semidynamic. Crossword puzzles are static.

* * *

STATIC

* * *

* * *

DYNAMIC

* * *

* * *

SEMIDYNAMIC

* * *

**Discrete** vs. **continuous**: The discrete/continuous distinction applies to the *state* of the environment, to the way *time* is handled, and to the *percepts* and *actions* of the agent. For example, the chess environment has a finite number of distinct states (excluding the clock). Chess also has a discrete set of percepts and actions. Taxi driving is a continuous-state and continuous-time problem: the speed and location of the taxi and of the other vehicles sweep through a range of continuous values and do so smoothly over time. Taxi-driving actions are also continuous (steering angles, etc.). Input from digital cameras is discrete, strictly speaking, but is typically treated as representing continuously varying intensities and locations.

* * *

DISCRETE

* * *

* * *

CONTINUOUS

* * *

**Known** vs. **unknown**: Strictly speaking, this distinction refers not to the environment itself but to the agent’s (or designer’s) state of knowledge about the “laws of physics” of the environment. In a known environment, the outcomes (or outcome probabilities if the environment is stochastic) for all actions are given. Obviously, if the environment is unknown, the agent will have to learn how it works in order to make good decisions. Note that the distinction between known and unknown environments is not the same as the one between fully and partially observable environments. It is quite possible for a *known* environment to be *partially* observable—for example, in solitaire card games, I know the rules but am still unable to see the cards that have not yet been turned over. Conversely, an *unknown* environment can be *fully* observable—in a new video game, the screen may show the entire game state but I still don’t know what the buttons do until I try them.

* * *

KNOWN

* * *

* * *

UNKNOWN

* * *

As one might expect, the hardest case is *partially observable*, *multiagent*, *stochastic*, *sequential*, *dynamic*, *continuous*, and *unknown*. Taxi driving is hard in all these senses, except that for the most part the driver’s environment is known. Driving a rented car in a new country with unfamiliar geography and traffic laws is a lot more exciting.

[Figure 2.6](#index_split_009.html#filepos230832) lists the properties of a number of familiar environments. Note that the answers are not always cut and dried. For example, we describe the part-picking robot as episodic, because it normally considers each part in isolation. But if one day there is a large batch of defective parts, the robot should learn from several observations that the distribution of defects has changed, and should modify its behavior for subsequent parts. We have not included a “known/unknown” column because, as explained earlier, this is not strictly a property of the environment. For some environments, such as chess and poker, it is quite easy to supply the agent with full knowledge of the rules, but it is nonetheless interesting to consider how an agent might learn to play these games without such knowledge.

> ![image](images/00016.jpg)

> **Figure 2.6** Examples of task environments and their characteristics.

Several of the answers in the table depend on how the task environment is defined. We have listed the medical-diagnosis task as single-agent because the disease process in a patient is not profitably modeled as an agent; but a medical-diagnosis system might also have to deal with recalcitrant patients and skeptical staff, so the environment could have a multiagent aspect. Furthermore, medical diagnosis is episodic if one conceives of the task as selecting a diagnosis given a list of symptoms; the problem is sequential if the task can include proposing a series of tests, evaluating progress over the course of treatment, and so on. Also, many environments are episodic at higher levels than the agent’s individual actions. For example, a chess tournament consists of a sequence of games; each game is an episode because (by and large) the contribution of the moves in one game to the agent’s overall performance is not affected by the moves in its previous game. On the other hand, decision making within a single game is certainly sequential.

The code repository associated with this book (aima.cs.berkeley.edu) includes implementations of a number of environments, together with a general-purpose environment simulator that places one or more agents in a simulated environment, observes their behavior over time, and evaluates them according to a given performance measure. Such experiments are often carried out not for a single environment but for many environments drawn from an **environment class**. For example, to evaluate a taxi driver in simulated traffic, we would want to run many simulations with different traffic, lighting, and weather conditions. If we designed the agent for a single scenario, we might be able to take advantage of specific properties of the particular case but might not identify a good design for driving in general. For this reason, the code repository also includes an **environment generator** for each environment class that selects particular environments (with certain likelihoods) in which to run the agent. For example, the vacuum environment generator initializes the dirt pattern and agent location randomly. We are then interested in the agent’s average performance over the environment class. A rational agent for a given environment class maximizes this average performance. Exercises 2.8 to 2.13 take you through the process of developing an environment class and evaluating various agents therein.

* * *

ENVIRONMENT CLASS

* * *

* * *

ENVIRONMENT GENERATOR

* * *

### 2.4 THE STRUCTURE OF AGENTS

So far we have talked about agents by describing *behavior*—the action that is performed after any given sequence of percepts. Now we must bite the bullet and talk about how the insides work. The job of AI is to design an **agent program** that implements the agent function—the mapping from percepts to actions. We assume this program will run on some sort of computing device with physical sensors and actuators—we call this the **architecture**:

> *agent* = *architecture* + *program*.

* * *

AGENT PROGRAM

* * *

* * *

ARCHITECTURE

* * *

Obviously, the program we choose has to be one that is appropriate for the architecture. If the program is going to recommend actions like *Walk*, the architecture had better have legs. The architecture might be just an ordinary PC, or it might be a robotic car with several onboard computers, cameras, and other sensors. In general, the architecture makes the percepts from the sensors available to the program, runs the program, and feeds the program’s action choices to the actuators as they are generated. Most of this book is about designing agent programs, although [Chapters 24](#index_split_015.html#filepos3631932) and [25](#index_split_015.html#filepos3777962) deal directly with the sensors and actuators.

#### **2.4.1 Agent programs**

The agent programs that we design in this book all have the same skeleton: they take the current percept as input from the sensors and return an action to the actuators.[⁴](#index_split_015.html#filepos5569002) Notice the difference between the agent program, which takes the current percept as input, and the agent function, which takes the entire percept history. The agent program takes just the current percept as input because nothing more is available from the environment; if the agent’s actions need to depend on the entire percept sequence, the agent will have to remember the percepts.

We describe the agent programs in the simple pseudocode language that is defined in Appendix B. (The online code repository contains implementations in real programming languages.) For example, [Figure 2.7](#index_split_009.html#filepos237294) shows a rather trivial agent program that keeps track of the percept sequence and then uses it to index into a table of actions to decide what to do. The table—an example of which is given for the vacuum world in [Figure 2.3](#index_split_009.html#filepos194730)—represents explicitly the agent function that the agent program embodies. To build a rational agent in this way, we as designers must construct a table that contains the appropriate action for every possible percept sequence.

> ![image](images/00017.jpg)

> **Figure 2.7** The TABLE\-DRIVEN\-AGENT program is invoked for each new percept and returns an action each time. It retains the complete percept sequence in memory.

It is instructive to consider why the table-driven approach to agent construction is doomed to failure. Let *P* be the set of possible percepts and let *T* be the lifetime of the agent (the total number of percepts it will receive). The lookup table will contain ![square.jpg](images/00018.jpg)entries. Consider the automated taxi: the visual input from a single camera comes in at the rate of roughly 27 megabytes per second (30 frames per second, 640 × 480 pixels with 24 bits of color information). This gives a lookup table with over 10^(250,000,000,000) entries for an hour’s driving. Even the lookup table for chess—a tiny, well-behaved fragment of the real world—would have at least 10^(150) entries. The daunting size of these tables (the number of atoms in the observable universe is less than 10^(80)) means that (a) no physical agent in this universe will have the space to store the table, (b) the designer would not have time to create the table, (c) no agent could ever learn all the right table entries from its experience, and (d) even if the environment is simple enough to yield a feasible table size, the designer still has no guidance about how to fill in the table entries.

Despite all this, TABLE\-DRIVEN\-AGENT *does* do what we want: it implements the desired agent function. The key challenge for AI is to find out how to write programs that, to the extent possible, produce rational behavior from a smallish program rather than from a vast table. We have many examples showing that this can be done successfully in other areas: for example, the huge tables of square roots used by engineers and schoolchildren prior to the 1970s have now been replaced by a five-line program for Newton’s method running on electronic calculators. The question is, can AI do for general intelligent behavior what Newton did for square roots? We believe the answer is yes.

In the remainder of this section, we outline four basic kinds of agent programs that embody the principles underlying almost all intelligent systems:

> • Simple reflex agents;

> • Model-based reflex agents;

> • Goal-based agents; and

> • Utility-based agents.

Each kind of agent program combines particular components in particular ways to generate actions. [Section 2.4.6](#index_split_000.html#filepos263526) explains in general terms how to convert all these agents into *learning* *agents* that can improve the performance of their components so as to generate better actions. Finally, [Section 2.4.7](#index_split_000.html#filepos271690) describes the variety of ways in which the components themselves can be represented within the agent. This variety provides a major organizing principle for the field and for the book itself.

> ![image](images/00019.jpg)

> **Figure 2.8** The agent program for a simple reflex agent in the two-state vacuum environment. This program implements the agent function tabulated in [Figure 2.3](#index_split_009.html#filepos194730).

#### **2.4.2 Simple reflex agents**

The simplest kind of agent is the **simple reflex agent**. These agents select actions on the basis of the *current* percept, ignoring the rest of the percept history. For example, the vacuum agent whose agent function is tabulated in [Figure 2.3](#index_split_009.html#filepos194730) is a simple reflex agent, because its decision is based only on the current location and on whether that location contains dirt. An agent program for this agent is shown in [Figure 2.8](#index_split_009.html#filepos241136).

* * *

SIMPLE REFLEX AGENT

* * *

Notice that the vacuum agent program is very small indeed compared to the corresponding table. The most obvious reduction comes from ignoring the percept history, which cuts down the number of possibilities from 4^(*T*) to just 4. A further, small reduction comes from the fact that when the current square is dirty, the action does not depend on the location.

Simple reflex behaviors occur even in more complex environments. Imagine yourself as the driver of the automated taxi. If the car in front brakes and its brake lights come on, then you should notice this and initiate braking. In other words, some processing is done on the visual input to establish the condition we call “The car in front is braking.” Then, this triggers some established connection in the agent program to the action “initiate braking.” We call such a connection a **condition–action rule**,[⁵](#index_split_015.html#filepos5569438) written as

* * *

CONDITION–ACTION RULE

* * *

> **if** *car-in-frontis-braking* **then** *initiate-braking*.

Humans also have many such connections, some of which are learned responses (as for driving) and some of which are innate reflexes (such as blinking when something approaches the eye). In the course of the book, we show several different ways in which such connections can be learned and implemented.

The program in [Figure 2.8](#index_split_009.html#filepos241136) is specific to one particular vacuum environment. A more general and flexible approach is first to build a general-purpose interpreter for condition–action rules and then to create rule sets for specific task environments. [Figure 2.9](#index_split_009.html#filepos245453) gives the structure of this general program in schematic form, showing how the condition–action rules allow the agent to make the connection from percept to action. (Do not worry if this seems trivial; it gets more interesting shortly.) We use rectangles to denote the current internal state of the agent’s decision process, and ovals to represent the background information used in the process. The agent program, which is also very simple, is shown in [Figure 2.10](#index_split_009.html#filepos245739). The INTERPRET\-INPUT function generates an abstracted description of the current state from the percept, and the RULE\-MATCH function returns the first rule in the set of rules that matches the given state description. Note that the description in terms of “rules” and “matching” is purely conceptual; actual implementations can be as simple as a collection of logic gates implementing a Boolean circuit.

> ![image](images/00020.jpg)

> **Figure 2.9** Schematic diagram of a simple reflex agent.

> ![image](images/00021.jpg)

> **Figure 2.10** A simple reflex agent. It acts according to a rule whose condition matches the current state, as defined by the percept.

![hand](images/00006.jpg)

Simple reflex agents have the admirable property of being simple, but they turn out to be of limited intelligence. The agent in [Figure 2.10](#index_split_009.html#filepos245739) will work *only if the correct decision can be made on the basis of only the current percept—that is, only if the environment is fully observable.* Even a little bit of unobservability can cause serious trouble. For example, the braking rule given earlier assumes that the condition *car-in-frontis-braking* can be determined from the current percept—a single frame of video. This works if the car in front has a centrally mounted brake light. Unfortunately, older models have different configurations of taillights, brake lights, and turn-signal lights, and it is not always possible to tell from a single image whether the car is braking. A simple reflex agent driving behind such a car would either brake continuously and unnecessarily, or, worse, never brake at all.

We can see a similar problem arising in the vacuum world. Suppose that a simple reflex vacuum agent is deprived of its location sensor and has only a dirt sensor. Such an agent has just two possible percepts: \[*Dirty*\] and \[*Clean*\]. It can *Suck* in response to \[*Dirty*\]; what should it do in response to \[*Clean*\]? Moving *Left* fails (forever) if it happens to start in square *A*, and moving *Right* fails (forever) if it happens to start in square *B*. Infinite loops are often unavoidable for simple reflex agents operating in partially observable environments.

Escape from infinite loops is possible if the agent can **randomize** its actions. For example, if the vacuum agent perceives \[*Clean*\], it might flip a coin to choose between *Left* and *Right*. It is easy to show that the agent will reach the other square in an average of two steps. Then, if that square is dirty, the agent will clean it and the task will be complete. Hence, a randomized simple reflex agent might outperform a deterministic simple reflex agent.

* * *

RANDOMIZATION

* * *

We mentioned in [Section 2.3](#index_split_000.html#filepos209973) that randomized behavior of the right kind can be rational in some multiagent environments. In single-agent environments, randomization is usually *not* rational. It is a useful trick that helps a simple reflex agent in some situations, but in most cases we can do much better with more sophisticated deterministic agents.

#### **2.4.3 Model-based reflex agents**

The most effective way to handle partial observability is for the agent to *keep track of the part of the world it can’t see now*. That is, the agent should maintain some sort of **internal state** that depends on the percept history and thereby reflects at least some of the unobserved aspects of the current state. For the braking problem, the internal state is not too extensive—just the previous frame from the camera, allowing the agent to detect when two red lights at the edge of the vehicle go on or off simultaneously. For other driving tasks such as changing lanes, the agent needs to keep track of where the other cars are if it can’t see them all at once. And for any driving to be possible at all, the agent needs to keep track of where its keys are.

* * *

INTERNAL STATE

* * *

Updating this internal state information as time goes by requires two kinds of knowledge to be encoded in the agent program. First, we need some information about how the world evolves independently of the agent—for example, that an overtaking car generally will be closer behind than it was a moment ago. Second, we need some information about how the agent’s own actions affect the world—for example, that when the agent turns the steering wheel clockwise, the car turns to the right, or that after driving for five minutes northbound on the freeway, one is usually about five miles north of where one was five minutes ago. This knowledge about “how the world works”—whether implemented in simple Boolean circuits or in complete scientific theories—is called a **model** of the world. An agent that uses such a model is called a **model-based agent**.

* * *

MODEL-BASED AGENT

* * *

[Figure 2.11](#index_split_009.html#filepos252157) gives the structure of the model-based reflex agent with internal state, showing how the current percept is combined with the old internal state to generate the updated description of the current state, based on the agent’s model of how the world works. The agent program is shown in [Figure 2.12](#index_split_009.html#filepos252428). The interesting part is the function UPDATE\-STATE, which is responsible for creating the new internal state description. The details of how models and states are represented vary widely depending on the type of environment and the particular technology used in the agent design. Detailed examples of models and updating algorithms appear in [Chapters 4](#index_split_000.html#filepos513290), [12](#index_split_015.html#filepos1750417), [11](#index_split_015.html#filepos1612250), [15](#index_split_015.html#filepos2253296), [17](#index_split_015.html#filepos2562268), and [25](#index_split_015.html#filepos3777962).

> ![image](images/00022.jpg)

> **Figure 2.11** A model-based reflex agent.

> ![image](images/00023.jpg)

> **Figure 2.12** A model-based reflex agent. It keeps track of the current state of the world, using an internal model. It then chooses an action in the same way as the reflex agent.

Regardless of the kind of representation used, it is seldom possible for the agent to determine the current state of a partially observable environment *exactly*. Instead, the box labeled “what the world is like now” ([Figure 2.11](#index_split_009.html#filepos252157)) represents the agent’s “best guess” (or sometimes best guesses). For example, an automated taxi may not be able to see around the large truck that has stopped in front of it and can only guess about what may be causing the hold-up. Thus, uncertainty about the current state may be unavoidable, but the agent still has to make a decision.

A perhaps less obvious point about the internal “state” maintained by a model-based agent is that it does not have to describe “what the world is like now” in a literal sense. For 52example, the taxi may be driving back home, and it may have a rule telling it to fill up with gas on the way home unless it has at least half a tank. Although “driving back home” may *seem* to an aspect of the world state, the fact of the taxi’s *destination* is actually an aspect of the agent’s internal state. If you find this puzzling, consider that the taxi could be in exactly the same place at the same time, but intending to reach a different destination.

> ![image](images/00024.jpg)

> **Figure 2.13** A model-based, goal-based agent. It keeps track of the world state as well as a set of goals it is trying to achieve, and chooses an action that will (eventually) lead to the achievement of its goals.

#### **2.4.4 Goal-based agents**

Knowing something about the current state of the environment is not always enough to decide what to do. For example, at a road junction, the taxi can turn left, turn right, or go straight on. The correct decision depends on where the taxi is trying to get to. In other words, as well as a current state description, the agent needs some sort of **goal** information that describes situations that are desirable—for example, being at the passenger’s destination. The agent program can combine this with the model (the same information as was used in the model-based reflex agent) to choose actions that achieve the goal. [Figure 2.13](#index_split_009.html#filepos254297) shows the goal-based agent’s structure.

* * *

GOAL

* * *

Sometimes goal-based action selection is straightforward—for example, when goal satisfaction results immediately from a single action. Sometimes it will be more tricky—for example, when the agent has to consider long sequences of twists and turns in order to find a way to achieve the goal. **Search** ([Chapters 3](#index_split_000.html#filepos301685) to [5](#index_split_000.html#filepos660071)) and **planning** ([Chapters 10](#index_split_015.html#filepos1477055) and [11](#index_split_015.html#filepos1612250)) are the subfields of AI devoted to finding action sequences that achieve the agent’s goals.

Notice that decision making of this kind is fundamentally different from the condition–action rules described earlier, in that it involves consideration of the future—both “What will happen if I do such-and-such?” and “Will that make me happy?” In the reflex agent designs, this information is not explicitly represented, because the built-in rules map directly from percepts to actions. The reflex agent brakes when it sees brake lights. A goal-based agent, in principle, could reason that if the car in front has its brake lights on, it will slow down. Given the way the world usually evolves, the only action that will achieve the goal of not hitting other cars is to brake.

Although the goal-based agent appears less efficient, it is more flexible because the knowledge that supports its decisions is represented explicitly and can be modified. If it starts to rain, the agent can update its knowledge of how effectively its brakes will operate; this will automatically cause all of the relevant behaviors to be altered to suit the new conditions. For the reflex agent, on the other hand, we would have to rewrite many condition–action rules. The goal-based agent’s behavior can easily be changed to go to a different destination, simply by specifying that destination as the goal. The reflex agent’s rules for when to turn and when to go straight will work only for a single destination; they must all be replaced to go somewhere new.

#### **2.4.5 Utility-based agents**

Goals alone are not enough to generate high-quality behavior in most environments. For example, many action sequences will get the taxi to its destination (thereby achieving the goal) but some are quicker, safer, more reliable, or cheaper than others. Goals just provide a crude binary distinction between “happy” and “unhappy” states. A more general performance measure should allow a comparison of different world states according to exactly how happy they would make the agent. Because “happy” does not sound very scientific, economists and computer scientists use the term **utility** instead.[⁶](#index_split_015.html#filepos5569676)

* * *

UTILITY

* * *

We have already seen that a performance measure assigns a score to any given sequence of environment states, so it can easily distinguish between more and less desirable ways of getting to the taxi’s destination. An agent’s **utility function** is essentially an internalization of the performance measure. If the internal utility function and the external performance measure are in agreement, then an agent that chooses actions to maximize its utility will be rational according to the external performance measure.

* * *

UTILITY FUNCTION

* * *

Let us emphasize again that this is not the *only* way to be rational—we have already seen a rational agent program for the vacuum world ([Figure 2.8](#index_split_009.html#filepos241136)) that has no idea what its utility function is—but, like goal-based agents, a utility-based agent has many advantages in terms of flexibility and learning. Furthermore, in two kinds of cases, goals are inadequate but a utility-based agent can still make rational decisions. First, when there are conflicting goals, only some of which can be achieved (for example, speed and safety), the utility function specifies the appropriate tradeoff. Second, when there are several goals that the agent can aim for, none of which can be achieved with certainty, utility provides a way in which the likelihood of success can be weighed against the importance of the goals.

Partial observability and stochasticity are ubiquitous in the real world, and so, therefore, is decision making under uncertainty. Technically speaking, a rational utility-based agent chooses the action that maximizes the **expected utility** of the action outcomes—that is, the utility the agent expects to derive, on average, given the probabilities and utilities of each outcome. (Appendix A defines expectation more precisely.) In [Chapter 16](#index_split_015.html#filepos2423989), we show that any rational agent must behave *as if* it possesses a utility function whose expected value it tries to maximize. An agent that possesses an *explicit* utility function can make rational decisions with a general-purpose algorithm that does not depend on the specific utility function being maximized. In this way, the “global” definition of rationality—designating as rational those agent functions that have the highest performance—is turned into a “local” constraint on rational-agent designs that can be expressed in a simple program.

> ![image](images/00025.jpg)

> **Figure 2.14** A model-based, utility-based agent. It uses a model of the world, along with a utility function that measures its preferences among states of the world. Then it chooses the action that leads to the best expected utility, where expected utility is computed by averaging over all possible outcome states, weighted by the probability of the outcome.

* * *

EXPECTED UTILITY

* * *

The utility-based agent structure appears in [Figure 2.14](#index_split_009.html#filepos261711). Utility-based agent programs appear in Part IV, where we design decision-making agents that must handle the uncertainty inherent in stochastic or partially observable environments.

At this point, the reader may be wondering, “Is it that simple? We just build agents that maximize expected utility, and we’re done?” It’s true that such agents would be intelligent, but it’s not simple. A utility-based agent has to model and keep track of its environment, tasks that have involved a great deal of research on perception, representation, reasoning, and learning. The results of this research fill many of the chapters of this book. Choosing the utility-maximizing course of action is also a difficult task, requiring ingenious algorithms that fill several more chapters. Even with these algorithms, perfect rationality is usually unachievable in practice because of computational complexity, as we noted in [Chapter 1](#index_split_000.html#filepos57382).

#### **2.4.6 Learning agents**

We have described agent programs with various methods for selecting actions. We have not, so far, explained how the agent programs *come into being*. In his famous early paper, Turing (1950) considers the idea of actually programming his intelligent machines by hand. He estimates how much work this might take and concludes “Some more expeditious method seems desirable.” The method he proposes is to build learning machines and then to teach them. In many areas of AI, this is now the preferred method for creating state-of-the-art systems. Learning has another advantage, as we noted earlier: it allows the agent to operate in initially unknown environments and to become more competent than its initial knowledge alone might allow. In this section, we briefly introduce the main ideas of learning agents. Throughout the book, we comment on opportunities and methods for learning in particular kinds of agents. Part V goes into much more depth on the learning algorithms themselves.

> ![image](images/00026.jpg)

> **Figure 2.15** A general learning agent.

A learning agent can be divided into four conceptual components, as shown in [Figure 2.15](#index_split_009.html#filepos264745). The most important distinction is between the **learning element**, which is responsible for making improvements, and the **performance element**, which is responsible for selecting external actions. The performance element is what we have previously considered to be the entire agent: it takes in percepts and decides on actions. The learning element uses feedback from the **critic** on how the agent is doing and determines how the performance element should be modified to do better in the future.

* * *

LEARNING ELEMENT

* * *

* * *

PERFORMANCE ELEMENT

* * *

* * *

CRITIC

* * *

The design of the learning element depends very much on the design of the performance element. When trying to design an agent that learns a certain capability, the first question is not “How am I going to get it to learn this?” but “What kind of performance element will my agent need to do this once it has learned how?” Given an agent design, learning mechanisms can be constructed to improve every part of the agent.

The critic tells the learning element how well the agent is doing with respect to a fixed performance standard. The critic is necessary because the percepts themselves provide no indication of the agent’s success. For example, a chess program could receive a percept indicating that it has checkmated its opponent, but it needs a performance standard to know that this is a good thing; the percept itself does not say so. It is important that the performance standard be fixed. Conceptually, one should think of it as being outside the agent altogether because the agent must not modify it to fit its own behavior.

The last component of the learning agent is the **problem generator**. It is responsible for suggesting actions that will lead to new and informative experiences. The point is that if the performance element had its way, it would keep doing the actions that are best, given what it knows. But if the agent is willing to explore a little and do some perhaps suboptimal actions in the short run, it might discover much better actions for the long run. The problem generator’s job is to suggest these exploratory actions. This is what scientists do when they carry out experiments. Galileo did not think that dropping rocks from the top of a tower in Pisa was valuable in itself. He was not trying to break the rocks or to modify the brains of unfortunate passers-by. His aim was to modify his own brain by identifying a better theory of the motion of objects.

* * *

PROBLEM GENERATOR

* * *

To make the overall design more concrete, let us return to the automated taxi example. The performance element consists of whatever collection of knowledge and procedures the taxi has for selecting its driving actions. The taxi goes out on the road and drives, using this performance element. The critic observes the world and passes information along to the learning element. For example, after the taxi makes a quick left turn across three lanes of traffic, the critic observes the shocking language used by other drivers. From this experience, the learning element is able to formulate a rule saying this was a bad action, and the performance element is modified by installation of the new rule. The problem generator might identify certain areas of behavior in need of improvement and suggest experiments, such as trying out the brakes on different road surfaces under different conditions.

The learning element can make changes to any of the “knowledge” components shown in the agent diagrams ([Figures 2.9](#index_split_009.html#filepos245453), [2.11](#index_split_009.html#filepos252157), [2.13](#index_split_009.html#filepos254297), and [2.14](#index_split_009.html#filepos261711)). The simplest cases involve learning directly from the percept sequence. Observation of pairs of successive states of the environment can allow the agent to learn “How the world evolves,” and observation of the results of its actions can allow the agent to learn “What my actions do.” For example, if the taxi exerts a certain braking pressure when driving on a wet road, then it will soon find out how much deceleration is actually achieved. Clearly, these two learning tasks are more difficult if the environment is only partially observable.

The forms of learning in the preceding paragraph do not need to access the external performance standard—in a sense, the standard is the universal one of making predictions that agree with experiment. The situation is slightly more complex for a utility-based agent that wishes to learn utility information. For example, suppose the taxi-driving agent receives no tips from passengers who have been thoroughly shaken up during the trip. The external performance standard must inform the agent that the loss of tips is a negative contribution to its overall performance; then the agent might be able to learn that violent maneuvers do not contribute to its own utility. In a sense, the performance standard distinguishes part of the incoming percept as a **reward** (or **penalty**) that provides direct feedback on the quality of the agent’s behavior. Hard-wired performance standards such as pain and hunger in animals can be understood in this way. This issue is discussed further in [Chapter 21](#index_split_015.html#filepos3262268).

In summary, agents have a variety of components, and those components can be represented in many ways within the agent program, so there appears to be great variety among learning methods. There is, however, a single unifying theme. Learning in intelligent agents can be summarized as a process of modification of each component of the agent to bring the components into closer agreement with the available feedback information, thereby improving the overall performance of the agent.

#### **2.4.7 How the components of agent programs work**

We have described agent programs (in very high-level terms) as consisting of various components, whose function it is to answer questions such as: “What is the world like now?” “What action should I do now?” “What do my actions do?” The next question for a student of AI is, “How on earth do these components work?” It takes about a thousand pages to begin to answer that question properly, but here we want to draw the reader’s attention to some basic distinctions among the various ways that the components can represent the environment that the agent inhabits.

Roughly speaking, we can place the representations along an axis of increasing complexity and expressive power—**atomic**, **factored**, and **structured**. To illustrate these ideas, it helps to consider a particular agent component, such as the one that deals with “What my actions do.” This component describes the changes that might occur in the environment as the result of taking an action, and [Figure 2.16](#index_split_009.html#filepos273210) provides schematic depictions of how those transitions might be represented. (a) Atomic (b) Factored (b) Structured

> ![image](images/00027.jpg)

> **Figure 2.16** Three ways to represent states and the transitions between them. (a) Atomic representation: a state (such as B or C) is a black box with no internal structure; (b) Factored representation: a state consists of a vector of attribute values; values can be Boolean, real-valued, or one of a fixed set of symbols. (c) Structured representation: a state includes objects, each of which may have attributes of its own as well as relationships to other objects.

In an **atomic representation** each state of the world is indivisible—it has no internal structure. Consider the problem of finding a driving route from one end of a country to the other via some sequence of cities (we address this problem in [Figure 3.2](#index_split_010.html#filepos318111) [on page 68](#index_split_010.html#filepos318104)). For the purposes of solving this problem, it may suffice to reduce the state of world to just the name of the city we are in—a single atom of knowledge; a “black box” whose only discernible property is that of being identical to or different from another black box. The algorithms underlying **search** and **gameplaying** ([Chapters 3](#index_split_000.html#filepos301685)–[5](#index_split_000.html#filepos660071)), **Hidden Markov models** ([Chapter 15](#index_split_015.html#filepos2253296)), and **Markov decision processes** ([Chapter 17](#index_split_015.html#filepos2562268)) all work with atomic representations—or, at least, they treat representations *as if* they were atomic.

* * *

ATOMIC REPRESENTATION

* * *

Now consider a higher-fidelity description for the same problem, where we need to be concerned with more than just atomic location in one city or another; we might need to pay attention to how much gas is in the tank, our current GPS coordinates, whether or not the oil warning light is working, how much spare change we have for toll crossings, what station is on the radio, and so on. A **factored representation** splits up each state into a fixed set of **variables** or **attributes**, each of which can have a **value**. While two different atomic states have nothing in common—they are just different black boxes—two different factored states can share some attributes (such as being at some particular GPS location) and not others (such as having lots of gas or having no gas); this makes it much easier to work out how to turn one state into another. With factored representations, we can also represent *uncertainty*—for example, ignorance about the amount of gas in the tank can be represented by leaving that attribute blank. Many important areas of AI are based on factored representations, including **constraint satisfaction** algorithms ([Chapter 6](#index_split_000.html#filepos813005)), **propositional logic** ([Chapter 7](#index_split_000.html#filepos939379)), **planning**([Chapters 10](#index_split_015.html#filepos1477055) and [11](#index_split_015.html#filepos1612250)), **Bayesian networks** ([Chapters 13](#index_split_015.html#filepos1915714)–[16](#index_split_015.html#filepos2423989)), and the **machine learning** algorithms in [Chapters 18](#index_split_015.html#filepos2753020), [20](#index_split_015.html#filepos3158034), and [21](#index_split_015.html#filepos3262268).

* * *

FACTORED REPRESENTATION

* * *

* * *

VARIABLE

* * *

* * *

ATTRIBUTE

* * *

* * *

VALUE

* * *

For many purposes, we need to understand the world as having *things* in it that are *related* to each other, not just variables with values. For example, we might notice that a large truck ahead of us is reversing into the driveway of a dairy farm but a cow has got loose and is blocking the truck’s path. A factored representation is unlikely to be pre-equipped with the attribute *TruckAheadBackingIntoDairyFarmDrivewayBlockedByLooseCow* with value *true* or *false*. Instead, we would need a **structured representation**, in which objects such as cows and trucks and their various and varying relationships can be described explicitly. (See [Figure 2.16](#index_split_009.html#filepos273210)(c).) Structured representations underlie **relational databases** and **first-order logic** ([Chapters 8](#index_split_000.html#filepos1149778), [9](#index_split_015.html#filepos1300686), and [12](#index_split_015.html#filepos1750417)), **first-order probability models** ([Chapter 14](#index_split_015.html#filepos2036437)), **knowledge-based learning** ([Chapter 19](#index_split_015.html#filepos3033423)) and much of **natural language understanding**([Chapters 22](#index_split_015.html#filepos3374172) and [23](#index_split_015.html#filepos3484309)). In fact, almost everything that humans express in natural language concerns objects and their relationships.

* * *

STRUCTURED REPRESENTATION

* * *

As we mentioned earlier, the axis along which atomic, factored, and structured representations lie is the axis of increasing **expressiveness**. Roughly speaking, a more expressive representation can capture, at least as concisely, everything a less expressive one can capture, plus some more. Often, the more expressive language is *much* more concise; for example, the rules of chess can be written in a page or two of a structured-representation language such as first-order logic but require thousands of pages when written in a factored-representation language such as propositional logic. On the other hand, reasoning and learning become more complex as the expressive power of the representation increases. To gain the benefits of expressive representations while avoiding their drawbacks, intelligent systems for the real world may need to operate at all points along the axis simultaneously.

* * *

EXPRESSIVENESS

* * *

### 2.5 SUMMARY

This chapter has been something of a whirlwind tour of AI, which we have conceived of as the science of agent design. The major points to recall are as follows:

> • An **agent** is something that perceives and acts in an environment. The **agent function** for an agent specifies the action taken by the agent in response to any percept sequence.

> • The **performance measure** evaluates the behavior of the agent in an environment. A **rational agent** acts so as to maximize the expected value of the performance measure, given the percept sequence it has seen so far.

> • A **task environment** specification includes the performance measure, the external environment, the actuators, and the sensors. In designing an agent, the first step must always be to specify the task environment as fully as possible.

> • Task environments vary along several significant dimensions. They can be fully or partially observable, single-agent or multiagent, deterministic or stochastic, episodic or sequential, static or dynamic, discrete or continuous, and known or unknown.

> • The **agent program** implements the agent function. There exists a variety of basic agent-program designs reflecting the kind of information made explicit and used in the decision process. The designs vary in efficiency, compactness, and flexibility. The appropriate design of the agent program depends on the nature of the environment.

> • **Simple reflex agents** respond directly to percepts, whereas **model-based reflex agents** maintain internal state to track aspects of the world that are not evident in the current percept. **Goal-based agents** act to achieve their goals, and **utility-based agents** try to maximize their own expected “happiness.”

> • All agents can improve their performance through **learning**.

### BIBLIOGRAPHICAL AND HISTORICAL NOTES

The central role of action in intelligence—the notion of practical reasoning—goes back at least as far as Aristotle’s *Nicomachean Ethics*. Practical reasoning was also the subject of McCarthy’s (1958) influential paper “Programs with Common Sense.” The fields of robotics and control theory are, by their very nature, concerned principally with physical agents. The concept of a **controller** in control theory is identical to that of an agent in AI. Perhaps surprisingly, AI has concentrated for most of its history on isolated components of agents—question-answering systems, theorem-provers, vision systems, and so on—rather than on whole agents. The discussion of agents in the text by Genesereth and Nilsson (1987) was an influential exception. The whole-agent view is now widely accepted and is a central theme in recent texts (Poole **et al.**, 1998; Nilsson, 1998; Padgham and Winikoff, 2004; Jones, 2007).

* * *

CONTROLLER

* * *

[Chapter 1](#index_split_000.html#filepos57382) traced the roots of the concept of rationality in philosophy and economics. In AI, the concept was of peripheral interest until the mid-1980s, when it began to suffuse many discussions about the proper technical foundations of the field. A paper by Jon Doyle (1983) predicted that rational agent design would come to be seen as the core mission of AI, while other popular topics would spin off to form new disciplines.

Careful attention to the properties of the environment and their consequences for rational agent design is most apparent in the control theory tradition—for example, classical control systems (Dorf and Bishop, 2004; Kirk, 2004) handle fully observable, deterministic environments; stochastic optimal control (Kumar and Varaiya, 1986; Bertsekas and Shreve, 2007) handles partially observable, stochastic environments; and hybrid control (Henzinger and Sastry, 1998; Cassandras and Lygeros, 2006) deals with environments containing both discrete and continuous elements. The distinction between fully and partially observable environments is also central in the **dynamic programming** literature developed in the field of operations research (Puterman, 1994), which we discuss in [Chapter 17](#index_split_015.html#filepos2562268).

Reflex agents were the primary model for psychological behaviorists such as Skinner (1953), who attempted to reduce the psychology of organisms strictly to input/output or stimulus/response mappings. The advance from behaviorism to functionalism in psychology, which was at least partly driven by the application of the computer metaphor to agents (Putnam, 1960; Lewis, 1966), introduced the internal state of the agent into the picture. Most work in AI views the idea of pure reflex agents with state as too simple to provide much leverage, but work by Rosenschein (1985) and Brooks (1986) questioned this assumption (see [Chapter 25](#index_split_015.html#filepos3777962)). In recent years, a great deal of work has gone into finding efficient algorithms for keeping track of complex environments (Hamscher **et al.**, 1992; Simon, 2006). The Remote Agent program (described [on page 28](#index_split_008.html#filepos166159)) that controlled the Deep Space One spacecraft is a particularly impressive example (Muscettola **et al.**, 1998; Jonsson **et al.**, 2000).

Goal-based agents are presupposed in everything from Aristotle’s view of practical reasoning to McCarthy’s early papers on logical AI. Shakey the Robot (Fikes and Nilsson, 1971; Nilsson, 1984) was the first robotic embodiment of a logical, goal-based agent. A full logical analysis of goal-based agents appeared in Genesereth and Nilsson (1987), and a goal-based programming methodology called agent-oriented programming was developed by Shoham (1993). The agent-based approach is now extremely popular in software engineering (Ciancarini and Wooldridge, 2001). It has also infiltrated the area of operating systems, where **autonomic computing** refers to computer systems and networks that monitor and control themselves with a perceive–act loop and machine learning methods (Kephart and Chess, 2003). Noting that a collection of agent programs designed to work well together in a true multiagent environment necessarily exhibits modularity—the programs share no internal state and communicate with each other only through the environment—it is common within the field of **multiagent systems** to design the agent program of a single agent as a collection of autonomous sub-agents. In some cases, one can even prove that the resulting system gives the same optimal solutions as a monolithic design.

* * *

AUTONOMIC COMPUTING

* * *

* * *

MULTIAGENT SYSTEMS

* * *

The goal-based view of agents also dominates the cognitive psychology tradition in the area of problem solving, beginning with the enormously influential *Human Problem Solving* (Newell and Simon, 1972) and running through all of Newell’s later work (Newell, 1990). Goals, further analyzed as *desires* (general) and *intentions* (currently pursued), are central to the theory of agents developed by Bratman (1987). This theory has been influential both in natural language understanding and multiagent systems.

Horvitz **et al.** (1988) specifically suggest the use of rationality conceived as the maximization of expected utility as a basis for AI. The text by Pearl (1988) was the first in AI to cover probability and utility theory in depth; its exposition of practical methods for reasoning and decision making under uncertainty was probably the single biggest factor in the rapid shift towards utility-based agents in the 1990s (see Part IV).

The general design for learning agents portrayed in [Figure 2.15](#index_split_009.html#filepos264745) is classic in the machine learning literature (Buchanan **et al.**, 1978; Mitchell, 1997). Examples of the design, as embodied in programs, go back at least as far as Arthur Samuel’s (1959, 1967) learning program for playing checkers. Learning agents are discussed in depth in Part V.

Interest in agents and in agent design has risen rapidly in recent years, partly because of the growth of the Internet and the perceived need for automated and mobile **softbot** (Etzioni and Weld, 1994). Relevant papers are collected in *Readings in Agents* (Huhns and Singh, 1998) and *Foundations of Rational Agency* (Wooldridge and Rao, 1999). Texts on multiagent systems usually provide a good introduction to many aspects of agent design (Weiss, 2000a; Wooldridge, 2002). Several conference series devoted to agents began in the 1990s, including the International Workshop on Agent Theories, Architectures, and Languages (ATAL), the International Conference on Autonomous Agents (AGENTS), and the International Conference on MultiAgent Systems (ICMAS). In 2002, these three merged to form the International Joint Conference on Autonomous Agents and MultiAgent Systems (AAMAS). The journal *Autonomous Agents and MultiAgent Systems* was founded in 1998. Finally, *Dung Beetle Ecology* (Hanski and Cambefort, 1991) provides a wealth of interesting information on the behavior of dung beetles. YouTube features inspiring video recordings of their activities.

### EXERCISES

**2.1** Suppose that the performance measure is concerned with just the first T time steps of the environment and ignores everything thereafter. Show that a rational agent’s action may depend not just on the state of the environment but also on the time step it has reached.

**2.2** Let us examine the rationality of various vacuum-cleaner agent functions.

> **a**. Show that the simple vacuum-cleaner agent function described in [Figure 2.3](#index_split_009.html#filepos194730) is indeed rational under the assumptions listed [on page 38](#index_split_009.html#filepos201200).

> **b**. Describe a rational agent function for the case in which each movement costs one point. Does the corresponding agent program require internal state?

> **c**. Discuss possible agent designs for the cases in which clean squares can become dirty and the geography of the environment is unknown. Does it make sense for the agent to learn from its experience in these cases? If so, what should it learn? If not, why not?

**2.3** For each of the following assertions, say whether it is true or false and support your answer with examples or counterexamples where appropriate.

> **a**. An agent that senses only partial information about the state cannot be perfectly rational.

> **b**. There exist task environments in which no pure reflex agent can behave rationally.

> **c**. There exists a task environment in which every agent is rational.

> **d**. The input to an agent program is the same as the input to the agent function.

> **e**. Every agent function is implementable by some program/machine combination.

> **f**. Suppose an agent selects its action uniformly at random from the set of possible actions. There exists a deterministic task environment in which this agent is rational.

> **g**. It is possible for a given agent to be perfectly rational in two distinct task environments.

> **h**. Every agent is rational in an unobservable environment.

> **i**. A perfectly rational poker-playing agent never loses.

**2.4** For each of the following activities, give a PEAS description of the task environment and characterize it in terms of the properties listed in [Section 2.3.2](#index_split_000.html#filepos217402).

> • Playing soccer.

> • Exploring the subsurface oceans of Titan.

> • Shopping for used AI books on the Internet.

> • Playing a tennis match.

> • Practicing tennis against a wall.

> • Performing a high jump.

> • Knitting a sweater.

> • Bidding on an item at an auction.

**2.5** Define in your own words the following terms: agent, agent function, agent program, rationality, autonomy, reflex agent, model-based agent, goal-based agent, utility-based agent, learning agent.

**2.6** This exercise explores the differences between agent functions and agent programs.

> **a**. Can there be more than one agent program that implements a given agent function? Give an example, or show why one is not possible.

> **b**. Are there agent functions that cannot be implemented by any agent program?

> **c**. Given a fixed machine architecture, does each agent program implement exactly one agent function?

> **d**. Given an architecture with *n* bits of storage, how many different possible agent programs are there?

> **e**. Suppose we keep the agent program fixed but speed up the machine by a factor of two. Does that change the agent function?

**2.7** Write pseudocode agent programs for the goal-based and utility-based agents.

![radio](images/00004.jpg)

The following exercises all concern the implementation of environments and agents for the vacuum-cleaner world.

**2.8** Implement a performance-measuring environment simulator for the vacuum-cleaner world depicted in [Figure 2.2](#index_split_009.html#filepos194440) and specified [on page 38](#index_split_009.html#filepos201200). Your implementation should be modular so that the sensors, actuators, and environment characteristics (size, shape, dirt placement, etc.) can be changed easily. (*Note:* for some choices of programming language and operating system there are already implementations in the online code repository.)

**2.9** Implement a simple reflex agent for the vacuum environment in Exercise 2.8. Run the environment with this agent for all possible initial dirt configurations and agent locations. Record the performance score for each configuration and the overall average score.

**2.10** Consider a modified version of the vacuum environment in Exercise 2.8, in which the agent is penalized one point for each movement.

> **a**. Can a simple reflex agent be perfectly rational for this environment? Explain.

> **b**. What about a reflex agent with state? Design such an agent.

> **c**. How do your answers to **a** and **b** change if the agent’s percepts give it the clean/dirty status of every square in the environment?

**2.11** Consider a modified version of the vacuum environment in Exercise 2.8, in which the geography of the environment—its extent, boundaries, and obstacles—is unknown, as is the initial dirt configuration. (The agent can go Up and Down as well as Left and Right.)

> **a**. Can a simple reflex agent be perfectly rational for this environment? Explain.

> **b**. Can a simple reflex agent with a *randomized* agent function outperform a simple reflex agent? Design such an agent and measure its performance on several environments.

> **c**. Can you design an environment in which your randomized agent will perform poorly? Show your results.

> **d**. Can a reflex agent with state outperform a simple reflex agent? Design such an agent and measure its performance on several environments. Can you design a rational agent of this type?

**2.12** Repeat Exercise 2.11 for the case in which the location sensor is replaced with a “bump” sensor that detects the agent’s attempts to move into an obstacle or to cross the boundaries of the environment. Suppose the bump sensor stops working; how should the agent behave?

**2.13** The vacuum environments in the preceding exercises have all been deterministic. Discuss possible agent programs for each of the following stochastic versions:

> **a**. Murphy’s law: twenty-five percent of the time, the Suck action fails to clean the floor if it is dirty and deposits dirt onto the floor if the floor is clean. How is your agent program affected if the dirt sensor gives the wrong answer 10% of the time?

> **b**. Small children: At each time step, each clean square has a 10% chance of becoming dirty. Can you come up with a rational agent design for this case?

## **3 SOLVING PROBLEMS BY SEARCHING**

> *In which we see how an agent can find a sequence of actions that achieves its goals when no single action will do.*

The simplest agents discussed in [Chapter 2](#index_split_000.html#filepos187684) were the reflex agents, which base their actions on a direct mapping from states to actions. Such agents cannot operate well in environments for which this mapping would be too large to store and would take too long to learn. Goal-based agents, on the other hand, consider future actions and the desirability of their outcomes.

This chapter describes one kind of goal-based agent called a **problem-solving agent**. Problem-solving agents use **atomic** representations, as described in [Section 2.4.7](#index_split_000.html#filepos271690)—that is, states of the world are considered as wholes, with no internal structure visible to the problem-solving algorithms. Goal-based agents that use more advanced **factored** or **structured** representations are usually called **planning agents** and are discussed in [Chapters 7](#index_split_000.html#filepos939379) and [10](#index_split_015.html#filepos1477055).

* * *

PROBLEM-SOLVING AGENT

* * *

Our discussion of problem solving begins with precise definitions of **problems** and their **solutions** and give several examples to illustrate these definitions. We then describe several general-purpose search algorithms that can be used to solve these problems. We will see several **uninformed** search algorithms—algorithms that are given no information about the problem other than its definition. Although some of these algorithms can solve any solvable problem, none of them can do so efficiently. **Informed** search algorithms, on the other hand, can do quite well given some guidance on where to look for solutions.

In this chapter, we limit ourselves to the simplest kind of task environment, for which the solution to a problem is always a *fixed sequence* of actions. The more general case—where the agent’s future actions may vary depending on future percepts—is handled in [Chapter 4](#index_split_000.html#filepos513290).

This chapter uses the concepts of asymptotic complexity (that is, *O*() notation) and NP-completeness. Readers unfamiliar with these concepts should consult Appendix A.

### 3.1 PROBLEM\-SOLVING AGENTS

Intelligent agents are supposed to maximize their performance measure. As we mentioned in [Chapter 2](#index_split_000.html#filepos187684), achieving this is sometimes simplified if the agent can adopt a **goal** and aim at satisfying it. Let us first look at why and how an agent might do this.

Imagine an agent in the city of Arad, Romania, enjoying a touring holiday. The agent’s performance measure contains many factors: it wants to improve its suntan, improve its Romanian, take in the sights, enjoy the nightlife (such as it is), avoid hangovers, and so on. The decision problem is a complex one involving many tradeoffs and careful reading of guidebooks. Now, suppose the agent has a nonrefundable ticket to fly out of Bucharest the following day. In that case, it makes sense for the agent to adopt the **goal** of getting to Bucharest. Courses of action that don’t reach Bucharest on time can be rejected without further consideration and the agent’s decision problem is greatly simplified. Goals help organize behavior by limiting the objectives that the agent is trying to achieve and hence the actions it needs to consider. **Goal formulation**, based on the current situation and the agent’s performance measure, is the first step in problem solving.

* * *

GOAL FORMULATION

* * *

We will consider a goal to be a set of world states—exactly those states in which the goal is satisfied. The agent’s task is to find out how to act, now and in the future, so that it reaches a goal state. Before it can do this, it needs to decide (or we need to decide on its behalf) what sorts of actions and states it should consider. If it were to consider actions at the level of “move the left foot forward an inch” or “turn the steering wheel one degree left,”the agent would probably never find its way out of the parking lot, let alone to Bucharest, because at that level of detail there is too much uncertainty in the world and there would be too many steps in a solution. **Problem formulation** is the process of deciding what actions and states to consider, given a goal. We discuss this process in more detail later. For now, let us assume that the agent will consider actions at the level of driving from one major town to another. Each state therefore corresponds to being in a particular town.

* * *

PROBLEM FORMULATION

* * *

Our agent has now adopted the goal of driving to Bucharest and is considering where to go from Arad. Three roads lead out of Arad, one toward Sibiu, one to Timisoara, and one to Zerind. None of these achieves the goal, so unless the agent is familiar with the geography of Romania, it will not know which road to follow.[¹](#index_split_015.html#filepos5569915) In other words, the agent will not know which of its possible actions is best, because it does not yet know enough about the state that results from taking each action. If the agent has no additional information—i.e., if the environment is **unknown** in the sense defined in [Section 2.3](#index_split_000.html#filepos209973)—then it is has no choice but to try one of the actions at random. This sad situation is discussed in [Chapter 4](#index_split_000.html#filepos513290).

But suppose the agent has a map of Romania. The point of a map is to provide the agent with information about the states it might get itself into and the actions it can take. The agent can use this information to consider *subsequent* stages of a hypothetical journey via each of the three towns, trying to find a journey that eventually gets to Bucharest. Once it has found a path on the map from Arad to Bucharest, it can achieve its goal by carrying out the driving actions that correspond to the legs of the journey. In general, *an agent with several immediate options of unknown value can decide what to do by first examining* future *actions that eventually lead to states of known value.*

![hand](images/00006.jpg)

To be more specific about what we mean by “examining future actions,” we have to be more specific about properties of the environment, as defined in [Section 2.3](#index_split_000.html#filepos209973). For now, we assume that the environment is **observable**, so the agent always knows the current state. For the agent driving in Romania, it’s reasonable to suppose that each city on the map has a sign indicating its presence to arriving drivers. We also assume the environment is **discrete**, so at any given state there are only finitely many actions to choose from. This is true for navigating in Romania because each city is connected to a small number of other cities. We will assume the environment is **known**, so the agent knows which states are reached by each action. (Having an accurate map suffices to meet this condition for navigation problems.) Finally, we assume that the environment is **deterministic**, so each action has exactly one outcome. Under ideal conditions, this is true for the agent in Romania—it means that if it chooses to drive from Arad to Sibiu, it does end up in Sibiu. Of course, conditions are not always ideal, as we show in [Chapter 4](#index_split_000.html#filepos513290).

*Under these assumptions, the solution to any problem is a fixed sequence of actions.* “Of course!” one might say, “What else could it be?” Well, in general it could be a branching strategy that recommends different actions in the future depending on what percepts arrive. For example, under less than ideal conditions, the agent might plan to drive from Arad to Sibiu and then to Rimnicu Vilcea but may also need to have a contingency plan in case it arrives by accident in Zerind instead of Sibiu. Fortunately, if the agent knows the initial state and the environment is known and deterministic, it knows exactly where it will be after the first action and what it will perceive. Since only one percept is possible after the first action, the solution can specify only one possible second action, and so on.

![hand](images/00006.jpg)

The process of looking for a sequence of actions that reaches the goal is called **search**. A search algorithm takes a problem as input and returns a **solution** in the form of an action sequence. Once a solution is found, the actions it recommends can be carried out. This is called the **execution** phase. Thus, we have a simple “formulate, search, execute” design for the agent, as shown in [Figure 3.1](#index_split_010.html#filepos314502). After formulating a goal and a problem to solve, the agent calls a search procedure to solve it. It then uses the solution to guide its actions, doing whatever the solution recommends as the next thing to do—typically, the first action of the sequence—and then removing that step from the sequence. Once the solution has been executed, the agent will formulate a new goal.

* * *

SEARCH

* * *

* * *

SOLUTION

* * *

* * *

EXECUTION

* * *

Notice that while the agent is executing the solution sequence it *ignores its percepts* when choosing an action because it knows in advance what they will be. An agent that carries out its plans with its eyes closed, so to speak, must be quite certain of what is going on. Control theorists call this an **open-loop** system, because ignoring the percepts breaks the loop between agent and environment.

* * *

OPEN-LOOP

* * *

We first describe the process of problem formulation, and then devote the bulk of the chapter to various algorithms for the SEARCH function. We do not discuss the workings of the UPDATE\-STATE and FORMULATE\-GOAL functions further in this chapter.

#### **3.1.1 Well-defined problems and solutions**

A **problem** can be defined formally by five components:

* * *

PROBLEM

* * *

> • The **initial state** that the agent starts in. For example, the initial state for our agent in Romania might be described as *In*(*Arad*).

* * *

INITIAL STATE

* * *

> ![image](images/00028.jpg)

> **Figure 3.1** A simple problem-solving agent. It first formulates a goal and a problem, searches for a sequence of actions that would solve the problem, and then executes the actions one at a time. When this is complete, it formulates another goal and starts over.

> • A description of the possible **actions** available to the agent. Given a particular state *s*, ACTIONS(*s*) returns the set of actions that can be executed in *s*. We say that each of these actions is **applicable** in s. For example, from the state *In*(*Arad*), the applicable actions are {*Go*(*Sibiu*), *Go*(*Timisoara*), *Go*(*Zerind*)}.

* * *

ACTIONS

* * *

* * *

APPLICABLE

* * *

> • A description of what each action does; the formal name for this is the **transition model**, specified by a function RESULT(*s*, *a*) that returns the state that results from doing action *a* in state *s*. We also use the term **successor** to refer to any state reachable from a given state by a single action.[²](#index_split_015.html#filepos5570241) For example, we have

* * *

TRANSITION MODEL

* * *

* * *

SUCCESSOR

* * *

> RESULT(*In*(*Arad*), *Go*(*Zerind*)) = *In*(*Zerind*).

> Together, the initial state, actions, and transition model implicitly define the **state space** of the problem—the set of all states reachable from the initial state by any sequence of actions. The state space forms a directed network or **graph** in which the nodes are states and the links between nodes are actions. (The map of Romania shown in [Figure 3.2](#index_split_010.html#filepos318111) can be interpreted as a state-space graph if we view each road as standing for two driving actions, one in each direction.) A **path** in the state space is a sequence of states connected by a sequence of actions.

* * *

STATE SPACE

* * *

* * *

GRAPH

* * *

* * *

PATH

* * *

> • The **goal test**, which determines whether a given state is a goal state. Sometimes there is an explicit set of possible goal states, and the test simply checks whether the given state is one of them. The agent’s goal in Romania is the singleton set {*In*(*Bucharest*)}.

* * *

GOAL TEST

* * *

> ![image](images/00029.jpg)

> **Figure 3.2** A simplified road map of part of Romania.

Sometimes the goal is specified by an abstract property rather than an explicitly enumerated set of states. For example, in chess, the goal is to reach a state called “checkmate,”where the opponent’s king is under attack and can’t escape.

> • A **path cost** function that assigns a numeric cost to each path. The problem-solving agent chooses a cost function that reflects its own performance measure. For the agent trying to get to Bucharest, time is of the essence, so the cost of a path might be its length in kilometers. In this chapter, we assume that the cost of a path can be described as the *sum* of the costs of the individual actions along the path.[³](#index_split_015.html#filepos5570910) The **step cost** of taking action *a* in state *s* to reach state *s*′ is denoted by *c*(*s*, *a*, *s*′). The step costs for Romania are shown in [Figure 3.2](#index_split_010.html#filepos318111) as route distances. We assume that step costs are nonnegative.[⁴](#index_split_015.html#filepos5571186)

* * *

PATH COST

* * *

* * *

STEP COST

* * *

The preceding elements define a problem and can be gathered into a single data structure that is given as input to a problem-solving algorithm. A **solution** to a problem is an action sequence that leads from the initial state to a goal state. Solution quality is measured by the path cost function, and an **optimal solution** has the lowest path cost among all solutions.

* * *

OPTIMAL SOLUTION

* * *

#### **3.1.2 Formulating problems**

In the preceding section we proposed a formulation of the problem of getting to Bucharest in terms of the initial state, actions, transition model, goal test, and path cost. This formulation seems reasonable, but it is still a *model*—an abstract mathematical description—and not the real thing. Compare the simple state description we have chosen, *In(Arad)*, to an actual cross-country trip, where the state of the world includes so many things: the traveling companions, the current radio program, the scenery out of the window, the proximity of law enforcement officers, the distance to the next rest stop, the condition of the road, the weather, and so on. All these considerations are left out of our state descriptions because they are irrelevant to the problem of finding a route to Bucharest. The process of removing detail from a representation is called **abstraction**.

* * *

ABSTRACTION

* * *

In addition to abstracting the state description, we must abstract the actions themselves. A driving action has many effects. Besides changing the location of the vehicle and its occupants, it takes up time, consumes fuel, generates pollution, and changes the agent (as they say, travel is broadening). Our formulation takes into account only the change in location. Also, there are many actions that we omit altogether: turning on the radio, looking out of the window, slowing down for law enforcement officers, and so on. And of course, we don’t specify actions at the level of “turn steering wheel to the left by one degree.”

Can we be more precise about defining the appropriate level of abstraction? Think of the abstract states and actions we have chosen as corresponding to large sets of detailed world states and detailed action sequences. Now consider a solution to the abstract problem: for example, the path from Arad to Sibiu to Rimnicu Vilcea to Pitesti to Bucharest. This abstract solution corresponds to a large number of more detailed paths. For example, we could drive with the radio on between Sibiu and Rimnicu Vilcea, and then switch it off for the rest of the trip. The abstraction is *valid* if we can expand any abstract solution into a solution in the more detailed world; a sufficient condition is that for every detailed state that is “in Arad,”there is a detailed path to some state that is “in Sibiu,” and so on.[⁵](#index_split_015.html#filepos5571358) The abstraction is *useful* if carrying out each of the actions in the solution is easier than the original problem; in this case they are easy enough that they can be carried out without further search or planning by an average driving agent. The choice of a good abstraction thus involves removing as much detail as possible while retaining validity and ensuring that the abstract actions are easy to carry out. Were it not for the ability to construct useful abstractions, intelligent agents would be completely swamped by the real world.

### 3.2 EXAMPLE PROBLEMS

The problem-solving approach has been applied to a vast array of task environments. We list some of the best known here, distinguishing between *toy* and *real-world* problems. A **toy problem** is intended to illustrate or exercise various problem-solving methods. It can be given a concise, exact description and hence is usable by different researchers to compare the performance of algorithms. A **real-world problem** is one whose solutions people actually care about. Such problems tend not to have a single agreed-upon description, but we can give the general flavor of their formulations.

* * *

TOY PROBLEM

* * *

* * *

REAL-WORLD PROBLEM

* * *

> ![image](images/00030.jpg)

> **Figure 3.3** The state space for the vacuum world. Links denote actions: L = *Left*, R = *Right*, S = *Suck*.

#### **3.2.1 Toy problems**

The first example we examine is the **vacuum world** first introduced in [Chapter 2](#index_split_000.html#filepos187684). (See [Figure 2.2](#index_split_009.html#filepos194440).) This can be formulated as a problem as follows:

> • **States**: The state is determined by both the agent location and the dirt locations. The agent is in one of two locations, each of which might or might not contain dirt. Thus, there are 2 × 2² = 8 possible world states. A larger environment with *n* locations has *n* ⋅ 2^(*n*) states.

> • **Initial state**: Any state can be designated as the initial state.

> • **Actions**: In this simple environment, each state has just three actions: *Left*, *Right*, and *Suck*. Larger environments might also include *Up* and *Down*.

> • **Transition model**: The actions have their expected effects, except that moving *Left* in the leftmost square, moving *Right* in the rightmost square, and *Suck*ing in a clean square have no effect. The complete state space is shown in [Figure 3.3](#index_split_010.html#filepos324794).

> • **Goal test**: This checks whether all the squares are clean.

> • **Path cost**: Each step costs 1, so the path cost is the number of steps in the path.

Compared with the real world, this toy problem has discrete locations, discrete dirt, reliable cleaning, and it never gets any dirtier. [Chapter 4](#index_split_000.html#filepos513290) relaxes some of these assumptions.

The **8-puzzle**, an instance of which is shown in [Figure 3.4](#index_split_010.html#filepos327993), consists of a 3×3 board with eight numbered tiles and a blank space. A tile adjacent to the blank space can slide into the space. The object is to reach a specified goal state, such as the one shown on the right of the figure. The standard formulation is as follows:

* * *

8-PUZZLE

* * *

> ![image](images/00031.jpg)

> **Figure 3.4** A typical instance of the 8-puzzle.

> • **States**: A state description specifies the location of each of the eight tiles and the blank in one of the nine squares.

> • **Initial state**: Any state can be designated as the initial state. Note that any given goal can be reached from exactly half of the possible initial states (Exercise 3.4).

> • **Actions**: The simplest formulation defines the actions as movements of the blank space *Left*, *Right*, *Up*, or *Down*. Different subsets of these are possible depending on where the blank is.

> • **Transition model**: Given a state and action, this returns the resulting state; for example, if we apply *Left* to the start state in [Figure 3.4](#index_split_010.html#filepos327993), the resulting state has the 5 and the blank switched.

> • **Goal test**: This checks whether the state matches the goal configuration shown in [Figure 3.4](#index_split_010.html#filepos327993). (Other goal configurations are possible.)

> • **Path cost**: Each step costs 1, so the path cost is the number of steps in the path.

What abstractions have we included here? The actions are abstracted to their beginning and final states, ignoring the intermediate locations where the block is sliding. We have abstracted away actions such as shaking the board when pieces get stuck and ruled out extracting the pieces with a knife and putting them back again. We are left with a description of the rules of the puzzle, avoiding all the details of physical manipulations.

The 8-puzzle belongs to the family of **sliding-block puzzles**, which are often used as test problems for new search algorithms in AI. This family is known to be NP-complete, so one does not expect to find methods significantly better in the worst case than the search algorithms described in this chapter and the next. The 8-puzzle has 9!/2 = 181, 440 reachable states and is easily solved. The 15-puzzle (on a 4 × 4 board) has around 1.3 trillion states, and random instances can be solved optimally in a few milliseconds by the best search algorithms. The 24-puzzle (on a 5 × 5 board) has around 10^(25) states, and random instances take several hours to solve optimally.

* * *

SLIDING-BLOCK PUZZLES

* * *

The goal of the **8-queens problem** is to place eight queens on a chessboard such that no queen attacks any other. (A queen attacks any piece in the same row, column or diagonal.) [Figure 3.5](#index_split_010.html#filepos331770) shows an attempted solution that fails: the queen in the rightmost column is attacked by the queen at the top left.

* * *

8-QUEENS PROBLEM

* * *

> ![image](images/00032.jpg)

> **Figure 3.5** Almost a solution to the 8-queens problem. (Solution is left as an exercise.)

Although efficient special-purpose algorithms exist for this problem and for the whole *n*\-queens family, it remains a useful test problem for search algorithms. There are two main kinds of formulation. An **incremental formulation** involves operators that *augment* the state description, starting with an empty state; for the 8-queens problem, this means that each action adds a queen to the state. A **complete-state formulation** starts with all 8 queens on the board and moves them around. In either case, the path cost is of no interest because only the final state counts. The first incremental formulation one might try is the following:

* * *

INCREMENTAL FORMULATION

* * *

* * *

COMPLETE-STATE FORMULATION

* * *

> • **States**: Any arrangement of 0 to 8 queens on the board is a state.

> • **Initial state**: No queens on the board.

> • **Actions**: Add a queen to any empty square.

> • **Transition model**: Returns the board with a queen added to the specified square.

> • **Goal test**: 8 queens are on the board, none attacked.

In this formulation, we have 64 ⋅ 63 … 57 ≈ 1.8 × 10^(14) possible sequences to investigate. A better formulation would prohibit placing a queen in any square that is already attacked:

> • **States**: All possible arrangements of *n* queens (0 ≤ *n* ≤ 8), one per column in the leftmost *n* columns, with no queen attacking another.

> • **Actions**: Add a queen to any square in the leftmost empty column such that it is not attacked by any other queen.

This formulation reduces the 8-queens state space from 1.8 × 10^(14) to just 2,057, and solutions are easy to find. On the other hand, for 100 queens the reduction is from roughly 10^(400) states to about 10^(52) states (Exercise 3.5)—a big improvement, but not enough to make the problem tractable. [Section 4.1](#index_split_000.html#filepos515228) describes the complete-state formulation, and [Chapter 6](#index_split_000.html#filepos813005) gives a simple algorithm that solves even the million-queens problem with ease.

Our final toy problem was devised by Donald Knuth (1964) and illustrates how infinite state spaces can arise. Knuth conjectured that, starting with the number 4, a sequence of factorial, square root, and floor operations will reach any desired positive integer. For example, we can reach 5 from 4 as follows:

> ![equ](images/00033.jpg)

The problem definition is very simple:

> • **States**: Positive numbers.

> • **Initial state**: 4.

> • **Actions**: Apply factorial, square root, or floor operation (factorial for integers only).

> • **Transition model**: As given by the mathematical definitions of the operations.

> • **Goal test**: State is the desired positive integer.

To our knowledge there is no bound on how large a number might be constructed in the process of reaching a given target—for example, the number 620,448,401,733,239,439,360,000 is generated in the expression for 5—so the state space for this problem is infinite. Such state spaces arise frequently in tasks involving the generation of mathematical expressions, circuits, proofs, programs, and other recursively defined objects.

#### **3.2.2 Real-world problems**

We have already seen how the **route-finding problem** is defined in terms of specified locations and transitions along links between them. Route-finding algorithms are used in a variety of applications. Some, such as Web sites and in-car systems that provide driving directions, are relatively straightforward extensions of the Romania example. Others, such as routing video streams in computer networks, military operations planning, and airline travel-planning systems, involve much more complex specifications. Consider the airline travel problems that must be solved by a travel-planning Web site:

* * *

ROUTE-FINDING PROBLEM

* * *

> • **States**: Each state obviously includes a location (e.g., an airport) and the current time. Furthermore, because the cost of an action (*a* flight segment) may depend on previous segments, their fare bases, and their status as domestic or international, the state must record extra information about these “historical” aspects.

> • **Initial state**: This is specified by the user’s query.

> • **Actions**: Take any flight from the current location, in any seat class, leaving after the current time, leaving enough time for within-airport transfer if needed.

> • **Transition model**: The state resulting from taking a flight will have the flight’s destination as the current location and the flight’s arrival time as the current time.

> • **Goal test**: Are we at the final destination specified by the user?

> • **Path cost**: This depends on monetary cost, waiting time, flight time, customs and immigration procedures, seat quality, time of day, type of airplane, frequent-flyer mileage awards, and so on.

Commercial travel advice systems use a problem formulation of this kind, with many additional complications to handle the byzantine fare structures that airlines impose. Any seasoned traveler knows, however, that not all air travel goes according to plan. A really good system should include contingency plans—such as backup reservations on alternate flights—to the extent that these are justified by the cost and likelihood of failure of the original plan.

**Touring problems** are closely related to route-finding problems, but with an important difference. Consider, for example, the problem “Visit every city in [Figure 3.2](#index_split_010.html#filepos318111) at least once, starting and ending in Bucharest.” As with route finding, the actions correspond to trips between adjacent cities. The state space, however, is quite different. Each state must include not just the current location but also the *set of cities the agent has visited*. So the initial state would be *In*(*Bucharest*), *Visited*({*Bucharest*}), a typical intermediate state would be *In*(*Vaslui*), *Visited*({*Bucharest, Urziceni, Vaslui*}), and the goal test would check whether the agent is in Bucharest and all 20 cities have been visited.

* * *

TOURING PROBLEM

* * *

The **traveling salesperson problem** (TSP) is a touring problem in which each city must be visited exactly once. The aim is to find the *shortest* tour. The problem is known to be NP-hard, but an enormous amount of effort has been expended to improve the capabilities of TSP algorithms. In addition to planning trips for traveling salespersons, these algorithms have been used for tasks such as planning movements of automatic circuit-board drills and of stocking machines on shop floors.

* * *

TRAVELING SALESPERSON PROBLEM

* * *

A **VLSI layout** problem requires positioning millions of components and connections on a chip to minimize area, minimize circuit delays, minimize stray capacitances, and maximize manufacturing yield. The layout problem comes after the logical design phase and is usually split into two parts: **cell layout** and **channel routing**. In cell layout, the primitive components of the circuit are grouped into cells, each of which performs some recognized function. Each cell has a fixed footprint (size and shape) and requires a certain number of connections to each of the other cells. The aim is to place the cells on the chip so that they do not overlap and so that there is room for the connecting wires to be placed between the cells. Channel routing finds a specific route for each wire through the gaps between the cells. These search problems are extremely complex, but definitely worth solving. Later in this chapter, we present some algorithms capable of solving them.

* * *

VLSI LAYOUT

* * *

**Robot navigation** is a generalization of the route-finding problem described earlier. Rather than following a discrete set of routes, a robot can move in a continuous space with (in principle) an infinite set of possible actions and states. For a circular robot moving on a flat surface, the space is essentially two-dimensional. When the robot has arms and legs or wheels that must also be controlled, the search space becomes many-dimensional. Advanced techniques are required just to make the search space finite. We examine some of these methods in [Chapter 25](#index_split_015.html#filepos3777962). In addition to the complexity of the problem, real robots must also deal with errors in their sensor readings and motor controls.

* * *

ROBOT NAVIGATION

* * *

**Automatic assembly sequencing** of complex objects by a robot was first demonstrated by FREDDY (Michie, 1972). Progress since then has been slow but sure, to the point where the assembly of intricate objects such as electric motors is economically feasible. In assembly problems, the aim is to find an order in which to assemble the parts of some object. If the wrong order is chosen, there will be no way to add some part later in the sequence without undoing some of the work already done. Checking a step in the sequence for feasibility is a difficult geometrical search problem closely related to robot navigation. Thus, the generation of legal actions is the expensive part of assembly sequencing. Any practical algorithm must avoid exploring all but a tiny fraction of the state space. Another important assembly problem is **protein design**, in which the goal is to find a sequence of amino acids that will fold into a three-dimensional protein with the right properties to cure some disease.

* * *

AUTOMATIC ASSEMBLY SEQUENCING

* * *

* * *

PROTEIN DESIGN

* * *

### 3.3 SEARCHING FOR SOLUTIONS

Having formulated some problems, we now need to solve them. A solution is an action sequence, so search algorithms work by considering various possible action sequences. The possible action sequences starting at the initial state form a **search tree** with the initial state at the root; the branches are actions and the **nodes** correspond to states in the state space of the problem. [Figure 3.6](#index_split_010.html#filepos351692) shows the first few steps in growing the search tree for finding a route from Arad to Bucharest. The root node of the tree corresponds to the initial state, *In(Arad)*. The first step is to test whether this is a goal state. (Clearly it is not, but it is important to check so that we can solve trick problems like “starting in Arad, get to Arad.”) Then we need to consider taking various actions. We do this by **expanding** the current state; that is, applying each legal action to the current state, thereby **generating** a new set of states. In this case, we add three branches from the **parent node** *In(Arad)* leading to three new **child nodes**: *In(Sibiu), In(Timisoara),* and *In(Zerind)*. Now we must choose which of these three possibilities to consider further.

* * *

SEARCH TREE

* * *

* * *

NODE

* * *

* * *

EXPANDING

* * *

* * *

GENERATING

* * *

* * *

PARENT NODE

* * *

* * *

CHILD NODE

* * *

This is the essence of search—following up one option now and putting the others aside for later, in case the first choice does not lead to a solution. Suppose we choose Sibiu first. We check to see whether it is a goal state (it is not) and then expand it to get *In(Arad)*, *In(Fagaras)*, *In(Oradea)*, and *In(RimnicuVilcea)*. We can then choose any of these four or go back and choose Timisoara or Zerind. Each of these six nodes is a **leaf node**, that is, a node with no children in the tree. The set of all leaf nodes available for expansion at any given point is called the **frontier**. (Many authors call it the **open list**, which is both geographically less evocative and less accurate, because other data structures are better suited than a list.) In [Figure 3.6](#index_split_010.html#filepos351692), the frontier of each tree consists of those nodes with bold outlines.

* * *

LEAF NODE

* * *

* * *

FRONTIER

* * *

* * *

OPEN LIST

* * *

The process of expanding nodes on the frontier continues until either a solution is found or there are no more states to expand. The general TREE\-SEARCH algorithm is shown informally in [Figure 3.7](#index_split_010.html#filepos352194). Search algorithms all share this basic structure; they vary primarily according to how they choose which state to expand next—the so-called **search strategy**.

* * *

SEARCH STRATEGY

* * *

The eagle-eyed reader will notice one peculiar thing about the search tree shown in [Figure 3.6](#index_split_010.html#filepos351692): it includes the path from Arad to Sibiu and back to Arad again! We say that *In(Arad)* is a **repeated state** in the search tree, generated in this case by a **loopy path**. Considering such loopy paths means that the complete search tree for Romania is *infinite* because there is no limit to how often one can traverse a loop. On the other hand, the state space—the map shown in [Figure 3.2](#index_split_010.html#filepos318111)—has only 20 states. As we discuss in [Section 3.4](#index_split_000.html#filepos367450), loops can cause certain algorithms to fail, making otherwise solvable problems unsolvable. Fortunately, there is no need to consider loopy paths. We can rely on more than intuition for this: because path costs are additive and step costs are nonnegative, a loopy path to any given state is never better than the same path with the loop removed.

* * *

REPEATED STATE

* * *

* * *

LOOPY PATH

* * *

Loopy paths are a special case of the more general concept of **redundant paths**,which exist whenever there is more than one way to get from one state to another. Consider the paths Arad–Sibiu (140 km long) and Arad–Zerind–Oradea–Sibiu (297 km long). Obviously, the second path is redundant—it’s just a worse way to get to the same state. If you are concerned about reaching the goal, there’s never any reason to keep more than one path to any given state, because any goal state that is reachable by extending one path is also reachable by extending the other.

* * *

REDUNDANT PATH

* * *

In some cases, it is possible to define the problem itself so as to eliminate redundant paths. For example, if we formulate the 8-queens problem ([page 71](#index_split_010.html#filepos327986)) so that a queen can be placed in any column, then each state with *n* queens can be reached by *n*! different paths; but if we reformulate the problem so that each new queen is placed in the leftmost empty column, then each state can be reached only through one path.

> ![image](images/00034.jpg)

> **Figure 3.6** Partial search trees for finding a route from Arad to Bucharest. Nodes that have been expanded are shaded; nodes that have been generated but not yet expanded are outlined in bold; nodes that have not yet been generated are shown in faint dashed lines.

> ![image](images/00035.jpg)

> **Figure 3.7** An informal description of the general tree-search and graph-search algorithms. The parts of GRAPH\-SEARCH marked in bold italic are the additions needed to handle repeated states.

In other cases, redundant paths are unavoidable. This includes all problems where the actions are reversible, such as route-finding problems and sliding-block puzzles. Route-finding on a **rectangular grid** (like the one used later for [Figure 3.9](#index_split_010.html#filepos356410)) is a particularly important example in computer games. In such a grid, each state has four successors, so a search tree of depth *d* that includes repeated states has 4^(*d*) leaves; but there are only about 2*d*² distinct states within *d* steps of any given state. For *d* = 20, this means about a trillion nodes but only about 800 distinct states. Thus, following redundant paths can cause a tractable problem to become intractable. This is true even for algorithms that know how to avoid infinite loops.

* * *

RECTANGULAR GRID

* * *

![hand](images/00006.jpg)

As the saying goes, *algorithms that forget their history are doomed to repeat it.* The way to avoid exploring redundant paths is to remember where one has been. To do this, we augment the TREE\-SEARCH algorithm with a data structure called the **explored set** (also known as the **closed list**), which remembers every expanded node. Newly generated nodes that match previously generated nodes—ones in the explored set or the frontier—can be discarded instead of being added to the frontier. The new algorithm, called GRAPH\-SEARCH,is shown informally in [Figure 3.7](#index_split_010.html#filepos352194). The specific algorithms in this chapter draw on this general design.

* * *

EXPLORED SET

* * *

* * *

CLOSED LIST

* * *

Clearly, the search tree constructed by the GRAPH\-SEARCH algorithm contains at most one copy of each state, so we can think of it as growing a tree directly on the state-space graph, as shown in [Figure 3.8](#index_split_010.html#filepos355846). The algorithm has another nice property: the frontier **separates** the state-space graph into the explored region and the unexplored region, so that every path from the initial state to an unexplored state has to pass through a state in the frontier. (If this seems completely obvious, try Exercise 3.13 now.) This property is illustrated in [Figure 3.9](#index_split_010.html#filepos356410). As every step moves a state from the frontier into the explored region while moving some states from the unexplored region into the frontier, we see that the algorithm is *systematically* examining the states in the state space, one by one, until it finds a solution.

* * *

SEPARATOR

* * *

> ![image](images/00036.jpg)

> **Figure 3.8** A sequence of search trees generated by a graph search on the Romania problem of [Figure 3.2](#index_split_010.html#filepos318111). At each stage, we have extended each path by one step. Notice that at the third stage, the northernmost city (Oradea) has become a dead end: both of its successors are already explored via other paths.

> ![image](images/00037.jpg)

> **Figure 3.9** The separation property of GRAPH\-SEARCH, illustrated on a rectangular-grid problem. The frontier (white nodes) always separates the explored region of the state space (black nodes) from the unexplored region (gray nodes). In (a), just the root has been expanded. In (b), one leaf node has been expanded. In (c), the remaining successors of the root have been expanded in clockwise order.

#### **3.3.1 Infrastructure for search algorithms**

Search algorithms require a data structure to keep track of the search tree that is being constructed. For each node *n* of the tree, we have a structure that contains four components:

> • *n*.STATE: the state in the state space to which the node corresponds;

> • *n*.PARENT: the node in the search tree that generated this node;

> • *n*.ACTION: the action that was applied to the parent to generate the node;

> • *n*.PATH\-COST: the cost, traditionally denoted by *g*(*n*), of the path from the initial state to the node, as indicated by the parent pointers.

> ![image](images/00038.jpg)

> **Figure 3.10** Nodes are the data structures from which the search tree is constructed. Each has a parent, a state, and various bookkeeping fields. Arrows point from child to parent.

Given the components for a parent node, it is easy to see how to compute the necessary components for a child node. The function CHILD\-NODE takes a parent node and an action and returns the resulting child node:

> ![image](images/00039.jpg)

The node data structure is depicted in [Figure 3.10](#index_split_010.html#filepos358289). Notice how the PARENT pointers string the nodes together into a tree structure. These pointers also allow the solution path to be extracted when a goal node is found; we use the SOLUTION function to return the sequence of actions obtained by following parent pointers back to the root.

Up to now, we have not been very careful to distinguish between nodes and states, but in writing detailed algorithms it’s important to make that distinction. A node is a bookkeeping data structure used to represent the search tree. A state corresponds to a configuration of the world. Thus, nodes are on particular paths, as defined by PARENT pointers, whereas states are not. Furthermore, two different nodes can contain the same world state if that state is generated via two different search paths.

Now that we have nodes, we need somewhere to put them. The frontier needs to be stored in such a way that the search algorithm can easily choose the next node to expand according to its preferred strategy. The appropriate data structure for this is a **queue**. The operations on a queue are as follows:

> • EMPTY?(*queue*) returns true only if there are no more elements in the queue.

> • POP(*queue*) removes the first element of the queue and returns it.

> • INSERT(*element, queue*) inserts an element and returns the resulting queue.

* * *

QUEUE

* * *

Queues are characterized by the *order* in which they store the inserted nodes. Three common variants are the first-in, first-out or **FIFO queue**, which pops the *oldest* element of the queue; the last-in, first-out or **LIFO queue** (also known as a **stack**), which pops the *newest* element of the queue; and the **priority queue**, which pops the element of the queue with the highest priority according to some ordering function.

* * *

FIFO QUEUE

* * *

* * *

LIFO QUEUE

* * *

* * *

PRIORITY QUEUE

* * *

The explored set can be implemented with a hash table to allow efficient checking for repeated states. With a good implementation, insertion and lookup can be done in roughly constant time no matter how many states are stored. One must take care to implement the hash table with the right notion of equality between states. For example, in the traveling salesperson problem ([page 74](#index_split_010.html#filepos339627)), the hash table needs to know that the set of visited cities {Bucharest,Urziceni,Vaslui} is the same as {Urziceni,Vaslui,Bucharest}. Sometimes this can be achieved most easily by insisting that the data structures for states be in some **canonical form**; that is, logically equivalent states should map to the same data structure. In the case of states described by sets, for example, a bit-vector representation or a sorted list without repetition would be canonical, whereas an unsorted list would not.

* * *

CANONICAL FORM

* * *

#### **3.3.2 Measuring problem-solving performance**

Before we get into the design of specific search algorithms, we need to consider the criteria that might be used to choose among them. We can evaluate an algorithm’s performance in four ways:

> • **Completeness**: Is the algorithm guaranteed to find a solution when there is one?

* * *

COMPLETENESS

* * *

> • **Optimality**: Does the strategy find the optimal solution, as defined [on page 68](#index_split_010.html#filepos318104)?

* * *

OPTIMALITY

* * *

> • **Time complexity**: How long does it take to find a solution?

* * *

TIME COMPLEXITY

* * *

> • **Space complexity**: How much memory is needed to perform the search?

* * *

SPACE COMPLEXITY

* * *

Time and space complexity are always considered with respect to some measure of the problem difficulty. In theoretical computer science, the typical measure is the size of the state space graph, |*V*| + |*E*|, where *V* is the set of vertices (nodes) of the graph and *E* is the set of edges (links). This is appropriate when the graph is an explicit data structure that is input to the search program. (The map of Romania is an example of this.) In AI, the graph is often represented *implicitly* by the initial state, actions, and transition model and is frequently infinite. For these reasons, complexity is expressed in terms of three quantities: *b*, the **branching factor** or maximum number of successors of any node; *d*, the **depth** of the shallowest goal node (i.e., the number of steps along the path from the root); and *m*, the maximum length of any path in the state space. Time is often measured in terms of the number of nodes generated during the search, and space in terms of the maximum number of nodes stored in memory. For the most part, we describe time and space complexity for search on a tree; for a graph, the answer depends on how “redundant” the paths in the state space are.

* * *

BRANCHING FACTOR

* * *

* * *

DEPTH

* * *

To assess the effectiveness of a search algorithm, we can consider just the **search cost**—which typically depends on the time complexity but can also include a term for memory usage—or we can use the **total cost**, which combines the search cost and the path cost of the solution found. For the problem of finding a route from Arad to Bucharest, the search cost is the amount of time taken by the search and the solution cost is the total length of the path in kilometers. Thus, to compute the total cost, we have to add milliseconds and kilometers. There is no “official exchange rate” between the two, but it might be reasonable in this case to convert kilometers into milliseconds by using an estimate of the car’s average speed (because time is what the agent cares about). This enables the agent to find an optimal tradeoff point at which further computation to find a shorter path becomes counterproductive. The more general problem of tradeoffs between different goods is taken up in [Chapter 16](#index_split_015.html#filepos2423989).

* * *

SEARCH COST

* * *

* * *

TOTAL COST

* * *

### 3.4 UNINFORMED SEARCH STRATEGIES

This section covers several search strategies that come under the heading of **uninformed search** (also called **blind search**). The term means that the strategies have no additional information about states beyond that provided in the problem definition. All they can do is generate successors and distinguish a goal state from a non-goal state. All search strategies are distinguished by the *order* in which nodes are expanded. Strategies that know whether one non-goal state is “more promising” than another are called **informed search** or **heuristic search** strategies; they are covered in [Section 3.5](#index_split_000.html#filepos401935).

* * *

UNINFORMED SEARCH

* * *

* * *

BLIND SEARCH

* * *

* * *

INFORMED SEARCH

* * *

* * *

HEURISTIC SEARCH

* * *

#### **3.4.1 Breadth-first search**

**Breadth-first search** is a simple strategy in which the root node is expanded first, then all the successors of the root node are expanded next, then *their* successors, and so on. In general, all the nodes are expanded at a given depth in the search tree before any nodes at the next level are expanded.

* * *

BREADTH-FIRST SEARCH

* * *

Breadth-first search is an instance of the general graph-search algorithm ([Figure 3.7](#index_split_010.html#filepos352194)) in which the *shallowest* unexpanded node is chosen for expansion. This is achieved very simply by using a FIFO queue for the frontier. Thus, new nodes (which are always deeper than their parents) go to the back of the queue, and old nodes, which are shallower than the new nodes, get expanded first. There is one slight tweak on the general graph-search algorithm, which is that the goal test is applied to each node when it is *generated* rather than when it is selected for expansion. This decision is explained below, where we discuss time complexity. Note also that the algorithm, following the general template for graph search, discards any new path to a state already in the frontier or explored set; it is easy to see that any such path must be at least as deep as the one already found. Thus, breadth-first search always has the shallowest path to every node on the frontier.

Pseudocode is given in [Figure 3.11](#index_split_010.html#filepos371533). [Figure 3.12](#index_split_010.html#filepos373078) shows the progress of the search on a simple binary tree.

How does breadth-first search rate according to the four criteria from the previous section? We can easily see that it is *complete*—if the shallowest goal node is at some finite depth *d*, breadth-first search will eventually find it after generating all shallower nodes (provided the branching factor *b* is finite). Note that as soon as a goal node is generated, we know it is the shallowest goal node because all shallower nodes must have been generated already and failed the goal test. Now, the *shallowest* goal node is not necessarily the *optimal* one; technically, breadth-first search is optimal if the path cost is a nondecreasing function of the depth of the node. The most common such scenario is that all actions have the same cost.

> ![image](images/00040.jpg)

> **Figure 3.11** Breadth-first search on a graph.

So far, the news about breadth-first search has been good. The news about time and space is not so good. Imagine searching a uniform tree where every state has *b* successors. The root of the search tree generates *b* nodes at the first level, each of which generates *b* more nodes, for a total of *b*² at the second level. Each of *these* generates *b* more nodes, yielding *b*³ nodes at the third level, and so on. Now suppose that the solution is at depth *d*. In the worst case, it is the last node generated at that level. Then the total number of nodes generated is

> *b* + *b*² + *b*³ + … + *b*^(*d*) = *O*(*b*^(*d*)).

(If the algorithm were to apply the goal test to nodes when selected for expansion, rather than when generated, the whole layer of nodes at depth *d* would be expanded before the goal was detected and the time complexity would be *O*(*b*^(*d*+1)).)

> ![image](images/00041.jpg)

> **Figure 3.12** Breadth-first search on a simple binary tree. At each stage, the node to be expanded next is indicated by a marker.

As for space complexity: for any kind of graph search, which stores every expanded node in the *explored* set, the space complexity is always within a factor of *b* of the time complexity. For breadth-first graph search in particular, every node generated remains in memory. There will be *O*(*b*^(*d*−1)) nodes in the explored set and *O*(*b^d*) nodes in the frontier, so the space complexity is *O*(*b*^(*d*)), i.e., it is dominated by the size of the frontier. Switching to a tree search would not save much space, and in a state space with many redundant paths, switching could cost a great deal of time.

An exponential complexity bound such as *O*(*b*^(*d*)) is scary. [Figure 3.13](#index_split_010.html#filepos374813) shows why. It lists, for various values of the solution depth *d*, the time and memory required for a breadth-first search with branching factor *b* = 10. The table assumes that 1 million nodes can be generated per second and that a node requires 1000 bytes of storage. Many search problems fit roughly within these assumptions (give or take a factor of 100) when run on a modern personal computer.

> ![image](images/00042.jpg)

> **Figure 3.13** Time and memory requirements for breadth-first search. The numbers shown assume branching factor *b* = 10; 1 million nodes/second; 1000 bytes/node.

![hand](images/00006.jpg)

Two lessons can be learned from [Figure 3.13](#index_split_010.html#filepos374813). First, *the memory requirements are a bigger problem for breadth-first search than is the execution time.* One might wait 13 days for the solution to an important problem with search depth 12, but no personal computer has the petabyte of memory it would take. Fortunately, other strategies require less memory.

![hand](images/00006.jpg)

The second lesson is that time is still a major factor. If your problem has a solution at depth 16, then (given our assumptions) it will take about 350 years for breadth-first search (or indeed any uninformed search) to find it. In general, *exponential-complexity search problems cannot be solved by uninformed methods for any but the smallest instances.*

#### **3.4.2 Uniform-cost search**

When all step costs are equal, breadth-first search is optimal because it always expands the *shallowest* unexpanded node. By a simple extension, we can find an algorithm that is optimal with any step-cost function. Instead of expanding the shallowest node, **uniform-cost search** expands the node *n* with the *lowest path cost* *g*(*n*). This is done by storing the frontier as a priority queue ordered by *g*. The algorithm is shown in [Figure 3.14](#index_split_010.html#filepos377697).

* * *

UNIFORM-COST SEARCH

* * *

In addition to the ordering of the queue by path cost, there are two other significant differences from breadth-first search. The first is that the goal test is applied to a node when it is *selected for expansion* (as in the generic graph-search algorithm shown in [Figure 3.7](#index_split_010.html#filepos352194)) rather than when it is first generated. The reason is that the first goal node that is *generated* may be on a suboptimal path. The second difference is that a test is added in case a better path is found to a node currently on the frontier.

> ![image](images/00043.jpg)

> **Figure 3.14** Uniform-cost search on a graph. The algorithm is identical to the general graph search algorithm in [Figure 3.7](#index_split_010.html#filepos352194), except for the use of a priority queue and the addition of an extra check in case a shorter path to a frontier state is discovered. The data structure for *frontier* needs to support efficient membership testing, so it should combine the capabilities of a priority queue and a hash table.

> ![image](images/00044.jpg)

> **Figure 3.15** Part of the Romania state space, selected to illustrate uniform-cost search.

Both of these modifications come into play in the example shown in [Figure 3.15](#index_split_010.html#filepos378375), where the problem is to get from Sibiu to Bucharest. The successors of Sibiu are Rimnicu Vilcea and Fagaras, with costs 80 and 99, respectively. The least-cost node, Rimnicu Vilcea, is expanded next, adding Pitesti with cost 80 + 97 = 177. The least-cost node is now Fagaras, so it is expanded, adding Bucharest with cost 99 + 211 = 310. Now a goal node has been generated, but uniform-cost search keeps going, choosing Pitesti for expansion and adding a second path to Bucharest with cost 80 + 97 + 101 = 278. Now the algorithm checks to see if this new path is better than the old one; it is, so the old one is discarded. Bucharest, now with *g*\-cost 278, is selected for expansion and the solution is returned.

It is easy to see that uniform-cost search is optimal in general. First, we observe that whenever uniform-cost search selects a node *n* for expansion, the optimal path to that node has been found. (Were this not the case, there would have to be another frontier node *n*′ on the optimal path from the start node to *n*, by the graph separation property of [Figure 3.9](#index_split_010.html#filepos356410); by definition, *n*′ would have lower *g*\-cost than *n* and would have been selected first.) Then, because step costs are nonnegative, paths never get shorter as nodes are added. These two facts together imply that *uniform-cost search expands nodes in order of their optimal path cost.* Hence, the first goal node selected for expansion must be the optimal solution.

![hand](images/00006.jpg)

Uniform-cost search does not care about the *number* of steps a path has, but only about their total cost. Therefore, it will get stuck in an infinite loop if there is a path with an infinite sequence of zero-cost actions—for example, a sequence of *NoOp* actions.[⁶](#index_split_015.html#filepos5571564) Completeness is guaranteed provided the cost of every step exceeds some small positive constant ε.

Uniform-cost search is guided by path costs rather than depths, so its complexity is not easily characterized in terms of *b* and *d*. Instead, let *C*^(\*) be the cost of the optimal solution,[⁷](#index_split_015.html#filepos5571776) and assume that every action costs at least. Then the algorithm’s worst-case time and space complexity is ![math](images/00045.jpg), which can be much greater than *b*^(*d*). This is because uniform-cost search can explore large trees of small steps before exploring paths involving large and perhaps useful steps. When all step costs are equal, ![math](images/00046.jpg)is just *b*^(*d* + 1). When all step costs are the same, uniform-cost search is similar to breadth-first search, except that the latter stops as soon as it generates a goal, whereas uniform-cost search examines all the nodes at the goal’s depth to see if one has a lower cost; thus uniform-cost search does strictly more work by expanding nodes at depth *d* unnecessarily.

#### **3.4.3 Depth-first search**

**Depth-first search** always expands the *deepest* node in the current frontier of the search tree. The progress of the search is illustrated in [Figure 3.16](#index_split_010.html#filepos383871). The search proceeds immediately to the deepest level of the search tree, where the nodes have no successors. As those nodes are expanded, they are dropped from the frontier, so then the search “backs up” to the next deepest node that still has unexplored successors.

* * *

DEPTH-FIRST SEARCH

* * *

The depth-first search algorithm is an instance of the graph-search algorithm in [Figure 3.7](#index_split_010.html#filepos352194); whereas breadth-first-search uses a FIFO queue, depth-first search uses a LIFO queue. A LIFO queue means that the most recently generated node is chosen for expansion. This must be the deepest unexpanded node because it is one deeper than its parent—which, in turn, was the deepest unexpanded node when it was selected.

As an alternative to the GRAPH\-SEARCH\-style implementation, it is common to implement depth-first search with a recursive function that calls itself on each of its children in turn. (*A* recursive depth-first algorithm incorporating a depth limit is shown in [Figure 3.17](#index_split_010.html#filepos390780).)

> ![image](images/00047.jpg)

> **Figure 3.16** Depth-first search on a binary tree. The unexplored region is shown in light gray. Explored nodes with no descendants in the frontier are removed from memory. Nodes at depth 3 have no successors and *M* is the only goal node.

The properties of depth-first search depend strongly on whether the graph-search or tree-search version is used. The graph-search version, which avoids repeated states and redundant paths, is complete in finite state spaces because it will eventually expand every node. The tree-search version, on the other hand, is *not* complete—for example, in [Figure 3.6](#index_split_010.html#filepos351692) the algorithm will follow the Arad–Sibiu–Arad–Sibiu loop forever. Depth-first tree search can be modified at no extra memory cost so that it checks new states against those on the path from the root to the current node; this avoids infinite loops in finite state spaces but does not avoid the proliferation of redundant paths. In infinite state spaces, both versions fail if an infinite non-goal path is encountered. For example, in Knuth’s 4 problem, depth-first search would keep applying the factorial operator forever.

For similar reasons, both versions are nonoptimal. For example, in [Figure 3.16](#index_split_010.html#filepos383871), depth-first search will explore the entire left subtree even if node *C* is a goal node. If node *J* were also a goal node, then depth-first search would return it as a solution instead of *C*, which would be a better solution; hence, depth-first search is not optimal.

The time complexity of depth-first graph search is bounded by the size of the state space (which may be infinite, of course). A depth-first tree search, on the other hand, may generate all of the *O*(*b*^(*m*)) nodes in the search tree, where *m* is the maximum depth of any node; this can be much greater than the size of the state space. Note that *m* itself can be much larger than *d* (the depth of the shallowest solution) and is infinite if the tree is unbounded.

So far, depth-first search seems to have no clear advantage over breadth-first search, so why do we include it? The reason is the space complexity. For a graph search, there is no advantage, but a depth-first tree search needs to store only a single path from the root to a leaf node, along with the remaining unexpanded sibling nodes for each node on the path. Once a node has been expanded, it can be removed from memory as soon as all its descendants have been fully explored. (See [Figure 3.16](#index_split_010.html#filepos383871).) For a state space with branching factor *b* and maximum depth *m*, depth-first search requires storage of only *O*(*bm*) nodes. Using the same assumptions as for [Figure 3.13](#index_split_010.html#filepos374813) and assuming that nodes at the same depth as the goal node have no successors, we find that depth-first search would require 156 kilobytes instead of 10 exabytes at depth *d* = 16, a factor of 7 trillion times less space. This has led to the adoption of depth-first tree search as the basic workhorse of many areas of AI, including constraint satisfaction ([Chapter 6](#index_split_000.html#filepos813005)), propositional satisfiability ([Chapter 7](#index_split_000.html#filepos939379)), and logic programming ([Chapter 9](#index_split_015.html#filepos1300686)). For the remainder of this section, we focus primarily on the tree-search version of depth-first search.

A variant of depth-first search called **backtracking search** uses still less memory. (See [Chapter 6](#index_split_000.html#filepos813005) for more details.) In backtracking, only one successor is generated at a time rather than all successors; each partially expanded node remembers which successor to generate next. In this way, only *O*(*m*) memory is needed rather than *O*(*bm*). Backtracking search facilitates yet another memory-saving (and time-saving) trick: the idea of generating a successor by *modifying* the current state description directly rather than copying it first. This reduces the memory requirements to just one state description and *O*(*m*) actions. For this to work, we must be able to undo each modification when we go back to generate the next successor. For problems with large state descriptions, such as robotic assembly, these techniques are critical to success.

* * *

BACKTRACKING SEARCH

* * *

#### **3.4.4 Depth-limited search**

The embarrassing failure of depth-first search in infinite state spaces can be alleviated by supplying depth-first search with a predetermined depth limit ℓ. That is, nodes at depth ℓ are treated as if they have no successors. This approach is called **depth-limited search**. The depth limit solves the infinite-path problem. Unfortunately, it also introduces an additional source of incompleteness if we choose ℓ < *d*, that is, the shallowest goal is beyond the depth limit. (This is likely when *d* is unknown.) Depth-limited search will also be nonoptimal if we choose ℓ > *d*. Its time complexity is *O*(*b*^ℓ) and its space complexity is *O*(*b*ℓ). Depth-first search can be viewed as a special case of depth-limited search with ℓ = ∞.

* * *

DEPTH-LIMITED SEARCH

* * *

Sometimes, depth limits can be based on knowledge of the problem. For example, on the map of Romania there are 20 cities. Therefore, we know that if there is a solution, it must be of length 19 at the longest, so ℓ = 19 is a possible choice. But in fact if we studied the map carefully, we would discover that any city can be reached from any other city in at most 9 steps. This number, known as the **diameter** of the state space, gives us a better depth limit, which leads to a more efficient depth-limited search. For most problems, however, we will not know a good depth limit until we have solved the problem.

> ![image](images/00048.jpg)

> **Figure 3.17** A recursive implementation of depth-limited tree search.

* * *

DIAMETER

* * *

Depth-limited search can be implemented as a simple modification to the general tree-or graph-search algorithm. Alternatively, it can be implemented as a simple recursive algorithm as shown in [Figure 3.17](#index_split_010.html#filepos390780). Notice that depth-limited search can terminate with two kinds of failure: the standard *failure* value indicates no solution; the *cutoff* value indicates no solution within the depth limit.

#### **3.4.5 Iterative deepening depth-first search**

**Iterative deepening search** (or iterative deepening depth-first search) is a general strategy, often used in combination with depth-first tree search, that finds the best depth limit. It does this by gradually increasing the limit—first 0, then 1, then 2, and so on—until a goal is found. This will occur when the depth limit reaches *d*, the depth of the shallowest goal node. The algorithm is shown in [Figure 3.18](#index_split_010.html#filepos393712). Iterative deepening combines the benefits of depth-first and breadth-first search. Like depth-first search, its memory requirements are modest: *O*(*bd*) to be precise. Like breadth-first search, it is complete when the branching factor is finite and optimal when the path cost is a nondecreasing function of the depth of the node. [Figure 3.19](#index_split_010.html#filepos394196) shows four iterations of ITERATIVE\-DEEPENING\-SEARCH on a binary search tree, where the solution is found on the fourth iteration.

* * *

ITERATIVE DEEPENING SEARCH

* * *

Iterative deepening search may seem wasteful because states are generated multiple times. It turns out this is not too costly. The reason is that in a search tree with the same (or nearly the same) branching factor at each level, most of the nodes are in the bottom level, so it does not matter much that the upper levels are generated multiple times. In an iterative deepening search, the nodes on the bottom level (depth *d*) are generated once, those on the next-to-bottom level are generated twice, and so on, up to the children of the root, which are generated *d* times. So the total number of nodes generated in the worst case is

> ![image](images/00049.jpg)

> **Figure 3.18** The iterative deepening search algorithm, which repeatedly applies depth-limited search with increasing limits. It terminates when a solution is found or if the depth-limited search returns *failure*, meaning that no solution exists.

> ![image](images/00050.jpg)

> **Figure 3.19** Four iterations of iterative deepening search on a binary tree.

> *N*(IDS) = (*d*)*b* + (*d* − 1)*b*² + … + (1)*b*^(*d*),

which gives a time complexity of *O*(*b*^(*d*))—asymptotically the same as breadth-first search. There is some extra cost for generating the upper levels multiple times, but it is not large. For example, if *b* = 10 and *d* = 5, the numbers are

> *N*(IDS) = 50 + 400 + 3, 000 + 20, 000 + 100, 000 = 123, 450

> *N*(BFS) = 10 + 100 + 1, 000 + 10, 000 + 100, 000 = 111, 110.

If you are really concerned about repeating the repetition, you can use a hybrid approach that runs breadth-first search until almost all the available memory is consumed, and then runs iterative deepening from all the nodes in the frontier. *In general, iterative deepening is the preferred uninformed search method when the search space is large and the depth of the solution is not known.*

![hand](images/00006.jpg)

Iterative deepening search is analogous to breadth-first search in that it explores a complete layer of new nodes at each iteration before going on to the next layer. It would seem worthwhile to develop an iterative analog to uniform-cost search, inheriting the latter algorithm’s optimality guarantees while avoiding its memory requirements. The idea is to use increasing path-cost limits instead of increasing depth limits. The resulting algorithm, called **iterative lengthening search**, is explored in Exercise 3.17. It turns out, unfortunately, that iterative lengthening incurs substantial overhead compared to uniform-cost search.

* * *

ITERATIVE LENGTHENING SEARCH

* * *

#### **3.4.6 Bidirectional search**

The idea behind bidirectional search is to run two simultaneous searches—one forward from the initial state and the other backward from the goal—hoping that the two searches meet in the middle ([Figure 3.20](#index_split_010.html#filepos398865)). The motivation is that *b*^(*d*/2) + *b*^(*d*/2) is much less than *b*^(*d*), or in the figure, the area of the two small circles is less than the area of one big circle centered on the start and reaching to the goal.

Bidirectional search is implemented by replacing the goal test with a check to see whether the frontiers of the two searches intersect; if they do, a solution has been found. (It is important to realize that the first such solution found may not be optimal, even if the two searches are both breadth-first; some additional search is required to make sure there isn’t another shortcut across the gap.) The check can be done when each node is generated or selected for expansion and, with a hash table, will take constant time. For example, if a problem has solution depth *d* = 6, and each direction runs breadth-first search one node at a time, then in the worst case the two searches meet when they have generated all of the nodes at depth 3. For *b* = 10, this means a total of 2,220 node generations, compared with 1,111,110 for a standard breadth-first search. Thus, the time complexity of bidirectional search using breadth-first searches in both directions is *O*(*b*^(*d*/2)). The space complexity is also *O*(*b*^(*d*/2)). We can reduce this by roughly half if one of the two searches is done by iterative deepening, but at least one of the frontiers must be kept in memory so that the intersection check can be done. This space requirement is the most significant weakness of bidirectional search.

> ![image](images/00051.jpg)

> **Figure 3.20** A schematic view of a bidirectional search that is about to succeed when a branch from the start node meets a branch from the goal node.

The reduction in time complexity makes bidirectional search attractive, but how do we search backward? This is not as easy as it sounds. Let the **predecessors** of a state *x* be all those states that have *x* as a successor. Bidirectional search requires a method for computing predecessors. When all the actions in the state space are reversible, the predecessors of *x* are just its successors. Other cases may require substantial ingenuity.

* * *

PREDECESSOR

* * *

Consider the question of what we mean by “the goal” in searching “backward from the goal.” For the 8-puzzle and for finding a route in Romania, there is just one goal state, so the backward search is very much like the forward search. If there are several *explicitly listed* goal states—for example, the two dirt-free goal states in [Figure 3.3](#index_split_010.html#filepos324794)—then we can construct a new dummy goal state whose immediate predecessors are all the actual goal states. But if the goal is an abstract description, such as the goal that “no queen attacks another queen” in the *n*\-queens problem, then bidirectional search is difficult to use.

#### **3.4.7 Comparing uninformed search strategies**

[Figure 3.21](#index_split_010.html#filepos401227) compares search strategies in terms of the four evaluation criteria set forth in [Section 3.3.2](#index_split_000.html#filepos363065). This comparison is for tree-search versions. For graph searches, the main differences are that depth-first search is complete for finite state spaces and that the space and time complexities are bounded by the size of the state space.

> ![image](images/00052.jpg)

> **Figure 3.21** Evaluation of tree-search strategies. *b* is the branching factor; *d* is the depth of the shallowest solution; *m* is the maximum depth of the search tree; *l* is the depth limit. Superscript caveats are as follows:^(*a*) complete if *b* is finite;^(*b*) complete if step costs ≥ ε for positive ε;^(*c*) optimal if step costs are all identical;^(*d*) if both directions use breadth-first search.

### 3.5 INFORMED (HEURISTIC) SEARCH STRATEGIES

This section shows how an **informed search** strategy—one that uses problem-specific knowledge beyond the definition of the problem itself—can find solutions more efficiently than can an uninformed strategy.

* * *

INFORMED SEARCH

* * *

The general approach we consider is called **best-first search**. Best-first search is an instance of the general TREE\-SEARCH or GRAPH\-SEARCH algorithm in which a node is selected for expansion based on an **evaluation function**, *f*(*n*). The evaluation function is construed as a cost estimate, so the node with the *lowest* evaluation is expanded first. The implementation of best-first graph search is identical to that for uniform-cost search ([Figure 3.14](#index_split_010.html#filepos377697)), except for the use of *f* instead of *g* to order the priority queue.

* * *

BEST-FIRST SEARCH

* * *

* * *

EVALUATION FUNCTION

* * *

The choice of *f* determines the search strategy. (For example, as Exercise 3.21 shows, best-first tree search includes depth-first search as a special case.) Most best-first algorithms include as a component of *f* a **heuristic function**, denoted *h*(*n*):

* * *

HEURISTIC FUNCTION

* * *

> *h*(*n*) = estimated cost of the cheapest path from the state at node *n* to a goal state.

(Notice that *h*(*n*) takes a *node* as input, but, unlike *g*(*n*), it depends only on the *state* at that node.) For example, in Romania, one might estimate the cost of the cheapest path from Arad to Bucharest via the straight-line distance from Arad to Bucharest.

Heuristic functions are the most common form in which additional knowledge of the problem is imparted to the search algorithm. We study heuristics in more depth in [Section 3.6](#index_split_000.html#filepos439536). For now, we consider them to be arbitrary, nonnegative, problem-specific functions, with one constraint: if *n* is a goal node, then *h*(*n*) = 0. The remainder of this section covers two ways to use heuristic information to guide search.

#### **3.5.1 Greedy best-first search**

**Greedy best-first search**[⁸](#index_split_015.html#filepos5572002) tries to expand the node that is closest to the goal, on the grounds that this is likely to lead to a solution quickly. Thus, it evaluates nodes by using just the heuristic function; that is, *f*(*n*) = *h*(*n*).

* * *

GREEDY BEST-FIRST SEARCH

* * *

Let us see how this works for route-finding problems in Romania; we use the **straight-line distance** heuristic, which we will call *h*[*SLD*]. If the goal is Bucharest, we need to know the straight-line distances to Bucharest, which are shown in [Figure 3.22](#index_split_010.html#filepos407430). For example, *h*[*SLD*](*In*(*Arad*)) = 366. Notice that the values of *h*[*SLD*] cannot be computed from the problem description itself. Moreover, it takes a certain amount of experience to know that *h*[*SLD*] is correlated with actual road distances and is, therefore, a useful heuristic.

* * *

STRAIGHT-LINE DISTANCE

* * *

[Figure 3.23](#index_split_010.html#filepos410724) shows the progress of a greedy best-first search using *h*[*SLD*] to find a path from Arad to Bucharest. The first node to be expanded from Arad will be Sibiu because it is closer to Bucharest than either Zerind or Timisoara. The next node to be expanded will be Fagaras because it is closest. Fagaras in turn generates Bucharest, which is the goal. For this particular problem, greedy best-first search using *h*[*SLD*] finds a solution without ever expanding a node that is not on the solution path; hence, its search cost is minimal. It is not optimal, however: the path via Sibiu and Fagaras to Bucharest is 32 kilometers longer than the path through Rimnicu Vilcea and Pitesti. This shows why the algorithm is called “greedy”—at each step it tries to get as close to the goal as it can.

> ![image](images/00053.jpg)

> **Figure 3.22** Values of *h*[*SLD*]—straight-line distances to Bucharest.

Greedy best-first tree search is also incomplete even in a finite state space, much like depth-first search. Consider the problem of getting from Iasi to Fagaras. The heuristic suggests that Neamt be expanded first because it is closest to Fagaras, but it is a dead end. The solution is to go first to Vaslui—a step that is actually farther from the goal according to the heuristic—and then to continue to Urziceni, Bucharest, and Fagaras. The algorithm will never find this solution, however, because expanding Neamt puts Iasi back into the frontier, Iasi is closer to Fagaras than Vaslui is, and so Iasi will be expanded again, leading to an infinite loop. (The graph search version *is* complete in finite spaces, but not in infinite ones.) The worst-case time and space complexity for the tree version is *O*(*b*^(*m*)),where *m* is the maximum depth of the search space. With a good heuristic function, however, the complexity can be reduced substantially. The amount of the reduction depends on the particular problem and on the quality of the heuristic.

#### **3.5.2 A\* search: Minimizing the total estimated solution cost**

The most widely known form of best-first search is called **A**^(\*) **search** (pronounced “A-star search”). It evaluates nodes by combining *g*(*n*), the cost to reach the node, and *h*(*n*), the cost to get from the node to the goal:

> *f*(*n*) = *g*(*n*)+ *h*(*n*).

* * *

A^(\*) SEARCH

* * *

Since *g*(*n*) gives the path cost from the start node to node *n*, and *h*(*n*) is the estimated cost of the cheapest path from *n* to the goal, we have

> *f*(*n*) = estimated cost of the cheapest solution through *n*.

Thus, if we are trying to find the cheapest solution, a reasonable thing to try first is the node with the lowest value of *g*(*n*) + *h*(*n*). It turns out that this strategy is more than just reasonable: provided that the heuristic function *h*(*n*) satisfies certain conditions, A^(\*) search is both complete and optimal. The algorithm is identical to UNIFORM\-COST\-SEARCH except that A^(\*) uses *g* + *h* instead of *g*.

> ![image](images/00054.jpg)

> **Figure 3.23** Stages in a greedy best-first tree search for Bucharest with the straight-line distance heuristic *h*[*SLD*]. Nodes are labeled with their *h*\-values.

##### **Conditions for optimality: Admissibility and consistency**

The first condition we require for optimality is that *h*(*n*) be an **admissible heuristic**. An admissible heuristic is one that *never overestimates* the cost to reach the goal. Because *g*(*n*) is the actual cost to reach *n* along the current path, and *f*(*n*)= *g*(*n*)+ *h*(*n*), we have as an immediate consequence that *f* (*n*) never overestimates the true cost of a solution along the current path through *n*.

* * *

ADMISSIBLE HEURISTIC

* * *

Admissible heuristics are by nature optimistic because they think the cost of solving the problem is less than it actually is. An obvious example of an admissible heuristic is the straight-line distance *h*[*SLD*] that we used in getting to Bucharest. Straight-line distance is admissible because the shortest path between any two points is a straight line, so the straight line cannot be an overestimate. In [Figure 3.24](#index_split_010.html#filepos418167), we show the progress of an A^(\*) tree search for Bucharest. The values of g are computed from the step costs in [Figure 3.2](#index_split_010.html#filepos318111), and the values of *h*[*SLD*] are given in [Figure 3.22](#index_split_010.html#filepos407430). Notice in particular that Bucharest first appears on the frontier at step (*e*), but it is not selected for expansion because its *f*\-cost (450) is higher than that of Pitesti (417). Another way to say this is that there *might* be a solution through Pitesti whose cost is as low as 417, so the algorithm will not settle for a solution that costs 450.

A second, slightly stronger condition called **consistency** (or sometimes **monotonicity**) is required only for applications of A^(\*) to graph search.[⁹](#index_split_015.html#filepos5572300) A heuristic *h*(*n*) is consistent if, for every node *n* and every successor *n*′ of *n* generated by any action *a*, the estimated cost of reaching the goal from *n* is no greater than the step cost of getting to *n*′ plus the estimated cost of reaching the goal from *n*′:

> *h*(*n*′) ≤ *c*(*n, a, n*′)+ *h*(*n*′).

* * *

CONSISTENCY

* * *

* * *

MONOTONICITY

* * *

This is a form of the general **triangle inequality**, which stipulates that each side of a triangle cannot be longer than the sum of the other two sides. Here, the triangle is formed by *n, n*′, and the goal *G*[*n*] closest to *n*. For an admissible heuristic, the inequality makes perfect sense: if there were a route from *n* to *G*[*n*] via *n*′ that was cheaper than *h*(*n*), that would violate the property that *h*(*n*) is a lower bound on the cost to reach *G*[*n*].

* * *

TRIANGLE INEQUALITY

* * *

It is fairly easy to show (Exercise 3.29) that every consistent heuristic is also admissible. Consistency is therefore a stricter requirement than admissibility, but one has to work quite hard to concoct heuristics that are admissible but not consistent. All the admissible heuristics we discuss in this chapter are also consistent. Consider, for example, *h*[*SLD*]. We know that the general triangle inequality is satisfied when each side is measured by the straight-line distance and that the straight-line distance between *n* and *n*′ is no greater than *c*(*n, a, n*′). Hence, *h*[*SLD*] is a consistent heuristic.

##### **Optimality of A\***

![hand](images/00006.jpg)

As we mentioned earlier, *A*^(\*) has the following properties: *the tree-search version of* A^(\*) *is optimal if* *h*(*n*) *is admissible, while the graph-search version is optimal if* *h*(*n*) *is consistent.*

We show the second of these two claims since it is more useful. The argument essentially mirrors the argument for the optimality of uniform-cost search, with *g* replaced by *f*—just as in the A^(\*) algorithm itself.

![hand](images/00006.jpg)

The first step is to establish the following: *if* *h*(*n*) *is consistent, then the values of* *f*(*n*) *along any path are nondecreasing.* The proof follows directly from the definition of consistency. Suppose *n*′ is a successor of *n*; then *g*(*n*′)= *g*(*n*) + *c*(*n, a, n*′) for some action *a*, and we have

> *f*(*n*′) = *g*(*n*′) + *h*(*n*′) = *g*(*n*) + *c*(*n, a, n*′)+ *h*(*n*′) ≥ *g*(*n*)+ *h*(*n*) = *f*(*n*).

![hand](images/00006.jpg)

The next step is to prove that *whenever A^(\*) selects a node* *n* *for expansion, the optimal path to that node has been found.* Were this not the case, there would have to be another frontier node *n*′ on the optimal path from the start node to *n*, by the graph separation property of [Figure 3.9](#index_split_010.html#filepos356410); because *f* is nondecreasing along any path, *n*′ would have lower *f*\-cost than *n* and would have been selected first.

> ![image](images/00055.jpg)

> **Figure 3.24** Stages in an A^(\*) search for Bucharest. Nodes are labeled with *f* = *g* + *h*. The *h* values are the straight-line distances to Bucharest taken from [Figure 3.22](#index_split_010.html#filepos407430).

> ![image](images/00056.jpg)

> **Figure 3.25** Map of Romania showing contours at *f* = 380, *f* = 400, and *f* = 420, with Arad as the start state. Nodes inside a given contour have *f*\-costs less than or equal to the contour value.

From the two preceding observations, it follows that the sequence of nodes expanded by A^(\*) using GRAPH\-SEARCH is in nondecreasing order of *f*(*n*). Hence, the first goal node selected for expansion must be an optimal solution because *f* is the true cost for goal nodes (which have *h* = 0) and all later goal nodes will be at least as expensive.

The fact that *f*\-costs are nondecreasing along any path also means that we can draw **contours** in the state space, just like the contours in a topographic map. [Figure 3.25](#index_split_010.html#filepos418649) shows an example. Inside the contour labeled 400, all nodes have *f*(*n*) less than or equal to 400, and so on. Then, because A^(\*) expands the frontier node of lowest *f*\-cost, we can see that an A\* search fans out from the start node, adding nodes in concentric bands of increasing *f*\-cost.

* * *

CONTOUR

* * *

With uniform-cost search (A^(\*) search using *h*(*n*) = 0), the bands will be “circular” around the start state. With more accurate heuristics, the bands will stretch toward the goal state and become more narrowly focused around the optimal path. If *C*^(\*) is the cost of the optimal solution path, then we can say the following:

> • A^(\*) expands all nodes with *f*(*n*) < *C*^(\*).

> • A^(\*) might then expand some of the nodes right on the “goal contour” (where *f*(*n*) = *C*^(\*)) before selecting a goal node.

Completeness requires that there be only finitely many nodes with cost less than or equal to *C*^(\*), a condition that is true if all step costs exceed some finite ε and if *b* is finite.

Notice that A^(\*) expands no nodes with *f*(*n*) > *C*^(\*)—for example, Timisoara is not expanded in [Figure 3.24](#index_split_010.html#filepos418167) even though it is a child of the root. We say that the subtree below Timisoara is **pruned**; because *h[SLD]* is admissible, the algorithm can safely ignore this subtree while still guaranteeing optimality. The concept of pruning—eliminating possibilities from consideration without having to examine them—is important for many areas of AI.

* * *

PRUNING

* * *

One final observation is that among optimal algorithms of this type—algorithms that extend search paths from the root and use the same heuristic information—A^(\*) is **optimally efficient** for any given consistent heuristic. That is, no other optimal algorithm is guaranteed to expand fewer nodes than A^(\*) (except possibly through tiebreaking among nodes with *f*(*n*) = *C*^(\*)). This is because any algorithm that *does not* expand all nodes with *f*(*n*) < *C*^(\*) runs the risk of missing the optimal solution.

* * *

OPTIMALLY EFFICIENT

* * *

That A^(\*) search is complete, optimal, and optimally efficient among all such algorithms is rather satisfying. Unfortunately, it does not mean that A^(\*) is the answer to all our searching needs. The catch is that, for most problems, the number of states within the goal contour search space is still exponential in the length of the solution. The details of the analysis are beyond the scope of this book, but the basic results are as follows. For problems with constant step costs, the growth in run time as a function of the optimal solution depth *d* is analyzed in terms of the the **absolute error** or the **relative error** of the heuristic. The absolute error is defined as Δ ≡ *h*^(\*) − *h*, where *h*^(\*) is the actual cost of getting from the root to the goal, and the relative error is defined as ε ≡ (*h*^(\*) − *h*)/*h*^(\*).

* * *

ABSOLUTE ERROR

* * *

* * *

RELATIVE ERROR

* * *

The complexity results depend very strongly on the assumptions made about the state space. The simplest model studied is a state space that has a single goal and is essentially a tree with reversible actions. (The 8-puzzle satisfies the first and third of these assumptions.) In this case, the time complexity of A^(\*) is exponential in the maximum absolute error, that is, *O*(*b*^Δ). For constant step costs, we can write this as *O*(*b*^(ε*d*)), where *d* is the solution depth. For almost all heuristics in practical use, the absolute error is at least proportional to the path cost *h*^(\*), so is constant or growing and the time complexity is exponential in d. We can also see the effect of a more accurate heuristic: *O*(*b*^(ε*d*)) = *O*((*b*^ε)^(*d*)), so the effective branching factor (defined more formally in the next section) is *b*^ε.

When the state space has many goal states—particularly *near-optimal* goal states—the search process can be led astray from the optimal path and there is an extra cost proportional to the number of goals whose cost is within a factor ε of the optimal cost. Finally, in the general case of a graph, the situation is even worse. There can be exponentially many states with *f*(*n*) < *C*^(\*) even if the absolute error is bounded by a constant. For example, consider a version of the vacuum world where the agent can clean up any square for unit cost without even having to visit it: in that case, squares can be cleaned in any order. With *N* initially dirty squares, there are 2^(*N*) states where some subset has been cleaned and all of them are on an optimal solution path—and hence satisfy *f*(*n*) < *C*^(\*)—even if the heuristic has an error of 1.

The complexity of A^(\*) often makes it impractical to insist on finding an optimal solution. One can use variants of A^(\*) that find suboptimal solutions quickly, or one can sometimes design heuristics that are more accurate but not strictly admissible. In any case, the use of a good heuristic still provides enormous savings compared to the use of an uninformed search. In [Section 3.6](#index_split_000.html#filepos439536), we look at the question of designing good heuristics.

Computation time is not, however, A^(\*)’s main drawback. Because it keeps all generated nodes in memory (as do all GRAPH\-SEARCH algorithms), A^(\*) usually runs out of space long before it runs out of time. For this reason, A^(\*) is not practical for many large-scale problems. There are, however, algorithms that overcome the space problem without sacrificing optimality or completeness, at a small cost in execution time. We discuss these next.

> ![image](images/00057.jpg)

> **Figure 3.26** The algorithm for recursive best-first search.

#### **3.5.3 Memory-bounded heuristic search**

The simplest way to reduce memory requirements for A^(\*) is to adapt the idea of iterative deepening to the heuristic search context, resulting in the **iterative-deepening A**^(\*) (IDA^(\*)) algorithm. The main difference between IDA^(\*) and standard iterative deepening is that the cutoff used is the *f*\-cost (*g* + *h*) rather than the depth; at each iteration, the cutoff value is the smallest *f*\-cost of any node that exceeded the cutoff on the previous iteration. IDA^(\*) is practical for many problems with unit step costs and avoids the substantial overhead associated with keeping a sorted queue of nodes. Unfortunately, it suffers from the same difficulties with real-valued costs as does the iterative version of uniform-cost search described in Exercise 3.17. This section briefly examines two other memory-bounded algorithms, called RBFS and MA^(\*).

* * *

ITERATIVE-DEEPENING A^(\*)

* * *

**Recursive best-first search** (RBFS) is a simple recursive algorithm that attempts to mimic the operation of standard best-first search, but using only linear space. The algorithm is shown in [Figure 3.26](#index_split_010.html#filepos427548). Its structure is similar to that of a recursive depth-first search, but rather than continuing indefinitely down the current path, it uses the *f\_limit* variable to keep track of the *f*\-value of the best *alternative* path available from any ancestor of the current node. If the current node exceeds this limit, the recursion unwinds back to the alternative path. As the recursion unwinds, RBFS replaces the *f*\-value of each node along the path with a **backed-up value**—the best *f*\-value of its children. In this way, RBFS remembers the f-value of the best leaf in the forgotten subtree and can therefore decide whether it’s worth reexpanding the subtree at some later time. [Figure 3.27](#index_split_010.html#filepos430443) shows how RBFS reaches Bucharest.

* * *

RECURSIVE BEST-FIRST SEARCH

* * *

* * *

BACKED-UP VALUE

* * *

> ![image](images/00058.jpg)

> **Figure 3.27** Stages in an RBFS search for the shortest route to Bucharest. The *f*\-limit value for each recursive call is shown on top of each current node, and every node is labeled with its *f*\-cost. (a) The path via Rimnicu Vilcea is followed until the current best leaf (Pitesti) has a value that is worse than the best alternative path (Fagaras). (b) The recursion unwinds and the best leaf value of the forgotten subtree (417) is backed up to Rimnicu Vilcea; then Fagaras is expanded, revealing a best leaf value of 450. (c) The recursion unwinds and the best leaf value of the forgotten subtree (450) is backed up to Fagaras; then Rimnicu Vilcea is expanded. This time, because the best alternative path (through Timisoara) costs at least 447, the expansion continues to Bucharest.

RBFS is somewhat more efficient than IDA^(\*), but still suffers from excessive node regeneration. In the example in [Figure 3.27](#index_split_010.html#filepos430443), RBFS follows the path via Rimnicu Vilcea, then “changes its mind” and tries Fagaras, and then changes its mind back again. These mind changes occur because every time the current best path is extended, its *f*\-value is likely to increase—*h* is usually less optimistic for nodes closer to the goal. When this happens, the second-best path might become the best path, so the search has to backtrack to follow it. Each mind change corresponds to an iteration of IDA^(\*) and could require many reexpansions of forgotten nodes to recreate the best path and extend it one more node.

Like A^(\*) tree search, RBFS is an optimal algorithm if the heuristic function *h*(*n*) is admissible. Its space complexity is linear in the depth of the deepest optimal solution, but its time complexity is rather difficult to characterize: it depends both on the accuracy of the heuristic function and on how often the best path changes as nodes are expanded.

IDA^(\*) and RBFS suffer from using *too little* memory. Between iterations, IDA^(\*) retains only a single number: the current *f*\-cost limit. RBFS retains more information in memory, but it uses only linear space: even if more memory were available, RBFS has no way to make use of it. Because they forget most of what they have done, both algorithms may end up reexpanding the same states many times over. Furthermore, they suffer the potentially exponential increase in complexity associated with redundant paths in graphs (see [Section 3.3](#index_split_000.html#filepos345175)).

It seems sensible, therefore, to use all available memory. Two algorithms that do this are **MA**^(\*) (memory-bounded A^(\*)) and **SMA**^(\*) (simplified MA^(\*)). SMA^(\*) is—well—simpler, so we will describe it. SMA^(\*) proceeds just like A^(\*), expanding the best leaf until memory is full. At this point, it cannot add a new node to the search tree without dropping an old one. SMA^(\*) always drops the *worst* leaf node—the one with the highest *f*\-value. Like RBFS, SMA^(\*) then backs up the value of the forgotten node to its parent. In this way, the ancestor of a forgotten subtree knows the quality of the best path in that subtree. With this information, SMA^(\*) regenerates the subtree only when all other paths have been shown to look worse than the path it has forgotten. Another way of saying this is that, if all the descendants of a node *n* are forgotten, then we will not know which way to go from *n*, but we will still have an idea of how worthwhile it is to go anywhere from *n*.

* * *

MA\*

* * *

* * *

SMA\*

* * *

The complete algorithm is too complicated to reproduce here,[^(10)](#index_split_015.html#filepos5572540) but there is one subtlety worth mentioning. We said that SMA^(\*) expands the best leaf and deletes the worst leaf. What if *all* the leaf nodes have the same *f*\-value? To avoid selecting the same node for deletion and expansion, SMA^(\*) expands the *newest* best leaf and deletes the *oldest* worst leaf. These coincide when there is only one leaf, but in that case, the current search tree must be a single path from root to leaf that fills all of memory. If the leaf is not a goal node, then *even if it is on an optimal solution path*, that solution is not reachable with the available memory. Therefore, the node can be discarded exactly as if it had no successors.

SMA^(\*) is complete if there is any reachable solution—that is, if *d*, the depth of the shallowest goal node, is less than the memory size (expressed in nodes). It is optimal if any optimal solution is reachable; otherwise, it returns the best reachable solution. In practical terms, SMA^(\*) is a fairly robust choice for finding optimal solutions, particularly when the state space is a graph, step costs are not uniform, and node generation is expensive compared to the overhead of maintaining the frontier and the explored set.

![hand](images/00006.jpg)

On very hard problems, however, it will often be the case that SMA^(\*) is forced to switch back and forth continually among many candidate solution paths, only a small subset of which can fit in memory. (This resembles the problem of **thrashing** in disk paging systems.) Then the extra time required for repeated regeneration of the same nodes means that problems that would be practically solvable by A^(\*), given unlimited memory, become intractable for SMA^(\*). That is to say, *memory limitations can make a problem intractable from the point of view of computation time.* Although no current theory explains the tradeoff between time and memory, it seems that this is an inescapable problem. The only way out is to drop the optimality requirement.

* * *

THRASHING

* * *

#### **3.5.4 Learning to search better**

We have presented several fixed strategies—breadth-first, greedy best-first, and so on—that have been designed by computer scientists. Could an agent *learn* how to search better? The answer is yes, and the method rests on an important concept called the **metalevel state space**. Each state in a metalevel state space captures the internal (computational) state of a program that is searching in an **object-level state space** such as Romania. For example, the internal state of the A^(\*) algorithm consists of the current search tree. Each action in the metalevel state space is a computation step that alters the internal state; for example, each computation step in A^(\*) expands a leaf node and adds its successors to the tree. Thus, [Figure 3.24](#index_split_010.html#filepos418167), which shows a sequence of larger and larger search trees, can be seen as depicting a path in the metalevel state space where each state on the path is an object-level search tree.

* * *

METALEVEL STATE SPACE

* * *

* * *

OBJECT-LEVEL STATE SPACE

* * *

Now, the path in [Figure 3.24](#index_split_010.html#filepos418167) has five steps, including one step, the expansion of Fagaras, that is not especially helpful. For harder problems, there will be many such missteps, and a **metalevel learning** algorithm can learn from these experiences to avoid exploring unpromising subtrees. The techniques used for this kind of learning are described in [Chapter 21](#index_split_015.html#filepos3262268). The goal of learning is to minimize the **total cost** of problem solving, trading off computational expense and path cost.

* * *

METALEVEL LEARNING

* * *

### 3.6 HEURISTIC FUNCTIONS

In this section, we look at heuristics for the 8-puzzle, in order to shed light on the nature of heuristics in general.

The 8-puzzle was one of the earliest heuristic search problems. As mentioned in [Section 3.2](#index_split_000.html#filepos323738), the object of the puzzle is to slide the tiles horizontally or vertically into the empty space until the configuration matches the goal configuration ([Figure 3.28](#index_split_010.html#filepos442646)).

The average solution cost for a randomly generated 8-puzzle instance is about 22 steps. The branching factor is about 3. (When the empty tile is in the middle, four moves are possible; when it is in a corner, two; and when it is along an edge, three.) This means that an exhaustive tree search to depth 22 would look at about 3^(22) ≈ 3.1 × 10^(10) states. A graph search would cut this down by a factor of about 170,000 because only 9!/2 = 181, 440 distinct states are reachable. (See Exercise 3.4.) This is a manageable number, but the corresponding number for the 15-puzzle is roughly 10^(13), so the next order of business is to find a good heuristic function. If we want to find the shortest solutions by using A^(\*), we need a heuristic function that never overestimates the number of steps to the goal. There is a long history of such heuristics for the 15-puzzle; here are two commonly used candidates:

> • *h*[1] = the number of misplaced tiles. For [Figure 3.28](#index_split_010.html#filepos442646), all of the eight tiles are out of position, so the start state would have *h*[1] = 8. *h*[1] is an admissible heuristic because it is clear that any tile that is out of place must be moved at least once.

> • *h*[2] = the sum of the distances of the tiles from their goal positions. Because tiles cannot move along diagonals, the distance we will count is the sum of the horizontal and vertical distances. This is sometimes called the **city block distance** or **Manhattan distance**. *h*[2] is also admissible because all any move can do is move one tile one step closer to the goal. Tiles 1 to 8 in the start state give a Manhattan distance of

> *h*[2] = 3 + 1 + 2 + 2 + 2 + 3 + 3 + 2 = 18.

As expected, neither of these overestimates the true solution cost, which is 26.

* * *

MANHATTAN DISTANCE

* * *

> ![image](images/00059.jpg)

> **Figure 3.28** A typical instance of the 8-puzzle. The solution is 26 steps long.

#### **3.6.1 The effect of heuristic accuracy on performance**

One way to characterize the quality of a heuristic is the **effective branching factor** *b*^(\*). If the total number of nodes generated by A^(\*) for a particular problem is *N* and the solution depth is *d*, then *b*^(\*) is the branching factor that a uniform tree of depth *d* would have to have in order to contain *N* + 1 nodes. Thus,

> *N* + 1 = 1 + *b*^(\*) + (*b*^(\*))² + … +(*b*^(\*))^(*d*).

* * *

EFFECTIVE BRANCHING FACTOR

* * *

For example, if A^(\*) finds a solution at depth 5 using 52 nodes, then the effective branching factor is 1.92. The effective branching factor can vary across problem instances, but usually it is fairly constant for sufficiently hard problems. (The existence of an effective branching factor follows from the result, mentioned earlier, that the number of nodes expanded by A^(\*) grows exponentially with solution depth.) Therefore, experimental measurements of *b*^(\*) on a small set of problems can provide a good guide to the heuristic’s overall usefulness. A well-designed heuristic would have a value of *b*^(\*) close to 1, allowing fairly large problems to be solved at reasonable computational cost.

To test the heuristic functions *h*[1] and *h*[2], we generated 1200 random problems with solution lengths from 2 to 24 (100 for each even number) and solved them with iterative deepening search and with A^(\*) tree search using both *h*[1] and *h*[2]. [Figure 3.29](#index_split_010.html#filepos445579) gives the average number of nodes generated by each strategy and the effective branching factor. The results suggest that *h*[2] is better than *h*[1], and is far better than using iterative deepening search. Even for small problems with *d* = 12, A^(\*) with *h*[2] is 50,000 times more efficient than uninformed iterative deepening search.

> ![image](images/00060.jpg)

> **Figure 3.29** Comparison of the search costs and effective branching factors for the ITERATIVE\-DEEPENING\-SEARCH and A^(\*) algorithms with *h*[1], *h*[2]. Data are averaged over 100 instances of the 8-puzzle for each of various solution lengths *d*.

One might ask whether *h*[2] is *always* better than *h*[1]. The answer is “Essentially, yes.” It is easy to see from the definitions of the two heuristics that, for any node *n*, *h*[2](*n*) ≥ *h*[1](*n*). We thus say that *h*[2] **dominates** *h*[1]. Domination translates directly into efficiency: A^(\*) using *h*[2] will never expand more nodes than A^(\*) using *h*[1] (except possibly for some nodes with *f*(*n*)= *C*^(\*)). The argument is simple. Recall the observation [on page 97](#index_split_010.html#filepos418642) that every node with *f*(*n*) < *C*^(\*) will surely be expanded. This is the same as saying that every node with *h*(*n*) < *C*^(\*) − *g*(*n*) will surely be expanded. But because *h*[2] is at least as big as *h*[1] for all nodes, every node that is surely expanded by A^(\*) search with *h*[2] will also surely be expanded with *h*[1], and *h*[1] might cause other nodes to be expanded as well. Hence, it is generally better to use a heuristic function with higher values, provided it is consistent and that the computation time for the heuristic is not too long.

* * *

DOMINATION

* * *

#### **3.6.2 Generating admissible heuristics from relaxed problems**

We have seen that both *h*[1] (misplaced tiles) and *h*[2] (Manhattan distance) are fairly good heuristics for the 8-puzzle and that *h*[2] is better. How might one have come up with *h*[2]? Is it possible for a computer to invent such a heuristic mechanically?

*h*[1] and *h*[2] are estimates of the remaining path length for the 8-puzzle, but they are also perfectly accurate path lengths for *simplified* versions of the puzzle. If the rules of the puzzle were changed so that a tile could move anywhere instead of just to the adjacent empty square, then *h*[1] would give the exact number of steps in the shortest solution. Similarly, if a tile could move one square in any direction, even onto an occupied square, then *h*[2] would give the exact number of steps in the shortest solution. A problem with fewer restrictions on the actions is called a **relaxed problem**. The state-space graph of the relaxed problem is a *supergraph* of the original state space because the removal of restrictions creates added edges in the graph.

* * *

RELAXED PROBLEM

* * *

Because the relaxed problem adds edges to the state space, any optimal solution in the original problem is, by definition, also a solution in the relaxed problem; but the relaxed problem may have *better* solutions if the added edges provide short cuts. Hence, *the cost of an optimal solution to a relaxed problem is an admissible heuristic for the original problem.* Furthermore, because the derived heuristic is an exact cost for the relaxed problem, it must obey the triangle inequality and is therefore **consistent** (see [page 95](#index_split_010.html#filepos412349)).

![hand](images/00006.jpg)

If a problem definition is written down in a formal language, it is possible to construct relaxed problems automatically.[^(11)](#index_split_015.html#filepos5572707) For example, if the 8-puzzle actions are described as

A tile can move from square A to square B if

> A is horizontally or vertically adjacent to B **and** B is blank,

we can generate three relaxed problems by removing one or both of the conditions:

> (a) A tile can move from square A to square B if A is adjacent to B.

> (b) A tile can move from square A to square B if B is blank.

> (c) A tile can move from square A to square B.

From (a), we can derive *h*[2] (Manhattan distance). The reasoning is that *h*[2] would be the proper score if we moved each tile in turn to its destination. The heuristic derived from (b) is discussed in Exercise 3.31. From (c), we can derive *h*[1] (misplaced tiles) because it would be the proper score if tiles could move to their intended destination in one step. Notice that it is crucial that the relaxed problems generated by this technique can be solved essentially *without search*, because the relaxed rules allow the problem to be decomposed into eight independent subproblems. If the relaxed problem is hard to solve, then the values of the corresponding heuristic will be expensive to obtain.[^(12)](#index_split_015.html#filepos5573074)

A program called ABSOLVER can generate heuristics automatically from problem definitions, using the “relaxed problem” method and various other techniques (Prieditis, 1993). ABSOLVER generated a new heuristic for the 8-puzzle that was better than any preexisting heuristic and found the first useful heuristic for the famous Rubik’s Cube puzzle.

One problem with generating new heuristic functions is that one often fails to get a single “clearly best” heuristic. If a collection of admissible heuristics *h*[1]…*h*[*m*] is available for a problem and none of them dominates any of the others, which should we choose? As it turns out, we need not make a choice. We can have the best of all worlds, by defining

> *h*(*n*) = max{*h*[1](*n*),…, *h*[*m*](*n*)}.

> ![image](images/00061.jpg)

> **Figure 3.30** A subproblem of the 8-puzzle instance given in [Figure 3.28](#index_split_010.html#filepos442646). The task is to get tiles 1, 2, 3, and 4 into their correct positions, without worrying about what happens to the other tiles.

This composite heuristic uses whichever function is most accurate on the node in question. Because the component heuristics are admissible, *h* is admissible; it is also easy to prove that *h* is consistent. Furthermore, *h* dominates all of its component heuristics.

#### **3.6.3 Generating admissible heuristics from subproblems: Pattern databases**

Admissible heuristics can also be derived from the solution cost of a **subproblem** of a given problem. For example, [Figure 3.30](#index_split_010.html#filepos453210) shows a subproblem of the 8-puzzle instance in [Figure 3.28](#index_split_010.html#filepos442646). The subproblem involves getting tiles 1, 2, 3, 4 into their correct positions. Clearly, the cost of the optimal solution of this subproblem is a lower bound on the cost of the complete problem. It turns out to be more accurate than Manhattan distance in some cases.

* * *

SUBPROBLEM

* * *

The idea behind **pattern databases** is to store these exact solution costs for every possible subproblem instance—in our example, every possible configuration of the four tiles and the blank. (The locations of the other four tiles are irrelevant for the purposes of solving the subproblem, but moves of those tiles do count toward the cost.) Then we compute an admissible heuristic *h[DB]* for each complete state encountered during a search simply by looking up the corresponding subproblem configuration in the database. The database itself is constructed by searching back[^(13)](#index_split_015.html#filepos5573399) from the goal and recording the cost of each new pattern encountered; the expense of this search is amortized over many subsequent problem instances.

* * *

PATTERN DATABASE

* * *

The choice of 1-2-3-4 is fairly arbitrary; we could also construct databases for 5-6-7-8, for 2-4-6-8, and so on. Each database yields an admissible heuristic, and these heuristics can be combined, as explained earlier, by taking the maximum value. A combined heuristic of this kind is much more accurate than the Manhattan distance; the number of nodes generated when solving random 15-puzzles can be reduced by a factor of 1000.

One might wonder whether the heuristics obtained from the 1-2-3-4 database and the 5-6-7-8 could be *added*, since the two subproblems seem not to overlap. Would this still give an admissible heuristic? The answer is no, because the solutions of the 1-2-3-4 subproblem and the 5-6-7-8 subproblem for a given state will almost certainly share some moves—it is unlikely that 1-2-3-4 can be moved into place without touching 5-6-7-8, and vice versa. But what if we don’t count those moves? That is, we record not the total cost of solving the 1-2-3-4 subproblem, but just the number of moves involving 1-2-3-4. Then it is easy to see that the sum of the two costs is still a lower bound on the cost of solving the entire problem. This is the idea behind **disjoint pattern databases**. With such databases, it is possible to solve random 15-puzzles in a few milliseconds—the number of nodes generated is reduced by a factor of 10,000 compared with the use of Manhattan distance. For 24-puzzles, a speedup of roughly a factor of a million can be obtained.

* * *

DISJOINT PATTERN DATABASES

* * *

Disjoint pattern databases work for sliding-tile puzzles because the problem can be divided up in such a way that each move affects only one subproblem—because only one tile is moved at a time. For a problem such as Rubik’s Cube, this kind of subdivision is difficult because each move affects 8 or 9 of the 26 cubies. More general ways of defining additive, admissible heuristics have been proposed that do apply to Rubik’s cube (Yang **et al.**, 2008), but they have not yielded a heuristic better than the best nonadditive heuristic for the problem.

#### **3.6.4 Learning heuristics from experience**

A heuristic function *h*(*n*) is supposed to estimate the cost of a solution beginning from the state at node n. How could an agent construct such a function? One solution was given in the preceding sections—namely, to devise relaxed problems for which an optimal solution can be found easily. Another solution is to learn from experience. “Experience” here means solving lots of 8-puzzles, for instance. Each optimal solution to an 8-puzzle problem provides examples from which *h*(*n*) can be learned. Each example consists of a state from the solution path and the actual cost of the solution from that point. From these examples, a learning algorithm can be used to construct a function *h*(*n*) that can (with luck) predict solution costs for other states that arise during search. Techniques for doing just this using neural nets, decision trees, and other methods are demonstrated in [Chapter 18](#index_split_015.html#filepos2753020). (The reinforcement learning methods described in [Chapter 21](#index_split_015.html#filepos3262268) are also applicable.)

Inductive learning methods work best when supplied with **features** of a state that are relevant to predicting the state’s value, rather than with just the raw state description. For example, the feature “number of misplaced tiles” might be helpful in predicting the actual distance of a state from the goal. Let’s call this feature *x*[1](*n*). We could take 100 randomly generated 8-puzzle configurations and gather statistics on their actual solution costs. We might find that when *x*[1](*n*) is 5, the average solution cost is around 14, and so on. Given these data, the value of *x*[1] can be used to predict *h*(*n*). Of course, we can use several features. A second feature *x*[2](*n*) might be “number of pairs of adjacent tiles that are not adjacent in the goal state.” How should *x*[1](*n*) and *x*[2](*n*) be combined to predict *h*(*n*)? A common approach is to use a linear combination:

> *h*(*n*) = *c*[1]*x*[1](*n*) + *c*[2]*x*[2](*n*).

* * *

FEATURE

* * *

The constants *c*[1] and *c*[2] are adjusted to give the best fit to the actual data on solution costs. One expects both *c*[1] and *c*[2] to be positive because misplaced tiles and incorrect adjacent pairs make the problem harder to solve. Notice that this heuristic does satisfy the condition that *h*(*n*) = 0 for goal states, but it is not necessarily admissible or consistent.

### 3.7 SUMMARY

This chapter has introduced methods that an agent can use to select actions in environments that are deterministic, observable, static, and completely known. In such cases, the agent can construct sequences of actions that achieve its goals; this process is called **search**.

> • Before an agent can start searching for solutions, a **goal** must be identified and a well-defined **problem** must be formulated.

> • A problem consists of five parts: the **initial state**, a set of **actions**, a **transition model** describing the results of those actions, a **goal test** function, and a **path cost** function. The environment of the problem is represented by a **state space**. A **path** through the state space from the initial state to a goal state is a **solution**.

> • Search algorithms treat states and actions as **atomic**: they do not consider any internal structure they might possess.

> • A general TREE\-SEARCH algorithm considers all possible paths to find a solution, whereas a GRAPH\-SEARCH algorithm avoids consideration of redundant paths.

> • Search algorithms are judged on the basis of **completeness**, **optimality**, **time complexity**, and **space complexity**. Complexity depends on *b*, the branching factor in the state space, and *d*, the depth of the shallowest solution.

> • **Uninformed search** methods have access only to the problem definition. The basic algorithms are as follows:

> **– Breadth-first search** expands the shallowest nodes first; it is complete, optimal for unit step costs, but has exponential space complexity.

> **– Uniform-cost search** expands the node with lowest path cost, *g*(*n*), and is optimal for general step costs.

> **– Depth-first search** expands the deepest unexpanded node first. It is neither complete nor optimal, but has linear space complexity. **Depth-limited search** adds a depth bound.

> **– Iterative deepening search** calls depth-first search with increasing depth limits until a goal is found. It is complete, optimal for unit step costs, has time complexity comparable to breadth-first search, and has linear space complexity.

> **– Bidirectional search** can enormously reduce time complexity, but it is not always applicable and may require too much space.

> • **Informed search** methods may have access to a **heuristic** function *h*(*n*) that estimates the cost of a solution from *n*.

> **–** The generic **best-first search** algorithm selects a node for expansion according to an **evaluation function**.

> **– Greedy best-first search** expands nodes with minimal *h*(*n*). It is not optimal but is often efficient.

> **– A**^(\*) **search** expands nodes with minimal *f*(*n*) = *g*(*n*)+ *h*(*n*). A^(\*) is complete and optimal, provided that *h*(*n*) is admissible (for TREE\-SEARCH) or consistent (for GRAPH\-SEARCH). The space complexity of A^(\*) is still prohibitive.

> **– RBFS** (recursive best-first search) and **SMA**^(\*) (simplified memory-bounded A^(\*)) are robust, optimal search algorithms that use limited amounts of memory; given enough time, they can solve problems that A^(\*) cannot solve because it runs out of memory.

> • The performance of heuristic search algorithms depends on the quality of the heuristic function. One can sometimes construct good heuristics by relaxing the problem definition, by storing precomputed solution costs for subproblems in a pattern database, or by learning from experience with the problem class.

### BIBLIOGRAPHICAL AND HISTORICAL NOTES

The topic of state-space search originated in more or less its current form in the early years of AI. Newell and Simon’s work on the Logic Theorist (1957) and GPS (1961) led to the establishment of search algorithms as the primary weapons in the armory of 1960s AI researchers and to the establishment of problem solving as the canonical AI task. Work in operations research by Richard Bellman (1957) showed the importance of additive path costs in simplifying optimization algorithms. The text on *Automated Problem Solving* by Nils Nilsson (1971) established the area on a solid theoretical footing.

Most of the state-space search problems analyzed in this chapter have a long history in the literature and are less trivial than they might seem. The missionaries and cannibals problem used in Exercise 3.9 was analyzed in detail by Amarel (1968). It had been considered earlier—in AI by Simon and Newell (1961) and in operations research by Bellman and Dreyfus (1962).

The 8-puzzle is a smaller cousin of the 15-puzzle, whose history is recounted at length by Slocum and Sonneveld (2006). It was widely believed to have been invented by the famous American game designer Sam Loyd, based on his claims to that effect from 1891 onward (Loyd, 1959). Actually it was invented by Noyes Chapman, a postmaster in Canastota, New York, in the mid-1870s. (Chapman was unable to patent his invention, as a generic patent covering sliding blocks with letters, numbers, or pictures was granted to Ernest Kinsey in 1878.) It quickly attracted the attention of the public and of mathematicians (Johnson and Story, 1879; Tait, 1880). The editors of the *American Journal of Mathematics* stated, “The ‘15’ puzzle for the last few weeks has been prominently before the American public, and may safely be said to have engaged the attention of nine out of ten persons of both sexes and all ages and conditions of the community.” Ratner and Warmuth (1986) showed that the general *n* × *n* version of the 15-puzzle belongs to the class of NP-complete problems.

The 8-queens problem was first published anonymously in the German chess magazine *Schach* in 1848; it was later attributed to one Max Bezzel. It was republished in 1850 and at that time drew the attention of the eminent mathematician Carl Friedrich Gauss, who attempted to enumerate all possible solutions; initially he found only 72, but eventually he found the correct answer of 92, although Nauck published all 92 solutions first, in 1850. Netto (1901) generalized the problem to *n* queens, and Abramson and Yung (1989) found an *O*(*n*) algorithm.

Each of the real-world search problems listed in the chapter has been the subject of a good deal of research effort. Methods for selecting optimal airline flights remain proprietary for the most part, but Carl de Marcken (personal communication) has shown that airline ticket pricing and restrictions have become so convoluted that the problem of selecting an optimal flight is formally *undecidable*. The traveling-salesperson problem is a standard combinatorial problem in theoretical computer science (Lawler **et al.**, 1992). Karp (1972) proved the TSP to be NP-hard, but effective heuristic approximation methods were developed (Lin and Kernighan, 1973). Arora (1998) devised a fully polynomial approximation scheme for Euclidean TSPs. VLSI layout methods are surveyed by Shahookar and Mazumder (1991), and many layout optimization papers appear in VLSI journals. Robotic navigation and assembly problems are discussed in [Chapter 25](#index_split_015.html#filepos3777962).

Uninformed search algorithms for problem solving are a central topic of classical computer science (Horowitz and Sahni, 1978) and operations research (Dreyfus, 1969). Breadth-first search was formulated for solving mazes by Moore (1959). The method of **dynamic programming** (Bellman, 1957; Bellman and Dreyfus, 1962), which systematically records solutions for all subproblems of increasing lengths, can be seen as a form of breadth-first search on graphs. The two-point shortest-path algorithm of Dijkstra (1959) is the origin of uniform-cost search. These works also introduced the idea of explored and frontier sets (closed and open lists).

A version of iterative deepening designed to make efficient use of the chess clock was first used by Slate and Atkin (1977) in the CHESS 4.5 gameplaying program. Martelli’s algorithm B (1977) includes an iterative deepening aspect and also dominates A^(\*)’s worst-case performance with admissible but inconsistent heuristics. The iterative deepening technique came to the fore in work by Korf (1985a). Bidirectional search, which was introduced by Pohl (1971), can also be effective in some cases.

The use of heuristic information in problem solving appears in an early paper by Simon and Newell (1958), but the phrase “heuristic search” and the use of heuristic functions that estimate the distance to the goal came somewhat later (Newell and Ernst, 1965; Lin, 1965). Doran and Michie (1966) conducted extensive experimental studies of heuristic search. Although they analyzed path length and “penetrance” (the ratio of path length to the total number of nodes examined so far), they appear to have ignored the information provided by the path cost *g*(*n*). The A^(\*) algorithm, incorporating the current path cost into heuristic search, was developed by Hart, Nilsson, and Raphael (1968), with some later corrections (Hart **et al.**, 1972). Dechter and Pearl (1985) demonstrated the optimal efficiency of A^(\*).

The original A^(\*) paper introduced the consistency condition on heuristic functions. The monotone condition was introduced by Pohl (1977) as a simpler replacement, but Pearl (1984) showed that the two were equivalent.

Pohl (1977) pioneered the study of the relationship between the error in heuristic functions and the time complexity of A^(\*). Basic results were obtained for tree search with unit step costs and a single goal node (Pohl, 1977; Gaschnig, 1979; Huyn **et al.**, 1980; Pearl, 1984) and with multiple goal nodes (Dinh **et al.**, 2007). The “effective branching factor” was proposed by Nilsson (1971) as an empirical measure of the efficiency; it is equivalent to assuming a time cost of *O*((*b*^(\*))^(*d*)). For tree search applied to a graph, Korf **et al.** (2001) argue that the time cost is better modeled as *O*(*b*^(*d*−*k*)), where *k* depends on the heuristic accuracy; this analysis has elicited some controversy, however. For graph search, Helmert and Röger (2008) noted that several well-known problems contained exponentially many nodes on optimal solution paths, implying exponential time complexity for A^(\*) even with constant absolute error in *h*.

There are many variations on the A^(\*) algorithm. Pohl (1973) proposed the use of *dynamic weighting*, which uses a weighted sum *f*[*w*](*n*)= *w*[*g*]*g*(*n*)+ *w*[*h*]*h*(*n*) of the current path length and the heuristic function as an evaluation function, rather than the simple sum *f*(*n*) = *g*(*n*) + *h*(*n*) used in A^(\*). The weights *w*[*g*] and *w*[*h*] are adjusted dynamically as the search progresses. Pohl’s algorithm can be shown to be ε-admissible—that is, guaranteed to find solutions within a factor 1 + ε of the optimal solution, where ε is a parameter supplied to the algorithm. The same property is exhibited by the ![image](images/00062.jpg)algorithm (Pearl, 1984), which can select any node from the frontier provided its *f*\-cost is within a factor 1 + ε of the lowest-*f*\-cost frontier node. The selection can be done so as to minimize search cost.

Bidirectional versions of A^(\*) have been investigated; a combination of bidirectional A^(\*) and known landmarks was used to efficiently find driving routes for Microsoft’s online map service (Goldberg **et al.**, 2006). After caching a set of paths between landmarks, the algorithm can find an optimal path between any pair of points in a 24 million point graph of the United States, searching less than 0.1% of the graph. Others approaches to bidirectional search include a breadth-first search backward from the goal up to a fixed depth, followed by a forward IDA^(\*) search (Dillenburg and Nelson, 1994; Manzini, 1995).

A\* and other state-space search algorithms are closely related to the *branch-and-bound* techniques that are widely used in operations research (Lawler and Wood, 1966). The relationships between state-space search and branch-and-bound have been investigated in depth (Kumar and Kanal, 1983; Nau **et al.**, 1984; Kumar **et al.**, 1988). Martelli and Montanari (1978) demonstrate a connection between dynamic programming (see [Chapter 17](#index_split_015.html#filepos2562268)) and certain types of state-space search. Kumar and Kanal (1988) attempt a “grand unification” of heuristic search, dynamic programming, and branch-and-bound techniques under the name of CDP—the “composite decision process.”

Because computers in the late 1950s and early 1960s had at most a few thousand words of main memory, memory-bounded heuristic search was an early research topic. The Graph Traverser (Doran and Michie, 1966), one of the earliest search programs, commits to an operator after searching best-first up to the memory limit. IDA^(\*) (Korf, 1985a, 1985b) was the first widely used optimal, memory-bounded heuristic search algorithm, and a large number of variants have been developed. An analysis of the efficiency of IDA^(\*) and of its difficulties with real-valued heuristics appears in Patrick **et al.** (1992).

RBFS (Korf, 1993) is actually somewhat more complicated than the algorithm shown in [Figure 3.26](#index_split_010.html#filepos427548), which is closer to an independently developed algorithm called **iterative expansion** (Russell, 1992). RBFS uses a lower bound as well as the upper bound; the two algorithms behave identically with admissible heuristics, but RBFS expands nodes in best-first order even with an inadmissible heuristic. The idea of keeping track of the best alternative path appeared earlier in Bratko’s (1986) elegant Prolog implementation of A^(\*) and in the DTA^(\*)algorithm (Russell and Wefald, 1991). The latter work also discusses metalevel state spaces and metalevel learning.

* * *

ITERATIVE EXPANSION

* * *

The MA^(\*) algorithm appeared in Chakrabarti **et al.** (1989). SMA^(\*), or Simplified MA^(\*), emerged from an attempt to implement MA^(\*) as a comparison algorithm for IE (Russell, 1992). Kaindl and Khorsand (1994) have applied SMA^(\*) to produce a bidirectional search algorithm that is substantially faster than previous algorithms. Korf and Zhang (2000) describe a divide-and-conquer approach, and Zhou and Hansen (2002) introduce memory-bounded A^(\*) graph search and a strategy for switching to breadth-first search to increase memory-efficiency (Zhou and Hansen, 2006). Korf (1995) surveys memory-bounded search techniques.

The idea that admissible heuristics can be derived by problem relaxation appears in the seminal paper by Held and Karp (1970), who used the minimum-spanning-tree heuristic to solve the TSP. (See Exercise 3.30.)

The automation of the relaxation process was implemented successfully by Prieditis (1993), building on earlier work with Mostow (Mostow and Prieditis, 1989). Holte and Hernadvolgyi (2001) describe more recent steps towards automating the process. The use of pattern databases to derive admissible heuristics is due to Gasser (1995) and Culberson and Schaeffer (1996, 1998); disjoint pattern databases are described by Korf and Felner (2002); a similar method using symbolic patterns is due to Edelkamp (2009). Felner **et al.** (2007) show how to compress pattern databases to save space. The probabilistic interpretation of heuristics was investigated in depth by Pearl (1984) and Hansson and Mayer (1989).

By far the most comprehensive source on heuristics and heuristic search algorithms is Pearl’s (1984) *Heuristics* text. This book provides especially good coverage of the wide variety of offshoots and variations of A^(\*), including rigorous proofs of their formal properties. Kanal and Kumar (1988) present an anthology of important articles on heuristic search, and Rayward-Smith **et al.** (1996) cover approaches from Operations Research. Papers about new search algorithms—which, remarkably, continue to be discovered—appear in journals such as *Artificial Intelligence* and *Journal of the ACM*.

The topic of **parallel search** algorithms was not covered in the chapter, partly because it requires a lengthy discussion of parallel computer architectures. Parallel search became a popular topic in the 1990s in both AI and theoretical computer science (Mahanti and Daniels, 1993; Grama and Kumar, 1995; Crauser **et al.**, 1998) and is making a comeback in the era of new multicore and cluster architectures (Ralphs **et al.**, 2004; Korf and Schultze, 2005). Also of increasing importance are search algorithms for very large graphs that require disk storage (Korf, 2008).

* * *

PARALLEL SEARCH

* * *

### EXERCISES

**3.1** Explain why problem formulation must follow goal formulation.

**3.2** Your goal is to navigate a robot out of a maze. The robot starts in the center of the maze facing north. You can turn the robot to face north, east, south, or west. You can direct the robot to move forward a certain distance, although it will stop before hitting a wall.

> **a**. Formulate this problem. How large is the state space?

> **b**. In navigating a maze, the only place we need to turn is at the intersection of two or more corridors. Reformulate this problem using this observation. How large is the state space now?

> **c**. From each point in the maze, we can move in any of the four directions until we reach a turning point, and this is the only action we need to do. Reformulate the problem using these actions. Do we need to keep track of the robot’s orientation now?

> **d**. In our initial description of the problem we already abstracted from the real world, restricting actions and removing details. List three such simplifications we made.

**3.3** Suppose two friends live in different cities on a map, such as the Romania map shown in [Figure 3.2](#index_split_010.html#filepos318111). On every turn, we can simultaneously move each friend to a neighboring city on the map. The amount of time needed to move from city *i* to neighbor *j* is equal to the road distance *d*(*i, j*) between the cities, but on each turn the friend that arrives first must wait until the other one arrives (and calls the first on his/her cell phone) before the next turn can begin. We want the two friends to meet as quickly as possible.

> **a**. Write a detailed formulation for this search problem. (You will find it helpful to define some formal notation here.)

> **b**. Let *D*(*i, j*) be the straight-line distance between cities *i* and *j*. Which of the following heuristic functions are admissible? (*i*) *D*(*i, j*); (ii) 2 ⋅ *D*(*i, j*); (iii) *D*(*i, j*)/2.

> **c**. Are there completely connected maps for which no solution exists?

> **d**. Are there maps in which all solutions require one friend to visit the same city twice?

**3.4** Show that the 8-puzzle states are divided into two disjoint sets, such that any state is reachable from any other state in the same set, while no state is reachable from any state in the other set. (*Hint*: See Berlekamp **et al.** (1982).) Devise a procedure to decide which set a given state is in, and explain why this is useful for generating random states.

**3.5** Consider the *n*\-queens problem using the “efficient” incremental formulation given [on page 72](#index_split_010.html#filepos331763). Explain why the state space has at least ![equ](images/00063.jpg)states and estimate the largest *n* for which exhaustive exploration is feasible. (*Hint*: Derive a lower bound on the branching factor by considering the maximum number of squares that a queen can attack in any column.)

**3.6** Give a complete problem formulation for each of the following. Choose a formulation that is precise enough to be implemented.

> **a.** Using only four colors, you have to color a planar map in such a way that no two adjacent regions have the same color.

> **b.** A 3-foot-tall monkey is in a room where some bananas are suspended from the 8-foot ceiling. He would like to get the bananas. The room contains two stackable, movable, climbable 3-foot-high crates.

> ![image](images/00064.jpg)

> **Figure 3.31** A scene with polygonal obstacles. *S* and *G* are the start and goal states.

> **c**. You have a program that outputs the message “illegal input record” when fed a certain file of input records. You know that processing of each record is independent of the other records. You want to discover what record is illegal.

> **d**. You have three jugs, measuring 12 gallons, 8 gallons, and 3 gallons, and a water faucet. You can fill the jugs up or empty them out from one to another or onto the ground. You need to measure out exactly one gallon.

**3.7** Consider the problem of finding the shortest path between two points on a plane that has convex polygonal obstacles as shown in [Figure 3.31](#index_split_010.html#filepos487681). This is an idealization of the problem that a robot has to solve to navigate in a crowded environment.

> **a**. Suppose the state space consists of all positions (*x*, *y*) in the plane. How many states are there? How many paths are there to the goal?

> **b**. Explain briefly why the shortest path from one polygon vertex to any other in the scene must consist of straight-line segments joining some of the vertices of the polygons. Define a good state space now. How large is this state space?

> **c**. Define the necessary functions to implement the search problem, including an ACTIONS function that takes a vertex as input and returns a set of vectors, each of which maps the current vertex to one of the vertices that can be reached in a straight line. (Do not forget the neighbors on the same polygon.) Use the straight-line distance for the heuristic function.

> **d**. Apply one or more of the algorithms in this chapter to solve a range of problems in the domain, and comment on their performance.

![radio](images/00004.jpg)

**3.8** [On page 68](#index_split_010.html#filepos318104), we said that we would not consider problems with negative path costs. In this exercise, we explore this decision in more depth.

> **a**. Suppose that actions can have arbitrarily large negative costs; explain why this possibility would force any optimal algorithm to explore the entire state space.

> **b**. Does it help if we insist that step costs must be greater than or equal to some negative constant *c*? Consider both trees and graphs.

> **c**. Suppose that a set of actions forms a loop in the state space such that executing the set in some order results in no net change to the state. If all of these actions have negative cost, what does this imply about the optimal behavior for an agent in such an environment?

> **d**. One can easily imagine actions with high negative cost, even in domains such as route finding. For example, some stretches of road might have such beautiful scenery as to far outweigh the normal costs in terms of time and fuel. Explain, in precise terms, within the context of state-space search, why humans do not drive around scenic loops indefinitely, and explain how to define the state space and actions for route finding so that artificial agents can also avoid looping.

> **e**. Can you think of a real domain in which step costs are such as to cause looping?

**3.9** The **missionaries and cannibals** problem is usually stated as follows. Three missionaries and three cannibals are on one side of a river, along with a boat that can hold one or two people. Find a way to get everyone to the other side without ever leaving a group of missionaries in one place outnumbered by the cannibals in that place. This problem is famous in AI because it was the subject of the first paper that approached problem formulation from an analytical viewpoint (Amarel, 1968).

> **a**. Formulate the problem precisely, making only those distinctions necessary to ensure a valid solution. Draw a diagram of the complete state space.

> **b**. Implement and solve the problem optimally using an appropriate search algorithm. Is it a good idea to check for repeated states?

> **c**. Why do you think people have a hard time solving this puzzle, given that the state space is so simple?

![radio](images/00004.jpg)

**3.10** Define in your own words the following terms: state, state space, search tree, search node, goal, action, transition model, and branching factor.

**3.11** What’s the difference between a world state, a state description, and a search node? Why is this distinction useful?

**3.12** An action such as *Go(Sibiu)* really consists of a long sequence of finer-grained actions: turn on the car, release the brake, accelerate forward, *etc.* Having composite actions of this kind reduces the number of steps in a solution sequence, thereby reducing the search time. Suppose we take this to the logical extreme, by making super-composite actions out of every possible sequence of *Go* actions. Then every problem instance is solved by a single super-composite action, such as *Go(Sibiu)Go(Rimnicu Vilcea)Go(Pitesti)Go(Bucharest)*. Explain how search would work in this formulation. Is this a practical approach for speeding up problem solving?

**3.13** Prove that GRAPH\-SEARCH satisfies the graph separation property illustrated in [Figure 3.9](#index_split_010.html#filepos356410). (*Hint*: Begin by showing that the property holds at the start, then show that if it holds before an iteration of the algorithm, it holds afterwards.) Describe a search algorithm that violates the property.

> ![image](images/00065.jpg)

> **Figure 3.32** The track pieces in a wooden railway set; each is labeled with the number of copies in the set. Note that curved pieces and “fork” pieces (“switches” or “points”) can be flipped over so they can curve in either direction. Each curve subtends 45 degrees.

**3.14** Which of the following are true and which are false? Explain your answers.

> **a**. Depth-first search always expands at least as many nodes as A^(\*) search with an admissible heuristic.

> **b**. *h*(*n*) = 0 is an admissible heuristic for the 8-puzzle.

> **c**. A^(\*) is of no use in robotics because percepts, states, and actions are continuous.

> **d**. Breadth-first search is complete even if zero step costs are allowed.

> **e**. Assume that a rook can move on a chessboard any number of squares in a straight line, vertically or horizontally, but cannot jump over other pieces. Manhattan distance is an admissible heuristic for the problem of moving the rook from square A to square B in the smallest number of moves.

**3.15** Consider a state space where the start state is number 1 and each state *k* has two successors: numbers 2*k* and 2*k* + 1.

> **a**. Draw the portion of the state space for states 1 to 15.

> **b**. Suppose the goal state is 11. List the order in which nodes will be visited for breadth-first search, depth-limited search with limit 3, and iterative deepening search.

> **c**. How well would bidirectional search work on this problem? What is the branching factor in each direction of the bidirectional search?

> **d**. Does the answer to (c) suggest a reformulation of the problem that would allow you to solve the problem of getting from state 1 to a given goal state with almost no search?

> **e**. Call the action going from *k* to 2*k* Left, and the action going to 2*k* + 1 Right. Can you find an algorithm that outputs the solution to this problem without any search at all?

**3.16** A basic wooden railway set contains the pieces shown in [Figure 3.32](#index_split_010.html#filepos495313). The task is to connect these pieces into a railway that has no overlapping tracks and no loose ends where a train could run off onto the floor.

> **a**. Suppose that the pieces fit together *exactly* with no slack. Give a precise formulation of the task as a search problem.

> **b**. Identify a suitable uninformed search algorithm for this task and explain your choice.

> **c**. Explain why removing any one of the “fork” pieces makes the problem unsolvable.

> **d**. Give an upper bound on the total size of the state space defined by your formulation. (*Hint*: think about the maximum branching factor for the construction process and the maximum depth, ignoring the problem of overlapping pieces and loose ends. Begin by pretending that every piece is unique.)

**3.17** [On page 90](#index_split_010.html#filepos394488), we mentioned **iterative lengthening search**, an iterative analog of uniform cost search. The idea is to use increasing limits on path cost. If a node is generated whose path cost exceeds the current limit, it is immediately discarded. For each new iteration, the limit is set to the lowest path cost of any node discarded in the previous iteration.

> **a**. Show that this algorithm is optimal for general path costs.

> **b**. Consider a uniform tree with branching factor *b*, solution depth *d*, and unit step costs. How many iterations will iterative lengthening require?

> **c**. Now consider step costs drawn from the continuous range \[ε, 1\],where 0 < ε < 1. How many iterations are required in the worst case?

> **d**. Implement the algorithm and apply it to instances of the 8-puzzle and traveling salesperson problems. Compare the algorithm’s performance to that of uniform-cost search, and comment on your results.

![radio](images/00004.jpg)

**3.18** Describe a state space in which iterative deepening search performs much worse than depth-first search (for example, *O*(*n*²) vs. *O*(*n*)).

**3.19** Write a program that will take as input two Web page URLs and find a path of links from one to the other. What is an appropriate search strategy? Is bidirectional search a good idea? Could a search engine be used to implement a predecessor function?

![radio](images/00004.jpg)

**3.20** Consider the vacuum-world problem defined in [Figure 2.2](#index_split_009.html#filepos194440).

> **a**. Which of the algorithms defined in this chapter would be appropriate for this problem? Should the algorithm use tree search or graph search?

> **b**. Apply your chosen algorithm to compute an optimal sequence of actions for a 3 × 3 world whose initial state has dirt in the three top squares and the agent in the center.

> **c**. Construct a search agent for the vacuum world, and evaluate its performance in a set of 3 × 3 worlds with probability 0.2 of dirt in each square. Include the search cost as well as path cost in the performance measure, using a reasonable exchange rate.

> **d**. Compare your best search agent with a simple randomized reflex agent that sucks if there is dirt and otherwise moves randomly.

> **e**. Consider what would happen if the world were enlarged to *n* × *n*. How does the performance of the search agent and of the reflex agent vary with *n*?

![radio](images/00004.jpg)

**3.21** Prove each of the following statements, or give a counterexample:

> **a**. Breadth-first search is a special case of uniform-cost search.

> **b**. Depth-first search is a special case of best-first tree search.

> **c**. Uniform-cost search is a special case of A^(\*) search.

**3.22** Compare the performance of A^(\*) and RBFS on a set of randomly generated problems in the 8-puzzle (with Manhattan distance) and TSP (with MST—see Exercise 3.30) domains. Discuss your results. What happens to the performance of RBFS when a small random number is added to the heuristic values in the 8-puzzle domain?

![radio](images/00004.jpg)

**3.23** Trace the operation of A^(\*) search applied to the problem of getting to Bucharest from Lugoj using the straight-line distance heuristic. That is, show the sequence of nodes that the algorithm will consider and the *f*, *g*, and *h* score for each node.

**3.24** Devise a state space in which A^(\*) using GRAPH\-SEARCH returns a suboptimal solution with an *h*(*n*) function that is admissible but inconsistent.

![radio](images/00004.jpg)

**3.25** The **heuristic path algorithm** (Pohl, 1977) is a best-first search in which the evaluation function is *f*(*n*) = (2 − *w*)*g*(*n*) + *wh*(*n*). For what values of *w* is this complete? For what values is it optimal, assuming that *h* is admissible? What kind of search does this perform for *w* = 0, *w* = 1, and *w* = 2?

* * *

HEURISTIC PATH ALGORITHM

* * *

**3.26** Consider the unbounded version of the regular 2D grid shown in [Figure 3.9](#index_split_010.html#filepos356410). The start state is at the origin, (0,0), and the goal state is at (*x*, *y*).

> **a**. What is the branching factor b in this state space?

> **b**. How many distinct states are there at depth *k* (for *k* > 0)?

> **c**. What is the maximum number of nodes expanded by breadth-first tree search?

> **d**. What is the maximum number of nodes expanded by breadth-first graph search?

> **e**. Is *h* = |*u* − *x*| + |*v* − *y*| an admissible heuristic for a state at (*u, v*)? Explain.

> **f**. How many nodes are expanded by A^(\*) graph search using *h*?

> **g**. Does *h* remain admissible if some links are removed?

> **h**. Does *h* remain admissible if some links are added between nonadjacent states?

**3.27** *n* vehicles occupy squares (1, 1) through (*n*, 1) (i.e., the bottom row) of an *n* × *n* grid. The vehicles must be moved to the top row but in reverse order; so the vehicle *i* that starts in (*i*, 1) must end up in (*n* − *i* + 1, *n*). On each time step, every one of the *n* vehicles can move one square up, down, left, or right, or stay put; but if a vehicle stays put, one other adjacent vehicle (but not more than one) can hop over it. Two vehicles cannot occupy the same square.

> **a**. Calculate the size of the state space as a function of *n*.

> **b**. Calculate the branching factor as a function of *n*.

> **c**. Suppose that vehicle i is at (*x*[*i*],*y*[*i*]); write a nontrivial admissible heuristic *h*[*i*] for the number of moves it will require to get to its goal location (*n* − *i* + 1, *n*), assuming no other vehicles are on the grid.

> **d**. Which of the following heuristics are admissible for the problem of moving all *n* vehicles to their destinations? Explain.

> (*i*) ![equ](images/00066.jpg)

> (ii) max{*h*[1],…,*h*[*n*]}.

> (iii) min{*h*[1],…,*h*[*n*]}.

**3.28** Invent a heuristic function for the 8-puzzle that sometimes overestimates, and show how it can lead to a suboptimal solution on a particular problem. (You can use a computer to help if you want.) Prove that if *h* never overestimates by more than *c*, A^(\*) using *h* returns a solution whose cost exceeds that of the optimal solution by no more than *c*.

**3.29** Prove that if a heuristic is consistent, it must be admissible. Construct an admissible heuristic that is not consistent.

**3.30** The traveling salesperson problem (TSP) can be solved with the minimum-spanning-tree (MST) heuristic, which estimates the cost of completing a tour, given that a partial tour has already been constructed. The MST cost of a set of cities is the smallest sum of the link costs of any tree that connects all the cities.

> **a**. Show how this heuristic can be derived from a relaxed version of the TSP.

> **b**. Show that the MST heuristic dominates straight-line distance.

> **c**. Write a problem generator for instances of the TSP where cities are represented by random points in the unit square.

> **d**. Find an efficient algorithm in the literature for constructing the MST, and use it with A^(\*) graph search to solve instances of the TSP.

![radio](images/00004.jpg)

**3.31** [On page 105](#index_split_010.html#filepos448560), we defined the relaxation of the 8-puzzle in which a tile can move from square A to square B if B is blank. The exact solution of this problem defines **Gaschnig’s heuristic** (Gaschnig, 1979). Explain why Gaschnig’s heuristic is at least as accurate as *h*[1] (misplaced tiles), and show cases where it is more accurate than both *h*[1] and *h*[2] (Manhattan distance). Explain how to calculate Gaschnig’s heuristic efficiently.

**3.32** We gave two simple heuristics for the 8-puzzle: Manhattan distance and misplaced tiles. Several heuristics in the literature purport to improve on this—see, for example, Nilsson (1971), Mostow and Prieditis (1989), and Hansson **et al.** (1992). Test these claims by implementing the heuristics and comparing the performance of the resulting algorithms.

![radio](images/00004.jpg)

## **4 BEYOND CLASSICAL SEARCH**

> *In which we relax the simplifying assumptions of the previous chapter, thereby getting closer to the real world.*

[Chapter 3](#index_split_000.html#filepos301685) addressed a single category of problems: observable, deterministic, known environments where the solution is a sequence of actions. In this chapter, we look at what happens when these assumptions are relaxed. We begin with a fairly simple case: Sections 4.1 and 4.2 cover algorithms that perform purely **local search** in the state space, evaluating and modifying one or more current states rather than systematically exploring paths from an initial state. These algorithms are suitable for problems in which all that matters is the solution state, not the path cost to reach it. The family of local search algorithms includes methods inspired by statistical physics (**simulated annealing**) and evolutionary biology (**genetic algorithms**).

Then, in Sections 4.3–4.4, we examine what happens when we relax the assumptions of determinism and observability. The key idea is that if an agent cannot predict exactly what percept it will receive, then it will need to consider what to do under each **contingency** that its percepts may reveal. With partial observability, the agent will also need to keep track of the states it might be in.

Finally, [Section 4.5](#index_split_000.html#filepos605406) investigates **online search**, in which the agent is faced with a state space that is initially unknown and must be explored.

### 4.1 LOCAL SEARCH ALGORITHMS AND OPTIMIZATION PROBLEMS

The search algorithms that we have seen so far are designed to explore search spaces systematically. This systematicity is achieved by keeping one or more paths in memory and by recording which alternatives have been explored at each point along the path. When a goal is found, the *path* to that goal also constitutes a *solution* to the problem. In many problems, however, the path to the goal is irrelevant. For example, in the 8-queens problem (see [page 71](#index_split_010.html#filepos327986)), what matters is the final configuration of queens, not the order in which they are added. The same general property holds for many important applications such as integrated-circuit design, factory-floor layout, job-shop scheduling, automatic programming, telecommunications network optimization, vehicle routing, and portfolio management.

If the path to the goal does not matter, we might consider a different class of algorithms, ones that do not worry about paths at all. **Local search** algorithms operate using a single **current node** (rather than multiple paths) and generally move only to neighbors of that node. Typically, the paths followed by the search are not retained. Although local search algorithms are not systematic, they have two key advantages: (1) they use very little memory—usually a constant amount; and (2) they can often find reasonable solutions in large or infinite (continuous) state spaces for which systematic algorithms are unsuitable.

* * *

LOCAL SEARCH

* * *

* * *

CURRENT NODE

* * *

In addition to finding goals, local search algorithms are useful for solving pure **optimization problems**, in which the aim is to find the best state according to an **objective function**. Many optimization problems do not fit the “standard” search model introduced in [Chapter 3](#index_split_000.html#filepos301685). For example, nature provides an objective function—reproductive fitness—that Darwinian evolution could be seen as attempting to optimize, but there is no “goal test” and no “path cost” for this problem.

* * *

OPTIMIZATION PROBLEM

* * *

* * *

OBJECTIVE FUNCTION

* * *

To understand local search, we find it useful to consider the **state-space landscape** (as in [Figure 4.1](#index_split_011.html#filepos519331)). A landscape has both “location” (defined by the state) and “elevation” (defined by the value of the heuristic cost function or objective function). If elevation corresponds to cost, then the aim is to find the lowest valley—a **global minimum**; if elevation corresponds to an objective function, then the aim is to find the highest peak—a **global maximum**. (You can convert from one to the other just by inserting a minus sign.) Local search algorithms explore this landscape. A **complete** local search algorithm always finds a goal if one exists; an **optimal** algorithm always finds a global minimum/maximum.

* * *

STATE-SPACE LANDSCAPE

* * *

* * *

GLOBAL MINIMUM

* * *

* * *

GLOBAL MAXIMUM

* * *

> ![image](images/00067.jpg)

> **Figure 4.1** A one-dimensional state-space landscape in which elevation corresponds to the objective function. The aim is to find the global maximum. Hill-climbing search modifies the current state to try to improve it, as shown by the arrow. The various topographic features are defined in the text.

> ![image](images/00068.jpg)

> **Figure 4.2** The hill-climbing search algorithm, which is the most basic local search technique. At each step the current node is replaced by the best neighbor; in this version, that means the neighbor with the highest VALUE, but if a heuristic cost estimate h is used, we would find the neighbor with the lowest *h*.

#### **4.1.1 Hill-climbing search**

The **hill-climbing** search algorithm (**steepest-ascent** version) is shown in [Figure 4.2](#index_split_011.html#filepos519868). It is simply a loop that continually moves in the direction of increasing value—that is, uphill. It terminates when it reaches a “peak” where no neighbor has a higher value. The algorithm does not maintain a search tree, so the data structure for the current node need only record the state and the value of the objective function. Hill climbing does not look ahead beyond the immediate neighbors of the current state. This resembles trying to find the top of Mount Everest in a thick fog while suffering from amnesia.

* * *

HILL CLIMBING

* * *

* * *

STEEPEST ASCENT

* * *

To illustrate hill climbing, we will use the **8-queens problem** introduced [on page 71](#index_split_010.html#filepos327986). Local search algorithms typically use a **complete-state formulation**, where each state has 8 queens on the board, one per column. The successors of a state are all possible states generated by moving a single queen to another square in the same column (so each state has 8 × 7 = 56 successors). The heuristic cost function h is the number of pairs of queens that are attacking each other, either directly or indirectly. The global minimum of this function is zero, which occurs only at perfect solutions. [Figure 4.3](#index_split_011.html#filepos524086)(a) shows a state with *h* = 17. The figure also shows the values of all its successors, with the best successors having *h* = 12. Hill-climbing algorithms typically choose randomly among the set of best successors if there is more than one.

Hill climbing is sometimes called **greedy local search** because it grabs a good neighbor state without thinking ahead about where to go next. Although greed is considered one of the seven deadly sins, it turns out that greedy algorithms often perform quite well. Hill climbing often makes rapid progress toward a solution because it is usually quite easy to improve a bad state. For example, from the state in [Figure 4.3](#index_split_011.html#filepos524086)(a), it takes just five steps to reach the state in [Figure 4.3](#index_split_011.html#filepos524086)(b), which has *h* = 1 and is very nearly a solution. Unfortunately, hill climbing often gets stuck for the following reasons:

* * *

GREEDY LOCAL SEARCH

* * *

* * *

LOCAL MAXIMUM

* * *

> • **Local maxima**: a local maximum is a peak that is higher than each of its neighboring states but lower than the global maximum. Hill-climbing algorithms that reach the vicinity of a local maximum will be drawn upward toward the peak but will then be stuck with nowhere else to go. [Figure 4.1](#index_split_011.html#filepos519331) illustrates the problem schematically. More concretely, the state in [Figure 4.3](#index_split_011.html#filepos524086)(b) is a local maximum (i.e., a local minimum for the cost *h*); every move of a single queen makes the situation worse.

> ![image](images/00069.jpg)

> **Figure 4.3** (a) An 8-queens state with heuristic cost estimate *h* = 17, showing the value of *h* for each possible successor obtained by moving a queen within its column. The best moves are marked. (b) A local minimum in the 8-queens state space; the state has *h* = 1 but every successor has a higher cost.

> • **Ridges**: a ridge is shown in [Figure 4.4](#index_split_011.html#filepos527159). Ridges result in a sequence of local maxima that is very difficult for greedy algorithms to navigate.

* * *

RIDGE

* * *

> • **Plateaux**: a plateau is a flat area of the state-space landscape. It can be a flat local maximum, from which no uphill exit exists, or a **shoulder**, from which progress is possible. (See [Figure 4.1](#index_split_011.html#filepos519331).) A hill-climbing search might get lost on the plateau.

* * *

PLATEAU

* * *

* * *

SHOULDER

* * *

In each case, the algorithm reaches a point at which no progress is being made. Starting from a randomly generated 8-queens state, steepest-ascent hill climbing gets stuck 86% of the time, solving only 14% of problem instances. It works quickly, taking just 4 steps on average when it succeeds and 3 when it gets stuck—not bad for a state space with 8⁸ ≈ 17 million states.

The algorithm in [Figure 4.2](#index_split_011.html#filepos519868) halts if it reaches a plateau where the best successor has the same value as the current state. Might it not be a good idea to keep going—to allow a **sideways move** in the hope that the plateau is really a shoulder, as shown in [Figure 4.1](#index_split_011.html#filepos519331)? The answer is usually yes, but we must take care. If we always allow sideways moves when there are no uphill moves, an infinite loop will occur whenever the algorithm reaches a flat local maximum that is not a shoulder. One common solution is to put a limit on the number of consecutive sideways moves allowed. For example, we could allow up to, say, 100 consecutive sideways moves in the 8-queens problem. This raises the percentage of problem instances solved by hill climbing from 14% to 94%. Success comes at a cost: the algorithm averages roughly 21 steps for each successful instance and 64 for each failure.

* * *

SIDEWAYS MOVE

* * *

> ![image](images/00070.jpg)

> **Figure 4.4** Illustration of why ridges cause difficulties for hill climbing. The grid of states (dark circles) is superimposed on a ridge rising from left to right, creating a sequence of local maxima that are not directly connected to each other. From each local maximum, all the available actions point downhill.

Many variants of hill climbing have been invented. **Stochastic hill climbing** chooses at random from among the uphill moves; the probability of selection can vary with the steepness of the uphill move. This usually converges more slowly than steepest ascent, but in some state landscapes, it finds better solutions. **First-choice hill climbing** implements stochastic hill climbing by generating successors randomly until one is generated that is better than the current state. This is a good strategy when a state has many (e.g., thousands) of successors.

* * *

STOCHASTIC HILL CLIMBING

* * *

* * *

FIRST-CHOICE HILL CLIMBING

* * *

The hill-climbing algorithms described so far are incomplete—they often fail to find a goal when one exists because they can get stuck on local maxima. **Random-restart hill climbing** adopts the well-known adage, “If at first you don’t succeed, try, try again.” It conducts a series of hill-climbing searches from randomly generated initial states,[¹](#index_split_015.html#filepos5573749) until a goal is found. It is trivially complete with probability approaching 1, because it will eventually generate a goal state as the initial state. If each hill-climbing search has a probability *p* of success, then the expected number of restarts required is 1/*p*. For 8-queens instances with no sideways moves allowed, *p* ≈ 0.14, so we need roughly 7 iterations to find a goal (6 failures and 1 success). The expected number of steps is the cost of one successful iteration plus (1−*p*)/*p* times the cost of failure, or roughly 22 steps in all. When we allow sideways moves, 1/0.94 ≈ 1.06 iterations are needed on average and (1 × 21) + (0.06/0.94) × 64 ≈ 25 steps. For 8-queens, then, random-restart hill climbing is very effective indeed. Even for three million queens, the approach can find solutions in under a minute.[²](#index_split_015.html#filepos5573965)

* * *

RANDOM-RESTART HILL CLIMBING

* * *

The success of hill climbing depends very much on the shape of the state-space landscape: if there are few local maxima and plateaux, random-restart hill climbing will find a good solution very quickly. On the other hand, many real problems have a landscape that looks more like a widely scattered family of balding porcupines on a flat floor, with miniature porcupines living on the tip of each porcupine needle, *ad infinitum*. NP-hard problems typically have an exponential number of local maxima to get stuck on. Despite this, a reasonably good local maximum can often be found after a small number of restarts.

#### **4.1.2 Simulated annealing**

A hill-climbing algorithm that *never* makes “downhill” moves toward states with lower value (or higher cost) is guaranteed to be incomplete, because it can get stuck on a local maximum. In contrast, a purely random walk—that is, moving to a successor chosen uniformly at random from the set of successors—is complete but extremely inefficient. Therefore, it seems reasonable to try to combine hill climbing with a random walk in some way that yields both efficiency and completeness. **Simulated annealing** is such an algorithm. In metallurgy, **annealing** is the process used to temper or harden metals and glass by heating them to a high temperature and then gradually cooling them, thus allowing the material to reach a low-energy crystalline state. To explain simulated annealing, we switch our point of view from hill climbing to **gradient descent** (i.e., minimizing cost) and imagine the task of getting a ping-pong ball into the deepest crevice in a bumpy surface. If we just let the ball roll, it will come to rest at a local minimum. If we shake the surface, we can bounce the ball out of the local minimum. The trick is to shake just hard enough to bounce the ball out of local minima but not hard enough to dislodge it from the global minimum. The simulated-annealing solution is to start by shaking hard (i.e., at a high temperature) and then gradually reduce the intensity of the shaking (i.e., lower the temperature).

* * *

SIMULATED ANNEALING

* * *

* * *

GRADIENT DESCENT

* * *

The innermost loop of the simulated-annealing algorithm ([Figure 4.5](#index_split_011.html#filepos534744)) is quite similar to hill climbing. Instead of picking the *best* move, however, it picks a *random* move. If the move improves the situation, it is always accepted. Otherwise, the algorithm accepts the move with some probability less than 1. The probability decreases exponentially with the “badness” of the move—the amount Δ*E* by which the evaluation is worsened. The probability also decreases as the “temperature” *T* goes down: “bad” moves are more likely to be allowed at the start when *T* is high, and they become more unlikely as *T* decreases. If the *schedule* lowers *T* slowly enough, the algorithm will find a global optimum with probability approaching 1.

Simulated annealing was first used extensively to solve VLSI layout problems in the early 1980s. It has been applied widely to factory scheduling and other large-scale optimization tasks. In Exercise 4.4, you are asked to compare its performance to that of random-restart hill climbing on the 8-queens puzzle.

#### **4.1.3 Local beam search**

Keeping just one node in memory might seem to be an extreme reaction to the problem of memory limitations. The **local beam search** algorithm[³](#index_split_015.html#filepos5574399) keeps track of *k* states rather than just one. It begins with *k* randomly generated states. At each step, all the successors of all *k* states are generated. If any one is a goal, the algorithm halts. Otherwise, it selects the *k* best successors from the complete list and repeats.

* * *

LOCAL BEAM SEARCH

* * *

> ![image](images/00071.jpg)

> **Figure 4.5** The simulated annealing algorithm, a version of stochastic hill climbing where some downhill moves are allowed. Downhill moves are accepted readily early in the annealing schedule and then less often as time goes on. The *schedule* input determines the value of the temperature *T* as a function of time.

At first sight, a local beam search with *k* states might seem to be nothing more than running *k* random restarts in parallel instead of in sequence. In fact, the two algorithms are quite different. In a random-restart search, each search process runs independently of the others. *In a local beam search, useful information is passed among the parallel search threads.* In effect, the states that generate the best successors say to the others, “Come over here, the grass is greener!” The algorithm quickly abandons unfruitful searches and moves its resources to where the most progress is being made.

![hand](images/00006.jpg)

In its simplest form, local beam search can suffer from a lack of diversity among the *k* states—they can quickly become concentrated in a small region of the state space, making the search little more than an expensive version of hill climbing. A variant called **stochastic beam search**, analogous to stochastic hill climbing, helps alleviate this problem. Instead of choosing the best *k* from the the pool of candidate successors, stochastic beam search chooses *k* successors at random, with the probability of choosing a given successor being an increasing function of its value. Stochastic beam search bears some resemblance to the process of natural selection, whereby the “successors” (offspring) of a “state” (organism) populate the next generation according to its “value” (fitness).

* * *

STOCHASTIC BEAM SEARCH

* * *

#### **4.1.4 Genetic algorithms**

A **genetic algorithm** (or **GA**) is a variant of stochastic beam search in which successor states are generated by combining *two* parent states rather than by modifying a single state. The analogy to natural selection is the same as in stochastic beam search, except that now we are dealing with sexual rather than asexual reproduction.

* * *

GENETIC ALGORITHM

* * *

> ![image](images/00072.jpg)

> **Figure 4.6** The genetic algorithm, illustrated for digit strings representing 8-queens states. The initial population in (a) is ranked by the fitness function in (b), resulting in pairs for mating in (c). They produce offspring in (d), which are subject to mutation in (e).

> ![image](images/00073.jpg)

> **Figure 4.7** The 8-queens states corresponding to the first two parents in [Figure 4.6](#index_split_011.html#filepos537773)(c) and the first offspring in [Figure 4.6](#index_split_011.html#filepos537773)(d). The shaded columns are lost in the crossover step and the unshaded columns are retained.

Like beam searches, GAs begin with a set of *k* randomly generated states, called the **population**. Each state, or **individual**, is represented as a string over a finite alphabet—most commonly, a string of 0s and 1s. For example, an 8-queens state must specify the positions of 8 queens, each in a column of 8 squares, and so requires 8 × log[2] 8 = 24 bits. Alternatively, the state could be represented as 8 digits, each in the range from 1 to 8. (We demonstrate later that the two encodings behave differently.) [Figure 4.6](#index_split_011.html#filepos537773)(a) shows a population of four 8-digit strings representing 8-queens states.

* * *

POPULATION

* * *

* * *

INDIVIDUAL

* * *

The production of the next generation of states is shown in [Figure 4.6](#index_split_011.html#filepos537773)(b)–(e). In (b), each state is rated by the objective function, or (in GA terminology) the **fitness function**. A fitness function should return higher values for better states, so, for the 8-queens problem we use the number of *nonattacking* pairs of queens, which has a value of 28 for a solution. The values of the four states are 24, 23, 20, and 11. In this particular variant of the genetic algorithm, the probability of being chosen for reproducing is directly proportional to the fitness score, and the percentages are shown next to the raw scores.

* * *

FITNESS FUNCTION

* * *

In (c), two pairs are selected at random for reproduction, in accordance with the probabilities in (b). Notice that one individual is selected twice and one not at all.[⁴](#index_split_015.html#filepos5574607) For each pair to be mated, a **crossover** point is chosen randomly from the positions in the string. In [Figure 4.6](#index_split_011.html#filepos537773), the crossover points are after the third digit in the first pair and after the fifth digit in the second pair.[⁵](#index_split_015.html#filepos5574952)

* * *

CROSSOVER

* * *

In (d), the offspring themselves are created by crossing over the parent strings at the crossover point. For example, the first child of the first pair gets the first three digits from the first parent and the remaining digits from the second parent, whereas the second child gets the first three digits from the second parent and the rest from the first parent. The 8-queens states involved in this reproduction step are shown in [Figure 4.7](#index_split_011.html#filepos538277). The example shows that when two parent states are quite different, the crossover operation can produce a state that is a long way from either parent state. It is often the case that the population is quite diverse early on in the process, so crossover (like simulated annealing) frequently takes large steps in the state space early in the search process and smaller steps later on when most individuals are quite similar.

Finally, in (e), each location is subject to random **mutation** with a small independent probability. One digit was mutated in the first, third, and fourth offspring. In the 8-queens problem, this corresponds to choosing a queen at random and moving it to a random square in its column. [Figure 4.8](#index_split_011.html#filepos545069) describes an algorithm that implements all these steps.

* * *

MUTATION

* * *

Like stochastic beam search, genetic algorithms combine an uphill tendency with random exploration and exchange of information among parallel search threads. The primary advantage, if any, of genetic algorithms comes from the crossover operation. Yet it can be shown mathematically that, if the positions of the genetic code are permuted initially in a random order, crossover conveys no advantage. Intuitively, the advantage comes from the ability of crossover to combine large blocks of letters that have evolved independently to perform useful functions, thus raising the level of granularity at which the search operates. For example, it could be that putting the first three queens in positions 2, 4, and 6 (where they do not attack each other) constitutes a useful block that can be combined with other blocks to construct a solution.

The theory of genetic algorithms explains how this works using the idea of a **schema**, which is a substring in which some of the positions can be left unspecified. For example, the schema 246\*\*\*\*\* describes all 8-queens states in which the first three queens are in positions 2, 4, and 6, respectively. Strings that match the schema (such as 24613578) are called **instances** of the schema. It can be shown that if the average fitness of the instances of a schema is above the mean, then the number of instances of the schema within the population will grow over time. Clearly, this effect is unlikely to be significant if adjacent bits are totally unrelated to each other, because then there will be few contiguous blocks that provide a consistent benefit. Genetic algorithms work best when schemata correspond to meaningful components of a solution. For example, if the string is a representation of an antenna, then the schemata may represent components of the antenna, such as reflectors and deflectors. A good component is likely to be good in a variety of different designs. This suggests that successful use of genetic algorithms requires careful engineering of the representation.

* * *

SCHEMA

* * *

* * *

INSTANCE

* * *

> ![image](images/00074.jpg)

> **Figure 4.8** A genetic algorithm. The algorithm is the same as the one diagrammed in [Figure 4.6](#index_split_011.html#filepos537773), with one variation: in this more popular version, each mating of two parents produces only one offspring, not two.

In practice, genetic algorithms have had a widespread impact on optimization problems, such as circuit layout and job-shop scheduling. At present, it is not clear whether the appeal of genetic algorithms arises from their performance or from their æsthetically pleasing origins in the theory of evolution. Much work remains to be done to identify the conditions under which genetic algorithms perform well.

### 4.2 LOCAL SEARCH IN CONTINUOUS SPACES

In [Chapter 2](#index_split_000.html#filepos187684), we explained the distinction between discrete and continuous environments, pointing out that most real-world environments are continuous. Yet none of the algorithms we have described (except for first-choice hill climbing and simulated annealing) can handle continuous state and action spaces, because they have infinite branching factors. This section provides a *very brief* introduction to some local search techniques for finding optimal solutions in continuous spaces. The literature on this topic is vast; many of the basic techniques originated in the 17th century, after the development of calculus by Newton and Leibniz.[⁶](#index_split_015.html#filepos5575290) We find uses for these techniques at several places in the book, including the chapters on learning, vision, and robotics.

* * *

EVOLUTION AND SEARCH

The theory of **evolution** was developed in Charles Darwin’s *On the Origin of Species by Means of Natural Selection* (1859) and independently by Alfred Russel Wallace (1858). The central idea is simple: variations occur in reproduction and will be preserved in successive generations approximately in proportion to their effect on reproductive fitness.

Darwin’s theory was developed with no knowledge of how the traits of organisms can be inherited and modified. The probabilistic laws governing these processes were first identified by Gregor Mendel (1866), a monk who experimented with sweet peas. Much later, Watson and Crick (1953) identified the structure of the DNA molecule and its alphabet, AGTC (adenine, guanine, thymine, cytosine). In the standard model, variation occurs both by point mutations in the letter sequence and by “crossover” (in which the DNA of an offspring is generated by combining long sections of DNA from each parent).

The analogy to local search algorithms has already been described; the principal difference between stochastic beam search and evolution is the use of *sexual* reproduction, wherein successors are generated from *multiple* organisms rather than just one. The actual mechanisms of evolution are, however, far richer than most genetic algorithms allow. For example, mutations can involve reversals, duplications, and movement of large chunks of DNA; some viruses borrow DNA from one organism and insert it in another; and there are transposable genes that do nothing but copy themselves many thousands of times within the genome. There are even genes that poison cells from potential mates that do not carry the gene, thereby increasing their own chances of replication. Most important is the fact that the *genes themselves encode the mechanisms* whereby the genome is reproduced and translated into an organism. In genetic algorithms, those mechanisms are a separate program that is not represented within the strings being manipulated.

Darwinian evolution may appear inefficient, having generated blindly some 10^(45) or so organisms without improving its search heuristics one iota. Fifty years before Darwin, however, the otherwise great French naturalist Jean Lamarck (1809) proposed a theory of evolution whereby traits *acquired by adaptation during an organism’s lifetime* would be passed on to its offspring. Such a process would be effective but does not seem to occur in nature. Much later, James Baldwin (1896) proposed a superficially similar theory: that behavior learned during an organism’s lifetime could accelerate the rate of evolution. Unlike Lamarck’s, Baldwin’s theory is entirely consistent with Darwinian evolution because it relies on selection pressures operating on individuals that have found local optima among the set of possible behaviors allowed by their genetic makeup. Computer simulations confirm that the “Baldwin effect” is real, once “ordinary” evolution has created organisms whose internal performance measure correlates with actual fitness.

* * *

We begin with an example. Suppose we want to place three new airports anywhere in Romania, such that the sum of squared distances from each city on the map ([Figure 3.2](#index_split_010.html#filepos318111)) to its nearest airport is minimized. The state space is then defined by the coordinates of the airports: (*x*[1], *y*[1]), (*x*[2], *y*[2]), and (*x*[3], *y*[3]). This is a *six-dimensional* space; we also say that states are defined by six **variables**. (In general, states are defined by an *n*\-dimensional vector of variables, **x**.) Moving around in this space corresponds to moving one or more of the airports on the map. The objective function *f* (*x*[1], *y*[1], *x*[2], *y*[2], *x*[3], *y*[3]) is relatively easy to compute for any particular state once we compute the closest cities. Let *C*[*i*] be the set of cities whose closest airport (in the current state) is airport i. Then, *in the neighborhood of the current state*, where the *C*[*i*]s remain constant, we have

> ![equ](images/00075.jpg)

* * *

VARIABLE

* * *

This expression is correct *locally*, but not globally because the sets *C*[*i*] are (discontinuous) functions of the state.

One way to avoid continuous problems is simply to **discretize** the neighborhood of each state. For example, we can move only one airport at a time in either the *x* or *y* direction by a fixed amount ±δ. With 6 variables, this gives 12 possible successors for each state. We can then apply any of the local search algorithms described previously. We could also apply stochastic hill climbing and simulated annealing directly, without discretizing the space. These algorithms choose successors randomly, which can be done by generating random vectors of length δ.

* * *

DISCRETIZATION

* * *

Many methods attempt to use the **gradient** of the landscape to find a maximum. The gradient of the objective function is a vector ▽*f* that gives the magnitude and direction of the steepest slope. For our problem, we have

> ![equ](images/00076.jpg)

In some cases, we can find a maximum by solving the equation ▽*f* = 0. (This could be done, for example, if we were placing just one airport; the solution is the arithmetic mean of all the cities’ coordinates.) In many cases, however, this equation cannot be solved in closed form. For example, with three airports, the expression for the gradient depends on what cities are closest to each airport in the current state. This means we can compute the gradient *locally* (but not *globally*); for example,

> ![equ](images/00077.jpg)

Given a locally correct expression for the gradient, we can perform steepest-ascent hill climbing by updating the current state according to the formula

> **x** ← **x** + α▽*f*(**x**)

where α is a small constant often called the **step size**. In other cases, the objective function might not be available in a differentiable form at all—for example, the value of a particular set of airport locations might be determined by running some large-scale economic simulation package. In those cases, we can calculate a so-called **empirical gradient** by evaluating the response to small increments and decrements in each coordinate. Empirical gradient search is the same as steepest-ascent hill climbing in a discretized version of the state space.

* * *

STEP SIZE

* * *

* * *

EMPIRICAL GRADIENT

* * *

Hidden beneath the phrase “α is a small constant” lies a huge variety of methods for adjusting α. The basic problem is that, if α is too small, too many steps are needed; if α is too large, the search could overshoot the maximum. The technique of **line search** tries to overcome this dilemma by extending the current gradient direction—usually by repeatedly doubling α—until *f* starts to decrease again. The point at which this occurs becomes the new current state. There are several schools of thought about how the new direction should be chosen at this point.

* * *

LINE SEARCH

* * *

For many problems, the most effective algorithm is the venerable **Newton–Raphson** method. This is a general technique for finding roots of functions—that is, solving equations of the form *g*(*x*) = 0. It works by computing a new estimate for the root *x* according to Newton’s formula

* * *

NEWTON–RAPHSON

* * *

> *x* ← *x* − *g*(*x*)/*g*′(*x*).

To find a maximum or minimum of *f*, we need to find **x** such that the *gradient* is zero (i.e., ▽*f*(**x**) = **0**). Thus, *g*(*x*) in Newton’s formula becomes ▽*f* (**x**), and the update equation can be written in matrix–vector form as

> ![equ](images/00078.jpg)

where **H**[*f*](**x**) is the **Hessian** matrix of second derivatives, whose elements *H*[*ij*] are given by ∂²*f*/∂*x*[*i*]∂*x*[*j*]. For our airport example, we can see from Equation (4.2) that **H**[*f*](**x**) is particularly simple: the off-diagonal elements are zero and the diagonal elements for airport *i* are just twice the number of cities in *C*[*i*]. A moment’s calculation shows that one step of the update moves airport i directly to the centroid of *C*[*i*], which is the minimum of the local expression for *f* from Equation (4.1).[⁷](#index_split_015.html#filepos5575498) For high-dimensional problems, however, computing the *n*² entries of the Hessian and inverting it may be expensive, so many approximate versions of the Newton–Raphson method have been developed.

* * *

HESSIAN

* * *

Local search methods suffer from local maxima, ridges, and plateaux in continuous state spaces just as much as in discrete spaces. Random restarts and simulated annealing can be used and are often helpful. High-dimensional continuous spaces are, however, big places in which it is easy to get lost.

A final topic with which a passing acquaintance is useful is **constrained optimization**. An optimization problem is constrained if solutions must satisfy some hard constraints on the values of the variables. For example, in our airport-siting problem, we might constrain sites to be inside Romania and on dry land (rather than in the middle of lakes). The difficulty of constrained optimization problems depends on the nature of the constraints and the objective function. The best-known category is that of **linear programming** problems, in which constraints must be linear inequalities forming a **convex set**[⁸](#index_split_015.html#filepos5575858) and the objective function is also linear. The time complexity of linear programming is polynomial in the number of variables.

* * *

CONSTRAINED OPTIMIZATION

* * *

* * *

LINEAR PROGRAMMING

* * *

* * *

CONVEX SET

* * *

Linear programming is probably the most widely studied and broadly useful class of optimization problems. It is a special case of the more general problem of **convex optimization**, which allows the constraint region to be any convex region and the objective to be any function that is convex within the constraint region. Under certain conditions, convex optimization problems are also polynomially solvable and may be feasible in practice with thousands of variables. Several important problems in machine learning and control theory can be formulated as convex optimization problems (see [Chapter 20](#index_split_015.html#filepos3158034)).

* * *

CONVEX OPTIMIZATION

* * *

### 4.3 SEARCHING WITH NONDETERMINISTIC ACTIONS

In [Chapter 3](#index_split_000.html#filepos301685), we assumed that the environment is fully observable and deterministic and that the agent knows what the effects of each action are. Therefore, the agent can calculate exactly which state results from any sequence of actions and always knows which state it is in. Its percepts provide no new information after each action, although of course they tell the agent the initial state.

When the environment is either partially observable or nondeterministic (or both), percepts become useful. In a partially observable environment, every percept helps narrow down the set of possible states the agent might be in, thus making it easier for the agent to achieve its goals. When the environment is nondeterministic, percepts tell the agent which of the possible outcomes of its actions has actually occurred. In both cases, the future percepts cannot be determined in advance and the agent’s future actions will depend on those future percepts. So the solution to a problem is not a sequence but a **contingency plan** (also known as a **strategy**) that specifies what to do depending on what percepts are received. In this section, we examine the case of nondeterminism, deferring partial observability to [Section 4.4](#index_split_000.html#filepos575701).

* * *

CONTINGENCY PLAN

* * *

* * *

STRATEGY

* * *

#### **4.3.1 The erratic vacuum world**

As an example, we use the vacuum world, first introduced in [Chapter 2](#index_split_000.html#filepos187684) and defined as a search problem in [Section 3.2.1](#index_split_000.html#filepos325111). Recall that the state space has eight states, as shown in [Figure 4.9](#index_split_011.html#filepos563775). There are three actions—*Left*, *Right*, and *Suck*—and the goal is to clean up all the dirt (states 7 and 8). If the environment is observable, deterministic, and completely known, then the problem is trivially solvable by any of the algorithms in [Chapter 3](#index_split_000.html#filepos301685) and the solution is an action sequence. For example, if the initial state is 1, then the action sequence \[*Suck*,*Right*,*Suck*\] will reach a goal state, 8.

> ![image](images/00079.jpg)

> **Figure 4.9** The eight possible states of the vacuum world; states 7 and 8 are goal states.

Now suppose that we introduce nondeterminism in the form of a powerful but erratic vacuum cleaner. In the **erratic vacuum world**, the *Suck* action works as follows:

> • When applied to a dirty square the action cleans the square and sometimes cleans up dirt in an adjacent square, too.

> • When applied to a clean square the action sometimes deposits dirt on the carpet.[⁹](#index_split_015.html#filepos5576239)

* * *

ERRATIC VACUUM WORLD

* * *

To provide a precise formulation of this problem, we need to generalize the notion of a **transition model** from [Chapter 3](#index_split_000.html#filepos301685). Instead of defining the transition model by a RESULT function that returns a single state, we use a RESULTS function that returns a *set* of possible outcome states. For example, in the erratic vacuum world, the *Suck* action in state 1 leads to a state in the set {5, 7}—the dirt in the right-hand square may or may not be vacuumed up.

We also need to generalize the notion of a **solution** to the problem. For example, if we start in state 1, there is no single *sequence* of actions that solves the problem. Instead, we need a contingency plan such as the following:

> ![equ](images/00080.jpg)

Thus, solutions for nondeterministic problems can contain nested **if**–**then**–**else** statements; this means that they are *trees* rather than sequences. This allows the selection of actions based on contingencies arising during execution. Many problems in the real, physical world are contingency problems because exact prediction is impossible. For this reason, many people keep their eyes open while walking around or driving.

#### **4.3.2** AND–OR **search trees**

The next question is how to find contingent solutions to nondeterministic problems. As in [Chapter 3](#index_split_000.html#filepos301685), we begin by constructing search trees, but here the trees have a different character. In a deterministic environment, the only branching is introduced by the agent’s own choices in each state. We call these nodes **OR** **nodes**. In the vacuum world, for example, at an OR node the agent chooses *Left or Right or Suck*. In a nondeterministic environment, branching is also introduced by the *environment’s* choice of outcome for each action. We call these nodes **AND** **nodes**. For example, the *Suck* action in state 1 leads to a state in the set {5, 7}, so the agent would need to find a plan for state 5 *and* for state 7. These two kinds of nodes alternate, leading to an AND–OR **tree** as illustrated in [Figure 4.10](#index_split_011.html#filepos568015).

* * *

OR NODE

* * *

* * *

AND NODE

* * *

* * *

AND–OR TREE

* * *

> ![image](images/00081.jpg)

> **Figure 4.10** The first two levels of the search tree for the erratic vacuum world. State nodes are OR nodes where some action must be chosen. At the AND nodes, shown as circles, every outcome must be handled, as indicated by the arc linking the outgoing branches. The solution found is shown in bold lines.

A solution for an AND–OR search problem is a subtree that (1) has a goal node at every leaf, (2) specifies one action at each of its OR nodes, and (3) includes every outcome branch at each of its AND nodes. The solution is shown in bold lines in the figure; it corresponds to the plan given in Equation (4.3). (The plan uses if–then–else notation to handle the AND branches, but when there are more than two branches at a node, it might be better to use a **case** construct.) Modifying the basic problem-solving agent shown in [Figure 3.1](#index_split_010.html#filepos314502) to execute contingent solutions of this kind is straightforward. One may also consider a somewhat different agent design, in which the agent can act *before* it has found a guaranteed plan and deals with some contingencies only as they arise during execution. This type of **interleaving** of search and execution is also useful for exploration problems (see [Section 4.5](#index_split_000.html#filepos605406)) and for game playing (see [Chapter 5](#index_split_000.html#filepos660071)).

* * *

INTERLEAVING

* * *

> ![image](images/00082.jpg)

> **Figure 4.11** An algorithm for searching AND–OR graphs generated by nondeterministic environments. It returns a conditional plan that reaches a goal state in all circumstances. (The notation \[*x* | *l*\] refers to the list formed by adding object *x* to the front of list *l*.)

[Figure 4.11](#index_split_011.html#filepos569895) gives a recursive, depth-first algorithm for AND–OR graph search. One key aspect of the algorithm is the way in which it deals with cycles, which often arise in nondeterministic problems (e.g., if an action sometimes has no effect or if an unintended effect can be corrected). If the current state is identical to a state on the path from the root, then it returns with failure. This doesn’t mean that there is *no* solution from the current state; it simply means that if there *is* a noncyclic solution, it must be reachable from the earlier incarnation of the current state, so the new incarnation can be discarded. With this check, we ensure that the algorithm terminates in every finite state space, because every path must reach a goal, a dead end, or a repeated state. Notice that the algorithm does not check whether the current state is a repetition of a state on some *other* path from the root, which is important for efficiency. Exercise 4.5 investigates this issue.

AND–OR graphs can also be explored by breadth-first or best-first methods. The concept of a heuristic function must be modified to estimate the cost of a contingent solution rather than a sequence, but the notion of admissibility carries over and there is an analog of the A^(\*) algorithm for finding optimal solutions. Pointers are given in the bibliographical notes at the end of the chapter.

> ![image](images/00083.jpg)

> **Figure 4.12** Part of the search graph for the slippery vacuum world, where we have shown (some) cycles explicitly. All solutions for this problem are cyclic plans because there is no way to move reliably.

#### **4.3.3 Try, try again**

Consider the slippery vacuum world, which is identical to the ordinary (non-erratic) vacuum world except that movement actions sometimes fail, leaving the agent in the same location. For example, moving *Right* in state 1 leads to the state set {1, 2}. [Figure 4.12](#index_split_011.html#filepos572108) shows part of the search graph; clearly, there are no longer any acyclic solutions from state 1, and AND\-OR\-GRAPH\-SEARCH would return with failure. There is, however, a **cyclic solution**, whichistokeeptrying *Right* until it works. We can express this solution by adding a **label** to denote some portion of the plan and using that label later instead of repeating the plan itself. Thus, our cyclic solution is

> \[*Suck*, *L*[1]: *Right*, **if** *State* = 5 **then** *L*[1] **else** *Suck*\].

* * *

CYCLIC SOLUTION

* * *

* * *

LABEL

* * *

(A better syntax for the looping part of this plan would be “**while** *State* = 5 **do** *Right*.”) In general a cyclic plan may be considered a solution provided that every leaf is a goal state and that a leaf is reachable from every point in the plan. The modifications needed to AND-OR\-GRAPH\-SEARCH are covered in Exercise 4.6. The key realization is that a loop in the state space back to a state *L* translates to a loop in the plan back to the point where the subplan for state *L* is executed.

Given the definition of a cyclic solution, an agent executing such a solution will eventually reach the goal *provided that each outcome of a nondeterministic action eventually occurs*. Is this condition reasonable? It depends on the reason for the nondeterminism. If the action rolls a die, then it’s reasonable to suppose that eventually a six will be rolled. If the action is to insert a hotel card key into the door lock, but it doesn’t work the first time, then perhaps it will eventually work, or perhaps one has the wrong key (or the wrong room!). After seven or eight tries, most people will assume the problem is with the key and will go back to the front desk to get a new one. One way to understand this decision is to say that the initial problem formulation (observable, nondeterministic) is abandoned in favor of a different formulation (partially observable, deterministic) where the failure is attributed to an unobservable property of the key. We have more to say on this issue in [Chapter 13](#index_split_015.html#filepos1915714).

### 4.4 SEARCHING WITH PARTIAL OBSERVATIONS

We now turn to the problem of partial observability, where the agent’s percepts do not suffice to pin down the exact state. As noted at the beginning of the previous section, if the agent is in one of several possible states, then an action may lead to one of several possible outcomes—*even if the environment is deterministic*. The key concept required for solving partially observable problems is the **belief state**, representing the agent’s current belief about the possible physical states it might be in, given the sequence of actions and percepts up to that point. We begin with the simplest scenario for studying belief states, which is when the agent has no sensors at all; then we add in partial sensing as well as nondeterministic actions.

* * *

BELIEF STATE

* * *

#### **4.4.1 Searching with no observation**

When the agent’s percepts provide *no information at all*, we have what is called a **sensorless** problem or sometimes a **conformant** problem. At first, one might think the sensorless agent has no hope of solving a problem if it has no idea what state it’s in; in fact, sensorless problems are quite often solvable. Moreover, sensorless agents can be surprisingly useful, primarily because they *don’t* rely on sensors working properly. In manufacturing systems, for example, many ingenious methods have been developed for orienting parts correctly from an unknown initial position by using a sequence of actions with no sensing at all. The high cost of sensing is another reason to avoid it: for example, doctors often prescribe a broad-spectrum antibiotic rather than using the contingent plan of doing an expensive blood test, then waiting for the results to come back, and then prescribing a more specific antibiotic and perhaps hospitalization because the infection has progressed too far.

* * *

SENSORLESS

* * *

* * *

CONFORMANT

* * *

We can make a sensorless version of the vacuum world. Assume that the agent knows the geography of its world, but doesn’t know its location or the distribution of dirt. In that case, its initial state could be any element of the set {1, 2, 3, 4, 5, 6, 7, 8}. Now, consider what happens if it tries the action *Right*. This will cause it to be in one of the states {2, 4, 6, 8}—the agent now has more information! Furthermore, the action sequence \[*Right*,*Suck*\] will always end up in one of the states {4, 8}. Finally, the sequence \[*Right*,*Suck*,*Left*,*Suck*\] is guaranteed to reach the goal state 7 no matter what the start state. We say that the agent can **coerce** the world into state 7.

* * *

COERCION

* * *

To solve sensorless problems, we search in the space of belief states rather than physical states.[^(10)](#index_split_015.html#filepos5576545) Notice that in belief-state space, the problem is *fully observable* because the agent always knows its own belief state. Furthermore, the solution (if any) is always a sequence of actions. This is because, as in the ordinary problems of [Chapter 3](#index_split_000.html#filepos301685), the percepts received after each action are completely predictable—they’re always empty! So there are no contingencies to plan for. This is true *even if the environment is nondeterminstic*.

It is instructive to see how the belief-state search problem is constructed. Suppose the underlying physical problem *P* is defined by ACTIONS[*P*], RESULT[*P*], GOAL\-TEST[*P*], and STEP\-COST[*P*]. Then we can define the corresponding sensorless problem as follows:

> • **Belief states**: The entire belief-state space contains every possible set of physical states. If *P* has *N* states, then the sensorless problem has up to 2^(*N*) states, although many may be unreachable from the initial state.

> • **Initial state**: Typically the set of all states in *P*, although in some cases the agent will have more knowledge than this.

> • **Actions**: This is slightly tricky. Suppose the agent is in belief state *b* = {*s*[1], *s*[2]}, but ACTIONS[*P*](*s*[1]) ≠ ACTIONS[*P*] (*s*[2]); then the agent is unsure of which actions are legal. If we assume that illegal actions have no effect on the environment, then it is safe to take the *union* of all the actions in any of the physical states in the current belief state *b*:

> ![equ](images/00084.jpg)

> On the other hand, if an illegal action might be the end of the world, it is safer to allow only the *intersection*, that is, the set of actions legal in *all* the states. For the vacuum world, every state has the same legal actions, so both methods give the same result.

> • **Transition model**: The agent doesn’t know which state in the belief state is the right one; so as far as it knows, it might get to any of the states resulting from applying the action to one of the physical states in the belief state. For deterministic actions, the set of states that might be reached is

> ![equ](images/00085.jpg)

With deterministic actions, *b*′ is never larger than *b*. With nondeterminism, we have

> ![equ](images/00086.jpg)

which may be larger than *b*, as shown in [Figure 4.13](#index_split_011.html#filepos584356). The process of generating the new belief state after the action is called the **prediction** step; the notation *b*′ = PREDICTION[*P*] (*b*, *a*) will come in handy.

* * *

PREDICTION

* * *

> • **Goal test**: The agent wants a plan that is sure to work, which means that a belief state satisfies the goal only if *all* the physical states in it satisfy GOAL\-TEST[*P*]. The agent may *accidentally* achieve the goal earlier, but it won’t *know* that it has done so.

> • **Path cost**: This is also tricky. If the same action can have different costs in different states, then the cost of taking an action in a given belief state could be one of several values. (This gives rise to a new class of problems, which we explore in Exercise 4.9.) For now we assume that the cost of an action is the same in all states and so can be transferred directly from the underlying physical problem.

> ![image](images/00087.jpg)

> **Figure 4.13** (a) Predicting the next belief state for the sensorless vacuum world with a deterministic action, *Right*. (b) Prediction for the same belief state and action in the slippery version of the sensorless vacuum world.

[Figure 4.14](#index_split_011.html#filepos588778) shows the reachable belief-state space for the deterministic, sensorless vacuum world. There are only 12 reachable belief states out of 2⁸ = 256 possible belief states.

The preceding definitions enable the automatic construction of the belief-state problem formulation from the definition of the underlying physical problem. Once this is done, we can apply any of the search algorithms of [Chapter 3](#index_split_000.html#filepos301685). In fact, we can do a little bit more than that. In “ordinary” graph search, newly generated states are tested to see if they are identical to existing states. This works for belief states, too; for example, in [Figure 4.14](#index_split_011.html#filepos588778), the action sequence \[*Suck*,*Left*,*Suck*\] starting at the initial state reaches the same belief state as \[*Right*,*Left*,*Suck*\], namely, {5, 7}. Now, consider the belief state reached by \[*Left*\], namely, {1, 3, 5, 7}. Obviously, this is not identical to {5, 7}, but it is a *superset*. It is easy to prove (Exercise 4.8) that if an action sequence is a solution for a belief state *b*, it is also a solution for any subset of *b*. Hence, we can discard a path reaching {1, 3, 5, 7} if {5, 7} has already been generated. Conversely, if {1, 3, 5, 7} has already been generated and found to be solvable, then any *subset*, such as {5, 7}, is guaranteed to be solvable. This extra level of pruning may dramatically improve the efficiency of sensorless problem solving.

Even with this improvement, however, sensorless problem-solving as we have described it is seldom feasible in practice. The difficulty is not so much the vastness of the belief-state space—even though it is exponentially larger than the underlying physical state space; in most cases the branching factor and solution length in the belief-state space and physical state space are not so different. The real difficulty lies with the size of each belief state. For example, the initial belief state for the 10 × 10 vacuum world contains 100 × 2^(100) or around 10^(32) physical states—far too many if we use the atomic representation, which is an explicit list of states.

One solution is to represent the belief state by some more compact description. In English, we could say the agent knows “Nothing” in the initial state; after moving *Left*, we could say, “Not in the rightmost column,” and so on. [Chapter 7](#index_split_000.html#filepos939379) explains how to do this in a formal representation scheme. Another approach is to avoid the standard search algorithms, which treat belief states as black boxes just like any other problem state. Instead, we can look *inside* the belief states and develop **incremental belief-state search** algorithms that build up the solution one physical state at a time. For example, in the sensorless vacuum world, the initial belief state is {1, 2, 3, 4, 5, 6, 7, 8}, and we have to find an action sequence that works in all 8 states. We can do this by first finding a solution that works for state 1; then we check if it works for state 2; if not, go back and find a different solution for state 1, and so on. Just as an AND–OR search has to find a solution for every branch at an AND node, this algorithm has to find a solution for every state in the belief state; the difference is that AND–OR search can find a different solution for each branch, whereas an incremental belief-state search has to find *one* solution that works for *all* the states.

> ![image](images/00088.jpg)

**Figure 4.14** The reachable portion of the belief-state space for the deterministic, sensorless vacuum world. Each shaded box corresponds to a single belief state. At any given point, the agent is in a particular belief state but does not know which physical state it is in. The initial belief state (complete ignorance) is the top center box. Actions are represented by labeled links. Self-loops are omitted for clarity.

* * *

INCREMENTAL BELIEF-STATE SEARCH

* * *

The main advantage of the incremental approach is that it is typically able to detect failure quickly—when a belief state is unsolvable, it is usually the case that a small subset of the belief state, consisting of the first few states examined, is also unsolvable. In some cases, this leads to a speedup proportional to the size of the belief states, which may themselves be as large as the physical state space itself.

Even the most efficient solution algorithm is not of much use when no solutions exist. Many things just cannot be done without sensing. For example, the sensorless 8-puzzle is impossible. On the other hand, a little bit of sensing can go a long way. For example, every 8-puzzle instance is solvable if just one square is visible—the solution involves moving each tile in turn into the visible square and then keeping track of its location.

#### **4.4.2 Searching with observations**

For a general partially observable problem, we have to specify how the environment generates percepts for the agent. For example, we might define the local-sensing vacuum world to be one in which the agent has a position sensor and a local dirt sensor but has no sensor capable of detecting dirt in other squares. The formal problem specification includes a PERCEPT(*s*) function that returns the percept received in a given state. (If sensing is nondeterministic, then we use a PERCEPTS function that returns a set of possible percepts.) For example, in the local-sensing vacuum world, the PERCEPT in state 1 is \[*A*, *Dirty*\]. Fully observable problems are a special case in which PERCEPT(*s*) = *s* for every state s, while sensorless problems are a special case in which PERCEPT(*s*) = *null*.

When observations are partial, it will usually be the case that several states could have produced any given percept. For example, the percept \[*A*, *Dirty*\] is produced by state 3 as well as by state 1. Hence, given this as the initial percept, the initial belief state for the local-sensing vacuum world will be {1, 3}. The ACTIONS, STEP\-COST, and GOAL\-TEST are constructed from the underlying physical problem just as for sensorless problems, but the transition model is a bit more complicated. We can think of transitions from one belief state to the next for a particular action as occurring in three stages, as shown in [Figure 4.15](#index_split_011.html#filepos594083):

> • The **prediction** stage is the same as for sensorless problems: given the action *a* in belief state *b*, the predicted belief state is ![equ](images/00089.jpg).[^(11)](#index_split_015.html#filepos5576873)

> • The **observation prediction** stage determines the set of percepts *o* that could be observed in the predicted belief state:

> ![equ](images/00090.jpg)

> • The **update** stage determines, for each possible percept, the belief state that would result from the percept. The new belief state *b*[*o*] is just the set of states in ![equ](images/00091.jpg)that could have produced the percept:

> ![equ](images/00092.jpg)

> Notice that each updated belief state b[*o*] can be no larger than the predicted belief state ![equ](images/00091.jpg); observations can only help reduce uncertainty compared to the sensorless case. Moreover, for deterministic sensing, the belief states for the different possible percepts will be disjoint, forming a *partition* of the original predicted belief state.

> ![image](images/00093.jpg)

> **Figure 4.15** Two example of transitions in local-sensing vacuum worlds. (a) In the deterministic world, *Right* is applied in the initial belief state, resulting in a new belief state with two possible physical states; for those states, the possible percepts are \[*B*, *Dirty*\] and \[*B*, *Clean*\], leading to two belief states, each of which is a singleton. (b) In the slippery world, *Right* is applied in the initial belief state, giving a new belief state with four physical states; for those states, the possible percepts are \[*A*, *Dirty*\], \[*B*, *Dirty*\], and \[*B*, *Clean*\], leading to three belief states as shown.

Putting these three stages together, we obtain the possible belief states resulting from a given action and the subsequent possible percepts:

> ![equ](images/00094.jpg)

Again, the nondeterminism in the partially observable problem comes from the inability to predict exactly which percept will be received after acting; underlying nondeterminism in the physical environment may *contribute* to this inability by enlarging the belief state at the prediction stage, leading to more percepts at the observation stage.

#### **4.4.3 Solving partially observable problems**

The preceding section showed how to derive the RESULTS function for a nondeterministic belief-state problem from an underlying physical problem and the PERCEPT function. Given such a formulation, the AND–OR search algorithm of [Figure 4.11](#index_split_011.html#filepos569895) can be applied directly to derive a solution. [Figure 4.16](#index_split_011.html#filepos596521) shows part of the search tree for the local-sensing vacuum world, assuming an initial percept \[*A*, *Dirty*\]. The solution is the conditional plan

> ![image](images/00095.jpg)

> **Figure 4.16** The first level of the AND–OR search tree for a problem in the local-sensing vacuum world; *Suck* is the first step of the solution.

> \[*Suck*, *Right*, **if** *Bstate* = {6} **then** *Suck* **else** \[ \]\].

Notice that, because we supplied a belief-state problem to the AND–OR search algorithm, it returned a conditional plan that tests the belief state rather than the actual state. This is as it should be: in a partially observable environment the agent won’t be able to execute a solution that requires testing the actual state.

As in the case of standard search algorithms applied to sensorless problems, the AND–OR search algorithm treats belief states as black boxes, just like any other states. One can improve on this by checking for previously generated belief states that are subsets or supersets of the current state, just as for sensorless problems. One can also derive incremental search algorithms, analogous to those described for sensorless problems, that provide substantial speedups over the black-box approach.

#### **4.4.4 An agent for partially observable environments**

The design of a problem-solving agent for partially observable environments is quite similar to the simple problem-solving agent in [Figure 3.1](#index_split_010.html#filepos314502): the agent formulates a problem, calls a search algorithm (such as AND\-OR\-GRAPH\-SEARCH) to solve it, and executes the solution. There are two main differences. First, the solution to a problem will be a conditional plan rather than a sequence; if the first step is an if–then–else expression, the agent will need to test the condition in the if-part and execute the then-part or the else-part accordingly. Second, the agent will need to maintain its belief state as it performs actions and receives percepts. This process resembles the prediction–observation–update process in Equation (4.5) but is actually simpler because the percept is given by the environment rather than calculated by the agent. Given an initial belief state *b*, an action *a*, and a percept *o*, the new belief state is:

> ![image](images/00096.jpg)

> **Figure 4.17** Two prediction–update cycles of belief-state maintenance in the kindergarten vacuum world with local sensing.

> ![equ](images/00097.jpg)

[Figure 4.17](#index_split_011.html#filepos599431) shows the belief state being maintained in the *kindergarten* vacuum world with local sensing, wherein any square may become dirty at any time unless the agent is actively cleaning it at that moment.[^(12)](#index_split_015.html#filepos5577125)

In partially observable environments—which include the vast majority of real-world environments—maintaining one’s belief state is a core function of any intelligent system. This function goes under various names, including **monitoring**, **filtering** and **state estimation**. Equation (4.6) is called a **recursive** state estimator because it computes the new belief state from the previous one rather than by examining the entire percept sequence. If the agent is not to “fall behind,” the computation has to happen as fast as percepts are coming in. As the environment becomes more complex, the exact update computation becomes infeasible and the agent will have to compute an approximate belief state, perhaps focusing on the implications of the percept for the aspects of the environment that are of current interest. Most work on this problem has been done for stochastic, continuous-state environments with the tools of probability theory, as explained in [Chapter 15](#index_split_015.html#filepos2253296). Here we will show an example in a discrete environment with detrministic sensors and nondeterministic actions.

* * *

MONITORING

* * *

* * *

FILTERING

* * *

* * *

STATE ESTIMATION

* * *

* * *

RECURSIVE

* * *

The example concerns a robot with the task of **localization**: working out where it is, given a map of the world and a sequence of percepts and actions. Our robot is placed in the maze-like environment of [Figure 4.18](#index_split_011.html#filepos603436). The robot is equipped with four sonar sensors that tell whether there is an obstacle—the outer wall or a black square in the figure—in each of the four compass directions. We assume that the sensors give perfectly correct data, and that the robot has a correct map of the enviornment. But unfortunately the robot’s navigational system is broken, so when it executes a *Move* action, it moves randomly to one of the adjacent squares. The robot’s task is to determine its current location.

* * *

LOCALIZATION

* * *

Suppose the robot has just been switched on, so it does not know where it is. Thus its initial belief state *b* consists of the set of all locations. The the robot receives the percept *NSW*, meaning there are obstacles to the north, west, and south, and does an update using the equation *b*[*o*] = UPDATE(*b*), yielding the 4 locations shown in [Figure 4.18](#index_split_011.html#filepos603436)(a). You can inspect the maze to see that those are the only four locations that yield the percept *NWS*.

> ![image](images/00098.jpg)

> **Figure 4.18** Possible positions of the robot, ![equ](images/00099.jpg), (a) after one observation *E*[1] = *NSW* and (b) after a second observation *E*[2] = *NS*. When sensors are noiseless and the transition model is accurate, there are no other possible locations for the robot consistent with this sequence of two observations.

Next the robot executes a *Move* action, but the result is nondeterministic. The new belief state, *b*[*a*] = PREDICT(*b*[*o*], *Move*), contains all the locations that are one step away from the locations in *b*[*o*]. When the second percept, *NS*, arrives, the robot does UPDATE(*b*[*a*], *NS*) and finds that the belief state has collapsed down to the single location shown in [Figure 4.18](#index_split_011.html#filepos603436)(b). That’s the only location that could be the result of

> UPDATE(PREDICT(UPDATE(*b*, *NSW*), *Move*), *NS*).

With nondetermnistic actions the PREDICT step grows the belief state, but the UPDATE step shrinks it back down—as long as the percepts provide some useful identifying information. Sometimes the percepts don’t help much for localization: If there were one or more long east-west corridors, then a robot could receive a long sequence of *NS* percepts, but never know where in the corridor(s) it was.

### 4.5 ONLINE SEARCH AGENTS AND UNKNOWN ENVIRONMENTS

So far we have concentrated on agents that use **offline search** algorithms. They compute a complete solution before setting foot in the real world and then execute the solution. In contrast, an **online search**[^(13)](#index_split_015.html#filepos5577335) agent **interleaves** computation and action: first it takes an action, then it observes the environment and computes the next action. Online search is a good idea in dynamic or semidynamic domains—domains where there is a penalty for sitting around and computing too long. Online search is also helpful in nondeterministic domains because it allows the agent to focus its computational efforts on the contingencies that actually arise rather than those that *might* happen but probably won’t. Of course, there is a tradeoff: the more an agent plans ahead, the less often it will find itself up the creek without a paddle.

* * *

OFFLINE SEARCH

* * *

* * *

ONLINE SEARCH

* * *

Online search is a *necessary* idea for unknown environments, where the agent does not know what states exist or what its actions do. In this state of ignorance, the agent faces an **exploration problem** and must use its actions as experiments in order to learn enough to make deliberation worthwhile.

* * *

EXPLORATION PROBLEM

* * *

The canonical example of online search is a robot that is placed in a new building and must explore it to build a map that it can use for getting from *A* to *B*. Methods for escaping from labyrinths—required knowledge for aspiring heroes of antiquity—are also examples of online search algorithms. Spatial exploration is not the only form of exploration, however. Consider a newborn baby: it has many possible actions but knows the outcomes of none of them, and it has experienced only a few of the possible states that it can reach. The baby’s gradual discovery of how the world works is, in part, an online search process.

#### **4.5.1 Online search problems**

An online search problem must be solved by an agent executing actions, rather than by pure computation. We assume a deterministic and fully observable environment ([Chapter 17](#index_split_015.html#filepos2562268) relaxes these assumptions), but we stipulate that the agent knows only the following:

> • ACTIONS(*s*), which returns a list of actions allowed in state *s*;

> • The step-cost function *c*(*s*, *a*, *s*′)—note that this cannot be used until the agent knows that *s*′ is the outcome; and

> • GOAL\-TEST(*s*).

Note in particular that the agent *cannot* determine RESULT(*s*, *a*) except by actually being in *s* and doing *a*. For example, in the maze problem shown in [Figure 4.19](#index_split_011.html#filepos609755), the agent does not know that going *Up* from (1,1) leads to (1,2); nor, having done that, does it know that going *Down* will take it back to (1,1). This degree of ignorance can be reduced in some applications—for example, a robot explorer might know how its movement actions work and be ignorant only of the locations of obstacles.

> ![image](images/00100.jpg)

> **Figure 4.19** A simple maze problem. The agent starts at *S* and must reach *G* but knows nothing of the environment.

> ![image](images/00101.jpg)

> **Figure 4.20** (a) Two state spaces that might lead an online search agent into a dead end. Any given agent will fail in at least one of these spaces. (b) A two-dimensional environment that can cause an online search agent to follow an arbitrarily inefficient route to the goal. Whichever choice the agent makes, the adversary blocks that route with another long, thin wall, so that the path followed is much longer than the best possible path.

Finally, the agent might have access to an admissible heuristic function *h*(*s*) that estimates the distance from the current state to a goal state. For example, in [Figure 4.19](#index_split_011.html#filepos609755), the agent might know the location of the goal and be able to use the Manhattan-distance heuristic.

Typically, the agent’s objective is to reach a goal state while minimizing cost. (Another possible objective is simply to explore the entire environment.) The cost is the total path cost of the path that the agent actually travels. It is common to compare this cost with the path cost of the path the agent would follow *if it knew the search space in advance*—that is, the actual shortest path (or shortest complete exploration). In the language of online algorithms, this is called the **competitive ratio**; we would like it to be as small as possible.

* * *

COMPETITIVE RATIO

* * *

Although this sounds like a reasonable request, it is easy to see that the best achievable competitive ratio is infinite in some cases. For example, if some actions are **irreversible**—i.e., they lead to a state from which no action leads back to the previous state—the online search might accidentally reach a **dead-end** state from which no goal state is reachable. Perhaps the term “accidentally” is unconvincing—after all, there might be an algorithm that happens not to take the dead-end path as it explores. Our claim, to be more precise, is that *no algorithm can avoid dead ends in all state spaces.* Consider the two dead-end state spaces in [Figure 4.20](#index_split_011.html#filepos610116)(a). To an online search algorithm that has visited states S and A, the two state spaces look *identical*, so it must make the same decision in both. Therefore, it will fail in one of them. This is an example of an **adversary argument**—we can imagine an adversary constructing the state space while the agent explores it and putting the goals and dead ends wherever it chooses.

* * *

IRREVERSIBLE

* * *

* * *

DEAD END

* * *

* * *

ADVERSARY ARGUMENT

* * *

![hand](images/00006.jpg)

Dead ends are a real difficulty for robot exploration—staircases, ramps, cliffs, one-way streets, and all kinds of natural terrain present opportunities for irreversible actions. To make progress, we simply assume that the state space is **safely explorable**—that is, some goal state is reachable from every reachable state. State spaces with reversible actions, such as mazes and 8-puzzles, can be viewed as undirected graphs and are clearly safely explorable.

* * *

SAFELY EXPLORABLE

* * *

Even in safely explorable environments, no bounded competitive ratio can be guaranteed if there are paths of unbounded cost. This is easy to show in environments with irreversible actions, but in fact it remains true for the reversible case as well, as [Figure 4.20](#index_split_011.html#filepos610116)(b) shows. For this reason, it is common to describe the performance of online search algorithms in terms of the size of the entire state space rather than just the depth of the shallowest goal.

#### **4.5.2 Online search agents**

After each action, an online agent receives a percept telling it what state it has reached; from this information, it can augment its map of the environment. The current map is used to decide where to go next. This interleaving of planning and action means that online search algorithms are quite different from the offline search algorithms we have seen previously. For example, offline algorithms such as A^(\*) can expand a node in one part of the space and then immediately expand a node in another part of the space, because node expansion involves simulated rather than real actions. An online algorithm, on the other hand, can discover successors only for a node that it physically occupies. To avoid traveling all the way across the tree to expand the next node, it seems better to expand nodes in a *local* order. Depth-first search has exactly this property because (except when backtracking) the next node expanded is a child of the previous node expanded.

An online depth-first search agent is shown in [Figure 4.21](#index_split_011.html#filepos616826). This agent stores its map in a table, RESULT\[*s*, *a*\], that records the state resulting from executing action *a* in state *s*. Whenever an action from the current state has not been explored, the agent tries that action. The difficulty comes when the agent has tried all the actions in a state. In offline depth-first search, the state is simply dropped from the queue; in an online search, the agent has to backtrack physically. In depth-first search, this means going back to the state from which the agent most recently entered the current state. To achieve that, the algorithm keeps a table that lists, for each state, the predecessor states to which the agent has not yet backtracked. If the agent has run out of states to which it can backtrack, then its search is complete.

> ![image](images/00102.jpg)

> **Figure 4.21** An online search agent that uses depth-first exploration. The agent is applicable only in state spaces in which every action can be “undone” by some other action.

We recommend that the reader trace through the progress of ONLINE\-DFS-AGENT when applied to the maze given in [Figure 4.19](#index_split_011.html#filepos609755). It is fairly easy to see that the agent will, in the worst case, end up traversing every link in the state space exactly twice. For exploration, this is optimal; for finding a goal, on the other hand, the agent’s competitive ratio could be arbitrarily bad if it goes off on a long excursion when there is a goal right next to the initial state. An online variant of iterative deepening solves this problem; for an environment that is a uniform tree, the competitive ratio of such an agent is a small constant.

Because of its method of backtracking, ONLINE\-DFS-AGENT works only in state spaces where the actions are reversible. There are slightly more complex algorithms that work in general state spaces, but no such algorithm has a bounded competitive ratio.

#### **4.5.3 Online local search**

Like depth-first search, **hill-climbing search** has the property of locality in its node expansions. In fact, because it keeps just one current state in memory, hill-climbing search is *already* an online search algorithm! Unfortunately, it is not very useful in its simplest form because it leaves the agent sitting at local maxima with nowhere to go. Moreover, random restarts cannot be used, because the agent cannot transport itself to a new state.

* * *

RANDOM WALK

* * *

Instead of random restarts, one might consider using a **random walk** to explore the environment. A random walk simply selects at random one of the available actions from the current state; preference can be given to actions that have not yet been tried. It is easy to prove that a random walk will *eventually* find a goal or complete its exploration, provided that the space is finite.[^(14)](#index_split_015.html#filepos5577654) On the other hand, the process can be very slow. [Figure 4.22](#index_split_011.html#filepos620007) shows an environment in which a random walk will take exponentially many steps to find the goal because, at each step, backward progress is twice as likely as forward progress. The example is contrived, of course, but there are many real-world state spaces whose topology causes these kinds of “traps” for random walks.

> ![image](images/00103.jpg)

> **Figure 4.22** An environment in which a random walk will take exponentially many steps to find the goal.

Augmenting hill climbing with *memory* rather than randomness turns out to be a more effective approach. The basic idea is to store a “current best estimate” *H*(*s*) of the cost to reach the goal from each state that has been visited. *H*(*s*) starts out being just the heuristic estimate *h*(*s*) and is updated as the agent gains experience in the state space. [Figure 4.23](#index_split_011.html#filepos623806) shows a simple example in a one-dimensional state space. In (*a*), the agent seems to be stuck in a flat local minimum at the shaded state. Rather than staying where it is, the agent should follow what seems to be the best path to the goal given the current cost estimates for its neighbors. The estimated cost to reach the goal through a neighbor *s*′ is the cost to get to *s*′ plus the estimated cost to get to a goal from there—that is, *c*(*s*, *a*, *s*′)+ *H*(*s*′). In the example, there are two actions, with estimated costs 1 + 9 and 1 + 2, so it seems best to move right. Now, it is clear that the cost estimate of 2 for the shaded state was overly optimistic. Since the best move cost 1 and led to a state that is at least 2 steps from a goal, the shaded state must be at least 3 steps from a goal, so its *H* should be updated accordingly, as shown in [Figure 4.23](#index_split_011.html#filepos623806)(b). Continuing this process, the agent will move back and forth twice more, updating *H* each time and “flattening out” the local minimum until it escapes to the right.

An agent implementing this scheme, which is called learning real-time A^(\*) (**LRTA**^(\*)), is shown in [Figure 4.24](#index_split_011.html#filepos624374). Like ONLINE\-DFS-AGENT, it builds a map of the environment in the result table. It updates the cost estimate for the state it has just left and then chooses the “apparently best” move according to its current cost estimates. One important detail is that actions that have not yet been tried in a state *s* are always assumed to lead immediately to the goal with the least possible cost, namely *h*(*s*). This **optimism under uncertainty** encourages the agent to explore new, possibly promising paths.

* * *

LRTA\*

* * *

* * *

OPTIMISM UNDER UNCERTAINTY

* * *

An LRTA^(\*) agent is guaranteed to find a goal in any finite, safely explorable environment. Unlike A^(\*), however, it is not complete for infinite state spaces—there are cases where it can be led infinitely astray. It can explore an environment of *n* states in *O*(*n*²) steps in the worst case, but often does much better. The LRTA^(\*) agent is just one of a large family of online agents that one can define by specifying the action selection rule and the update rule in different ways. We discuss this family, developed originally for stochastic environments, in [Chapter 21](#index_split_015.html#filepos3262268).

> ![image](images/00104.jpg)

> **Figure 4.23** Five iterations of LRTA^(\*) on a one-dimensional state space. Each state is labeled with *H*(*s*), the current cost estimate to reach a goal, and each link is labeled with its step cost. The shaded state marks the location of the agent, and the updated cost estimates at each iteration are circled.

> ![image](images/00105.jpg)

> **Figure 4.24** LRTA\*-AGENT selects an action according to the values of neighboring states, which are updated as the agent moves about the state space.

#### **4.5.4 Learning in online search**

The initial ignorance of online search agents provides several opportunities for learning. First, the agents learn a “map” of the environment—more precisely, the outcome of each action in each state—simply by recording each of their experiences. (Notice that the assumption of deterministic environments means that one experience is enough for each action.) Second, the local search agents acquire more accurate estimates of the cost of each state by using local updating rules, as in LRTA^(\*). In [Chapter 21](#index_split_015.html#filepos3262268), we show that these updates eventually converge to *exact* values for every state, provided that the agent explores the state space in the right way. Once exact values are known, optimal decisions can be taken simply by moving to the lowest-cost successor—that is, pure hill climbing is then an optimal strategy.

If you followed our suggestion to trace the behavior of ONLINE\-DFS-AGENT in the environment of [Figure 4.19](#index_split_011.html#filepos609755), you will have noticed that the agent is not very bright. For example, after it has seen that the *Up* action goes from (1,1) to (1,2), the agent still has no idea that the *Down* action goes back to (1,1) or that the *Up* action also goes from (2,1) to (2,2), from (2,2) to (2,3), and so on. In general, we would like the agent to learn that *Up* increases the *y*\-coordinate unless there is a wall in the way, that *Down* reduces it, and so on. For this to happen, we need two things. First, we need a formal and explicitly manipulable representation for these kinds of general rules; so far, we have hidden the information inside the black box called the RESULT function. Part III is devoted to this issue. Second, we need algorithms that can construct suitable general rules from the specific observations made by the agent. These are covered in [Chapter 18](#index_split_015.html#filepos2753020).

### 4.6 SUMMARY

This chapter has examined search algorithms for problems beyond the “classical” case of finding the shortest path to a goal in an observable, deterministic, discrete environment.

> • *Local search* methods such as **hill climbing** operate on complete-state formulations, keeping only a small number of nodes in memory. Several stochastic algorithms have been developed, including **simulated annealing**, which returns optimal solutions when given an appropriate cooling schedule.

> • Many local search methods apply also to problems in continuous spaces. **Linear programming** and **convex optimization** problems obey certain restrictions on the shape of the state space and the nature of the objective function, and admit polynomial-time algorithms that are often extremely efficient in practice.

> • A **genetic algorithm** is a stochastic hill-climbing search in which a large population of states is maintained. New states are generated by **mutation** and by **crossover**, which combines pairs of states from the population.

> • In **nondeterministic** environments, agents can apply AND–OR search to generate **contingent** plans that reach the goal regardless of which outcomes occur during execution.

> • When the environment is partially observable, the **belief state** represents the set of possible states that the agent might be in.

> • Standard search algorithms can be applied directly to belief-state space to solve **sensorless problems**, and belief-state AND–OR search can solve general partially observable problems. Incremental algorithms that construct solutions state-by-state within a belief state are often more efficient.

> • **Exploration problems** arise when the agent has no idea about the states and actions of its environment. For safely explorable environments, **online search** agents can build a map and find a goal if one exists. Updating heuristic estimates from experience provides an effective method to escape from local minima.

### BIBLIOGRAPHICAL AND HISTORICAL NOTES

Local search techniques have a long history in mathematics and computer science. Indeed, the Newton–Raphson method (Newton, 1671; Raphson, 1690) can be seen as a very efficient local search method for continuous spaces in which gradient information is available. Brent (1973) is a classic reference for optimization algorithms that do not require such information. Beam search, which we have presented as a local search algorithm, originated as a bounded-width variant of dynamic programming for speech recognition in the HARPY system (Lowerre, 1976). A related algorithm is analyzed in depth by Pearl (1984, [Ch. 5](#index_split_000.html#filepos660071)).

The topic of local search was reinvigorated in the early 1990s by surprisingly good results for large constraint-satisfaction problems such as *n*\-queens (Minton **et al.**, 1992) and logical reasoning (Selman **et al.**, 1992) and by the incorporation of randomness, multiple simultaneous searches, and other improvements. This renaissance of what Christos Papadimitriou has called “New Age” algorithms also sparked increased interest among theoretical computer scientists (Koutsoupias and Papadimitriou, 1992; Aldous and Vazirani, 1994). In the field of operations research, a variant of hill climbing called **tabu search** has gained popularity (Glover and Laguna, 1997). This algorithm maintains a tabu list of *k* previously visited states that cannot be revisited; as well as improving efficiency when searching graphs, this list can allow the algorithm to escape from some local minima. Another useful improvement on hill climbing is the STAGE algorithm (Boyan and Moore, 1998). The idea is to use the local maxima found by random-restart hill climbing to get an idea of the overall shape of the landscape. The algorithm fits a smooth surface to the set of local maxima and then calculates the global maximum of that surface analytically. This becomes the new restart point. The algorithm has been shown to work in practice on hard problems. Gomes **et al.** (1998) showed that the run times of systematic backtracking algorithms often have a **heavy-tailed distribution**, which means that the probability of a very long run time is more than would be predicted if the run times were exponentially distributed. When the run time distribution is heavy-tailed, random restarts find a solution faster, on average, than a single run to completion.

* * *

TABU SEARCH

* * *

* * *

HEAVY-TAILED DISTRIBUTION

* * *

Simulated annealing was first described by Kirkpatrick **et al.** (1983), who borrowed directly from the **Metropolis algorithm** (which is used to simulate complex systems in physics (Metropolis **et al.**, 1953) and was supposedly invented at a Los Alamos dinner party). Simulated annealing is now a field in itself, with hundreds of papers published every year.

Finding optimal solutions in continuous spaces is the subject matter of several fields, including **optimization theory**, **optimal control theory**,andthe **calculus of variations**. The basic techniques are explained well by Bishop (1995); Press **et al.** (2007) cover a wide range of algorithms and provide working software.

As Andrew Moore points out, researchers have taken inspiration for search and optimization algorithms from a wide variety of fields of study: metallurgy (simulated annealing), biology (genetic algorithms), economics (market-based algorithms), entomology (ant colony optimization), neurology (neural networks), animal behavior (reinforcement learning), mountaineering (hill climbing), and others.

**Linear programming** (LP) was first studied systematically by the Russian mathematician Leonid Kantorovich (1939). It was one of the first applications of computers; the **simplex algorithm** (Dantzig, 1949) is still used despite worst-case exponential complexity. Karmarkar (1984) developed the far more efficient family of **interior-point** methods, which was shown to have polynomial complexity for the more general class of convex optimization problems by Nesterov and Nemirovski (1994). Excellent introductions to convex optimization are provided by Ben-Tal and Nemirovski (2001) and Boyd and Vandenberghe (2004).

Work by Sewall Wright (1931) on the concept of a **fitness landscape** was an important precursor to the development of genetic algorithms. In the 1950s, several statisticians, including Box (1957) and Friedman (1959), used evolutionary techniques for optimization problems, but it wasn’t until Rechenberg (1965) introduced **evolution strategies** to solve optimization problems for airfoils that the approach gained popularity. In the 1960s and 1970s, John Holland (1975) championed genetic algorithms, both as a useful tool and as a method to expand our understanding of adaptation, biological or otherwise (Holland, 1995). The **artificial life** movement (Langton, 1995) takes this idea one step further, viewing the products of genetic algorithms as *organisms* rather than solutions to problems. Work in this field by Hinton and Nowlan (1987) and Ackley and Littman (1991) has done much to clarify the implications of the Baldwin effect. For general background on evolution, we recommend Smith and Szathmàry (1999), Ridley (2004), and Carroll (2007).

* * *

EVOLUTION STRATEGY

* * *

* * *

ARTIFICIAL LIFE

* * *

Most comparisons of genetic algorithms to other approaches (especially stochastic hill climbing) have found that the genetic algorithms are slower to converge (O’Reilly and Oppacher, 1994; Mitchell **et al.**, 1996; Juels and Wattenberg, 1996; Baluja, 1997). Such findings are not universally popular within the GA community, but recent attempts within that community to understand population-based search as an approximate form of Bayesian learning (see [Chapter 20](#index_split_015.html#filepos3158034)) might help close the gap between the field and its critics (Pelikan **et al.**, 1999). The theory of **quadratic dynamical systems** may also explain the performance of GAs (Rabani **et al.**, 1998). See Lohn **et al.** (2001) for an example of GAs applied to antenna design, and Renner and Ekart (2003) for an application to computer-aided design.

The field of **genetic programming** is closely related to genetic algorithms. The principal difference is that the representations that are mutated and combined are programs rather than bit strings. The programs are represented in the form of expression trees; the expressions can be in a standard language such as Lisp or can be specially designed to represent circuits, robot controllers, and so on. Crossover involves splicing together subtrees rather than substrings. This form of mutation guarantees that the offspring are well-formed expressions, which would not be the case if programs were manipulated as strings.

* * *

GENETIC PROGRAMMING

* * *

Interest in genetic programming was spurred by John Koza’s work (Koza, 1992, 1994), but it goes back at least to early experiments with machine code by Friedberg (1958) and with finite-state automata by Fogel **et al.** (1966). As with genetic algorithms, there is debate about the effectiveness of the technique. Koza **et al.** (1999) describe experiments in the use of genetic programming to design circuit devices.

The journals *Evolutionary Computation* and *IEEE Transactions on Evolutionary Computation* cover genetic algorithms and genetic programming; articles are also found in *Complex Systems*, *Adaptive Behavior*, and *Artificial Life*. The main conference is the *Genetic and Evolutionary Computation Conference* (GECCO). Good overview texts on genetic algorithms are given by Mitchell (1996), Fogel (2000), and Langdon and Poli (2002), and by the free online book by Poli **et al.** (2008).

The unpredictability and partial observability of real environments were recognized early on in robotics projects that used planning techniques, including Shakey (Fikes **et al.**, 1972) and FREDDY (Michie, 1974). The problems received more attention after the publication of McDermott’s (1978a) influential article, *Planning and Acting*.

The first work to make explicit use of AND–OR trees seems to have been Slagle’s SAINT program for symbolic integration, mentioned in [Chapter 1](#index_split_000.html#filepos57382). Amarel (1967) applied the idea to propositional theorem proving, a topic discussed in [Chapter 7](#index_split_000.html#filepos939379), and introduced a search algorithm similar to AND\-OR\-GRAPH\-SEARCH. The algorithm was further developed and formalized by Nilsson (1971), who also described AO^(\*)—which, as its name suggests, finds optimal solutions given an admissible heuristic. AO^(\*) was analyzed and improved by Martelli and Montanari (1973). AO^(\*) is a top-down algorithm; a bottom-up generalization of A^(\*) is A\*LD, for A^(\*) Lightest Derivation (Felzenszwalb and McAllester, 2007). Interest in AND–OR search has undergone a revival in recent years, with new algorithms for finding cyclic solutions (Jimenez and Torras, 2000; Hansen and Zilberstein, 2001) and new techniques inspired by dynamic programming (Bonet and Geffner, 2005).

The idea of transforming partially observable problems into belief-state problems originated with Astrom (1965) for the much more complex case of probabilistic uncertainty (see [Chapter 17](#index_split_015.html#filepos2562268)). Erdmann and Mason (1988) studied the problem of robotic manipulation without sensors, using a continuous form of belief-state search. They showed that it was possible to orient a part on a table from an arbitrary initial position by a well-designed sequence of tilting actions. More practical methods, based on a series of precisely oriented diagonal barriers across a conveyor belt, use the same algorithmic insights (Wiegley **et al.**, 1996).

The belief-state approach was reinvented in the context of sensorless and partially observable search problems by Genesereth and Nourbakhsh (1993). Additional work was done on sensorless problems in the logic-based planning community (Goldman and Boddy, 1996;Smith and Weld, 1998). This work has emphasized concise representations for belief states, as explained in [Chapter 11](#index_split_015.html#filepos1612250). Bonet and Geffner (2000) introduced the first effective heuristics for belief-state search; these were refined by Bryce **et al.** (2006). The incremental approach to belief-state search, in which solutions are constructed incrementally for subsets of states within each belief state, was studied in the planning literature by Kurien **et al.** (2002); several new incremental algorithms were introduced for nondeterministic, partially observable problems by Russell and Wolfe (2005). Additional references for planning in stochastic, partially observable environments appear in [Chapter 17](#index_split_015.html#filepos2562268).

Algorithms for exploring unknown state spaces have been of interest for many centuries. Depth-first search in a maze can be implemented by keeping one’s left hand on the wall; loops can be avoided by marking each junction. Depth-first search fails with irreversible actions; the more general problem of exploring **Eulerian graphs** (i.e., graphs in which each node has equal numbers of incoming and outgoing edges) was solved by an algorithm due to Hierholzer (1873). The first thorough algorithmic study of the exploration problem for arbitrary graphs was carried out by Deng and Papadimitriou (1990), who developed a completely general algorithm but showed that no bounded competitive ratio is possible for exploring a general graph. Papadimitriou and Yannakakis (1991) examined the question of finding paths to a goal in geometric path-planning environments (where all actions are reversible). They showed that a small competitive ratio is achievable with square obstacles, but with general rectangular obstacles no bounded ratio can be achieved. (See [Figure 4.20](#index_split_011.html#filepos610116).)

* * *

EULERIAN GRAPH

* * *

The LRTA^(\*) algorithm was developed by Korf (1990) as part of an investigation into **real-time search** for environments in which the agent must act after searching for only a fixed amount of time (a common situation in two-player games). LRTA^(\*) is in fact a special case of reinforcement learning algorithms for stochastic environments (Barto **et al.**, 1995). Its policy of optimism under uncertainty—always head for the closest unvisited state—can result in an exploration pattern that is less efficient in the uninformed case than simple depth-first search (Koenig, 2000). Dasgupta **et al.** (1994) show that online iterative deepening search is optimally efficient for finding a goal in a uniform tree with no heuristic information. Several informed variants on the LRTA^(\*) theme have been developed with different methods for searching and updating within the known portion of the graph (Pemberton and Korf, 1992). As yet, there is no good understanding of how to find goals with optimal efficiency when using heuristic information.

* * *

REAL-TIME SEARCH

* * *

### EXERCISES

**4.1** Give the name of the algorithm that results from each of the following special cases:

> **a**. Local beam search with *k* = 1.

> **b**. Local beam search with one initial state and no limit on the number of states retained.

> **c**. Simulated annealing with *T* = 0 at all times (and omitting the termination test).

> **d**. Simulated annealing with *T* = ∞ at all times.

> **e**. Genetic algorithm with population size *N* = 1.

**4.2** Exercise 3.16 considers the problem of building railway tracks under the assumption that pieces fit exactly with no slack. Now consider the real problem, in which pieces don’t fit exactly but allow for up to 10 degrees of rotation to either side of the “proper” alignment. Explain how to formulate the problem so it could be solved by simulated annealing.

**4.3** In this exercise, we explore the use of local search methods to solve TSPs of the type defined in Exercise 3.30.

> **a**. Implement and test a hill-climbing method to solve TSPs. Compare the results with optimal solutions obtained from the A^(\*) algorithm with the MST heuristic (Exercise 3.30).

> **b**. Repeat part (a) using a genetic algorithm instead of hill climbing. You may want to consult Larrañaga **et al.** (1999) for some suggestions for representations.

![radio](images/00004.jpg)

**4.4** Generate a large number of 8-puzzle and 8-queens instances and solve them (where possible) by hill climbing (steepest-ascent and first-choice variants), hill climbing with random restart, and simulated annealing. Measure the search cost and percentage of solved problems and graph these against the optimal solution cost. Comment on your results.

![radio](images/00004.jpg)

**4.5** The AND\-OR\-GRAPH\-SEARCH algorithm in [Figure 4.11](#index_split_011.html#filepos569895) checks for repeated states only on the path from the root to the current state. Suppose that, in addition, the algorithm were to store *every* visited state and check against that list. (See BREADTH\-FIRST\-SEARCH in [Figure 3.11](#index_split_010.html#filepos371533) for an example.) Determine the information that should be stored and how the algorithm should use that information when a repeated state is found. (*Hint*: You will need to distinguish at least between states for which a successful subplan was constructed previously and states for which no subplan could be found.) Explain how to use labels, as defined in [Section 4.3.3](#index_split_000.html#filepos572500), to avoid having multiple copies of subplans.

**4.6** Explain precisely how to modify the AND\-OR\-GRAPH\-SEARCH algorithm to generate a cyclic plan if no acyclic plan exists. You will need to deal with three issues: labeling the plan steps so that a cyclic plan can point back to an earlier part of the plan, modifying OR-SEARCH so that it continues to look for acyclic plans after finding a cyclic plan, and augmenting the plan representation to indicate whether a plan is cyclic. Show how your algorithm works on (a) the slippery vacuum world, and (b) the slippery, erratic vacuum world. You might wish to use a computer implementation to check your results.

![radio](images/00004.jpg)

**4.7** In [Section 4.4.1](#index_split_000.html#filepos576796) we introduced belief states to solve sensorless search problems. A sequence of actions solves a sensorless problem if it maps every physical state in the initial belief state *b* to a goal state. Suppose the agent knows *h*^(\*)(*s*), the true optimal cost of solving the physical state *s* in the fully observable problem, for every state *s* in *b*. Find an admissible heuristic *h*(*b*) for the sensorless problem in terms of these costs, and prove its admissibilty. Comment on the accuracy of this heuristic on the sensorless vacuum problem of [Figure 4.14](#index_split_011.html#filepos588778). How well does A^(\*) perform?

**4.8** This exercise explores subset–superset relations between belief states in sensorless or partially observable environments.

> **a**. Prove that if an action sequence is a solution for a belief state *b*, it is also a solution for any subset of *b*. Can anything be said about supersets of *b*?

> **b**. Explain in detail how to modify graph search for sensorless problems to take advantage of your answers in (a).

> **c**. Explain in detail how to modify AND–OR search for partially observable problems, beyond the modifications you describe in (b).

**4.9** [On page 139](#index_split_011.html#filepos579399) it was assumed that a given action would have the same cost when executed in any physical state within a given belief state. (This leads to a belief-state search problem with well-defined step costs.) Now consider what happens when the assumption does not hold. Does the notion of optimality still make sense in this context, or does it require modification? Consider also various possible definitions of the “cost” of executing an action in a belief state; for example, we could use the *minimum* of the physical costs; or the *maximum*; or a cost *interval* with the lower bound being the minimum cost and the upper bound being the maximum; or just keep the set of all possible costs for that action. For each of these, explore whether A^(\*) (with modifications if necessary) can return optimal solutions.

**4.10** Consider the sensorless version of the erratic vacuum world. Draw the belief-state space reachable from the initial belief state {1, 2, 3, 4, 5, 6, 7, 8}, and explain why the problem is unsolvable.

![radio](images/00004.jpg)

**4.11** We can turn the navigation problem in Exercise 3.7 into an environment as follows:

> • The percept will be a list of the positions, *relative to the agent*, of the visible vertices. The percept does *not* include the position of the robot! The robot must learn its own position from the map; for now, you can assume that each location has a different “view.”

> • Each action will be a vector describing a straight-line path to follow. If the path is unobstructed, the action succeeds; otherwise, the robot stops at the point where its path first intersects an obstacle. If the agent returns a zero motion vector and is at the goal (which is fixed and known), then the environment teleports the agent to a *random location* (not inside an obstacle).

> • The performance measure charges the agent 1 point for each unit of distance traversed and awards 1000 points each time the goal is reached.

> **a**. Implement this environment and a problem-solving agent for it. After each teleportation, the agent will need to formulate a new problem, which will involve discovering its current location.

> **b**. Document your agent’s performance (by having the agent generate suitable commentary as it moves around) and report its performance over 100 episodes.

> **c**. Modify the environment so that 30% of the time the agent ends up at an unintended destination (chosen randomly from the other visible vertices if any; otherwise, no move at all). This is a crude model of the motion errors of a real robot. Modify the agent so that when such an error is detected, it finds out where it is and then constructs a plan to get back to where it was and resume the old plan. Remember that sometimes getting back to where it was might also fail! Show an example of the agent successfully overcoming two successive motion errors and still reaching the goal.

> **d**. Now try two different recovery schemes after an error: (1) head for the closest vertex on the original route; and (2) replan a route to the goal from the new location. Compare the performance of the three recovery schemes. Would the inclusion of search costs affect the comparison?

> **e**. Now suppose that there are locations from which the view is identical. (For example, suppose the world is a grid with square obstacles.) What kind of problem does the agent now face? What do solutions look like?

**4.12** Suppose that an agent is in a 3 × 3 maze environment like the one shown in [Figure 4.19](#index_split_011.html#filepos609755). The agent knows that its initial location is (1,1), that the goal is at (3,3), and that the actions *Up*, *Down*, *Left*, *Right* have their usual effects unless blocked by a wall. The agent does *not* know where the internal walls are. In any given state, the agent perceives the set of legal actions; it can also tell whether the state is one it has visited before.

> **a**. Explain how this online search problem can be viewed as an offline search in belief-state space, where the initial belief state includes all possible environment configurations. How large is the initial belief state? How large is the space of belief states?

> **b**. How many distinct percepts are possible in the initial state?

> **c**. Describe the first few branches of a contingency plan for this problem. How large (roughly) is the complete plan?

Notice that this contingency plan is a solution for *every possible environment* fitting the given description. Therefore, interleaving of search and execution is not strictly necessary even in unknown environments.

**4.13** In this exercise, we examine hill climbing in the context of robot navigation, using the environment in [Figure 3.31](#index_split_010.html#filepos487681) as an example.

> **a**. Repeat Exercise 4.11 using hill climbing. Does your agent ever get stuck in a local minimum? Is it *possible* for it to get stuck with convex obstacles?

> **b**. Construct a nonconvex polygonal environment in which the agent gets stuck.

> **c**. Modify the hill-climbing algorithm so that, instead of doing a depth-1 search to decide where to go next, it does a depth-*k* search. It should find the best *k*\-step path and do one step along it, and then repeat the process.

> **d**. Istheresome *k* for which the new algorithm is guaranteed to escape from local minima?

> **e**. Explain how LRTA^(\*) enables the agent to escape from local minima in this case.

![radio](images/00004.jpg)

**4.14** Like DFS, online DFS is incomplete for reversible state spaces with infinite paths. For example, suppose that states are points on the infinite two-dimensional grid and actions are unit vectors (1, 0), (0, 1), (−1, 0), (0, −1), tried in that order. Show that online DFS starting at (0, 0) will not reach (1, −1). Suppose the agent can observe, in addition to its current state, all successor states and the actions that would lead to them. Write an algorithm that is complete even for bidirected state spaces with infinite paths. What states does it visit in reaching (1, −1)?

## **5 ADVERSARIAL SEARCH**

> *In which we examine the problems that arise when we try to plan ahead in a world where other agents are planning against us.*

### 5.1 GAMES

[Chapter 2](#index_split_000.html#filepos187684) introduced **multiagent environments,** in which each agent needs to consider the actions of other agents and how they affect its own welfare. The unpredictability of these other agents can introduce **contingencies** into the agent’s problem-solving process, as discussed in [Chapter 4](#index_split_000.html#filepos513290). In this chapter we cover **competitive** environments, in which the agents’ goals are in conflict, giving rise to **adversarial search** problems—often known as **games.**

* * *

GAME

* * *

Mathematical **game theory,** a branch of economics, views any multiagent environment as a game, provided that the impact of each agent on the others is “significant,” regardless of whether the agents are cooperative or competitive.[¹](#index_split_015.html#filepos5577974) In AI, the most common games are of a rather specialized kind—what game theorists call deterministic, turn-taking, two-player, **zero-sum games** of **perfect information**(such as chess). In our terminology, this means deterministic, fully observable environments in which two agents act alternately and in which the utility values at the end of the game are always equal and opposite. For example, if one player wins a game of chess, the other player necessarily loses. It is this opposition between the agents’ utility functions that makes the situation adversarial.

* * *

ZERO-SUM GAMES

* * *

* * *

PERFECT INFORMATION

* * *

Games have engaged the intellectual faculties of humans—sometimes to an alarming degree—for as long as civilization has existed. For AI researchers, the abstract nature of games makes them an appealing subject for study. The state of a game is easy to represent, and agents are usually restricted to a small number of actions whose outcomes are defined by precise rules. Physical games, such as croquet and ice hockey, have much more complicated descriptions, a much larger range of possible actions, and rather imprecise rules defining the legality of actions. With the exception of robot soccer, these physical games have not attracted much interest in the AI community.

Games, unlike most of the toy problems studied in [Chapter 3](#index_split_000.html#filepos301685), are interesting *because* they are too hard to solve. For example, chess has an average branching factor of about 35, and games often go to 50 moves by each player, so the search tree has about 35**^(100)** or 10**^(154)** nodes (although the search graph has “only” about 10^(40) distinct nodes). Games, like the real world, therefore require the ability to make *some* decision even when calculating the *optimal* decision is infeasible. Games also penalize inefficiency severely. Whereas an implementation of A\* search that is half as efficient will simply take twice as long to run to completion, a chess program that is half as efficient in using its available time probably will be beaten into the ground, other things being equal. Gameplaying research has therefore spawned a number of interesting ideas on how to make the best possible use of time.

We begin with a definition of the optimal move and an algorithm for finding it. We then look at techniques for choosing a good move when time is limited. **Pruning** allows us to ignore portions of the search tree that make no difference to the final choice, and heuristic **evaluation functions** allow us to approximate the true utility of a state without doing a complete search. [Section 5.5](#index_split_000.html#filepos717429) discusses games such as backgammon that include an element of chance; we also discuss bridge, which includes elements of **imperfect information** because not all cards are visible to each player. Finally, we look at how state-of-the-art gameplaying programs fare against human opposition and at directions for future developments.

* * *

PRUNING

* * *

* * *

IMPERFECT INFORMATION

* * *

We first consider games with two players, whom we call max and minfor reasons that will soon become obvious. maxmoves first, and then they take turns moving until the game is over. At the end of the game, points are awarded to the winning player and penalties are given to the loser. A game can be formally defined as a kind of search problem with the following elements:

> • *S[0]*: The **initial state,** which specifies how the game is set up at the start.

> • PLAYER(*s*): Defines which player has the move in a state.

> • ACTIONS(*s*): Returns the set of legal moves in a state.

> • RESULT(*s,a*): The **transition model,** which defines the result of a move.

> • TERMINAL\-TEST(*s*): A **terminal test,** which is true when the game is over and false otherwise. States where the game has ended are called **terminal states.**

* * *

TERMINAL TEST

* * *

* * *

TERMINAL STATES

* * *

> • UTILITY (*s,p*): A **utility function**(also called an objective function or payoff function), defines the final numeric value for a game that ends in terminal states for a playerp.In chess, the outcome is a win, loss, or draw, with values + 1, 0, or ½. Some games have a wider variety of possible outcomes; the payoffs in backgammon range from 0 to + 192. A **zero-sum game** is (confusingly) defined as one where the total payoff to all players is the same for every instance of the game. Chess is zero-sum because every game has payoff of either 0 + 1, 1 + 0 or ½ + ½. “Constant-sum” would have been a better term, but zero-sum is traditional and makes sense if you imagine each player is charged an entry fee of ½.

* * *

GAME TREE

* * *

The initial state, ACTIONS function, and RESULT function define the **game tree** for the game—a tree where the nodes are game states and the edges are moves. [Figure 5.1](#index_split_012.html#filepos669668) shows part of the game tree for tic-tac-toe (noughts and crosses). From the initial state, MAX has nine possible moves. Play alternates between MAX’s placing an X and MIN’s placing an Ountil we reach leaf nodes corresponding to terminal states such that one player has three in a row or all the squares are filled. The number on each leaf node indicates the utility value of the terminal state from the point of view of MAX; high values are assumed to be good for MAX and bad for MIN (which is how the players get their names).

For tic-tac-toe the game tree is relatively small—fewer than 9! = 362,880 terminal nodes. But for chess there are over 10^(40)nodes, so the game tree is best thought of as a theoretical construct that we cannot realize in the physical world. But regardless of the size of the game tree, it is MAX’s job to search for a good move. We use the term **search tree** for a tree that is superimposed on the full game tree, and examines enough nodes to allow a player to determine what move to make.

* * *

SEARCH TREE

* * *

> ![image](images/00106.jpg)

> **Figure 5.1** A (partial) game tree for the game of tic-tac-toe. The top node is the initial state, and MAX moves first, placing an X in an empty square. We show part of the tree, giving alternating moves by MIN (*O*) and MAX (*X*),until we eventually reach terminal states, which can be assigned utilities according to the rules of the game.

### 5.2 OPTIMAL DECISIONS IN GAMES

In a normal search problem, the optimal solution would be a sequence of actions leading to a goal state—a terminal state that is a win. In adversarial search, MIN has something to say strategy about it. MAX therefore must find a contingent **strategy,** which specifies MAX’s move in the initial state, then MAX’s moves in the states resulting from every possible response by MIN, then MAX’s moves in the states resulting from every possible response by MIN to *those* moves, and so on. This is exactly analogous to the AND\-OR search algorithm ([Figure 4.11](#index_split_011.html#filepos569895)) with MAX playing the role of OR and MIN equivalent to AND. Roughly speaking, an optimal strategy leads to outcomes at least as good as any other strategy when one is playing an infallible opponent. We begin by showing how to find this optimal strategy.

* * *

STRATEGY

* * *

> ![image](images/00107.jpg)

> **Figure 5.2** A two-ply game tree. The Δ nodes are “MAX nodes,” in which it is MAX’s turn to move, and the ▽ nodes are “MIN nodes.” The terminal nodes show the utility values for MAX; the other nodes are labeled with their minimax values. MAX’s best move at the root is *a*[1] because it leads to the state with the highest minimax value, and MIN’sbest reply is *b*[1] because it leads to the state with the lowest minimax value.

Even a simple game like tic-tac-toe is too complex for us to draw the entire game tree on one page, so we will switch to the trivial game in [Figure 5.2](#index_split_012.html#filepos671688). The possible moves for MAX at the root node are labeled *a*[1], *a*[2], and *a*[3]. The possible replies to *a*[1] for MIN are *b*[1], *b*[2], *b*[3], and so on. This particular game ends after one move each by MAX and MIN. (In game parlance, we say that this tree is one move deep, consisting of two half-moves, each of which is called a **ply**.) The utilities of the terminal states in this game range from 2 to 14.

* * *

PLY

* * *

Given a game tree, the optimal strategy can be determined from the **minimax value** of each node, which we write as MINIMAX(*n*). The minimax value of a node is the utility (for MAX)of being in the corresponding state, *assuming that both players play optimally* from there to the end of the game. Obviously, the minimax value of a terminal state is just its utility. Furthermore, given a choice, MAX prefers to move to a state of maximum value, whereas M INprefers a state of minimum value. So we have the following:

* * *

MINIMAX VALUE

* * *

> ![equ](images/00108.jpg)

Let us apply these definitions to the game tree in [Figure 5.2](#index_split_012.html#filepos671688). The terminal nodes on the bottom level get their utility values from the game’s UTILITY function. The first minnode, labeled *B*, has three successor states with values 3, 12, and 8, so its minimax value is 3. Similarly, the other two MIN nodes have minimax value 2. The root node is a MAX node; its successor states have minimax values 3, 2, and 2; so it has a minimax value of 3. We can also identify minimax decision the **minimax decision** at the root: action *a[1]* is the optimal choice for MAX because it leads to the state with the highest minimax value.

* * *

MINIMAX DECISION

* * *

This definition of optimal play for MAX assumes that minalso plays optimally—it maximizes the *worst-case* outcome for MAX. What if MIN does not play optimally? Then it is easy to show (Exercise 5.7) that MAX will do even better. Other strategies against suboptimal opponents may do better than the minimax strategy, but these strategies necessarily do worse against optimal opponents.

#### **5.2.1 The minimax algorithm**

The **minimax algorithm**([Figure 5.3](#index_split_012.html#filepos681233)) computes the minimax decision from the current state. It uses a simple recursive computation of the minimax values of each successor state, directly implementing the defining equations. The recursion proceeds all the way down to the leaves of the tree, and then the minimax values are **backed up** through the tree as the recursion unwinds. For example, in [Figure 5.2](#index_split_012.html#filepos671688), the algorithm first recurses down to the three bottom-left nodes and uses the UTILITY function on them to discover that their values are 3, 12, and 8, respectively. Then it takes the minimum of these values, 3, and returns it as the backed-up value of node *B*. A similar process gives the backed-up values of 2 for *C* and 2 for *D*. Finally, we take the maximum of 3, 2, and 2 to get the backed-up value of 3 for the root node.

* * *

MINIMAX ALGORITHM

* * *

The minimax algorithm performs a complete depth-first exploration of the game tree. If the maximum depth of the tree is *m* and there are *b* legal moves at each point, then the time complexity of the minimax algorithm is *O*(*b*^(*m*)). The space complexity is *O*(*bm*) for an algorithm that generates all actions at once, or *O*(*m*) for an algorithm that generates actions one at a time (see [page 87](#index_split_010.html#filepos385788)). For real games, of course, the time cost is totally impractical, but this algorithm serves as the basis for the mathematical analysis of games and for more practical algorithms.

#### **5.2.2 Optimal decisions in multiplayer games**

Many popular games allow more than two players. Let us examine how to extend the minimax idea to multiplayer games. This is straightforward from the technical viewpoint, but raises some interesting new conceptual issues.

First, we need to replace the single value for each node with a *vector* of values. For example, in a three-player game with players *A, B*, and *C*, a vector (*v[A]*, *v*[*B*], *v*[*C*]) is associated with each node. For terminal states, this vector gives the utility of the state from each player’s viewpoint. (In two-player, zero-sum games, the two-element vector can be reduced to a single value because the values are always opposite.) The simplest way to implement this is to have the Utilityfunction return a vector of utilities.

Now we have to consider nonterminal states. Consider the node marked Xin the game tree shown in [Figure 5.4](#index_split_012.html#filepos682106). In that state, player *C* chooses what to do. The two choices lead to terminal states with utility vectors (*v[A]* = 1, *v*[*B*] = 2, *v*[*C*] = 6) and (*v*[*A*] = 4, *v*[*B*] = 2,*v*[*C*] = 3).Since 6 is bigger than 3, *C* should choose the first move. This means that if state *X* is reached, subsequent play will lead to a terminal state with utilities (*v*[A] = 1, *v*[*B*] = 2, *v*[*C*] = 6).Hence, the backed-up value of *X* is this vector. The backed-up value of a node *n* is always the utility vector of the successor state with the highest value for the player choosing at *n*. Anyone who plays multiplayer games, such as Diplomacy, quickly becomes aware that much more alliance is going on than in two-player games. Multiplayer games usually involve **alliances**, whether formal or informal, among the players. Alliances are made and broken as the game proceeds. How are we to understand such behavior? Are alliances a natural consequence of optimal strategies for each player in a multiplayer game? It turns out that they can be. For example, suppose *A* and *B* are in weak positions and *C* is in a stronger position. Then it is often optimal for both *A* and *B* to attack *C* rather than each other, lest *C* destroy each of them individually. In this way, collaboration emerges from purely selfish behavior. Of course, as soon as *C* weakens under the joint onslaught, the alliance loses its value, and either *A* or *B* could violate the agreement. In some cases, explicit alliances merely make concrete what would have happened anyway. In other cases, a social stigma attaches to breaking an alliance, so players must balance the immediate advantage of breaking an alliance against the long-term disadvantage of being perceived as untrustworthy. See [Section 17.5](#index_split_015.html#filepos2641741) for more on these complications.

* * *

ALLIANCE

* * *

> ![image](images/00109.jpg)

> **Figure 5.3** An algorithm for calculating minimax decisions. It returns the action corresponding to the best possible move, that is, the move that leads to the outcome with the best utility, under the assumption that the opponent plays to minimize utility. The functions MAX\-VALUE and MIN\-VALUEGO through the whole game tree, all the way to the leaves, to determine the backed-up value of a state. The notation argmax[*a* ∈ *S*] *f*(*a*)computes the element *a* of set *S* that has the maximum value of *f*(*a*).

> ![image](images/00110.jpg)

> **Figure 5.4** The first three plies of a game tree with three players (*A*, *B*, *C*). Each node is labeled with values from the viewpoint of each player. The best move is marked at the root.

If the game is not zero-sum, then collaboration can also occur with just two players. Suppose, for example, that there is a terminal state with utilities 〈*v*[A] = 1000, *v*[B] = 1000〉 and that 1000 is the highest possible utility for each player. Then the optimal strategy is for both players to do everything possible to reach this state—that is, the players will automatically cooperate to achieve a mutually desirable goal.

### 5.3 ALPHA–BETA PRUNING

The problem with minimax search is that the number of game states it has to examine is exponential in the depth of the tree. Unfortunately, we can’t eliminate the exponent, but it turns out we can effectively cut it in half. The trick is that it is possible to compute the correct minimax decision without looking at every node in the game tree. That is, we can borrow the idea of **pruning** from [Chapter 3](#index_split_000.html#filepos301685) to eliminate large parts of the tree from consideration. The particular technique we examine is called **alpha-beta pruning.** When applied to a standard minimax tree, it returns the same move as minimax would, but prunes away branches that cannot possibly influence the final decision.

* * *

ALPHA–BETA PRUNING

* * *

Consider again the two-ply game tree from [Figure 5.2](#index_split_012.html#filepos671688). Let’s go through the calculation of the optimal decision once more, this time paying careful attention to what we know at each point in the process. The steps are explained in [Figure 5.5](#index_split_012.html#filepos685927). The outcome is that we can identify the minimax decision without ever evaluating two of the leaf nodes.

Another way to look at this is as a simplification of the formula for MINIMAX. Let the two unevaluated successors of node *C* in [Figure 5.5](#index_split_012.html#filepos685927) have values *x* and *y*. Then the value of the root node is given by

> ![image](images/00111.jpg)

In other words, the value of the root and hence the minimax decision are *independent* of the values of the pruned leaves *x* and *y*.

Alpha–beta pruning can be applied to trees of any depth, and it is often possible to prune entire subtrees rather than just leaves. The general principle is this: consider a node *n* somewhere in the tree (see [Figure 5.6](#index_split_012.html#filepos688331)), such that Player has a choice of moving to that node. If Player has a better choice meither at the parent node of nor at any choice point further up, then *n will never be reached in actual play.* So once we have found out enough about *n* (by examining some of its descendants) to reach this conclusion, we can prune it.

> ![image](images/00112.jpg)

> **Figure 5.5** Stages in the calculation of the optimal decision for the game tree in [Figure 5.2](#index_split_012.html#filepos671688). At each point, we show the range of possible values for each node. (a) The first leaf below *B* has the value 3. Hence, *B*, which is a MIN node, has a value of *at most* 3. (b) The second leaf below *B* has a value of 12; MIN would avoid this move, so the value of *B* is still at most 3. (c) The third leaf below *B* has a value of 8; we have seen all *B*’s successor states, so the value of *B* is exactly 3. Now, we can infer that the value of the root is *at least*3, because MAX has a choice worth 3 at the root. (d) The first leaf below *C* has the value 2. Hence, *C*, which is a MIN node, has a value of *at most* 2. But we know that *B* is worth 3, so MAX would never choose *C*. Therefore, there is no point in looking at the other successor states of *C*. This is an example of alpha-beta pruning. (e) The first leaf below *d* has the value 14, so *d* is worth *at most* 14. This is still higher than MAX’s best alternative (i.e., 3), so we need to keep exploring *D*’s successor states. Notice also that we now have bounds on all of the successors of the root, so the root’s value is also at most 14. (f) The second successor of *d* is worth 5, so again we need to keep exploring. The third successor is worth 2, so now *d* is worth exactly 2. MAX’s decision at the rootis to move to *B*, giving a value of 3.

![hand](images/00006.jpg)

Remember that minimax search is depth-first, so at any one time we just have to consider the nodes along a single path in the tree. Alpha-beta pruning gets its name from the following two parameters that describe bounds on the backed-up values that appear anywhere along the path:

> ![image](images/00113.jpg)

> **[Figure 5.6](#index_split_012.html#filepos688331)** The general case for alpha-beta pruning. If *m* is better than *n* for Player, we will never get to *n* in play.

> ![image](images/00114.jpg)

Alpha-beta search updates the values of α and β as it goes along and prunes the remaining branches at a node (i.e., terminates the recursive call) as soon as the value of the current node is known to be worse than the current α or β value for MAX or MIN, respectively. The complete algorithm is given in [Figure 5.7](#index_split_012.html#filepos691149). We encourage you to trace its behavior when applied to the tree in [Figure 5.5](#index_split_012.html#filepos685927).

#### **5.3.1 Move ordering**

The effectiveness of alpha-beta pruning is highly dependent on the order in which the states are examined. For example, in [Figure 5.5](#index_split_012.html#filepos685927)(e) and (*f*), we could not prune any successors of *D* at all because the worst successors (from the point of view of MIN)were generated first. If the third successor of *D* had been generated first, we would have been able to prune the other two. This suggests that it might be worthwhile to try to examine first the successors that are likely to be best.

If this can be done,[²](#index_split_015.html#filepos5578183) then it turns out that alpha-beta needs to examine only *O*(*b*^(*m*/2)) nodes to pick the best move, instead of *O*(*b*^(*m*)) for minimax. This means that the effective branching factor becomes ![equ](images/00115.jpg)instead of *b*—for chess, about 6instead of 35. Put another way, alpha-beta can solve a tree roughly twice as deep as minimax in the same amount of time. If successors are examined in random order rather than best-first, the total number of nodes examined will be roughly *O*(*b*^(3*m*/4))for moderate *b*. For chess, a fairly simple ordering function (such as trying captures first, then threats, then forward moves, and then backward moves) gets you to within about a factor of 2 of the best-case *O*(*b*^(*m*/2)) result.

> ![image](images/00116.jpg)

> **Figure 5.7** The alpha-beta search algorithm. Notice that these routines are the same as the MINIMAX functions in [Figure 5.3](#index_split_012.html#filepos681233), except for the two lines in each of MIN\-VALUE and MAX\-VALUE that maintain α and β (and the bookkeeping to pass these parameters along).

Adding dynamic move-ordering schemes, such as trying first the moves that were found to be best in the past, brings us quite close to the theoretical limit. The past could be the previous move—often the same threats remain—or it could come from previous exploration of the current move. One way to gain information from the current move is with iterative deepening search. First, search 1 ply deep and record the best path of moves. Then search 1 ply deeper, but use the recorded path to inform move ordering. As we saw in [Chapter 3](#index_split_000.html#filepos301685), iterative deepening on an exponential game tree adds only a constant fraction to the total search time, which can be more than made up from better move ordering. The best moves are often called **killer moves** and to try them first is called the killer move heuristic.

* * *

KILLER MOVES

* * *

In [Chapter 3](#index_split_000.html#filepos301685), we noted that repeated states in the search tree can cause an exponential increase in search cost. In many games, repeated states occur frequently because of **transpositions**—different permutations of the move sequence that end up in the same position. For example, if White has one move, *a*[1], that can be answered by Black with *b*[1] and an unrelated move *a*[2] on the other side of the board that can be answered by *b*[2], then the sequences \[*a*[1], *b*[1], *a*[2], *b*[2]\] and \[*a*[2], *b*[2], *a*[1], *b*[1]\] both end up in the same position. It is worthwhile to store the evaluation of the resulting position in a hash table the first time it is encountered so that we don’t have to recompute it on subsequent occurrences. The hash table of previously seen positions is traditionally called a **transposition table**; it is essentially identical to the *explored* list in GRAPH\-SEARCH (Section 3.3). Using a transposition table can have a dramatic effect, sometimes as much as doubling the reachable search depth in chess. On the other hand, if we are evaluating a million nodes per second, at some point it is not practical to keep *all* of them in the transposition table. Various strategies have been used to choose which nodes to keep and which to discard.

* * *

TRANSPOSITION

* * *

* * *

TRANSPOSITION TABLE

* * *

### 5.4 IMPERFECT REAL\-TIME DECISIONS

The minimax algorithm generates the entire game search space, whereas the alpha–beta algorithm allows us to prune large parts of it. However, alpha–beta still has to search all the way to terminal states for at least a portion of the search space. This depth is usually not practical, because moves must be made in a reasonable amount of time—typically a few minutes at most. Claude Shannon’s paper *Programming a Computer for Playing Chess* (1950) proposed instead that programs should cut off the search earlier and apply a heuristic **evaluation function** to states in the search, effectively turning nonterminal nodes into terminal leaves. In other words, the suggestion is to alter minimax or alpha–beta in two ways: replace the utility function by a heuristic evaluation function EVAL, which estimates the position’s utility, and replace the terminal test by a **cutoff test** that decides when to apply EVAL. That gives us the following for heuristic minimax for state s and maximum depth *d*:

> ![equ](images/00117.jpg)

* * *

EVALUATION FUNCTION

* * *

* * *

CUTOFF TEST

* * *

#### **5.4.1 Evaluation functions**

An evaluation function returns an *estimate* of the expected utility of the game from a given position, just as the heuristic functions of [Chapter 3](#index_split_000.html#filepos301685) return an estimate of the distance to the goal. The idea of an estimator was not new when Shannon proposed it. For centuries, chess players (and aficionados of other games) have developed ways of judging the value of a position because humans are even more limited in the amount of search they can do than are computer programs. It should be clear that the performance of a gameplaying program depends strongly on the quality of its evaluation function. An inaccurate evaluation function will guide an agent toward positions that turn out to be lost. How exactly do we design good evaluation functions?

First, the evaluation function should order the *terminal* states in the same way as the true utility function: states that are wins must evaluate better than draws, which in turn must be better than losses. Otherwise, an agent using the evaluation function might err even if it can see ahead all the way to the end of the game. Second, the computation must not take too long! (The whole point is to search faster.) Third, for nonterminal states, the evaluation function should be strongly correlated with the actual chances of winning.

One might well wonder about the phrase “chances of winning.” After all, chess is not a game of chance: we know the current state with certainty, and no dice are involved. But if the search must be cut off at nonterminal states, then the algorithm will necessarily be *uncertain* about the final outcomes of those states. This type of uncertainty is induced by computational, rather than informational, limitations. Given the limited amount of computation that the evaluation function is allowed to do for a given state, the best it can do is make a guess about the final outcome.

Let us make this idea more concrete. Most evaluation functions work by calculating various **features** of the state—for example, in chess, we would have features for the number of white pawns, black pawns, white queens, black queens, and so on. The features, taken together, define various *categories* or *equivalence classes* of states: the states in each category have the same values for all the features. For example, one category contains all two-pawn vs. one-pawn endgames. Any given category, generally speaking, will contain some states that lead to wins, some that lead to draws, and some that lead to losses. The evaluation function cannot know which states are which, but it can return a single value that reflects the *proportion* of states with each outcome. For example, suppose our experience suggests that 72% of the states encountered in the two-pawns vs. one-pawn category lead to a win (utility +1); 20% to a loss (0), and 8% to a draw (1/2). Then a reasonable evaluation for states in the category is the **expected value**: (0.72 × +1) + (0.20 × 0) + (0.08 × 1/2) = 0.76. In principle, the expected value can be determined for each category, resulting in an evaluation function that works for any state. As with terminal states, the evaluation function need not return actual expected values as long as the *ordering* of the states is the same.

* * *

EXPECTED VALUE

* * *

In practice, this kind of analysis requires too many categories and hence too much experience to estimate all the probabilities of winning. Instead, most evaluation functions compute separate numerical contributions from each feature and then *combine* them to find the total value. For example, introductory chess books give an approximate **material value** for each piece: each pawn is worth 1, a knight or bishop is worth 3, a rook 5, and the queen 9. Other features such as “good pawn structure” and “king safety” might be worth half a pawn, say. These feature values are then simply added up to obtain the evaluation of the position.

* * *

MATERIAL VALUE

* * *

A secure advantage equivalent to a pawn gives a substantial likelihood of winning, and a secure advantage equivalent to three pawns should give almost certain victory, as illustrated in [Figure 5.8](#index_split_012.html#filepos685927)(a). Mathematically, this kind of evaluation function is called a **weighted linear function** because it can be expressed as

> ![equ](images/00118.jpg)

* * *

WEIGHTED LINEAR FUNCTION

* * *

where each *w*[*i*] is a weight and each *f*[*i*] is a feature of the position. For chess, the *f*[*i*] could be the numbers of each kind of piece on the board, and the *w*[*i*] could be the values of the pieces (1 for pawn, 3 for bishop, etc.).

Adding up the values of features seems like a reasonable thing to do, but in fact it involves a strong assumption: that the contribution of each feature is *independent* of the values of the other features. For example, assigning the value 3 to a bishop ignores the fact that bishops are more powerful in the endgame, when they have a lot of space to maneuver. For this reason, current programs for chess and other games also use *nonlinear* combinations of features. For example, a pair of bishops might be worth slightly more than twice the value of a single bishop, and a bishop is worth more in the endgame (that is, when the *move number* feature is high or the *number of remaining pieces* feature is low).

> ![image](images/00119.jpg)

> **Figure 5.8** Two chess positions that differ only in the position of the rook at lower right. In (a), Black has an advantage of a knight and two pawns, which should be enough to win the game. In (b), White will capture the queen, giving it an advantage that should be strong enough to win.

The astute reader will have noticed that the features and weights are *not* part of the rules of chess! They come from centuries of human chess-playing experience. In games where this kind of experience is not available, the weights of the evaluation function can be estimated by the machine learning techniques of [Chapter 18](#index_split_015.html#filepos2753020). Reassuringly, applying these techniques to chess has confirmed that a bishop is indeed worth about three pawns.

#### **5.4.2 Cutting off search**

The next step is to modify ALPHA\-BETA\-SEARCH so that it will call the heuristic EVAL function when it is appropriate to cut off the search. We replace the two lines in [Figure 5.7](#index_split_012.html#filepos691149) that mention TERMINAL\-TEST with the following line:

> **if** CUTOFF\-TEST (*state*, *depth*) **then return** EVAL(*state*)

We also must arrange for some bookkeeping so that the current *depth* is incremented on each recursive call. The most straightforward approach to controlling the amount of search is to set a fixed depth limit so that CUTOFF\-TEST(*state*, *depth*) returns *true* for all *depth* greater than some fixed depth *d*. (It must also return true for all terminal states, just as TERMINAL\-TEST did.) The depth *d* is chosen so that a move is selected within the allocated time. A more robust approach is to apply iterative deepening. (See [Chapter 3](#index_split_000.html#filepos301685).) When time runs out, the program returns the move selected by the deepest completed search. As a bonus, iterative deepening also helps with move ordering.

These simple approaches can lead to errors due to the approximate nature of the evaluation function. Consider again the simple evaluation function for chess based on material advantage. Suppose the program searches to the depth limit, reaching the position in [Figure 5.8](#index_split_012.html#filepos702741)(b), where Black is ahead by a knight and two pawns. It would report this as the heuristic value of the state, thereby declaring that the state is a probable win by Black. But White’s next move captures Black’s queen with no compensation. Hence, the position is really won for White, but this can be seen only by looking ahead one more ply.

Obviously, a more sophisticated cutoff test is needed. The evaluation function should be applied only to positions that are **quiescent**—that is, unlikely to exhibit wild swings in value in the near future. In chess, for example, positions in which favorable captures can be made are not quiescent for an evaluation function that just counts material. Nonquiescent positions can be expanded further until quiescent positions are reached. This extra search is called a **quiescence search**; sometimes it is restricted to consider only certain types of moves, such as capture moves, that will quickly resolve the uncertainties in the position.

* * *

QUIESCENCE

* * *

* * *

QUIESCENCE SEARCH

* * *

The **horizon effect** is more difficult to eliminate. It arises when the program is facing an opponent’s move that causes serious damage and is ultimately unavoidable, but can be temporarily avoided by delaying tactics. Consider the chess game in Figure 5.9. It is clear that there is no way for the black bishop to escape. For example, the white rook can capture it by moving to h1, then a1, then a2; a capture at depth 6 ply. But Black does have a sequence of moves that pushes the capture of the bishop “over the horizon.” Suppose Black searches to depth 8 ply. Most moves by Black will lead to the eventual capture of the bishop, and thus will be marked as “bad” moves. But Black will consider checking the white king with the pawn at e4. This will lead to the king capturing the pawn. Now Black will consider checking again, with the pawn at f5, leading to another pawn capture. That takes up 4 ply, and from there the remaining 4 ply is not enough to capture the bishop. Black thinks that the line of play has saved the bishop at the price of two pawns, when actually all it has done is push the inevitable capture of the bishop beyond the horizon that Black can see.

* * *

HORIZON EFFECT

* * *

One strategy to mitigate the horizon effect is the **singular extension**, a move that is “clearly better” than all other moves in a given position. Once discovered anywhere in the tree in the course of a search, this singular move is remembered. When the search reaches the normal depth limit, the algorithm checks to see if the singular extension is a legal move; if it is, the algorithm allows the move to be considered. This makes the tree deeper, but because there will be few singular extensions, it does not add many total nodes to the tree.

* * *

SINGULAR

* * *

* * *

EXTENSION

* * *

#### **5.4.3 Forward pruning**

So far, we have talked about cutting off search at a certain level and about doing alpha–beta pruning that provably has no effect on the result (at least with respect to the heuristic evaluation values). It is also possible to do **forward pruning**, meaning that some moves at a given node are pruned immediately without further consideration. Clearly, most humans playing chess consider only a few moves from each position (at least consciously). One approach to forward pruning is **beam search**: on each ply, consider only a “beam” of the *n* best moves (according to the evaluation function) rather than considering all possible moves. Unfortunately, this approach is rather dangerous because there is no guarantee that the best move will not be pruned away.

* * *

FORWARD PRUNING

* * *

* * *

BEAM SEARCH

* * *

> ![image](images/00120.jpg)

> **Figure 5.9** The horizon effect. With Black to move, the black bishop is surely doomed. But Black can forestall that event by checking the white king with its pawns, forcing the king to capture the pawns. This pushes the inevitable loss of the bishop over the horizon, and thus the pawn sacrifices are seen by the search algorithm as good moves rather than bad ones.

The PROBCUT, or probabilistic cut, algorithm (Buro, 1995) is a forward-pruning version of alpha–beta search that uses statistics gained from prior experience to lessen the chance that the best move will be pruned. Alpha–beta search prunes any node that is *provably* outside the current (α, β) window. PROBCUT also prunes nodes that are *probably* outside the window. It computes this probability by doing a shallow search to compute the backed-up value *v* of a node and then using past experience to estimate how likely it is that a score of *v* at depth d in the tree would be outside (α, β). Buro applied this technique to his Othello program, LOGISTELLO, and found that a version of his program with PROBCUT beat the regular version 64% of the time, even when the regular version was given twice as much time.

Combining all the techniques described here results in a program that can play creditable chess (or other games). Let us assume we have implemented an evaluation function for chess, a reasonable cutoff test with a quiescence search, and a large transposition table. Let us also assume that, after months of tedious bit-bashing, we can generate and evaluate around a million nodes per second on the latest PC, allowing us to search roughly 200 million nodes per move under standard time controls (three minutes per move). The branching factor for chess is about 35, on average, and 35⁵ is about 50 million, so if we used minimax search, we could look ahead only about five plies. Though not incompetent, such a program can be fooled easily by an average human chess player, who can occasionally plan six or eight plies ahead. With alpha–beta search we get to about 10 plies, which results in an expert level of play. [Section 5.8](#index_split_000.html#filepos757873) describes additional pruning techniques that can extend the effective search depth to roughly 14 plies. To reach grandmaster status we would need an extensively tuned evaluation function and a large database of optimal opening and endgame moves.

#### **5.4.4 Search versus lookup**

Somehow it seems like overkill for a chess program to start a game by considering a tree of a billion game states, only to conclude that it will move its pawn to e4. Books describing good play in the opening and endgame in chess have been available for about a century (Tattersall, 1911). It is not surprising, therefore, that many gameplaying programs use *table lookup* rather than search for the opening and ending of games.

For the openings, the computer is mostly relying on the expertise of humans. The best advice of human experts on how to play each opening is copied from books and entered into tables for the computer’s use. However, computers can also gather statistics from a database of previously played games to see which opening sequences most often lead to a win. In the early moves there are few choices, and thus much expert commentary and past games on which to draw. Usually after ten moves we end up in a rarely seen position, and the program must switch from table lookup to search.

Near the end of the game there are again fewer possible positions, and thus more chance to do lookup. But here it is the computer that has the expertise: computer analysis of endgames goes far beyond anything achieved by humans. A human can tell you the general strategy for playing a king-and-rook-versus-king (KRK) endgame: reduce the opposing king’s mobility by squeezing it toward one edge of the board, using your king to prevent the opponent from escaping the squeeze. Other endings, such as king, bishop, and knight versus king (KBNK), are difficult to master and have no succinct strategy description. A computer, on the other hand, can completely *solve* the endgame by producing a **policy**, which is a mapping from every possible state to the best move in that state. Then we can just look up the best move rather than recompute it anew. How big will the KBNK lookup table be? It turns out there are 462 ways that two kings can be placed on the board without being adjacent. After the kings are placed, there are 62 empty squares for the bishop, 61 for the knight, and two possible players to move next, so there are just 462 × 62 × 61 × 2 = 3, 494, 568 possible positions. Some of these are checkmates; mark them as such in a table. Then do a **retrograde** minimax search: reverse the rules of chess to do unmoves rather than moves. Any move by White that, no matter what move Black responds with, ends up in a position marked as a win, must also be a win. Continue this search until all 3,494,568 positions are resolved as win, loss, or draw, and you have an infallible lookup table for all KBNK endgames.

* * *

POLICY

* * *

* * *

RETROGRADE

* * *

Using this technique and a *tour de force* of optimization tricks, Ken Thompson (1986, 1996) and Lewis Stiller (1992, 1996) solved all chess endgames with up to five pieces and some with six pieces, making them available on the Internet. Stiller discovered one case where a forced mate existed but required 262 moves; this caused some consternation because the rules of chess require a capture or pawn move to occur within 50 moves. Later work by Marc Bourzutschky and Yakov Konoval (Bourzutschky, 2006) solved all pawnless six-piece and some seven-piece endgames; there is a KQNKRBN endgame that with best play requires 517 moves until a capture, which then leads to a mate.

If we could extend the chess endgame tables from 6 pieces to 32, then White would know on the opening move whether it would be a win, loss, or draw. This has not happened so far for chess, but it has happened for checkers, as explained in the historical notes section.

### 5.5 STOCHASTIC GAMES

In real life, many unpredictable external events can put us into unforeseen situations. Many games mirror this unpredictability by including a random element, such as the throwing of dice. We call these **stochastic games**. Backgammon is a typical game that combines luck and skill. Dice are rolled at the beginning of a player’s turn to determine the legal moves. In the backgammon position of [Figure 5.10](#index_split_012.html#filepos718279), for example, White has rolled a 6–5 and has four possible moves.

* * *

STOCHASTIC GAMES

* * *

> ![image](images/00121.jpg)

> **Figure 5.10** A typical backgammon position. The goal of the game is to move all one’s pieces off the board. White moves clockwise toward 25, and Black moves counterclockwise toward 0. A piece can move to any position unless multiple opponent pieces are there; if there is one opponent, it is captured and must start over. In the position shown, White has rolled 6–5 and must choose among four legal moves: (5–10,5–11), (5–11,19–24), (5–10,10–16), and (5–11,11–16), where the notation (5–11,11–16) means move one piece from position 5 to 11, and then move a piece from 11 to 16.

Although White knows what his or her own legal moves are, White does not know what Black is going to roll and thus does not know what Black’s legal moves will be. That means White cannot construct a standard game tree of the sort we saw in chess and tic-tac-toe. A game tree in backgammon must include **chance nodes** in addition to MAX and MIN nodes. Chance nodes are shown as circles in [Figure 5.11](#index_split_012.html#filepos720240). The branches leading from each chance node denote the possible dice rolls; each branch is labeled with the roll and its probability. There are 36 ways to roll two dice, each equally likely; but because a 6–5 is the same as a 5–6, there are only 21 distinct rolls. The six doubles (1–1 through 6–6) each have a probability of 1/36, so we say P (1–1) = 1/36. The other 15 distinct rolls each have a 1/18 probability.

* * *

CHANCE NODES

* * *

> ![image](images/00122.jpg)

> **Figure 5.11** Schematic game tree for a backgammon position.

The next step is to understand how to make correct decisions. Obviously, we still want to pick the move that leads to the best position. However, positions do not have definite minimax values. Instead, we can only calculate the **expected value** of a position: the average over all possible outcomes of the chance nodes.

* * *

EXPECTED VALUE

* * *

This leads us to generalize the **minimax value** for deterministic games to an **expectiminimax value** for games with chance nodes. Terminal nodes and MAX and MIN nodes (for which the dice roll is known) work exactly the same way as before. For chance nodes we compute the expected value, which is the sum of the value over all outcomes, weighted by the probability of each chance action:

> ![equ](images/00123.jpg)

* * *

EXPECTIMINIMAX VALUE

* * *

where *r* represents a possible dice roll (or other chance event) and RESULT(*s*, *r*) is the same state as *s*, with the additional fact that the result of the dice roll is *r*.

#### **5.5.1 Evaluation functions for games of chance**

As with minimax, the obvious approximation to make with expectiminimax is to cut the search off at some point and apply an evaluation function to each leaf. One might think that evaluation functions for games such as backgammon should be just like evaluation functions for chess—they just need to give higher scores to better positions. But in fact, the presence of chance nodes means that one has to be more careful about what the evaluation values mean. [Figure 5.12](#index_split_012.html#filepos723414) shows what happens: with an evaluation function that assigns the values \[1, 2, 3, 4\] to the leaves, move *a*[1] is best; with values \[1, 20, 30, 400\], move *a*[2] is best. Hence, the program behaves totally differently if we make a change in the scale of some evaluation values! It turns out that to avoid this sensitivity, the evaluation function must be a positive linear transformation of the probability of winning from a position (or, more generally, of the expected utility of the position). This is an important and general property of situations in which uncertainty is involved, and we discuss it further in [Chapter 16](#index_split_015.html#filepos2423989).

> ![image](images/00124.jpg)

> **Figure 5.12** An order-preserving transformation on leaf values changes the best move.

If the program knew in advance all the dice rolls that would occur for the rest of the game, solving a game with dice would be just like solving a game without dice, which minimax does in *O*(*b*^(*m*)) time, where *b* is the branching factor and *m* is the maximum depth of the game tree. Because expectiminimax is also considering all the possible dice-roll sequences, it will take *O*(*b*^(*m*)*n*^(*m*)), where *n* is the number of distinct rolls.

Even if the search depth is limited to some small depth *d*, the extra cost compared with that of minimax makes it unrealistic to consider looking ahead very far in most games of chance. In backgammon *n* is 21 and *b* is usually around 20, but in some situations can be as high as 4000 for dice rolls that are doubles. Three plies is probably all we could manage.

Another way to think about the problem is this: the advantage of alpha–beta is that it ignores future developments that just are not going to happen, given best play. Thus, it concentrates on likely occurrences. In games with dice, there are *no* likely sequences of moves, because for those moves to take place, the dice would first have to come out the right way to make them legal. This is a general problem whenever uncertainty enters the picture: the possibilities are multiplied enormously, and forming detailed plans of action becomes pointless because the world probably will not play along.

It may have occurred to you that something like alpha–beta pruning could be applied to game trees with chance nodes. It turns out that it can. The analysis for MIN and MAX nodes is unchanged, but we can also prune chance nodes, using a bit of ingenuity. Consider the chance node *C* in [Figure 5.11](#index_split_012.html#filepos720240) and what happens to its value as we examine and evaluate its children. Is it possible to find an upper bound on the value of *C* before we have looked at all its children? (Recall that this is what alpha–beta needs in order to prune a node and its subtree.) At first sight, it might seem impossible because the value of *C* is the *average* of its children’s values, and in order to compute the average of a set of numbers, we must look at all the numbers. But if we put bounds on the possible values of the utility function, then we can arrive at bounds for the average without looking at every number. For example, say that all utility values are between −2 and +2; then the value of leaf nodes is bounded, and in turn we *can* place an upper bound on the value of a chance node without looking at all its children.

An alternative is to do **Monte Carlo simulation** to evaluate a position. Start with an alpha–beta (or other) search algorithm. From a start position, have the algorithm play thousands of games against itself, using random dice rolls. In the case of backgammon, the resulting win percentage has been shown to be a good approximation of the value of the position, even if the algorithm has an imperfect heuristic and is searching only a few plies (Tesauro, 1995). For games with dice, this type of simulation is called a **rollout**.

* * *

MONTE CARLO SIMULATION

* * *

* * *

ROLLOUT

* * *

### 5.6 PARTIALLY OBSERVABLE GAMES

Chess has often been described as war in miniature, but it lacks at least one major characteristic of real wars, namely, **partial observability**. In the “fog of war,” the existence and disposition of enemy units is often unknown until revealed by direct contact. As a result, warfare includes the use of scouts and spies to gather information and the use of concealment and bluff to confuse the enemy. Partially observable games share these characteristics and are thus qualitatively different from the games described in the preceding sections.

#### **5.6.1 Kriegspiel: Partially observable chess**

In *deterministic* partially observable games, uncertainty about the state of the board arises entirely from lack of access to the choices made by the opponent. This class includes children’s games such as Battleships (where each player’s ships are placed in locations hidden from the opponent but do not move) and Stratego (where piece locations are known but piece types are hidden). We will examine the game of **Kriegspiel**, a partially observable variant of chess in which pieces can move but are completely invisible to the opponent.

* * *

KRIEGSPIEL

* * *

The rules of Kriegspiel are as follows: White and Black each see a board containing only their own pieces. A referee, who can see all the pieces, adjudicates the game and periodically makes announcements that are heard by both players. On his turn, White proposes to the referee any move that would be legal if there were no black pieces. If the move is in fact not legal (because of the black pieces), the referee announces “illegal.” In this case, White may keep proposing moves until a legal one is found—and learns more about the location of Black’s pieces in the process. Once a legal move is proposed, the referee announces one or more of the following: “Capture on square *X*” if there is a capture, and “Check by *D*” if the black king is in check, where *D* is the direction of the check, and can be one of “Knight,” “Rank,” “File,” “Long diagonal,” or “Short diagonal.” (In case of discovered check, the referee may make two “Check” announcements.) If Black is checkmated or stalemated, the referee says so; otherwise, it is Black’s turn to move.

Kriegspiel may seem terrifyingly impossible, but humans manage it quite well and computer programs are beginning to catch up. It helps to recall the notion of a **belief state** as defined in [Section 4.4](#index_split_000.html#filepos575701) and illustrated in Figure 4.14—the set of all *logically possible* board states given the complete history of percepts to date. Initially, White’s belief state is a singleton because Black’s pieces haven’t moved yet. After White makes a move and Black responds, White’s belief state contains 20 positions because Black has 20 replies to any White move. Keeping track of the belief state as the game progresses is exactly the problem of **state estimation**, for which the update step is given in Equation (4.6). We can map Kriegspiel state estimation directly onto the partially observable, nondeterministic framework of [Section 4.4](#index_split_000.html#filepos575701) if we consider the opponent as the source of nondeterminism; that is, the RESULTS of White’s move are composed from the (predictable) outcome of White’s own move and the unpredictable outcome given by Black’s reply.[³](#index_split_015.html#filepos5578402)

Given a current belief state, White may ask, “Can I win the game?” For a partially observable game, the notion of a **strategy** is altered; instead of specifying a move to make for each possible *move* the opponent might make, we need a move for every possible *percept sequence* that might be received. For Kriegspiel, a winning strategy, or **guaranteed checkmate**, is one that, for each possible percept sequence, leads to an actual checkmate for every possible board state in the current belief state, regardless of how the opponent moves. With this definition, the opponent’s belief state is irrelevant—the strategy has to work even if the opponent can see all the pieces. This greatly simplifies the computation. Figure 5.13 shows part of a guaranteed checkmate for the KRK (king and rook against king) endgame. In this case, Black has just one piece (the king), so a belief state for White can be shown in a single board by marking each possible position of the Black king.

* * *

GUARANTEED CHECKMATE

* * *

The general AND-OR search algorithm can be applied to the belief-state space to find guaranteed checkmates, just as in [Section 4.4](#index_split_000.html#filepos575701). The incremental belief-state algorithm mentioned in that section often finds midgame checkmates up to depth 9—probably well beyond the abilities of human players.

In addition to guaranteed checkmates, Kriegspiel admits an entirely new concept that makes no sense in fully observable games: **probabilistic checkmate**. Such checkmates are still required to work in every board state in the belief state; they are probabilistic with respect to randomization of the winning player’s moves. To get the basic idea, consider the problem of finding a lone black king using just the white king. Simply by moving randomly, the white king will *eventually* bump into the black king even if the latter tries to avoid this fate, since Black cannot keep guessing the right evasive moves indefinitely. In the terminology of probability theory, detection occurs *with probability* 1. The KBNK endgame—king, bishop and knight against king—is won in this sense; White presents Black with an infinite random sequence of choices, for one of which Black will guess incorrectly and reveal his position, leading to checkmate. The KBBK endgame, on the other hand, is won with probability 1 − ε. White can force a win only by leaving one of his bishops unprotected for one move. If Black happens to be in the right place and captures the bishop (a move that would lose if the bishops are protected), the game is drawn. White can choose to make the risky move at some randomly chosen point in the middle of a very long sequence, thus reducing ε to an arbitrarily small constant, but cannot reduce ε to zero.

* * *

PROBABILISTIC CHECKMATE

* * *

> ![image](images/00125.jpg)

> **Figure 5.13** Part of a guaranteed checkmate in the KRK endgame, shown on a reduced board. In the initial belief state, Black’s king is in one of three possible locations. By a combination of probing moves, the strategy narrows this down to one. Completion of the checkmate is left as an exercise.

It is quite rare that a guaranteed or probabilistic checkmate can be found within any reasonable depth, except in the endgame. Sometimes a checkmate strategy works for *some* of the board states in the current belief state but not others. Trying such a strategy may succeed, leading to an **accidental checkmate**—accidental in the sense that White could not *know* that it would be checkmate—if Black’s pieces happen to be in the right places. (Most checkmates in games between humans are of this accidental nature.) This idea leads naturally to the question of *how likely* it is that a given strategy will win, which leads in turn to the question of *how likely* it is that each board state in the current belief state is the true board state.

* * *

ACCIDENTAL CHECKMATE

* * *

One’s first inclination might be to propose that all board states in the current belief state are equally likely—but this can’t be right. Consider, for example, White’s belief state after Black’s first move of the game. By definition (assuming that Black plays optimally), Black must have played an optimal move, so all board states resulting from suboptimal moves ought to be assigned zero probability. This argument is not quite right either, because *each player’s goal is not just to move pieces to the right squares but also to minimize the information that the opponent has about their location.* Playing any *predictable* “optimal” strategy provides the opponent with information. Hence, optimal play in partially observable games requires a willingness to play somewhat *randomly*. (This is why restaurant hygiene inspectors do *random* inspection visits.) This means occasionally selecting moves that may seem “intrinsically” weak—but they gain strength from their very unpredictability, because the opponent is unlikely to have prepared any defense against them.

![hand](images/00006.jpg)

From these considerations, it seems that the probabilities associated with the board states in the current belief state can only be calculated given an optimal randomized strategy; in turn, computing that strategy seems to require knowing the probabilities of the various states the board might be in. This conundrum can be resolved by adopting the game-theoretic notion of an **equilibrium** solution, which we pursue further in [Chapter 17](#index_split_015.html#filepos2562268). An equilibrium specifies an optimal randomized strategy for each player. Computing equilibria is prohibitively expensive, however, even for small games, and is out of the question for Kriegspiel. At present, the design of effective algorithms for general Kriegspiel play is an open research topic. Most systems perform bounded-depth lookahead in their own belief-state space, ignoring the opponent’s belief state. Evaluation functions resemble those for the observable game but include a component for the size of the belief state—smaller is better!

#### **5.6.2 Card games**

Card games provide many examples of *stochastic* partial observability, where the missing information is generated randomly. For example, in many games, cards are dealt randomly at the beginning of the game, with each player receiving a hand that is not visible to the other players. Such games include bridge, whist, hearts, and some forms of poker.

At first sight, it might seem that these card games are just like dice games: the cards are dealt randomly and determine the moves available to each player, but all the “dice” are rolled at the beginning! Even though this analogy turns out to be incorrect, it suggests an effective algorithm: consider all possible deals of the invisible cards; solve each one as if it were a fully observable game; and then choose the move that has the best outcome averaged over all the deals. Suppose that each deal *s* occurs with probability *P*(*s*); then the move we want is

> ![equ](images/00126.jpg)

Here, we run exact MINIMAX if computationally feasible; otherwise, we run H-MINIMAX.

Now, in most card games, the number of possible deals is rather large. For example, in bridge play, each player sees just two of the four hands; there are two unseen hands of 13 cards each, so the number of deals is ![equ](images/00127.jpg). Solving even one deal is quite difficult, so solving ten million is out of the question. Instead, we resort to a Monte Carlo approximation: instead of adding up *all* the deals, we take a *random sample* of *N* deals, where the probability of deal s appearing in the sample is proportional to *P*(*s*):

> ![equ](images/00128.jpg)

(Notice that *P*(*s*) does not appear explicitly in the summation, because the samples are already drawn according to *P*(*s*).) As *N* grows large, the sum over the random sample tends to the exact value, but even for fairly small *N*—say, 100 to 1,000—the method gives a good approximation. It can also be applied to deterministic games such as Kriegspiel, given some reasonable estimate of *P*(*s*).

For games like whist and hearts, where there is no bidding or betting phase before play commences, each deal will be equally likely and so the values of *P*(*s*) are all equal. For bridge, play is preceded by a bidding phase in which each team indicates how many tricks it expects to win. Since players bid based on the cards they hold, the other players learn more about the probability of each deal. Taking this into account in deciding how to play the hand is tricky, for the reasons mentioned in our description of Kriegspiel: players may bid in such a way as to minimize the information conveyed to their opponents. Even so, the approach is quite effective for bridge, as we show in [Section 5.7](#index_split_000.html#filepos744950).

The strategy described in Equations 5.1 and 5.2 is sometimes called *averaging over clairvoyance* because it assumes that the game will become observable to both players immediately after the first move. Despite its intuitive appeal, the strategy can lead one astray. Consider the following story:

> Day 1: Road *A* leads to a heap of gold; Road *B* leads to a fork. Take the left fork and you’ll find a bigger heap of gold, but take the right fork and you’ll be run over by a bus. Day 2: Road *A* leads to a heap of gold; Road *B* leads to a fork. Take the right fork and you’ll find a bigger heap of gold, but take the left fork and you’ll be run over by a bus. Day 3: Road *A* leads to a heap of gold; Road *B* leads to a fork. One branch of the fork leads to a bigger heap of gold, but take the wrong fork and you’ll be hit by a bus. Unfortunately you don’t know which fork is which.

Averaging over clairvoyance leads to the following reasoning: on Day 1, *B* is the right choice; on Day 2, *B* is the right choice; on Day 3, the situation is the same as either Day 1 or Day 2, so *B* must still be the right choice.

Now we can see how averaging over clairvoyance fails: it does not consider the *belief state* that the agent will be in after acting. A belief state of total ignorance is not desirable, especially when one possibility is certain death. Because it assumes that every future state will automatically be one of perfect knowledge, the approach never selects actions that *gather information* (like the first move in [Figure 5.13](#index_split_012.html#filepos734987)); nor will it choose actions that hide information from the opponent or provide information to a partner because it assumes that they already know the information; and it will never **bluff** in poker,[⁴](#index_split_015.html#filepos5578729) because it assumes the opponent can see its cards. In [Chapter 17](#index_split_015.html#filepos2562268), we show how to construct algorithms that do all these things by virtue of solving the true partially observable decision problem.

* * *

BLUFF

* * *

### 5.7 STATE-OF-THE\-ART GAME PROGRAMS

In 1965, the Russian mathematician Alexander Kronrod called chess “the *Drosophila* of artificial intelligence.” John McCarthy disagrees: whereas geneticists use fruit flies to make discoveries that apply to biology more broadly, AI has used chess to do the equivalent of breeding very fast fruit flies. Perhaps a better analogy is that chess is to AI as Grand Prix motor racing is to the car industry: state-of-the-art game programs are blindingly fast, highly optimized machines that incorporate the latest engineering advances, but they aren’t much use for doing the shopping or driving off-road. Nonetheless, racing and gameplaying generate excitement and a steady stream of innovations that have been adopted by the wider community. In this section we look at what it takes to come out on top in various games.

**Chess**: IBM’s DEEP BLUE chess program, now retired, is well known for defeating world champion Garry Kasparov in a widely publicized exhibition match. Deep Blue ran on a parallel computer with 30 IBM RS/6000 processors doing alpha–beta search. The unique part was a configuration of 480 custom VLSI chess processors that performed move generation and move ordering for the last few levels of the tree, and evaluated the leaf nodes. Deep Blue searched up to 30 billion positions per move, reaching depth 14 routinely. The key to its success seems to have been its ability to generate singular extensions beyond the depth limit for sufficiently interesting lines of forcing/forced moves. In some cases the search reached a depth of 40 plies. The evaluation function had over 8000 features, many of them describing highly specific patterns of pieces. An “opening book” of about 4000 positions was used, as well as a database of 700,000 grandmaster games from which consensus recommendations could be extracted. The system also used a large endgame database of solved positions containing all positions with five pieces and many with six pieces. This database had the effect of substantially extending the effective search depth, allowing Deep Blue to play perfectly in some cases even when it was many moves away from checkmate.

* * *

CHESS

* * *

The success of DEEP BLUE reinforced the widely held belief that progress in computer gameplaying has come primarily from ever-more-powerful hardware—a view encouraged by IBM. But algorithmic improvements have allowed programs running on standard PCs to win World Computer Chess Championships. A variety of pruning heuristics are used to reduce the effective branching factor to less than 3 (compared with the actual branching factor of about 35). The most important of these is the **null move** heuristic, which generates a good lower bound on the value of a position, using a shallow search in which the opponent gets to move twice at the beginning. This lower bound often allows alpha–beta pruning without the expense of a full-depth search. Also important is **futility pruning**, which helps decide in advance which moves will cause a beta cutoff in the successor nodes.

* * *

NULL MOVE

* * *

* * *

FUTILITY PRUNING

* * *

HYDRA can be seen as the successor to DEEP BLUE. HYDRA runs on a 64-processor cluster with 1 gigabyte per processor and with custom hardware in the form of FPGA (Field Programmable Gate Array) chips. HYDRA reaches 200 million evaluations per second, about the same as Deep Blue, but HYDRA reaches 18 plies deep rather than just 14 because of aggressive use of the null move heuristic and forward pruning.

RYBKA, winner of the 2008 and 2009 World Computer Chess Championships, is considered the strongest current computer player. It uses an off-the-shelf 8-core 3.2 GHz Intel Xeon processor, but little is known about the design of the program. RYBKA’s main advantage appears to be its evaluation function, which has been tuned by its main developer, International Master Vasik Rajlich, and at least three other grandmasters.

The most recent matches suggest that the top computer chess programs have pulled ahead of all human contenders. (See the historical notes for details.)

**Checkers**: Jonathan Schaeffer and colleagues developed CHINOOK, which runs on regular PCs and uses alpha–beta search. Chinook defeated the long-running human champion in an abbreviated match in 1990, and since 2007 CHINOOK has been able to play perfectly by using alpha–beta search combined with a database of 39 trillion endgame positions.

* * *

CHECKERS

* * *

**Othello**, also called Reversi, is probably more popular as a computer game than as a board game. It has a smaller search space than chess, usually 5 to 15 legal moves, but evaluation expertise had to be developed from scratch. In 1997, the LOGISTELLO program (Buro, 2002) defeated the human world champion, Takeshi Murakami, by six games to none. It is generally acknowledged that humans are no match for computers at Othello.

* * *

OTHELLO

* * *

**Backgammon**: [Section 5.5](#index_split_000.html#filepos717429) explained why the inclusion of uncertainty from dice rolls makes deep search an expensive luxury. Most work on backgammon has gone into improving the evaluation function. Gerry Tesauro (1992) combined reinforcement learning with neural networks to develop a remarkably accurate evaluator that is used with a search to depth 2 or 3. After playing more than a million training games against itself, Tesauro’s program, TD-GAMMON, is competitive with top human players. The program’s opinions on the opening moves of the game have in some cases radically altered the received wisdom.

* * *

BACKGAMMON

* * *

**Go** is the most popular board game in Asia. Because the board is 19 × 19 and moves are allowed into (almost) every empty square, the branching factor starts at 361, which is too daunting for regular alpha–beta search methods. In addition, it is difficult to write an evaluation function because control of territory is often very unpredictable until the endgame. Therefore the top programs, such as MOGO, avoid alpha–beta search and instead use Monte Carlo rollouts. The trick is to decide what moves to make in the course of the rollout. There is no aggressive pruning; all moves are possible. The UCT (upper confidence bounds on trees) method works by making random moves in the first few iterations, and over time guiding the sampling process to prefer moves that have led to wins in previous samples. Some tricks are added, including *knowledge-based rules* that suggest particular moves whenever a given pattern is detected and *limited local search* to decide tactical questions. Some programs also include special techniques from **combinatorial game theory** to analyze endgames. These techniques decompose a position into sub-positions that can be analyzed separately and then combined (Berlekamp and Wolfe, 1994; Müller, 2003). The optimal solutions obtained in this way have surprised many professional Go players, who thought they had been playing optimally all along. Current Go programs play at the master level on a reduced 9 × 9 board, but are still at advanced amateur level on a full board.

* * *

GO

* * *

* * *

COMBINATORIAL GAME THEORY

* * *

**Bridge** is a card game of imperfect information: a player’s cards are hidden from the other players. Bridge is also a *multiplayer* game with four players instead of two, although the players are paired into two teams. As in [Section 5.6](#index_split_000.html#filepos727487), optimal play in partially observable games like bridge can include elements of information gathering, communication, and careful weighing of probabilities. Many of these techniques are used in the Bridge Baron program (Smith **et al.**, 1998), which won the 1997 computer bridge championship. While it does not play optimally, Bridge Baron is one of the few successful gameplaying systems to use complex, hierarchical plans (see [Chapter 11](#index_split_015.html#filepos1612250)) involving high-level ideas, such as **finessing** and **squeezing**, that are familiar to bridge players.

* * *

BRIDGE

* * *

The GIB program (Ginsberg, 1999) won the 2000 computer bridge championship quite decisively using the Monte Carlo method. Since then, other winning programs have followed GIB’s lead. GIB’s major innovation is using **explanation-based generalization** to compute and cache general rules for optimal play in various standard classes of situations rather than evaluating each situation individually. For example, in a situation where one player has the cards A-K-Q-J-4-3-2 of one suit and another player has 10-9-8-7-6-5, there are 7 × 6 = 42 ways that the first player can lead from that suit and the second player can follow. But GIB treats these situations as just two: the first player can lead either a high card or a low card; the exact cards played don’t matter. With this optimization (and a few others), GIB can solve a 52-card, fully observable deal *exactly* in about a second. GIB’s tactical accuracy makes up for its inability to reason about information. It finished 12th in a field of 35 in the par contest (involving just play of the hand, not bidding) at the 1998 human world championship, far exceeding the expectations of many human experts.

* * *

EXPLANATION-BASED GENERALIZATION

* * *

There are several reasons why GIB plays at expert level with Monte Carlo simulation, whereas Kriegspiel programs do not. First, GIB’s evaluation of the fully observable version of the game is exact, searching the full game tree, while Kriegspiel programs rely on inexact heuristics. But far more important is the fact that in bridge, most of the uncertainty in the partially observable information comes from the randomness of the deal, not from the adversarial play of the opponent. Monte Carlo simulation handles randomness well, but does not always handle strategy well, especially when the strategy involves the value of information.

**Scrabble**: Most people think the hard part about Scrabble is coming up with good words, but given the official dictionary, it turns out to be rather easy to program a move generator to find the highest-scoring move (Gordon, 1994). That doesn’t mean the game is solved, however: merely taking the top-scoring move each turn results in a good but not expert player. The problem is that Scrabble is both partially observable and stochastic: you don’t know what letters the other player has or what letters you will draw next. So playing Scrabble well combines the difficulties of backgammon and bridge. Nevertheless, in 2006, the QUACKLE program defeated the former world champion, David Boys, 3–2.

* * *

SCRABBLE

* * *

### 5.8 ALTERNATIVE APPROACHES

Because calculating optimal decisions in games is intractable in most cases, all algorithms must make some assumptions and approximations. The standard approach, based on minimax, evaluation functions, and alpha–beta, is just one way to do this. Probably because it has been worked on for so long, the standard approach dominates other methods in tournament play. Some believe that this has caused game playing to become divorced from the mainstream of AI research: the standard approach no longer provides much room for new insight into general questions of decision making. In this section, we look at the alternatives.

> ![image](images/00129.jpg)

> **Figure 5.14** A two-ply game tree for which heuristic minimax may make an error.

First, let us consider heuristic minimax. It selects an optimal move in a given search tree *provided that the leaf node evaluations are exactly correct*. In reality, evaluations are usually crude estimates of the value of a position and can be considered to have large errors associated with them. Figure 5.14 shows a two-ply game tree for which minimax suggests taking the right-hand branch because 100 > 99. That is the correct move if the evaluations are all correct. But of course the evaluation function is only approximate. Suppose that the evaluation of each node has an error that is independent of other nodes and is randomly distributed with mean zero and standard deviation of σ. Then when σ = 5, the left-hand branch is actually better 71% of the time, and 58% of the time when σ = 2. The intuition behind this is that the right-hand branch has four nodes that are close to 99; if an error in the evaluation of any one of the four makes the right-hand branch slip below 99, then the left-hand branch is better.

In reality, circumstances are actually worse than this because the error in the evaluation function is *not* independent. If we get one node wrong, the chances are high that nearby nodes in the tree will also be wrong. The fact that the node labeled 99 has siblings labeled 1000 suggests that in fact it might have a higher true value. We can use an evaluation function that returns a probability distribution over possible values, but it is difficult to combine these distributions properly, because we won’t have a good model of the very strong dependencies that exist between the values of sibling nodes

Next, we consider the search algorithm that generates the tree. The aim of an algorithm designer is to specify a computation that runs quickly and yields a good move. The alpha–beta algorithm is designed not just to select a good move but also to calculate bounds on the values of all the legal moves. To see why this extra information is unnecessary, consider a position in which there is only one legal move. Alpha–beta search still will generate and evaluate a large search tree, telling us that the only move is the best move and assigning it a value. But since we have to make the move anyway, knowing the move’s value is useless. Similarly, if there is one obviously good move and several moves that are legal but lead to a quick loss, we would not want alpha–beta to waste time determining a precise value for the lone good move. Better to just make the move quickly and save the time for later. This leads to the idea of the *utility of a node expansion*. A good search algorithm should select node expansions of high utility—that is, ones that are likely to lead to the discovery of a significantly better move. If there are no node expansions whose utility is higher than their cost (in terms of time), then the algorithm should stop searching and make a move. Notice that this works not only for clear-favorite situations but also for the case of *symmetrical* moves, for which no amount of search will show that one move is better than another.

This kind of reasoning about what computations to do is called **metareasoning** (reasoning about reasoning). It applies not just to game playing but to any kind of reasoning at all. All computations are done in the service of trying to reach better decisions, all have costs, and all have some likelihood of resulting in a certain improvement in decision quality. Alpha–beta incorporates the simplest kind of metareasoning, namely, a theorem to the effect that certain branches of the tree can be ignored without loss. It is possible to do much better. In [Chapter 16](#index_split_015.html#filepos2423989), we see how these ideas can be made precise and implementable.

* * *

METAREASONING

* * *

Finally, let us reexamine the nature of search itself. Algorithms for heuristic search and for game playing generate sequences of concrete states, starting from the initial state and then applying an evaluation function. Clearly, this is not how humans play games. In chess, one often has a particular goal in mind—for example, trapping the opponent’s queen—and can use this goal to *selectively* generate plausible plans for achieving it. This kind of goal-directed reasoning or planning sometimes eliminates combinatorial search altogether. David Wilkins’ (1980) PARADISE is the only program to have used goal-directed reasoning successfully in chess: it was capable of solving some chess problems requiring an 18-move combination. As yet there is no good understanding of how to *combine* the two kinds of algorithms into a robust and efficient system, although Bridge Baron might be a step in the right direction. A fully integrated system would be a significant achievement not just for gameplaying research but also for AI research in general, because it would be a good basis for a general intelligent agent.

### 5.9 SUMMARY

We have looked at a variety of games to understand what optimal play means and to understand how to play well in practice. The most important ideas are as follows:

> • A game can be defined by the **initial state** (how the board is set up), the legal **actions**in each state, the **result** of each action, a **terminal test** (which says when the game is over), and a **utility function** that applies to terminal states.

> • In two-player zero-sum games with **perfect information**, the **minimax** algorithm can select optimal moves by a depth-first enumeration of the game tree.

> • The **alpha–beta** search algorithm computes the same optimal move as minimax, but achieves much greater efficiency by eliminating subtrees that are provably irrelevant.

> • Usually, it is not feasible to consider the whole game tree (even with alpha–beta), so we need to cut the search off at some point and apply a heuristic **evaluation function** that estimates the utility of a state.

> • Many game programs precompute tables of best moves in the opening and endgame so that they can look up a move rather than search.

> • Games of chance can be handled by an extension to the minimax algorithm that evaluates a **chance node** by taking the average utility of all its children, weighted by the probability of each child.

> • Optimal play in games of **imperfect information**, such as Kriegspiel and bridge, requires reasoning about the current and future **belief states** of each player. A simple approximation can be obtained by averaging the value of an action over each possible configuration of missing information.

> • Programs have bested even champion human players at games such as chess, checkers, and Othello. Humans retain the edge in several games of imperfect information, such as poker, bridge, and Kriegspiel, and in games with very large branching factors and little good heuristic knowledge, such as Go.

### BIBLIOGRAPHICAL AND HISTORICAL NOTES

The early history of mechanical game playing was marred by numerous frauds. The most notorious of these was Baron Wolfgang von Kempelen’s (1734–1804) “The Turk,” a supposed chess-playing automaton that defeated Napoleon before being exposed as a magician’s trick cabinet housing a human chess expert (see Levitt, 2000). It played from 1769 to 1854. In 1846, Charles Babbage (who had been fascinated by the Turk) appears to have contributed the first serious discussion of the feasibility of computer chess and checkers (Morrison and Morrison, 1961). He did not understand the exponential complexity of search trees, claiming “the combinations involved in the Analytical Engine enormously surpassed any required, even by the game of chess.” Babbage also designed, but did not build, a special-purpose machine for playing tic-tac-toe. The first true gameplaying machine was built around 1890 by the Spanish engineer Leonardo Torres y Quevedo. It specialized in the “KRK” (king and rook vs. king) chess endgame, guaranteeing a win with king and rook from any position.

The minimax algorithm is traced to a 1912 paper by Ernst Zermelo, the developer of modern set theory. The paper unfortunately contained several errors and did not describe minimax correctly. On the other hand, it did lay out the ideas of retrograde analysis and proposed (but did not prove) what became known as Zermelo’s theorem: that chess is determined—White can force a win or Black can or it is a draw; we just don’t know which. Zermelo says that should we eventually know, “Chess would of course lose the character of a game at all.” A solid foundation for game theory was developed in the seminal work *Theory of Games and Economic Behavior* (von Neumann and Morgenstern, 1944), which included an analysis showing that some games *require* strategies that are randomized (or otherwise unpredictable). See [Chapter 17](#index_split_015.html#filepos2562268) for more information.

John McCarthy conceived the idea of alpha–beta search in 1956, although he did not publish it. The NSS chess program (Newell **et al.**, 1958) used a simplified version of alpha–beta; it was the first chess program to do so. Alpha–beta pruning was described by Hart and Edwards (1961) and Hart **et al.** (1972). Alpha–beta was used by the “Kotok–McCarthy” chess program written by a student of John McCarthy (Kotok, 1962). Knuth and Moore (1975) proved the correctness of alpha–beta and analysed its time complexity. Pearl (1982b) shows alpha–beta to be asymptotically optimal among all fixed-depth game-tree search algorithms.

Several attempts have been made to overcome the problems with the “standard approach” that were outlined in [Section 5.8](#index_split_000.html#filepos757873). The first nonexhaustive heuristic search algorithm with some theoretical grounding was probably B\* (Berliner, 1979), which attempts to maintain interval bounds on the possible value of a node in the game tree rather than giving it a single point-valued estimate. Leaf nodes are selected for expansion in an attempt to refine the top-level bounds until one move is “clearly best.” Palay (1985) extends the B\* idea using probability distributions on values in place of intervals. David McAllester’s (1988) conspiracy number search expands leaf nodes that, by changing their values, could cause the program to prefer a new move at the root. MGSS\* (Russell and Wefald, 1989) uses the decision-theoretic techniques of [Chapter 16](#index_split_015.html#filepos2423989) to estimate the value of expanding each leaf in terms of the expected improvement in decision quality at the root. It outplayed an alpha–beta algorithm at Othello despite searching an order of magnitude fewer nodes. The MGSS approach is, in principle, applicable to the control of any form of deliberation.

Alpha–beta search is in many ways the two-player analog of depth-first branch-and-bound, which is dominated by A\* in the single-agent case. The SSS\* algorithm (Stockman, 1979) can be viewed as a two-player A\* and never expands more nodes than alpha–beta to reach the same decision. The memory requirements and computational overhead of the queue make SSS\* in its original form impractical, but a linear-space version has been developed from the RBFS algorithm (Korf and Chickering, 1996). Plaat **et al.** (1996) developed a new view of SSS\* as a combination of alpha–beta and transposition tables, showing how to overcome the drawbacks of the original algorithm and developing a new variant called MTD(*f*) that has been adopted by a number of top programs.

D. F. Beal (1980) and Dana Nau (1980, 1983) studied the weaknesses of minimax applied to approximate evaluations. They showed that under certain assumptions about the distribution of leaf values in the tree, minimaxing can yield values at the root that are actually *less* reliable than the direct reliable than the direct use of the evaluation function itself. Pearl’s book *Heuristics* (1984) partially explains this apparent paradox and analyzes many gameplaying algorithms. Baum and Smith (1997) propose a probability-based replacement for minimax, showing that it results in better choices in certain games. The expectiminimax algorithm was proposed by Donald Michie (1966). Bruce Ballard (1983) extended alpha–beta pruning to cover trees with chance nodes and Hauk (2004) reexamines this work and provides empirical results.

Koller and Pfeffer (1997) describe a system for completely solving partially observable games. The system is quite general, handling games whose optimal strategy requires randomized moves and games that are more complex than those handled by any previous system. Still, it can’t handle games as complex as poker, bridge, and Kriegspiel. Frank *et al*. (1998) describe several variants of Monte Carlo search, including one where MIN has complete information but MAX does not. Among deterministic, partially observable games, Kriegspiel has received the most attention. Ferguson demonstrated hand-derived randomized strategies for winning Kriegspiel with a bishop and knight (1992) or two bishops (1995) against a king. The first Kriegspiel programs concentrated on finding endgame checkmates and performed AND—OR search in belief-state space (Sakuta and Iida, 2002; Bolognesi and Ciancarini, 2003). Incremental belief-state algorithms enabled much more complex midgame checkmates to be found (Russell and Wolfe, 2005; Wolfe and Russell, 2007), but efficient state estimation remains the primary obstacle to effective general play (Parker *et al*., 2005).

Chess was one of the first tasks undertaken in AI, with early efforts by many of the pioneers of computing, including Konrad Zuse in 1945, Norbert Wiener in his book *Cybernetics* (1948), and Alan Turing in 1950 (see Turing *et al*., 1953). But it was Claude Shannon’s article *Programming a Computer for Playing Chess* (1950) that had the most complete set of ideas, describing a representation for board positions, an evaluation function, quiescence search, and some ideas for selective (nonexhaustive) game-tree search. Slater (1950) and the commentators on his article also explored the possibilities for computer chess play.

D. G. Prinz (1952) completed a program that solved chess endgame problems but did not play a full game. Stan Ulam and a group at the Los Alamos National Lab produced a program that played chess on a 6 × 6 board with no bishops (Kister *et al*., 1957). It could search 4 plies deep in about 12 minutes. Alex Bernstein wrote the first documented program to play a full game of standard chess (Bernstein and Roberts, 1958).[⁵](#index_split_015.html#filepos5578956)

The first computer chess match featured the Kotok—McCarthy program from MIT (Kotok, 1962) and the ITEP program written in the mid-1960s at Moscow’s Institute of Theoretical and Experimental Physics (Adelson-Velsky *et al*., 1970). This intercontinental match was played by telegraph. It ended with a 3–1 victory for the ITEP program in 1967. The first chess program to compete successfully with humans was MIT’s MACHACK-6 (Greenblatt *et al*., 1967). Its Elo rating of approximately 1400 was well above the novice level of 1000.

The Fredkin Prize, established in 1980, offered awards for progressive milestones in chess play. The $5,000 prize for the first program to achieve a master rating went to BELLE (Condon and Thompson, 1982), which achieved a rating of 2250. The $10,000 prize for the first program to achieve a USCF (United States Chess Federation) rating of 2500 (near the grandmaster level) was awarded to DEEP THOUGHT (Hsu *et al*., 1990) in 1989. The grand prize, $100,000, went to DEEP BLUE (Campbell *et al*., 2002; Hsu, 2004) for its landmark victory over world champion Garry Kasparov in a 1997 exhibition match. Kasparov wrote:

> The decisive game of the match was Game 2, which left a scar in my memory … we saw something that went well beyond our wildest expectations of how well a computer would be able to foresee the long-term positional consequences of its decisions. The machine refused to move to a position that had a decisive short-term advantage—showing a very human sense of danger. (Kasparov, 1997)

Probably the most complete description of a modern chess program is provided by Ernst Heinz (2000), whose DARK THOUGHT program was the highest-ranked noncommercial PC program at the 1999 world championships.

> ![image](images/00130.jpg)

> **Figure 5.15** Pioneers in computer chess: (a) Herbert Simon and Allen Newell, developers of the NSS program (1958); (b) John McCarthy and the Kotok-McCarthy program on an IBM 7090 (1967).

In recent years, chess programs are pulling ahead of even the world’s best humans. In 2004–2005 HYDRA defeated grand master Evgeny Vladimirov 3.5–0.5, world champion Ruslan Ponomariov 2–0, and seventh-ranked Michael Adams 5.5–0.5. In 2006, DEEP FRITZ beat world champion Vladimir Kramnik 4–2, and in 2007 RYBKA defeated several grand masters in games in which it gave odds (such as a pawn) to the human players. As of 2009, the highest Elo rating ever recorded was Kasparov’s 2851. HYDRA (Donninger and Lorenz, 2004) is rated somewhere between 2850 and 3000, based mostly on its trouncing of Michael Adams. The RYBKA program is rated between 2900 and 3100, but this is based on a small number of games and is not considered reliable. Ross (2004) shows how human players have learned to exploit some of the weaknesses of the computer programs.

**Checkers** was the first of the classic games fully played by a computer. Christopher Strachey (1952) wrote the first working program for checkers. Beginning in 1952, Arthur Samuel of IBM, working in his spare time, developed a checkers program that learned its own evaluation function by playing itself thousands of times (Samuel, 1959, 1967). We describe this idea in more detail in [Chapter 21](#index_split_015.html#filepos3262268). Samuel’s program began as a novice but after only a few days’ self-play had improved itself beyond Samuel’s own level. In 1962 it defeated Robert Nealy, a champion at “blind checkers,” through an error on his part. When one considers that Samuel’s computing equipment (an IBM 704) had 10,000 words of main memory, magnetic tape for long-term storage, and a.000001 GHz processor, the win remains a great accomplishment.

The challenge started by Samuel was taken up by Jonathan Schaeffer of the University of Alberta. His CHINOOK program came in second in the 1990 U.S. Open and earned the right to challenge for the world championship. It then ran up against a problem, in the form of Marion Tinsley. Dr. Tinsley had been world champion for over 40 years, losing only three games in all that time. In the first match against CHINOOK, Tinsley suffered his fourth and fifth losses, but won the match 20.5–18.5. A rematch at the 1994 world championship ended prematurely when Tinsley had to withdraw for health reasons. CHINOOK became the official world champion. Schaeffer kept on building on his database of endgames, and in 2007 “solved” checkers (Schaeffer *et al*., 2007; Schaeffer, 2008). This had been predicted by Richard Bellman (1965). In the paper that introduced the dynamic programming approach to retrograde analysis, he wrote, “In checkers, the number of possible moves in any given situation is so small that we can confidently expect a complete digital computer solution to the problem of optimal play in this game.” Bellman did not, however, fully appreciate the size of the checkers game tree. There are about 500 quadrillion positions. After 18 years of computation on a cluster of 50 or more machines, Jonathan Schaeffer’s team completed an endgame table for all checkers positions with 10 or fewer pieces: over 39 trillion entries. From there, they were able to do forward alpha–beta search to derive a policy that proves that checkers is in fact a draw with best play by both sides. Note that this is an application of bidirectional search (Section 3.4.6). Building an endgame table for all of checkers would be impractical: it would require a billion gigabytes of storage. Searching without any table would also be impractical: the search tree has about 847 positions, and would take thousands of years to search with today’s technology. Only a combination of clever search, endgame data, and a drop in the price of processors and memory could solve checkers. Thus, checkers joins Qubic (Patashnik, 1980), Connect Four (Allis, 1988), and Nine-Men’s Morris (Gasser, 1998) as games that have been solved by computer analysis.

**Backgammon**, a game of chance, was analyzed mathematically by Gerolamo Cardano (1663), but only taken up for computer play in the late 1970s, first with the BKG program (Berliner, 1980b); it used a complex, manually constructed evaluation function and searched only to depth 1. It was the first program to defeat a human world champion at a major classic game (Berliner, 1980a). Berliner readily acknowledged that BKG was very lucky with the dice. Gerry Tesauro’s (1995) TD-GAMMON played consistently at world champion level. The BGBLITZ program was the winner of the 2008 Computer Olympiad.

**Go** is a deterministic game, but the large branching factor makes it challeging. The key issues and early literature in computer Go are summarized by Bouzy and Cazenave (2001) and Müller (2002). Up to 1997 there were no competent Go programs. Now the best programs play *most* of their moves at the master level; the only problem is that over the course of a game they usually make at least one serious blunder that allows a strong opponent to win. Whereas alpha–beta search reigns in most games, many recent Go programs have adopted Monte Carlo methods based on the UCT (upper confidence bounds on trees) scheme (Kocsis and Szepesvari, 2006). The strongest Go program as of 2009 is Gelly and Silver’s MOGO (Wang and Gelly, 2007; Gelly and Silver, 2008). In August 2008, MOGO scored a surprising win against top professional Myungwan Kim, albeit with MOGO receiving a handicap of nine stones (about the equivalent of a queen handicap in chess). Kim estimated MOGO’s strength at 2–3 dan, the low end of advanced amateur. For this match, MOGO was run on an 800-processor 15 teraflop supercomputer (1000 times Deep Blue). A few weeks later, MOGO, with only a five-stone handicap, won against a 6-dan professional. In the 9 × 9 form of Go, MOGO is at approximately the 1-dan professional level. Rapid advances are likely as experimentation continues with new forms of Monte Carlo search. The *Computer Go* *Newsletter*, published by the Computer Go Association, describes current developments.

**Bridge**: Smith *et al*. (1998) report on how their planning-based program won the 1998 computer bridge championship, and (Ginsberg, 2001) describes how his GIB program, based on Monte Carlo simulation, won the following computer championship and did surprisingly well against human players and standard book problem sets. From 2001–2007, the computer bridge championship was won five times by JACK and twice by WBRIDGE5\. Neither has had academic articles explaining their structure, but both are rumored to use the Monte Carlo technique, which was first proposed for bridge by Levy (1989).

Scrabble: A good description of a top program, MAVEN, is given by its creator, Brian Sheppard (2002). Generating the highest-scoring move is described by Gordon (1994), and modeling opponents is covered by Richards and Amir (2007).

**Soccer** (Kitano *et al*., 1997b; Visser *et al*., 2008) and **billiards** (Lam and Greenspan, 2008; Archibald *et al*., 2009) and other stochastic games with a continuous space of actions are beginning to attract attention in AI, both in simulation and with physical robot players.

Computer game competitions occur annually, and papers appear in a variety of venues. The rather misleadingly named conference proceedings *Heuristic Programming in Artificial Intelligence* report on the Computer Olympiads, which include a wide variety of games. The General Game Competition (Love *et al*., 2006) tests programs that must learn to play an unknown game given only a logical description of the rules of the game. There are also several edited collections of important papers on gameplaying research (Levy, 1988a, 1988b; Marsland and Schaeffer, 1990). The International Computer Chess Association (ICCA), founded in 1977, publishes the *ICGA Journal* (formerly the *ICCA Journal*). Important papers have been published in the serial anthology *Advances in Computer Chess*, starting with Clarke (1977). Volume 134 of the journal *Artificial Intelligence* (2002) contains descriptions of state-of-the-art programs for chess, Othello, Hex, shogi, Go, backgammon, poker, Scrabble, and other games. Since 1998, a biennial *Computers and Games* conference has been held.

### EXERCISES

**5.1** Suppose you have an oracle, *OM*(*s*), that correctly predicts the opponent’s move in any state. Using this, formulate the definition of a game as a (single-agent) search problem. Describe an algorithm for finding the optimal move.

**5.2** Consider the problem of solving two 8-puzzles.

> **a.** Give a complete problem formulation in the style of [Chapter 3](#index_split_000.html#filepos301685).

> **b.** How large is the reachable state space? Give an exact numerical expression.

> **c.** Suppose we make the problem adversarial as follows: the two players take turns moving; a coin is flipped to determine the puzzle on which to make a move in that turn; and the winner is the first to solve one puzzle. Which algorithm can be used to choose a move in this setting?

> **d.** Give an informal proof that someone will eventually win if both play perfectly.

> ![image](images/00131.jpg)

> **Figure 5.16** (a) A map where the cost of every edge is 1. Initially the pursuer *P* is at node **b** and the evader *E* is at node **d**. (b) A partial game tree for this map. Each node is labeled with the *P*, *E* positions. *P* moves first. Branches marked “?” have yet to be explored.

5.3 Imagine that, in Exercise 3.3, one of the friends wants to avoid the other. The problem then becomes a two-player **pursuit–evasion** game. We assume now that the players take turns moving. The game ends only when the players are on the same node; the terminal payoff to the pursuer is minus the total time taken. (The evader “wins” by never losing.) An example is shown in [Figure 5.16.](#index_split_012.html#filepos789577)

> **a.** Copy the game tree and mark the values of the terminal nodes.

> **b.** Next to each internal node, write the strongest fact you can infer about its value (a number, one or more inequalities such as “≥ 14”, or a “?”).

> **c.** Beneath each question mark, write the name of the node reached by that branch.

> **d.** Explain how a bound on the value of the nodes in (c) can be derived from consideration of shortest-path lengths on the map, and derive such bounds for these nodes. Remember the cost to get to each leaf as well as the cost to solve it.

> **e.** Now suppose that the tree as given, with the leaf bounds from (d), is evaluated from left to right. Circle those “?” nodes that would *not* need to be expanded further, given the bounds from part (d), and cross out those that need not be considered at all.

> **f.** Can you prove anything in general about who wins the game on a map that is a tree?

* * *

PURSUIT–CEVASION

* * *

197**5.4** Describe and implement state descriptions, move generators, terminal tests, utility functions, and evaluation functions for one or more of the following stochastic games: Monopoly, Scrabble, bridge play with a given contract, or Texas hold’em poker.

![radio](images/00004.jpg)

**5.5** Describe and implement a *real-time, multiplayer* gameplaying environment, where time is part of the environment state and players are given fixed time allocations.

**5.6** Discuss how well the standard approach to game playing would apply to games such as tennis, pool, and croquet, which take place in a continuous physical state space.

**5.7** Prove the following assertion: For every game tree, the utility obtained by MAX using minimax decisions against a suboptimal MIN will be never be lower than the utility obtained playing against an optimal MIN. Can you come up with a game tree in which MAX can do still better using a *suboptimal* strategy against a suboptimal MIN?

> ![image](images/00132.jpg)

> **Figure 5.17** The starting position of a simple game. Player *A* moves first. The two players take turns moving, and each player must move his token to an open adjacent space in either direction. If the opponent occupies an adjacent space, then a player may jump over the opponent to the next open space if any. (For example, if *A* is on 3 and *B* is on 2, then *A* may move back to 1.) The game ends when one player reaches the opposite end of the board. If player *A* reaches space 4 first, then the value of the game to *A* is +1; if player *B* reaches space 1 first, then the value of the game to *A* is −1.

**5.8** Consider the two-player game described in [Figure 5.17](#index_split_012.html#filepos793724).

> **a.** Draw the complete game tree, using the following conventions:

> • Write each state as (*s[A]*, *s[B]*), where *s[A]* and *s[B]* denote the token locations.

> • Put each terminal state in a square box and write its game value in a circle.

> • Put *loop states* (states that already appear on the path to the root) in double square boxes. Since their value is unclear, annotate each with a “?” in a circle.

> **b.** Now mark each node with its backed-up minimax value (also in a circle). Explain how you handled the “?” values and why.

> **c.** Explain why the standard minimax algorithm would fail on this game tree and briefly sketch how you might fix it, drawing on your answer to (b). Does your modified algorithm give optimal decisions for all games with loops?

> **d.** This 4-square game can be generalized to *n* squares for any *n* > 2. Prove that *A* wins if *n* is even and loses if *n* is odd.

**5.9** This problem exercises the basic concepts of game playing, using tic-tac-toe (noughts and crosses) as an example. We define *X[n]* as the number of rows, columns, or diagonals with exactly *n* *X*’s and no *O*’s. Similarly, *O*[*n*] is the number of rows, columns, or diagonals with just *n* *O*’s. The utility function assigns +1 to any position with *X[3]* = 1 and −1 to any position with *O*[3] = 1. All other terminal positions have utility 0. For nonterminal positions, we use a linear evaluation function defined as *Eval* (*s*) = 3*X*[2](*s*) + *X*[1](*s*)–(3*O*[2](*s*)+*O*[1](*s*)).

> **a.** Approximately how many possible games of tic-tac-toe are there?

> **b.** Show the whole game tree starting from an empty board down to depth 2 (i.e., one *X* and one *O* on the board), taking symmetry into account.

> **c.** Mark on your tree the evaluations of all the positions at depth 2.

> **d.** Using the minimax algorithm, mark on your tree the backed-up values for the positions at depths 1 and 0, and use those values to choose the best starting move.

> **e.** Circle the nodes at depth 2 that would *not* be evaluated if alpha–beta pruning were applied, assuming the nodes are generated in the optimal order for alpha–beta pruning.

**5.10** Consider the family of generalized tic-tac-toe games, defined as follows. Each particular game is specified by a set *S* of *squares* and a collection *W* of *winning positions*. Each winning position is a subset of *S*. For example, in standard tic-tac-toe, *S* is a set of 9 squares and *W* is a collection of 8 subsets of *W*: the three rows, the three columns, and the two diagonals. In other respects, the game is identical to standard tic-tac-toe. Starting from an empty board, players alternate placing their marks on an empty square. A player who marks every square in a winning position wins the game. It is a tie if all squares are marked and neither player has won.

> **a.** Let *N* = |*S*|, the number of squares. Give an upper bound on the number of nodes in the complete game tree for generalized tic-tac-toe as a function of *N*.

> **b.** Give a lower bound on the size of the game tree for the worst case, where *W* = { }.

> **c.** Propose a plausible evaluation function that can be used for any instance of generalized tic-tac-toe. The function may depend on *S* and *W*.

> **d.** Assume that it is possible to generate a new board and check whether it is a winning position in 100*N* machine instructions and assume a 2 gigahertz processor. Ignore memory limitations. Using your estimate in (a), roughly how large a game tree can be completely solved by alpha–beta in a second of CPU time? a minute? an hour?

![radio](images/00004.jpg)

**5.11** Develop a general gameplaying program, capable of playing a variety of games.

> **a.** Implement move generators and evaluation functions for one or more of the following games: Kalah, Othello, checkers, and chess.

> **b.** Construct a general alpha–beta gameplaying agent.

> **c.** Compare the effect of increasing search depth, improving move ordering, and improving the evaluation function. How close does your effective branching factor come to the ideal case of perfect move ordering?

> **d.** Implement a selective search algorithm, such as B\* (Berliner, 1979), conspiracy number search (McAllester, 1988), or MGSS\* (Russell and Wefald, 1989) and compare its performance to A\*.

> ![image](images/00133.jpg)

> **Figure 5.18** Situation when considering whether to prune node *n[j]*.

**5.12** Describe how the minimax and alpha–beta algorithms change for two-player, nonzero-sum games in which each player has a distinct utility function and both utility functions are known to both players. If there are no constraints on the two terminal utilities, is it possible for any node to be pruned by alpha–beta? What if the player’s utility functions on any state differ by at most a constant *k*, making the game almost cooperative?

**5.13** Develop a formal proof of correctness for alpha–beta pruning. To do this, consider the situation shown in [Figure 5.18](#index_split_012.html#filepos801765). The question is whether to prune node *n[j]*, which is a max-node and a descendant of node *n[1]*. The basic idea is to prune it if and only if the minimax value of *n[1]* can be shown to be independent of the value of *n[j]*.

> **a.** Mode *n*[1] takes on the minimum value among its children: ![equ](images/00134.jpg). Find a similar expression for *n*[2] and hence an expression for *n*[1] in terms of *n[j]*.

> **b.** Let *l[i]* be the minimum (or maximum) value of the nodes to the *left* of node *n[i]* at depth *i*, whose minimax value is already known. Similarly, let *r[i]* be the minimum (or maximum) value of the unexplored nodes to the right of *n[i]* at depth *i*. Rewrite your expression for *n[1]* in terms of the *l*[*i*] and *r*[*i*] values.

> **c.** Now reformulate the expression to show that in order to affect *n[1]*, *n[j]* must not exceed a certain bound derived from the *l[i]* values.

> **d.** Repeat the process for the case where *n[j]* is a minnode.

**5.14** Prove that alpha-beta pruning takes time *O*(2^(*m*/2)) with optimal move ordering, where *m* is the maximum depth of the game tree.

**5.15** Suppose you have a chess program that can evaluate 10 million nodes per second. Decide on a compact representation of a game state for storage in a transposition table. About how many entries can you fit in a 2-gigabyte in-memory table? Will that be enough for the three minutes of search allocated for one move? How many table lookups can you do in the time it would take to do one evaluation? Now suppose the transposition table is stored on disk. About how many evaluations could you do in the time it takes to do one disk seek with standard disk hardware?

> ![image](images/00135.jpg)

> **Figure 5.19** The complete game tree for a trivial game with chance nodes.

**5.16** This question considers pruning in games with chance nodes. [Figure 5.19](#index_split_012.html#filepos805435) shows the complete game tree for a trivial game. Assume that the leaf nodes are to be evaluated in leftto-right order, and that before a leaf node is evaluated, we know nothing about its value–the range of possible values is −∞ to ∞.

> **a.** Copy the figure, mark the value of all the internal nodes, and indicate the best move at the root with an arrow.

> **b.** Given the values of the first six leaves, do we need to evaluate the seventh and eighth leaves? Given the values of the first seven leaves, do we need to evaluate the eighth leaf? Explain your answers.

> **c.** Suppose the leaf node values are known to lie between −2 and 2 inclusive. After the first two leaves are evaluated, what is the value range for the left-hand chance node?

> **d.** Circle all the leaves that need not be evaluated under the assumption in (c).

![radio](images/00004.jpg)

**5.17** Implement the expectiminimax algorithm and the *\-alpha–beta algorithm, which is described by Ballard (1983), for pruning game trees with chance nodes. Try them on a game such as backgammon and measure the pruning effectiveness of* -alpha–beta.

![book](images/00005.jpg)

**5.18** Prove that with a positive linear transformation of leaf values (i.e., transforming a value *x* to *ax* + *b* where *a* > 0), the choice of move remains unchanged in a game tree, even when there are chance nodes.

**5.19** Consider the following procedure for choosing moves in games with chance nodes:

> • Generate some dice-roll sequences (say, 50) down to a suitable depth (say, 8).

> • With known dice rolls, the game tree becomes deterministic. For each dice-roll sequence, solve the resulting deterministic game tree using alpha–beta.

> • Use the results to estimate the value of each move and to choose the best.

Will this procedure work well? Why (or why not)?

**5.20** In the following, a “max” tree consists only of max nodes, whereas an “expectimax” tree consists of a max node at the root with alternating layers of chance and max nodes. At chance nodes, all outcome probabilities are nonzero. The goal is to *find the value of the root* with a bounded-depth search. For each of (a)–(f), either give an example or explain why this is impossible.

> **a.** Assuming that leaf values are finite but unbounded, is pruning (as in alpha–beta) ever possible in a max tree?

> **b.** Is pruning ever possible in an expectimax tree under the same conditions?

> **c.** If leaf values are all nonnegative, is pruning ever possible in a max tree? Give an example, or explain why not.

> **d.** If leaf values are all nonnegative, is pruning ever possible in an expectimax tree? Give an example, or explain why not.

> **e.** If leaf values are all in the range \[0, 1\], is pruning ever possible in a max tree? Give an example, or explain why not.

> **f.** If leaf values are all in the range \[0, 1\], is pruning ever possible in an expectimax tree?

> **g.** Consider the outcomes of a chance node in an expectimax tree. Which of the following evaluation orders is most likely to yield pruning opportunities?

> (i) Lowest probability first

> (ii) Highest probability first

> (iii) Doesn’t make any difference

**5.21** Which of the following are true and which are false? Give brief explanations.

> **a.** In a fully observable, turn-taking, zero-sum game between two perfectly rational players, it does not help the first player to know what strategy the second player is using–that is, what move the second player will make, given the first player’s move.

> **b.** In a partially observable, turn-taking, zero-sum game between two perfectly rational players, it does not help the first player to know what move the second player will make, given the first player’s move.

> **c.** A perfectly rational backgammon agent never loses.

**5.22** Consider carefully the interplay of chance events and partial information in each of the games in Exercise 5.4.

> **a.** For which is the standard expectiminimax model appropriate? Implement the algorithm and run it in your gameplaying agent, with appropriate modifications to the gameplaying environment.

> **b.** For which would the scheme described in Exercise 5.19 be appropriate?

> **c.** Discuss how you might deal with the fact that in some of the games, the players do not have the same knowledge of the current state.

## **6 CONSTRAINT SATISFACTION PROBLEMS**

> *In which we see how treating states as more than just little black boxes leads to the invention of a range of powerful new search methods and a deeper understanding of problem structure and complexity.*

[Chapters 3](#index_split_000.html#filepos301685) and [4](#index_split_000.html#filepos513290) explored the idea that problems can be solved by searching in a space of **states**. These states can be evaluated by domain-specific heuristics and tested to see whether they are goal states. From the point of view of the search algorithm, however, each state is atomic, or indivisible—a black box with no internal structure.

This chapter describes a way to solve a wide variety of problems more efficiently. We use a **factored representation** for each state: a set of variables, each of which has a value. A problem is solved when each variable has a value that satisfies all the constraints on the variable. A problem described this way is called a **constraint satisfaction problem**, or CSP.

* * *

CONSTRAINT SATISFACTION PROBLEM

* * *

CSP search algorithms take advantage of the structure of states and use *general-purpose* rather than *problem-specific* heuristics to enable the solution of complex problems. The main idea is to eliminate large portions of the search space all at once by identifying variable/value combinations that violate the constraints.

### 6.1 DEFINING CONSTRAINT SATISFACTION PROBLEMS

A constraint satisfaction problem consists of three components, *X*, *D*, and *C*:

> *X* is a set of variables, {*X*[1], …, *X*[*n*]}.

> *D* is a set of domains, {*D*[1], …, *D*[*n*]}, one for each variable.

> *C* is a set of constraints that specify allowable combinations of values.

Each domain *D*[*i*] consists of a set of allowable values, {*v*[1], …, *v*[*k*]} for variable *X*[*i*]. Each constraint *C*[*i*] consists of a pair 〈*scope*, *rel*〉, where *scope* is a tuple of variables that participate in the constraint and *rel* is a relation that defines the values that those variables can take on. A relation can be represented as an explicit list of all tuples of values that satisfy the constraint, or as an abstract relation that supports two operations: testing if a tuple is a member of the relation and enumerating the members of the relation. For example, if *X*[1] and *X*[2] both have the domain {A,B}, then the constraint saying the two variables must have different values can be written as ![equ](images/00136.jpg).

To solve a CSP, we need to define a state space and the notion of a solution. Each state in a CSP is defined by an **assignment** of values to some or all of the variables, {*X*[*i*] = *v*[*i*], *X*[*j*] = *v*[*j*], …}. An assignment that does not violate any constraints is called a **consistent** or legal assignment. A **complete assignment** is one in which every variable is assigned, and a **solution** to a CSP is a consistent, complete assignment. A **partial assignment** is one that assigns values to only some of the variables.

* * *

ASSIGNMENT

* * *

* * *

CONSISTENT

* * *

* * *

COMPLETE ASSIGNMENT

* * *

* * *

SOLUTION

* * *

* * *

PARTIAL ASSIGNMENT

* * *

#### **6.1.1 Example problem: Map coloring**

Suppose that, having tired of Romania, we are looking at a map of Australia showing each of its states and territories ([Figure 6.1](#index_split_013.html#filepos821837)(a)). We are given the task of coloring each region either red, green, or blue in such a way that no neighboring regions have the same color. To formulate this as a CSP, we define the variables to be the regions

> ![equ](images/00137.jpg)

The domain of each variable is the set *D*[*i*] = {*red*, *green*, *blue*}. The constraints require neighboring regions to have distinct colors. Since there are nine places where regions border, there are nine constraints:

> ![equ](images/00138.jpg)

Here we are using abbreviations; *SA* ≠ *WA* is a shortcut for 〈(*SA*, *WA*), *SA* ≠ *WA*〉, where *SA* ≠ *WA* can be fully enumerated in turn as

> ![equ](images/00139.jpg)

There are many possible solutions to this problem, such as

> ![equ](images/00140.jpg)

It can be helpful to visualize a CSP as a **constraint graph**, as shown in [Figure 6.1](#index_split_013.html#filepos821837)(b). The nodes of the graph correspond to variables of the problem, and a link connects any two variables that participate in a constraint.

* * *

CONSTRAINT GRAPH

* * *

Why formulate a problem as a CSP? One reason is that the CSPs yield a natural representation for a wide variety of problems; if you already have a CSP-solving system, it is often easier to solve a problem using it than to design a custom solution using another search technique. In addition, CSP solvers can be faster than state-space searchers because the CSP solver can quickly eliminate large swatches of the search space. For example, once we have chosen {*SA* = *blue*} in the Australia problem, we can conclude that none of the five neighboring variables can take on the value *blue*. Without taking advantage of constraint propagation, a search procedure would have to consider 3⁵ = 243 assignments for the five neighboring variables; with constraint propagation we never have to consider blue as a value, so we have only 2⁵ = 32 assignments to look at, a reduction of 87%.

In regular state-space search we can only ask: is this specific state a goal? No? What about this one? With CSPs, once we find out that a partial assignment is not a solution, we can immediately discard further refinements of the partial assignment. Furthermore, we can see *why* the assignment is not a solution—we see which variables violate a constraint—so we can focus attention on the variables that matter. As a result, many problems that are intractable for regular state-space search can be solved quickly when formulated as a CSP.

> ![image](images/00141.jpg)

> **Figure 6.1** (a) The principal states and territories of Australia. Coloring this map can be viewed as a constraint satisfaction problem (CSP). The goal is to assign colors to each region so that no neighboring regions have the same color. (b) The map-coloring problem represented as a constraint graph.

#### **6.1.2 Example problem: Job-shop scheduling**

Factories have the problem of scheduling a day’s worth of jobs, subject to various constraints. In practice, many of these problems are solved with CSP techniques. Consider the problem of scheduling the assembly of a car. The whole job is composed of tasks, and we can model each task as a variable, where the value of each variable is the time that the task starts, expressed as an integer number of minutes. Constraints can assert that one task must occur before another—for example, a wheel must be installed before the hubcap is put on—and that only so many tasks can go on at once. Constraints can also specify that a task takes a certain amount of time to complete.

We consider a small part of the car assembly, consisting of 15 tasks: install axles (front and back), affix all four wheels (right and left, front and back), tighten nuts for each wheel, affix hubcaps, and inspect the final assembly. We can represent the tasks with 15 variables:

> ![equ](images/00142.jpg)

The value of each variable is the time that the task starts. Next we represent **precedence constraints** between individual tasks. Whenever a task *T*[1] must occur before task *T*[2], and task *T*[1] takes duration *d*[1] to complete, we add an arithmetic constraint of the form

* * *

PRECEDENCE CONSTRAINTS

* * *

> ![equ](images/00143.jpg)

In our example, the axles have to be in place before the wheels are put on, and it takes 10 minutes to install an axle, so we write

> ![equ](images/00144.jpg)

Next we say that, for each wheel, we must affix the wheel (which takes 1 minute), then tighten the nuts (2 minutes), and finally attach the hubcap (1 minute, but not represented yet):

> ![equ](images/00145.jpg)

* * *

DISJUNCTIVE CONSTRAINT

* * *

Suppose we have four workers to install wheels, but they have to share one tool that helps put the axle in place. We need a **disjunctive constraint** to say that *Axle*[*F*] and *Axle*[*B*] must not overlap in time; either one comes first or the other does:

> ![equ](images/00146.jpg)

This looks like a more complicated constraint, combining arithmetic and logic. But it still reduces to a set of pairs of values that *Axle*[*F*] and *Axle*[*F*] can take on.

We also need to assert that the inspection comes last and takes 3 minutes. For every variable except Inspect we add a constraint of the form *X* + *d*[*X*] ≤ *Inspect*. Finally, suppose there is a requirement to get the whole assembly done in 30 minutes. We can achieve that by limiting the domain of all variables:

> ![equ](images/00147.jpg)

This particular problem is trivial to solve, but CSPs have been applied to job-shop scheduling problems like this with thousands of variables. In some cases, there are complicated constraints that are difficult to specify in the CSP formalism, and more advanced planning techniques are used, as discussed in [Chapter 11](#index_split_015.html#filepos1612250).

#### **6.1.3 Variations on the CSP formalism**

The simplest kind of CSP involves variables that have **discrete**, **finite domains**. Map-coloring problems and scheduling with time limits are both of this kind. The 8-queens problem described in [Chapter 3](#index_split_000.html#filepos301685) can also be viewed as a finite-domain CSP, where the variables *Q*[1], …, *Q*[8] are the positions of each queen in columns 1, …, 8 and each variable has the domain *D*[*i*] = {1, 2, 3, 4, 5, 6, 7, 8}.

* * *

DISCRETE DOMAIN

* * *

* * *

FINITE DOMAIN

* * *

A discrete domain can be **infinite**, such as the set of integers or strings. (If we didn’t put a deadline on the job-scheduling problem, there would be an infinite number of start times for each variable.) With infinite domains, it is no longer possible to describe constraints by enumerating all allowed combinations of values. Instead, a **constraint language** must be used that understands constraints such as *T*[1] + *d*[1] ≤ *T*[2] directly, without enumerating the set of pairs of allowable values for (*T*[1], *T*[2]). Special solution algorithms (which we do not discuss here) exist for **linear constraints** on integer variables—that is, constraints, such as the one just given, in which each variable appears only in linear form. It can be shown that no algorithm exists for solving general **nonlinear constraints** on integer variables.

* * *

INFINITE

* * *

* * *

CONSTRAINT LANGUAGE

* * *

* * *

LINEAR CONSTRAINTS

* * *

* * *

NONLINEAR CONSTRAINTS

* * *

Constraint satisfaction problems with **continuous domains** are common in the real world and are widely studied in the field of operations research. For example, the scheduling of experiments on the Hubble Space Telescope requires very precise timing of observations; the start and finish of each observation and maneuver are continuous-valued variables that must obey a variety of astronomical, precedence, and power constraints. The best-known category of continuous-domain CSPs is that of **linear programming** problems, where constraints must be linear equalities or inequalities. Linear programming problems can be solved in time polynomial in the number of variables. Problems with different types of constraints and objective functions have also been studied—quadratic programming, second-order conic programming, and so on.

* * *

CONTINUOUS DOMAINS

* * *

In addition to examining the types of variables that can appear in CSPs, it is useful to look at the types of constraints. The simplest type is the **unary constraint**, which restricts the value of a single variable. For example, in the map-coloring problem it could be the case that South Australians won’t tolerate the color green; we can express that with the unary constraint 〈(*SA*), *SA* ≠ green〉

* * *

UNARY CONSTRAINT

* * *

A **binary constraint** relates two variables. For example, *SA* ≠ *NSW* is a binary constraint. A binary CSP is one with only binary constraints; it can be represented as a constraint graph, as in [Figure 6.1](#index_split_013.html#filepos821837)(b).

* * *

BINARY CONSTRAINT

* * *

We can also describe higher-order constraints, such as asserting that the value of *Y* is between *X* and *Z*, with the ternary constraint *Between*(*X*, *Y*, *Z*).

A constraint involving an arbitrary number of variables is called a **global constraint**. (The name is traditional but confusing because it need not involve *all* the variables in a problem). One of the most common global constraints is *Alldiff*, which says that all of the variables involved in the constraint must have different values. In Sudoku problems (see [Section 6.2.6](#index_split_000.html#filepos857810)), all variables in a row or column must satisfy an *Alldiff* constraint. An other example is provided by **cryptarithmetic** puzzles. (See [Figure 6.2](#index_split_013.html#filepos834934)(a).) Each letter in a cryptarithmetic puzzle represents a different digit. For the case in [Figure 6.2](#index_split_013.html#filepos834934)(a), this would be represented as the global constraint *Alldiff* (*F*, *T*, *U*, *W*, *R*, *O*). The addition constraints on the four columns of the puzzle can be written as the following *n*\-ary constraints:

> ![equ](images/00148.jpg)

* * *

GLOBAL CONSTRAINT

* * *

* * *

CRYPTARITHMETIC

* * *

where *C*[10], *C*[100], and *C*[1000] are auxiliary variables representing the digit carried over into the tens, hundreds, or thousands column. These constraints can be represented in a **constraint hypergraph**, such as the one shown in Figure 6.2(b). A hypergraph consists of ordinary nodes (the circles in the figure) and hypernodes (the squares), which represent n-ary constraints.

* * *

CONSTRAINT HYPERGRAPH

* * *

* * *

DUAL GRAPH

* * *

Alternatively, as Exercise 6.6 asks you to prove, every finite-domain constraint can be reduced to a set of binary constraints if enough auxiliary variables are introduced, so we could transform any CSP into one with only binary constraints; this makes the algorithms simpler. Another way to convert an *n*\-ary CSP to a binary one is the **dual graph** transformation: create a new graph in which there will be one variable for each constraint in the original graph, and one binary constraint for each pair of constraints in the original graph that share variables. For example, if the original graph has variables {*X*, *Y*, *Z*} and constraints 〈(*X*, *Y*, *Z*), *C*[1]〉 and 〈(*X*, *Y*), *C*[2]〉 then the dual graph would have variables {*C*[1], *C*[2]} with the binary constraint 〈(*X*, *Y*), *R*[1]〉, where (*X*, *Y*) are the shared variables and *R*[1] is a new relation that defines the constraint between the shared variables, as specified by the original *C*[1] and *C*[2].

> ![image](images/00149.jpg)

> **Figure 6.2** (a) A cryptarithmetic problem. Each letter stands for a distinct digit; the aim is to find a substitution of digits for letters such that the resulting sum is arithmetically correct, with the added restriction that no leading zeroes are allowed. (b) The constraint hypergraph for the cryptarithmetic problem, showing the *Alldiff* constraint (square box at the top) as well as the column addition constraints (four square boxes in the middle). The variables *C*[1], *C*[2], and *C*[3] represent the carry digits for the three columns.

There are however two reasons why we might prefer a global constraint such as *Alldiff* rather than a set of binary constraints. First, it is easier and less error-prone to write the problem description using *Alldiff*. Second, it is possible to design special-purpose inference algorithms for global constraints that are not available for a set of more primitive constraints. We describe these inference algorithms in [Section 6.2.5](#index_split_000.html#filepos852424).

The constraints we have described so far have all been absolute constraints, violation of which rules out a potential solution. Many real-world CSPs include **preference constraints** indicating which solutions are preferred. For example, in a university class-scheduling problem there are absolute constraints that no professor can teach two classes at the same time. But we also may allow preference constraints: Prof. R might prefer teaching in the morning, whereas Prof. N prefers teaching in the afternoon. A schedule that has Prof. R teaching at 2 p.m. would still be an allowable solution (unless Prof. R happens to be the department chair) but would not be an optimal one. Preference constraints can often be encoded as costs on individual variable assignments—for example, assigning an afternoon slot for Prof. R costs 2 points against the overall objective function, whereas a morning slot costs 1. With this formulation, CSPs with preferences can be solved with optimization search methods, either path-based or local. We call such a problem a **constraint optimization problem**, or COP. Linear programming problems do this kind of optimization.

* * *

PREFERENCE CONSTRAINTS

* * *

* * *

CONSTRAINT OPTIMIZATION PROBLEM

* * *

### 6.2 CONSTRAINT PROPAGATION: INFERENCE IN CSPS

In regular state-space search, an algorithm can do only one thing: search. In CSPs there is a choice: an algorithm can search (choose a new variable assignment from several possibilities) or do a specific type of **inference** called **constraint propagation**: using the constraints to reduce the number of legal values for a variable, which in turn can reduce the legal values for another variable, and so on. Constraint propagation may be intertwined with search, or it may be done as a preprocessing step, before search starts. Sometimes this preprocessing can solve the whole problem, so no search is required at all.

* * *

INFERENCE

* * *

* * *

CONSTRAINT PROPAGATION

* * *

The key idea is **local consistency**. If we treat each variable as a node in a graph (see [Figure 6.1](#index_split_013.html#filepos821837)(b)) and each binary constraint as an arc, then the process of enforcing local consistency in each part of the graph causes inconsistent values to be eliminated throughout the graph. There are different types of local consistency, which we now cover in turn.

* * *

LOCAL CONSISTENCY

* * *

#### **6.2.1 Node consistency**

A single variable (corresponding to a node in the CSP network) is **node-consistent** if all the values in the variable’s domain satisfy the variable’s unary constraints. For example, in the variant of the Australia map-coloring problem ([Figure 6.1](#index_split_013.html#filepos821837)) where South Australians dislike green, the variable *SA* starts with domain {*red*, *green*, *blue*}, and we can make it node consistent by eliminating green, leaving *SA* with the reduced domain {*red*, *blue*}. We say that a network is node-consistent if every variable in the network is node-consistent.

* * *

NODE CONSISTENCY

* * *

It is always possible to eliminate all the unary constraints in a CSP by running node consistency. It is also possible to transform all *n*\-ary constraints into binary ones (see Exercise 6.6). Because of this, it is common to define CSP solvers that work with only binary constraints; we make that assumption for the rest of this chapter, except where noted.

#### **6.2.2 Arc consistency**

A variable in a CSP is **arc-consistent** if every value in its domain satisfies the variable’s binary constraints. More formally, *X[i]* is arc-consistent with respect to another variable *X[j]* if for every value in the current domain *D[i]* there is some value in the domain *D[j]* that satisfies the binary constraint on the arc (*X[i]*, *X[j]*). A network is arc-consistent if every variable is arc consistent with every other variable. For example, consider the constraint *Y* = *X²* where the domain of both *X* and *Y* is the set of digits. We can write this constraint explicitly as

> ![equ](images/00150.jpg)

* * *

ARC CONSISTENCY

* * *

To make *X* arc-consistent with respect to *Y*, we reduce *X*’s domain to {0, 1, 2, 3}. If we also make *y* arc-consistent with respect to *X*, then *Y*’s domain becomes {0, 1, 4, 9} and the whole CSP is arc-consistent.

On the other hand, arc consistency can do nothing for the Australia map-coloring problem. Consider the following inequality constraint on (*SA*, *WA*):

> ![equ](images/00151.jpg)

> ![image](images/00152.jpg)

> **Figure 6.3** The arc-consistency algorithm AC-3. After applying AC-3, either every arc is arc-consistent, or some variable has an empty domain, indicating that the CSP cannot be solved. The name “AC-3” was used by the algorithm’s inventor (Mackworth, 1977) because it’s the third version developed in the paper.

No matter what value you choose for *SA* (or for *WA*), there is a valid value for the other variable. So applying arc consistency has no effect on the domains of either variable.

The most popular algorithm for arc consistency is called AC-3 (see [Figure 6.3](#index_split_013.html#filepos842548)). To make every variable arc-consistent, the AC-3 algorithm maintains a queue of arcs to consider. (Actually, the order of consideration is not important, so the data structure is really a set, but tradition calls it a queue.) Initially, the queue contains all the arcs in the CSP. AC-3 then pops off an arbitrary arc (*X*[*i*], *X*[*j*]) from the queue and makes *X*[*i*] arc-consistent with respect to *X[j]*. If this leaves *D[i]* unchanged, the algorithm just moves on to the next arc. But if this revises *D[i]* (makes the domain smaller), then we add to the queue all arcs (*X[k]*, *X[i]*) where *X[k]* is a neighbor of *X[i]*. We need to do that because the change in *D[i]* might enable further reductions in the domains of *D[k]*, even if we have previously considered *X[k]*. If *D[i]* is revised down to nothing, then we know the whole CSP has no consistent solution, and AC-3 can immediately return failure. Otherwise, we keep checking, trying to remove values from the domains of variables until no more arcs are in the queue. At that point, we are left with a CSP that is equivalent to the original CSP—they both have the same solutions—but the arc-consistent CSP will in most cases be faster to search because its variables have smaller domains.

The complexity of AC-3 can be analyzed as follows. Assume a CSP with *n* variables, each with domain size at most *d*, and with *c* binary constraints (arcs). Each arc (*X[k]*, *X[i]*) can be inserted in the queue only *d* times because *X[i]* has at most *d* values to delete. Checking consistency of an arc can be done in *O*(*d*²) time, so we get *O*(*cd*³) total worst-case time.[¹](#index_split_015.html#filepos5579133)

It is possible to extend the notion of arc consistency to handle *n*\-ary rather than just binary constraints; this is called generalized arc consistency or sometimes hyperarc consistency, depending on the author. A variable *X[i]* is **generalized arc consistent** with respect to an *n*\-ary constraint if for every value *v* in the domain of *X[i]* there exists a tuple of values that is a member of the constraint, has all its values taken from the domains of the corresponding variables, and has its *X[i]* component equal to *v*. For example, if all variables have the domain {0, 1, 2, 3}, then to make the variable *X* consistent with the constraint *X* < *Y* < *Z*, we would have to eliminate 2 and 3 from the domain of *X* because the constraint cannot be satisfied when *X* is 2 or 3.

* * *

GENERALIZED ARC CONSISTENT

* * *

#### **6.2.3 Path consistency**

Arc consistency can go a long way toward reducing the domains of variables, sometimes finding a solution (by reducing every domain to size 1) and sometimes finding that the CSP cannot be solved (by reducing some domain to size 0). But for other networks, arc consistency fails to make enough inferences. Consider the map-coloring problem on Australia, but with only two colors allowed, red and blue. Arc consistency can do nothing because every variable is already arc consistent: each can be red with blue at the other end of the arc (or vice versa). But clearly there is no solution to the problem: because Western Australia, Northern Territory and South Australia all touch each other, we need at least three colors for them alone.

Arc consistency tightens down the domains (unary constraints) using the arcs (binary constraints). To make progress on problems like map coloring, we need a stronger notion of consistency. **Path consistency** tightens the binary constraints by using implicit constraints that are inferred by looking at triples of variables.

* * *

PATH CONSISTENCY

* * *

A two-variable set {*X[i]*, *X[j]*} is path-consistent with respect to a third variable *X[m]* if, for every assignment {*X[i]* = *a*, *X[j]* = *b*} consistent with the constraints on {*X[i]*, *X[j]*}, there is an assignment to *X[m]* that satisfies the constraints on {*X[i]*, *X[m]*} and {*X[m]*, *X[j]*}. This is called path consistency because one can think of it as looking at a path from *X[i]* to *X[j]* with *X[m]* in the middle.

Let’s see how path consistency fares in coloring the Australia map with two colors. We will make the set {*WA*, *SA*} path consistent with respect to *NT*. We start by enumerating the consistent assignments to the set. In this case, there are only two: {*WA* = *red*, *SA* = *blue*} and {*WA* = *blue*, *SA* = *red*}. We can see that with both of these assignments *NT* can be neither *red* nor *blue* (because it would conflict with either *WA* or *SA*). Because there is no valid choice for *NT*, we eliminate both assignments, and we end up with no valid assignments for {*WA*, *SA*}. Therefore, we know that there can be no solution to this problem. The PC-2 algorithm (Mackworth, 1977) achieves path consistency in much the same way that AC-3 achieves arc consistency. Because it is so similar, we do not show it here.

#### **6.2.4** *K***\-consistency**

Stronger forms of propagation can be defined with the notion of *k***\-consistency**. A CSP is *k*\-consistent if, for any set of *k* − 1 variables and for any consistent assignment to those variables, a consistent value can always be assigned to any *k*th variable. 1-consistency says that, given the empty set, we can make any set of one variable consistent: this is what we called node consistency. 2-consistency is the same as arc consistency. For binary constraint networks, 3-consistency is the same as path consistency.

* * *

K-CONSISTENCY

* * *

A CSP is **strongly** *k***\-consistent** if it is *k*\-consistent and is also (*k* − 1)-consistent, (*k* − 2)-consistent, … all the way down to 1-consistent. Now suppose we have a CSP with n nodes and make it strongly *n*\-consistent (i.e., strongly *k*\-consistent for *k* = *n*). We can then solve the problem as follows: First, we choose a consistent value for *X*[1]. We are then guaranteed to be able to choose a value for *X*[2] because the graph is 2-consistent, for *X*[3] because it is 3-consistent, and so on. For each variable *X[i]*, we need only search through the d values in the domain to find a value consistent with *X*[1], …, *X*[*i*−1]. We are guaranteed to find a solution in time *O*(*n*²*d*). Of course, there is no free lunch: any algorithm for establishing *n*\-consistency must take time exponential in *n* in the worst case. Worse, *n*\-consistency also requires space that is exponential in *n*. The memory issue is even more severe than the time. In practice, determining the appropriate level of consistency checking is mostly an empirical science. It can be said practitioners commonly compute 2-consistency and less commonly 3-consistency.

* * *

STRONGLY

* * *

* * *

K-CONSISTENT

* * *

#### **6.2.5 Global constraints**

Remember that a **global constraint** is one involving an arbitrary number of variables (but not necessarily all variables). Global constraints occur frequently in real problems and can be handled by special-purpose algorithms that are more efficient than the general-purpose methods described so far. For example, the *Alldiff* constraint says that all the variables involved must have distinct values (as in the cryptarithmetic problem above and Sudoku puzzles below). One simple form of inconsistency detection for *Alldiff* constraints works as follows: if *m* variables are involved in the constraint, and if they have *n* possible distinct values altogether, and *m* > *n*, then the constraint cannot be satisfied.

This leads to the following simple algorithm: First, remove any variable in the constraint that has a singleton domain, and delete that variable’s value from the domains of the remaining variables. Repeat as long as there are singleton variables. If at any point an empty domain is produced or there are more variables than domain values left, then an inconsistency has been detected.

This method can detect the inconsistency in the assignment {*WA* = *red*, *NSW* = *red*} for [Figure 6.1](#index_split_013.html#filepos821837). Notice that the variables *SA*, *NT*, and *Q* are effectively connected by an *Alldiff* constraint because each pair must have two different colors. After applying AC-3 with the partial assignment, the domain of each variable is reduced to {*green*, *blue*}. That is, we have three variables and only two colors, so the *Alldiff* constraint is violated. Thus, a simple consistency procedure for a higher-order constraint is sometimes more effective than applying arc consistency to an equivalent set of binary constraints. There are more complex inference algorithms for *Alldiff* (see van Hoeve and Katriel, 2006) that propagate more constraints but are more computationally expensive to run.

Another important higher-order constraint is the **resource constraint**, sometimes called the atmost constraint. For example, in a scheduling problem, let *P*[1], …, *P*[4] denote the numbers of personnel assigned to each of four tasks. The constraint that no more than 10 personnel are assigned in total is written as *Atmost*(10, *P*[1], *P*[2], *P*[3], *P*[4]). We can detect an inconsistency simply by checking the sum of the minimum values of the current domains; for example, if each variable has the domain {3, 4, 5, 6}, the Atmost constraint cannot be satisfied. We can also enforce consistency by deleting the maximum value of any domain if it is not consistent with the minimum values of the other domains. Thus, if each variable in our example has the domain {2, 3, 4, 5, 6}, the values 5 and 6 can be deleted from each domain.

* * *

RESOURCE CONSTRAINT

* * *

For large resource-limited problems with integer values—such as logistical problems involving moving thousands of people in hundreds of vehicles—it is usually not possible to represent the domain of each variable as a large set of integers and gradually reduce that set by consistency-checking methods. Instead, domains are represented by upper and lower bounds and are managed by **bounds propagation**. For example, in an airline-scheduling problem, let’s suppose there are two flights, *F*[1] and *F*[2], for which the planes have capacities 165 and 385, respectively. The initial domains for the numbers of passengers on each flight are then

> ![equ](images/00153.jpg)

* * *

BOUNDS PROPAGATION

* * *

Now suppose we have the additional constraint that the two flights together must carry 420 people: *F*[1] + *F*[2] = 420. Propagating bounds constraints, we reduce the domains to

> ![equ](images/00154.jpg)

We say that a CSP is **bounds consistent** if for every variable *X*, and for both the lower-bound and upper-bound values of *X*, there exists some value of *Y* that satisfies the constraint between *X* and *Y* for every variable *Y*. This kind of bounds propagation is widely used in practical constraint problems.

* * *

BOUNDS CONSISTENT

* * *

#### **6.2.6 Sudoku example**

The popular **Sudoku** puzzle has introduced millions of people to constraint satisfaction problems, although they may not recognize it. A Sudoku board consists of 81 squares, some of which are initially filled with digits from 1 to 9. The puzzle is to fill in all the remaining squares such that no digit appears twice in any row, column, or 3 × 3 box (see [Figure 6.4](#index_split_013.html#filepos859366)). A row, column, or box is called a **unit**.

* * *

SUDOKU

* * *

The Sudoku puzzles that are printed in newspapers and puzzle books have the property that there is exactly one solution. Although some can be tricky to solve by hand, taking tens of minutes, even the hardest Sudoku problems yield to a CSP solver in less than 0.1 second.

A Sudoku puzzle can be considered a CSP with 81 variables, one for each square. We use the variable names *A1* through *A9* for the top row (left to right), down to *I1* through *I9* for the bottom row. The empty squares have the domain {1, 2, 3, 4, 5, 6, 7, 8, 9} and the prefilled squares have a domain consisting of a single value. In addition, there are 27 different

> ![image](images/00155.jpg)

> **Figure 6.4** (a) A Sudoku puzzle and (b) its solution.

*Alldiff* constraints: one for each row, column, and box of 9 squares.

> ![equ](images/00156.jpg)

Let us see how far arc consistency can take us. Assume that the *Alldiff* constraints have been expanded into binary constraints (such as *A1* ≠ *A2* ) so that we can apply the AC-3 algorithm directly. Consider variable *E6* from [Figure 6.4](#index_split_013.html#filepos859366)(a)—the empty square between the 2 and the 8 in the middle box. From the constraints in the box, we can remove not only 2 and 8 but also 1 and 7 from *E6*’s domain. From the constraints in its column, we can eliminate 5, 6, 2, 8, 9, and 3. That leaves *E6* with a domain of {4}; in other words, we know the answer for *E6*. Now consider variable *I6* —the square in the bottom middle box surrounded by 1, 3, and 3. Applying arc consistency in its column, we eliminate 5, 6, 2, 4 (since we now know *E6* must be 4), 8, 9, and 3. We eliminate 1 by arc consistency with *I5*, and we are left with only the value 7 in the domain of *I6*. Now there are 8 known values in column 6, so arc consistency can infer that *A6* must be 1. Inference continues along these lines, and eventually, AC-3 can solve the entire puzzle—all the variables have their domains reduced to a single value, as shown in [Figure 6.4](#index_split_013.html#filepos859366)(b).

Of course, Sudoku would soon lose its appeal if every puzzle could be solved by a mechanical application of AC-3, and indeed AC-3 works only for the easiest Sudoku puzzles. Slightly harder ones can be solved by PC-2, but at a greater computational cost: there are 255,960 different path constraints to consider in a Sudoku puzzle. To solve the hardest puzzles and to make efficient progress, we will have to be more clever.

Indeed, the appeal of Sudoku puzzles for the human solver is the need to be resourceful in applying more complex inference strategies. Aficionados give them colorful names, such as “naked triples.” That strategy works as follows: in any unit (row, column or box), find three squares that each have a domain that contains the same three numbers or a subset of those numbers. For example, the three domains might be {1, 8}, {3, 8}, and {1, 3, 8}. From that we don’t know which square contains 1, 3, or 8, but we do know that the three numbers must be distributed among the three squares. Therefore we can remove 1, 3, and 8 from the domains of every *other* square in the unit.

It is interesting to note how far we can go without saying much that is specific to Sudoku. We do of course have to say that there are 81 variables, that their domains are the digits 1 to 9, and that there are 27 *Alldiff* constraints. But beyond that, all the strategies—arc consistency, path consistency, etc.—apply generally to all CSPs, not just to Sudoku problems. Even naked triples is really a strategy for enforcing consistency of *Alldiff* constraints and has nothing to do with Sudoku *per se*. This is the power of the CSP formalism: for each new problem area, we only need to define the problem in terms of constraints; then the general constraint-solving mechanisms can take over.

### 6.3 BACKTRACKING SEARCH FOR CSPS

Sudoku problems are designed to be solved by inference over constraints. But many other CSPs cannot be solved by inference alone; there comes a time when we must search for a solution. In this section we look at backtracking search algorithms that work on partial assignments; in the next section we look at local search algorithms over complete assignments.

We could apply a standard depth-limited search (from [Chapter 3](#index_split_000.html#filepos301685)). A state would be a partial assignment, and an action would be adding *var = value* to the assignment. But for a CSP with *n* variables of domain size *d*, we quickly notice something terrible: the branching factor at the top level is *nd* because any of *d* values can be assigned to any of *n* variables. At the next level, the branching factor is (*n* − 1)*d*, and so on for *n* levels. We generate a tree with *n*! *d^n* leaves, even though there are only *d^n* possible complete assignments!

Our seemingly reasonable but naive formulation ignores crucial property common to all CSPs: **commutativity**. A problem is commutative if the order of application of any given set of actions has no effect on the outcome. CSPs are commutative because when assigning values to variables, we reach the same partial assignment regardless of order. Therefore, we need only consider a *single* variable at each node in the search tree. For example, at the root node of a search tree for coloring the map of Australia, we might make a choice between *SA* = *red*, *SA* = *green*, and *SA* = *blue*, but we would never choose between *SA* = *red* and *WA* = *blue*. With this restriction, the number of leaves is *d^n*, as we would hope.

* * *

COMMUTATIVITY

* * *

> ![image](images/00157.jpg)

> **Figure 6.5** A simple backtracking algorithm for constraint satisfaction problems. The algorithm is modeled on the recursive depth-first search of [Chapter 3](#index_split_000.html#filepos301685). By varying the functions SELECT\-UNASSIGNED\-VARIABLE and ORDER\-DOMAIN\-VALUES, we can implement the general-purpose heuristics discussed in the text. The function INFERENCE can optionally be used to impose arc-, path-, or *k*\-consistency, as desired. If a value choice leads to failure (noticed either by INFERENCE or by BACKTRACK), then value assignments (including those made by INFERENCE) are removed from the current assignment and a new value is tried.

The term **backtracking search** is used for a depth-first search that chooses values for one variable at a time and backtracks when a variable has no legal values left to assign. The algorithm is shown in Figure 6.5. It repeatedly chooses an unassigned variable, and then tries all values in the domain of that variable in turn, trying to find a solution. If an inconsistency is detected, then BACKTRACK returns failure, causing the previous call to try another value. Part of the search tree for the Australia problem is shown in [Figure 6.6](#index_split_013.html#filepos868820), where we have assigned variables in the order *WA*, *NT*, *Q*, …. Because the representation of CSPs is standardized, there is no need to supply BACKTRACKING\-SEARCH with a domain-specific initial state, action function, transition model, or goal test.

* * *

BACKTRACKING SEARCH

* * *

Notice that BACKTRACKING\-SEARCH keeps only a single representation of a state and alters that representation rather than creating new ones, as described [on page 87](#index_split_010.html#filepos385788).

In [Chapter 3](#index_split_000.html#filepos301685) we improved the poor performance of uninformed search algorithms by supplying them with domain-specific heuristic functions derived from our knowledge of the problem. It turns out that we can solve CSPs efficiently *without* such domain-specific knowledge. Instead, we can add some sophistication to the unspecified functions in [Figure 6.5](#index_split_013.html#filepos865613), using them to address the following questions:

> 1\. Which variable should be assigned next (SELECT\-UNASSIGNED\-VARIABLE), and in what order should its values be tried (ORDER\-DOMAIN\-VALUES)?

> ![image](images/00158.jpg)

> **Figure 6.6** Part of the search tree for the map-coloring problem in [Figure 6.1](#index_split_013.html#filepos821837).

> 2\. What inferences should be performed at each step in the search (INFERENCE)?

> 3\. When the search arrives at an assignment that violates a constraint, can the search avoid repeating this failure?

The subsections that follow answer each of these questions in turn.

#### **6.3.1 Variable and value ordering**

The backtracking algorithm contains the line

> *var* ← SELECT\-UNASSIGNED\-VARIABLE(*csp*).

The simplest strategy for SELECT\-UNASSIGNED\-VARIABLE is to choose the next unassigned variable in order, {*X*[1], *X*[2], …}. This static variable ordering seldom results in the most efficient search. For example, after the assignments for *WA* = *red* and *NT* = *green* in [Figure 6.6](#index_split_013.html#filepos868820), there is only one possible value for *SA*, so it makes sense to assign *SA* = *blue* next rather than assigning *Q*. In fact, after *SA* is assigned, the choices for *Q*, *NSW*, and *V* are all forced. This intuitive idea—choosing the variable with the fewest “legal” values—is called the **minimum-remaining-values** (MRV) heuristic. It also has been called the “most constrained variable” or “fail-first” heuristic, the latter because it picks a variable that is most likely to cause a failure soon, thereby pruning the search tree. If some variable *X* has no legal values left, the MRV heuristic will select *X* and failure will be detected immediately—avoiding pointless searches through other variables. The MRV heuristic usually performs better than a random or static ordering, sometimes by a factor of 1,000 or more, although the results vary widely depending on the problem.

* * *

MINIMUM-REMAINING-VALUES

* * *

The MRV heuristic doesn’t help at all in choosing the first region to color in Australia, because initially every region has three legal colors. In this case, the **degree heuristic** comes in handy. It attempts to reduce the branching factor on future choices by selecting the variable that is involved in the largest number of constraints on other unassigned variables. In [Figure 6.1](#index_split_013.html#filepos821837), *SA* is the variable with highest degree, 5; the other variables have degree 2 or 3, except for *T*, which has degree 0. In fact, once *SA* is chosen, applying the degree heuristic solves the problem without any false steps—you can choose *any* consistent color at each choice point and still arrive at a solution with no backtracking. The minimum-remaining-values heuristic is usually a more powerful guide, but the degree heuristic can be useful as a tiebreaker.

* * *

DEGREE HEURISTIC

* * *

Once a variable has been selected, the algorithm must decide on the order in which to examine its values. For this, the **least-constraining-value** heuristic can be effective in some cases. It prefers the value that rules out the fewest choices for the neighboring variables in the constraint graph. For example, suppose that in [Figure 6.1](#index_split_013.html#filepos821837) we have generated the partial assignment with *WA* = *red* and *NT* = *green* and that our next choice is for *Q*. Blue would be a bad choice because it eliminates the last legal value left for *Q*’s neighbor, *SA*. The least-constraining-value heuristic therefore prefers red to blue. In general, the heuristic is trying to leave the maximum flexibility for subsequent variable assignments. Of course, if we are trying to find all the solutions to a problem, not just the first one, then the ordering does not matter because we have to consider every value anyway. The same holds if there are no solutions to the problem.

* * *

LEAST-CONSTRAINING-VALUE

* * *

Why should variable selection be fail-first, but value selection be fail-last? It turns out that, for a wide variety of problems, a variable ordering that chooses a variable with the minimum number of remaining values helps minimize the number of nodes in the search tree by pruning larger parts of the tree earlier. For value ordering, the trick is that we only need one solution; therefore it makes sense to look for the most likely values first. If we wanted to enumerate all solutions rather than just find one, then value ordering would be irrelevant.

#### **6.3.2 Interleaving search and inference**

So far we have seen how AC-3 and other algorithms can infer reductions in the domain of variables *before* we begin the search. But inference can be even more powerful in the course of a search: every time we make a choice of a value for a variable, we have a brand-new opportunity to infer new domain reductions on the neighboring variables.

One of the simplest forms of inference is called **forward checking**. Whenever a variable *X* is assigned, the forward-checking process establishes arc consistency for it: for each unassigned variable *Y* that is connected to *X* by a constraint, delete from *Y*’s domain any value that is inconsistent with the value chosen for *X*. Because forward checking only does arc consistency inferences, there is no reason to do forward checking if we have already done arc consistency as a preprocessing step.

* * *

FORWARD CHECKING

* * *

[Figure 6.7](#index_split_013.html#filepos877599) shows the progress of backtracking search on the Australia CSP with forward checking. There are two important points to notice about this example. First, notice that after *WA* = *red* and *Q* = *green* are assigned, the domains of *NT* and *SA* are reduced to a single value; we have eliminated branching on these variables altogether by propagating information from *WA* and *Q*. A second point to notice is that after *V* = *blue*, the domain of *SA* is empty. Hence, forward checking has detected that the partial assignment {*WA* = *red*, *Q* = *green*, *V* = *blue*} is inconsistent with the constraints of the problem, and the algorithm will therefore backtrack immediately.

For many problems the search will be more effective if we combine the MRV heuristic with forward checking. Consider [Figure 6.7](#index_split_013.html#filepos877599) after assigning {*WA* = *red*}. Intuitively, it seems that that assignment constrains its neighbors, *NT* and *SA*, so we should handle those variables next, and then all the other variables will fall into place. That’s exactly what happens with MRV: *NT* and *SA* have two values, so one of them is chosen first, then the other, then *Q*, *NSW*, and *V* in order. Finally *T* still has three values, and any one of them works. We can view forward checking as an efficient way to incrementally compute the information that the MRV heuristic needs to do its job.

> ![image](images/00159.jpg)

> **Figure 6.7** The progress of a map-coloring search with forward checking. *WA* = *red* is assigned first; then forward checking deletes red from the domains of the neighboring variables *NT* and *SA*. After *Q* = *green* is assigned, green is deleted from the domains of *NT*, *SA*, and *NSW*. After *V* = *blue* is assigned, *blue* is deleted from the domains of *NSW* and *SA*, leaving *SA* with no legal values.

Although forward checking detects many inconsistencies, it does not detect all of them. The problem is that it makes the current variable arc-consistent, but doesn’t look ahead and make all the other variables arc-consistent. For example, consider the third row of [Figure 6.7](#index_split_013.html#filepos877599). It shows that when *WA* is *red* and *Q* is *green*, both *NT* and *SA* are forced to be blue. Forward checking does not look far enough ahead to notice that this is an inconsistency: *NT* and *SA* are adjacent and so cannot have the same value.

The algorithm called MAC (for **Maintaining Arc Consistency (MAC)**) detects this inconsistency. After a variable *X[i]* is assigned a value, the INFERENCE procedure calls AC-3, but instead of a queue of all arcs in the CSP, we start with only the arcs (*X[j]*, *X[i]*) for all *X[j]* that are unassigned variables that are neighbors of *X[i]*. From there, AC-3 does constraint propagation in the usual way, and if any variable has its domain reduced to the empty set, the call to AC-3 fails and we know to backtrack immediately. We can see that MAC is strictly more powerful than forward checking because forward checking does the same thing as MAC on the initial arcs in MAC’s queue; but unlike MAC, forward checking does not recursively propagate constraints when changes are made to the domains of variables.

* * *

MAINTAINING ARC CONSISTENCY (MAC)

* * *

#### **6.3.3 Intelligent backtracking: Looking backward**

The BACKTRACKING\-SEARCH algorithm in [Figure 6.5](#index_split_013.html#filepos865613) has a very simple policy for what to do when a branch of the search fails: back up to the preceding variable and try a different value for it. This is called **chronological backtracking** because the *most recent* decision point is revisited. In this subsection, we consider better possibilities.

* * *

CHRONOLOGICAL BACKTRACKING

* * *

Consider what happens when we apply simple backtracking in [Figure 6.1](#index_split_013.html#filepos821837) with a fixed variable ordering *Q*, *NSW*, *V*, *T*, *SA*, *WA*, *NT*. Suppose we have generated the partial assignment {*Q* = *red*, *NSW* = *green*, *V* = *blue*, *T* = *red*}. When we try the next variable, *SA*, we see that every value violates a constraint. We back up to *T* and try a new color for Tasmania! Obviously this is silly—recoloring Tasmania cannot possibly resolve the problem with South Australia.

A more intelligent approach to backtracking is to backtrack to a variable that might fix the problem—a variable that was responsible for making one of the possible values of *SA* impossible. To do this, we will keep track of a set of assignments that are in conflict with some value for *SA*. The set (in this case {*Q* = *red*, *NSW* = *green*, *V* = *blue*,}), is called the **conflict set** for *SA*. The **backjumping** method backtracks to the *most recent* assignment in the conflict set; in this case, backjumping would jump over Tasmania and try a new value for *V*. This method is easily implemented by a modification to BACKTRACK such that it accumulates the conflict set while checking for a legal value to assign. If no legal value is found, the algorithm should return the most recent element of the conflict set along with the failure indicator.

* * *

CONFLICT SET

* * *

* * *

BACKJUMPING

* * *

The sharp-eyed reader will have noticed that forward checking can supply the conflict set with no extra work: whenever forward checking based on an assignment *X* = *x* deletes a value from *Y*’s domain, it should add *X* = *x* to *Y*’s conflict set. If the last value is deleted from *Y*’s domain, then the assignments in the conflict set of *Y* are added to the conflict set of *X*. Then, when we get to *Y*, we know immediately where to backtrack if needed.

The eagle-eyed reader will have noticed something odd: backjumping occurs when every value in a domain is in conflict with the current assignment; but forward checking detects this event and prevents the search from ever reaching such a node! In fact, it can be shown that *every* branch pruned by backjumping is also pruned by forward checking. Hence, simple backjumping is redundant in a forward-checking search or, indeed, in a search that uses stronger consistency checking, such as MAC.

Despite the observations of the preceding paragraph, the idea behind backjumping remains a good one: to backtrack based on the reasons for failure. Backjumping notices failure when a variable’s domain becomes empty, but in many cases a branch is doomed long before this occurs. Consider again the partial assignment {*WA* = *red*, *NSW* = *red*} (which, from our earlier discussion, is inconsistent). Suppose we try *T* = *red* next and then assign *NT*, *Q*, *V*, *SA*. We know that no assignment can work for these last four variables, so eventually we run out of values to try at *NT*. Now, the question is, where to backtrack? Backjumping cannot work, because *NT* *does* have values consistent with the preceding assigned variables—*NT* doesn’t have a complete conflict set of preceding variables that caused it to fail. We know, however, that the four variables *NT*, *Q*, *V*, and *SA*, *taken together*, failed because of a set of preceding variables, which must be those variables that directly conflict with the four. This leads to a deeper notion of the conflict set for a variable such as *NT*: it is that set of preceding variables that caused *NT*, *together with any subsequent variables*, to have no consistent solution. In this case, the set is *WA* and *NSW*, so the algorithm should backtrack to *NSW* and skip over Tasmania. A backjumping algorithm that uses conflict sets defined in this way is called **conflict-directed backjumping**.

* * *

CONFLICT-DIRECTED BACKJUMPING

* * *

We must now explain how these new conflict sets are computed. The method is in fact quite simple. The “terminal” failure of a branch of the search always occurs because a variable’s domain becomes empty; that variable has a standard conflict set. In our example, SA fails, and its conflict set is (say) {*WA*, *NT*, *Q*}. We backjump to *Q*, and *Q* *absorbs* the conflict set from *SA* (minus *Q* itself, of course) into its own direct conflict set, which is {*NT*, *NSW*}; the new conflict set is {*WA*, *NT*, *NSW*}. That is, there is no solution from *Q* onward, given the preceding assignment to {*WA*, *NT*, *NSW*}. Therefore, we backtrack to *NT*, the most recent of these. *NT* absorbs {*WA*, *NT*, *NSW*} − {*NT*} into its own direct conflict set {*WA*}, giving {*WA*, *NSW*} (as stated in the previous paragraph). Now the algorithm backjumps to *NSW*, as we would hope. To summarize: let *X[j]* be the current variable, and let conf (*X[j]*) be its conflict set. If every possible value for *X[j]* fails, backjump to the most recent variable *X[i]* in conf (*X[j]*), and set

> ![equ](images/00160.jpg)

When we reach a contradiction, backjumping can tell us how far to back up, so we don’t waste time changing variables that won’t fix the problem. But we would also like to avoid running into the same problem again. When the search arrives at a contradiction, we know that some subset of the conflict set is responsible for the problem. **Constraint learning** is the idea of finding a minimum set of variables from the conflict set that causes the problem. This set of variables, along with their corresponding values, is called a **no-good**. We then record the no-good, either by adding a new constraint to the CSP or by keeping a separate cache of no-goods.

* * *

CONSTRAINT LEARNING

* * *

* * *

NO-GOOD

* * *

For example, consider the state {*WA* = *red*, *NT* = *green*, *Q* = *blue*} in the bottom row of [Figure 6.6](#index_split_013.html#filepos868820). Forward checking can tell us this state is a no-good because there is no valid assignment to *SA*. In this particular case, recording the no-good would not help, because once we prune this branch from the search tree, we will never encounter this combination again. But suppose that the search tree in [Figure 6.6](#index_split_013.html#filepos868820) were actually part of a larger search tree that started by first assigning values for *V* and *T*. Then it would be worthwhile to record {*WA* = *red*, *NT* = *green*, *Q* = *blue*} as a no-good because we are going to run into the same problem again for each possible set of assignments to *V* and *T*.

No-goods can be effectively used by forward checking or by backjumping. Constraint learning is one of the most important techniques used by modern CSP solvers to achieve efficiency on complex problems.

### 6.4 LOCAL SEARCH FOR CSPS

Local search algorithms (see [Section 4.1](#index_split_000.html#filepos515228)) turn out to be effective in solving many CSPs. They use a complete-state formulation: the initial state assigns a value to every variable, and the search changes the value of one variable at a time. For example, in the 8-queens problem (see [Figure 4.3](#index_split_011.html#filepos524086)), the initial state might be a random configuration of 8 queens in 8 columns, and each step moves a single queen to a new position in its column. Typically, the initial guess violates several constraints. The point of local search is to eliminate the violated constraints.[²](#index_split_015.html#filepos5579426)

In choosing a new value for a variable, the most obvious heuristic is to select the value that results in the minimum number of conflicts with other variables—the **minconflicts** heuristic. The algorithm is shown in Figure 6.8 and its application to an 8-queens problem is diagrammed in [Figure 6.9](#index_split_013.html#filepos891463).

> ![image](images/00161.jpg)

> **Figure 6.8** The MIN\-CONFLICTS algorithm for solving CSPs by local search. The initial state may be chosen randomly or by a greedy assignment process that chooses a minimal-conflict value for each variable in turn. The CONFLICTS function counts the number of constraints violated by a particular value, given the rest of the current assignment.

* * *

MINCONFLICTS

* * *

> ![image](images/00162.jpg)

> **Figure 6.9** A two-step solution using minconflicts for an 8-queens problem. At each stage, a queen is chosen for reassignment in its column. The number of conflicts (in this case, the number of attacking queens) is shown in each square. The algorithm moves the queen to the minconflicts square, breaking ties randomly.

Minconflicts is surprisingly effective for many CSPs. Amazingly, on the n-queens problem, if you don’t count the initial placement of queens, the run time of minconflicts is roughly *independent of problem size*. It solves even the *million*\-queens problem in an average of 50 steps (after the initial assignment). This remarkable observation was the stimulus leading to a great deal of research in the 1990s on local search and the distinction between easy and hard problems, which we take up in [Chapter 7](#index_split_000.html#filepos939379). Roughly speaking, *n*\-queens is easy for local search because solutions are densely distributed throughout the state space. Minconflicts also works well for hard problems. For example, it has been used to schedule observations for the Hubble Space Telescope, reducing the time taken to schedule a week of observations from three weeks (!) to around 10 minutes.

All the local search techniques from [Section 4.1](#index_split_000.html#filepos515228) are candidates for application to CSPs, and some of those have proved especially effective. The landscape of a CSP under the minconflicts heuristic usually has a series of plateaux. There may be millions of variable assignments that are only one conflict away from a solution. Plateau search—allowing sideways moves to another state with the same score—can help local search find its way off this plateau. This wandering on the plateau can be directed with **tabu search**: keeping a small list of recently visited states and forbidding the algorithm to return to those states. Simulated annealing can also be used to escape from plateaux.

Another technique, called **constraint weighting**, can help concentrate the search on the important constraints. Each constraint is given a numeric weight, *W[i]*, initially all 1. At each step of the search, the algorithm chooses a variable/value pair to change that will result in the lowest total weight of all violated constraints. The weights are then adjusted by incrementing the weight of each constraint that is violated by the current assignment. This has two benefits: it adds topography to plateaux, making sure that it is possible to improve from the current state, and it also, over time, adds weight to the constraints that are proving difficult to solve.

* * *

CONSTRAINT WEIGHTING

* * *

Another advantage of local search is that it can be used in an online setting when the problem changes. This is particularly important in scheduling problems. A week’s airline schedule may involve thousands of flights and tens of thousands of personnel assignments, but bad weather at one airport can render the schedule infeasible. We would like to repair the schedule with a minimum number of changes. This can be easily done with a local search algorithm starting from the current schedule. A backtracking search with the new set of constraints usually requires much more time and might find a solution with many changes from the current schedule.

### 6.5 THE STRUCTURE OF PROBLEMS

In this section, we examine ways in which the *structure* of the problem, as represented by the constraint graph, can be used to find solutions quickly. Most of the approaches here also apply to other problems besides CSPs, such as probabilistic reasoning. After all, the only way we can possibly hope to deal with the real world is to decompose it into many subproblems. Looking again at the constraint graph for Australia ([Figure 6.1](#index_split_013.html#filepos821837)(b), repeated as [Figure 6.12](#index_split_013.html#filepos901836)(a)), one fact stands out: Tasmania is not connected to the mainland.[³](#index_split_015.html#filepos5579739) Intuitively, it is obvious that coloring Tasmania and coloring the mainland are **independent subproblems**—any solution for the mainland combined with any solution for Tasmania yields a solution for the whole map. Independence can be ascertained simply by finding **connected components** of the constraint graph. Each component corresponds to a subproblem *CSP[i]*. If assignment *S[i]* is a solution of *CSP[i]*, then ![image](images/00163.jpg)is a solution of ![image](images/00164.jpg). Why is this important? Consider the following: suppose each *CSP[i]* has *c* variables from the total of *n* variables, where *c* is a constant. Then there are *n*/*c* subproblems, each of which takes at most *d^c* work to solve, where *d* is the size of the domain. Hence, the total work is *O*(*d^cn/c*), which is *linear* in *n*; without the decomposition, the total work is *O*(*d^n*), which is exponential in *n*. Let’s make this more concrete: dividing a Boolean CSP with 80 variables into four subproblems reduces the worst-case solution time from the lifetime of the universe down to less than a second.

* * *

INDEPENDENT SUBPROBLEMS

* * *

* * *

CONNECTED COMPONENT

* * *

Completely independent subproblems are delicious, then, but rare. Fortunately, some other graph structures are also easy to solve. For example, a constraint graph is a **tree** when any two variables are connected by only one path. We show that *any tree-structured CSP can be solved in time linear in the number of variables.*[⁴](#index_split_015.html#filepos5580054) The key is a new notion of consistency, called **directed arc consistency** or DAC. A CSP is defined to be directed arc-consistent under an ordering of variables *X*[1], *X*[2], …, *X[n]* if and only if every *X[i]* is arc-consistent with each *X[j]* for *j* > *i*.

* * *

DIRECTED ARC CONSISTENCY

* * *

![hand](images/00006.jpg)

To solve a tree-structured CSP, first pick any variable to be the root of the tree, and choose an ordering of the variables such that each variable appears after its parent in the tree. Such an ordering is called a **topological sort**. [Figure 6.10](#index_split_013.html#filepos900054)(a) shows a sample tree and (b) shows one possible ordering. Any tree with n nodes has *n* − 1 arcs, so we can make this graph directed arc-consistent in *O*(*n*) steps, each of which must compare up to *d* possible domain values for two variables, for a total time of *O*(*nd*²). Once we have a directed arc-consistent graph, we can just march down the list of variables and choose any remaining value. Since each link from a parent to its child is arc consistent, we know that for any value we choose for the parent, there will be a valid value left to choose for the child. That means we won’t have to backtrack; we can move linearly through the variables. The complete algorithm is shown in [Figure 6.11](#index_split_013.html#filepos901400).

* * *

TOPOLOGICAL SORT

* * *

> ![image](images/00165.jpg)

> **Figure 6.10** (a) The constraint graph of a tree-structured CSP. (b) A linear ordering of the variables consistent with the tree with *A* as the root. This is known as a **topological sort** of the variables.

Now that we have an efficient algorithm for trees, we can consider whether more general constraint graphs can be *reduced* to trees somehow. There are two primary ways to do this, one based on removing nodes and one based on collapsing nodes together.

The first approach involves assigning values to some variables so that the remaining variables form a tree. Consider the constraint graph for Australia, shown again in [Figure 6.12](#index_split_013.html#filepos901836)(a). If we could delete South Australia, the graph would become a tree, as in (b). Fortunately, we can do this (in the graph, not the continent) by fixing a value for *SA* and deleting from the domains of the other variables any values that are inconsistent with the value chosen for *SA*.

> ![image](images/00166.jpg)

> **Figure 6.11** The TREE\-CSP-SOLVER algorithm for solving tree-structured CSPs. If the CSP has a solution, we will find it in linear time; if not, we will detect a contradiction.

> ![image](images/00167.jpg)

> **Figure 6.12** (a) The original constraint graph from [Figure 6.1](#index_split_013.html#filepos821837). (b) The constraint graph after the removal of *SA*.

Now, any solution for the CSP after *SA* and its constraints are removed will be consistent with the value chosen for *SA*. (This works for binary CSPs; the situation is more complicated with higher-order constraints.) Therefore, we can solve the remaining tree with the algorithm given above and thus solve the whole problem. Of course, in the general case (as opposed to map coloring), the value chosen for *SA* could be the wrong one, so we would need to try each possible value. The general algorithm is as follows:

> 1\. Choose a subset *S* of the CSP’s variables such that the constraint graph becomes a tree after removal of *S*. *S* is called a **cycle cutset**.

* * *

CYCLE CUTSET

* * *

> 2\. For each possible assignment to the variables in *S* that satisfies all constraints on *S*,

> (a) remove from the domains of the remaining variables any values that are inconsistent with the assignment for *S*, and

> (b) If the remaining CSP has a solution, return it together with the assignment for *S*.

If the cycle cutset has size *c*, then the total run time is *O*(*d^c* (*n* − *c*)*d*²): we have to try each of the *d^c* combinations of values for the variables in *S*, and for each combination we must solve a tree problem of size *n* − *c*. If the graph is “nearly a tree,” then *c* will be small and the savings over straight backtracking will be huge. In the worst case, however, *c* can be as large as (*n* − 2). Finding the *smallest* cycle cutset is NP-hard, but several efficient approximation algorithms are known. The overall algorithmic approach is called **cutset conditioning**; it comes up again in [Chapter 14](#index_split_015.html#filepos2036437), where it is used for reasoning about probabilities.

* * *

CUTSET CONDITIONING

* * *

The second approach is based on constructing a **tree decomposition** of the constraint graph into a set of connected subproblems. Each subproblem is solved independently, and the resulting solutions are then combined. Like most divide-and-conquer algorithms, this works well if no subproblem is too large. [Figure 6.13](#index_split_013.html#filepos908792) shows a tree decomposition of the map-coloring problem into five subproblems. A tree decomposition must satisfy the following three requirements:

* * *

TREE DECOMPOSITION

* * *

> • Every variable in the original problem appears in at least one of the subproblems.

> • If two variables are connected by a constraint in the original problem, they must appear together (along with the constraint) in at least one of the subproblems.

> • If a variable appears in two subproblems in the tree, it must appear in every subproblem along the path connecting those subproblems.

The first two conditions ensure that all the variables and constraints are represented in the decomposition. The third condition seems rather technical, but simply reflects the constraint that any given variable must have the same value in every subproblem in which it appears; the links joining subproblems in the tree enforce this constraint. For example, *SA* appears in all four of the connected subproblems in [Figure 6.13](#index_split_013.html#filepos908792). You can verify from [Figure 6.12](#index_split_013.html#filepos901836) that this decomposition makes sense.

We solve each subproblem independently; if any one has no solution, we know the entire problem has no solution. If we can solve all the subproblems, then we attempt to construct a global solution as follows. First, we view each subproblem as a “mega-variable” whose domain is the set of all solutions for the subproblem. For example, the leftmost subproblem in [Figure 6.13](#index_split_013.html#filepos908792) is a map-coloring problem with three variables and hence has six solutions—one is {*WA* = *red*, *SA* = *blue*, *NT* = *green*}. Then, we solve the constraints connecting the subproblems, using the efficient algorithm for trees given earlier. The constraints between subproblems simply insist that the subproblem solutions agree on their shared variables. For example, given the solution {*WA* = *red*, *SA* = *blue*, *NT* = *green*} for the first subproblem, the only consistent solution for the next subproblem is {*SA* = *blue*, *NT* = *green*, *Q* = *red*}.

* * *

TREE WIDTH

* * *

A given constraint graph admits many tree decompositions; in choosing a decomposition, the aim is to make the subproblems as small as possible. The **tree width** of a tree decomposition of a graph is one less than the size of the largest subproblem; the tree width of the graph itself is defined to be the minimum tree width among all its tree decompositions. If a graph has tree width w and we are given the corresponding tree decomposition, then the problem can be solved in *O*(*nd*^(*w*+1)) time. Hence, *CSPs with constraint graphs of bounded tree width are solvable in polynomial time.* Unfortunately, finding the decomposition with minimal tree width is NP-hard, but there are heuristic methods that work well in practice.

> ![image](images/00168.jpg)

> **Figure 6.13** A tree decomposition of the constraint graph in [Figure 6.12](#index_split_013.html#filepos901836)(a).

![hand](images/00006.jpg)

So far, we have looked at the structure of the constraint graph. There can be important structure in the *values* of variables as well. Consider the map-coloring problem with *n* colors. For every consistent solution, there is actually a set of *n*! solutions formed by permuting the color names. For example, on the Australia map we know that *WA*, *NT*, and *SA* must all have different colors, but there are 3! = 6 ways to assign the three colors to these three regions. This is called **value symmetry**. We would like to reduce the search space by a factor of *n*! by breaking the symmetry. We do this by introducing a **symmetry-breaking constraint**. For our example, we might impose an arbitrary ordering constraint, *NT* < *SA* < *WA*, that requires the three values to be in alphabetical order. This constraint ensures that only one of the *n*! solutions is possible: {*NT* = *blue*, *SA* = *green*, *WA* = *red*}.

* * *

VALUE SYMMETRY

* * *

* * *

SYMMETRY-BREAKING CONSTRAINT

* * *

For map coloring, it was easy to find a constraint that eliminates the symmetry, and in general it is possible to find constraints that eliminate all but one symmetric solution in polynomial time, but it is NP-hard to eliminate all symmetry among intermediate sets of values during search. In practice, breaking value symmetry has proved to be important and effective on a wide range of problems.

### 6.6 SUMMARY

> • **Constraint satisfaction problems** (CSPs) represent a state with a set of variable/value pairs and represent the conditions for a solution by a set of constraints on the variables. Many important real-world problems can be described as CSPs.

> • A number of inference techniques use the constraints to infer which variable/value pairs are consistent and which are not. These include node, arc, path, and *k*\-consistency.

> • **Backtracking search**, a form of depth-first search, is commonly used for solving CSPs. Inference can be interwoven with search.

> • The **minimum-remaining-values** and **degree** heuristics are domain-independent methods for deciding which variable to choose next in a backtracking search. The **least-constraining-value** heuristic helps in deciding which value to try first for a given variable. Backtracking occurs when no legal assignment can be found for a variable. **Conflict-directed backjumping** backtracks directly to the source of the problem.

> • Local search using the **minconflicts** heuristic has also been applied to constraint satisfaction problems with great success.

> • The complexity of solving a CSP is strongly related to the structure of its constraint graph. Tree-structured problems can be solved in linear time. **Cutset conditioning** can reduce a general CSP to a tree-structured one and is quite efficient if a small cutset can be found. **Tree decomposition** techniques transform the CSP into a tree of subproblems and are efficient if the **tree width** of the constraint graph is small.

### BIBLIOGRAPHICAL AND HISTORICAL NOTES

The earliest work related to constraint satisfaction dealt largely with numerical constraints. Equational constraints with integer domains were studied by the Indian mathematician Brahmagupta in the seventh century; they are often called **Diophantine equations**, after the Greek mathematician Diophantus (c. 200–284), who actually considered the domain of positive rationals. Systematic methods for solving linear equations by variable elimination were studied by Gauss (1829); the solution of linear inequality constraints goes back to Fourier (1827).

* * *

DIOPHANTINE EQUATIONS

* * *

Finite-domain constraint satisfaction problems also have a long history. For example, **graph coloring** (of which map coloring is a special case) is an old problem in mathematics. The four-color conjecture (that every planar graph can be colored with four or fewer colors) was first made by Francis Guthrie, a student of De Morgan, in 1852. It resisted solution—despite several published claims to the contrary—until a proof was devised by Appel and Haken (1977) (see the book *Four Colors Suffice* (Wilson, 2004)). Purists were disappointed that part of the proof relied on a computer, so Georges Gonthier (2008), using the COQ theorem prover, derived a formal proof that Appel and Haken’s proof was correct.

* * *

GRAPH COLORING

* * *

Specific classes of constraint satisfaction problems occur throughout the history of computer science. One of the most influential early examples was the SKETCHPAD system (Sutherland, 1963), which solved geometric constraints in diagrams and was the forerunner of modern drawing programs and CAD tools. The identification of CSPs as a *general* class is due to Ugo Montanari (1974). The reduction of higher-order CSPs to purely binary CSPs with auxiliary variables (see Exercise 6.6) is due originally to the 19th-century logician Charles Sanders Peirce. It was introduced into the CSP literature by Dechter (1990b) and was elaborated by Bacchus and van Beek (1998). CSPs with preferences among solutions are studied widely in the optimization literature; see Bistarelli **et al.** (1997) for a generalization of the CSP framework to allow for preferences. The bucket-elimination algorithm (Dechter, 1999) can also be applied to optimization problems.

Constraint propagation methods were popularized by Waltz’s (1975) success on polyhedral line-labeling problems for computer vision. Waltz showed that, in many problems, propagation completely eliminates the need for backtracking. Montanari (1974) introduced the notion of constraint networks and propagation by path consistency. Alan Mackworth (1977) proposed the AC-3 algorithm for enforcing arc consistency as well as the general idea of combining backtracking with some degree of consistency enforcement. AC-4, a more efficient arc-consistency algorithm, was developed by Mohr and Henderson (1986). Soon after Mackworth’s paper appeared, researchers began experimenting with the tradeoff between the cost of consistency enforcement and the benefits in terms of search reduction. Haralick and Elliot (1980) favored the minimal forward-checking algorithm described by McGregor (1979), whereas Gaschnig (1979) suggested full arc-consistency checking after each variable assignment—an algorithm later called MAC by Sabin and Freuder (1994). The latter paper provides somewhat convincing evidence that, on harder CSPs, full arc-consistency checking pays off. Freuder (1978, 1982) investigated the notion of *k*\-consistency and its relationship to the complexity of solving CSPs. Apt (1999) describes a generic algorithmic framework within which consistency propagation algorithms can be analyzed, and Bessière (2006) presents a current survey.

Special methods for handling higher-order or global constraints were developed first within the context of **constraint logic programming**. Marriott and Stuckey (1998) provide excellent coverage of research in this area. The *Alldiff* constraint was studied by Regin (1994), Stergiou and Walsh (1999), and van Hoeve (2001). Bounds constraints were incorporated into constraint logic programming by Van Hentenryck **et al.** (1998). A survey of global constraints is provided by van Hoeve and Katriel (2006).

Sudoku has become the most widely known CSP and was described as such by Simonis (2005). Agerbeck and Hansen (2008) describe some of the strategies and show that Sudoku on an *n*² × *n*² board is in the class of *NP*\-hard problems. Reeson **et al.** (2007) show an interactive solver based on CSP techniques.

The idea of backtracking search goes back to Golomb and Baumert (1965), and its application to constraint satisfaction is due to Bitner and Reingold (1975), although they trace the basic algorithm back to the 19th century. Bitner and Reingold also introduced the MRV heuristic, which they called the *most-constrained-variable* heuristic. Brelaz (1979) used the degree heuristic as a tiebreaker after applying the MRV heuristic. The resulting algorithm, despite its simplicity, is still the best method for *k*\-coloring arbitrary graphs. Haralick and Elliot (1980) proposed the least-constraining-value heuristic.

The basic backjumping method is due to John Gaschnig (1977, 1979). Kondrak and van Beek (1997) showed that this algorithm is essentially subsumed by forward checking. Conflict-directed backjumping was devised by Prosser (1993). The most general and powerful form of intelligent backtracking was actually developed very early on by Stallman and Sussman (1977). Their technique of **dependency-directed backtracking** led to the development of **truth maintenance systems** (Doyle, 1979), which we discuss in [Section 12.6.2](#index_split_015.html#filepos1838642). The connection between the two areas is analyzed by de Kleer (1989).

* * *

DEPENDENCY-DIRECTED BACKTRACKING

* * *

The work of Stallman and Sussman also introduced the idea of **constraint learning**, in which partial results obtained by search can be saved and reused later in the search. The idea was formalized Dechter (1990a). **Backmarking** (Gaschnig, 1979) is a particularly simple method in which consistent and inconsistent pairwise assignments are saved and used to avoid rechecking constraints. Backmarking can be combined with conflict-directed backjumping; Kondrak and van Beek (1997) present a hybrid algorithm that provably subsumes either method taken separately. The method of **dynamic backtracking** (Ginsberg, 1993) retains successful partial assignments from later subsets of variables when backtracking over an earlier choice that does not invalidate the later success.

* * *

BACKMARKING

* * *

* * *

DYNAMIC BACKTRACKING

* * *

Empirical studies of several randomized backtracking methods were done by Gomes **et al.** (2000) and Gomes and Selman (2001). Van Beek (2006) surveys backtracking.

Local search in constraint satisfaction problems was popularized by the work of Kirkpatrick **et al.** (1983) on simulated annealing (see [Chapter 4](#index_split_000.html#filepos513290)), which is widely used for scheduling problems. The minconflicts heuristic was first proposed by Gu (1989) and was developed independently by Minton **et al.** (1992). Sosic and Gu (1994) showed how it could be applied to solve the 3,000,000 queens problem in less than a minute. The astounding success of local search using minconflicts on the *n*\-queens problem led to a reappraisal of the nature and prevalence of “easy” and “hard” problems. Peter Cheeseman **et al.** (1991) explored the difficulty of randomly generated CSPs and discovered that almost all such problems either are trivially easy or have no solutions. Only if the parameters of the problem generator are set in a certain narrow range, within which roughly half of the problems are solvable, do we find “hard” problem instances. We discuss this phenomenon further in [Chapter 7](#index_split_000.html#filepos939379). Konolige (1994) showed that local search is inferior to backtracking search on problems with a certain degree of local structure; this led to work that combined local search and inference, such as that by Pinkas and Dechter (1995). Hoos and Tsang (2006) survey local search techniques.

Work relating the structure and complexity of CSPs originates with Freuder (1985), who showed that search on arc consistent trees works without any backtracking. A similar result, with extensions to acyclic hypergraphs, was developed in the database community (Beeri **et al.**, 1983). Bayardo and Miranker (1994) present an algorithm for tree-structured CSPs that runs in linear time without any preprocessing.

Since those papers were published, there has been a great deal of progress in developing more general results relating the complexity of solving a CSP to the structure of its constraint graph. The notion of tree width was introduced by the graph theorists Robertson and Seymour (1986). Dechter and Pearl (1987, 1989), building on the work of Freuder, applied a related notion (which they called **induced width**) to constraint satisfaction problems and developed the tree decomposition approach sketched in [Section 6.5](#index_split_000.html#filepos895328). Drawing on this work and on results from database theory, Gottlob **et al.** (1999a, 1999b) developed a notion, **hypertree width**, that is based on the characterization of the CSP as a hypergraph. In addition to showing that any CSP with hypertree width w can be solved in time *O*(*n*^(*w*+1) log *n*), they also showed that hypertree width subsumes all previously defined measures of “width” in the sense that there are cases where the hypertree width is bounded and the other measures are unbounded.

Interest in look-back approaches to backtracking was rekindled by the work of Bayardo and Schrag (1997), whose RELSAT algorithm combined constraint learning and backjumping and was shown to outperform many other algorithms of the time. This led to AND/OR search algorithms applicable to both CSPs and probabilistic reasoning (Dechter and Mateescu, 2007). Brown **et al.** (1988) introduce the idea of symmetry breaking in CSPs, and Gent **et al.** (2006) give a recent survey.

The field of **distributed constraint satisfaction** looks at solving CSPs when there is a collection of agents, each of which controls a subset of the constraint variables. There have been annual workshops on this problem since 2000, and good coverage elsewhere (Collin **et al.**, 1999; Pearce **et al.**, 2008; Shoham and Leyton-Brown, 2009).

* * *

DISTRIBUTED CONSTRAINT SATISFACTION

* * *

Comparing CSP algorithms is mostly an empirical science: few theoretical results show that one algorithm dominates another on all problems; instead, we need to run experiments to see which algorithms perform better on typical instances of problems. As Hooker (1995) points out, we need to be careful to distinguish between competitive testing—as occurs in competitions among algorithms based on run time—and scientific testing, whose goal is to identify the properties of an algorithm that determine its efficacy on a class of problems.

The recent textbooks by Apt (2003) and Dechter (2003), and the collection by Rossi *et al.* (2006) are excellent resources on constraint processing. There are several good earlier surveys, including those by Kumar (1992), Dechter and Frost (2002), and Bartak (2001); and the encyclopedia articles by Dechter (1992) and Mackworth (1992). Pearson and Jeavons (1997) survey tractable classes of CSPs, covering both structural decomposition methods and methods that rely on properties of the domains or constraints themselves. Kondrak and van Beek (1997) give an analytical survey of backtracking search algorithms, and Bacchus and van Run (1995) give a more empirical survey. Constraint programming is covered in the books by Apt (2003) and Fruhwirth and Abdennadher (2003). Several interesting applications are described in the collection edited by Freuder and Mackworth (1994). Papers on constraint satisfaction appear regularly in *Artificial Intelligence* and in the specialist journal *Constraints*. The primary conference venue is the International Conference on Principles and Practice of Constraint Programming, often called *CP*.

### EXERCISES

**6.1** How many solutions are there for the map-coloring problem in [Figure 6.1](#index_split_013.html#filepos821837)? How many solutions if four colors are allowed? Two colors?

**6.2** Consider the problem of placing *k* knights on an *n* × *n* chessboard such that no two knights are attacking each other, where *k* is given and *k* ≤ *n*².

> **a.** Choose a CSP formulation. In your formulation, what are the variables?

> **b.** What are the possible values of each variable?

> **c.** What sets of variables are constrained, and how?

> **d.** Now consider the problem of putting *as many knights as possible* on the board without any attacks. Explain how to solve this with local search by defining appropriate ACTIONS and RESULT functions and a sensible objective function.

**6.3** Consider the problem of constructing (not solving) crossword puzzles:[⁵](#index_split_015.html#filepos5580256) fitting words into a rectangular grid. The grid, which is given as part of the problem, specifies which squares are blank and which are shaded. Assume that a list of words (i.e., a dictionary) is provided and that the task is to fill in the blank squares by using any subset of the list. Formulate this problem precisely in two ways:

> **a.** As a general search problem. Choose an appropriate search algorithm and specify a heuristic function. Is it better to fill in blanks one letter at a time or one word at a time?

> **b.** As a constraint satisfaction problem. Should the variables be words or letters?

Which formulation do you think will be better? Why?

**6.4** Give precise formulations for each of the following as constraint satisfaction problems:

> **a.** Rectilinear floor-planning: find non-overlapping places in a large rectangle for a number of smaller rectangles.

> **b.** Class scheduling: There is a fixed number of professors and classrooms, a list of classes to be offered, and a list of possible time slots for classes. Each professor has a set of classes that he or she can teach.

> **c.** Hamiltonian tour: given a network of cities connected by roads, choose an order to visit all cities in a country without repeating any.

**6.5** Solve the cryptarithmetic problem in [Figure 6.2](#index_split_013.html#filepos834934) by hand, using the strategy of backtracking with forward checking and the MRV and least-constraining-value heuristics.

**6.6** Show how a single ternary constraint such as “*A* + *B* = *C*” can be turned into three binary constraints by using an auxiliary variable. You may assume finite domains. (*Hint*: Consider a new variable that takes on values that are pairs of other values, and consider constraints such as “*X* is the first element of the pair *Y*.”) Next, show how constraints with more than three variables can be treated similarly. Finally, show how unary constraints can be eliminated by altering the domains of variables. This completes the demonstration that any CSP can be transformed into a CSP with only binary constraints.

**6.7** Consider the following logic puzzle: In five houses, each with a different color, live five persons of different nationalities, each of whom prefers a different brand of candy, a different drink, and a different pet. Given the following facts, the questions to answer are “Where does the zebra live, and in which house do they drink water?”

> The Englishman lives in the red house.

> The Spaniard owns the dog.

> The Norwegian lives in the first house on the left.

> The green house is immediately to the right of the ivory house.

> The man who eats Hershey bars lives in the house next to the man with the fox.

> Kit Kats are eaten in the yellow house.

> The Norwegian lives next to the blue house.

> The Smarties eater owns snails.

> The Snickers eater drinks orange juice.

> The Ukrainian drinks tea.

> The Japanese eats Milky Ways.

> Kit Kats are eaten in a house next to the house where the horse is kept.

> Coffee is drunk in the green house.

> Milk is drunk in the middle house.

Discuss different representations of this problem as a CSP. Why would one prefer one representation over another?

**6.8** Consider the graph with 8 nodes *A*[1], *A*[2], *A*[3], *A*[4], *H*, *T*, *F*[1], *F*[2]. *A[i]* is connected to *A*[*i*+1] for all *i*, each *A[i]* is connected to *H*, *H* is connected to *T*, and *T* is connected to each *F[i]*. Find a 3-coloring of this graph by hand using the following strategy: backtracking with conflict-directed backjumping, the variable order *A*[1], *H*, *A*[4], *F*[1], *A*[2], *F*[2], *A*[3], *T*, and the value order *R*, *G*, *B*.

**6.9** Explain why it is a good heuristic to choose the variable that is most constrained but the value that is least constraining in a CSP search.

**6.10** Generate random instances of map-coloring problems as follows: scatter *n* points on the unit square; select a point *X* at random, connect *X* by a straight line to the nearest point *Y* such that *X* is not already connected to *Y* and the line crosses no other line; repeat the previous step until no more connections are possible. The points represent regions on the map and the lines connect neighbors. Now try to find *k*\-colorings of each map, for both *k* = 3 and *k* = 4, using minconflicts, backtracking, backtracking with forward checking, and backtracking with MAC. Construct a table of average run times for each algorithm for values of *n* up to the largest you can manage. Comment on your results.

![radio](images/00004.jpg)

**6.11** Use the AC-3 algorithm to show that arc consistency can detect the inconsistency of the partial assignment {*WA* = *green*, *V* = *red*} for the problem shown in [Figure 6.1](#index_split_013.html#filepos821837).

**6.12** What is the worst-case complexity of running AC-3 on a tree-structured CSP?

**6.13** AC-3 puts back on the queue *every* arc (*X[k]*, *X[i]*) whenever *any* value is deleted from the domain of *X[i]*, even if each value of *X[k]* is consistent with several remaining values of *X[i]*. Suppose that, for every arc (*X[k]*, *X[i]*), we keep track of the number of remaining values of *X[i]* that are consistent with each value of *X[k]*. Explain how to update these numbers efficiently and hence show that arc consistency can be enforced in total time *O*(*n*²*d*²).

**6.14** The TREE\-CSP-SOLVER ([Figure 6.10](#index_split_013.html#filepos900054)) makes arcs consistent starting at the leaves and working backwards towards the root. Why does it do that? What would happen if it went in the opposite direction?

**6.15** We introduced Sudoku as a CSP to be solved by search over partial assignments because that is the way people generally undertake solving Sudoku problems. It is also possible, of course, to attack these problems with local search over complete assignments. How well would a local solver using the minconflicts heuristic do on Sudoku problems?

**6.16** Define in your own words the terms constraint, backtracking search, arc consistency, backjumping, minconflicts, and cycle cutset.

![radio](images/00004.jpg)

**6.17** Suppose that a graph is known to have a cycle cutset of no more than *k* nodes. Describe a simple algorithm for finding a minimal cycle cutset whose run time is not much more than *O*(*n^k*) for a CSP with *n* variables. Search the literature for methods for finding approximately minimal cycle cutsets in time that is polynomial in the size of the cutset. Does the existence of such algorithms make the cycle cutset method practical?

## **7 LOGICAL AGENTS**

> *In which we design agents that can form representations of a complex world, use a process of inference to derive new representations about the world, and use these new representations to deduce what to do.*

Humans, it seems, know things; and what they know helps them do things. These are not empty statements. They make strong claims about how the intelligence of humans is achieved—not by purely reflex mechanisms but by processes of **reasoning** that operate on internal **representations** of knowledge. In AI, this approach to intelligence is embodied in **knowledge-based agents**.

* * *

REASONING

* * *

* * *

REPRESENTATION

* * *

* * *

KNOWLEDGE-BASED AGENTS

* * *

The problem-solving agents of [Chapters 3](#index_split_000.html#filepos301685) and [4](#index_split_000.html#filepos513290) know things, but only in a very limited, inflexible sense. For example, the transition model for the 8-puzzle—knowledge of what the actions do—is hidden inside the domain-specific code of the RESULT function. It can be used to predict the outcome of actions but not to deduce that two tiles cannot occupy the same space or that states with odd parity cannot be reached from states with even parity. The atomic representations used by problem-solving agents are also very limiting. In a partially observable environment, an agent’s only choice for representing what it knows about the current state is to list all possible concrete states—a hopeless prospect in large environments.

[Chapter 6](#index_split_000.html#filepos813005) introduced the idea of representing states as assignments of values to variables; this is a step in the right direction, enabling some parts of the agent to work in a domain-independent way and allowing for more efficient algorithms. In this chapter and those that follow, we take this step to its logical conclusion, so to speak—we develop **logic** as a general class of representations to support knowledge-based agents. Such agents can combine and recombine information to suit myriad purposes. Often, this process can be quite far removed from the needs of the moment—as when a mathematician proves a theorem or an astronomer calculates the earth’s life expectancy. Knowledge-based agents can accept new tasks in the form of explicitly described goals; they can achieve competence quickly by being told or learning new knowledge about the environment; and they can adapt to changes in the environment by updating the relevant knowledge.

* * *

LOGIC

* * *

We begin in [Section 7.1](#index_split_000.html#filepos943668) with the overall agent design. [Section 7.2](#index_split_000.html#filepos950662) introduces a simple new environment, the wumpus world, and illustrates the operation of a knowledge-based agent without going into any technical detail. Then we explain the general principles of **logic** in [Section 7.3](#index_split_000.html#filepos961559) and the specifics of **propositional logic** in [Section 7.4](#index_split_000.html#filepos975576). While less expressive than **first-order logic** ([Chapter 8](#index_split_000.html#filepos1149778)), propositional logic illustrates all the basic concepts of logic; it also comes with well-developed inference technologies, which we describe in sections [7.5](#index_split_000.html#filepos997899) and [7.6](#index_split_000.html#filepos1045666). Finally, [Section 7.7](#index_split_000.html#filepos1065123) combines the concept of knowledge-based agents with the technology of propositional logic to build some simple agents for the wumpus world.

### 7.1 KNOWLEDGE\-BASED AGENTS

The central component of a knowledge-based agent is its **knowledge base**, or KB. A knowledge base is a set of **sentences**. (Here “sentence” is used as a technical term. It is related but not identical to the sentences of English and other natural languages.) Each sentence is expressed in a language called a **knowledge representation language** and represents some assertion about the world. Sometimes we dignify a sentence with the name **axiom**, when the sentence is taken as given without being derived from other sentences.

* * *

KNOWLEDGE BASE

* * *

* * *

SENTENCE

* * *

* * *

KNOWLEDGE REPRESENTATION LANGUAGE

* * *

* * *

AXIOM

* * *

There must be a way to add new sentences to the knowledge base and a way to query what is known. The standard names for these operations are TELL and ASK, respectively. Both operations may involve **inference**—that is, deriving new sentences from old. Inference must obey the requirement that when one ASKs a question of the knowledge base, the answer should follow from what has been told (or TELLed) to the knowledge base previously. Later in this chapter, we will be more precise about the crucial word “follow.” For now, take it to mean that the inference process should not make things up as it goes along.

* * *

INFERENCE

* * *

[Figure 7.1](#index_split_014.html#filepos949029) shows the outline of a knowledge-based agent program. Like all our agents, it takes a percept as input and returns an action. The agent maintains a knowledge base, *KB*, which may initially contain some **background knowledge**.

* * *

BACKGROUND KNOWLEDGE

* * *

Each time the agent program is called, it does three things. First, it TELLS the knowledge base what it perceives. Second, it ASKs the knowledge base what action it should perform. In the process of answering this query, extensive reasoning may be done about the current state of the world, about the outcomes of possible action sequences, and so on. Third, the agent program TELLS the knowledge base which action was chosen, and the agent executes the action.

The details of the representation language are hidden inside three functions that implement the interface between the sensors and actuators on one side and the core representation and reasoning system on the other. MAKE\-PERCEPT\-SENTENCE constructs a sentence asserting that the agent perceived the given percept at the given time. MAKE\-ACTION\-QUERY constructs a sentence that asks what action should be done at the current time. Finally, MAKE\-ACTION\-SENTENCE constructs a sentence asserting that the chosen action was executed. The details of the inference mechanisms are hidden inside TELL and ASK. Later sections will reveal these details.

The agent in [Figure 7.1](#index_split_014.html#filepos949029) appears quite similar to the agents with internal state described in [Chapter 2](#index_split_000.html#filepos187684). Because of the definitions of TELL and ASK, however, the knowledge-based agent is not an arbitrary program for calculating actions. It is amenable to a description at the **knowledge level**, where we need specify only what the agent knows and what its goals are, in order to fix its behavior. For example, an automated taxi might have the goal of taking a passenger from San Francisco to Marin County and might know that the Golden Gate Bridge is the only link between the two locations. Then we can expect it to cross the Golden Gate Bridge *because it knows that that will achieve its goal*. Notice that this analysis is independent of how the taxi works at the **implementation level**. It doesn’t matter whether its geographical knowledge is implemented as linked lists or pixel maps, or whether it reasons by manipulating strings of symbols stored in registers or by propagating noisy signals in a network of neurons.

* * *

KNOWLEDGE LEVEL

* * *

* * *

IMPLEMENTATION LEVEL

* * *

> ![image](images/00169.jpg)

> **Figure 7.1** A generic knowledge-based agent. Given a percept, the agent adds the percept to its knowledge base, asks the knowledge base for the best action, and tells the knowledge base that it has in fact taken that action.

A knowledge-based agent can be built simply by TELLing it what it needs to know. Starting with an empty knowledge base, the agent designer can TELL sentences one by one until the agent knows how to operate in its environment. This is called the **declarative** approach to system building. In contrast, the **procedural** approach encodes desired behaviors directly as program code. In the 1970s and 1980s, advocates of the two approaches engaged in heated debates. We now understand that a successful agent often combines both declarative and procedural elements in its design, and that declarative knowledge can often be compiled into more efficient procedural code.

* * *

DECLARATIVE

* * *

We can also provide a knowledge-based agent with mechanisms that allow it to learn for itself. These mechanisms, which are discussed in [Chapter 18](#index_split_015.html#filepos2753020), create general knowledge about the environment from a series of percepts. A learning agent can be fully autonomous.

### 7.2 THE WUMPUS WORLD

In this section we describe an environment in which knowledge-based agents can show their worth. The **wumpus world** is a cave consisting of rooms connected by passageways. Lurking somewhere in the cave is the terrible wumpus, a beast that eats anyone who enters its room. The wumpus can be shot by an agent, but the agent has only one arrow. Some rooms contain bottomless pits that will trap anyone who wanders into these rooms (except for the wumpus, which is too big to fall in). The only mitigating feature of this bleak environment is the possibility of finding a heap of gold. Although the wumpus world is rather tame by modern computer game standards, it illustrates some important points about intelligence.

* * *

WUMPUS WORLD

* * *

A sample wumpus world is shown in [Figure 7.2](#index_split_014.html#filepos956323). The precise definition of the task environment is given, as suggested in [Section 2.3](#index_split_000.html#filepos209973), by the PEAS description:

> • **Performance measure**: +1000 for climbing out of the cave with the gold, −1000 for falling into a pit or being eaten by the wumpus, −1 for each action taken and −10 for using up the arrow. The game ends either when the agent dies or when the agent climbs out of the cave.

> • **Environment**: A 4 × 4 grid of rooms. The agent always starts in the square labeled \[1,1\], facing to the right. The locations of the gold and the wumpus are chosen randomly, with a uniform distribution, from the squares other than the start square. In addition, each square other than the start can be a pit, with probability 0.2.

> • **Actuators**: The agent can move *Forward*, *TurnLeft* by 90°, or *TurnRight* by 90^°. The agent dies a miserable death if it enters a square containing a pit or a live wumpus. (It is safe, albeit smelly, to enter a square with a dead wumpus.) If an agent tries to move forward and bumps into a wall, then the agent does not move. The action *Grab* can be used to pick up the gold if it is in the same square as the agent. The action *Shoot* can be used to fire an arrow in a straight line in the direction the agent is facing. The arrow continues until it either hits (and hence kills) the wumpus or hits a wall. The agent has only one arrow, so only the first *Shoot* action has any effect. Finally, the action *Climb* can be used to climb out of the cave, but only from square \[1,1\].

> • **Sensors**: The agent has five sensors, each of which gives a single bit of information:

> **–** In the square containing the wumpus and in the directly (not diagonally) adjacent squares, the agent will perceive a *Stench*.

> **–** In the squares directly adjacent to a pit, the agent will perceive a *Breeze*.

> **–** In the square where the gold is, the agent will perceive a *Glitter*.

> **–** When an agent walks into a wall, it will perceive a *Bump*.

> **–** When the wumpus is killed, it emits a woeful *Scream* that can be perceived anywhere in the cave.

> The percepts will be given to the agent program in the form of a list of five symbols; for example, if there is a stench and a breeze, but no glitter, bump, or scream, the agent program will get \[*Stench, Breeze, None, None, None*\].

We can characterize the wumpus environment along the various dimensions given in [Chapter 2](#index_split_000.html#filepos187684). Clearly, it is discrete, static, and single-agent. (The wumpus doesn’t move, fortunately.) It is sequential, because rewards may come only after many actions are taken. It is partially observable, because some aspects of the state are not directly perceivable: the agent’s location, the wumpus’s state of health, and the availability of an arrow. As for the locations of the pits and the wumpus: we could treat them as unobserved parts of the state that happen to be immutable—in which case, the transition model for the environment is completely known; or we could say that the transition model itself is unknown because the agent doesn’t know which *Forward* actions are fatal–in which case, discovering the locations of pits and wumpus completes the agent’s knowledge of the transition model.

> ![image](images/00170.jpg)

> **Figure 7.2** A typical wumpus world. The agent is in the bottom left corner, facing right.

For an agent in the environment, the main challenge is its initial ignorance of the configuration of the environment; overcoming this ignorance seems to require logical reasoning. In most instances of the wumpus world, it is possible for the agent to retrieve the gold safely. Occasionally, the agent must choose between going home empty-handed and risking death to find the gold. About 21% of the environments are utterly unfair, because the gold is in a pit or surrounded by pits.

Let us watch a knowledge-based wumpus agent exploring the environment shown in [Figure 7.2](#index_split_014.html#filepos956323). We use an informal knowledge representation language consisting of writing down symbols in a grid (as in Figures [7.3](#index_split_014.html#filepos959784) and [7.4](#index_split_014.html#filepos960239)).

The agent’s initial knowledge base contains the rules of the environment, as described previously; in particular, it knows that it is in \[1,1\] and that \[1,1\] is a safe square; we denote that with an “A” and “OK,” respectively, in square \[1,1\].

The first percept is \[*None, None, None, None, None*\], from which the agent can conclude that its neighboring squares, \[1,2\] and \[2,1\], are free of dangers—they are OK. [Figure 7.3](#index_split_014.html#filepos959784)(a) shows the agent’s state of knowledge at this point.

A cautious agent will move only into a square that it knows to be OK. Let us suppose the agent decides to move forward to \[2,1\]. The agent perceives a breeze (denoted by “B”) in \[2,1\], so there must be a pit in a neighboring square. The pit cannot be in \[1,1\], by the rules of the game, so there must be a pit in \[2,2\] or \[3,1\] or both. The notation “P?” in [Figure 7.3](#index_split_014.html#filepos959784)(b) indicates a possible pit in those squares. At this point, there is only one known square that is OK and that has not yet been visited. So the prudent agent will turn around, go back to \[1,1\], and then proceed to \[1,2\].

The agent perceives a stench in \[1,2\], resulting in the state of knowledge shown in [Figure 7.4](#index_split_014.html#filepos960239)(a). The stench in \[1,2\] means that there must be a wumpus nearby. But the wumpus cannot be in \[1,1\], by the rules of the game, and it cannot be in \[2,2\] (or the agent would have detected a stench when it was in \[2,1\]). Therefore, the agent can infer that the wumpus is in \[1,3\]. The notation W! indicates this inference. Moreover, the lack of a breeze in \[1,2\] implies that there is no pit in \[2,2\]. Yet the agent has already inferred that there must be a pit in either \[2,2\] or \[3,1\], so this means it must be in \[3,1\]. This is a fairly difficult inference, because it combines knowledge gained at different times in different places and relies on the lack of a percept to make one crucial step.

> ![image](images/00171.jpg)

> **Figure 7.3** The first step taken by the agent in the wumpus world. (a) The initial situation, after percept \[*None, None, None, None, None*\]. (b) After one move, with percept \[*None, Breeze, None, None, None*\].

> ![image](images/00172.jpg)

> **Figure 7.4** Two later stages in the progress of the agent. (a) After the third move, with percept \[*Stench, None, None, None, None*\]. (b) After the fifth move, with percept \[*Stench, Breeze, Glitter, None, None*\].

The agent has now proved to itself that there is neither a pit nor a wumpus in \[2,2\], so it is OK to move there. We do not show the agent’s state of knowledge at \[2,2\]; we just assume that the agent turns and moves to \[2,3\], giving us [Figure 7.4](#index_split_014.html#filepos960239)(b). In \[2,3\], the agent detects a glitter, so it should grab the gold and then return home.

Note that in each case for which the agent draws a conclusion from the available information, that conclusion is *guaranteed* to be correct if the available information is correct. This is a fundamental property of logical reasoning. In the rest of this chapter, we describe how to build logical agents that can represent information and draw conclusions such as those described in the preceding paragraphs.

### 7.3 LOGIC

This section summarizes the fundamental concepts of logical representation and reasoning. These beautiful ideas are independent of any of logic’s particular forms. We therefore postpone the technical details of those forms until the next section, using instead the familiar example of ordinary arithmetic.

In [Section 7.1](#index_split_000.html#filepos943668), we said that knowledge bases consist of sentences. These sentences are expressed according to the **syntax** of the representation language, which specifies all the sentences that are well formed. The notion of syntax is clear enough in ordinary arithmetic: “*x* + *y* = 4” is a well-formed sentence, whereas “*x*4*y*\+ =” is not.

* * *

SYNTAX

* * *

A logic must also define the **semantics** or meaning of sentences. The semantics defines the **truth** of each sentence with respect to each **possible world**. For example, the semantics for arithmetic specifies that the sentence “*x* + *y* = 4” is true in a world where *x* is 2 and *y* is 2, but false in a world where *x* is 1 and *y* is 1. In standard logics, every sentence must be either true or false in each possible world—there is no “in between.”[¹](#index_split_015.html#filepos5580521)

* * *

SEMANTICS

* * *

* * *

TRUTH

* * *

* * *

POSSIBLE WORLD

* * *

When we need to be precise, we use the term **model** in place of “possible world.” Whereas possible worlds might be thought of as (potentially) real environments that the agent might or might not be in, models are mathematical abstractions, each of which simply fixes the truth or falsehood of every relevant sentence. Informally, we may think of a possible world as, for example, having *x* men and *y* women sitting at a table playing bridge, and the sentence *x* + *y* = 4 is true when there are four people in total. Formally, the possible models are just all possible assignments of real numbers to the variables *x* and *y*. Each such assignment fixes the truth of any sentence of arithmetic whose variables are *x* and *y*. If a sentence α is true in model m, we say that *m* **satisfies** α or sometimes *m* **is a model of** α. We use the notation *M*(α) to mean the set of all models of α.

* * *

MODEL

* * *

* * *

SATISFACTION

* * *

* * *

ENTAILMENT

* * *

Now that we have a notion of truth, we are ready to talk about logical reasoning. This involves the relation of logical **entailment** between sentences—the idea that a sentence *follows logically* from another sentence. In mathematical notation, we write

> α ⊨ β

> ![image](images/00173.jpg)

> **Figure 7.5** Possible models for the presence of pits in squares \[1,2\], \[2,2\], and \[3,1\]. The KB corresponding to the observations of nothing in \[1,1\] and a breeze in \[2,1\] is shown by the solid line. (a) Dotted line shows models of α[1] (no pit in \[1,2\]). (b) Dotted line shows models of α[2] (no pit in \[2,2\]).

to mean that the sentence α entails the sentence β. The formal definition of entailment is this: α ⊨ β if and only if, in every model in which α is true, β is also true. Using the notation just introduced, we can write

> α ⊨ β if and only if *M*(α) ⊆ *M*(β).

(Note the direction of the ⊆ here: if α ⊨ β, then α is a *stronger* assertion than β: it rules out *more* possible worlds.) The relation of entailment is familiar from arithmetic; we are happy with the idea that the sentence *x* = 0 entails the sentence *xy* = 0. Obviously, in any model where *x* is zero, it is the case that *xy* is zero (regardless of the value of *y*).

We can apply the same kind of analysis to the wumpus-world reasoning example given in the preceding section. Consider the situation in [Figure 7.3](#index_split_014.html#filepos959784)(b): the agent has detected nothing in \[1,1\] and a breeze in \[2,1\]. These percepts, combined with the agent’s knowledge of the rules of the wumpus world, constitute the KB. The agent is interested (among other things) in whether the adjacent squares \[1,2\], \[2,2\], and \[3,1\] contain pits. Each of the three squares might or might not contain a pit, so (for the purposes of this example) there are 2³ = 8 possible models. These eight models are shown in [Figure 7.5](#index_split_014.html#filepos965424).[²](#index_split_015.html#filepos5580739)

The KB can be thought of as a set of sentences or as a single sentence that asserts all the individual sentences. The KB is false in models that contradict what the agent knows—for example, the KB is false in any model in which \[1,2\] contains a pit, because there is no breeze in \[1,1\]. There are in fact just three models in which the KB is true, and these are shown surrounded by a solid line in [Figure 7.5](#index_split_014.html#filepos965424). Now let us consider two possible conclusions:

> ![image](images/00174.jpg)

We have surrounded the models of α[1] and α[2] with dotted lines in Figures [7.5](#index_split_014.html#filepos965424)(*a*) and [7.5](#index_split_014.html#filepos965424)(*b*), respectively. By inspection, we see the following:

> in every model in which *KB* is true, α[1] is also true.

Hence, *KB* ⊨ α[1]: there is no pit in \[1,2\]. We can also see that

in some models in which *KB* is true, α[2] is false.

Hence, ![image](images/00175.jpg): the agent *cannot* conclude that there is no pit in \[2,2\]. (Nor can it conclude that there *is* a pit in \[2,2\].)[³](#index_split_015.html#filepos5581133)

The preceding example not only illustrates entailment but also shows how the definition of entailment can be applied to derive conclusions—that is, to carry out **logical inference**. The inference algorithm illustrated in [Figure 7.5](#index_split_014.html#filepos965424) is called **model checking**, because it enumerates all possible models to check that α is true in all models in which *KB* is true, that is, that *M*(*KB*) ⊆ *M*(α).

* * *

LOGICAL INFERENCE

* * *

* * *

MODEL CHECKING

* * *

In understanding entailment and inference, it might help to think of the set of all consequences of *KB* as a haystack and of α as a needle. Entailment is like the needle being in the haystack; inference is like finding it. This distinction is embodied in some formal notation: if an inference algorithm i can derive α from *KB*, we write

> ![image](images/00176.jpg)

which is pronounced “α is derived from *KB* by *i* ”or “*i* derives α from *KB*.”

An inference algorithm that derives only entailed sentences is called **sound** or **truth-preserving**. Soundness is a highly desirable property. An unsound inference procedure essentially makes things up as it goes along—it announces the discovery of nonexistent needles. It is easy to see that model checking, when it is applicable,[⁴](#index_split_015.html#filepos5581368) is a sound procedure.

* * *

SOUND

* * *

* * *

TRUTH-PRESERVING

* * *

The property of **completeness** is also desirable: an inference algorithm is complete if it can derive any sentence that is entailed. For real haystacks, which are finite in extent, it seems obvious that a systematic examination can always decide whether the needle is in the haystack. For many knowledge bases, however, the haystack of consequences is infinite, and completeness becomes an important issue.[⁵](#index_split_015.html#filepos5581812) Fortunately, there are complete inference procedures for logics that are sufficiently expressive to handle many knowledge bases.

* * *

COMPLETENESS

* * *

![hand](images/00006.jpg)

We have described a reasoning process whose conclusions are guaranteed to be true in any world in which the premises are true; in particular, *if KB is true in the* real *world, then any sentence α derived from KB by a sound inference procedure is also true in the real world.* So, while an inference process operates on “syntax”—internal physical configurations such as bits in registers or patterns of electrical blips in brains—the process *corresponds* to the real-world relationship whereby some aspect of the real world is the case[⁶](#index_split_015.html#filepos5582050) by virtue of other aspects of the real world being the case. This correspondence between world and representation is illustrated in [Figure 7.6](#index_split_014.html#filepos973343).

> ![image](images/00177.jpg)

> **Figure 7.6** Sentences are physical configurations of the agent, and reasoning is a process of constructing new physical configurations from old ones. Logical reasoning should ensure that the new configurations represent aspects of the world that actually follow from the aspects that the old configurations represent.

The final issue to consider is **grounding**—the connection between logical reasoning processes and the real environment in which the agent exists. In particular, *how do we know that KB is true in the real world?* (After all, *KB* is just “syntax” inside the agent’s head.) This is a philosophical question about which many, many books have been written. (See [Chapter 26](#index_split_015.html#filepos3949421).) A simple answer is that the agent’s sensors create the connection. For example, our wumpus-world agent has a smell sensor. The agent program creates a suitable sentence whenever there is a smell. Then, whenever that sentence is in the knowledge base, it is true in the real world. Thus, the meaning and truth of percept sentences are defined by the processes of sensing and sentence construction that produce them. What about the rest of the agent’s knowledge, such as its belief that wumpuses cause smells in adjacent squares? This is not a direct representation of a single percept, but a general rule—derived, perhaps, from perceptual experience but not identical to a statement of that experience. General rules like this are produced by a sentence construction process called **learning**, which is the subject of Part V. Learning is fallible. It could be the case that wumpuses cause smells *except on February 29 in leap years*, which is when they take their baths. Thus, *KB* may not be true in the real world, but with good learning procedures, there is reason for optimism.

* * *

GROUNDING

* * *

### 7.4 PROPOSITIONAL LOGIC: A VERY SIMPLE LOGIC

We now present a simple but powerful logic called **propositional logic**. We cover the syntax of propositional logic and its semantics—the way in which the truth of sentences is determined. Then we look at **entailment**—the relation between a sentence and another sentence that follows from it—and see how this leads to a simple algorithm for logical inference. Everything takes place, of course, in the wumpus world.

* * *

PROPOSITIONAL LOGIC

* * *

#### **7.4.1 Syntax**

The **syntax** of propositional logic defines the allowable sentences. The **atomic sentences** consist of a single **proposition symbol**. Each such symbol stands for a proposition that can be true or false. We use symbols that start with an uppercase letter and may contain other letters or subscripts, for example: *P*, *Q*, *R*, *W*[1,3] and *North*. The names are arbitrary but are often chosen to have some mnemonic value—we use *W*[1,3] to stand for the proposition that the wumpus is in \[1,3\]. (Remember that symbols such as *W*[1,3] are *atomic*, i.e., *W*, 1, and 3 are not meaningful parts of the symbol.) There are two proposition symbols with fixed meanings: *True* is the always-true proposition and *False* is the always-false proposition. **Complex sentences** are constructed from simpler sentences, using parentheses and **logical connectives**. There are five connectives in common use:

* * *

ATOMIC SENTENCES

* * *

* * *

PROPOSITION SYMBOL

* * *

* * *

COMPLEX SENTENCES

* * *

* * *

LOGICAL CONNECTIVES

* * *

> ¬ (not). A sentence such as ¬*W*[1,3] is called the **negation** of *W*[1,3]. A **literal** is either an atomic sentence (a **positive literal**) or a negated atomic sentence (a **negative literal**).

* * *

NEGATION

* * *

* * *

LITERAL

* * *

> ⋀ (and). A sentence whose main connective is ⋀, such as *W*[1,3] ⋀ *P*[3,1], is called a **conjunction**; its parts are the **conjuncts**. (The ⋀ looks like an “A” for “And.”)

* * *

CONJUNCTION

* * *

> ⋁ (or). A sentence using ⋁,such as (*W*[1,3] ⋀*P*[3,1]) ⋁ *W*[2,2], is a **disjunction** of the **disjuncts** (*W*[1,3] ⋀ *P*[3,1]) and *W*[2,2]. (Historically, the ⋁ comes from the Latin “vel,” which means “or.” For most people, it is easier to remember ⋁ as an upside-down ⋀.)

* * *

DISJUNCTION

* * *

> ⇒ (implies). A sentence such as (*W*[1,3] ⋀ *P*[3,1]) ⇒ ¬*W*[2,2] is called an **implication** (or conditional). Its **premise** or **antecedent** is (*W*[1,3] ⋀ *P*[3,1]), and its **conclusion** or **consequent** is ¬*W*[2,2]. Implications are also known as **rules** or **if–then** statements. The implication symbol is sometimes written in other books as ⊃ or →.

* * *

IMPLICATION

* * *

* * *

PREMISE

* * *

* * *

CONCLUSION

* * *

* * *

RULES

* * *

> ⇔ (if and only if). The sentence *W*[1,3] ⇔ ¬*W*[2,2] is a **biconditional**. Some other books write this as ≡.

* * *

BICONDITIONAL

* * *

> ![image](images/00178.jpg)

> **Figure 7.7** A BNF (Backus–Naur Form) grammar of sentences in propositional logic, along with operator precedences, from highest to lowest.

[Figure 7.7](#index_split_014.html#filepos981136) gives a formal grammar of propositional logic; see [page 1060](#index_split_015.html#filepos4111078) if you are not familiar with the BNF notation. The BNF grammar by itself is ambiguous; a sentence with several operators can be parsed by the grammar in multiple ways. To eliminate the ambiguity we define a precedence for each operator. The “not” operator (¬) has the highest precedence, which means that in the sentence ¬A ⋀ B the ¬binds most tightly, giving us the equivalent of (¬A) ⋀ B rather than ¬(*A* ⋀ *B*). (The notation for ordinary arithmetic is the same: −2+4 is 2, not −6.) When in doubt, use parentheses to make sure of the right interpretation. Square brackets mean the same thing as parentheses; the choice of square brackets or parentheses is solely to make it easier for a human to read a sentence.

#### **7.4.2 Semantics**

Having specified the syntax of propositional logic, we now specify its semantics. The semantics defines the rules for determining the truth of a sentence with respect to a particular model. In propositional logic, a model simply fixes the **truth value**—*true* or *false*—for every proposition symbol. For example, if the sentences in the knowledge base make use of the proposition symbols *P*[1,2], *P*[2,2], and *P*[3,1], then one possible model is

> *m*[1] = {*P*[1,2] = *false*, *P*[2,2] = *false*, *P*[3,1] = *true*}.

* * *

TRUTH VALUE

* * *

With three proposition symbols, there are 2³ = 8 possible models—exactly those depicted in [Figure 7.5](#index_split_014.html#filepos965424). Notice, however, that the models are purely mathematical objects with no necessary connection to wumpus worlds. *P*[1,2] is just a symbol; it might mean “there is a pit in \[1,2\]” or “I’m in Paris today and tomorrow.”

The semantics for propositional logic must specify how to compute the truth value of *any* sentence, given a model. This is done recursively. All sentences are constructed from atomic sentences and the five connectives; therefore, we need to specify how to compute the truth of atomic sentences and how to compute the truth of sentences formed with each of the five connectives. Atomic sentences are easy:

> • *True* is true in every model and *False* is false in every model.

> • The truth value of every other proposition symbol must be specified directly in the model. For example, in the model *m*[1] given earlier, *P*[1,2] is false.

For complex sentences, we have five rules, which hold for any subsentences *P* and *Q* in any model *m* (here “iff” means “if and only if”):

> • ¬*P* is true iff *P* is false in *m*.

> • *P* ⋀ *Q* is true iff both *P* and *Q* are true in *m*.

> • *P* ⋁ *Q* is true iff either *P* or *Q* is true in *m*.

> • *P* ⇒ *Q* is true unless *P* is true and *Q* is false in *m*.

> • *P* ⇔ *Q* is true iff *P* and *Q* are both true or both false in *m*.

* * *

TRUTH TABLE

* * *

The rules can also be expressed with **truth tables** that specify the truth value of a complex sentence for each possible assignment of truth values to its components. Truth tables for the five connectives are given in [Figure 7.8](#index_split_014.html#filepos987107). From these tables, the truth value of any sentence *s* can be computed with respect to any model *m* by a simple recursive evaluation. For example, the sentence ¬*P*[1,2] ⋀ (*P*[2,2] ⋁ *P*[3,1]), evaluated in *m*[1], gives true ⋀ (*false* ⋁ *true*)= *true* ⋀ *true* = *true*. Exercise 7.3 asks you to write the algorithm PL-TRUE?(*s*, *m*), which computes the truth value of a propositional logic sentence *s* in a model *m*.

> ![image](images/00179.jpg)

> **Figure 7.8** Truth tables for the five logical connectives. To use the table to compute, for example, the value of *P* ⋁ *Q* when *P* is true and *Q* is false, first look on the left for the row where *P* is true and *Q* is false (the third row). Then look in that row under the *P*⋁*Q* column to see the result: true.

The truth tables for “and,” “or,” and “not” are in close accord with our intuitions about the English words. The main point of possible confusion is that *P* ⋁ *Q* is true when *P* is true or *Q* is true *or both*. A different connective, called “exclusive or” (“xor” for short), yields false when both disjuncts are true.[⁷](#index_split_015.html#filepos5582277) There is no consensus on the symbol for exclusive or; some choices are ⋁ or ≠ or ⊕.

The truth table for ⇒ may not quite fit one’s intuitive understanding of “*P* implies *Q*” or “if *P* then *Q*.” For one thing, propositional logic does not require any relation of *causation* or *relevance* between *P* and *Q*. The sentence “5 is odd implies Tokyo is the capital of Japan” is a true sentence of propositional logic (under the normal interpretation), even though it is a decidedly odd sentence of English. Another point of confusion is that any implication is true whenever its antecedent is false. For example, “5 is even implies Sam is smart” is true, regardless of whether Sam is smart. This seems bizarre, but it makes sense if you think of “*P* ⇒ *Q*” as saying, “If *P* is true, then I am claiming that *Q* is true. Otherwise I am making no claim.” The only way for this sentence to be *false* is if *P* is true but *Q* is false.

The biconditional, *P* ⇔ *Q*, is true whenever both *P* ⇒ *Q* and Q ⇒ *P* are true. In English, this is often written as “*P* if and only if *Q*.” Many of the rules of the wumpus world are best written using ⇔. For example, a square is breezy *if* a neighboring square has a pit, and a square is breezy *only if* a neighboring square has a pit. So we need a biconditional,

> *B*[1,1] ⇔ (*P*[1,2] ⋁ *P*[2,1]),

where *B*[1,1] means that there is a breeze in \[1,1\].

#### **7.4.3 A simple knowledge base**

Now that we have defined the semantics for propositional logic, we can construct a knowledge base for the wumpus world. We focus first on the *immutable* aspects of the wumpus world, leaving the mutable aspects for a later section. For now, we need the following symbols for each \[*x*, *y*\] location:

> *P*[*x,y*] is true if there is a pit in \[*x, y*\].

> *W[x,y]* is true if there is a wumpus in \[*x, y*\], dead or alive.

> *B*[*x,y*] is true if the agent perceives a breeze in \[*x, y*\].

> *S[x,y]* is true if the agent perceives a stench in \[*x, y*\].

The sentences we write will suffice to derive ¬*P*[1,2] (there is no pit in \[1,2\]), as was done informally in [Section 7.3](#index_split_000.html#filepos961559). We label each sentence *R*[*i*] so that we can refer to them:

> • There is no pit in \[1,1\]:

> *R*[1] : ¬*P*[1,1].

> • A square is breezy if and only if there is a pit in a neighboring square. This has to be stated for each square; for now, we include just the relevant squares:

> *R*[2] : *B*[1,1] ⇔ (*P*[1,2] ⋁ *P*[2,1]).

> *R*[3] : *B*[2,1] ⇔ (*P*[1,1] ⋁ *P*[2,2] ⋁ *P*[3,1]).

> • The preceding sentences are true in all wumpus worlds. Now we include the breeze percepts for the first two squares visited in the specific world the agent is in, leading up to the situation in [Figure 7.3](#index_split_014.html#filepos959784)(b).

> *R*[4] : ¬*B*[1,1].

> *R*[5] : *B*[2,1].

#### **7.4.4 A simple inference procedure**

Our goal now is to decide whether *KB* ⊨ α for some sentence α. For example, is ¬*P*[1,2] entailed by our *KB*? Our first algorithm for inference is a model-checking approach that is a direct implementation of the definition of entailment: enumerate the models, and check that α is true in every model in which *KB* is true. Models are assignments of true or false to every proposition symbol. Returning to our wumpus-world example, the relevant proposition symbols are *B*[1,1], *B*[2,1], *P*[1,1], *P*[1,2], *P*[2,1], *P*[2,2], and *P*[3,1]. With seven symbols, there are 2⁷ = 128 possible models; in three of these, *KB* is true ([Figure 7.9](#index_split_014.html#filepos996264)). In those three models, ¬*P*[1,2] is true, hence there is no pit in \[1,2\]. On the other hand, *P*[2,2] is true in two of the three models and false in one, so we cannot yet tell whether there is a pit in \[2,2\].

[Figure 7.9](#index_split_014.html#filepos996264) reproduces in a more precise form the reasoning illustrated in [Figure 7.5](#index_split_014.html#filepos965424). A general algorithm for deciding entailment in propositional logic is shown in [Figure 7.10](#index_split_014.html#filepos996892). Like the BACKTRACKING\-SEARCH algorithm [on page 215](#index_split_013.html#filepos865606), TT-ENTAILS? performs a recursive enumeration of a finite space of assignments to symbols. The algorithm is **sound** because it implements directly the definition of entailment, and **complete** because it works for any *KB* and α and always terminates—there are only finitely many models to examine.

Of course, “finitely many” is not always the same as “few.” If *KB* and α contain *n* symbols in all, then there are 2^(*n*) models. Thus, the time complexity of the algorithm is *O*(2^(*n*)). (The space complexity is only *O*(*n*) because the enumeration is depth-first.) Later in this chapter we show algorithms that are much more efficient in many cases. Unfortunately, propositional entailment is co-NP-complete (i.e., probably no easier than NP-complete—see Appendix A), so *every known inference algorithm for propositional logic has a worst-case complexity that is exponential in the size of the input.*

![image](images/00006.jpg)

> ![image](images/00180.jpg)

> **Figure 7.9** A truth table constructed for the knowledge base given in the text. *KB* is true if *R*[1] through *R*[5] are true, which occurs in just 3 of the 128 rows (the ones underlined in the right-hand column). In all 3 rows, *P*[1,2] is false, so there is no pit in \[1,2\]. On the other hand, there might (or might not) be a pit in \[2,2\].

> ![image](images/00181.jpg)

> **Figure 7.10** A truth-table enumeration algorithm for deciding propositional entailment. (TT stands for truth table.) PL-TRUE? returns *true* if a sentence holds within a model. The variable *model* represents a partial model—an assignment to some of the symbols. The keyword “**and**” is used here as a logical operation on its two arguments, returning *true* or *false*.

> ![image](images/00182.jpg)

> **Figure 7.11** Standard logical equivalences. The symbols α, β, and γ stand for arbitrary sentences of propositional logic.

### 7.5 PROPOSITIONAL THEOREM PROVING

So far, we have shown how to determine entailment by *model checking*: enumerating models and showing that the sentence must hold in all models. In this section, we show how entailment can be done by **theorem proving**—applying rules of inference directly to the sentences in our knowledge base to construct a proof of the desired sentence without consulting models. If the number of models is large but the length of the proof is short, then theorem proving can be more efficient than model checking.

* * *

THEOREM PROVING

* * *

Before we plunge into the details of theorem-proving algorithms, we will need some additional concepts related to entailment. The first concept is **logical equivalence**: two sentences α and β are logically equivalent if they are true in the same set of models. We write this as α ≡ β. For example, we can easily show (using truth tables) that *P* ⋀ Q and Q ⋀ *P* are logically equivalent; other equivalences are shown in [Figure 7.11](#index_split_014.html#filepos997575). These equivalences play much the same role in logic as arithmetic identities do in ordinary mathematics. An alternative definition of equivalence is as follows: any two sentences α and β are equivalent only if each of them entails the other:

* * *

LOGICAL EQUIVALENCE

* * *

> α ≡ β if and only if α ⊨ β and β ⊨ α.

The second concept we will need is **validity**. A sentence is valid if it is true in *all* models. For example, the sentence *P* ⋁¬*P* is valid. Valid sentences are also known as **tautologies**—they are *necessarily* true. Because the sentence *True* is true in all models, every valid sentence is logically equivalent to *True*. What good are valid sentences? From our definition of entailment, we can derive the **deduction theorem**, which was known to the ancient Greeks:

> *For any sentences* α *and* β, α ⊨ β *if and only if the sentence* (α ⇒ β) *is valid.*

* * *

VALIDITY

* * *

* * *

TAUTOLOGY

* * *

* * *

DEDUCTION THEOREM

* * *

![image](images/00006.jpg)

(Exercise 7.5 asks for a proof.) Hence, we can decide if α ⊨ β by checking that (α ⇒ β) is true in every model—which is essentially what the inference algorithm in [Figure 7.10](#index_split_014.html#filepos996892) does— or by proving that (α ⇒ β) is equivalent to True. Conversely, the deduction theorem states that every valid implication sentence describes a legitimate inference.

The final concept we will need is **satisfiability**. A sentence is satisfiable if it is true in, or satisfied by, *some* model. For example, the knowledge base given earlier, (*R*[1] ⋀ *R*[2] ⋀ *R*[3] ⋀ *R*[4] ⋀ *R*[5]), is satisfiable because there are three models in which it is true, as shown in [Figure 7.9](#index_split_014.html#filepos996264). Satisfiability can be checked by enumerating the possible models until one is found that satisfies the sentence. The problem of determining the satisfiability of sentences in propositional logic—the **SAT** problem—was the first problem proved to be NP-complete. Many problems in computer science are really satisfiability problems. For example, all the constraint satisfaction problems in [Chapter 6](#index_split_000.html#filepos813005) ask whether the constraints are satisfiable by some assignment.

* * *

SATISFIABILITY

* * *

* * *

SAT

* * *

Validity and satisfiability are of course connected: α is valid iff ¬α is unsatisfiable; contrapositively, α is satisfiable iff ¬α is not valid. We also have the following useful result:

> α ⊨ β *if and only if the sentence* (α ⋀ ¬β) *is unsatisfiable.*

Proving β from α by checking the unsatisfiability of (α ⋀ ¬β) corresponds exactly to the standard mathematical proof technique of *reductio ad absurdum* (literally, “reduction to an absurd thing”). It is also called proof by **refutation** or proof by **contradiction**. One assumes a sentence β to be false and shows that this leads to a contradiction with known axioms α. This contradiction is exactly what is meant by saying that the sentence (α ⋀¬β) is unsatisfiable.

* * *

REDUCTIOAD ABSURDUM

* * *

* * *

REFUTATION

* * *

* * *

CONTRADICTION

* * *

![image](images/00006.jpg)

#### **7.5.1 Inference and proofs**

This section covers **inference rules** that can be applied to derive a **proof**—a chain of conclusions that leads to the desired goal. The best-known rule is called **Modus Ponens** (Latin for *mode that affirms*) and is written

> ![equ](images/00183.jpg)

The notation means that, whenever any sentences of the form α ⇒ β and α are given, then the sentence β can be inferred. For example, if (*WumpusAhead* ⋀*WumpusAlive*) ⇒ *Shoot* and (*WumpusAhead* ⋀ *WumpusAlive*) are given, then *Shoot* can be inferred.

* * *

INFERENCE RULES

* * *

* * *

PROOF

* * *

* * *

MODUS PONENS

* * *

Another useful inference rule is **And-Elimination**, which says that, from a conjunction, any of the conjuncts can be inferred:

> ![equ](images/00184.jpg)

For example, from (*WumpusAhead* ⋀ *WumpusAlive*), *WumpusAlive* can be inferred.

* * *

AND-ELIMINATION

* * *

By considering the possible truth values of α and β, one can show easily that Modus Ponens and And-Elimination are sound once and for all. These rules can then be used in any particular instances where they apply, generating sound inferences without the need for enumerating models.

All of the logical equivalences in [Figure 7.11](#index_split_014.html#filepos997575) can be used as inference rules. For example, the equivalence for biconditional elimination yields the two inference rules

> ![equ](images/00185.jpg)

Not all inference rules work in both directions like this. For example, we cannot run Modus Ponens in the opposite direction to obtain α ⇒ β and α from β.

Let us see how these inference rules and equivalences can be used in the wumpus world. We start with the knowledge base containing *R*[1] through *R*[5] and show how to prove ¬*P*[1,2], that is, there is no pit in \[1,2\]. First, we apply biconditional elimination to *R*[2] to obtain

> *R*[6] : (*B*[1,1] ⇒ (*P*[1,2] ⋁ *P*[2,1])) ⋀ ((*P*[1,2] ⋁ *P*[2,1]) ⇒ *B*[1,1]).

Then we apply And-Elimination to *R*[6] to obtain

> *R*[7] : ((*P*[1,2] ⋁ *P*[2,1]) ⇒ *B*[1,1]).

Logical equivalence for contrapositives gives

> *R*[8] : (¬*B*[1,1] ⇒ ¬(*P*[1,2] ⋁ *P*[2,1])).

Now we can apply Modus Ponens with *R*[8] and the percept *R*[4] (i.e., ¬*B*[1,1]), to obtain

> *R*[9] : ¬(*P*[1,2] ⋁ *P*[2,1]).

Finally, we apply De Morgan’s rule, giving the conclusion

> *R*[10] : ¬*P*[1,2] ⋀ ¬*P*[2,1].

That is, neither \[1,2\] nor \[2,1\] contains a pit.

We found this proof by hand, but we can apply any of the search algorithms in [Chapter 3](#index_split_000.html#filepos301685) to find a sequence of steps that constitutes a proof. We just need to define a proof problem as follows:

> • INITIAL STATE: the initial knowledge base.

> • ACTIONS: the set of actions consists of all the inference rules applied to all the sentences that match the top half of the inference rule.

> • RESULT: the result of an action is to add the sentence in the bottom half of the inference rule.

> • GOAL: the goal is a state that contains the sentence we are trying to prove.

Thus, searching for proofs is an alternative to enumerating models. In many practical cases *finding a proof can be more efficient because the proof can ignore irrelevant propositions, no matter how many of them there are.* For example, the proof given earlier leading to ¬*P*[1,2] ⋀ ¬*P*[2,1] does not mention the propositions *B*[2,1], *P*[1,1], *P*[2,2], or *P*[3,1]. They can be ignored because the goal proposition, *P*[1,2], appears only in sentence *R*[2]; the other propositions in *R*[2] appear only in *R*[4] and *R*[2];so *R*[1], *R*[3],and *R*[5] have no bearing on the proof. The same would hold even if we added a million more sentences to the knowledge base; the simple truth-table algorithm, on the other hand, would be overwhelmed by the exponential explosion of models.

![image](images/00006.jpg)

One final property of logical systems is **monotonicity**, which says that the set of entailed sentences can only *increase* as information is added to the knowledge base.[⁸](#index_split_015.html#filepos5582443) For any sentences α and β,

> if *KB* ⊨ α then *KB* ⋀ β ⊨ α.

* * *

MONOTONICITY

* * *

For example, suppose the knowledge base contains the additional assertion β stating that there are exactly eight pits in the world. This knowledge might help the agent draw *additional* conclusions, but it cannot invalidate any conclusion α already inferred—such as the conclusion that there is no pit in \[1,2\]. Monotonicity means that inference rules can be applied whenever suitable premises are found in the knowledge base—the conclusion of the rule must follow *regardless of what else is in the knowledge base*.

#### **7.5.2 Proof by resolution**

We have argued that the inference rules covered so far are *sound*, but we have not discussed the question of *completeness* for the inference algorithms that use them. Search algorithms such as iterative deepening search ([page 89](#index_split_010.html#filepos393451)) are complete in the sense that they will find any reachable goal, but if the available inference rules are inadequate, then the goal is not reachable—no proof exists that uses only those inference rules. For example, if we removed the biconditional elimination rule, the proof in the preceding section would not go through. The current section introduces a single inference rule, **resolution**, that yields a complete inference algorithm when coupled with any complete search algorithm.

We begin by using a simple version of the resolution rule in the wumpus world. Let us consider the steps leading up to [Figure 7.4](#index_split_014.html#filepos960239)(a): the agent returns from \[2,1\] to \[1,1\] and then goes to \[1,2\], where it perceives a stench, but no breeze. We add the following facts to the knowledge base:

> *R*[11] : ¬*B*[1,2].

> *R*[12] : *B*[1,2] ⇔ (*P*[1,1] ⋁ *P*[2,2] ⋁ *P*[1,3]).

By the same process that led to *R*[10] earlier, we can now derive the absence of pits in \[2,2\] and \[1,3\] (remember that \[1,1\] is already known to be pitless):

> *R*[13] : ¬*P*[2,2].

> *R*[14] : ¬*P*[1,3].

We can also apply biconditional elimination to *R*[3], followed by Modus Ponens with *R*[5], to obtain the fact that there is a pit in \[1,1\], \[2,2\], or \[3,1\]:

> *R*[15] : *P*[1,1] ⋁ *P*[2,2] ⋁ *P*[3,1].

Now comes the first application of the resolution rule: the literal ¬*P*[2,2] in *R*[13] *resolves with* the literal *P*[2,2] in *R*[15] to give the **resolvent**

> *R*[16] : *P*[1,1] ⋁ *P*[3,1].

* * *

RESOLVENT

* * *

In English; if there’s a pit in one of \[1,1\], \[2,2\], and \[3,1\] and it’s not in \[2,2\], then it’s in \[1,1\] or \[3,1\]. Similarly, the literal ¬*P*[1,1] in *R*[1] resolves with the literal *P*[1,1] in *R*[16] to give

> *R*[17] : *P*[3,1].

In English: if there’s a pit in \[1,1\] or \[3,1\] and it’s not in \[1,1\], then it’s in \[3,1\]. These last two inference steps are examples of the **unit resolution** inference rule,

> ![equ](images/00186.jpg)

* * *

UNIT RESOLUTION

* * *

where each ℓ is a literal and ℓ[*i*] and *m* are **complementary literals** (i.e., one is the negation of the other). Thus, the unit resolution rule takes a **clause**—a disjunction of literals—and a literal and produces a new clause. Note that a single literal can be viewed as a disjunction of one literal, also known as a **unit clause**.

* * *

COMPLEMENTARY LITERALS

* * *

* * *

CLAUSE

* * *

* * *

UNIT CLAUSE

* * *

The unit resolution rule can be generalized to the full **resolution** rule,

> ![equ](images/00187.jpg)

where ℓ[*i*] and *m*[*j*] are complementary literals. This says that resolution takes two clauses and produces a new clause containing all the literals of the two original clauses *except* the two complementary literals. For example, we have

> ![equ](images/00188.jpg)

* * *

RESOLUTION

* * *

There is one more technical aspect of the resolution rule: the resulting clause should contain only one copy of each literal.[⁹](#index_split_015.html#filepos5582765) The removal of multiple copies of literals is called **factoring**. For example, if we resolve (*A* ⋁ *B*) with (*A* ⋁¬*B*), we obtain (*A* ⋁ *A*), which is reduced to just *A*.

* * *

FACTORING

* * *

The *soundness* of the resolution rule can be seen easily by considering the literal ℓ[*i*] that is complementary to literal *m*[*j*] in the other clause. If ℓ[*i*] is true, then *m*[*j*] is false, and hence *m*[1] ⋁ … ⋁ *m*[*j*−1] ⋁ *m*[*j*+1] ⋁ … ⋁ *m*[*n*] must be true, because *m*[1] ⋁ … ⋁ *m*[*n*] is given. If ℓ[*i*] is false, then ℓ[1] ⋁ … ⋁ ℓ[*i*−1] ⋁ [*i*+1] ⋁ … ⋁ ℓ[*k*] must be true because ℓ[1] ⋁ … ⋁ ℓ[*k*] is given. Now ℓ[*i*] is either true or false, so one or other of these conclusions holds—exactly as the resolution rule states.

![image](images/00006.jpg)

What is more surprising about the resolution rule is that it forms the basis for a family of *complete* inference procedures. *A resolution-based theorem prover can, for any sentences* α *and* β *in propositional logic, decide whether* α ⊨ β*.* The next two subsections explain how resolution accomplishes this.

##### **Conjunctive normal form**

The resolution rule applies only to clauses (that is, disjunctions of literals), so it would seem to be relevant only to knowledge bases and queries consisting of clauses. How, then, can it lead to a complete inference procedure for all of propositional logic? The answer is that *every sentence of propositional logic is logically equivalent to a conjunction of clauses.* A sentence expressed as a conjunction of clauses is said to be in **conjunctive normal form** or **CNF** (see [Figure 7.14](#index_split_014.html#filepos1036521)). We now describe a procedure for converting to CNF. We illustrate the procedure by converting the sentence *B*[1,1] ⇔ (*P*[1,2] ⋁ *P*[2,1]) into CNF. The steps are as follows:

> 1\. Eliminate ⇔, replacing α ⇔ β with (α ⇒ β) ⋀ (β ⇒ α).

> (*B*[1,1] ⇒ (*P*[1,2] ⋁ *P*[2,1])) ⋀ ((*P*[1,2] ⋁ *P*[2,1]) ⇒ *B*[1,1]).

> 2\. Eliminate ⇒, replacing α ⇒ β with ¬α ⋁ β:

> (¬*B*[1,1] ⋁ *P*[1,2] ⋁ *P*[2,1]) ⋀ (¬(*P*[1,2] ⋁ *P*[2,1]) ⋁ *B*[1,1]).

![image](images/00006.jpg)

* * *

CONJUNCTIVE NORMAL FORM

* * *

> 3\. CNF requires ¬ to appear only in literals, so we “move ¬ inwards” by repeated application of the following equivalences from [Figure 7.11](#index_split_014.html#filepos997575):

> ¬(¬α) ≡ α (double-negation elimination)

> ¬(α ⋀ β) ≡ (¬ α ⋁ ¬ β) (De Morgan)

> ¬(α ⋁ β) ≡ (¬ α ⋀ ¬ β) (De Morgan)

> In the example, we require just one application of the last rule:

> (¬*B*[1,1] ⋁ *P*[1,2] ⋁ *P*[2,1]) ⋀ ((¬*P*[1,2] ⋀¬*P*[2,1]) ⋁ *B*[1,1]).

> 4\. Now we have a sentence containing nested ⋀ and ⋁ operators applied to literals. We apply the distributivity law from [Figure 7.11](#index_split_014.html#filepos997575), distributing ⋁ over ⋀ wherever possible.

> (¬*B*[1,1] ⋁ *P*[1,2] ⋁ *P*[2,1]) ⋀ (¬*P*[1,2] ⋁ *B*[1,1]) ⋀ (¬*P*[2,1] ⋁ *B*[1,1]).

The original sentence is now in CNF, as a conjunction of three clauses. It is much harder to read, but it can be used as input to a resolution procedure.

##### **A resolution algorithm**

Inference procedures based on resolution work by using the principle of proof by contradiction introduced [on page 250](#index_split_014.html#filepos1001363). That is, to show that *KB* ⊨ α, we show that (*KB* ⋀ ¬α) is unsatisfiable. We do this by proving a contradiction.

A resolution algorithm is shown in [Figure 7.12](#index_split_014.html#filepos1028081). First, (*KB* ⋀ ¬α) is converted into CNF. Then, the resolution rule is applied to the resulting clauses. Each pair that contains complementary literals is resolved to produce a new clause, which is added to the set if it is not already present. The process continues until one of two things happens:

> • there are no new clauses that can be added, in which case *KB* does not entail α; or,

> • two clauses resolve to yield the *empty* clause, in which case *KB* entails α.

The empty clause—a disjunction of no disjuncts—is equivalent to False because a disjunction is true only if at least one of its disjuncts is true. Another way to see that an empty clause represents a contradiction is to observe that it arises only from resolving two complementary unit clauses such as *P* and ¬*P*.

We can apply the resolution procedure to a very simple inference in the wumpus world. When the agent is in \[1,1\], there is no breeze, so there can be no pits in neighboring squares. The relevant knowledge base is

> *KB* = *R*[2] ⋀ *R*[4] = (*B*[1,1] ⇔ (*P*[1,2] ⋁ *P*[2,1])) ⋀ ¬*B*[1,1]

and we wish to prove α which is, say, ¬*P*[1,2]. When we convert (*KB* ⋀ ¬α) into CNF, we obtain the clauses shown at the top of [Figure 7.13](#index_split_014.html#filepos1028496). The second row of the figure shows clauses obtained by resolving pairs in the first row. Then, when *P*[1,2] is resolved with ¬*P*[1,2], we obtain the empty clause, shown as a small square. Inspection of [Figure 7.13](#index_split_014.html#filepos1028496) reveals that many resolution steps are pointless. For example, the clause *B*[1,1] ⋁ ¬*B*[1,1] ⋁ *P*[1,2] is equivalent to *True* ⋁ *P*[1,2] which is equivalent to *True*. Deducing that *True* is true is not very helpful. Therefore, any clause in which two complementary literals appear can be discarded.

> ![image](images/00189.jpg)

> **Figure 7.12** A simple resolution algorithm for propositional logic. The function PL-RESOLVE returns the set of all possible clauses obtained by resolving its two inputs.

> ![image](images/00190.jpg)

> **Figure 7.13** Partial application of PL-RESOLUTION to a simple inference in the wumpus world. ¬*P*[1,2] is shown to follow from the first four clauses in the top row.

##### **Completeness of resolution**

To conclude our discussion of resolution, we now show why PL-RESOLUTION is complete. To do this, we introduce the **resolution closure** *RC*(*S*) of a set of clauses *S*, which is the set of all clauses derivable by repeated application of the resolution rule to clauses in *S* or their derivatives. The resolution closure is what PL-RESOLUTION computes as the final value of the variable *clauses*. It is easy to see that *RC*(*S*) must be finite, because there are only finitely many distinct clauses that can be constructed out of the symbols *P*[1],…,*P*[*k*] that appear in *S*. (Notice that this would not be true without the factoring step that removes multiple copies of literals.) Hence, PL-RESOLUTION always terminates.

* * *

RESOLUTION CLOSURE

* * *

The completeness theorem for resolution in propositional logic is called the **ground resolution theorem**:

* * *

GROUND RESOLUTION THEOREM

* * *

> If a set of clauses is unsatisfiable, then the resolution closure of those clauses contains the empty clause.

This theorem is proved by demonstrating its contrapositive: if the closure *RC*(*S*) does *not* contain the empty clause, then *S* is satisfiable. In fact, we can construct a model for S with suitable truth values for *P*[1],…,*P*[*k*]. The construction procedure is as follows:

For *i* from 1 to *k*,

> **–** If a clause in *RC*(*S*) contains the literal ¬*P*[*i*] and all its other literals are false under the assignment chosen for *P*[1],…,*P*[*i*−1], then assign *false* to *P*[*i*].

> **–** Otherwise, assign *true* to *P*[*i*].

This assignment to *P*[1],…,*P*[*k*] is a model of *S*. To see this, assume the opposite—that, at some stage *i* in the sequence, assigning symbol *P*[*i*] causes some clause *C* to become false. For this to happen, it must be the case that all the *other* literals in *C* must already have been falsified by assignments to *P*[1],…,*P*[*i*−1]. Thus, *C* must now look like either (*false* ⋁ *false* ⋁ … *false* ⋁ *P*[*i*]) or like (*false* ⋁ *false* ⋁ … *false* ⋁ ¬*P*[*i*]). If just one of these two is in *RC*(*S*), then the algorithm will assign the appropriate truth value to *P*[*i*] to make *C* true, so *C* can only be falsified if *both* of these clauses are in *RC*(*S*). Now,since *RC*(*S*) is closed under resolution, it will contain the resolvent of these two clauses, and that resolvent will have all of its literals already falsified by the assignments to *P*[1],…,*P*[*i*−1]. This contradicts our assumption that the first falsified clause appears at stage *i*. Hence, we have proved that the construction never falsifies a clause in *RC*(*S*); that is, it produces a model of *RC*(*S*) and thus a model of *S* itself (since *S* is contained in *RC*(*S*)).

#### **7.5.3 Horn clauses and definite clauses**

The completeness of resolution makes it a very important inference method. In many practical situations, however, the full power of resolution is not needed. Some real-world knowledge bases satisfy certain restrictions on the form of sentences they contain, which enables them to use a more restricted and efficient inference algorithm.

One such restricted form is the **definite clause**, which is a disjunction of literals of which *exactly one is positive*. For example, the clause (¬*L*[1,1] ⋁ ¬*Breeze* ⋁ *B*[1,1]) is a definite clause, whereas (¬*B*[1,1] ⋁ *P*[1,2] ⋁ *P*[2,1]) is not.

* * *

DEFINITE CLAUSE

* * *

Slightly more general is the **Horn clause**, which is a disjunction of literals of which *at most one is positive*. So all definite clauses are Horn clauses, as are clauses with no positive literals; these are called **goal clauses**. Horn clauses are closed under resolution: if you resolve two Horn clauses, you get back a Horn clause.

* * *

HORN CLAUSE

* * *

* * *

GOAL CLAUSES

* * *

Knowledge bases containing only definite clauses are interesting for three reasons:

> 1\. Every definite clause can be written as an implication whose premise is a conjunction of positive literals and whose conclusion is a single positive literal. (See Exercise 7.13.) For example, the definite clause (¬*L*[1,1] ⋁ ¬*Breeze* ⋁ *B*[1,1]) can be written as the implication (*L*[1,1] ⋀ *Breeze*) ⇒ *B*[1,1]. In the implication form, the sentence is easier to understand: it says that if the agent is in \[1,1\] and there is a breeze, then \[1,1\] is breezy. In Horn form, the premise is called the **body** and the conclusion is called the **head**. A sentence consisting of a single positive literal, such as *L*[1,1], is called a **fact**. It too can be written in implication form as *True* ⇒ *L*[1,1], but it is simpler to write just *L*[1,1].

* * *

BODY

* * *

* * *

HEAD

* * *

* * *

FACT

* * *

> ![image](images/00191.jpg)

> **Figure 7.14** A grammar for conjunctive normal form, Horn clauses, and definite clauses. A clause such as *A* ⋀ *B* ⇒ *C* is still a definite clause when it is written as ¬*A* ⋁ ¬*B* ⋁ *C*, but only the former is considered the canonical form for definite clauses. One more class is the *k*\-CNF sentence, which is a CNF sentence where each clause has at most *k* literals.

> 2\. Inference with Horn clauses can be done through the **forward-chaining** and **backward-chaining** algorithms, which we explain next. Both of these algorithms are natural, in that the inference steps are obvious and easy for humans to follow. This type of inference is the basis for **logic programming**, which is discussed in [Chapter 9](#index_split_015.html#filepos1300686).

* * *

FORWARD-CHAINING

* * *

* * *

BACKWARD-CHAINING

* * *

> 3\. Deciding entailment with Horn clauses can be done in time that is *linear* in the size of the knowledge base—a pleasant surprise.

#### **7.5.4 Forward and backward chaining**

The forward-chaining algorithm PL-FC-ENTAILS? (*KB*, *q*) determines if a single proposition symbol *q*—the query—is entailed by a knowledge base of definite clauses. It begins from known facts (positive literals) in the knowledge base. If all the premises of an implication are known, then its conclusion is added to the set of known facts. For example, if *L*[1,1] and Breeze are known and (*L*[1,1] ⋀ *Breeze*) ⇒ *B*[1,1] is in the knowledge base, then *B*[1,1] can be added. This process continues until the query *q* is added or until no further inferences can be made. The detailed algorithm is shown in [Figure 7.15](#index_split_014.html#filepos1040147); the main point to remember is that it runs in linear time.

The best way to understand the algorithm is through an example and a picture. [Figure 7.16](#index_split_014.html#filepos1043891)(a) shows a simple knowledge base of Horn clauses with *A* and *B* as known facts. [Figure 7.16](#index_split_014.html#filepos1043891)(b) shows the same knowledge base drawn as an **AND–OR graph** (see [Chapter 4](#index_split_000.html#filepos513290)). In AND–OR graphs, multiple links joined by an arc indicate a conjunction—every link must be proved—while multiple links without an arc indicate a disjunction—any link can be proved. It is easy to see how forward chaining works in the graph. The known leaves (here, *A* and *B*) are set, and inference propagates up the graph as far as possible. Wherever a conjunction appears, the propagation waits until all the conjuncts are known before proceeding. The reader is encouraged to work through the example in detail.

> ![image](images/00192.jpg)

> **Figure 7.15** The forward-chaining algorithm for propositional logic. The *agenda* keeps track of symbols known to be true but not yet “processed.” The *count* table keeps track of how many premises of each implication are as yet unknown. Whenever a new symbol *p* from the agenda is processed, the count is reduced by one for each implication in whose premise *p* appears (easily identified in constant time with appropriate indexing.) If a count reaches zero, all the premises of the implication are known, so its conclusion can be added to the agenda. Finally, we need to keep track of which symbols have been processed; a symbol that is already in the set of inferred symbols need not be added to the agenda again. This avoids redundant work and prevents loops caused by implications such as *P* ⇒ *Q* and *Q* ⇒ *P*.

It is easy to see that forward chaining is **sound**: every inference is essentially an application of Modus Ponens. Forward chaining is also **complete**: every entailed atomic sentence will be derived. The easiest way to see this is to consider the final state of the inferred table (after the algorithm reaches a **fixed point** where no new inferences are possible). The table contains true for each symbol inferred during the process, and false for all other symbols. We can view the table as a logical model; moreover, *every definite clause in the original KB is true in this model.* To see this, assume the opposite, namely that some clause *a*[1]⋀…⋀*a*[*k*] ⇒ *b* is false in the model. Then *a*[1] ⋀… ⋀ *a*[*k*] must be true in the model and b must be false in the model. But this contradicts our assumption that the algorithm has reached a fixed point! We can conclude, therefore, that the set of atomic sentences inferred at the fixed point defines a model of the original KB. Furthermore, any atomic sentence q that is entailed by the KB must be true in all its models and in this model in particular. Hence, every entailed atomic sentence q must be inferred by the algorithm.

* * *

FIXED POINT

* * *

* * *

DATA-DRIVEN

* * *

Forward chaining is an example of the general concept of **data-driven** reasoning—that is, reasoning in which the focus of attention starts with the known data. It can be used within an agent to derive conclusions from incoming percepts, often without a specific query in mind. For example, the wumpus agent might TELL its percepts to the knowledge base using an incremental forward-chaining algorithm in which new facts can be added to the agenda to initiate new inferences. In humans, a certain amount of data-driven reasoning occurs as new information arrives. For example, if I am indoors and hear rain starting to fall, it might occur to me that the picnic will be canceled. Yet it will probably not occur to me that the seventeenth petal on the largest rose in my neighbor’s garden will get wet; humans keep forward chaining under careful control, lest they be swamped with irrelevant consequences.

> ![image](images/00193.jpg)

> **Figure 7.16** (a) A set of Horn clauses. (b) The corresponding AND–OR graph.

The backward-chaining algorithm, as its name suggests, works backward from the query. If the query *q* is known to be true, then no work is needed. Otherwise, the algorithm finds those implications in the knowledge base whose conclusion is *q*. If all the premises of one of those implications can be proved true (by backward chaining), then *q* is true. When applied to the query *Q* in [Figure 7.16](#index_split_014.html#filepos1043891), it works back down the graph until it reaches a set of known facts, *A* and *B*, that forms the basis for a proof. The algorithm is essentially identical to the AND\-OR\-GRAPH\-SEARCH algorithm in [Figure 4.11](#index_split_011.html#filepos569895). As with forward chaining, an efficient implementation runs in linear time.

Backward chaining is a form of **goal-directed reasoning**. It is useful for answering specific questions such as “What shall I do now?” and “Where are my keys?” Often, the cost of backward chaining is *much less* than linear in the size of the knowledge base, because the process touches only relevant facts.

* * *

GOAL-DIRECTED

* * *

* * *

REASONING

* * *

### 7.6 EFFECTIVE PROPOSITIONAL MODEL CHECKING

In this section, we describe two families of efficient algorithms for general propositional inference based on model checking: One approach based on backtracking search, and one on local hill-climbing search. These algorithms are part of the “technology” of propositional logic. This section can be skimmed on a first reading of the chapter.

The algorithms we describe are for checking satisfiability: the SAT problem. (As noted earlier, testing entailment, α ⊨ β, can be done by testing *un*satisfiability of α ⋀ ¬β.) We have already noted the connection between finding a satisfying model for a logical sentence and finding a solution for a constraint satisfaction problem, so it is perhaps not surprising that the two families of algorithms closely resemble the backtracking algorithms of [Section 6.3](#index_split_000.html#filepos863258) and the local search algorithms of [Section 6.4](#index_split_000.html#filepos889433). They are, however, extremely important in their own right because so many combinatorial problems in computer science can be reduced to checking the satisfiability of a propositional sentence. Any improvement in satisfiability algorithms has huge consequences for our ability to handle complexity in general.

#### **7.6.1 A complete backtracking algorithm**

The first algorithm we consider is often called the **Davis–Putnam algorithm**, after the seminal paper by Martin Davis and Hilary Putnam (1960). The algorithm is in fact the version described by Davis, Logemann, and Loveland (1962), so we will call it DPLL after the initials of all four authors. DPLL takes as input a sentence in conjunctive normal form—a set of clauses. Like BACKTRACKING\-SEARCH and TT-ENTAILS?, it is essentially a recursive, depth-first enumeration of possible models. It embodies three improvements over the simple scheme of TT-ENTAILS?:

> • *Early termination*: The algorithm detects whether the sentence must be true or false, even with a partially completed model. A clause is true if *any* literal is true, even if the other literals do not yet have truth values; hence, the sentence as a whole could be judged true even before the model is complete. For example, the sentence (*A* ⋁ *B*) ⋀ (*A* ⋁ *C*) is true if *A* is true, regardless of the values of *B* and *C*. Similarly, a sentence is false if *any* clause is false, which occurs when each of its literals is false. Again, this can occur long before the model is complete. Early termination avoids examination of entire subtrees in the search space.

> • *Pure symbol heuristic*: A **pure symbol** is a symbol that always appears with the same “sign” in all clauses. For example, in the three clauses (*A* ⋁ ¬*B*), (¬*B* ⋁ ¬*C*), and (*C* ⋁ *A*), the symbol *A* is pure because only the positive literal appears, *B* is pure because only the negative literal appears, and *C* is impure. It is easy to see that if a sentence has a model, then it has a model with the pure symbols assigned so as to make their literals *true*, because doing so can never make a clause false. Note that, in determining the purity of a symbol, the algorithm can ignore clauses that are already known to be true in the model constructed so far. For example, if the model contains *B* = *false*, then the clause (¬*B* ⋁ ¬*C*) is already true, and in the remaining clauses *C* appears only as a positive literal; therefore *C* becomes pure.

> • *Unit clause heuristic*: A **unit clause** was defined earlier as a clause with just one literal. In the context of DPLL, it also means clauses in which all literals but one are already assigned false by the model. For example, if the model contains *B* = *true*, then (¬*B* ⋁ ¬*C*) simplifies to ¬*C*, which is a unit clause. Obviously, for this clause to be true, C must be set to *false*. The unit clause heuristic assigns all such symbols before branching on the remainder. One important consequence of the heuristic is that any attempt to prove (by refutation) a literal that is already in the knowledge base will succeed immediately (Exercise 7.23). Notice also that assigning one unit clause can create another unit clause—for example, when *C* is set to *false*, (*C* ⋁ *A*) becomes a unit clause, causing *true* to be assigned to *A*. This “cascade” of forced assignments is called **unit propagation**. It resembles the process of forward chaining with definite clauses, and indeed, if the CNF expression contains only definite clauses then DPLL essentially replicates forward chaining. (See Exercise 7.24.)

* * *

DAVIS–PUTNAM ALGORITHM

* * *

* * *

PURE SYMBOL

* * *

* * *

UNIT PROPAGATION

* * *

> ![image](images/00194.jpg)

> **Figure 7.17** The DPLL algorithm for checking satisfiability of a sentence in propositional logic. The ideas behind FIND\-PURE\-SYMBOL and FIND\-UNIT\-CLAUSE are described in the text; each returns a symbol (or null) and the truth value to assign to that symbol. Like TT-ENTAILS?, DPLL operates over partial models.

The DPLL algorithm is shown in [Figure 7.17](#index_split_014.html#filepos1051769), which gives the the essential skeleton of the search process.

What [Figure 7.17](#index_split_014.html#filepos1051769) does not show are the tricks that enable SAT solvers to scale up to large problems. It is interesting that most of these tricks are in fact rather general, and we have seen them before in other guises:

> 1\. **Component analysis** (as seen with Tasmania in CSPs): As DPLL assigns truth values to variables, the set of clauses may become separated into disjoint subsets, called **components**, that share no unassigned variables. Given an efficient way to detect when this occurs, a solver can gain considerable speed by working on each component separately.

> 2\. **Variable and value ordering** (as seen in [Section 6.3.1](#index_split_000.html#filepos869613) for CSPs): Our simple implementation of DPLL uses an arbitrary variable ordering and always tries the value *true* before *false*. The **degree heuristic** (see [page 216](#index_split_013.html#filepos868813)) suggests choosing the variable that appears most frequently over all remaining clauses.

> 3\. **Intelligent backtracking** (as seen in [Section 6.3](#index_split_000.html#filepos863258) for CSPs): Many problems that cannot be solved in hours of run time with chronological backtracking can be solved in seconds with intelligent backtracking that backs up all the way to the relevant point of conflict. All SAT solvers that do intelligent backtracking use some form of **conflict clause learning** to record conflicts so that they won’t be repeated later in the search. Usually a limited-size set of conflicts is kept, and rarely used ones are dropped.

> 4\. **Random restarts** (as seen [on page 124](#index_split_011.html#filepos527152) for hill-climbing): Sometimes a run appears not to be making progress. In this case, we can start over from the top of the search tree, rather than trying to continue. After restarting, different random choices (in variable and value selection) are made. Clauses that are learned in the first run are retained after the restart and can help prune the search space. Restarting does not guarantee that a solution will be found faster, but it does reduce the variance on the time to solution.

> 5\. **Clever indexing** (as seen in many algorithms): The speedup methods used in DPLL itself, as well as the tricks used in modern solvers, require fast indexing of such things as “the set of clauses in which variable *X*[*i*] appears as a positive literal.” This task is complicated by the fact that the algorithms are interested only in the clauses that have not yet been satisfied by previous assignments to variables, so the indexing structures must be updated dynamically as the computation proceeds.

With these enhancements, modern solvers can handle problems with tens of millions of variables. They have revolutionized areas such as hardware verification and security protocol verification, which previously required laborious, hand-guided proofs.

#### **7.6.2 Local search algorithms**

We have seen several local search algorithms so far in this book, including HILL\-CLIMBING ([page 122](#index_split_011.html#filepos519861)) and SIMULATED\-ANNEALING ([page 126](#index_split_011.html#filepos534299)). These algorithms can be applied directly to satisfiability problems, provided that we choose the right evaluation function. Because the goal is to find an assignment that satisfies every clause, an evaluation function that counts the number of unsatisfied clauses will do the job. In fact, this is exactly the measure used by the MIN\-CONFLICTS algorithm for CSPs ([page 221](#index_split_013.html#filepos890524)). All these algorithms take steps in the space of complete assignments, flipping the truth value of one symbol at a time. The space usually contains many local minima, to escape from which various forms of randomness are required. In recent years, there has been a great deal of experimentation to find a good balance between greediness and randomness.

One of the simplest and most effective algorithms to emerge from all this work is called WALKSAT ([Figure 7.18](#index_split_014.html#filepos1058511)). On every iteration, the algorithm picks an unsatisfied clause and picks a symbol in the clause to flip. It chooses randomly between two ways to pick which symbol to flip: (1) a “minconflicts” step that minimizes the number of unsatisfied clauses in the new state and (2) a “random walk” step that picks the symbol randomly.

When WALKSAT returns a model, the input sentence is indeed satisfiable, but when it returns *failure*, there are two possible causes: either the sentence is unsatisfiable or we need to give the algorithm more time. If we set *max\_flips* = ∞ and *p* > 0, WALKSAT will eventually return a model (if one exists), because the random-walk steps will eventually hit upon the solution. Alas, if *max\_flips* is infinity and the sentence is unsatisfiable, then the algorithm never terminates!

> ![image](images/00195.jpg)

> **Figure 7.18** The WALKSAT algorithm for checking satisfiability by randomly flipping the values of variables. Many versions of the algorithm exist.

For this reason, WALKSAT is most useful when we expect a solution to exist—for example, the problems discussed in [Chapters 3](#index_split_000.html#filepos301685) and [6](#index_split_000.html#filepos813005) usually have solutions. On the other hand, WALKSAT cannot always detect *unsatisfiability*, which is required for deciding entailment. For example, an agent cannot *reliably* use WALKSAT to prove that a square is safe in the wumpus world. Instead, it can say, “I thought about it for an hour and couldn’t come up with a possible world in which the square *isn’t* safe.” This may be a good empirical indicator that the square is safe, but it’s certainly not a proof.

#### **7.6.3 The landscape of random SAT problems**

Some SAT problems are harder than others. *Easy* problems can be solved by any old algorithm, but because we know that SAT is NP-complete, at least some problem instances must require exponential run time. In [Chapter 6](#index_split_000.html#filepos813005), we saw some surprising discoveries about certain kinds of problems. For example, the *n*\-queens problem—thought to be quite tricky for backtracking search algorithms—turned out to be trivially easy for local search methods, such as minconflicts. This is because solutions are very densely distributed in the space of assignments, and any initial assignment is guaranteed to have a solution nearby. Thus, n-queens is easy because it is **underconstrained**.

* * *

UNDERCONSTRAINED

* * *

When we look at satisfiability problems in conjunctive normal form, an underconstrained problem is one with relatively *few* clauses constraining the variables. For example, here is a randomly generated 3-CNF sentence with five symbols and five clauses:

> (¬*D* ⋁ ¬*B* ⋁ *C*) ⋀ (*B* ⋁ ¬*A* ⋁ ¬*C*) ⋀ (¬*C* ⋁ ¬*B* ⋁ *E*)

> ⋀ (*E* ⋁ ¬*D* ⋁ *B*) ⋀ (*B* ⋁ *E* ⋁ ¬*C*).

Sixteen of the 32 possible assignments are models of this sentence, so, on average, it would take just two random guesses to find a model. This is an easy satisfiability problem, as are most such underconstrained problems. On the other hand, an *overconstrained* problem has many clauses relative to the number of variables and is likely to have no solutions.

To go beyond these basic intuitions, we must define exactly how random sentences are generated. The notation *CNF*[*k*](*m*, *n*) denotes a *k*\-CNF sentence with *m* clauses and *n* symbols, where the clauses are chosen uniformly, independently, and without replacement from among all clauses with *k* different literals, which are positive or negative at random. (A symbol may not appear twice in a clause, nor may a clause appear twice in a sentence.)

Given a source of random sentences, we can measure the probability of satisfiability. [Figure 7.19](#index_split_014.html#filepos1063903)(a) plots the probability for *CN* *F*[3](*m*, 50), that is, sentences with 50 variables and 3 literals per clause, as a function of the clause/symbol ratio, *m*/*n*. As we expect, for small *m*/*n* the probability of satisfiability is close to 1, and at large *m*/*n* the probability is close to 0. The probability drops fairly sharply around *m*/*n* = 4.3. Empirically, we find that the “cliff” stays in roughly the same place (for *k* = 3) and gets sharper and sharper as *n* increases. Theoretically, the **satisfiability threshold conjecture** says that for every *k* ≥ 3, there is a threshold ratio *r*[*k*] such that, as *n* goes to infinity, the probability that *CN* *F*[*k*](*n*, *rn*) is satisfiable becomes 1 for all values of *r* below the threshold, and 0 for all values above. The conjecture remains unproven.

* * *

SATISFIABILITY THRESHOLD CONJECTURE

* * *

> ![image](images/00196.jpg)

> **Figure 7.19** (a) Graph showing the probability that a random 3-CNF sentence with *n* = 50 symbols is satisfiable, as a function of the clause/symbol ratio *m*/*n*. (b) Graph of the median run time (measured in number of recursive calls to DPLL, a good proxy) on random 3-CNF sentences. The most difficult problems have a clause/symbol ratio of about 4.3.

Now that we have a good idea where the satisfiable and unsatisfiable problems are, the next question is, where are the hard problems? It turns out that they are also often at the threshold value. [Figure 7.19](#index_split_014.html#filepos1063903)(b) shows that 50-symbol problems at the threshold value of 4.3 are about 20 times more difficult to solve than those at a ratio of 3.3. The underconstrained problems are easiest to solve (because it is so easy to guess a solution); the overconstrained problems are not as easy as the underconstrained, but still are much easier than the ones right at the threshold.

### 7.7 AGENTS BASED ON PROPOSITIONAL LOGIC

In this section, we bring together what we have learned so far in order to construct wumpus world agents that use propositional logic. The first step is to enable the agent to deduce, to the extent possible, the state of the world given its percept history. This requires writing down a complete logical model of the effects of actions. We also show how the agent can keep track of the world efficiently without going back into the percept history for each inference. Finally, we show how the agent can use logical inference to construct plans that are guaranteed to achieve its goals.

#### **7.7.1 The current state of the world**

As stated at the beginning of the chapter, a logical agent operates by deducing what to do from a knowledge base of sentences about the world. The knowledge base is composed of axioms—general knowledge about how the world works—and percept sentences obtained from the agent’s experience in a particular world. In this section, we focus on the problem of deducing the current state of the wumpus world—where am I, is that square safe, and so on.

We began collecting axioms in [Section 7.4.3](#index_split_000.html#filepos990242). The agent knows that the starting square contains no pit (¬*P*[1,1]) and no wumpus (¬*W*[1,1]). Furthermore, for each square, it knows that the square is breezy if and only if a neighboring square has a pit; and a square is smelly if and only if a neighboring square has a wumpus. Thus, we include a large collection of sentences of the following form:

> *B*[1,1] ⇔ (*P*[1,2] ⋁ *P*[2,1])

> *S*[1,1] ⇔ (*W*[1,2] ⋁ *W*[2,1])

> …

The agent also knows that there is exactly one wumpus. This is expressed in two parts. First, we have to say that there is *at least one* wumpus:

> *W*[1,1] ⋁ *W*[1,2] ⋁ … ⋁ *W*[4,3] ⋁ *W*[4,4].

Then, we have to say that there is *at most one* wumpus. For each pair of locations, we add a sentence saying that at least one of them must be wumpus-free:

> ¬*W*[1,1] ⋁ ¬*W*[1,2]

> ¬*W*[1,1] ⋁ ¬*W*[1,3]

> …

> ¬*W*[4,3] ⋁ ¬*W*[4,4].

So far, so good. Now let’s consider the agent’s percepts. If there is currently a stench, one might suppose that a proposition *Stench* should be added to the knowledge base. This is not quite right, however: if there was no stench at the previous time step, then ¬*Stench* would already be asserted, and the new assertion would simply result in a contradiction. The problem is solved when we realize that a percept asserts something *only about the current time*. Thus, if the time step (as supplied to MAKE\-PERCEPT\-SENTENCE in [Figure 7.1](#index_split_014.html#filepos949029)) is 4, then we add *Stench*⁴ to the knowledge base, rather than *Stench*—neatly avoiding any contradiction with ¬*Stench*³. The same goes for the breeze, bump, glitter, and scream percepts.

The idea of associating propositions with time steps extends to any aspect of the world that changes over time. For example, the initial knowledge base includes ![equ](images/00197.jpg)—the agent is in square \[1, 1\] at time 0—as well as *FacingEast*⁰, *HaveArrow*⁰, and *WumpusAlive*⁰. Weuse the word **fluent** (from the Latin *fluens*, flowing) to refer an aspect of the world that changes. “Fluent” is a synonym for “state variable,” in the sense described in the discussion of factored representations in [Section 2.4.7](#index_split_000.html#filepos271690) [on page 57](#index_split_009.html#filepos271341). Symbols associated with permanent aspects of the world do not need a time superscript and are sometimes called **atemporal variables**.

* * *

FLUENT

* * *

* * *

ATEMPORAL VARIABLE

* * *

We can connect stench and breeze percepts directly to the properties of the squares where they are experienced through the location fluent as follows.[^(10)](#index_split_015.html#filepos5583094) For any time step *t* and any square \[*x*, *y*\], we assert

> ![equ](images/00198.jpg)

Now, of course, we need axioms that allow the agent to keep track of fluents such as ![equ](images/00199.jpg). These fluents change as the result of actions taken by the agent, so, in the terminology of [Chapter 3](#index_split_000.html#filepos301685), we need to write down the **transition model** of the wumpus world as a set of logical sentences.

First, we need proposition symbols for the occurrences of actions. As with percepts, these symbols are indexed by time; thus, *Forward*⁰ means that the agent executes the *Forward* action at time 0. By convention, the percept for a given time step happens first, followed by the action for that time step, followed by a transition to the next time step.

To describe how the world changes, we can try writing **effect axioms** that specify the outcome of an action at the next time step. For example, if the agent is at location \[1, 1\] facing east at time 0 and goes *Forward*, the result is that the agent is in square \[2, 1\] and no longer is in \[1, 1\]:

> ![equ](images/00200.jpg)

* * *

EFFECT AXIOM

* * *

We would need one such sentence for each possible time step, for each of the 16 squares, and each of the four orientations. We would also need similar sentences for the other actions: *Grab, Shoot, Climb, TurnLeft*, and *TurnRight*.

Let us suppose that the agent does decide to move *Forward* at time 0 and asserts this fact into its knowledge base. Given the effect axiom in Equation (7.1), combined with the initial assertions about the state at time 0, the agent can now deduce that it is in \[2, 1\]. That is, ASK![equ](images/00201.jpg). So far, so good. Unfortunately, the news elsewhere is less good: if we ASK(*KB*, *HaveArrow*¹), the answer is *false*, that is, the agent cannot prove it still has the arrow; nor can it prove it *doesn’t* have it! The information has been lost because the effect axiom fails to state what remains *unchanged* as the result of an action. The need to do this gives rise to the **frame problem**.[^(11)](#index_split_015.html#filepos5583287) One possible solution to the frame problem would be to add **frame axioms** explicitly asserting all the propositions that remain the same. For example, for each time t we would have

> ![equ](images/00202.jpg)

* * *

FRAME PROBLEM

* * *

* * *

FRAME AXIOM

* * *

where we explicitly mention every proposition that stays unchanged from time *t* to time *t* + 1 under the action *Forward*. Although the agent now knows that it still has the arrow after moving forward and that the wumpus hasn’t died or come back to life, the proliferation of frame axioms seems remarkably inefficient. In a world with *m* different actions and *n* fluents, the set of frame axioms will be of size *O*(*mn*). This specific manifestation of the frame problem is sometimes called the **representational frame problem**. Historically, the problem was a significant one for AI researchers; we explore it further in the notes at the end of the chapter.

* * *

REPRESENTATIONAL

* * *

* * *

FRAME PROBLEM

* * *

The representational frame problem is significant because the real world has very many fluents, to put it mildly. Fortunately for us humans, each action typically changes no more than some small number *k* of those fluents—the world exhibits **locality**. Solving the representational frame problem requires defining the transition model with a set of axioms of size *O*(*mk*) rather than size *O*(*mn*). There is also an **inferential frame problem**: the problem of projecting forward the results of a t step plan of action in time *O*(*kt*) rather than *O*(*nt*).

The solution to the problem involves changing one’s focus from writing axioms about *actions* to writing axioms about *fluents*. Thus, for each fluent *F*, we will have an axiom that defines the truth value of *F*^(*t*+1) in terms of fluents (including *F* itself) at time t and the actions that may have occurred at time *t*. Now, the truth value of *F*^(*t*+1) can be set in one of two ways: either the action at time *t* causes *f* to be true at *t* + 1,or *f* was already true at time *t* and the action at time *t* does not cause it to be false. An axiom of this form is called a **successor-state axiom** and has this schema:

> ![equ](images/00203.jpg)

One of the simplest successor-state axioms is the one for *HaveArrow*. Because there is no action for reloading, the *ActionCausesF*^(*t*) part goes away and we are left with

> ![equ](images/00204.jpg)

For the agent’s location, the successor-state axioms are more elaborate. For example, ![equ](images/00205.jpg)is true if either (a) the agent moved *Forward* from \[1, 2\] when facing south, or from \[2, 1\] when facing west; or (b) ![equ](images/00206.jpg)was already true and the action did not cause movement (either because the action was not *Forward* or because the action bumped into a wall). Written out in propositional logic, this becomes

> ![equ](images/00207.jpg)

Exercise 7.26 asks you to write out axioms for the remaining wumpus world fluents.

Given a complete set of successor-state axioms and the other axioms listed at the beginning of this section, the agent will be able to ASK and answer any answerable question about the current state of the world. For example, in [Section 7.2](#index_split_000.html#filepos950662) the initial sequence of percepts and actions is

> ![equ](images/00208.jpg)

At this point, we have ![equ](images/00209.jpg), so the agent knows where it is. Moreover, ASK(*KB*, *W*[1,3]) = *true* and ASK(*KB*, *P*[3,1]) = *true*, so the agent has found the wumpus and one of the pits. The most important question for the agent is whether a square is OK to move into, that is, the square contains no pit nor live wumpus. It’s convenient to add axioms for this, having the form

> ![equ](images/00210.jpg)

Finally, ASK![equ](images/00211.jpg), so the square \[2, 2\] is OK to move into. In fact, given a sound and complete inference algorithm such as DPLL, the agent can answer any answerable question about which squares are OK—and can do so in just a few milliseconds for small-to-medium wumpus worlds.

Solving the representational and inferential frame problems is a big step forward, but a pernicious problem remains: we need to confirm that *all* the necessary preconditions of an action hold for it to have its intended effect. We said that the *Forward* action moves the agent ahead unless there is a wall in the way, but there are many other unusual exceptions that could cause the action to fail: the agent might trip and fall, be stricken with a heart attack, be carried away by giant bats, *etc.* Specifying all these exceptions is called the **qualification problem**. There is no complete solution within logic; system designers have to use good judgment in deciding how detailed they want to be in specifying their model, and what details they want to leave out. We will see in [Chapter 13](#index_split_015.html#filepos1915714) that probability theory allows us to summarize all the exceptions without explicitly naming them.

* * *

QUALIFICATION PROBLEM

* * *

#### **7.7.2 A hybrid agent**

The ability to deduce various aspects of the state of the world can be combined fairly straightforwardly with condition–action rules and with problem-solving algorithms from [Chapters 3](#index_split_000.html#filepos301685) and [4](#index_split_000.html#filepos513290) to produce a **hybrid agent** for the wumpus world. [Figure 7.20](#index_split_014.html#filepos1086803) shows one possible way to do this. The agent program maintains and updates a knowledge base as well as a current plan. The initial knowledge base contains the *atemporal* axioms—those that don’t depend on *t*, such as the axiom relating the breeziness of squares to the presence of pits. At each time step, the new percept sentence is added along with all the axioms that depend on *t*, such as the successor-state axioms. (The next section explains why the agent doesn’t need axioms for *future* time steps.) Then, the agent uses logical inference, by ASKing questions of the knowledge base, to work out which squares are safe and which have yet to be visited.

* * *

HYBRID AGENT

* * *

The main body of the agent program constructs a plan based on a decreasing priority of goals. First, if there is a glitter, the program constructs a plan to grab the gold, follow a route back to the initial location, and climb out of the cave. Otherwise, if there is no current plan, the program plans a route to the closest safe square that it has not visited yet, making sure the route goes through only safe squares. Route planning is done with *A*^(\*) search, not with ASK. If there are no safe squares to explore, the next step—if the agent still has an arrow—is to try to make a safe square by shooting at one of the possible wumpus locations. These are determined by asking where ASK(*KB*, ¬*W[x,y]*) is false—that is, where it is *not* known that there is *not* a wumpus. The function PLAN\-SHOT (not shown) uses PLAN\-ROUTE to plan a sequence of actions that will line up this shot. If this fails, the program looks for a square to explore that is not provably unsafe—that is, a square for which ![equ](images/00212.jpg)returns false. If there is no such square, then the mission is impossible and the agent retreats to \[1, 1\] and climbs out of the cave.

#### **7.7.3 Logical state estimation**

The agent program in [Figure 7.20](#index_split_014.html#filepos1086803) works quite well, but it has one major weakness: as time goes by, the computational expense involved in the calls to ASK goes up and up. This happens mainly because the required inferences have to go back further and further in time and involve more and more proposition symbols. Obviously, this is unsustainable—we cannot have an agent whose time to process each percept grows in proportion to the length of its life! What we really need is a *constant* update time—that is, independent of *t*. The obvious answer is to save, or **cache**, the results of inference, so that the inference process at the next time step can build on the results of earlier steps instead of having to start again from scratch.

* * *

CACHING

* * *

As we saw in [Section 4.4](#index_split_000.html#filepos575701), the past history of percepts and all their ramifications can be replaced by the **belief state**—that is, some representation of the set of all possible current states of the world.[^(12)](#index_split_015.html#filepos5583713) The process of updating the belief state as new percepts arrive is called **state estimation**. Whereas in [Section 4.4](#index_split_000.html#filepos575701) the belief state was an explicit list of states, here we can use a logical sentence involving the proposition symbols associated with the current time step, as well as the atemporal symbols. For example, the logical sentence

> ![equ](images/00212.jpg)

represents the set of all states at time 1 in which the wumpus is alive, the agent is at \[2, 1\], that square is breezy, and there is a pit in \[3, 1\] or \[2, 2\] or both.

Maintaining an exact belief state as a logical formula turns out not to be easy. If there are *n* fluent symbols for time *t*, then there are 2^(*n*) possible states—that is, assignments of truth values to those symbols. Now, the set of belief states is the powerset (set of all subsets) of the set of physical states. There are 2^(*n*) physical states, hence 2^(2*n*) belief states. Even if we used the most compact possible encoding of logical formulas, with each belief state represented by a unique binary number, we would need numbers with log[2](2^(2*n*))=2^(*n*) bits to label the current belief state. That is, exact state estimation may require logical formulas whose size is exponential in the number of symbols.

> ![image](images/00213.jpg)

> **Figure 7.20** A hybrid agent program for the wumpus world. It uses a propositional knowledge base to infer the state of the world, and a combination of problem-solving search and domain-specific code to decide what actions to take.

One very common and natural scheme for *approximate* state estimation is to represent belief states as conjunctions of literals, that is, 1-CNF formulas. To do this, the agent program simply tries to prove *X^t* and ¬*X^t* for each symbol *X^t* (as well as each atemporal symbol whose truth value is not yet known), given the belief state at *t* − 1. The conjunction of provable literals becomes the new belief state, and the previous belief state is discarded.

> ![image](images/00214.jpg)

> **Figure 7.21** Depiction of a 1-CNF belief state (bold outline) as a simply representable, conservative approximation to the exact (wiggly) belief state (shaded region with dashed outline). Each possible world is shown as a circle; the shaded ones are consistent with all the percepts.

![image](images/00006.jpg)

It is important to understand that this scheme may lose some information as time goes along. For example, if the sentence in Equation (7.4) were the true belief state, then neither *P*[3,1] nor *P*[2,2] would be provable individually and neither would appear in the 1-CNF belief state. (Exercise 7.27 explores one possible solution to this problem.) On the other hand, because every literal in the 1-CNF belief state is proved from the previous belief state, and the initial belief state is a true assertion, we know that entire 1-CNF belief state must be true. Thus, *the set of possible states represented by the 1-CNF belief state includes all states that are in fact possible given the full percept history.* As illustrated in [Figure 7.21](#index_split_014.html#filepos1087865), the 1-CNF belief state acts as a simple outer envelope, or **conservative approximation**, around the exact belief state. We see this idea of conservative approximations to complicated sets as a recurring theme in many areas of AI.

* * *

CONSERVATIVE APPROXIMATION

* * *

#### **7.7.4 Making plans by propositional inference**

The agent in [Figure 7.20](#index_split_014.html#filepos1086803) uses logical inference to determine which squares are safe, but uses A\* search to make plans. In this section, we show how to make plans by logical inference. The basic idea is very simple:

> 1\. Construct a sentence that includes

> (a) *Init*⁰, a collection of assertions about the initial state;

> (b) *Transition*¹,…, *Transition*^(*t*), the successor-state axioms for all possible actions at each time up to some maximum time *t*;

> (c) the assertion that the goal is achieved at time *t*: *HaveGold^t* ⋀ *ClimbedOut^t*.

> 2\. Present the whole sentence to a SAT solver. If the solver finds a satisfying model, then the goal is achievable; if the sentence is unsatisfiable, then the planning problem is impossible.

> 3\. Assuming a model is found, extract from the model those variables that represent actions and are assigned *true*. Together they represent a plan to achieve the goals.

A propositional planning procedure, SATPLAN, is shown in [Figure 7.22](#index_split_014.html#filepos1092191). It implements the basic idea just given, with one twist. Because the agent does not know how many steps it will take to reach the goal, the algorithm tries each possible number of steps *t*, up to some maximum conceivable plan length *T*[max]. In this way, it is guaranteed to find the shortest plan if one exists. Because of the way SATPLAN searches for a solution, this approach cannot be used in a partially observable environment; SATPLAN would just set the unobservable variables to the values it needs to create a solution.

> ![image](images/00215.jpg)

> **Figure 7.22** The SATPLAN algorithm. The planning problem is translated into a CNF sentence in which the goal is asserted to hold at a fixed time step t and axioms are included for each time step up to *t*. If the satisfiability algorithm finds a model, then a plan is extracted by looking at those proposition symbols that refer to actions and are assigned *true* in the model. If no model exists, then the process is repeated with the goal moved one step later.

The key step in using SATPLAN is the construction of the knowledge base. It might seem, on casual inspection, that the wumpus world axioms in [Section 7.7.1](#index_split_000.html#filepos1065941) suffice for steps 1(a) and 1(b) above. There is, however, a significant difference between the requirements for entailment (as tested by ASK) and those for satisfiability. Consider, for example, the agent’s location, initially \[1, 1\], and suppose the agent’s unambitious goal is to be in \[2, 1\] at time 1. The initial knowledge base contains ![equ](images/00216.jpg)and the goal is ![equ](images/00217.jpg). Using ASK, we can prove ![equ](images/00217.jpg)if *Forward*⁰ is asserted, and, reassuringly, we cannot prove ![equ](images/00217.jpg)if, say, *Shoot*⁰ is asserted instead. Now, SATPLAN will find the plan \[*Forward*⁰\]; so far, so good. Unfortunately, SATPLAN also finds the plan \[*Shoot*⁰\]. How could this be? To find out, we inspect the model that SATPLAN constructs: it includes the assignment ![equ](images/00218.jpg), that is, the agent can be in \[2, 1\] at time 1 by being there at time 0 and shooting. One might ask, “Didn’t we say the agent is in \[1, 1\] at time 0?” Yes, we did, but we didn’t tell the agent that it can’t be in two places at once! For entailment, ![equ](images/00218.jpg)is unknown and cannot, therefore, be used in a proof; for satisfiability, on the other hand, ![equ](images/00218.jpg)is unknown and can, therefore, be set to whatever value helps to make the goal true. For this reason, SATPLAN is a good debugging tool for knowledge bases because it reveals places where knowledge is missing. In this particular case, we can fix the knowledge base by asserting that, at each time step, the agent is in exactly one location, using a collection of sentences similar to those used to assert the existence of exactly one wumpus. Alternatively, we can assert ![equ](images/00219.jpg)for all locations other than \[1, 1\]; the successor-state axiom for location takes care of subsequent time steps. The same fixes also work to make sure the agent has only one orientation.

SATPLAN has more surprises in store, however. The first is that it finds models with impossible actions, such as shooting with no arrow. To understand why, we need to look more carefully at what the successor-state axioms (such as Equation (7.3)) say about actions whose preconditions are not satisfied. The axioms *do* predict correctly that nothing will happen when such an action is executed (see Exercise 10.14), but they do *not* say that the action cannot be executed! To avoid generating plans with illegal actions, we must add **precondition axioms** stating that an action occurrence requires the preconditions to be satisfied.[^(13)](#index_split_015.html#filepos5583985) For example, we need to say, for each time *t*, that

> ![equ](images/00220.jpg)

* * *

PRECONDITION AXIOMS

* * *

This ensures that if a plan selects the *Shoot* action at any time, it must be the case that the agent has an arrow at that time.

SATPLAN’s second surprise is the creation of plans with multiple simultaneous actions. For example, it may come up with a model in which both *Forward*⁰ and *Shoot*⁰ are true, which is not allowed. To eliminate this problem, we introduce **action exclusion axioms**: for every pair of actions ![equ](images/00221.jpg)and ![equ](images/00222.jpg)we add the axiom

> ![equ](images/00223.jpg)

* * *

ACTION EXCLUSION AXIOM

* * *

It might be pointed out that walking forward and shooting at the same time is not so hard to do, whereas, say, shooting and grabbing at the same time is rather impractical. By imposing action exclusion axioms only on pairs of actions that really do interfere with each other, we can allow for plans that include multiple simultaneous actions—and because SATPLAN finds the shortest legal plan, we can be sure that it will take advantage of this capability.

To summarize, SATPLAN finds models for a sentence containing the initial state, the goal, the successor-state axioms, the precondition axioms, and the action exclusion axioms. It can be shown that this collection of axioms is sufficient, in the sense that there are no longer any spurious “solutions.” Any model satisfying the propositional sentence will be a valid plan for the original problem. Modern SAT-solving technology makes the approach quite practical. For example, a DPLL-style solver has no difficulty in generating the 11-step solution for the wumpus world instance shown in [Figure 7.2](#index_split_014.html#filepos956323).

This section has described a declarative approach to agent construction: the agent works by a combination of asserting sentences in the knowledge base and performing logical inference. This approach has some weaknesses hidden in phrases such as “for each time *t*” and “for each square \[*x*, *y*\].” For any practical agent, these phrases have to be implemented by code that generates instances of the general sentence schema automatically for insertion into the knowledge base. For a wumpus world of reasonable size—one comparable to a smallish computer game—we might need a 100 × 100 board and 1000 time steps, leading to knowledge bases with tens or hundreds of millions of sentences. Not only does this become rather impractical, but it also illustrates a deeper problem: we know something about the wumpus world—namely, that the “physics” works the same way across all squares and all time steps—that we cannot express directly in the language of propositional logic. To solve this problem, we need a more expressive language, one in which phrases like “for each time *t*” and “for each square \[*x*, *y*\]” can be written in a natural way. First-order logic, described in [Chapter 8](#index_split_000.html#filepos1149778), is such a language; in first-order logic a wumpus world of any size and duration can be described in about ten sentences rather than ten million or ten trillion.

### 7.8 SUMMARY

We have introduced knowledge-based agents and have shown how to define a logic with which such agents can reason about the world. The main points are as follows:

> • Intelligent agents need knowledge about the world in order to reach good decisions.

> • Knowledge is contained in agents in the form of **sentences** in a **knowledge representation language** that are stored in a **knowledge base**.

> • A knowledge-based agent is composed of a knowledge base and an inference mechanism. It operates by storing sentences about the world in its knowledge base, using the inference mechanism to infer new sentences, and using these sentences to decide what action to take.

> • A representation language is defined by its **syntax**, which specifies the structure of sentences, and its **semantics**, which defines the **truth** of each sentence in each **possible world** or **model**.

> • The relationship of **entailment** between sentences is crucial to our understanding of reasoning. A sentence α entails another sentence β if β is true in all worlds where α is true. Equivalent definitions include the **validity** of the sentence α ⇒ β and the **unsatisfiability** of the sentence α ⋀ ¬β.

> • Inference is the process of deriving new sentences from old ones. **Sound** inference algorithms derive *only* sentences that are entailed; **complete** algorithms derive *all* sentences that are entailed.

> • **Propositional logic** is a simple language consisting of **proposition symbols** and **logical connectives**. It can handle propositions that are known true, known false, or completely unknown.

> • The set of possible models, given a fixed propositional vocabulary, is finite, so entailment can be checked by enumerating models. Efficient **model-checking** inference algorithms for propositional logic include backtracking and local search methods and can often solve large problems quickly.

> • **Inference rules** are patterns of sound inference that can be used to find proofs. The **resolution** rule yields a complete inference algorithm for knowledge bases that are expressed in **conjunctive normal form**. **Forward chaining** and **backward chaining** are very natural reasoning algorithms for knowledge bases in **Horn form**.

> • **Local search** methods such as WALKSAT can be used to find solutions. Such algorithms are sound but not complete.

> • Logical **state estimation** involves maintaining a logical sentence that describes the set of possible states consistent with the observation history. Each update step requires inference using the transition model of the environment, which is built from **successor-state axioms** that specify how each **fluent** changes.

> • Decisions within a logical agent can be made by SAT solving: finding possible models specifying future action sequences that reach the goal. This approach works only for fully observable or sensorless environments.

> • Propositional logic does not scale to environments of unbounded size because it lacks the expressive power to deal concisely with time, space, and universal patterns of relationships among objects.

### BIBLIOGRAPHICAL AND HISTORICAL NOTES

John McCarthy’s paper “Programs with Common Sense” (McCarthy, 1958, 1968) promulgated the notion of agents that use logical reasoning to mediate between percepts and actions. It also raised the flag of declarativism, pointing out that telling an agent what it needs to know is an elegant way to build software. Allen Newell’s (1982) article “The Knowledge Level”makes the case that rational agents can be described and analyzed at an abstract level defined by the knowledge they possess rather than the programs they run. The declarative and procedural approaches to AI are analyzed in depth by Boden (1977). The debate was revived by, among others, Brooks (1991) and Nilsson (1991), and continues to this day (Shaparau **et al.**, 2008). Meanwhile, the declarative approach has spread into other areas of computer science such as networking (Loo **et al.**, 2006).

Logic itself had its origins in ancient Greek philosophy and mathematics. Various logical principles—principles connecting the syntactic structure of sentences with their truth and falsity, with their meaning, or with the validity of arguments in which they figure—are scattered in the works of Plato. The first known systematic study of logic was carried out by Aristotle, whose work was assembled by his students after his death in 322 B.C. as a treatise called the *Organon*. Aristotle’s **syllogisms** were what we would now call inference rules. Although the syllogisms included elements of both propositional and first-order logic, the system as a whole lacked the compositional properties required to handle sentences of arbitrary complexity.

* * *

SYLLOGISM

* * *

The closely related Megarian and Stoic schools (originating in the fifth century B.C. and continuing for several centuries thereafter) began the systematic study of the basic logical connectives. The use of truth tables for defining connectives is due to Philo of Megara. The Stoics took five basic inference rules as valid without proof, including the rule we now call Modus Ponens. They derived a number of other rules from these five, using, among other principles, the deduction theorem ([page 249](#index_split_014.html#filepos997568)) and were much clearer about the notion of proof than was Aristotle. A good account of the history of Megarian and Stoic logic is given by Benson Mates (1953).

The idea of reducing logical inference to a purely mechanical process applied to a formal language is due to Wilhelm Leibniz (1646–1716), although he had limited success in implementing the ideas. George Boole (1847) introduced the first comprehensive and workable system of formal logic in his book *The Mathematical Analysis of Logic*. Boole’s logic was closely modeled on the ordinary algebra of real numbers and used substitution of logically equivalent expressions as its primary inference method. Although Boole’s system still fell short of full propositional logic, it was close enough that other mathematicians could quickly fill in the gaps. Schröder (1877) described conjunctive normal form, while Horn form was introduced much later by Alfred Horn (1951). The first comprehensive exposition of modern propositional logic (and first-order logic) is found in Gottlob Frege’s (1879) *Begriffschrift* (“Concept Writing” or “Conceptual Notation”).

The first mechanical device to carry out logical inferences was constructed by the third Earl of Stanhope (1753–1816). The Stanhope Demonstrator could handle syllogisms and certain inferences in the theory of probability. William Stanley Jevons, one of those who improved upon and extended Boole’s work, constructed his “logical piano” in 1869 to perform inferences in Boolean logic. An entertaining and instructive history of these and other early mechanical devices for reasoning is given by Martin Gardner (1968). The first published computer program for logical inference was the Logic Theorist of Newell, Shaw, and Simon (1957). This program was intended to model human thought processes. Martin Davis (1957) had actually designed a program that came up with a proof in 1954, but the Logic Theorist’s results were published slightly earlier.

Truth tables as a method of testing validity or unsatisfiability in propositional logic were introduced independently by Emil Post (1921) and Ludwig Wittgenstein (1922). In the 1930s, a great deal of progress was made on inference methods for first-order logic. In particular, Gödel (1930) showed that a complete procedure for inference in first-order logic could be obtained via a reduction to propositional logic, using Herbrand’s theorem (Herbrand, 1930). We take up this history again in [Chapter 9](#index_split_015.html#filepos1300686); the important point here is that the development of efficient propositional algorithms in the 1960s was motivated largely by the interest of mathematicians in an effective theorem prover for first-order logic. The Davis–Putnam algorithm (Davis and Putnam, 1960) was the first effective algorithm for propositional resolution but was in most cases much less efficient than the DPLL backtracking algorithm introduced two years later (1962). The full resolution rule and a proof of its completeness appeared in a seminal paper by J. A. Robinson (1965), which also showed how to do first-order reasoning without resort to propositional techniques.

Stephen Cook (1971) showed that deciding satisfiability of a sentence in propositional logic (the SAT problem) is NP-complete. Since deciding entailment is equivalent to deciding unsatisfiability, it is co-NP-complete. Many subsets of propositional logic are known for which the satisfiability problem is polynomially solvable; Horn clauses are one such subset. The linear-time forward-chaining algorithm for Horn clauses is due to Dowling and Gallier (1984), who describe their algorithm as a dataflow process similar to the propagation of signals in a circuit.

Early theoretical investigations showed that DPLL has polynomial average-case complexity for certain natural distributions of problems. This potentially exciting fact became less exciting when Franco and Paull (1983) showed that the same problems could be solved in constant time simply by guessing random assignments. The random-generation method described in the chapter produces much harder problems. Motivated by the empirical success of local search on these problems, Koutsoupias and Papadimitriou (1992) showed that a simple hill-climbing algorithm can solve *almost all* satisfiability problem instances very quickly, suggesting that hard problems are rare. Moreover, Schöning (1999) exhibited a randomized hill-climbing algorithm whose *worst-case* expected run time on 3-SAT problems (that is, satisfiability of 3-CNF sentences) is *O*(1.333^(*n*))—still exponential, but substantially faster than previous worst-case bounds. The current record is *O*(1.324^(*n*)) (Iwama and Tamaki, 2004). Achlioptas **et al.** (2004) and Alekhnovich **et al.** (2005) exhibit families of 3-SAT instances for which all known DPLL-like algorithms require exponential running time.

On the practical side, efficiency gains in propositional solvers have been marked. Given ten minutes of computing time, the original DPLL algorithm in 1962 could only solve problems with no more than 10 or 15 variables. By 1995 the SATZ solver (Li and Anbulagan, 1997) could handle 1,000 variables, thanks to optimized data structures for indexing variables. Two crucial contributions were the **watched literal** indexing technique of Zhang and Stickel (1996), which makes unit propagation very efficient, and the introduction of clause (i.e., constraint) learning techniques from the CSP community by Bayardo and Schrag (1997). Using these ideas, and spurred by the prospect of solving industrial-scale circuit verification problems, Moskewicz **et al.** (2001) developed the CHAFF solver, which could handle problems with millions of variables. Beginning in 2002, SAT competitions have been held regularly; most of the winning entries have either been descendants of CHAFF or have used the same general approach. RSAT (Pipatsrisawat and Darwiche, 2007), the 2007 winner, falls in the latter category. Also noteworthy is MINISAT (Een and Sörensson, 2003), an open-source implementation available at `http://minisat.se` that is designed to be easily modified and improved. The current landscape of solvers is surveyed by Gomes **et al.** (2008).

Local search algorithms for satisfiability were tried by various authors throughout the 1980s; all of the algorithms were based on the idea of minimizing the number of unsatisfied clauses (Hansen and Jaumard, 1990). A particularly effective algorithm was developed by Gu (1989) and independently by Selman **et al.** (1992), who called it GSAT and showed that it was capable of solving a wide range of very hard problems very quickly. The WALKSAT algorithm described in the chapter is due to Selman **et al.** (1996).

The “phase transition” in satisfiability of random k-SAT problems was first observed by Simon and Dubois (1989) and has given rise to a great deal of theoretical and empirical research—due, in part, to the obvious connection to phase transition phenomena in statistical physics. Cheeseman **et al.** (1991) observed phase transitions in several CSPs and conjecture that all NP-hard problems have a phase transition. Crawford and Auton (1993) located the 3-SAT transition at a clause/variable ratio of around 4.26, noting that this coincides with a sharp peak in the run time of their SAT solver. Cook and Mitchell (1997) provide an excellent summary of the early literature on the problem.

The current state of theoretical understanding is summarized by Achlioptas (2009). The **satisfiability threshold conjecture** states that, for each *k*, there is a sharp satisfiability threshold *r*[*k*], such that as the number of variables *n* → ∞, instances below the threshold are *satisfiable* with probability 1, while those above the threshold are *unsatisfiable* with probability 1. The conjecture was not quite proved by Friedgut (1999): a sharp threshold exists but its location might depend on *n* even as *n* → ∞. Despite significant progress in asymptotic analysis of the threshold location for large *k* (Achlioptas and Peres, 2004; Achlioptas **et al.**, 2007), all that can be proved for *k* = 3 is that it lies in the range \[3.52,4.51\]. Current theory suggests that a peak in the run time of a SAT solver is not necessarily related to the satisfiability threshold, but instead to a phase transition in the solution distribution and structure of SAT instances. Empirical results due to Coarfa **et al.** (2003) support this view. In fact, algorithms such as **survey propagation** (Parisi and Zecchina, 2002; Maneva **et al.**, 2007) take advantage of special properties of random SAT instances near the satisfiability threshold and greatly outperform general SAT solvers on such instances.

* * *

SATISFIABILITY THRESHOLD CONJECTURE

* * *

* * *

SURVEY PROPAGATION

* * *

The best sources for information on satisfiability, both theoretical and practical, are the *Handbook of Satisfiability* (Biere **et al.**, 2009) and the regular *International Conferences on Theory and Applications of Satisfiability Testing*, known as SAT.

The idea of building agents with propositional logic can be traced back to the seminal paper of McCulloch and Pitts (1943), which initiated the field of neural networks. Contrary to popular supposition, the paper was concerned with the implementation of a Boolean circuit-based agent design in the brain. Circuit-based agents, which perform computation by propagating signals in hardware circuits rather than running algorithms in general-purpose computers, have received little attention in AI, however. The most notable exception is the work of Stan Rosenschein (Rosenschein, 1985; Kaelbling and Rosenschein, 1990), who developed ways to compile circuit-based agents from declarative descriptions of the task environment. (Rosenschein’s approach is described at some length in the second edition of this book.) The work of Rod Brooks (1986, 1989) demonstrates the effectiveness of circuit-based designs for controlling robots—a topic we take up in [Chapter 25](#index_split_015.html#filepos3777962). Brooks (1991) argues that circuit-based designs are *all* that is needed for AI—that representation and reasoning are cumbersome, expensive, and unnecessary. In our view, neither approach is sufficient by itself. Williams **et al.** (2003) show how a hybrid agent design not too different from our wumpus agent has been used to control NASA spacecraft, planning sequences of actions and diagnosing and recovering from faults.

The general problem of keeping track of a partially observable environment was introduced for state-based representations in [Chapter 4](#index_split_000.html#filepos513290). Its instantiation for propositional representations was studied by Amir and Russell (2003), who identified several classes of environments that admit efficient state-estimation algorithms and showed that for several other classes the problem is intractable. The **temporal-projection** problem, which involves determining what propositions hold true after an action sequence is executed, can be seen as a special case of state estimation with empty percepts. Many authors have studied this problem because of its importance in planning; some important hardness results were established by Liberatore (1997). The idea of representing a belief state with propositions can be traced to Wittgenstein (1922).

* * *

TEMPORAL-PROJECTION

* * *

Logical state estimation, of course, requires a logical representation of the effects of actions—a key problem in AI since the late 1950s. The dominant proposal has been the **situation calculus** formalism (McCarthy, 1963), which is couched within first-order logic. We discuss situation calculus, and various extensions and alternatives, in [Chapters 10](#index_split_015.html#filepos1477055) and [12](#index_split_015.html#filepos1750417). The approach taken in this chapter—using temporal indices on propositional variables—is more restrictive but has the benefit of simplicity. The general approach embodied in the SATPLAN algorithm was proposed by Kautz and Selman (1992). Later generations of SATPLAN were able to take advantage of the advances in SAT solvers, described earlier, and remain among the most effective ways of solving difficult problems (Kautz, 2006).

The **frame problem** was first recognized by McCarthy and Hayes (1969). Many researchers considered the problem unsolvable within first-order logic, and it spurred a great deal of research into nonmonotonic logics. Philosophers from Dreyfus (1972) to Crockett (1994) have cited the frame problem as one symptom of the inevitable failure of the entire AI enterprise. The solution of the frame problem with successor-state axioms is due to Ray Reiter (1991). Thielscher (1999) identifies the inferential frame problem as a separate idea and provides a solution. In retrospect, one can see that Rosenschein’s (1985) agents were using circuits that implemented successor-state axioms, but Rosenschein did not notice that the frame problem was thereby largely solved. Foo (2001) explains why the discrete-event control theory models typically used by engineers do not have to explicitly deal with the frame problem: because they are dealing with prediction and control, not with explanation and reasoning about counterfactual situations.

Modern propositional solvers have wide applicability in industrial applications. The application of propositional inference in the synthesis of computer hardware is now a standard technique having many large-scale deployments (Nowick **et al.**, 1993). The SATMC satisfiability checker was used to detect a previously unknown vulnerability in a Web browser user sign-on protocol (Armando **et al.**, 2008).

The wumpus world was invented by Gregory Yob (1975). Ironically, Yob developed it because he was bored with games played on a rectangular grid: the topology of his original wumpus world was a dodecahedron, and we put it back in the boring old grid. Michael Genesereth was the first to suggest that the wumpus world be used as an agent testbed.

### EXERCISES

**7.1** Suppose the agent has progressed to the point shown in [Figure 7.4](#index_split_014.html#filepos960239)(a), [page 239](#index_split_014.html#filepos959083), having perceived nothing in \[1,1\], a breeze in \[2,1\], and a stench in \[1,2\], and is now concerned with the contents of \[1,3\], \[2,2\], and \[3,1\]. Each of these can contain a pit, and at most one can contain a wumpus. Following the example of [Figure 7.5](#index_split_014.html#filepos965424), construct the set of possible worlds. (You should find 32 of them.) Mark the worlds in which the KB is true and those in which each of the following sentences is true:

> α[2] = “There is no pit in \[2,2\].”

> α[3] = “There is a wumpus in \[1,3\].”

Hence show that *KB* ⊨ α[2] and *KB* ⊨ α[3].

**7.2** (Adapted from Barwise and Etchemendy (1993).) Given the following, can you prove that the unicorn is mythical? How about magical? Horned?

> If the unicorn is mythical, then it is immortal, but if it is not mythical, then it is a mortal mammal. If the unicorn is either immortal or a mammal, then it is horned. The unicorn is magical if it is horned.

**7.3** Consider the problem of deciding whether a propositional logic sentence is true in a given model.

> **a**. Write a recursive algorithm PL-TRUE?(*s*, *m*) that returns *true* if and only if the sentence *s* is true in the model *m* (where *m* assigns a truth value for every symbol in *s*). The algorithm should run in time linear in the size of the sentence. (Alternatively, use a version of this function from the online code repository.)

> **b**. Give three examples of sentences that can be determined to be true or false in a *partial* model that does not specify a truth value for some of the symbols.

> **c**. Show that the truth value (if any) of a sentence in a partial model cannot be determined efficiently in general.

> **d**. Modify your PL-TRUE? algorithm so that it can sometimes judge truth from partial models, while retaining its recursive structure and linear run time. Give three examples of sentences whose truth in a partial model is *not* detected by your algorithm.

> **e**. Investigate whether the modified algorithm makes TT-ENTAILS? more efficient.

**7.4** Which of the following are correct?

> **a**. *False* ⊨ *True*.

> **b**. *True* ⊨ *False*.

> **c**. (*A* ⋀ *B*) ⊨ (*A* ⇔ *B*).

> **d**. *A* ⇔ *B* ⊨ *A* ⋁ *B*.

> **e**. *A* ⇔ *B* ⊨ ¬*A* ⋁ *B*.

> **f**. (*A* ⋀ *B*) ⇒ *C* ⊨ (*A* ⇒ *C*) ⋁ (*B* ⇒ *C*).

> **g**. (*C* ⋁ (¬*A* ⋀¬*B*)) ≡ ((*A* ⇒ *C*) ⋀ (*B* ⇒ *C*)).

> **h**. (*A* ⋁ *B*) ⋀ (¬*C* ⋁ ¬*D* ⋁ *E*) ⊨ (*A* ⋁ *B*).

> **i**. (*A* ⋁ *B*) ⋀ (¬*C* ⋁ ¬*D* ⋁ *E*) ⊨ (*A* ⋁ *B*) ⋀ (¬*D* ⋁ *E*).

> **j**. (*A* ⋁ *B*) ⋀¬(*A* ⇒ *B*) is satisfiable.

> **k**. (*A* ⇔ *B*) ⋀ (¬*A* ⋁ *B*) is satisfiable.

> **l**. (*A* ⇔ *B*) ⇔ *C* has the same number of models as (*A* ⇔ *B*) for any fixed set of proposition symbols that includes *A*, *B*, *C*.

**7.5** Prove each of the following assertions:

> **a**. α is valid if and only if *True* ⊨ α.

> **b**. Forany α, *False* ⊨ α.

> **c**. α ⊨ β if and only if the sentence (α ⇒ β) is valid.

> **d**. α ≡ β if and only if the sentence (α ⇔ β) is valid.

> **e**. α ⊨ β if and only if the sentence (α ⋀ ¬β) is unsatisfiable.

**7.6** Prove, or find a counterexample to, each of the following assertions:

> **a**. If α ⊨ γ or β ⊨ γ (or both) then (α ⋀ β) ⊨ γ

> **b**. If α ⊨ (β ⋀ γ) then α ⊨ β and α ⊨ γ.

> **c**. If α ⊨ (β ⋁ γ) then α ⊨ β or α ⊨ γ (or both).

**7.7** Consider a vocabulary with only four propositions, *A*, *B*, *C*,and *D*. How many models are there for the following sentences?

> **a**. *B* ⋁ *C*.

> **b**. ¬*A* ⋁ ¬*B* ⋁ ¬*C* ⋁ ¬*D*.

> **c**. (*A* ⇒ *B*) ⋀ *A* ⋀ ¬*B* ⋀ *C* ⋀ *D*.

**7.8** We have defined four binary logical connectives.

> **a**. Are there any others that might be useful?

> **b**. How many binary connectives can there be?

> **c**. Why are some of them not very useful?

**7.9** Using a method of your choice, verify each of the equivalences in [Figure 7.11](#index_split_014.html#filepos997575) ([page 249](#index_split_014.html#filepos997568)).

**7.10** Decide whether each of the following sentences is valid, unsatisfiable, or neither. Verify your decisions using truth tables or the equivalence rules of [Figure 7.11](#index_split_014.html#filepos997575) ([page 249](#index_split_014.html#filepos997568)).

> **a**. *Smoke* ⇒ *Smoke*

> **b**. *Smoke* ⇒ *Fire*

> **c**. (*Smoke* ⇒ *Fire*) ⇒ (¬*Smoke* ⇒ ¬*Fire*)

> **d**. *Smoke* ⋁ *Fire* ⋁ ¬*Fire*

> **e**. ((*Smoke* ⋀ *Heat*) ⇒ *Fire*) ⇔ ((*Smoke* ⇒ *Fire*) ⋁ (*Heat* ⇒ *Fire*))

> **f**. (*Smoke* ⇒ *Fire*) ⇒ ((*Smoke* ⋀ *Heat*) ⇒ *Fire*)

> **g**. *Big* ⋁ *Dumb* ⋁ (*Big* ⇒ *Dumb*)

**7.11** Any propositional logic sentence is logically equivalent to the assertion that each possible world in which it would be false is not the case. From this observation, prove that any sentence can be written in CNF.

**7.12** Use resolution to prove the sentence ¬*A*⋀ ¬*B* from the clauses in Exercise 7.20.

**7.13** This exercise looks into the relationship between clauses and implication sentences.

> **a**. Show that the clause (¬*P*[1] ⋁ … ⋁ ¬*P*[*m*] ⋁ *Q*) is logically equivalent to the implication sentence (*P*[1] ⋀ … ⋀ *P*[*m*]) ⇒ Q.

> **b**. Show that every clause (regardless of the number of positive literals) can be written in the form (*P*[1] ⋀ … ⋀ *P*[*m*]) ⇒ (*Q*[1] ⋁ … ⋁ *Q*[*n*]), where the *Ps* and *Q*s are proposition symbols. A knowledge base consisting of such sentences is in **implicative normal form** or **Kowalski form** (Kowalski, 1979).

* * *

IMPLICATIVE NORMAL FORM

* * *

> **c**. Write down the full resolution rule for sentences in implicative normal form.

**7.14** According to some political pundits, a person who is radical (*R*) is electable (*E*) if he/she is conservative (*C*), but otherwise is not electable.

> **a**. Which of the following are correct representations of this assertion?

> (i) (*R* ⋀ *E*) ⇔ *C*

> (ii) *R* ⇒ (*E* ⇔ *C*)

> (iii) *R* ⇒ ((*C* ⇒ *E*) ⋁ ¬*E*)

> **b**. Which of the sentences in (a) can be expressed in Horn form?

**7.15** This question considers representing satisfiability (SAT) problems as CSPs.

> **a**. Draw the constraint graph corresponding to the SAT problem

> (¬*X*[1] ⋁ *X*[2]) ⋀ (¬*X*[2] ⋁ *X*[3]) ⋀… ⋀ (¬*X*[*n*−1] ⋁ *X*[*n*])

> for the particular case *n* = 5.

> **b**. How many solutions are there for this general SAT problem as a function of *n*?

> **c**. Suppose we apply BACKTRACKING\-SEARCH ([page 215](#index_split_013.html#filepos865606)) to find *all* solutions to a SAT CSP of the type given in (*a*). (To find *all* solutions to a CSP, we simply modify the basic algorithm so it continues searching after each solution is found.) Assume that variables are ordered *X*[1],…, *X*[*n*] and false is ordered before true. How much time will the algorithm take to terminate? (Write an *O*(⋅) expression as a function of *n*.)

> **d**. We know that SAT problems in Horn form can be solved in linear time by forward chaining (unit propagation). We also know that every tree-structured binary CSP with discrete, finite domains can be solved in time linear in the number of variables ([Section 6.5](#index_split_000.html#filepos895328)). Are these two facts connected? Discuss.

**7.16** Explain why every nonempty propositional clause, by itself, is satisfiable. Prove rigorously that every set of five 3-SAT clauses is satisfiable, provided that each clause mentions exactly three distinct variables. What is the smallest set of such clauses that is unsatisfiable? Construct such a set.

**7.17** A propositional *2-CNF* expression is a conjunction of clauses, each containing *exactly 2* literals, e.g.,

> (*A* ⋁ *B*) ⋀ (¬*A* ⋁ *C*) ⋀ (¬*B* ⋁ *D*) ⋀ (¬*C* ⋁ *G*) ⋀ (¬*D* ⋁ *G*).

> **a**. Prove using resolution that the above sentence entails *G*.

> **b**. Two clauses are *semantically distinct* if they are not logically equivalent. How many semantically distinct 2-CNF clauses can be constructed from *n* proposition symbols?

> **c**. Using your answer to (*b*), prove that propositional resolution always terminates in time polynomial in *n* given a 2-CNF sentence containing no more than *n* distinct symbols.

> **d**. Explain why your argument in (c) does not apply to 3-CNF.

**7.18** Consider the following sentence:

> \[(*Food* ⇒ *Party*) ⋁ (*Drinks* ⇒ *Party*)\] ⇒ \[(*Food* ⋀ *Drinks*) ⇒ *Party*\].

> **a**. Determine, using enumeration, whether this sentence is valid, satisfiable (but not valid), or unsatisfiable.

> **b**. Convert the left-hand and right-hand sides of the main implication into CNF, showing each step, and explain how the results confirm your answer to (a).

> **c**. Prove your answer to (a) using resolution.

**7.19** A sentence is in **disjunctive normal form** (DNF) if it is the disjunction of conjunctions of literals. For example, the sentence (*A* ⋀ *B* ⋀ ¬*C*) ⋁ (¬*A* ⋀ *C*) ⋁ (*B* ⋀ ¬*C*) is in DNF.

* * *

DISJUNCTIVE NORMAL FORM

* * *

> **a**. Any propositional logic sentence is logically equivalent to the assertion that some possible world in which it would be true is in fact the case. From this observation, prove that any sentence can be written in DNF.

> **b**. Construct an algorithm that converts any sentence in propositional logic into DNF. (*Hint*: The algorithm is similar to the algorithm for conversion to CNF given in [Section 7.5.2](#index_split_000.html#filepos1012679).)

> **c**. Construct a simple algorithm that takes as input a sentence in DNF and returns a satisfying assignment if one exists, or reports that no satisfying assignment exists.

> **d**. Apply the algorithms in (b) and (c) to the following set of sentences:

> *A* ⇒ *B*

> *B* ⇒ *C*

> *C* ⇒ ¬*A*.

> **e**. Since the algorithm in (b) is very similar to the algorithm for conversion to CNF, and since the algorithm in (c) is much simpler than any algorithm for solving a set of sentences in CNF, why is this technique not used in automated reasoning?

**7.20** Convert the following set of sentences to clausal form.

> S1: *A* ⇔ (*B* ⋁ *E*).

> S2: *E* ⇒ *D*.

> S3: *C* ⋀ *f* ⇒ ¬*B*.

> S4: *E* ⇒ *B*.

> S5: *B* ⇒ *F*.

> S6: *B* ⇒ *C*

Give a trace of the execution of DPLL on the conjunction of these clauses.

**7.21** Is a randomly generated 4-CNF sentence with *n* symbols and *m* clauses more or less likely to be solvable than a randomly generated 3-CNF sentence with *n* symbols and *m* clauses? Explain.

**7.22** Minesweeper, the well-known computer game, is closely related to the wumpus world. A minesweeper world is a rectangular grid of *N* squares with *M* invisible mines scattered among them. Any square may be probed by the agent; instant death follows if a mine is probed. Minesweeper indicates the presence of mines by revealing, in each probed square, the *number* of mines that are directly or diagonally adjacent. The goal is to probe every unmined square.

> **a**. Let *X*[*i*,*j*] be true iff square \[*i*, *j*\] contains a mine. Write down the assertion that exactly two mines are adjacent to \[1,1\] as a sentence involving some logical combination of *X*[*i*,*j*] propositions.

> **b**. Generalize your assertion from (a) by explaining how to construct a CNF sentence asserting that *k* of *n* neighbors contain mines.

> **c**. Explain precisely how an agent can use DPLL to prove that a given square does (or does not) contain a mine, ignoring the global constraint that there are exactly *M* mines in all.

> **d**. Suppose that the global constraint is constructed from your method from part (b). How does the number of clauses depend on *M* and *N*? Suggest a way to modify DPLL so that the global constraint does not need to be represented explicitly.

> **e**. Are any conclusions derived by the method in part (c) invalidated when the global constraint is taken into account?

> **f**. Give examples of configurations of probe values that induce *long-range dependencies* such that the contents of a given unprobed square would give information about the contents of a far-distant square. (*Hint*: consider an *N* × 1 board.)

**7.23** How long does it take to prove *KB* ⊨ α using DPLL when α is a literal *already contained in* *KB*? Explain.

**7.24** Trace the behavior of DPLL on the knowledge base in [Figure 7.16](#index_split_014.html#filepos1043891) when trying to prove *Q*, and compare this behavior with that of the forward-chaining algorithm.

**7.25** Write a successor-state axiom for the *Locked* predicate, which applies to doors, assuming the only actions available are *Lock* and *Unlock*.

**7.26** [Section 7.7.1](#index_split_000.html#filepos1065941) provides some of the successor-state axioms required for the wumpus world. Write down axioms for all remaining fluent symbols.

**7.27** Modify the HYBRID\-WUMPUS\-AGENT to use the 1-CNF logical state estimation method described [on page 271](#index_split_014.html#filepos1087695). We noted on that page that such an agent will not be able to acquire, maintain, and use more complex beliefs such as the disjunction *P*[3,1] ⋁ *P*[2,2]. Suggest a method for overcoming this problem by defining additional proposition symbols, and try it out in the wumpus world. Does it improve the performance of the agent?

![radio](images/00004.jpg)

## **8 FIRST-ORDER LOGIC**

> *In which we notice that the world is blessed with many objects, some of which are related to other objects, and in which we endeavor to reason about them.*

In [Chapter 7](#index_split_000.html#filepos939379), we showed how a knowledge-based agent could represent the world in which it operates and deduce what actions to take. We used propositional logic as our representation language because it sufficed to illustrate the basic concepts of logic and knowledge-based agents. Unfortunately, propositional logic is too puny a language to represent knowledge of complex environments in a concise way. In this chapter, we examine **first-order logic**,[¹](#index_split_015.html#filepos5584229) which is sufficiently expressive to represent a good deal of our commonsense knowledge. It also either subsumes or forms the foundation of many other representation languages and has been studied intensively for many decades. We begin in [Section 8.1](#index_split_000.html#filepos1151373) with a discussion of representation languages in general; [Section 8.2](#index_split_000.html#filepos1172048) covers the syntax and semantics of first-order logic; Sections 8.3 and 8.4 illustrate the use of first-order logic for simple representations.

* * *

FIRST-ORDER LOGIC

* * *

### 8.1 REPRESENTATION REVISITED

In this section, we discuss the nature of representation languages. Our discussion motivates the development of first-order logic, a much more expressive language than the propositional logic introduced in [Chapter 7](#index_split_000.html#filepos939379). We look at propositional logic and at other kinds of languages to understand what works and what fails. Our discussion will be cursory, compressing centuries of thought, trial, and error into a few paragraphs.

Programming languages (such as C++ or Java or Lisp) are by far the largest class of formal languages in common use. Programs themselves represent, in a direct sense, only computational processes. Data structures within programs can represent facts; for example, a program could use a 4 × 4 array to represent the contents of the wumpus world. Thus, the programming language statement *World*\[2,2\] ← *Pit* is a fairly natural way to assert that there is a pit in square \[2,2\]. (Such representations might be considered *ad hoc*; database systems were developed precisely to provide a more general, domain-independent way to store and retrieve facts.) What programming languages lack is any general mechanism for deriving facts from other facts; each update to a data structure is done by a domain-specific procedure whose details are derived by the programmer from his or her own knowledge of the domain. This procedural approach can be contrasted with the **declarative** nature of propositional logic, in which knowledge and inference are separate, and inference is entirely domain independent.

A second drawback of data structures in programs (and of databases, for that matter) is the lack of any easy way to say, for example, “There is a pit in \[2,2\] or \[3,1\]” or “If the wumpus is in \[1,1\] then he is not in \[2,2\].” Programs can store a single value for each variable, and some systems allow the value to be “unknown,” but they lack the expressiveness required to handle partial information.

Propositional logic is a declarative language because its semantics is based on a truth relation between sentences and possible worlds. It also has sufficient expressive power to deal with partial information, using disjunction and negation. Propositional logic has a third property that is desirable in representation languages, namely, **compositionality**. In a compositional language, the meaning of a sentence is a function of the meaning of its parts. For example, the meaning of “*S*[1,4] ̂ *S*[1,2]” is related to the meanings of “*S*[1,4]” and “*S*[1,2].” It would be very strange if “*S*[1,4]” meant that there is a stench in square \[1,4\] and “*S*[1,2]” meant that there is a stench in square \[1,2\], but “*S*[1,4] ̂ *S*[1,2]” meant that France and Poland drew 1–1 in last week’s ice hockey qualifying match. Clearly, noncompositionality makes life much more difficult for the reasoning system.

* * *

COMPOSITIONALITY

* * *

As we saw in [Chapter 7](#index_split_000.html#filepos939379), however, propositional logic lacks the expressive power to *concisely* describe an environment with many objects. For example, we were forced to write a separate rule about breezes and pits for each square, such as

> ![equ](images/00224.jpg)

In English, on the other hand, it seems easy enough to say, once and for all, “Squares adjacent to pits are breezy.” The syntax and semantics of English somehow make it possible to describe the environment concisely.

#### **8.1.1 The language of thought**

Natural languages (such as English or Spanish) are very expressive indeed. We managed to write almost this whole book in natural language, with only occasional lapses into other languages (including logic, mathematics, and the language of diagrams). There is a long tradition in linguistics and the philosophy of language that views natural language as a declarative knowledge representation language. If we could uncover the rules for natural language, we could use it in representation and reasoning systems and gain the benefit of the billions of pages that have been written in natural language.

The modern view of natural language is that it serves a as a medium for **communication** rather than pure representation. When a speaker points and says, “Look!” the listener comes to know that, say, Superman has finally appeared over the rooftops. Yet we would not want to say that the sentence “Look!” represents that fact. Rather, the meaning of the sentence depends both on the sentence itself and on the **context** in which the sentence was spoken. Clearly, one could not store a sentence such as “Look!” in a knowledge base and expect to recover its meaning without also storing a representation of the context—which raises the question of how the context itself can be represented. Natural languages also suffer from **ambiguity**, a problem for a representation language. As Pinker (1995) puts it: “When people think about *spring*, surely they are not confused as to whether they are thinking about a season or something that goes *boing*—and if one word can correspond to two thoughts, thoughts can’t be words.”

* * *

AMBIGUITY

* * *

The famous **Sapir–Whorf hypothesis** claims that our understanding of the world *is* strongly influenced by the language we speak. Whorf (1956) wrote “We cut nature up, organize it into concepts, and ascribe significances as we do, largely because we are parties to an agreement to organize it this way—an agreement that holds throughout our speech community and is codified in the patterns of our language.” It is certainly true that different speech communities divide up the world differently. The French have two words “chaise” and “fauteuil,” for a concept that English speakers cover with one: “chair.” But English speakers can easily recognize the category fauteuil and give it a name—roughly “open-arm chair”—so does language really make a difference? Whorf relied mainly on intuition and speculation, but in the intervening years we actually have real data from anthropological, psychological and neurological studies.

For example, can you remember which of the following two phrases formed the opening of [Section 8.1](#index_split_000.html#filepos1151373)?

“In this section, we discuss the nature of representation languages…”

“This section covers the topic of knowledge representation languages…”

Wanner (1974) did a similar experiment and found that subjects made the right choice at chance level—about 50% of the time—but remembered the content of what they read with better than 90% accuracy. This suggests that people process the words to form some kind of *nonverbal* representation.

More interesting is the case in which a concept is completely absent in a language. Speakers of the Australian aboriginal language Guugu Yimithirr have no words for relative directions, such as front, back, right, or left. Instead they use absolute directions, saying, for example, the equivalent of “I have a pain in my north arm.” This difference in language makes a difference in behavior: Guugu Yimithirr speakers are better at navigating in open terrain, while English speakers are better at placing the fork to the right of the plate.

Language also seems to influence thought through seemingly arbitrary grammatical features such as the gender of nouns. For example, “bridge” is masculine in Spanish and feminine in German. Boroditsky (2003) asked subjects to choose English adjectives to describe a photograph of a particular bridge. Spanish speakers chose *big*, *dangerous*, *strong*, and *towering*, whereas German speakers chose *beautiful*, *elegant*, *fragile*,and *slender*. Words can serve as anchor points that affect how we perceive the world. Loftus and Palmer (1974) showed experimental subjects a movie of an auto accident. Subjects who were asked “How fast were the cars going when they contacted each other?” reported an average of 32 mph, while subjects who were asked the question with the word “smashed” instead of “contacted”reported 41mph for the same cars in the same movie.

In a first-order logic reasoning system that uses CNF, we can see that the linguistic form “¬(*A* ⋁ *B*)” and “¬*A* ̂ ¬*B*” are the same because we can look inside the system and see that the two sentences are stored as the same canonical CNF form. Can we do that with the human brain? Until recently the answer was “no,” but now it is “maybe.” Mitchell **et al.** (2008) put subjects in an fMRI (functional magnetic resonance imaging) machine, showed them words such as “celery,” and imaged their brains. The researchers were then able to train a computer program to predict, from a brain image, what word the subject had been presented with. Given two choices (e.g., “celery” or “airplane”), the system predicts correctly 77% of the time. The system can even predict at above-chance levels for words it has never seen an fMRI image of before (by considering the images of related words) and for people it has never seen before (proving that fMRI reveals some level of common representation across people). This type of work is still in its infancy, but fMRI (and other imaging technology such as intracranial electrophysiology (Sahin **et al.**, 2009)) promises to give us much more concrete ideas of what human knowledge representations are like.

From the viewpoint of formal logic, representing the same knowledge in two different ways makes absolutely no difference; the same facts will be derivable from either representation. In practice, however, one representation might require fewer steps to derive a conclusion, meaning that a reasoner with limited resources could get to the conclusion using one representation but not the other. For *nondeductive* tasks such as learning from experience, outcomes are *necessarily* dependent on the form of the representations used. We show in [Chapter 18](#index_split_015.html#filepos2753020) that when a learning program considers two possible theories of the world, both of which are consistent with all the data, the most common way of breaking the tie is to choose the most succinct theory—and that depends on the language used to represent theories. Thus, the influence of language on thought is unavoidable for any agent that does learning.

#### **8.1.2 Combining the best of formal and natural languages**

We can adopt the foundation of propositional logic—a declarative, compositional semantics that is context-independent and unambiguous—and build a more expressive logic on that foundation, borrowing representational ideas from natural language while avoiding its drawbacks. When we look at the syntax of natural language, the most obvious elements are nouns and noun phrases that refer to **objects** (squares, pits, wumpuses) and verbs and verb phrases that refer to **relations** among objects (is breezy, is adjacent to, shoots). Some of these relations are **functions**—relations in which there is only one “value” for a given “input.” It is easy to start listing examples of objects, relations, and functions:

> • Objects: people, houses, numbers, theories, Ronald McDonald, colors, baseball games, wars, centuries…

> • Relations: these can be unary relations or **properties** such as red, round, bogus, prime, multistoried…, or more general n-ary relations such as brother of, bigger than, inside, part of, has color, occurred after, owns, comes between,…

> • Functions: father of, best friend, third inning of, one more than, beginning of…

* * *

OBJECT

* * *

* * *

RELATION

* * *

* * *

FUNCTION

* * *

* * *

PROPERTY

* * *

Indeed, almost any assertion can be thought of as referring to objects and properties or relations. Some examples follow:

> • “One plus two equals three.”

> Objects: one, two, three, one plus two; Relation: equals; Function: plus. (“One plus two” is a name for the object that is obtained by applying the function “plus” to the objects “one” and “two.” “Three” is another name for this object.)

> • “Squares neighboring the wumpus are smelly.”

> Objects: wumpus, squares; Property: smelly; Relation: neighboring.

> • “Evil King John ruled England in 1200.”

> Objects: John, England, 1200; Relation: ruled; Properties: evil, king.

The language of **first-order logic**, whose syntax and semantics we define in the next section, is built around objects and relations. It has been so important to mathematics, philosophy, and artificial intelligence precisely because those fields—and indeed, much of everyday human existence—can be usefully thought of as dealing with objects and the relations among them. First-order logic can also express facts about *some* or *all* of the objects in the universe. This enables one to represent general laws or rules, such as the statement “Squares neighboring the wumpus are smelly.”

The primary difference between propositional and first-order logic lies in the **ontological commitment** made by each language—that is, what it assumes about the nature of *reality*. Mathematically, this commitment is expressed through the nature of the formal **models** with respect to which the truth of sentences is defined. For example, propositional logic assumes that there are facts that either hold or do not hold in the world. Each fact can be in one of two states: true or false, and each model assigns true or false to each proposition symbol (see [Section 7.4.2](#index_split_000.html#filepos982455)).[²](#index_split_015.html#filepos5584469) First-order logic assumes more; namely, that the world consists of objects with certain relations among them that do or do not hold. The formal models are correspondingly more complicated than those for propositional logic. Special-purpose logics make still further ontological commitments; for example, **temporal logic** assumes that facts hold at particular *times* and that those times (which may be points or intervals) are ordered. Thus, special-purpose logics give certain kinds of objects (and the axioms about them) “first class” status within the logic, rather than simply defining them within the knowledge base. **Higher-order logic** views the relations and functions referred to by first-order logic as objects in themselves. This allows one to make assertions about *all* relations—for example, one could wish to define what it means for a relation to be transitive. Unlike most special-purpose logics, higher-order logic is strictly more expressive than first-order logic, in the sense that some sentences of higher-order logic cannot be expressed by any finite number of first-order logic sentences.

* * *

ONTOLOGICAL COMMITMENT

* * *

* * *

TEMPORAL LOGIC

* * *

* * *

HIGHER-ORDER LOGIC

* * *

A logic can also be characterized by its **epistemological commitments**—the possible states of knowledge that it allows with respect to each fact. In both propositional and first-order logic, a sentence represents a fact and the agent either believes the sentence to be true, believes it to be false, or has no opinion. These logics therefore have three possible states of knowledge regarding any sentence. Systems using **probability theory**, on the other hand, can have any *degree of belief*, ranging from 0 (total disbelief) to 1 (total belief).[³](#index_split_015.html#filepos5584809) For example, a probabilistic wumpus-world agent might believe that the wumpus is in \[1,3\] with probability 0.75. The ontological and epistemological commitments of five different logics are summarized in [Figure 8.1](#index_split_015.html#filepos1171173).

* * *

EPISTEMOLOGICAL COMMITMENT

* * *

> ![image](images/00225.jpg)

> **Figure 8.1** Formal languages and their ontological and epistemological commitments.

In the next section, we will launch into the details of first-order logic. Just as a student of physics requires some familiarity with mathematics, a student of AI must develop a talent for working with logical notation. On the other hand, it is also important *not* to get too concerned with the *specifics* of logical notation—after all, there are dozens of different versions. The main things to keep hold of are how the language facilitates concise representations and how its semantics leads to sound reasoning procedures.

### 8.2 SYNTAX AND SEMANTICS OF FIRST\-ORDER LOGIC

We begin this section by specifying more precisely the way in which the possible worlds of first-order logic reflect the ontological commitment to objects and relations. Then we introduce the various elements of the language, explaining their semantics as we go along.

#### **8.2.1 Models for first-order logic**

Recall from [Chapter 7](#index_split_000.html#filepos939379) that the models of a logical language are the formal structures that constitute the possible worlds under consideration. Each model links the vocabulary of the logical sentences to elements of the possible world, so that the truth of any sentence can be determined. Thus, models for propositional logic link proposition symbols to predefined truth values. Models for first-order logic are much more interesting. First, they have objects in them! The **domain** of a model is the set of objects or **domain elements** it contains. The domain is required to be *nonempty*—every possible world must contain at least one object. (See Exercise 8.7 for a discussion of empty worlds.) Mathematically speaking, it doesn’t matter *what* these objects are—all that matters is *how many* there are in each particular model—but for pedagogical purposes we’ll use a concrete example. [Figure 8.2](#index_split_015.html#filepos1176764) shows a model with five objects: Richard the Lionheart, King of England from 1189 to 1199; his younger brother, the evil King John, who ruled from 1199 to 1215; the left legs of Richard and John; and a crown.

* * *

DOMAIN

* * *

* * *

DOMAIN ELEMENTS

* * *

The objects in the model may be *related* in various ways. In the figure, Richard and John are brothers. Formally speaking, a relation is just the set of **tuples** of objects that are related. (*A* tuple is a collection of objects arranged in a fixed order and is written with angle brackets surrounding the objects.) Thus, the brotherhood relation in this model is the set

> ![equ](images/00226.jpg)

* * *

TUPLE

* * *

* * *

TOTAL FUNCTIONS

* * *

(Here we have named the objects in English, but you may, if you wish, mentally substitute the pictures for the names.) The crown is on King John’s head, so the “on head” relation contains just one tuple, the crown, King John. The “brother” and “on head” relations are binary relations—that is, they relate pairs of objects. The model also contains unary relations, or properties: the “person” property is true of both Richard and John; the “king” property is true only of John (presumably because Richard is dead at this point); and the “crown” property is true only of the crown.

Certain kinds of relationships are best considered as functions, in that a given object must be related to exactly one object in this way. For example, each person has one left leg, so the model has a unary “left leg” function that includes the following mappings:

> ![equ](images/00227.jpg)

Strictly speaking, models in first-order logic require **total functions**, that is, there must be a value for every input tuple. Thus, the crown must have a left leg and so must each of the left legs. There is a technical solution to this awkward problem involving an additional “invisible” object that is the left leg of everything that has no left leg, including itself. Fortunately, as long as one makes no assertions about the left legs of things that have no left legs, these technicalities are of no import.

> 

> ![equ](images/00228.jpg)

> **Figure 8.2** A model containing five objects, two binary relations, three unary relations (indicated by labels on the objects), and one unary function, left-leg.

So far, we have described the elements that populate models for first-order logic. The other essential part of a model is the link between those elements and the vocabulary of the logical sentences, which we explain next.

#### **8.2.2 Symbols and interpretations**

We turn now to the syntax of first-order logic. The impatient reader can obtain a complete description from the formal grammar in [Figure 8.3](#index_split_015.html#filepos1181724).

The basic syntactic elements of first-order logic are the symbols that stand for objects, relations, and functions. The symbols, therefore, come in three kinds: **constant symbols**, which stand for objects; **predicate symbols**, which stand for relations; and **function symbols**, which stand for functions. We adopt the convention that these symbols will begin with uppercase letters. For example, we might use the constant symbols *Richard* and *John*; the predicate symbols *Brother*, *OnHead*, *Person*, *King*, and *Crown*; and the function symbol *LeftLeg*. As with proposition symbols, the choice of names is entirely up to the user. Each predicate and function symbol comes with an **arity** that fixes the number of arguments.

* * *

CONSTANT SYMBOL

* * *

* * *

PREDICATE SYMBOL

* * *

* * *

FUNCTION SYMBOL

* * *

* * *

ARITY

* * *

As in propositional logic, every model must provide the information required to determine if any given sentence is true or false. Thus, in addition to its objects, relations, and functions, each model includes an **interpretation** that specifies exactly which objects, relations and functions are referred to by the constant, predicate, and function symbols. One possible interpretation for our example—which a logician would call the **intended interpretation**—is as follows:

> • *Richard* refers to Richard the Lionheart and *John* refers to the evil King John.

> • *Brother* refers to the brotherhood relation, that is, the set of tuples of objects given in Equation (8.1); *OnHead* refers to the “on head” relation that holds between the crown and King John; *Person*, *King*, and *Crown* refer to the sets of objects that are persons, kings, and crowns.

> • *LeftLeg* refers to the “left leg” function, that is, the mapping given in Equation (8.2).

* * *

INTERPRETATION

* * *

* * *

INTENDED INTERPRETATION

* * *

There are many other possible interpretations, of course. For example, one interpretation maps *Richard* to the crown and *John* to King John’s left leg. There are five objects in the model, so there are 25 possible interpretations just for the constant symbols *Richard* and *John*. Notice that not all the objects need have a name—for example, the intended interpretation does not name the crown or the legs. It is also possible for an object to have several names; there is an interpretation under which both *Richard* and *John* refer to the crown.[⁴](#index_split_015.html#filepos5585119) If you find this possibility confusing, remember that, in propositional logic, it is perfectly possible to have a model in which *Cloudy* and *Sunny* are both true; it is the job of the knowledge base to rule out models that are inconsistent with our knowledge.

> ![image](images/00229.jpg)

> **Figure 8.3** The syntax of first-order logic with equality, specified in Backus–Naur form (see [page 1060](#index_split_015.html#filepos4111078) if you are not familiar with this notation). Operator precedences are specified, from highest to lowest. The precedence of quantifiers is such that a quantifier holds over everything to the right of it.

> ![image](images/00230.jpg)

> **Figure 8.4** Some members of the set of all models for a language with two constant symbols, *R* and *J*, and one binary relation symbol. The interpretation of each constant symbol is shown by a gray arrow. Within each model, the related objects are connected by arrows.

In summary, a model in first-order logic consists of a set of objects and an interpretation that maps constant symbols to objects, predicate symbols to relations on those objects, and function symbols to functions on those objects. Just as with propositional logic, entailment, validity, and so on are defined in terms of *all possible models*. To get an idea of what the set of all possible models looks like, see [Figure 8.4](#index_split_015.html#filepos1182294). It shows that models vary in how many objects they contain—from one up to infinity—and in the way the constant symbols map to objects. If there are two constant symbols and one object, then both symbols must refer to the same object; but this can still happen even with more objects. When there are more objects than constant symbols, some of the objects will have no names. Because the number of possible models is unbounded, checking entailment by the enumeration of all possible models is not feasible for first-order logic (unlike propositional logic). Even if the number of objects is restricted, the number of combinations can be very large. (See Exercise 8.5.) For the example in [Figure 8.4](#index_split_015.html#filepos1182294), there are 137,506,194,466 models with six or fewer objects.

#### **8.2.3 Terms**

A **term** is a logical expression that refers to an object. Constant symbols are therefore terms, but it is not always convenient to have a distinct symbol to name every object. For example, in English we might use the expression “King John’s left leg” rather than giving a name to his leg. This is what function symbols are for: instead of using a constant symbol, we use *LeftLeg*(*John*). In the general case, a complex term is formed by a function symbol followed by a parenthesized list of terms as arguments to the function symbol. It is important to remember that a complex term is just a complicated kind of name. It is not a “subroutine call” that “returns a value.” There is no *LeftLeg* subroutine that takes a person as input and returns a leg. We can reason about left legs (e.g., stating the general rule that everyone has one and then deducing that John must have one) without ever providing a definition of *LeftLeg*. This is something that cannot be done with subroutines in programming languages.[⁵](#index_split_015.html#filepos5585345)

* * *

TERM

* * *

The formal semantics of terms is straightforward. Consider a term *f*(*t*[1],…,*t*[*n*]). The function symbol *f* refers to some function in the model (call it *F*); the argument terms refer to objects in the domain (call them *d*[1],…,*d*[*n*]); and the term as a whole refers to the object that is the value of the function *F* applied to *d*[1],…,*d*[*n*]. For example, suppose the LeftLeg function symbol refers to the function shown in Equation (8.2) and *John* refers to King John, then *LeftLeg*(*John*) refers to King John’s left leg. In this way, the interpretation fixes the referent of every term.

#### **8.2.4 Atomic sentences**

Now that we have both terms for referring to objects and predicate symbols for referring to relations, we can put them together to make **atomic sentences** that state facts. An **atomic** **sentence** (or **atom** for short) is formed from a predicate symbol optionally followed by a parenthesized list of terms, such as

> *Brother* (*Richard*, *John*).

* * *

ATOMIC SENTENCE

* * *

* * *

ATOM

* * *

This states, under the intended interpretation given earlier, that Richard the Lionheart is the brother of King John.[⁶](#index_split_015.html#filepos5586265) Atomic sentences can have complex terms as arguments. Thus,

> *Married*(*Father*(*Richard*), *Mother* (*John*))

states that Richard the Lionheart’s father is married to King John’s mother (again, under a suitable interpretation).

*An atomic sentence is* ***true*** *in a given model if the relation referred to by the predicate symbol holds among the objects referred to by the arguments.*

![hand](images/00006.jpg)

#### **8.2.5 Complex sentences**

We can use **logical connectives** to construct more complex sentences, with the same syntax and semantics as in propositional calculus. Here are four sentences that are true in the model of [Figure 8.2](#index_split_015.html#filepos1176764) under our intended interpretation:

> ¬*Brother* (*LeftLeg*(*Richard*), *John*)

> *Brother* (*Richard*, *John*) ̂ *Brother* (*John*, *Richard*)

> *King*(*Richard*) ⋁ *King*(*John*)

> ¬*King*(*Richard*) ⇒ *King*(*John*).

#### **8.2.6 Quantifiers**

Once we have a logic that allows objects, it is only natural to want to express properties of entire collections of objects, instead of enumerating the objects by name. **Quantifiers** let us do this. First-order logic contains two standard quantifiers, called *universal* and *existential*.

* * *

QUANTIFIER

* * *

##### **Universal quantification** (∀)

Recall the difficulty we had in [Chapter 7](#index_split_000.html#filepos939379) with the expression of general rules in propositional logic. Rules such as “Squares neighboring the wumpus are smelly” and “All kings are persons” are the bread and butter of first-order logic. We deal with the first of these in [Section 8.3](#index_split_000.html#filepos1212170). The second rule, “All kings are persons,” is written in first-order logic as

> ![equ](images/00231.jpg)

∀ is usually pronounced “For all…”. (Remember that the upside-down A stands for “all.”) Thus, the sentence says, “For all *x*, if *x* is a king, then *x* is a person.” The symbol *x* is called a **variable**. By convention, variables are lowercase letters. A variable is a term all by itself, and as such can also serve as the argument of a function—for example, LeftLeg(*x*). A term with no variables is called a **ground term**.

* * *

VARIABLE

* * *

* * *

GROUND TERM

* * *

Intuitively, the sentence ∀ *x* *P*, where *P* is any logical expression, says that *P* is true for every object *x*. More precisely, ∀ *x* *P* is true in a given model if *P* is true in all possible **extended interpretations** constructed from the interpretation given in the model, where each extended interpretation specifies a domain element to which *x* refers.

* * *

EXTENDED INTERPRETATION

* * *

This sounds complicated, but it is really just a careful way of stating the intuitive meaning of universal quantification. Consider the model shown in [Figure 8.2](#index_split_015.html#filepos1176764) and the intended interpretation that goes with it. We can extend the interpretation in five ways:

> *x* → Richard the Lionheart,

> *x* → King John,

> *x* → Richard’s left leg,

> *x* → John’s left leg,

> *x* → the crown.

The universally quantified sentence ∀ *x* *King*(*x*) ⇒ *Person*(*x*) is true in the original model if the sentence *King*(*x*) ⇒ *Person*(*x*) is true under each of the five extended interpretations. That is, the universally quantified sentence is equivalent to asserting the following five sentences:

> Richard the Lionheart is a king ⇒ Richard the Lionheart is a person.

> King John is a king ⇒ King John is a person.

> Richard’s left leg is a king ⇒ Richard’s left leg is a person.

> John’s left leg is a king ⇒ John’s left leg is a person.

> The crown isaking ⇒ the crown is a person.

Let us look carefully at this set of assertions. Since, in our model, King John is the only king, the second sentence asserts that he is a person, as we would hope. But what about the other four sentences, which appear to make claims about legs and crowns? Is that part of the meaning of “All kings are persons”? In fact, the other four assertions are true in the model, but make no claim whatsoever about the personhood qualifications of legs, crowns, or indeed Richard. This is because none of these objects is a king. Looking at the truth table for ⇒ ([Figure 7.8](#index_split_014.html#filepos987107) on [page 246](#index_split_014.html#filepos986574)), we see that the implication is true whenever its premise is false—*regardless* of the truth of the conclusion. Thus, by asserting the universally quantified sentence, which is equivalent to asserting a whole list of individual implications, we end up asserting the conclusion of the rule just for those objects for whom the premise is true and saying nothing at all about those individuals for whom the premise is false. Thus, the truth-table definition of ⇒ turns out to be perfect for writing general rules with universal quantifiers.

A common mistake, made frequently even by diligent readers who have read this paragraph several times, is to use conjunction instead of implication. The sentence

> ![equ](images/00232.jpg)

would be equivalent to asserting

> Richard the Lionheart is a king ̂ Richard the Lionheart is a person,

> King John is a king ̂ King John is a person,

> Richard’s left leg is a king ̂ Richard’s left leg is a person,

and so on. Obviously, this does not capture what we want.

##### **Existential quantification (**∃**)**

Universal quantification makes statements about every object. Similarly, we can make a statement about *some* object in the universe without naming it, by using an existential quantifier. To say, for example, that King John has a crown on his head, we write

> ![equ](images/00233.jpg)

∃*x* is pronounced “There exists an *x* such that…”or“Forsome x…”.

Intuitively, the sentence ∃ *x* *P* says that *P* is true for at least one object *x*. More precisely, ∃ *x* *P* is true in a given model if *P* is true in *at least one* extended interpretation that assigns *x* to a domain element. That is, at least one of the following is true:

> Richard the Lionheart is a crown ̂ Richard the Lionheart is on John’s head;

> King John is a crown ̂ King John is on John’s head;

> Richard’s left leg is a crown ̂ Richard’s left leg is on John’s head;

> John’s left leg is a crown ̂ John’s left leg is on John’s head;

> The crown isacrown ̂ the crown is on John’s head.

The fifth assertion is true in the model, so the original existentially quantified sentence is true in the model. Notice that, by our definition, the sentence would also be true in a model in which King John was wearing two crowns. This is entirely consistent with the original sentence “King John has a crown on his head.”[⁷](#index_split_015.html#filepos5586530)

Just as ⇒ appears to be the natural connective to use with ∀, ̂ is the natural connective to use with ∃. Using ̂ as the main connective with ∀ led to an overly strong statement in the example in the previous section; using ⇒ with ∃ usually leads to a very weak statement, indeed. Consider the following sentence:

> ![equ](images/00234.jpg)

On the surface, this might look like a reasonable rendition of our sentence. Applying the semantics, we see that the sentence says that at least one of the following assertions is true:

> Richard the Lionheart is a crown ⇒ Richard the Lionheart is on John’s head;

> King John is a crown ⇒ King John is on John’s head;

> Richard’s left leg is a crown ⇒ Richard’s left leg is on John’s head;

and so on. Now an implication is true if both premise and conclusion are true, *or if its premise is false*. So if Richard the Lionheart is not a crown, then the first assertion is true and the existential is satisfied. So, an existentially quantified implication sentence is true whenever *any* object fails to satisfy the premise; hence such sentences really do not say much at all.

##### **Nested quantifiers**

We will often want to express more complex sentences using multiple quantifiers. The simplest case is where the quantifiers are of the same type. For example, “Brothers are siblings”can be written as

> ![equ](images/00235.jpg)

Consecutive quantifiers of the same type can be written as one quantifier with several variables. For example, to say that siblinghood is a symmetric relationship, we can write

> ![equ](images/00236.jpg)

In other cases we will have mixtures. “Everybody loves somebody” means that for every person, there is someone that person loves:

> ![equ](images/00237.jpg)

On the other hand, to say “There is someone who is loved by everyone,” we write

> ![equ](images/00238.jpg)

The order of quantification is therefore very important. It becomes clearer if we insert parentheses. ∀ *x* (∃ *y* *Loves*(*x*, *y*)) says that *everyone* has a particular property, namely, the property that they love someone. On the other hand, ∃ *y* (∀ *x* *Loves*(*x*, *y*)) says that *someone* in the world has a particular property, namely the property of being loved by everybody.

Some confusion can arise when two quantifiers are used with the same variable name. Consider the sentence

> ![equ](images/00239.jpg)

Here the *x* in *Brother* (*Richard*, *x*) is *existentially* quantified. The rule is that the variable belongs to the innermost quantifier that mentions it; then it will not be subject to any other quantification. Another way to think of it is this: ∃ *x* *Brother* (*Richard*, *x*) is a sentence about Richard (that he has a brother), not about *x*; so putting a ∀ *x* outside it has no effect. It could equally well have been written ∃ *z* *Brother* (*Richard*, *z*). Because this can be a source of confusion, we will always use different variable names with nested quantifiers.

##### **Connections between** ∀ **and** ∃

The two quantifiers are actually intimately connected with each other, through negation. Asserting that everyone dislikes parsnips is the same as asserting there does not exist someone who likes them, and vice versa:

> ![equ](images/00240.jpg)

We can go one step further: “Everyone likes ice cream” means that there is no one who does not like ice cream:

> ![equ](images/00241.jpg)

Because ∀ is really a conjunction over the universe of objects and ∃ is a disjunction, it should not be surprising that they obey De Morgan’s rules. The De Morgan rules for quantified and unquantified sentences are as follows:

> ![equ](images/00242.jpg)

Thus, we do not really need both ∀ and ∃, just as we do not really need both ̂ and ⋁. Still, readability is more important than parsimony, so we will keep both of the quantifiers.

#### **8.2.7 Equality**

First-order logic includes one more way to make atomic sentences, other than using a predicate and terms as described earlier. We can use the **equality symbol** to signify that two terms refer to the same object. For example,

> *Father* (*John*) = *Henry*

* * *

EQUALITY SYMBOL

* * *

says that the object referred to by *Father* (*John*) and the object referred to by *Henry* are the same. Because an interpretation fixes the referent of any term, determining the truth of an equality sentence is simply a matter of seeing that the referents of the two terms are the same object.

The equality symbol can be used to state facts about a given function, as we just did for the *Father* symbol. It can also be used with negation to insist that two terms are not the same object. To say that Richard has at least two brothers, we would write

> ∃ *x*, *y* *Brother* (*x*, *Richard*) ̂ *Brother* (*y*, *Richard*) ̂ ¬(*x* = *y*).

The sentence

∃ *x*, *y* *Brother* (*x*, *Richard*) ̂ *Brother* (*y*, *Richard*)

does not have the intended meaning. In particular, it is true in the model of [Figure 8.2](#index_split_015.html#filepos1176764), where Richard has only one brother. To see this, consider the extended interpretation in which both *x* and *y* are assigned to King John. The addition of ¬(*x* = *y*) rules out such models. The notation *x* ≠ *y* is sometimes used as an abbreviation for ¬(*x* = *y*).

#### **8.2.8 An alternative semantics?**

Continuing the example from the previous section, suppose that we believe that Richard has two brothers, John and Geoffrey.[⁸](#index_split_015.html#filepos5586861) Can we capture this state of affairs by asserting

> ![equ](images/00243.jpg)

Not quite. First, this assertion is true in a model where Richard has only one brother—we need to add John ≠ Geoffrey. Second, the sentence doesn’t rule out models in which Richard has many more brothers besides John and Geoffrey. Thus, the correct translation of “Richard’s brothers are John and Geoffrey” is as follows:

> ![equ](images/00244.jpg)

For many purposes, this seems much more cumbersome than the corresponding natural-language expression. As a consequence, humans may make mistakes in translating their knowledge into first-order logic, resulting in unintuitive behaviors from logical reasoning systems that use the knowledge. Can we devise a semantics that allows a more straightforward logical expression?

One proposal that is very popular in database systems works as follows. First, we insist that every constant symbol refer to a distinct object—the so-called **unique-names assumption**. Second, we assume that atomic sentences not known to be true are in fact false—the **closed-world assumption**. Finally, we invoke **domain closure**, meaning that each model contains no more domain elements than those named by the constant symbols. Under the resulting semantics, which we call **database semantics** to distinguish it from the standard semantics of first-order logic, the sentence Equation (8.3) does indeed state that Richard’s two brothers are John and Geoffrey. Database semantics is also used in logic programming systems, as explained in [Section 9.4.5](#index_split_015.html#filepos1383378).

* * *

UNIQUE-NAMES ASSUMPTION

* * *

* * *

CLOSED-WORLD ASSUMPTION

* * *

* * *

DOMAIN CLOSURE

* * *

* * *

DATABASE SEMANTICS

* * *

> ![image](images/00245.jpg)

> **Figure 8.5** Some members of the set of all models for a language with two constant symbols, *R* and *J*, and one binary relation symbol, under database semantics. The interpretation of the constant symbols is fixed, and there is a distinct object for each constant symbol.

It is instructive to consider the set of all possible models under database semantics for the same case as shown in [Figure 8.4](#index_split_015.html#filepos1182294). [Figure 8.5](#index_split_015.html#filepos1210189) shows some of the models, ranging from the model with no tuples satisfying the relation to the model with all tuples satisfying the relation. With two objects, there are four possible two-element tuples, so there are 2⁴ = 16 different subsets of tuples that can satisfy the relation. Thus, there are 16 possible models in all—a lot fewer than the infinitely many models for the standard first-order semantics. On the other hand, the database semantics requires definite knowledge of what the world contains.

This example brings up an important point: there is no one “correct” semantics for logic. The usefulness of any proposed semantics depends on how concise and intuitive it makes the expression of the kinds of knowledge we want to write down, and on how easy and natural it is to develop the corresponding rules of inference. Database semantics is most useful when we are certain about the identity of all the objects described in the knowledge base and when we have all the facts at hand; in other cases, it is quite awkward. For the rest of this chapter, we assume the standard semantics while noting instances in which this choice leads to cumbersome expressions.

### 8.3 USING FIRST\-ORDER LOGIC

Now that we have defined an expressive logical language, it is time to learn how to use it. The best way to do this is through examples. We have seen some simple sentences illustrating the various aspects of logical syntax; in this section, we provide more systematic representations of some simple **domains**. In knowledge representation, a domain is just some part of the world about which we wish to express some knowledge.

* * *

DOMAIN

* * *

We begin with a brief description of the TELL/ASK interface for first-order knowledge bases. Then we look at the domains of family relationships, numbers, sets, and lists, and at the wumpus world. The next section contains a more substantial example (electronic circuits) and [Chapter 12](#index_split_015.html#filepos1750417) covers everything in the universe.

#### **8.3.1 Assertions and queries in first-order logic**

Sentences are added to a knowledge base using TELL, exactly as in propositional logic. Such sentences are called **assertions**. For example, we can assert that John is a king, Richard is a person, and all kings are persons:

> ![equ](images/00246.jpg)

* * *

ASSERTION

* * *

We can ask questions of the knowledge base using ASK. For example,

> ASK(*KB*, *King*(*John*))

returns *true*. Questions asked with ASK are called **queries** or **goals**. Generally speaking, any query that is logically entailed by the knowledge base should be answered affirmatively. For example, given the two preceding assertions, the query

ASK(*KB*, *Person*(*John*))

* * *

QUERY

* * *

* * *

GOAL

* * *

should also return *true*. We can ask quantified queries, such as

ASK(*KB*, ∃ *x* *Person*(*x*)).

The answer is *true*, but this is perhaps not as helpful as we would like. It is rather like answering “Can you tell me the time?” with “Yes.” If we want to know what value of *x* makes the sentence true, we will need a different function, ASKVARS, which we call with

> ASK VARS(*KB*, *Person*(*x*))

and which yields a stream of answers. In this case there will be two answers: {*x*/*John*} and {*x*/*Richard*}. Such an answer is called a **substitution** or **binding list**. ASKVARS is usually reserved for knowledge bases consisting solely of Horn clauses, because in such knowledge bases every way of making the query true will bind the variables to specific values. That is not the case with first-order logic; if *KB* has been told *King*(*John*) ⋁ *King*(*Richard*), then there is no binding to *x* for the query ∃ *x* *King*(*x*), even though the query is true.

* * *

SUBSTITUTION

* * *

* * *

BINDING LIST

* * *

#### **8.3.2 The kinship domain**

The first example we consider is the domain of family relationships, or kinship. This domain includes facts such as “Elizabeth is the mother of Charles” and “Charles is the father of William” and rules such as “One’s grandmother is the mother of one’s parent.”

Clearly, the objects in our domain are people. We have two unary predicates, *Male* and *Female*. Kinship relations—parenthood, brotherhood, marriage, and so on—are represented by binary predicates: *Parent, Sibling, Brother, Sister, Child, Daughter, Son, Spouse, Wife, Husband, Grandparent, Grandchild, Cousin, Aunt, and Uncle*. We use functions for Mother and Father, because every person has exactly one of each of these (at least according to nature’s design).

We can go through each function and predicate, writing down what we know in terms of the other symbols. For example, one’s mother is one’s female parent:

> ![equ](images/00247.jpg)

One’s husband is one’s male spouse:

> ![equ](images/00248.jpg)

Male and female are disjoint categories:

> ![equ](images/00249.jpg)

Parent and child are inverse relations:

> ![equ](images/00250.jpg)

A grandparent is a parent of one’s parent:

> ![equ](images/00251.jpg)

A sibling is another child of one’s parents:

> ![equ](images/00252.jpg)

We could go on for several more pages like this, and Exercise 8.14 asks you to do just that.

Each of these sentences can be viewed as an **axiom** of the kinship domain, as explained in [Section 7.1](#index_split_000.html#filepos943668). Axioms are commonly associated with purely mathematical domains—we will see some axioms for numbers shortly—but they are needed in all domains. They provide the basic factual information from which useful conclusions can be derived. Our kinship axioms are also **definitions**; they have the form ∀ *x*, *y* *P*(*x*, *y*) ⇔…. The axioms define the *Mother* function and the *Husband, Male, Parent, Grandparent*, and *Sibling* predicates in terms of other predicates. Our definitions “bottom out” at a basic set of predicates (*Child, Spouse*, and *Female*) in terms of which the others are ultimately defined. This is a natural way in which to build up the representation of a domain, and it is analogous to the way in which software packages are built up by successive definitions of subroutines from primitive library functions. Notice that there is not necessarily a unique set of primitive predicates; we could equally well have used *Parent*, *Spouse*, and *Male*. In some domains, as we show, there is no clearly identifiable basic set.

* * *

DEFINITION

* * *

Not all logical sentences about a domain are axioms. Some are **theorems**—that is, they are entailed by the axioms. For example, consider the assertion that siblinghood is symmetric:

> ![equ](images/00253.jpg)

* * *

THEOREM

* * *

Is this an axiom or a theorem? In fact, it is a theorem that follows logically from the axiom that defines siblinghood. If we ASK the knowledge base this sentence, it should return *true*.

From a purely logical point of view, a knowledge base need contain only axioms and no theorems, because the theorems do not increase the set of conclusions that follow from the knowledge base. From a practical point of view, theorems are essential to reduce the computational cost of deriving new sentences. Without them, a reasoning system has to start from first principles every time, rather like a physicist having to rederive the rules of calculus for every new problem.

Not all axioms are definitions. Some provide more general information about certain predicates without constituting a definition. Indeed, some predicates have no complete definition because we do not know enough to characterize them fully. For example, there is no obvious definitive way to complete the sentence

> ![equ](images/00254.jpg)

Fortunately, first-order logic allows us to make use of the *Person* predicate without completely defining it. Instead, we can write partial specifications of properties that every person has and properties that make something a person:

> ![equ](images/00255.jpg)

Axioms can also be “just plain facts,” such as *Male*(*Jim*) and *Spouse*(*Jim, Laura*). Such facts form the descriptions of specific problem instances, enabling specific questions to be answered. The answers to these questions will then be theorems that follow from the axioms. Often, one finds that the expected answers are not forthcoming—for example, from *Spouse*(*Jim*, *Laura*) one expects (under the laws of many countries) to be able to infer ¬*Spouse*(*George*, *Laura*); but this does not follow from the axioms given earlier—even after we add *Jim* ≠ *George* as suggested in [Section 8.2.8](#index_split_000.html#filepos1207340). This is a sign that an axiom is missing. Exercise 8.8 asks the reader to supply it.

#### **8.3.3 Numbers, sets, and lists**

Numbers are perhaps the most vivid example of how a large theory can be built up from a tiny kernel of axioms. We describe here the theory of **natural numbers** or nonnegative integers. We need a predicate *NatNum* that will be true of natural numbers; we need one constant symbol, 0; and we need one function symbol, *S* (successor). The **Peano axioms** define natural numbers and addition.[⁹](#index_split_015.html#filepos5587027) Natural numbers are defined recursively:

> ![equ](images/00256.jpg)

* * *

NATURAL NUMBERS

* * *

* * *

PEANO AXIOMS

* * *

That is, 0 is a natural number, and for every object *n*, if *n* is a natural number, then *S*(*n*) is a natural number. So the natural numbers are 0, *S*(0), *S*(*S*(0)), and so on. (After reading [Section 8.2.8](#index_split_000.html#filepos1207340), you will notice that these axioms allow for other natural numbers besides the usual ones; see Exercise 8.12.) We also need axioms to constrain the successor function:

> ![equ](images/00257.jpg)

Now we can define addition in terms of the successor function:

> ![equ](images/00258.jpg)

The first of these axioms says that adding 0 to any natural number *m* gives *m* itself. Notice the use of the binary function symbol “+” inthe term +(*m*, 0); in ordinary mathematics, the term would be written *m* + 0 using **infix** notation. (The notation we have used for first-order logic is called **prefix**.) To make our sentences about numbers easier to read, we allow the use of infix notation. We can also write *S*(*n*) as *n* +1, so the second axiom becomes

> ![equ](images/00259.jpg)

* * *

PREFIX

* * *

This axiom reduces addition to repeated application of the successor function.

The use of infix notation is an example of **syntactic sugar**, that is, an extension to or abbreviation of the standard syntax that does not change the semantics. Any sentence that uses sugar can be “desugared” to produce an equivalent sentence in ordinary first-order logic.

* * *

SYNTACTIC SUGAR

* * *

Once we have addition, it is straightforward to define multiplication as repeated addition, exponentiation as repeated multiplication, integer division and remainders, prime numbers, and so on. Thus, the whole of number theory (including cryptography) can be built up from one constant, one function, one predicate and four axioms.

The domain of **sets** is also fundamental to mathematics as well as to commonsense reasoning. (In fact, it is possible to define number theory in terms of set theory.) We want to be able to represent individual sets, including the empty set. We need a way to build up sets by adding an element to a set or taking the union or intersection of two sets. We will want to know whether an element is a member of a set and we will want to distinguish sets from objects that are not sets.

* * *

SET

* * *

We will use the normal vocabulary of set theory as syntactic sugar. The empty set is a constant written as {}. There is one unary predicate, *Set*, which is true of sets. The binary predicates are *x* ∈ *s* (*x* is a member of set *s*) and *s*[1] ⊆ *s*[2] (set *s*[1] is a subset, not necessarily proper, of set *s*[2]). The binary functions are *s*[1] ∩ *s*[2] (the intersection of two sets), *s*[1] ∪ *s*[2] (the union of two sets), and {*x*|*s*} (the set resulting from adjoining element *x* to set *s*). One possible set of axioms is as follows:

> 1\. The only sets are the empty set and those made by adjoining something to a set:

> ![equ](images/00260.jpg)

> 2\. The empty set has no elements adjoined into it. In other words, there is no way to decompose {} into a smaller set and an element:

> ![equ](images/00261.jpg)

> 3\. Adjoining an element already in the set has no effect:

> ![equ](images/00262.jpg)

> 4\. The only members of a set are the elements that were adjoined into it. We express this recursively, saying that *x* is a member of *s* if and only if *s* is equal to some set *s*[2] adjoined with some element *y*, where either *y* is the same as *x* or *x* is a member of *s*[2]:

> ![equ](images/00263.jpg)

> 5\. A set is a subset of another set if and only if all of the first set’s members are members of the second set:

> ![equ](images/00264.jpg)

> 6\. Two sets are equal if and only if each is a subset of the other:

> ![equ](images/00265.jpg)

> 7\. An object is in the intersection of two sets if and only if it is a member of both sets:

> ![equ](images/00266.jpg)

> 8\. An object is in the union of two sets if and only if it is a member of either set:

> ![equ](images/00267.jpg)

**Lists** are similar to sets. The differences are that lists are ordered and the same element can appear more than once in a list. We can use the vocabulary of Lisp for lists: *Nil* is the constant list with no elements; *Cons, Append, First*, and *Rest* are functions; and *Find* is the predicate that does for lists what *Member* does for sets. *List*? is a predicate that is true only of lists. As with sets, it is common to use syntactic sugar in logical sentences involving lists. The empty list is \[\]. The term *Cons*(*x*, *y*), where *y* is a nonempty list, is written \[*x*|*y*\]. The term *Cons*(*x*, Nil) (i.e., the list containing the element *x*) is written as \[*x*\]. A list of several elements, such as \[*A*, *B*, *C*\], corresponds to the nested term *Cons*(*A*, *Cons*(*B*, *Cons*(*C*, *Nil*))). Exercise 8.16 asks you to write out the axioms for lists.

* * *

LIST

* * *

#### **8.3.4 The wumpus world**

Some propositional logic axioms for the wumpus world were given in [Chapter 7](#index_split_000.html#filepos939379). The first-order axioms in this section are much more concise, capturing in a natural way exactly what we want to say.

Recall that the wumpus agent receives a percept vector with five elements. The corresponding first-order sentence stored in the knowledge base must include both the percept and the time at which it occurred; otherwise, the agent will get confused about when it saw what. We use integers for time steps. A typical percept sentence would be

> *Percept*(\[*Stench, Breeze, Glitter, None, None*\], 5).

Here, *Percept* is a binary predicate, and *Stench* and so on are constants placed in a list. The actions in the wumpus world can be represented by logical terms:

> *Turn*(*Right*), *Turn*(*Left*), *Forward*, *Shoot*, *Grab*, *Climb*.

To determine which is best, the agent program executes the query

> ASKVARS(∃ *a* *BestAction*(*a*, 5)),

which returns a binding list such as {*a*/*Grab*}. The agent program can then return *Grab* as the action to take. The raw percept data implies certain facts about the current state. For example:

> ![equ](images/00268.jpg)

and so on. These rules exhibit a trivial form of the reasoning process called **perception**, which we study in depth in [Chapter 24](#index_split_015.html#filepos3631932). Notice the quantification over time *t*. In propositional logic, we would need copies of each sentence for each time step.

Simple “reflex” behavior can also be implemented by quantified implication sentences. For example, we have

> ![equ](images/00269.jpg)

Given the percept and rules from the preceding paragraphs, this would yield the desired conclusion *BestAction*(*Grab*, 5)—that is, *Grab* is the right thing to do.

We have represented the agent’s inputs and outputs; now it is time to represent the environment itself. Let us begin with objects. Obvious candidates are squares, pits, and the wumpus. We could name each square—*Square*[1,2] and so on—but then the fact that *Square*[1,2] and *Square*[1,3] are adjacent would have to be an “extra” fact, and we would need one such fact for each pair of squares. It is better to use a complex term in which the row and column appear as integers; for example, we can simply use the list term \[1, 2\]. Adjacency of any two squares can be defined as

> ![equ](images/00270.jpg)

We could name each pit, but this would be inappropriate for a different reason: there is no reason to distinguish among pits.[^(10)](#index_split_015.html#filepos5587357) It is simpler to use a unary predicate *Pit* that is true of squares containing pits. Finally, since there is exactly one wumpus, a constant Wumpus is just as good as a unary predicate (and perhaps more dignified from the wumpus’s viewpoint).

The agent’s location changes over time, so we write *At*(*Agent*, *s*, *t*) to mean that the agent is at square *s* at time *t*. We can fix the wumpus’s location with ∀*t* *At*(*Wumpus*, \[2, 2\], *t*). We can then say that objects can only be at one location at a time:

> ![equ](images/00271.jpg)

Given its current location, the agent can infer properties of the square from properties of its current percept. For example, if the agent is at a square and perceives a breeze, then that square is breezy:

> ![equ](images/00272.jpg)

It is useful to know that a *square* is breezy because we know that the pits cannot move about. Notice that *Breezy* has no time argument.

Having discovered which places are breezy (or smelly) and, very important, *not* breezy (or *not* smelly), the agent can deduce where the pits are (and where the wumpus is). Whereas propositional logic necessitates a separate axiom for each square (see *R*[2] and *R*[3] on [page 247](#index_split_014.html#filepos990777)) and would need a different set of axioms for each geographical layout of the world, first-order logic just needs one axiom:

> ![equ](images/00273.jpg)

Similarly, in first-order logic we can quantify over time, so we need just one successor-state axiom for each predicate, rather than a different copy for each time step. For example, the axiom for the arrow (Equation (7.2) on [page 267](#index_split_014.html#filepos1073936)) becomes

> ![equ](images/00274.jpg)

From these two example sentences, we can see that the first-order logic formulation is no less concise than the original English-language description given in [Chapter 7](#index_split_000.html#filepos939379). The reader is invited to construct analogous axioms for the agent’s location and orientation; in these cases, the axioms quantify over both space and time. As in the case of propositional state estimation, an agent can use logical inference with axioms of this kind to keep track of aspects of the world that are not directly observed. [Chapter 10](#index_split_015.html#filepos1477055) goes into more depth on the subject of first-order successor-state axioms and their uses for constructing plans.

### 8.4 KNOWLEDGE ENGINEERING IN FIRST\-ORDER LOGIC

The preceding section illustrated the use of first-order logic to represent knowledge in three simple domains. This section describes the general process of knowledge-base construction—a process called **knowledge engineering**. A knowledge engineer is someone who investigates a particular domain, learns what concepts are important in that domain, and creates a formal representation of the objects and relations in the domain. We illustrate the knowledge engineering process in an electronic circuit domain that should already be fairly familiar, so that we can concentrate on the representational issues involved. The approach we take is suitable for developing *special-purpose* knowledge bases whose domain is carefully circumscribed and whose range of queries is known in advance. *General-purpose* knowledge bases, which cover a broad range of human knowledge and are intended to support tasks such as natural language understanding, are discussed in [Chapter 12](#index_split_015.html#filepos1750417).

* * *

KNOWLEDGE ENGINEERING

* * *

#### **8.4.1 The knowledge-engineering process**

Knowledge engineering projects vary widely in content, scope, and difficulty, but all such projects include the following steps:

> 1\. *Identify the task.* The knowledge engineer must delineate the range of questions that the knowledge base will support and the kinds of facts that will be available for each specific problem instance. For example, does the wumpus knowledge base need to be able to choose actions or is it required to answer questions only about the contents of the environment? Will the sensor facts include the current location? The task will determine what knowledge must be represented in order to connect problem instances to answers. This step is analogous to the PEAS process for designing agents in [Chapter 2](#index_split_000.html#filepos187684).

> 2\. *Assemble the relevant knowledge.* The knowledge engineer might already be an expert in the domain, or might need to work with real experts to extract what they know—a process called **knowledge acquisition**. At this stage, the knowledge is not represented formally. The idea is to understand the scope of the knowledge base, as determined by the task, and to understand how the domain actually works.

* * *

KNOWLEDGE ACQUISITION

* * *

> For the wumpus world, which is defined by an artificial set of rules, the relevant knowledge is easy to identify. (Notice, however, that the definition of adjacency was not supplied explicitly in the wumpus-world rules.) For real domains, the issue of relevance can be quite difficult—for example, a system for simulating VLSI designs might or might not need to take into account stray capacitances and skin effects.

> 3\. *Decide on a vocabulary of predicates, functions, and constants.* That is, translate the important domain-level concepts into logic-level names. This involves many questions of knowledge-engineering *style*. Like programming style, this can have a significant impact on the eventual success of the project. For example, should pits be represented by objects or by a unary predicate on squares? Should the agent’s orientation be a function or a predicate? Should the wumpus’s location depend on time? Once the choices have been made, the result is a vocabulary that is known as the **ontology** of the domain. The word *ontology* means a particular theory of the nature of being or existence. The ontology determines what kinds of things exist, but does not determine their specific properties and interrelationships.

* * *

ONTOLOGY

* * *

> 4\. *Encode general knowledge about the domain.* The knowledge engineer writes down the axioms for all the vocabulary terms. This pins down (to the extent possible) the meaning of the terms, enabling the expert to check the content. Often, this step reveals misconceptions or gaps in the vocabulary that must be fixed by returning to step 3 and iterating through the process.

> 5\. *Encode a description of the specific problem instance.* If the ontology is well thought out, this step will be easy. It will involve writing simple atomic sentences about instances of concepts that are already part of the ontology. For a logical agent, problem instances are supplied by the sensors, whereas a “disembodied” knowledge base is supplied with additional sentences in the same way that traditional programs are supplied with input data.

> 6\. *Pose queries to the inference procedure and get answers.* This is where the reward is: we can let the inference procedure operate on the axioms and problem-specific facts to derive the facts we are interested in knowing. Thus, we avoid the need for writing an application-specific solution algorithm.

> 7\. *Debug the knowledge base.* Alas, the answers to queries will seldom be correct on the first try. More precisely, the answers will be correct *for the knowledge base as written*, assuming that the inference procedure is sound, but they will not be the ones that the user is expecting. For example, if an axiom is missing, some queries will not be answerable from the knowledge base. A considerable debugging process could ensue. Missing axioms or axioms that are too weak can be easily identified by noticing places where the chain of reasoning stops unexpectedly. For example, if the knowledge base includes a diagnostic rule (see Exercise 8.13) for finding the wumpus,

> ![equ](images/00275.jpg)

> instead of the biconditional, then the agent will never be able to prove the *absence* of wumpuses. Incorrect axioms can be identified because they are false statements about the world. For example, the sentence

> ![equ](images/00276.jpg)

![hand](images/00006.jpg)

> is false for reptiles, amphibians, and, more importantly, tables. *The falsehood of this sentence can be determined independently of the rest of the knowledge base.* In contrast, a typical error in a program looks like this:

> `offset = position + 1`.

> It is impossible to tell whether this statement is correct without looking at the rest of the program to see whether, for example, `offset` is used to refer to the current position, or to one beyond the current position, or whether the value of `position` is changed by another statement and so `offset` should also be changed again.

To understand this seven-step process better, we now apply it to an extended example—the domain of electronic circuits.

#### **8.4.2 The electronic circuits domain**

We will develop an ontology and knowledge base that allow us to reason about digital circuits of the kind shown in [Figure 8.6](#index_split_015.html#filepos1250106). We follow the seven-step process for knowledge engineering.

##### **Identify the task**

There are many reasoning tasks associated with digital circuits. At the highest level, one analyzes the circuit’s functionality. For example, does the circuit in [Figure 8.6](#index_split_015.html#filepos1250106) actually add properly? If all the inputs are high, what is the output of gate A2? Questions about the circuit’s structure are also interesting. For example, what are all the gates connected to the first input terminal? Does the circuit contain feedback loops? These will be our tasks in this section. There are more detailed levels of analysis, including those related to timing delays, circuit area, power consumption, production cost, and so on. Each of these levels would require additional knowledge.

##### **Assemble the relevant knowledge**

> ![image](images/00277.jpg)

> **Figure 8.6** A digital circuit C1, purporting to be a one-bit full adder. The first two inputs are the two bits to be added, and the third input is a carry bit. The first output is the sum, and the second output is a carry bit for the next adder. The circuit contains two XOR gates, two AND gates, and one OR gate.

What do we know about digital circuits? For our purposes, they are composed of wires and gates. Signals flow along wires to the input terminals of gates, and each gate produces a signal on the output terminal that flows along another wire. To determine what these signals will be, we need to know how the gates transform their input signals. There are four types of gates: AND, OR, and XOR gates have two input terminals, and NOT gates have one. All gates have one output terminal. Circuits, like gates, have input and output terminals.

To reason about functionality and connectivity, we do not need to talk about the wires themselves, the paths they take, or the junctions where they come together. All that matters is the connections between terminals—we can say that one output terminal is connected to another input terminal without having to say what actually connects them. Other factors such as the size, shape, color, or cost of the various components are irrelevant to our analysis.

If our purpose were something other than verifying designs at the gate level, the ontology would be different. For example, if we were interested in debugging faulty circuits, then it would probably be a good idea to include the wires in the ontology, because a faulty wire can corrupt the signal flowing along it. For resolving timing faults, we would need to include gate delays. If we were interested in designing a product that would be profitable, then the cost of the circuit and its speed relative to other products on the market would be important.

##### **Decide on a vocabulary**

We now know that we want to talk about circuits, terminals, signals, and gates. The next step is to choose functions, predicates, and constants to represent them. First, we need to be able to distinguish gates from each other and from other objects. Each gate is represented as an object named by a constant, about which we assert that it is a gate with, say, *Gate*(*X*[1]). The behavior of each gate is determined by its type: one of the constants *AND*, *OR*, *XOR*, or *NOT*. Because a gate has exactly one type, a function is appropriate: *Type*(*X*[1])= *XOR*. Circuits, like gates, are identified by a predicate: *Circuit*(C[1]).

Next we consider terminals, which are identified by the predicate *Terminal*(*x*). Agate or circuit can have one or more input terminals and one or more output terminals. We use the function *In*(1, *X*[1]) to denote the first input terminal for gate *X*[1]. A similar function Out is used for output terminals. The function *Arity*(*c*, *i*, *j*) says that circuit *c* has *i* input and j output terminals. The connectivity between gates can be represented by a predicate, Connected, which takes two terminals as arguments, as in *Connected*(*Out*(1, *X*[1]), *In*(1, *X*[2])).

Finally, we need to know whether a signal is on or off. One possibility is to use a unary predicate, *On*(*t*), which is true when the signal at a terminal is on. This makes it a little difficult, however, to pose questions such as “What are all the possible values of the signals at the output terminals of circuit *C*[1] ?” We therefore introduce as objects two signal values, 1 and 0, and a function *Signal*(*t*) that denotes the signal value for the terminal *t*.

##### **Encode general knowledge of the domain**

One sign that we have a good ontology is that we require only a few general rules, which can be stated clearly and concisely. These are all the axioms we will need:

> 1\. If two terminals are connected, then they have the same signal:

> ![equ](images/00278.jpg)

> 2\. The signal at every terminal is either 1 or 0:

> ![equ](images/00279.jpg)

> 3\. Connected is commutative:

> ![equ](images/00280.jpg)

> 4\. There are four types of gates:

> ![equ](images/00281.jpg)

> 5\. An AND gate’s output is 0 if and only if any of its inputs is 0:

> ![equ](images/00282.jpg)

> 6\. An OR gate’s output is 1 if and only if any of its inputs is 1:

> ![equ](images/00283.jpg)

> 7\. An XOR gate’s output is 1 if and only if its inputs are different:

> ![equ](images/00284.jpg)

> 8\. A NOT gate’s output is different from its input:

> ![equ](images/00285.jpg)

> 9\. The gates (except for NOT) have two inputs and one output.

> ![equ](images/00286.jpg)

> 10\. A circuit has terminals, up to its input and output arity, and nothing beyond its arity:

> ![equ](images/00287.jpg)

> 11\. Gates, terminals, signals, gate types, and Nothing are all distinct.

> ![equ](images/00288.jpg)

> 12\. Gates are circuits.

> ![equ](images/00289.jpg)

##### **Encode the specific problem instance**

The circuit shown in [Figure 8.6](#index_split_015.html#filepos1250106) is encoded as circuit *C*[1] with the following description. First, we categorize the circuit and its component gates:

> ![equ](images/00290.jpg)

Then, we show the connections between them:

> ![equ](images/00291.jpg)

##### **Pose queries to the inference procedure**

What combinations of inputs would cause the first output of C[1] (the sum bit) to be 0 and the second output of C[1] (the carry bit) to be 1?

> ![equ](images/00292.jpg)

The answers are substitutions for the variables *i*[1], *i*[2], and *i*[3] such that the resulting sentence is entailed by the knowledge base. ASKVARS will give us three such substitutions:

> ![equ](images/00293.jpg)

What are the possible sets of values of all the terminals for the adder circuit?

> ![equ](images/00294.jpg)

This final query will return a complete input–output table for the device, which can be used to check that it does in fact add its inputs correctly. This is a simple example of **circuit verification**. We can also use the definition of the circuit to build larger digital systems, for which the same kind of verification procedure can be carried out. (See Exercise 8.26.) Many domains are amenable to the same kind of structured knowledge-base development, in which more complex concepts are defined on top of simpler concepts.

* * *

CIRCUIT VERIFICATION

* * *

##### **Debug the knowledge base**

We can perturb the knowledge base in various ways to see what kinds of erroneous behaviors emerge. For example, suppose we fail to read [Section 8.2.8](#index_split_000.html#filepos1207340) and hence forget to assert that 1 ≠ 0. Suddenly, the system will be unable to prove any outputs for the circuit, except for the input cases 000 and 110. We can pinpoint the problem by asking for the outputs of each gate. For example, we can ask

> ![equ](images/00295.jpg)

which reveals that no outputs are known at *X*[1] for the input cases 10 and 01. Then, we look at the axiom for XOR gates, as applied to *X*[1]:

> ![equ](images/00296.jpg)

If the inputs are known to be, say, 1 and 0, then this reduces to

> ![equ](images/00297.jpg)

Now the problem is apparent: the system is unable to infer that *Signal*(*Out*(1, *X*[1])) = 1, so we need to tell it that 1 ≠ 0.

### 8.5 SUMMARY

This chapter has introduced **first-order logic**, a representation language that is far more powerful than propositional logic. The important points are as follows:

> • Knowledge representation languages should be declarative, compositional, expressive, context independent, and unambiguous.

> • Logics differ in their **ontological commitments** and **epistemological commitments**. While propositional logic commits only to the existence of facts, first-order logic commits to the existence of objects and relations and thereby gains expressive power.

> • The syntax of first-order logic builds on that of propositional logic. It adds terms to represent objects, and has universal and existential quantifiers to construct assertions about all or some of the possible values of the quantified variables.

> • A **possible world**,or **model**, for first-order logic includes a set of objects and an **interpretation** that maps constant symbols to objects, predicate symbols to relations among objects, and function symbols to functions on objects.

> • An atomic sentence is true just when the relation named by the predicate holds between the objects named by the terms. **Extended interpretations**, which map quantifier variables to objects in the model, define the truth of quantified sentences.

> • Developing a knowledge base in first-order logic requires a careful process of analyzing the domain, choosing a vocabulary, and encoding the axioms required to support the desired inferences.

### BIBLIOGRAPHICAL AND HISTORICAL NOTES

Although Aristotle’s logic deals with generalizations over objects, it fell far short of the expressive power of first-order logic. A major barrier to its further development was its concentration on one-place predicates to the exclusion of many-place relational predicates. The first systematic treatment of relations was given by Augustus De Morgan (1864), who cited the following example to show the sorts of inferences that Aristotle’s logic could not handle: “All horses are animals; therefore, the head of a horse is the head of an animal.” This inference is inaccessible to Aristotle because any valid rule that can support this inference must first analyze the sentence using the two-place predicate “x is the head of *y*.” The logic of relations was studied in depth by Charles Sanders Peirce (1870, 2004).

True first-order logic dates from the introduction of quantifiers in Gottlob Frege’s (1879) *Begriffschrift* (“Concept Writing” or “Conceptual Notation”). Peirce (1883) also developed first-order logic independently of Frege, although slightly later. Frege’s ability to nest quantifiers was a big step forward, but he used an awkward notation. The present notation for first-order logic is due substantially to Giuseppe Peano (1889), but the semantics is virtually identical to Frege’s. Oddly enough, Peano’s axioms were due in large measure to Grassmann (1861) and Dedekind (1888).

Leopold Löwenheim (1915) gave a systematic treatment of model theory for first-order logic, including the first proper treatment of the equality symbol. Löwenheim’s results were further extended by Thoralf Skolem (1920). Alfred Tarski (1935, 1956) gave an explicit definition of truth and model-theoretic satisfaction in first-order logic, using set theory.

McCarthy (1958) was primarily responsible for the introduction of first-order logic as a tool for building AI systems. The prospects for logic-based AI were advanced significantly by Robinson’s (1965) development of resolution, a complete procedure for first-order inference described in [Chapter 9](#index_split_015.html#filepos1300686). The logicist approach took root at Stanford University. Cordell Green (1969a, 1969b) developed a first-order reasoning system, QA3, leading to the first attempts to build a logical robot at SRI (Fikes and Nilsson, 1971). First-order logic was applied by Zohar Manna and Richard Waldinger (1971) for reasoning about programs and later by Michael Genesereth (1984) for reasoning about circuits. In Europe, logic programming (*a* restricted form of first-order reasoning) was developed for linguistic analysis (Colmerauer **et al.**, 1973) and for general declarative systems (Kowalski, 1974). Computational logic was also well entrenched at Edinburgh through the LCF (Logic for Computable Functions) project (Gordon **et al.**, 1979). These developments are chronicled further in [Chapters 9](#index_split_015.html#filepos1300686) and [12](#index_split_015.html#filepos1750417).

Practical applications built with first-order logic include a system for evaluating the manufacturing requirements for electronic products (Mannion, 2002), a system for reasoning about policies for file access and digital rights management (Halpern and Weissman, 2008), and a system for the automated composition of Web services (McIlraith and Zeng, 2001).

Reactions to the Whorf hypothesis (Whorf, 1956) and the problem of language and thought in general, appear in several recent books (Gumperz and Levinson, 1996; Bowerman and Levinson, 2001; Pinker, 2003; Gentner and Goldin-Meadow, 2003). The “theory” theory (Gopnik and Glymour, 2002; Tenenbaum **et al.**, 2007) views children’s learning about the world as analogous to the construction of scientific theories. Just as the predictions of a machine learning algorithm depend strongly on the vocabulary supplied to it, so will the child’s formulation of theories depend on the linguistic environment in which learning occurs.

There are a number of good introductory texts on first-order logic, including some by leading figures in the history of logic: Alfred Tarski (1941), Alonzo Church (1956), and W.V. Quine (1982) (which is one of the most readable). Enderton (1972) gives a more mathematically oriented perspective. A highly formal treatment of first-order logic, along with many more advanced topics in logic, is provided by Bell and Machover (1977). Manna and Waldinger (1985) give a readable introduction to logic from a computer science perspective, as do Huth and Ryan (2004), who concentrate on program verification. Barwise and Etchemendy (2002) take an approach similar to the one used here. Smullyan (1995) presents results concisely, using the tableau format. Gallier (1986) provides an extremely rigorous mathematical exposition of first-order logic, along with a great deal of material on its use in automated reasoning. *Logical Foundations of Artificial Intelligence* (Genesereth and Nilsson, 1987) is both a solid introduction to logic and the first systematic treatment of logical agents with percepts and actions, and there are two good handbooks: van Bentham and ter Meulen (1997) and Robinson and Voronkov (2001). The journal of record for the field of pure mathematical logic is the *Journal of Symbolic Logic*, whereas the *Journal of Applied Logic* deals with concerns closer to those of artificial intelligence.

### EXERCISES

**8.1** A logical knowledge base represents the world using a set of sentences with no explicit structure. An **analogical** representation, on the other hand, has physical structure that corresponds directly to the structure of the thing represented. Consider a road map of your country as an analogical representation of facts about the country—it represents facts with a map language. The two-dimensional structure of the map corresponds to the two-dimensional surface of the area.

> **a**. Give five examples of *symbols* in the map language.

> **b**. An *explicit* sentence is a sentence that the creator of the representation actually writes down. An *implicit* sentence is a sentence that results from explicit sentences because of properties of the analogical representation. Give three examples each of *implicit* and *explicit* sentences in the map language.

> **c**. Give three examples of facts about the physical structure of your country that cannot be represented in the map language.

> **d**. Give two examples of facts that are much easier to express in the map language than in first-order logic.

> **e**. Give two other examples of useful analogical representations. What are the advantages and disadvantages of each of these languages?

**8.2** Consider a knowledge base containing just two sentences: *P* (a) and *P* (*b*). Does this knowledge base entail ∀*x* *P*(*x*)? Explain your answer in terms of models.

**8.3** Is the sentence ∃ *x*, *y* *x* = *y* valid? Explain.

**8.4** Write down a logical sentence such that every world in which it is true contains exactly one object.

**8.5** Consider a symbol vocabulary that contains c constant symbols, *p*[*k*] predicate symbols of each arity *k*, and *f*[*k*] function symbols of each arity *k*, where 1 ≤ *k* ≤ *A*. Let the domain size be fixed at *D*. For any given model, each predicate or function symbol is mapped onto a relation or function, respectively, of the same arity. You may assume that the functions in the model allow some input tuples to have no value for the function (i.e., the value is the invisible object). Derive a formula for the number of possible models for a domain with *d* elements. Don’t worry about eliminating redundant combinations.

**8.6** Which of the following are valid (necessarily true) sentences?

> **a**. (∃*x* *x* = *x*) ⇒ (∀ *y* ∃*z* *y* = *z*).

> **b**. ∀ *x* *P* (*x*) ⋁¬*P*(*x*).

> **c**. ∀ *x* Smart(*x*) ⋁ (*x* = *x*).

**8.7** Consider a version of the semantics for first-order logic in which models with empty domains are allowed. Give at least two examples of sentences that are valid according to the

standard semantics but not according to the new semantics. Discuss which outcome makes more intuitive sense for your examples.

**8.8** Does the fact ¬*Spouse*(*George*, *Laura*) follow from the facts *Jim* ≠ *George* and *Spouse*(*Jim*, *Laura*)? If so, give a proof; if not, supply additional axioms as needed. What happens if we use *Spouse* as a unary function symbol instead of a binary predicate?

**8.9** This exercise uses the function *MapColor* and predicates *In*(*x*, *y*), *Borders*(*x*, *y*), and *Country*(*x*), whose arguments are geographical regions, along with constant symbols for various regions. In each of the following we give an English sentence and a number of candidate logical expressions. For each of the logical expressions, state whether it (1) correctly expresses the English sentence; (2) is syntactically invalid and therefore meaningless; or (3) is syntactically valid but does not express the meaning of the English sentence.

> **a**. Paris and Marseilles are both in France.

> (i) *In*(*Paris* ̂ *Marseilles*, *France*).

> (ii) *In*(*Paris*, *France*) ̂ *In*(*Marseilles*, *France*).

> (iii) *In*(*Paris*, *France*) ⋁ *In*(*Marseilles*, *France*).

> **b**. There is a country that borders both Iraq and Pakistan.

> (i) ∃ *c* *Country*(*c*) ̂ *Border* (*c*, *Iraq*) ̂ *Border* (*c*, *Pakistan*).

> (ii) ∃ *c* *Country*(*c*) ⇒ \[*Border* (*c*, *Iraq*) ̂ *Border* (*c*, *Pakistan*)\].

> (iii) \[∃ *c* *Country*(*c*)\] ⇒ \[*Border* (*c*, *Iraq*) ̂ *Border* (*c*, *Pakistan*)\].

> (iv) ∃ *c* *Border* (*Country*(*c*), *Iraq* ̂ *Pakistan*).

> **c**. All countries that border Ecuador are in South America.

> (i) ∀ *c* *Country*(*c*) ̂ *Border* (*c*, *Ecuador*) ⇒ *In*(*c*, *SouthAmerica*).

> (ii) ∀ *c* *Country*(*c*) ⇒ \[*Border* (*c*, *Ecuador*) ⇒ *In*(*c*, *SouthAmerica*)\].

> (iii) ∀ *c* \[*Country*(*c*) ⇒ *Border* (*c*, *Ecuador*)\] ⇒ *In*(*c*, *SouthAmerica*).

> (iv) ∀ *c* *Country*(*c*) ̂ *Border* (*c*, *Ecuador*) ̂ *In*(*c*, *SouthAmerica*).

> **d**. No region in South America borders any region in Europe.

> (i) ¬\[∃ *c*, *d* *In*(*c*, *SouthAmerica*) ̂ *In*(*d*, *Europe*) ̂ *Borders*(*c*, *d*)\].

> (ii) ∀ *c*, *d* \[*In*(*c*, *SouthAmerica*) ̂ *In*(*d*, *Europe*)\] ⇒ ¬*Borders*(*c*, *d*)\].

> (iii) ¬∀ *c* *In*(*c*, *SouthAmerica*) ⇒ ∃ *d* *In*(*d*, *Europe*) ̂ ¬*Borders*(*c*, *d*).

> (iv) ∀ *c* *In*(*c*, *SouthAmerica*) ⇒ ∀ *d* *In*(*d*, *Europe*) ⇒ ¬*Borders*(*c*, *d*).

> **e**. No two adjacent countries have the same map color.

> (i) ∀ *x*, *y* ¬*Country*(*x*) ⋁¬*Country*(*y*) ⋁¬*Borders*(*x*, *y*) ⋁ ¬(*MapColor*(*x*) = *MapColor*(*y*)).

> (ii) ∀ *x*, *y* (*Country*(*x*) ̂ *Country*(*y*) ̂ *Borders*(*x*, *y*) ̂¬(*x* = *y*)) ⇒ ¬(*MapColor* (*x*) = *MapColor* (*y*)).

> (iii) ∀ *x*, *y* *Country*(*x*) ̂ *Country*(*y*) ̂ *Borders*(*x*, *y*) ̂ ¬(*MapColor*(*x*) = *MapColor*(*y*)).

> (iv) ∀ *x*, *y* (*Country*(*x*) ̂ *Country*(*y*) ̂ *Borders*(*x*, *y*)) ⇒ *MapColor*(*x* = *y*).

**8.10** Consider a vocabulary with the following symbols:

> *Occupation*(*p*, *o*): Predicate. Person *p* has occupation *o*.

> *Customer* (*p*1, *p*2): Predicate. Person *p*1 is a customer of person *p*2.

> *Boss*(*p*1, *p*2): Predicate. Person *p*1 is a boss of person *p*2.

> *Doctor*, *Surgeon*, *Lawyer*, *Actor*: Constants denoting occupations.

> *Emily*, *Joe*: Constants denoting people.

Use these symbols to write the following assertions in first-order logic:

> **a**. Emily is either a surgeon or a lawyer.

> **b**. Joe is an actor, but he also holds another job.

> **c**. All surgeons are doctors.

> **d**. Joe does not have a lawyer (i.e., is not a customer of any lawyer).

> **e**. Emily has a boss who is a lawyer.

> **f**. There exists a lawyer all of whose customers are doctors.

> **g**. Every surgeon has a lawyer.

**8.11** Complete the following exercises about logical senntences:

> **a**. Translate into *good, natural* English (no xsor ys!):

> ![equ](images/00298.jpg)

> **b**. Explain why this sentence is entailed by the sentence

> ![equ](images/00299.jpg)

> **c**. Translate into first-order logic the following sentences:

> (i) Understanding leads to friendship.

> (ii) Friendship is transitive.

> Remember to define all predicates, functions, and constants you use.

**8.12** Rewrite the first two Peano axioms in [Section 8.3.3](#index_split_000.html#filepos1223866) as a single axiom that defines NatNum(*x*) so as to exclude the possibility of natural numbers except for those generated by the successor function.

**8.13** Equation (8.4) on [page 306](#index_split_015.html#filepos1235600) defines the conditions under which a square is breezy. Here we consider two other ways to describe this aspect of the wumpus world.

> **a**. We can write **diagnostic rules** leading from observed effects to hidden causes. For finding pits, the obvious diagnostic rules say that if a square is breezy, some adjacent square must contain a pit; and if a square is not breezy, then no adjacent square contains a pit. Write these two rules in first-order logic and show that their conjunction is logically equivalent to Equation (8.4).

> **b**. We can write **causal rules** leading from cause to effect. One obvious causal rule is that a pit causes all adjacent squares to be breezy. Write this rule in first-order logic, explain why it is incomplete compared to Equation (8.4), and supply the missing axiom.

* * *

DIAGNOSTIC RULE

* * *

* * *

CAUSAL RULE

* * *

> ![image](images/00300.jpg)

> **Figure 8.7** A typical family tree. The symbol “⋈” connects spouses and arrows point to children.

**8.14** Write axioms describing the predicates *Grandchild, Greatgrandparent, Ancestor, Brother, Sister, Da*