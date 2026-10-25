
knowledge of Python programming language, it should not be a problem for you to decipher the code in this section. You can use the code to build a system.

The last chapter of the book revolves around the concept of business intelligence. I will explain what business intelligence is and how it is similar to the concept of machine learning and artificial intelligence. You will get an insight into the processes of business intelligence. Then I will go on to explain different functions of business intelligence. You will learn how you can benefit by using these functions. Then I will move on to explaining the importance of business intelligence. You will learn the infrastructure of the working process of business intelligence. You will also learn who uses business intelligence in the present day. The chapter ends on a comprehensive explanation of the different advantages of business intelligence.

I don't expect you to be a master in Python programming to be able to read and understand this book. You should know the basic knowhow of Python programming. For ease of use, I have included in this book two chapters on Python programming. You can use that knowledge to build simple and object-oriented programming before you move on to building a deep learning model. I recommend that you keep a diary by your side to note down each important point and code snippet that you think you need to practice more. Once you have documented everything in the diary, you can move on to enter the practical phase. The more you practice, the better you get at building programs and understanding how deep learning models work and what their benefits are.

The best method for this deep learning madness is to read the book while keeping a computer operating system turned on so that you can practice and research whatever interesting item comes your way. Don't forget to install Python 2.7 or Python 3 on your system. Most of the code in the book is written in Python 2.7. Wherever there is a difference in the code between Python 2.7 and Python 3, I have mentioned it. Installing both versions will help you understand the nuances.

## Chapter One

### Basics of Python

This chapter will walk you through the basics of Python programming as you will need this knowledge to build artificial intelligence and machine learning models with deep learning techniques. Python is the building block of deep learning models. The first step is to check whether Python is installed on your computer system or not. If not, you will have to install a Python editor on your computer operating system. Text editors are dynamic and they recognize Python code, highlighting different sections as you write. This makes it easy to comprehend the structure of the code.

The first step is to understand the Python environment. Python may slightly differ on different operating systems. Generally, there are two versions of Python that are available on the market. Python 2 and Python 3 may be easily spotted on different systems. Python is still in the midst of evolution as each programming language tries to grow as new ideas and technologies continue to emerge. The developers of Python have made this language powerful and more versatile. Most of the changes are considered hardly noticeable. As operating systems evolve along the way, the older versions of Python such as Python 2 may not be as functional as the newest Python 3 is. If you have got both of them pre-installed on your system, it is recommended that you use Python 3.

There is an interpreter in Python 3 that is also known as the terminal window. This allows you to try different versions of Python without initially having to save and then run the program.

Python is a cross-platform language which means that you can run it on different operating systems as suits you. Windows do not come with Python as pre-installed on it that’s why you will have to download it and then install the same on the system. Once you have done that, you will have to download and install the text editor.

You need to check if Python is already installed on the system or not. Click open the command window and enter a command in the Start menu. Enter python in lowercase in the terminal window. If you see the following sign >>>, Python is installed on the system. If Python is not installed on the system, you are likely to see an error message on the screen.

In case there is no pre-installation of Python on the system, you will have to visit www.python.org to download and install Python. When you open the website, there will be a series of Python versions available for download. Choose the one you want to install on the system and click on download. Once the file has been downloaded on the system, you should go on to initiate the installation process. You should also make sure that you checkmark the option Add Python to PATH at the end of the installation process. It will make the process of configuration on your system easy and smooth.

### Python Variables

You will learn in this section about the different types of data you can work within Python programs. You will also learn about the process of storing data in variables and how to use variables in programs. One of the most basic features of Python is the variables. In the following code, I will create a variable in Python and assign it a value.

```
>>> x = " I am reading a book on deep learning techniques to build AI models."
>>> print(x)
I am reading a book on deep learning techniques to build AI models.
>>>
```

When I printed the program, the same line that I have assigned to the variable ‘x’ has been displayed on the screen of my computer. Each variable in Python holds a certain value which basically is the information that is associated with the variable. Now I will move onto the Python editor in which you will have to do the actual coding. I will use the same variable and value, and will also create a new variable and assign another value to the same to see how Python deals with them.

```python
x = " I am reading a book on deep learning techniques to build AI models."
y = " AI is revolutionizing different fields in the business world."
print (x)
print (y)
>>> ================= RESTART =================
>>>
I am reading a book on deep learning techniques to build AI models.
AI is revolutionizing different fields in the business world.
>>> 
```

You can initiate the Python editor by going to the File menu and clicking New. A new window will pop up, which you can use as the Python editor. You can write the code in the editor, then save and run it by clicking the F5 button on the keyboard. The results of the code will be displayed on the Python IDLE screen.

When you are working in Python variables in Python, you will have to take care of some guidelines and rules. If you break some of those rules, it will result in an error. Other guidelines will help you to write clean code that is easier to read and comprehend. Make sure that you follow variable rules. Names of the variables may contain numbers, letters, and underscores. They may start with an underscore or a letter but never with a number. For example, you may name a variable as x_1 but not 1_x. There is no room for extra spaces in the names of variables. However, underscores should be used to separate words in different variable names. For example, x 1 should not be the name of any variable. You must avoid using keywords that are inherent in Python. For example, the word print is inherent to Python. A variable name must be short but it should be descriptive. For example, if you are creating a variable to describe a student, you must write the full word instead of writing just the word ‘s.’ Python variables should be lowercase however, you won’t trigger errors even if you use an uppercase letter to name them. It is a good idea to avoid using them for as long as you can.

### Datatypes

Most programs define and gather different kinds of data and then use it on purpose. It allows you to classify different kinds of data. The first datatype that I will discuss is known as strings. Strings are quite simple at the first glance. A string is in the form of characters. Anything that is contained inside single or double quotes is known as a string.

```
x = " I am reading a book on deep learning techniques to build AI models."
y = ' AI is revolutionizing different fields in the business world.'
print (x)
print (y)
>>> ================= RESTART =================
>>> 
I am reading a book on deep learning techniques to build AI models.
```
