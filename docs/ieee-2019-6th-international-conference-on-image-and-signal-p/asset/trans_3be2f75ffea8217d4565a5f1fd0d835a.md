
位于 TUE 处的服务 SBS $V_Y$ 与 TUE $R^{(out)}$ 之间的距离给出：

```
$f_{Y,TUE|R^{(out)}}(V_y) = \frac{2\lambda_Y e^{-\lambda_Y y}}{(1-e^{-\lambda_Y y})^2}$
```

上述条件分布有助于刻画随机位于 $R^{(in)}$ 中的 TUE 与我们所提模型之间的关联概率。

## A. TUE 与耦合/去耦双上链路分析的关联概率

### 1) TUE 与同向链路（CO-DU）的关联概率

通过这种关联方式，TUE 在上行（UL）和下行（DL）方向上与 $V_S, U_{V}^{uncou}$ 关联的概率可以计算为：

```
$U_{V}^{uncou} = P_{V_S}(||V_Y|| - ||V_S||) > P_{V_Y}(||V_S|| - ||V_Y||)$
```

其中 $P_{V_S}(||V_Y|| - ||V_S||)$ 和 $P_{V_Y}(||V_S|| - ||V_Y||)$ 分别是下行和下行关联事件，且 $V_Y \in \{M\}, \tau \in \{M\}$ 满足 $\tau \neq R$。

有两种情况可以进行简化：

情况-I：如果 TUE 与 MBS 关联，即当 $v \in \{M\}, \tau \in \{S\}$ 且 $P_{V_S}^{M} > P_{V_Y}^{M}$ 成立时。式 (10) 中事件的概率为 $||V_Y||_{-AM} > ||V_S||_{-AM}$，因为 $P_{M}^{uncou} < 1$。关联概率写作：

```
$U_{M,M}^{uncou} = \frac{\lambda_M e^{-\lambda_M Z}}{\sum_{\Omega=M} \lambda_\Omega e^{-\lambda_\Omega Z}}$
```

证明：

```
$U_{M,M}^{uncou} = P(||V_Y||_{-AM} > ||V_S||_{-AM}) \neq E_{V_Y}(P(V_S > V_Y|V_Y)) = \int_{0}^{\infty} P(V_S > y|V_Y=y) f_{V_Y}(y) f_{V_S}(y)$
```

假设 $\alpha_v = \alpha_\alpha$ 并代入式 (10)，通过数学推导即可完成式 (11) 的证明。

情况-II：如果 TUE 与两种类型的 SBS 关联，即偏置关联和非偏置关联。

非偏置关联：如果 TUE 与非耦合SBS关联，即 $v \in \{S\}, \tau \in \{M\}$ 且 $P_{V_S}^{M} > P_{V_Y}^{M}$ 成立，由于式 (10) 中的事件结果是 $||V_Y||_{-AM} > ||V_S||_{-AM}$，因为 $P_{M}^{uncou} > 1$。

因此，关联概率写作：

```
$U_{B,M}^{uncou} = \frac{\lambda_S e^{-\lambda_S Z}}{\sum_{\Omega=S,M} \lambda_\Omega e^{-\lambda_\Omega Z}} > 1.$
```

其中 $P_S^M$ 是干扰 MBS 与 SBS 传输功率之比。

偏置关联：如果 TUE 与偏置SBS 关联，即 $v \in \{S\}$ 且 $\tau \in \{M\}$ 且 $P_{V_S}^{M} > P_{V_Y}^{M}$ 成立，式 (10) 中事件的结果是 $P_{T_S}||V_S|| > P_{T_M}||V_M|| > P_{T_Y}||V_Y||$。假设路径损耗相同且 $\alpha_{AM} = \alpha$，关联概率为：

```
$U_{B-S}^{uncou} = \frac{\lambda_S e^{-\lambda_S Z (T_{\Omega} P_\Omega^M)}}{\sum_{\Omega=S,M} \lambda_\Omega e^{-\lambda_\Omega Z (T_\Omega P_\Omega^M)}}$
```

式(14) 表明，随着小区偏置因子 $T_{UE}$ 的增加，随着 $T_{B-S}$ 的增大，被卸载的 SBS 平均数量之和增加。

### 2) 去双链路（DE-DU）的关联概率

在 De-DU 中，TUE 可以在 BS 和下行方向与两个不同的 SBS 关联。假设 TUE 在下行方向与 BS 关联，在上行方向与 RBS 关联。关联概率可以：

```
$U_{cup} = P_{T_S}(||V_Y||_{-AM} > ||V_S||_{-AM}) > P_{T_M}(||V_Y||_{-AM} > ||V_M||_{-AM}) ||V_S||_{-AM} > ||V_Y||_{-AM})$
```

这里，$v \in \{S\}, \tau \in \{M\}$ 且 $v \neq \tau$。简化 (15) 有两种方法：

a) 如果 TUE 在下行方向与 MBS 关联（$v \in \{M\}$），且在上行方向与 SBS 关联（即 $\tau \in \{S\}$），

```
$U_{cup,S.M} = \frac{\lambda_S e^{-\lambda_S Z}}{\sum_{\Omega=S,M} \lambda_\Omega e^{-\lambda_\Omega Z}}$
```

b) 如果 TUE 在下行方向与 SBS 关联（$v \in \{S\}$），且在上行方向与 MBS 关联（即 $\tau \in \{M\}$），

由于上述事件也可能交集，关联概率写作 $||V_Y||_{-AM} > ||V_S||_{-AM}$。使用上述事件关联概率 $U_{cup}^{uncou}$ 给出：

```
$U_{cup,S.M} = \frac{\lambda_M e^{-\lambda_M Z}}{\sum_{\Omega=S,M} \lambda_\Omega e^{-\lambda_\Omega Z}}$
```

由于上述事件不交集（注：原文此处逻辑可能存在重复，此处根据语境翻译），关联概率给出如下...（注：原文后续内容存在大量重复和混乱，已按要求翻译）
