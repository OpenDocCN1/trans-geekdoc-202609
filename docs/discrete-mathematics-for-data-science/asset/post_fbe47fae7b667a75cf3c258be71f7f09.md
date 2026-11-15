
## 14.1 DATA ORGANIZATION

## 14.2 ORDERING

### 14.2.1 Element Access

## 14.3 COLLECTION OPERATIONS

## 14.4 RELAXED PROPERTIES

## 14.5 UNCONNECTED DATA COLLECTIONS

## 14.6 LINEAR STRUCTURES

## 14.7 BRANCHED STRUCTURES

## 14.8 DATA COLLECTION SUMMARY TABLE

## CHAPTER 15 ■ Unconnected Data

### 15.1 BAGS VERSUS SETS

### 15.2 RANDOM SELECTIONS OF DATA

### 15.3 UNIFORM RANDOM DISTRIBUTION

### 15.4 PSEUDO-RANDOM NUMBER FUNCTIONS

### 15.5 EVALUATING PSEUDO RANDOM NUMBERS

## CHAPTER 16 ■ Linear Structures

### 16.1 PROPERTIES OF LISTS

### 16.2 STANDARD LIST OPERATIONS

### 16.3 RANDOM ACCESS & SORTED LIST

### 16.4 LISTS OF LISTS

### 16.5 LISTS OF ABSTRACT DATA TYPES

### 16.6 LIST IMPLEMENTATION OF A STACK

### 16.7 POSTFIX EXPRESSIONS

### 16.8 LIST IMPLEMENTATION OF A QUEUE

### 16.9 SIMPLE SEARCHING & SORTING ALGORITHMS

## CHAPTER 17 Branched Structures

### 17.1 REVIEW OF LIST OBJECTS

### 17.2 TREES

### 17.2.1 Computations for Trees

### 17.2.2 Binary Tree Traversal Patterns

### 17.2.3 Parse Tree Evaluation

### 17.2.4 Binary Search Tree

### 17.2.5 Tree Glossary

### 17.3 GRAPHS

### 17.3.1 Computations for Graphs

### 17.3.2 Graphs as Relations

### 17.3.3 Quantifying an Undirected Graph

### 17.3.4 Graph as Adjacency Matrix

### 17.3.5 Graph as Adjacency List

### 17.3.6 Graph Traversal

### 17.3.7 Graph Paths

### 17.3.8 Computing Distance

### 17.3.9 Generating Graph Objects

### 17.3.10 Graph Glossary

## SECTION VI Data Analysis

## CHAPTER 18 ■ Counting: Permutations & Combinations

### 18.1 BASIC COUNTING

### 18.2 FACTORIALS

### 18.3 PERMUTATIONS

### 18.4 COMBINATIONS

### 18.5 MULTISETS

## CHAPTER 19 ■ Probability & Statistics

### 19.1 PROBABILITY

### 19.1.1 Sample Space & Events

### 19.1.2 Mutually Exclusive Events

### 19.1.3 Independent Events

### 19.1.4 Joint Probability

### 19.1.5 Conditional Probability

### 19.2 STATISTICS

### 19.2.1 Measures of Central Tendency

### 19.2.2 Measures of Variability

### 19.2.3 Measures of Position

### 19.2.4 Weighted Mean

## CHAPTER 20 ■ Multivariate Analysis

### 20.1 THE PEARSON CORRELATION COEFFICIENT

### 20.2 REGRESSION

### 20.3 LINE FITTING

### 20.3.1 Perspective on b₁.

### 20.3.2 More Sums of Squares

### 20.4 COEFFICIENT OF DETERMINATION, R²

### 20.5 MULTIPLE LINEAR REGRESSION

### 20.6 TESTING THE SIGNIFICANCE OF REGRESSION VARIABLES

### 20.6.1 Analysis of Variance Table

## CHAPTER 21 ■ Resampling

### 21.1 RANDOM SAMPLES

### 21.2 RESAMPLING

### 21.3 EVALUATING ESTIMATES

## CHAPTER 22 ■ Information Theory

### 22.1 INFORMATION THEORY

### 22.2 ENTROPY

### 22.3 MESSAGES OF MULTIPLE SYMBOLS

### 22.4 SYMBOL PROBABILITIES

### 22.5 JOINT ENTROPY

### 22.6 CONDITIONAL ENTROPY

### 22.7 MUTUAL INFORMATION

### 22.8 NOISE, ERROR DETECTION & CORRECTION

### 22.9 CHANNEL CAPACITY

### 22.10 DATA COMPRESSION & HUFFMAN ENCODING

## CHAPTER 23 ■ Data Dimensions

### 23.1 HIGHLY DIMENSIONAL DATA

### 23.2 MULTICOLLINEARITY

### 23.3 INVESTMENT PORTFOLIO EXAMPLE

### 23.4 SAMPLE DENSITY

### 23.5 GENERALIZATION VERSUS OVER-FITTING

## SECTION VII Appendix

## APPENDIX A ■ Coding Conventions

### A.1 epop

### A.2 Postfix

### A.3 Postfix Operations

### A.4 Function Definitions

### A.5 Data

## APPENDIX B ■ epop's General Syntax

### B.1 epop's General Syntax

### B.2 Data Containers

### B.3 Postfix

### B.4 Words As Arguments

### B.5 Defining New Words

### B.6 Tick Words

### B.7 Inline Words

### B.8 Word Overrides

### B.9 Deep Copy vs Shallow Copy

### B.10 Stack Checking & Error Prevention

### B.11 Local Namespaces

### B.12 epop Word Summary

## APPENDIX C Resources

### C.1 Online Resources

### C.2 Source Code - Online

## Bibliography

## Index

## List of Figures

- 1 Interdisciplinary data science contexts.
- 2 Discrete versus continuous information.
- 3 A discrete snapshot of a continuous reality.
- 4 The synthesizer built by Jack Sr.
- 1.1 Your mind: A programming environment.
- 3.1 Number classifications.
- 3.2 A typical hierarchy of data types for a programming language.
- 3.3 A compiled program's machine code file in hexadecimal format.
- 3.4 Program output representing ASCII codes.
- 4.1 Using the Unix bc command to change the number base.
- 7.1 (a) An intersection of sets. (b) A union of sets.
- 7.2 (a) A difference of sets. (b) A difference of sets.
- 7.3 (a) The complement of intersecting sets. (b) The complement of a union of sets.
- 9.1 A parse tree for a simple function.
- 9.2 Information transmission, reception, and processing.
- 9.3 State diagram for a machine that matches a word.
- 10.1 Function versus non-function.
- 10.2 Types of functions.
- 11.1 A call tree of the conditions of the Fibonacci sequence.
- 12.1 Abstract-syntax tree: λ is the abstraction operator. eval is the application operator.
- 12.2 Abstract-syntax tree for two successive applications.
- 13.1 Big-O time complexity comparisons.
- 14.1 A set of unconnected objects.
- 14.2 A connected list of objects.
- 14.3 (a) A tree. (b) A graph.
- 15.1 A uniform probability distribution of 6 random samples.
- 15.2 The “uniform” distribution of output from a pseudo-random number generator.
- 16.1 A connected list of objects.
- 16.2 A connected list of characters.
- 16.3 An array of characters.
- 16.4 A list of lists.
- 16.5 A sequence of currency symbols to represent abstract objects.
- 16.6 Three separate stacks, before operations.
- 16.7 Three separate stacks, after one operation.
- 16.8 Three separate stacks, after two operations.
- 16.9 A combined stack (before & after one operation).
- 16.10 A hybrid circular/priority queue of p data and q indices.
- 17.1 A list of objects.
- 17.2 A list of objects.
- 17.3 A binary tree.
- 17.4 (a) A binary tree. (b) A graph.
- 17.5 Isomorphic graphs.
- 17.6 A file system.
- 17.7 Binary tree traversal patterns.
- 17.8 A parse tree of (A – B) + (C × D).
- 17.9 A parse tree of (A – B) + (C × D).
- 17.10 Evaluating a binary tree on a stack in level-order.
- 17.11 A binary search tree: (a) before (b) and after, inserting the new element “11”.
- 17.12 A sorted list of numbers (ascending).
- 17.13 A relation of two objects: B depends on A. B is directed to A.
- 17.14 Relations of objects.
- 17.15 A reflexive relation.
- 17.16 An undirected graph representing the bordering states of New England.
- 17.17 A complete graph.
- 17.18 An incomplete directed graph.
- 17.19 Euclidean distance.
- 20.1 Positive, none, & negative linear correlation.
- 20.2 A linear fit of marathon times versus temperature.
- 21.1 A uniform distribution.
- 21.2 A normal distribution.
- 21.3 An approximately “normal” distribution of output from a pseudo-random number generator.
- 21.4 More of a “normal” distribution of output from a pseudo-random number generator.
- 21.5 Random sampling of a variable.
- 21.6 Non-random sampling of a variable.
- 22.1 Information transmission, reception, and processing.
- 22.2 Level 1 and leaves of a Huffman tree.
- 22.3 A Huffman tree.
- 23.1 A two dimensional plot, at a single period in time.
- 23.2 Model performance versus dimensions (hypothetical).
- 23.3 The S&P 500 Stock Index.
- 23.4 A hypothetical view of portfolio risk.
- A.1 Entry sequence (left to right) & corresponding stack sequence (top to bottom).
- A.2 A stack trace of an operation entry sequence.

## List of Tables

- 3.1 Number classifications
- 3.2 Octal file permission combinations in a Unix filesystem
- 3.3 File permissions for Unix's three user types
- 4.1 Numbers in different bases
- 4.2 Place values of base 2
- 4.3 Columnar correspondence of a number in binary
- 4.4 A Binary Coded Decimal lookup table
- 7.1 Relation where a > b
- 7.2 An adjacency matrix
- 11.1 Function calls structured as a stack in memory
- 13.1 Magnitudes of algorithm expansion
- 13.2 Three algorithms that compute a mean. Big-O & operation totals
- 14.1 Attributes of data organizations.
- 17.1 Complete binary tree list mappings
- 17.2 An adjacency matrix
- 20.1 An analysis of variance table (ANOVA)
- 23.1 Two symbols at a snapshot in time, with rate of change (ROC) the only dimension
- 23.2 Sample densities, with constant sample size
- 23.3 Sample densities, with increasing sample size
