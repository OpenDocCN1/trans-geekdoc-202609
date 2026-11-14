# 3

# Computing Basics

> The Analytical Engine has no pretensions whatever to originate anything. It can do whatever we know how to order it to perform. —A. Lovelace

COMPUTING is about conventions more than numbers. Here, we present those conventions, explain computing concepts, define some jargon we'll use, and highlight common errors. This chapter will also give those without programming experience a place to start. For those already familiar with R , we also lay out all the packages we'll need to install.

# BRASS TACKS

Computers are simple creatures. Ambiguity is the computer’s natural enemy. Code is a set of instructions designed to stamp out ambiguity. The computer follows our instructions and, if all is clear, it performs whatever task we intended. Like natural languages, programming languages have family trees, meaning they are related to, and draw on, earlier languages.1 We can classify programming languages by their general features. R is an object-oriented, procedural, and functional programming language: we perform data procedures on objects using functions. These objects are different data types arranged in data structures. Functions are either included in base R , created during the session, or available in “packages.” Packages must be installed on our machines and loaded during each session.

1 For example, R (Team 2021) is the open-source progeny of S, itself influenced by Fortran and Scheme (of the Lisp family).

# Coding Environments

Computers comprise three “layers.” At the top is the GUI or Graphical User Interface. Whenever we point and click with our touchpad, mouse, or touchscreen, we interact with the GUI. Binary—zeros and ones—is at the bottom; computer hardware understands this layer. Several intermediaries exist between these two layers. Most programming languages used by social scientists and other computational scholars, like R or Python , are called “high-level” because they sit closer to the GUI.