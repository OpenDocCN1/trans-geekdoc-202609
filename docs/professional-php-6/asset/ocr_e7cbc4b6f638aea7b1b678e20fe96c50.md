After you have the hang of stepping over your code or following a script’s execution, you can use these to find out valuable information about the state of your code. The Debug pane, located by default in the upper-left corner of the ZS PHP Debug Perspective, provides you with five options to monitor and manage your project’s debugging. From here, you can view the value of variables, the position of watches, the stack trace, the position of breakpoints, and the buffer. All of these may come in handy, depending on what it is you are trying to determine about your code.

For example, let’s say you have stepped over the execution of a very simple PHP script in order to demonstrate how the Variables tab shows you information about all the variables associated with your code (including the global ones). This is shown in Figure B-7.

![](bbox=[0.246, 0.285, 0.679, 0.525])

Figure B-7: The Variables tab

If you look at the editor window after invoking the debugger, you will see the first line in the execution of your application highlighted. This is because, at present, the debugger is stopped at this point in the script’s execution. The values you see in the Variables pane are the values at this particular point in the program’s execution. If you already know the piece of code you want to inspect, you can forgo stepping over all the code line by line and place the cursor on the line you want the debugger to go to. Click Run ➔ Run to Line (or press Ctrl+R) to run the application until it reaches that line of code.

Tracing the execution stack is also a useful way of determining where you are in your code. The Debug pane enables you to view where you are in the program’s stack. This can be helpful because if one part of your code calls a function, the program’s execution leaves the current place to go off and run the called function. If the function itself makes use of other functions, then the program’s execution heads off again to go execute those. Being able to determine exactly where you are in all this is where the stack tracing capability of the debugger comes in.

Figure B-8 shows an example of the Debug pane being used to track a simple script that is in the middle of executing a method in a class, invoked from the index.php file.