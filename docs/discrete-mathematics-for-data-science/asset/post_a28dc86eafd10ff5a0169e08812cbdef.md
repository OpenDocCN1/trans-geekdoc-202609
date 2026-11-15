
## DISCRETE MATHEMATICS FOR DATA SCIENCE

![](img/ff796e63b14a88ab72583e78f3994e90_0_0.png)

Jack Pope

## DISCRETE MATHEMATICS FOR DATA SCIENCE

![](img/ff796e63b14a88ab72583e78f3994e90_1_0.png)

Jack Pope

## Discrete Mathematics for Data Science

*Discrete Mathematics for Data Science* provides an early course in both Data Science and Discrete Mathematics, focusing on how a deeper understanding of the former can unlock a more effective implementation of the latter. Students of Data Science come from a variety of disciplines, with Business, Statistics, Computer Science, Economics, and Psychology among the departments offering courses on the subject. Therefore, for many students, Data Science is considered a means of insight into a particular field of interest, with the study of its underlying discrete mathematics not a primary objective.

This book covers the topics of Discrete Mathematical Structures relevant to students of Data Science, offering a relevant and gentle introduction to both the theoretical and practical elements required to be a successful data scientist. The relaxed, accessible style makes it a perfect textbook for undergraduates.

## Features

- Numerous exercises and examples.
- Ideal as a textbook for a Discrete Mathematics course for data science and computer science students.
- Source code and solutions provided as a supplementary resource.

**Jack Pope** has wrangled financial data since *Big Data* meant a big pile of floppy disks. He works at Investment Economics (aka, System Goats) providing system configuration, guidance, and training for organizations interested in data science infrastructure. He is also department coordinator for Computer Science and Data Science at North Hennepin Community College and chairman of the Twin Cities IEEE Computer Society.

## Discrete Mathematics for Data Science

Jack Pope

## CRC Press
Taylor & Francis Group
Boca Raton London New York

CRC Press is an imprint of the Taylor & Francis Group, an informa business

A CHAPMAN & HALL BOOK

Designed cover image: [vectorstock.com](vectorstock.com)

First edition published 2026
by CRC Press
2385 NW Executive Center Drive, Suite 320, Boca Raton, FL 33431

and by CRC Press
4 Park Square, Milton Park, Abingdon, Oxon, OX14 4RN

*CRC Press is an imprint of Taylor & Francis Group, LLC*

© 2026 Jack Pope

Reasonable efforts have been made to publish reliable data and information, but the author and publisher cannot assume responsibility for the validity of all materials or the consequences of their use. The authors and publishers have attempted to trace the copyright holders of all material reproduced in this publication and apologize to copyright holders if permission to publish in this form has not been obtained. If any copyright material has not been acknowledged, please write and let us know so we may rectify in any future reprint.

Except as permitted under U.S. Copyright Law, no part of this book may be reprinted, reproduced, transmitted, or utilized in any form by any electronic, mechanical, or other means, now known or hereafter invented, including photocopying, microfilming, and recording, or in any information storage or retrieval system, without written permission from the publishers.

For permission to photocopy or use material electronically from this work, access [www.copyright.com](www.copyright.com) or contact the Copyright Clearance Center, Inc. (CCC), 222 Rosewood Drive, Danvers, MA 01923, 978-750-8400. For works that are not available on CCC, please contact mpkbookspermissions@tandf.co.uk

For Product Safety Concerns and Information please contact our EU representative GPSR@taylorandfrancis.com. Taylor & Francis Verlag GmbH, Kaufingerstraße 24, 80331 München, Germany.

Trademark notice: Product or corporate names may be trademarks or registered trademarks and are used only for identification and explanation without intent to infringe.

ISBN: 978-1-032-68722-3 (hbk)
ISBN: 978-1-032-68773-5 (pbk)
ISBN: 978-1-032-68775-9 (ebk)

DOI: 10.1201/9781032687759

Typeset in Latin Modern font by KnowledgeWorks Global Ltd.

Publisher's note: This book has been prepared from camera-ready copy provided by the authors.

## For Lisa

## Contents

- List of Figures
- List of Tables
- Preface
- 0.1 THE PURPOSE OF THIS BOOK
- 0.1.1 Context
- 0.1.2 History & Human Nature
- 0.2 PREREQUISITE KNOWLEDGE
- 0.3 UNIX
- 0.3.1 Coding Conventions
- 0.4 AUTHOR BIOGRAPHY
- Acknowledgments

## SECTION I Problem Solving

### CHAPTER 1 Your Mind: A Programming Environment

- 1.1 PSEUDO CODE
- 1.2 SYSTEMATIZING PROBLEMS VIA CODE
- 1.3 DATA CONFUSION
- 1.4 ERRONEOUS PROBLEMS & EXPENSIVE SOLUTIONS
- 1.5 PROBLEM-SOLVING AMID COMPLEXITY
- 1.6 CHALLENGES WITH PROBLEM SOLVING
- 1.7 MENTAL CONDITIONING FOR PROBLEM SOLVING
- 1.8 BOOKS FOR PROBLEM SOLVING

## SECTION II Elements

### CHAPTER 2 Atoms & Abstractions

- 2.1 THE MEANING OF DATA
- 2.1.1 Atomic Data
- 2.1.2 Abstract Data
- 2.2 ABSTRACT FUNCTIONS

### CHAPTER 3 Numbers

- 3.1 NUMBER CLASSIFICATIONS
- 3.2 COMPUTER NUMBERS
- 3.3 FILE EXTENSIONS
- 3.4 COMPUTER NUMBER TERMINOLOGY
- 3.5 NUMBER BASE NOTATION
- 3.6 COMPUTER TERMINOLOGY VS MATH TERMINOLOGY

### CHAPTER 4 Number Conversion

- 4.1 BASE CONVERSIONS
- 4.1.1 The Power Method
- 4.1.2 The Remainder Method
- 4.2 BINARY CODED DECIMAL (BCD)
- 4.3 EXAMPLE PROBLEMS
- 4.4 MACHINE REPRESENTATION OF NEGATIVE NUMBERS
- 4.5 THE IEEE 754 FLOATING POINT STANDARD
- 4.6 SIMPLISTIC CONVERSIONS
- 4.7 CHECKING YOUR NUMBER CONVERSIONS

### CHAPTER 5 Digital Arithmetic & Logic

- 5.1 BINARY ADDITION
- 5.2 BINARY SUBTRACTION
- 5.3 BINARY MULTIPLICATION
- 5.4 BINARY DIVISION
- 5.5 BOOLEAN LOGIC
- 5.6 MACHINE APPROACHES TO MULTIPLICATION & DIVISION
- 5.7 BINARY SUBTRACTION USING ONE'S COMPLEMENT
- 5.8 BINARY SUBTRACTION USING TWO'S COMPLEMENT
- 5.9 SHIFTERS FOR MULTIPLICATION AND DIVISION
- 5.10 MULTIPLICATION BY LEFT-SHIFT & ADDITION
- 5.11 DIVISION BY RIGHT-SHIFT & SUBTRACT
- 5.12 PRECISION LOSS WITH RIGHT SHIFT
- 5.13 ARITHMETIC ON IEEE 754 FRACTIONAL VALUES
- 5.14 DIVISION WITH IEEE 754 FLOATING POINT NUMBERS

## SECTION III Computational Logic

### CHAPTER 6 Propositional Logic

- 6.1 PROPOSITION
- 6.2 SYLLOGISMS
- 6.3 PROPOSITIONAL CONDITIONS
- 6.4 COMPOUND PROPOSITIONS
- 6.5 EQUATION MINIMIZATION
- 6.6 TIPS FOR EQUATION MINIMIZATION
- 6.7 SELECTED PATTERNS OF INFERENCE FOR EQUATION MINIMIZATION

### CHAPTER 7 Set Quantification

- 7.1 SETS
- 7.2 SET TYPES
- 7.3 QUANTIFICATION
- 7.4 SET RELATIONS
- 7.4.1 Domain and Range of Set Relations
- 7.5 TYPES OF SET RELATIONS
- 7.5.1 Inverse Relations
- 7.5.2 Identity Relations
- 7.5.3 Reflexive Relations
- 7.5.4 Symmetric Relations
- 7.5.5 Transitive Relations
- 7.5.6 Equality & Equivalence in Set Relations
- 7.6 VISUALIZING SET RELATIONS
- 7.7 VENN DIAGRAMS OF SETS
- 7.8 PROGRAMMATIC TREATMENT OF SETS AS LISTS

### CHAPTER 8 Proof

- 8.1 PROOFS FOR SETS
- 8.2 DEFINITIONS
- 8.3 SUBSET PROOFS
- 8.4 SET EQUALITY
- 8.5 SET EMPTINESS
- 8.6 CONDITIONAL PROOFS
- 8.7 PROOF TECHNIQUES
- 8.8 QUANTIFICATION PROOFS
- 8.9 RECURSION & PROOF BY INDUCTION
- 8.10 INDUCTION EXAMPLES

### CHAPTER 9 Computability

- 9.1 NP-COMPLETENESS
- 9.2 PROGRAMMING LANGUAGE ELEMENTS
- 9.3 LANGUAGE SYMBOLS
- 9.4 A MACHINE
- 9.5 PUSH DOWN AUTOMATON

## SECTION IV Functions

### CHAPTER 10 Functions & Abstractions

- 10.1 AXIOMATIC FOUNDATIONS
- 10.2 PEANO'S AXIOMS
- 10.3 FUNCTIONS
- 10.4 RANGE, IMAGE, & CODOMAIN
- 10.5 TYPES OF FUNCTIONS
- 10.6 INVERSE FUNCTIONS
- 10.7 FUNCTION COMPOSITION
- 10.8 FUNCTION ABSTRACTION
- 10.9 CURRYING

### CHAPTER 11 Repetition & Recursion

- 11.1 RECURSION
- 11.2 INFINITE CYCLES
- 11.3 PEANO'S RECURSIVE LOGIC
- 11.4 RECURRENCE RELATION
- 11.5 TRACKING RECURSION USING A STACK
- 11.6 WHEN TO USE RECURSION
- 11.7 ADDITIONAL EXAMPLES OF RECURSIVE ALGORITHMS

### CHAPTER 12 Lambda Calculus

- 12.1 LAMBDA λ CALCULUS
- 12.2 FUNCTION APPLICATION
- 12.3 APPLICABLE ORDER
- 12.4 REDUCTION & CONVERSION
- 12.4.1 Other Conversions
- 12.5 COMPUTING WITH LAMBDA CALCULUS
- 12.5.1 Boolean Functions
- 12.6 COMBINATORS

### CHAPTER 13 Algorithm Complexity

- 13.1 ALGORITHM ANALYSIS
- 13.2 BIG-O NOTATION
- 13.2.1 Big-O: The Worst Case Scenario
- 13.2.2 Worst vs Average vs Best Case Scenarios
- 13.2.3 Algorithm Efficiency vs Elegance
- 13.2.4 Big-O Cases
- 13.3 TIMING COMPUTATION

## SECTION V Data Organization

### CHAPTER 14 Data Organization
