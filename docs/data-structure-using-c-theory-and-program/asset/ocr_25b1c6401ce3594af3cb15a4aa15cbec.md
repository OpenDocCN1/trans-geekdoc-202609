62 Data Structure Using C

+   1. Delete at Beg
2. Display
3. Exit

Enter your choice: 1
1. Delete at Beg
2. Display
3. Exit

Enter your choice: 2
value of nodes in the list are as follows:
20 30 40

+   1. Delete at Beg
2. Display
3. Exit
Enter your choice: 3

c. (ii) Deletion at end

![](bbox=[0.301, 0.452, 0.698, 0.506])

![](bbox=[0.351, 0.532, 0.648, 0.584])

Algorithm
Steps

+   1. Start
2. Holds the address of the first node
3. Set node = start
4. Set temp = start
5. If node = NULL then
6. Write “UNDERFLOW” and
7. Exit
8. Repeat steps 9 and 10 while [node] ≠ NULL
9. Set temp = node
10. Set node = next [node]
11. End of step 8 loop
12. Set next [temp] = NULL