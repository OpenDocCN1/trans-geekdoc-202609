
## COMPUTATION

To learn from this book, you need to be able to write and understand computer code. I'm not asking you to write object-oriented C++, to build a portable application with statically typed Scala, or to engineer production-quality software. You don't need to be a software engineer to work as a business data scientist. But you do need to be able to read and write in a high-level *scripting* language—in other words, flexible code that can be used to describe recipes for data analysis.

The ability to interact with computers in this way—by typing commands rather than clicking buttons or choosing from a menu—is a basic data analysis skill. Having a script of commands allows you to rerun your analyses for new data without any additional work. It also allows you to make small changes to existing scripts to adapt them for new scenarios. Indeed, making small changes is how I recommend you work with the material in this book. The code for every in-text example is available online, and you can alter and extend these scripts to suit your data analysis needs.

The languages for data science and machine learning are getting progressively "higher level," meaning that you can do more with short statements and that grittier programming issues (e.g., memory allocation, data partitioning, optimization) are being solved automatically in the background. Some of the most exciting advances along these lines are in the area of deep learning, the type of general-purpose ML that powers the current rise in artificial intelligence technology (see Chapter 10). For example, Gluon wraps (i.e., provides higher-level functionality around) MXnet, a deep learning framework that makes it easier and faster to build deep neural networks. MXnet itself wraps C++, the fast and memory-efficient code that is actually compiled for execution. Similarly, Keras is an extension of Python that wraps together a number of other deep learning frameworks, such as Google's TensorFlow. These and future tools are creating a world of friendlier interfaces for faster and simplified machine learning.

In the examples for this book, all of your analysis will be conducted in R. This is an open-source high-level language for data analysis. R is used widely throughout industry, government, and academia. Microsoft produces an official enhanced version of R, and it and other companies sell enterprise products for managing data analysis. This is not a toy language used by a small group of professors or for teaching purposes—R is the real industrial-strength deal.

For the fundamentals of statistical analysis, R is tough to beat: all of the tools you need for linear modeling and uncertainty quantification are mainstays in R. We’ve also found it to be relatively forgiving with the novice programmer. A major strength of R is its ecosystem of contributed packages. These are add-ons that increase the capability of “core” R. For example, almost all of the ML tools that you will use in this book are available via packages. The quality of the packages is more varied than it is for R’s core functionality, but if a package has high usage, you can be confident that it works as intended.

You can run R in many ways. There is a dedicated graphical user interface (GUI) for whatever operating system you use. This is the program you will work with if you access R through the icons that arrive when you download and install R. Alternatively, you can operate R through a *notebook* environment like that provided by Project Jupyter. The notebooks mix code with Markdown, a user-friendly language for producing nice-looking HTML (websites), such that you can combine notes, code, and results in a single document that is viewable through any web browser. Finally, since R just works with text commands, you can run it through any command prompt or terminal on your computer. For example, see Figure 1.4.

![](img/315929ad4bddd26368466d02e06e2385_24_0.png)

FIGURE 1.4: R on Windows in R CMDer.

There are many great places to learn the basics of R. If you search simply R on Amazon, you will find a huge variety of resources for learning R. There are also many great tutorials available online, and many of them are free. You don't need to be an expert in R to read and learn from this book; you just need to be able to understand the fundamentals and be willing to mess around with the coded examples. Remember to use help (type `?function` for help on a given function), print often to see what your objects contain (to print variable A, you just type `A` or `print(A)`), and search the Internet when confused (Stack Overflow is a great source of information). The learning curve can be steep initially, but once you get the hang of it, the rest will come fast.

At its most basic, R is just a fancy calculator. Everything is based on assigning names.^10 For example, here’s a simple R script with variables and some basic arithmetic:

```
> A <- 2  
> B <- 4  
> A*B  
[1] 8
```

You can also work with *vectors* (and matrices) of multiple numbers:

```
> v <- c(2,4,6)  # c(x,y,z,…) is used to create a vector  
> v[1:2]  # a:b indexes `from a through b`  
[1] 2 4  
> v[1]*v[2]  
[1] 8
```

Throughout this book, you’ll see many snippets like the previous one. The # symbol denotes a comment, and we’ll often use this to add explanation to the code. These commented snippets are a tool for demonstrating the actual execution of data analysis routines. Full code scripts and data are available at http://taddylab.com/BDS.

R is not perfect, and it is not the best language for all purposes. Python provides a better workspace for many ML applications, especially those involving unstructured data like raw text. For large-scale ML, you should probably work with one of the deep learning frameworks referenced earlier, such as Gluon or Keras. Similarly, massive datasets are often stored in specialized distributed computing environments. Frameworks such as Spark, which you can access via the Scala or Python language, are essential for building the data pipes that slice and aggregate this information. To execute ML routines on this type of truly massive data, you might want to consider purpose-built frameworks like Spark.ML. If you work for a large firm, it is possible that you will need to learn proprietary languages that are designed to suit your company’s specific data management needs. And it is almost inevitable that at some point you will need to write an SQL query to “pull” data from a structured database.
