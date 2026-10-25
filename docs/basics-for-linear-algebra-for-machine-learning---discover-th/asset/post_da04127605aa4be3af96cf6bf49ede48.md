
- D.4 Greek Alphabet . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 189
- D.5 Sequence Notation . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 190
- D.6 Set Notation . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 191
- D.7 Other Notation . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 192
- D.8 Tips for Getting More Help . . . . . . . . . . . . . . . . . . . . . . . 192
- D.9 Further Reading . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 194
- D.10 Summary . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 194

## VIII Conclusions . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 195

## How Far You Have Come . . . . . . . . . . . . . . . . . . . . . . . . . . . 196

## Preface

I wrote this book to help machine learning practitioners, like you, get on top of linear algebra, fast.

### Linear Algebra Is Important in Machine Learning

There is no doubt that linear algebra is important in machine learning. Linear algebra is the mathematics of data. It’s all vectors and matrices of numbers. Modern statistics is described using the notation of linear algebra and modern statistical methods harness the tools of linear algebra. Modern machine learning methods are described the same way, using the notations and tools drawn directly from linear algebra. Even some classical methods used in the field, such as linear regression via linear least squares and singular-value decomposition, are linear algebra methods, and other methods, such as principal component analysis, were born from the marriage of linear algebra and statistics. To read and understand machine learning, you must be able to read and understand linear algebra.

### Practitioners Study Linear Algebra Too Early

If you ask how to get started in machine learning, you will very likely be told to start with linear algebra. We know that knowledge of linear algebra is critically important, but it does not have to be the place to start. Learning linear algebra first, then calculus, probability, statistics, and eventually machine learning theory is a long and slow bottom-up path. A better fit for developers is to start with systematic procedures that get results, and work back to the deeper understanding of theory, using working results as a context. I call this the top-down or results-first approach to machine learning, and linear algebra is not the first step, but perhaps the second or third.

### Practitioners Study Too Much Linear Algebra

When practitioners do circle back to study linear algebra, they learn far more of the field than is required for or relevant to machine learning. Linear algebra is a large field of study that has tendrils into engineering, physics and quantum physics. There are also theorems and derivations for nearly everything, most of which will not help you get better skill from or a deeper understanding of your machine learning model. Only a specific subset of linear algebra is required, though you can always go deeper once you have the basics.

## Practitioners Study Linear Algebra Wrong

Linear algebra textbooks will teach you linear algebra in the classical university bottom-up approach. This is too slow (and painful) for your needs as a machine learning practitioner. Like learning machine learning itself, take the top-down approach. Rather than starting with theorems and abstract concepts, you can learn the basics of linear algebra in a concrete way with data structures and worked examples of operations on those data structures. It’s so much faster. Once you know how operations work, you can circle back and learn how they were derived.

## A Better Way

This book was born out of my frustrations at seeing practitioner after practitioner diving into linear algebra textbooks and online courses designed for undergraduate students and giving up. The bottom-up approach is hard, especially if you already have a full time job. Linear algebra is not only important to machine learning, but it is also a lot of fun, or can be if it is approached in the right way. I put together this book to help you see the field the way I see it: as just another set of tools we can harness on our journey toward machine learning mastery.

Jason Brownlee
2018

## Part I

## Introduction

## Welcome

Welcome to _Basics of Linear Algebra for Machine Learning_. Linear algebra is a pillar of machine learning.

The field started to be formalized about 150 years ago, but it was only about 70 years ago that modern linear algebra came into existence. It’s a huge field of study that has made an impact on other areas of mathematics, such as statistics, as well as engineering and physics. Thankfully, we don’t need to know the breadth and depth of the field of linear algebra in order to improve our understanding and application of machine learning.

I designed this book to teach you step-by-step the basics of linear algebra with concrete and executable examples in Python.

## Who Is This Book For?

Before we get started, let’s make sure you are in the right place. This book is for developers that may know some applied machine learning. Maybe you know how to work through a predictive modeling problem end-to-end, or at least most of the main steps, with popular tools. The lessons in this book do assume a few things about you, such as:

- You know your way around basic Python for programming.
- You may know some basic NumPy for array manipulation.
- You want to learn linear algebra to deepen your understanding and application of machine learning.

This guide was written in the top-down and results-first machine learning style that you’re used to from MachineLearningMastery.com.

## About Your Outcomes

This book will teach you the basics of linear algebra that you need to know as a machine learning practitioner. After reading and working through this book, you will know:

- What linear algebra is and why it is relevant and important to machine learning.
- How to create, index, and generally manipulate data in NumPy arrays.
- What a vector is and how to perform vector arithmetic and calculate vector norms.
- What a matrix is and how to perform matrix arithmetic, including matrix multiplication.
- A suite of types of matrices, their properties, and advanced operations involving matrices.
- What a tensor is and how to perform basic tensor arithmetic.
- Matrix factorization methods, including the eigendecomposition and singular-value decomposition.
- How to calculate and interpret basic statistics using the tools of linear algebra.
- How to implement methods using the tools of linear algebra such as principal component analysis and linear least squares regression.

This new basic understanding of linear algebra will impact your practice of machine learning in the following ways:

- Read the linear algebra mathematics in machine learning papers.
- Implement the linear algebra descriptions of machine learning algorithms.
- Describe your machine learning models using the notation and operations of linear algebra.

This book is not a substitute for an undergraduate course in linear algebra or a textbook for such a course, although it could complement to such materials. For a good list of top courses, textbooks, and other resources on linear algebra, see the *Further Reading* section at the end of each tutorial.

## How to Read This Book

This book was written to be read linearly, from start to finish. That being said, if you know the basics and need help with a specific notation or operation, then you can flip straight to that section and get started. This book was designed for you to read on your workstation, on the screen, not on a tablet or eReader. My hope is that you have the book open right next to your editor and run the examples as you read about them.

This book is not intended to be read passively or be placed in a folder as a reference text. It is a playbook, a workbook, and a guidebook intended for you to learn by doing and then apply your new understanding with working Python examples. To get the most out of the book, I would recommend playing with the examples in each tutorial. Extend them, break them, then fix them. Try some of the extensions presented at the end of each lesson and let me know how you do.

## About the Book Structure

This book was designed around major data structures, operations, and techniques in linear algebra that are directly relevant to machine learning algorithms. There are a lot of things you could learn about linear algebra, from theory to abstract concepts to APIs. My goal is to take
