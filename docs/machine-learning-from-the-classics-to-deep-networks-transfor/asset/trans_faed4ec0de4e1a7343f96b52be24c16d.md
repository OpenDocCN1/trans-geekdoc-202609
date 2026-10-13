

## 算法流程

*   **For** `r = 1, 2, …, R`，**Do**；在实践中，`R = 3` 次迭代已足够。

    1.  **For** `j = 0, 1, 2, …, 9`，**Do**

        1.  **For** `i = 1, 2, …, I`，**Do**

        2.  
            ```
            c_ij = exp(b_ij) / sum_{k=0}^{9} exp(b_ik)
            ```

        3.  **End For**

        1.  
            ```
            s_j = sum_{i=1}^{I} c_ij * u_hat_{j|i}
            ```

        2.  
            ```
            v_j = (||s_j||^2 / (1 + ||s_j||^2)) * (s_j / ||s_j||)
            ```

        1.  **For** `i = 1, 2, …, I`，**Do**

        2.  
            ```
            b_ij <- b_ij + v_j^T * u_hat_{j|i}
            ```

        3.  **End For**

    2.  **End For**

*   **End For**

*   **Return** `v[j]`，`j = 0, 1, …, 9`。

