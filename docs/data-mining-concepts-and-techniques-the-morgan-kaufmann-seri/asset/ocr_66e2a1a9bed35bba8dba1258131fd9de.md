# 5.6.2 Mining copy and paste bugs in software programs

Pattern mining has found its interesting applications in software program analysis since the source code of a program module consists of long sequences of programming statements and the execution of a software program forms a sequence of executed codes. A large software program may consist of many program modules and its executions may leave tremendous amount of execution traces. Manual examination of such programming code or execution traces could be tedious and costly. Frequent and sequential pattern mining could provide useful tools to uncover interesting regularities or irregularities. Typical examples may include mining software bugs from source programs or execution sequences, mining programming rules from program revision histories, mining software function precedence protocols by examination of frequent subsequences, and revealing neglected conditions by frequent itemset or subgraph mining.

Here we examine one example which explores pattern discovery to find copy-pasting software program bugs from source code. Because a lot of program fragments may share some similar functions, code copy-pasting has become popular in software programming. A programmer may highlight a few lines of program code at one location of a program, copy these lines, paste them to another location in a program, and then perform appropriate modifications of the pasted programming code.

Copy-pasting is a common programming practice. Some statistic shows that about 12% of program code in the Linux file system and about 19% in the X Window system are copy-pasted. However, copy-pasted code is error-prone. Due to programmer's carelessness, changes on pasted code may not always be done consistently throughout. Such “forget-to-change” bugs can be common and lead to buggy programs.

Interestingly, such copy-pasting bugs can be mined by transforming source code into a sequence data set, on which sequential pattern mining can be conducted to identify likely mismatched identifier names, and hence catch the “forget-to-change” bugs.

Let’s examine such an example. Fig. 5.24 shows a program module that contains a copy-pasting bug: The first for-loop block is copied and pasted to form the second for-loop block, and every occurrence of the pasted identifier “total” should be consistently changed to “taken.” Unfortunately, the last change of “total” was missing, leading to a bug.

![](bbox=[0.385, 0.655, 0.585, 0.86])

# FIGURE 5.24 A program fragment that contains a copy-pasting bug.