Polyglot Programming in Applications Used for Genetic Data Analysis 321

(AMF), which is supported in Python by the pyAMF library. At present, technology is being replaced by HTML5, which is supported directly by web browsers, so HTML5 and JavaScript are recommended for use in new applications.

# Parallel Service Requests

The framework was designed to create the software that serves multiple users at the same time. The users communicate independently with the server via the Internet and the framework includes a component with the active object pattern [9] implementation to enhance concurrency and to exploit the server resources fully. This component, which is part of bioweb, is shown in Figure 3.

![](bbox=[0.195, 0.388, 0.805, 0.633])

Figure 3: Active object implementation delivered by the framework. The client requests are transformed into commands automatically, which are executed by separate threads.

The execution of calculation tasks is decoupled from task invocation to enhance concurrency and to simplify multithread usage, as shown in Figure 4. Calculation requests from the client application are converted into C++ objects. These objects are commands (the command design pattern is used) which contain specific parameters as well as algorithm and synchronization mechanisms. Commands are stored in the task queue and executed by separate execution from the thread pool. The command handlers are accessible from Python, so the user can examine the current command state, that is, tasks that are awaiting execution in the queue, executed tasks, and