
[FIGURE 6-21:](#c06.xhtml#rc06-fig-0021) Colab tracks which code you execute and in what order.

## Executing the Code

For your code to be useful, you need to run it at some point. Previous sections have mentioned the right-pointing arrow that appears in the current cell. Clicking it runs just the current cell. Of course, you have other options than clicking the right-pointing arrow, and all these options appear on the Runtime menu. The following list summarizes these options:

*   **Running the current cell:** Besides clicking the right-pointing arrow, you can also choose Runtime ⇒ Run the Focused Cell to execute the code in the current cell.

*   **Running other cells:** Colab provides options on the Runtime menu for executing the code in the next cell, the previous cell, or a selection of cells. Simply choose the option that matches the cell or set of cells you want to execute.

*   **Running all the cells:** In some cases, you want to execute all the code in a notebook. In this case, choose Runtime ⇒ Run All. Execution starts at the top of the notebook, in the first cell containing code, and continues to the last cell that contains code in the notebook. You can stop execution at any time by choosing Runtime ⇒ Interrupt Execution.

![Tip](images/tip.png)Choosing Runtime ⇒ Manage Sessions displays a dialog box containing a list of all the sessions that are currently executing for your account on Colab. You can use this dialog box to determine when the code in that notebook last executed and how much memory the notebook consumes. Click the TERMINATE link to end execution for a particular notebook.

## Sharing Your Notebook

You can share your Colab notebooks in a number of ways. For example, you can save it to GitHub or GitHub Gists. However, the two most direct methods are the following:

*   Create a share message and send it to the recipient.

*   Obtain a link to the code and send the link to the recipient.

In both cases, you click the Share button in the upper right of the Colab window. Two dialog boxes open, as shown in [Figure 6-22](#c06.xhtml#c06-fig-0022).

![FIGURE 6-22: Send a message or obtain a link to share your notebook.](images/9781119724018-fg0622.png)

[FIGURE 6-22:](#c06.xhtml#rc06-fig-0022) Send a message or obtain a link to share your notebook.

When you enter one or more names in the People field, an additional field opens in which to add a sharing message. You can type a message and click Send to send the link immediately. If you click the gear icon instead, you see another dialog box, where you can define how to share the notebook.

Click the Copy Link link in the Get Link dialog box to place the URL on the Clipboard for your device. You can then paste it into messages or other forms of communication with others.

## Getting Help

The most obvious place to obtain help with Colab is from the Colab Help menu. The menu doesn't have a general help link, but you can find it at [`https://colab.research.google.com/notebooks/welcome.ipynb`](https://colab.research.google.com/notebooks/welcome.ipynb) (which requires you to log into the Colab site). This menu does contain all the usual entries:

*   **Frequently Asked Questions (FAQs):** Takes you to a page containing questions that other people have asked.

*   **Search Code Snippets:** Opens a pane showing common tasks, such as working with a camera, in which you can search for example code that could meet your needs with a little modification. Clicking the Insert button inserts the code at the current cursor location in the cell that has focus. Each of the entries also shows an example of the code.

*   **Report a Bug:** Takes you to a page where you can report Colab errors.

*   **Ask a Question on Stack Overflow:** Displays a new browser tab, where you can ask questions from other users. You see a login screen if you haven’t already logged into Stack Overflow.

*   **Send Feedback:** Displays a dialog box with links for locations where you can obtain additional information.

Part 3

# Getting Started with the Math Basics

IN THIS PART …

Understanding the math used in machine learning

Considering the machine learning process

Ensuring that you get the right results

Performing tasks with simple learners

Chapter 7

# Demystifying the Math Behind Machine Learning

IN THIS CHAPTER

![Bullet](images/check.png)**Exploring matrices and using matrix calculus to your advantage**

![Bullet](images/check.png)**Understanding how probability works**

![Bullet](images/check.png)**Explaining the Bayesian point of view on probability**

![Bullet](images/check.png)**Describing observations using statistical measures**

If you want to implement existing machine learning algorithms from scratch or you need to devise new ones, you require a profound knowledge of probability, linear algebra, linear programming, and multivariable calculus. You also need to know how to translate math into working code, which means having sophisticated computing skills. This chapter begins by helping you understand the mechanics of machine learning math and describes how to translate math basics into usable code.

If you want to apply existing machine learning for practical purposes instead, you can leverage existing Python software libraries using a basic knowledge of math and statistics. In the end, you can’t avoid having some of these skills because machine learning has strong roots in both math and statistics, but you don’t need to overdo it. After you get some math basics down, the chapter shows how even simple Bayesian principles can help you perform some interesting machine learning tasks.

Even though this introductory book focuses on machine learning experiments using Python, in the text you still find many references to vectors, matrices, variables, probabilities, and their distributions. The book sometimes uses descriptive statistics as well. Consequently, it helps to know what a mean, a median, and a standard deviation are in order to understand what happens under the hood of the software you use. This knowledge makes it easier to learn how to use the software better. The last part of the chapter demonstrates how machine learning can help you make better predictions, even when you don’t have all the information you need.

![Remember](images/remember.png)You don’t have to type the source code for this chapter manually. In fact, using the downloadable source is a lot easier. You can find the source for this chapter in the `ML4D2E` folder of the downloadable source for Python code and the `ML4D2ER` folder of the downloadable source for the R code. The example files for this chapter will begin with `ML4D2E; 07;` (for Python) or `ML4D2E_R; 07;` (for R). See the Introduction for details on how to find these source files.

## Working with Data

Machine learning is so appealing because it allows machines to learn from real-world examples (such as sales records, signals from sensors, and textual data streaming from the Internet) and determine what such data implies. Common outputs from a machine learning algorithm are predictions of the future, prescriptions to act on now, or new knowledge in terms of examples categorized by groups. Many useful applications have already become a reality by leveraging these results:

*   Diagnosing hard-to-find diseases

*   Discovering criminal behavior and detecting criminals in action

*   Recommending the right product to the right person

*   Filtering and classifying data from the Internet at an enormous scale

*   Driving a car autonomously

The mathematical and statistical basis of machine learning makes outputting such useful results possible. Using math and statistics in this way enables the algorithms to understand anything with a numerical basis. The following sections help you understand basic data manipulation using scalars, vectors, and matrices:

*   **Scalar:** A single base data item. For example, the number 2 shown by itself is a scalar.
