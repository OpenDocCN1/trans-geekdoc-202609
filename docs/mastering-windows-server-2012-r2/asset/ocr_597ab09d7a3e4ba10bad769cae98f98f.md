# 1510 CHAPTER 30 MONITORING WINDOWS SERVER 2012 R2

You can also use Resource Monitor to help you identify what process may be locking a file or DLL. As an example, malware will prevent a file from being deleted by locking it. If you try to delete the malware file, the system bakes because it claims the file is locked. However, you can use Resource Monitor to get more details on what's happening.

Select the CPU tab and open the Asynchronous Handles section. You can type in the name of the file in the text box and click the Search button. Details on the handle will be displayed. You right-click the result and select End Process, and you should be able to delete the file.

# BE CAREFUL WITH END PROCESSES

Ending processes may result in system instability. You should end a process only as a last resort. It is sometimes a good solution but not a first solution. Additionally, some processes are resilient, and if stopped, they'll be restarted. This happens with some system resources and malware.

Sometimes you need to dig a little deeper. Identify the process ID (in the PID column), click the Overview tab, and look at the CPU section. The second column is labeled PID, and if you click it, you can sort the processes in ascending or descending order to easily find the process. When you click once, an arrow will indicate ascending order, and when you click it again, an arrow will display.

Once you've found the process, you can right-click it and end it here or gather information. If you select Analyze Wait Chain, it will show all the processes or waiting to use the resource.

# VIEWING SYSTEM RELIABILITY

System reliability is tracked by Reliability Monitor. It uses a stability index to assess the system's stability on a scale of 1 to 10, with 10 indicating perfect reliability.
Rability Monitor monitors hardware failures, application failures, Windows failures, and other miscellaneous failures and warnings. When a failure occurs, the stability index is reduced depending on the severity of the problem. The longer the runs without any failures, the higher the stability index.

Data is displayed on a graph that shows information, warnings, and failures. You can select any of the icons to view details on the

Reliability Monitor can be useful in identifying trends of systems. Most of your servers have similar stability indices. However, if you identify a server that has a significantly lower index, it could be because of problems with incompatible hardware or buggy applications.

# Using Data Collector Sets

Data collector sets are an exciting feature available within the Performance Monitor suite that appeared in Windows Server 2008. Each data collector set is a predefined set of performance counters, event trace data, and configuration information used to monitor key elements within a system.