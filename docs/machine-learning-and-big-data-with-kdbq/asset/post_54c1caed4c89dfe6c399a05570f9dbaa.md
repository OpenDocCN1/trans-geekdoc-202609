
## CHAPTER 4

## Editors and Other Tools

We are already equipped with enough knowledge to work with q. We have so far seen how to invoke the console. In this chapter, we focus on editors and tools we can use to work with q more efficiently. We intend to briefly introduce various tools and let the reader decide which tool to use for his or her work. We invoke the console. In this chapter, we focus on editors and tools we can use to work with q more efficiently. We intend to briefly introduce various tools and let the reader decide which tool to use for his or her work. Further, we aim to rebut but wrong belief that one has to give up on graphics tools when working with q.

In particular, we briefly remind the reader of the usage of the console as a tool for rapid development, and then focus on Jupyter Notebook, IntelliJ, qStudio, and q. The information presented in this chapter is valid as of the time of writing the book. It is likely that new or significantly improved editors will appear in the meantime and the information below becomes obsolete. Our main argument, though, should still hold: q is an extremely flexible language and a lot of the necessary tools that a user needs for software development and data science already exist and are adequate for obtaining insights into the data and for the flexible experimentation, research and expansion of their code.

## 4.1 CONSOLE

The console is a starting point for readers who have been following our book since the beginning. We have also discussed some useful options we can use when we invoke q. It is essential that our reader is familiar with the usage of the console since interpreter provides a universal way to run and type q. It is available in every operating system and makes starting with an idea very quick. In production systems, accessing a q service through the console is also one of the most efficient ways to deal with a potential issue and understand what is going on, assuming admin access is given. Figure 4.1 shows an example of the console output for a number of commands.

Further, the console will come very useful when we need to debug the code. The enhanced q functionality to provide debugging output is returned in the console but not in GUIs (unless we have access to console from the GUI interface).

Using the console as a means of accessing q is very fast. The console can also handle cases when we intentionally or by mistake return a large data set. The output of the table in the console is truncated, and we thus avoid data transfer which will happen when accessing a GUI or IDE.

## 82 LANGUAGE FUNDAMENTALS

```
C:\Windows\system32\cmd.exe
0.02278013 1 1
0.253808 1 -1
0.305249 1 -1
0.2318251 1 -1
0.07842500 1 -1
>+i+1
>2
>a=4;b=3;
>a+b
>testFunction:<[x]
>[0] testFunction:<x>
>testFunction:<x> 2*x
>testFunction 4
>sin
0.3796077 0.9260185 -0.889956 -0.3216224 0.3796077
>sin 'alpha'
>[0] sin 'alpha'
_>
```

FIGURE 4.1 Console output

On the other hand, the console has limitations when dealing with large projects. For instance, working on this book within the console would only make the work more complicated. The console by default does not allow syntax highlighting. One has to use further tools to achieve this. One way is to use external text editors with enabled highlighting, save the code into a script and then invoke the script from command line. One such popular editor is vim.

## 4.2 JUPTER NOTEBOOK

The Jupyter Notebook is an open-source web application, jap (a). It supports more than 40 programming languages, including Python, R and q. The Jupyter Notebook allows us to create interactive documents. Such documents can contain well-edited text as well as live and executable code for a wide range of visualisations, which enhance the message conveyed. Notebooks can be easily shared, either as a file through control software like git, or in the same way as we share a link to any page web.

The Jupyter Notebook is nowadays widely used by the machine learning and data science community. It can be used for various projects from modelling, simulations, or data visualisations, among others. The notebooks are, in particular, widespread across the Python community. It is easy to integrate systems like Spark or Apache to enhance Python performance, as well as accessing libraries like tensorflow, which are in the spotlight of the machine learning community.

Another appealing feature is that the text presented within the notebooks can contain LaTeX commands. The notebooks can compile it, and text can thus visually even the most complicated mathematical formulas. Lastly, it is relevant to stress when the Jupyter Notebook is invoked, it launches its q kernel. The user does not have to care about the q process itself much. The console is fully hidden from the user.

## Editors and Other Tools

The Jupyter Notebook now contains support for q and the kernel can be accessed at just (b). It brings functionalities like syntax highlighting, code completion, loading of scripts, and mainly the inline display of charts created through embedPy and matplotlib. The aforementioned library, embedPy, which allows integration of Python to q. Figure 4.2 shows an example of code run through jupyterq and an example usage of the notebook in conjunction with matplotlib.

A slight disadvantage may be encountered when using jupyterq its speed. In q, we are need to the bottleneck,,,,,,,,,,,,,,, to to to to to to to to to to to to to to to to to to to to to to to to to to to to to to to to to to to to to to to. In some cases, we need to provide an example of how it can be used by providing an example of how it can be used in conjunction with matplotlib, which is shown below. This is an example of the following. In some cases, we need to provide the reader to be aware of the following, which can be used in a data-driven approach. The following is an example of the following:

![img/97581](img/97581)

```
In [2]:
import matplotlib.pyplot as plt
y=50
x=50
plt.plot(x,y)
plt.xlabel("X values")
plt.ylabel("Y values")
plt.title("timeseries")
plt.show();
```

FIGURE 4.2 Jupyterq

## 84 LANGUAGE FUNDAMENTALS

## 4.3 GUIs

Let us present two GUIs to work with: qStudio, and Insight Pad. Both programs are examples of the GUIs which are available to readers. They have been chosen as examples and to encourage using them. Both GUIs have some common features which we will describe before proceeding with.

The most common feature, which differentiates the GUIs from Jupyter Notebook, is the fact that they do not run their instance of q. They are here to offer better visualisation when working with data. Their design – like a data explorer – is to connect to a running instance started by the user. This can be a process described in Chapter 1, where the –p option has been specified, the process is ‘listening’ in the background. In our examples below, we will assume that the reader has launched a session locally on laptop or PC, where the port has been set to –p 5000.

Establishing a connection from the GUIs to our q process – and assuming the process will give us access to all objects created within that instance. Thus, if we define a in the console of the running instance, then we will run some code from q, we will not see the code being typed in the console by default unless lower level handlers are overridden. The console from which we have launched q serves as one possible point of access to the running instance, but not the only one. Further, if we need a demanding query from the GUI, the console is effectively blocked and does not allow us to run any other query or submit any to the queue.

It may seem that we do not need to work on the q when we have a GUI. This is true for larger projects where we need to create more complex functions, the console may become necessary as it allows us to debug the code efficiently. The output of erroneous functions or queries may not be fully visible in the GUI as the GUI is necessarily a separate process which is merely a client to our main session.

Most GUIs have support for plotting functionality. This is a crucial feature as having in some simple plotting can facilitate in understanding the nature of our data, identify patterns or detect errors. Besides, GUIs also provide an interface to
