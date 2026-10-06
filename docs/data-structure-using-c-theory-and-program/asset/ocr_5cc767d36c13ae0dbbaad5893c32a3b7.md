# Chapter 2 Introduction to Array

+   10. repeat step 11 while i ≤ UBA
11. c(k)=A(i)
12. i=i+1
13. k=k+1
14. repeat step 15 while j ≤ UBB
15. c(k) = B(j)
16. j=j+1
17. k=k+1
18. Stop

# 2.4 REPRESENTATION OF ONE-DIMENSION IN MEMORY

![](bbox=[0.348, 0.343, 0.715, 0.413])

| Actual Address in the Memory | 1100 | 1104 | 1108 | 1102 | 1106 | 1120 |
|---|---|---|---|---|---|---||
| Elements | 15 | 7 | 11 | 44 | 93 | 20 |
| Address with respect to the array (Subscript) | 0 | 1 | 2 | 3 | 4 | 5 |

![](bbox=[0.383, 0.564, 0.515, 0.587])

# Calculation in single (one Address) Dimension Array

Let A be a 1-D array with n elements. As array are stored in consecutive memory location, the system need not keep track of the address of every element of A, but need to keep track of the address of 1st element only, denoted by: base address (A). The address of a particular element in a 1-D array is given below:
Address of element a[k]=B+W*K

Where B=size of each element of the array
K=address of the element.

Q1. Suppose the base address of the 1st element of the array is 5000 and each element of 5th element of a 1-D array occupies 2 bytes in the memory, then address will be given:

Solution: apply the formula
Address of element a[k] = B + W * K
Base address=5000