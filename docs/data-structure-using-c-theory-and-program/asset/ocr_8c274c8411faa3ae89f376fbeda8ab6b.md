# List_1

![](bbox=[0.113, 0.114, 0.292, 0.137])

# List_2

![](bbox=[0.113, 0.173, 0.292, 0.196])

Figure Before Merge

# List

![](bbox=[0.296, 0.26, 0.696, 0.283])

Figure After Merge

# Algorithm

Steps

+   1. Set node_1 = list_1
2. Create a new node named as list
3. If list = NULL then
4. Write “out of memory space” and
5. Exit
6. Set info [list] = info [node_1]
7. Set next [list] = NULL
8. Set node_1 = next [node_1]
9. Set node = list
10. Repeat steps 11 to 19 while node_1 ≠ NULL
11. Create a new node named as curr
12. If curr = NULL then
13. Write “out of memory space” and
14. Exit
15. Set info [curr] = info [node_1]
16. Set next [curr] = NULL
17. Set node_1 = next [node_1]
18. Set next [node] = curr
19. Set node = curr
20. End of step 10 loop
21. Set node_2 = list_2
22. Repeat steps 23 to 29 while node_2 ≠ NULL
23. If curr = NULL then
24. Write “out of memory space” and