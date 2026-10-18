
where `z^H := (z_1^H, ..., z_p^H) = H^ z ~ N_p(0_p, I_p)` by the orthogonality of `H`. Thus `y_{ik} = sum_{i=1}^{p} lambda_i (z_i^H)^2`, where `z_i^H ~ iid N(0, 1)` implies `(z_i^H)^2 ~ iid chi_1^2` with the mgf of `(1 - 2t)^{-1/2}`. The mgf of `y_{ik}` is therefore `M_{y_{ik}}(t) = prod_{i=1}^{p} (1 - 2t lambda_i)^{-1/2}` for `t < 1 / (2 lambda_max)`, and ([14.21](#c14.xhtml#c14-disp-0074)) reduces to

`P(x_i in B_G(S_i)) >= 1 - exp(-a^2 t - 1/2 sum_{i=1}^{p} ln(1 - 2t lambda_i))`.

First, we bound below the right‐hand side of the inequality by another function of `t`, by noting that for all `i = 1, ..., p`, `1 - 2t lambda_i >= 1 - 2t lambda_max` for `0 <= t < 1 / (2 lambda_max)`:
