# 84

# LANGUAGE FUNDAMENTALS

code and investigate the data in detail – in which case a heavy lifting IDE is more appropriate – wants to share data snippets easily, different tools in this list can be deployed appropriately.

In order to install Jupyter Notebook and the jupyter extension, please follow the corresponding web links. Both programs are installed, the reader can use the tool immediately and enjoy its power. This assumes that Python is installed on the computer and the reader has appropriate access to run pip or conda.

# 4.3 GUIs

Let us present two GUIs to work with: qStudio, and Insight Pad. Both programs are examples of the GUIs which are available to readers. They have been chosen as examples and to encourage exploration of what is on nowadays. Both GUIs have some common features which we will describe before proceeding with GUI-specific comments and hints to get readers using them as smoothly as possible.

The most common feature, which differentiates the GUIs to the Jupyter Notebook, is the fact that they do not run their instance of q. They are here to offer better visualisation when working with q and data. Their design – like a typical data explorer – is to connect to a running instance of q started by the user. This can be a process described in Chapter 1, where the –p option has been specified, the process is ‘listening’ in the background without any visible console, or it can be a process which the user connects to. In our examples below, we will assume that the reader has launched a session locally on their laptop or PC, where the port has been set to –p 5000 upon startup.

Establishing a connection from the GUIs to our q process – and assuming the process will give us access to all objects created within that instance. Thus, if we define a :1 in the console of the running instance, then we will run some code from q, we will not see the code being typed in the console by default unless lower level handlers are overridden. The console from which we have launched q serves as one possible point of access to the running instance, but not the only one. Further, if we need a demanding query from the GUI, the console is effectively blocked and does not allow us to run any other query or submit any to the queue.

It may seem that we do not need to work on the q when we have a GUI. This is true for larger projects where we need to create more complex functions, the console may become necessary as it allows us to debug the code efficiently. The output of erroneous functions or queries may not be fully visible in the GUI as the GUI is necessarily a separate process which is merely a client to our main session.

Most GUIs have support for plotting functionality. This is a crucial feature as having in some simple plotting can facilitate in understanding the nature of our data, identify patterns or detect errors. Besides, GUIs also provide an interface to