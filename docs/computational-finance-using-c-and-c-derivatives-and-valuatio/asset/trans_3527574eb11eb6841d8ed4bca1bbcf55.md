

## 变体期权的网格法 | 5.4

![](img/9db5fe198f89b66da8d21f3e2bc8868a_156_0.png)

**图 5.7** 资产网格点数增加时，欧式下行看涨期权 ($B < E$) 估计值的绝对误差。

```
$$\hat{b}_j = 1 - \Theta_m \Delta t - \frac{\Theta_m \sigma^2 S_j^2 \Delta t}{2\Delta S} = 1 - \Theta_m \Delta t \{r + \sigma^2 j^2\}}$$

$$\{\tilde{c}_j = \Theta_m \Delta t + \frac{(r-q)S_j \Delta t + \frac{\sigma^2 S_j^2 \Delta t}{2\Delta S} = \Theta_m \Delta t \{(r-q)j + \sigma^2 j^2\}}$$
```

可以看出这些系数与第 5.4.2 节中方程 (5.4.16) 到 (5.4.21) 给出的系数相同。

我们现在提供使用非均匀网格评估欧式下行和看涨期权的示例。

## 下行触出看涨期权的定价

此处，图 5.7 和 5.8 展示了使用非均匀网格而非均匀网格可以获得更高的精度。均匀网格是使用第 5.4 节和代码摘录 5.18 中概述的方法构建的。也就是说，一条资产网格线与当前资产价格 $S_0$ 重合，其他网格线以均匀间距 $\Delta S$ 分布在 $S_0$ 的上方和下方。这种方法的缺点是，根据障碍水平 $B$ 距离最近资产网格点的距离 $d_s$，将会产生一个未指定的定价误差。

![](img/9db5fe198f89b66da8d21f3e2bc8868a_157_0.png)

**图 5.8** 随着资产网格点数 $n_s$ 的变化，欧式下行触出障碍期权 ($E < B$) 估计值的绝对误差。我们展示了使用均匀和非均匀网格获得的结果对比；未采用对数变换。均匀网格的算法描述于第 5.4.3 节。使用了 Crank–Nicolson 方法 ($\Theta_{m_i} = 0.5$)，非均匀网格的概述见第 5.4.2 节，参数为 $E = 50.0$，$S_0 = 52.5$，$S_s = 65.0$，$S_{max} = 300.0$，$T = 0.5$，$\sigma = 0.2$，$r = \log(1.1)$，$q = 0.0$  $n_1 = 100$。使用代码摘录 4.7 中的解析公式得到的正确期权值为 17.0386。此外，随着资产点数 $n_s$ 的增加，$d_s$ 的幅度将在 0 到 $\Delta S/2$ 范围内震荡。

当 $d_s < 0$ 时，网格将准确；但当 $|d_s| \sim \Delta S/2$ 时，会产生巨大的定价误差。这导致图中 5.7 和 5.8 所示的震荡定价误差。

从图 5.7 和 5.8 可以看出，在这种情况下定价误差小得多，且没有表现出均匀网格产生的剧震荡。在下面的代码摘录 5.19 中，我们提供了用于获取图 5.7 和 5.8 中下行触出看涨期权非均匀网格值的程序。虽然此程序只处理欧式期权，但可以利用代码摘录 5.18 中的相同技术轻松修改，以处理美式期权；这留给读者练习。

## 变体期权网格法章节 | 5.4

```cpp
void barrier_downout(double barrier_level, double theta_m, double asset_price, double sigma, double r, double T, double strike, double put, double option_value, double greeks[], double q, long ns, long nt, double smax) {
    // 资产间隔数
    nt // 间隔数
    double a,b,c,a1,b1,c1,opt_vals,rhs,s,u;
    double ds,time_step;
    long i;
    double t0,t1,t2,mat=0.0;
    long n1,n2,n3;
    double ds_plus,ds_minus,temp1,temp2;
    double D=0;

    n1 = floor(asset_price/smax);
    if (n1 < 0) {
        printf("increase the number of asset points %d\n", n1);
    }
    n2 = ns;
    ds = asset_price/n1;
    time_step = T/n2;
    n3 = n2+2 // 分配所需数组的节点数（大小均为 n3+1）
    s[0]=0;
    s[n1]=asset_price;
    for(i=0; i<n1; i++) {
        s[i+1]=(double)ds;
    }
    // 设置资产价格下方
    for(i=0; i<n2; i++) {
        s[i+1]=asset_price+(double)i;
    }

    // 寻找对应障碍水平的索引
barrier_index=0;
    while(barrier_level > s[barrier_index]) {
        barrier_index++;
    }
    if (barrier_level == s[barrier_index]) { // 减少障碍索引
        barrier_index--;
    }
    if (barrier_level < s[barrier_index]) // 如果障碍不对应现有的线，则创建另一个
        for(i=0; i<n1-barrier_index; i++) {
            s[barrier_index+i+1]+=(double)ds;
        }
        barrier_index++;
        s[barrier_index]=barrier_level;
        if (n1-barrier) {
            n1++;
        }
    }
    // 设置 RHS 和 LS 系数（时间步 j）a[j], b[j]
    ... (此处代码逻辑保持原文，仅翻译注释) ...
```

## 5.4.4 对数变换与均匀网格

到目前为止，我们处理的是标准的 Black–Scholes 方程，即

