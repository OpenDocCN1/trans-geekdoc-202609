```
6  
7      std:: cout << ( * it) << "," << 
     \|\>  sigmoid001(t0).data().detach().item()
8      .toFloat()<< ","<< sig_approx (t0).data().detach().item().
9      toFloat()<< \"\n\" ;
1  
0  }
```

![](bbox=[0.23, 0.25, 0.82, 0.28])

*An the values are presented in Table 8.2:*

| Value | Sig | Approx |
| :---: | :---: | :---: |
| 0 | 0.5 | 0.5 |
| 0.1 | 0.524979 | 0.52597 |
| 0.2 | 0.549834 | 0.5518 |
| 0.3 | 0.574443 | 0.577353 |
| 0.4 | 0.598688 | 0.602499 |
| 0.5 | 0.622459 | 0.627115 |
| 0.6 | 0.645656 | 0.65109 |
| 0.7 | 0.668188 | 0.674323 |
| 0.8 | 0.689974 | 0.69673 |
| 0.9 | 0.710949 | 0.71824 |
| 0.99 | 0.729088 | 0.736785 |

TABLE 8.2: Computed values for the Sigmoid and the Sigmoid approximation .

# Tanh