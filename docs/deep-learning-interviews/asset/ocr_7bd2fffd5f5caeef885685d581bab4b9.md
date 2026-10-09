![](bbox=[0.15, 0.09, 0.88, 0.11])

Name the algorithm that he used and explain in detail why he used it .

# PRB-200 CH.PRB- 8.24.

Further to the above, the scientist then applies the following algorithm:

# Algorithm 3: Algo 1

```
Data: Two vectors v1 and v2 are provided
Apply algorithm xxx on the two vectors
Run algorithm 2
```

# Algorithm 4: Algo 2

```
1 float algo2 (const std:: vector< float > &v1, const
   std:: vector< float > &v2){
2 double mul = 0 ;
3 for (size_t i = 0 ; i < v1.size(); ++ i){
4     mul += v1[i] * v2[i];
5 }
6 if (mul < 0) {
7     return 0 ;
8 }
9 return mul;
10}
```

![](bbox=[0.37, 0.7, 0.64, 0.72])

+   1 Name the algorithm algo2 that he used and explain in detail what he used it for .
2 Write the mathematical formulae behind it .
3 What are the minimum and maximum values it can return?