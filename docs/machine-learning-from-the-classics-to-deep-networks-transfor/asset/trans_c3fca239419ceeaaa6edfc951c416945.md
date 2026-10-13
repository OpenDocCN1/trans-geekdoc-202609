
其中 `F[n] := F` 和 `H[n] := H` 的定义显而易见，且

```
Q_n = [σ_n^2 0 ... 0; 0 0 ... 0; 0 0 ... 0; ...], R_n = σ_v^2 (scalar)。
```

![Equation](images/B978044329238500010X/si516.png)

[图 4.21](#Chp004_119-175_B978044329238500010X.xhtml#f0115)A 显示了特定实现 `y[n]` 的值，而 [图 4.21](#Chp004_119-175_B978044329238500010X.xhtml#f0115)B 显示了 AR(2) 的相应实现（红色）以及预测的卡尔曼滤波序列 `x̂[n]`。观察可知，匹配效果非常好。对于 AR 过程的生成，我们使用了 `l = 2`、`α[1] = 0.95`、`α[2] = 0.9`、`σ[η]² = 0.5`。对于卡尔曼滤波器输出噪声，`σ = v21`。

![Figure 4.21 (A) A realization of the observation sequence, yn, which is used by the Kalman filter to obtain the predictions of the state variable. (B) The AR process (state variable) in red together with the predicted by the Kalman filter sequence (gray), for Example 4.4. The Kalman filter has removed the effect of the noise vn.](images/B978044329238500010X/gr021.jpg)

图 4.21 (A) 观测序列 `y[n]` 的一个实现，卡尔曼滤波器利用它来获得状态变量的预测。(B) AR 过程（状态变量，红色）与卡尔曼滤波器预测序列（灰色）的对比，针对 [示例 4.4](#Chp004_119-175_B978044329238500010X.xhtml#enun0075)。卡尔曼滤波器已消除噪声 `v[n]` 的影响。

## 习题

1.  4.1  证明方程组

    `Σθ = p`

    ![Equation](images/B978044329238500010X/si523.png)

    1.  若 `Σ > 0` ![Equation](images/B978044329238500010X/si524.png) 则有唯一解，若 `Σ` 为奇异矩阵则有无穷多解。

2.  4.2  证明方程组

    `Σθ = p`

    ![Equation](images/B978044329238500010X/si523.png)

    1.  总是有解。

3.  4.3  证明 `J(θ)`（均方误差）图形的等值轮廓形状
