# Mastering Classification Algorithms for Machine Learning

4 2 34 1 2 2 2 2 2 2 2 2 2 1.00 ? 200 4.0
? 1

.. . . . . . . . . . . . . . . . .
.. .

150 1 46 1 2 2 1 1 1 2 2 1 1 1 7.60 ? 242 3.3
50 2

151 2 44 1 2 2 1 2 2 1 2 2 0.90 126 142 4.3
? 2

152 2 61 1 1 2 1 1 2 1 1 2 2 0.80 75 20 4.1
? 2

153 2 53 2 1 2 1 2 2 2 1 1 1 1.50 81 19 4.1
48 2

154 1 43 1 2 2 1 2 2 2 2 1 1 2 1.20 100 19 3.1
42 2

[155 rows x 20 columns]

We notice 155 data points with 20 columns.
The first column contains the target variable, that is, whether the patient died. We will rename this column and leave the rest of the column names as it is:

```
df.rename(columns = {"target"}, inplace = True)
df.head()
target 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17
18 19
0 2 30 2 1 2 2 2 1 2 2 2 2 1.00 85 18 4.0
? 1
1 2 50 1 1 2 2 1 2 2 2 2 0.90 135 42 3.5
? 1
2 2 78 1 2 2 1 2 2 2 2 2 0.70 96 32 4.0
? 1
3 2 31 1 ? 1 2 2 2 2 2 2 2 0.70 46 52 4.0
80 1
4 2 34 1 2 2 2 2 2 2 2 2 2 1.00 ? 200 4.0
? 1
```