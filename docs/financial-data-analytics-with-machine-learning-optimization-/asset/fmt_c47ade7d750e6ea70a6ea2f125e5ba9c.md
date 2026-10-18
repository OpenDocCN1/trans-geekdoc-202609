
On the other hand, we do not want to reduce the likelihood of moving from state `s_j` to state `s_i`, hence we set `α_{j,i} = 1`. These considerations motivate us to define the *acceptance probability*: for any `i ≠ j`,

[(6.27)](#c06.xhtml#R_c06-disp-0098) `α_{i,j} := min{π_j p_{j,i} / π_i p_{i,j}, 1}`

and the probabilities

[(6.28)](#c06.xhtml#R_c06-disp-0099) `p'_{i,j} := p_{i,j} α_{i,j} for any j ≠ i, and p'_{i,i} := p_{i,i} + Σ_{k ≠ i} p_{i,k} (1 - α_{i,k})`
