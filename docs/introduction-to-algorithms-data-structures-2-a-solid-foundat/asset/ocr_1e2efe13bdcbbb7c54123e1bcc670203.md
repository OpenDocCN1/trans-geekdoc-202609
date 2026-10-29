# 2. Introduction to Data Structures

In this part of the course, I will introduce data structures. First, we're going to answer one fundamental question: **why do we need more data structures than a programming language provides?** This question will be answered in section 2.3.1. For now, let’s do some housekeeping.

In this course, we're going to rely on the concepts we learned in volume one (*Introduction to Algorithms & Data Structures 1*), namely big O notation, space and time complexity, and recursion. If you're unfamiliar with those concepts or just need a refresher, check out volume one. In addition, this course does assume that you have some programming experience.

We're going to use data structures that come built into nearly all programming languages as our point of reference. While we will explain the basics of how these structures work, we won't be going over how to use them in practice. If you're looking to learn how to program in Python before digging into this content, check out the following book that completely simplifies Python programming language for beginners:

https://www.scribd.com/book/513773394/Python-Programming-from-Beginner-to-Paid-Professional-Part-1-Learn-Python-for-Automation-IT-with-Video-Tutorials (or use this BIT.LY short link: http://bit.ly/3ZKREhB).

Even if you know nothing about Python, as long as you understand the fundamentals of programming, you should be able to follow along pretty well. If you're good to go, then awesome.

# 2.1. Course Overview

Let's start with an overview of this course. The first thing we're going to do is to explore a data structure we are somewhat already familiar with: arrays. If you've written code before, there's a high chance you have used an array. In this course, we're going to spend some time understanding how arrays work, what are the common operations on an array, and what are the run times associated with those operations.

Once we've done that, we're going to build a data type of our own called a **linked list**. In doing so, we're going to learn that there's more than one way to store data. In fact, there's way more than just one way. We're also going to explore what motivates us to build specific kinds of structures and look at the pros and cons of these structures. We'll do that by exploring four common operations: accessing a value, searching for a value, inserting a value, and deleting a value.

After that, we're going to circle back to algorithms and implement a new one: a sorting algorithm. In the introduction to algorithms course (volume one), we implemented a binary search algorithm. A precondition to binary search was that the list needed to be sorted. We're