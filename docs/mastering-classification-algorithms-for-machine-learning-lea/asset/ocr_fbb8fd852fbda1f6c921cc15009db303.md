# Boosting Algorithm 251

```
print(n)
0.9724993774095615
0.8077553943105392
0.34266990825021064
0.7457845827525092
0.09602112485743897
0.253775848540571
0.7134304936851307
0.735426110690173
0.3530574686977209
0.5755371067120092
```

Now, the number 0.972 lies between 0.950 and 0.975. This corresponds to the data point where x = 8.So, we pick this data point for the new dataset. We follow the same method for the rest of the nine randomly generated numbers and the dataset, as shown in Table 8.7:

| Lower Limit | Upper Limit | Random Number | x | y |
|---|---|---|---||
| 0.950 | 0.975 | 0.9724993774095615 | 8 | 1 |
| 0.550 | 0.950 | 0.8077553943105392 | 7 | 0 |
| 0.150 | 0.550 | 0.34226990825021064 | 6 | 0 |
| 0.550 | 0.950 | 0.7457845827525092 | 7 | 0 |
| 0.075 | 0.100 | 0.09602112485743897 | 3 | 1 |
| 0.150 | 0.950 | 0.253775848540571 | 6 | 0 |
| 0.550 | 0.950 | 0.7134304936851307 | 7 | 0 |
| 0.150 | 0.550 | 0.735426110690173 | 7 | 0 |
| 0.150 | 0.550 | 0.3530574686977209 | 6 | 0 |
| 0.550 | 0.950 | 0.5755371067120092 | 7 | 0 |

Table 8.7: Dataset formed for the second iteration.

Notice that the dataset formed, as shown in Table 8.7, mainly contains the data points where a wrong prediction was made in the first iteration. For our convenience, us sort these data points in Table 8.7 in the ascending order of the value of x. We get the dataset as shown in Table 8.8: