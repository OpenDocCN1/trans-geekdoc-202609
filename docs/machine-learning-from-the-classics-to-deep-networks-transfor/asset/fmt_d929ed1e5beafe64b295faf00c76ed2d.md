
### 算法流程

**For** `n = 1, 2, 3, …` **Do**

1. **For** `i = 1, 2, …, N` **Do**
    1. Draw `x_n^(i) ~ q(x | x_{n-1}^(i), y_n)`
    2. 
```
w_n^(i) = w_{n-1}^(i) * p(x_n^(i) | x_{n-1}^(i)) * p(y_n | x_n^(i)) / q(x_n^(i) | x_{n-1}^(i), y_n)
```
2. **End For**
3. **For** `i = 1, 2, …, N` **Do**
    1. Compute the normalized weight, `W_n^(i)`.
4. **End For**
5. Compute `N_eff`; Eq. [(17.40)](#Chp017_855-884_B9780443292385000238.xhtml#deq58).
6. **If** `N_eff ≤ N_T`; preselected value `N_T`.
