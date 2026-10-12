
# Topics Overview

Topics are carefully selected to give you a broad exposure to machine learning application while not overwhelming you with information overload.

The examples and case studies are carefully chosen to demonstrate each algorithm and model so that you can gain a deeper understanding of machine learning. Inside the book and in the appendices at the end of the book, we provide you with convenient references.

You can download the source code for the project and other free books at:

<http://aisciences.net/code>book5

# Your Free Gift

As a way of saying thanks for your purchase, AI Sciences Publishing Company is offering you a free eBook in Machine Learning with Python written by the data scientist Alain Kaufmann.

[![C:\\Users\\gchadad\\Dropbox\\Electro_books\\Covers\\bribes_mlfs_ai.jpg](images/00008.jpeg)](http://aisciences.net/free-books/)

It is a full book that contains useful machine learning techniques using Python. It is a 100-page book with one bonus chapter focusing on Anaconda Setup & Python Crash Course. AI Sciences encourages you to print, save, and share. [You can download it by going to the link below](http://aisciences.net/free-books/) or by clicking on the book cover above.

<http://aisciences.net/free-books/>

[If you want to help us produce more material like this, then please leave an honest review on Amazon. It really does make a difference.](https://www.amazon.com/dp/B07FTPKJMM)

# Installation & Setup

Are you excited about machine learning? We’ll get into that later. But first, we have to set up everything. We’ll use the most popular and convenient tools so you can focus more on machine learning itself.

## Download Anaconda

If you don’t yet have Anaconda installed, go to <https://www.anaconda.com/download/>, download the installer, and double-click it (mostly it’s just standard installation). Choose the Python 3+ version so the results will be consistent and you won’t run into too many problems. Also, Python 3 is where everything goes (Python 2 retired in 2020).

Anyway, why Anaconda? It’s a popular choice among many data scientists and machine learning engineers worldwide (over 6 million users already). It already includes Python 3 and many of the libraries and packages useful for machine learning, which is why the installer is a sizable file (500+ MB).

Some of the most awesome packages that you’ll encounter again and again in this book are:

*   `Numpy`
*   `Scipy`
*   `Matplotlib`
*   `Pandas`
*   `Scikit-learn`
*   `NLTK` (Natural Language Toolkit)
*   `Jupyter Notebook`

If you quickly want to get familiar with Anaconda, here’s a PDF cheat sheet (which you can also use as a reference in the future):

<https://docs.anaconda.com/_downloads/Anaconda-Starter-Guide-Cheat-Sheet.pdf>

## Running Jupyter Notebook

By this time, you should now have Anaconda installed. The next step is to run `Jupyter Notebook`. It’s a browser-based notebook where you can add code, text, and notes. Literally, we can think of it as a notebook, which is why many university professors and researchers use it.

If you have Anaconda installed already, find the `Anaconda Prompt` from your installed programs. Open it and then type `jupyter notebook` (without the quotes), and this will launch the notebook into your default browser. You can see your files and folders there. You can navigate to your target folder and create new notebooks there.

It’s very intuitive to use, and you’ll learn how to use it as you read along through our examples later. You can also explore more about `Jupyter Notebook` by reading their Quick Start Guide:

<http://jupyter-notebook-beginner-guide.readthedocs.io/en/latest/>

Anyway, here’s the Zen of Python (guiding principles for Python’s design found at <https://www.python.org/dev/peps/pep-0020/>). We included it here as a reminder of excellent coding and work practices:

```
Beautiful is better than ugly.

Explicit is better than implicit.

Simple is better than complex.

Complex is better than complicated.

Flat is better than nested.

Sparse is better than dense.

Readability counts.

Special cases aren't special enough to break the rules.

Although practicality beats purity.

Errors should never pass silently.

Unless explicitly silenced.

In the face of ambiguity, refuse the temptation to guess.

There should be one-- and preferably only one --obvious way to do it.

Although that way may not be obvious at first unless you're Dutch.

Now is better than never.

Although never is often better than *right* now.

If the implementation is hard to explain, it's a bad idea.

If the implementation is easy to explain, it may be a good idea.

Namespaces are one honking great idea -- let's do more of those!
```

# Python Crash Course

Now you’ve installed the necessary tools and packages. The next step is to quickly review Python so you can keep up with the discussions and examples later.

This won’t be the most comprehensive guide about Python. But this might be enough to keep you going because we’ll cover the basics and the most important things you can use for machine learning later. And because of Python’s intuitive syntax, you can still follow along with the lessons in the succeeding chapters.

## Strings, Lists, Functions, and More

We can assign values (strings, integers, and floats) to variables and access them later (and do a bunch of other things to them). Here’s an example:

```
yourName = 'Felicity'

print(yourName)
```

Returns `'Felicity'`

```
print(yourName[0])
```

This prints `'F'`, the first letter of `'Felicity'`. Indexing starts at zero in Python.

```
print(yourName[0:3])
```

Result would be `'Fel'`. Starts at zero index but excludes index 3.

```
print(len(yourName))
```

Counts the number of letters or finds out the “length” of the string. So the result here would be 8.

Speaking of numbers, we can also assign numeric values to variables:

```
yourAge = 22

print(yourAge)  # This is a comment. Anyway, this prints '22'

print(yourAge * 2)  # Prints 22*2 which is 44

yourAge = 25  # We can also reassign values to variables.
```

Let’s now talk about `Lists` (one of the most useful and popular data structures in Python):

```
myList = [1,2,3,4]

myList.append(5)  # myList then becomes [1,2,3,4,5]

myList[0]  # this returns the first value in the list, which is 1. Remember indexing in Python starts at zero.

print(len(myList))  # Prints the "length" of the list, which in this case 5.
```

Now let’s get into `Functions` and `Flow Control` (`If`, `Elif`, and `Else` statements):

```
def add_numbers(a,b):
    return a + b

print(add_numbers(3,4))
```

First we define a function and include an instruction. Then we call or test it but this time include the numbers. The function `add_numbers` will add 3 and 4, and print 7.

```
def if_even(num):
    if num % 2 == 0:
        print("Number is even.")
    else:
        print("It's odd.")

if_even(24)  # This returns "Number is even."
if_even(25)  # This returns "It's odd."
```

Well, that’s the end of our Python crash course. Next, let’s discuss how to use `Modules`.

# Jupyter Notebook
