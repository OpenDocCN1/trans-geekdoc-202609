# Algorithm

Steps:

+   1. if n=0then array is underflow and stop
2. read data as element to be deleted
3. read location at where deletion will be made
4. k=LB
5. repeat step 6 while a(k) ≠ data
6. k=k+1
7. repeat step 8 while k< UB
8. a(k)=a(k+1)
9. k=k+1
10. a(UB)=NULL
11. UB=UB-1
12. Stop

# Merging

This operation is use to merge two sorted array and create a third array in the sorted order. A simple algorithm is given.

Note:

+   LBA: lower bound of array_1
UBA: upper bound of array_1
LBB: lower bound of array_2
UBB: upper bound of array_2

# Algorithm

Steps:

+   1. i=LBA, J=LBB, K=0
2. repeat step 3 to 4 where I ≤ UBA and I ≤ UBB
3. if A(i) < B(j) then
4. c(k)=A(i)
5. i=i+1
6. else
7. c(k) = A(i)
8. j=j+1
9. k=k+1