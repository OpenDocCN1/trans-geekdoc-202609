

每笔贷款违约的概率均为 1.25%，且它们永远不会同时违约。因此，发生违约的概率为 2.5%。令 `x` 为贷款本金回收的百分比。则 `(0.025)(x) = 0.01`，或 `x = 0.4`，意味着 40% 的 `$10M = $4M` 将以 0.01 的概率被回收。然而，另一笔贷款获得了 `$0.2M` 的利润，因此 1 年期 99% `V@R` 为 `$10M - $4M - $0.2M = $5.8M`。

此外，该投资组合的 1 年期 99% ES 是在损失大于 `$5.8M` 的情况下的预期损失。由于损失在 `$5.8M` 和 `$9.8M` 之间均匀分布，其均值为 `$7.8M`。

## 8.2 巴塞尔协议与风险度量

风险度量用于指定必须添加到银行或金融机构的资本要求，以提供缓冲来应对潜在风险，从而满足监管机构的要求。1980 年，比利时、加拿大、法国、德国、意大利、日本、卢森堡、荷兰、瑞典、瑞士、英国和美国的监管当局为监测和维持健康的投资环境，成立了银行监管委员会，即 `Bank for International Settlements` (BIS)。此后，其他几个国家和地区的当局也加入了。他们定期在瑞士巴塞尔市会面（请参见 [图 8.3](#c08.xhtml#c08-fig-0003) 中的地图），1996 年，巴塞尔委员会对 1988 年协议发布了一项修正案，该修正案随后被称为“BIS 88” [\[6\]](#c08.xhtml#c08-bib-0006) 或“巴塞尔 I”。

从数学上讲，定义在具有有限二阶矩的随机变量空间上的风险度量 `ρ(·): L²(Ω; P) → R` 最好应当具备一些理想特性。在以下内容中，`L_A` 和 `L_B` 分别为投资组合 A 和 B 的损失变量。

![FIGURE 8.3 瑞士巴塞尔的位置。巴塞尔城市州地图，包含城市和城镇。照片检索自 https://ontheworldmap.com/switzerland/canton/basel-stadt/canton-of-basel-stadt-map-with-cities-and-towns.html。](images/c08f003.png)

[**FIGURE 8.3**](#c08.xhtml#R_c08-fig-0003) 瑞士巴塞尔的位置。巴塞尔城市州地图，包含城市和城镇。照片检索自 [https://ontheworldmap.com/switzerland/canton/basel-stadt/canton-of-basel-stadt-map-with-cities-and-towns.html](https://ontheworldmap.com/switzerland/canton/basel-stadt/canton-of-basel-stadt-map-with-cities-and-towns.html)。

1.  *单调性：* 如果一个投资组合的损失金额在样本空间的每种可能结果下都小于另一个投资组合的损失金额，则其风险度量应小于第二个投资组合的风险度量。 [`L_A ≤ L_B ⇒ ρ(L_A) ≤ ρ(L_B)`]

