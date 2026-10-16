
-   [敏感费罗蒙的选择](https://wiki.example.org/feynmans_learning_method)被应用在当前解 𝑖 与其其他解之间。其他解在满足条件时被应用，即概率条件更优于当前解，即更优于当前解。

2. 观察者蜜蜂

食物来源选择使用敏感费罗蒙

每个观察者蜜蜂，每个食物来源都会生成新的解并更新步长长度

Iter = Iter + 1

应用敏感费罗蒙到当前解。但现有解决方案优于其他解。否则，应将其实验对最佳解的计数记录在案。

3.  scouts 蜜蜂的阶段

试验食物来源的确定应超过“限制”值，或者在每次交互中，只有一只 scouts 蜜蜂被接受。

用于随机食物编号搜索的 scouts 蜜蜂在达到最大迭代次数后会返回到最佳解决方案。

## 9.8 不同参数在 ABC 用于酶优化中的影响

ABC 算法在 scouts 蜜蜂的食物来源数量（*N*）、食物来源数量（*M*）、选定食物来源数量、被派遣到选定食物来源的蜜蜂数量（Nre）、被派遣到其他食物来源的蜜蜂数量（Nsp）、搜索区域半径（Ngh）以及迭代次数（*I*[max]）([Zhang et al. 2010](#ch9.xhtml#ref9_54)) 时更具生产力。初始食物来源位置在满足条件的情况下被表示为该算法的明确问题范围内。

(9.3)  

*X*[*i**j*] = *X*[*j*]^(min) + *r**a**n* (0,1)(*X*[*j*]^(min)−*X*[*j*]^(min))  

where *i* = 1, …, *N* and *j* = 1, …, *j* are ranges in the equation. *N* is the number of parameters. In every area, subsequently, the new solutions created during ABC algorithm *V*[*jk*] within *X*[*k*] are demonstrated in Equation (9.4):

(9.4)  

*V*[*j**k**](*t*+1) = *X*[*j**k**](*t*) + *φ*[*j**k**](*t*)(*X*[*j**k**](*t*)−*X*[*w**k**](*t*))  

*K* = int  (*r**a**n**d* *X* *N*) + 1  

where *ø*[*jk*] and *X*[*jk*] represent the random numbers uniform distribution and the *j*th solution from among the solution set of the *k*th parameter. Though, the *ø*[*jk*] area and parameter *k* are selected casually from the domains \[1 and −1\] and \[1 and *N*\], respectively.Beyond these situations, the explanation for each problem in a suitable way is replaced by the earlier one. The earlier solution is replaced if the new solution is more adaptable. After that, solutions for each bee are selected by the scout bees ([Liu et al. 2018](#ch9.xhtml#ref9_35)).

## 9.9 ABC 用于优化的控制参数

ABC 优化/参数调整是为了在进行分析时选择最合适的参数设计。ABC 算法在参数优化后能够提供最佳参数。早期的 ABC 版本在基本函数上最为高效。尽管 ABC 算法在处理复合和非分离约束问题及函数时的收敛性能并不十分有效（[Karaboga et al. 2014](#ch9.xhtml#ref9_27); [Sonmez 2011](#ch9.xhtml#ref9_48)）。收敛速率和改进（[Karaboga and Basturk 2007](#ch9.xhtml#ref9_26)）通过扰动控制参数频率变化的方法进行分析，该方法通常被称为缩放因子，它通过改变相邻解和参数上限来决定参数的幅度，由 ABC 性能控制。提出的修改版本旨在解决实参优化问题的高效优化。人工蜜蜂群算法（ABCA）的常见修改集中在扰动过程的控制上。基本版本的 ABC 在生成新解时，将频率固定，导致收敛速度缓慢，仅针对单个参数；这是预期结果的父解。但在提议的 ABCA（[Mohapatra et al. 2017](#ch9.xhtml#ref9_39)）中，引入了新的控制参数——修改率（MR）。

## 9.10 ABC 算法的修改

ABC 子部分的变化可能导致不同研究者在参数调节与性能提升之间观察到的差异。为了解决优化问题的受限性，在 ABC 选择过程中的工蜂通常使用 Deb 的规则来调节策略，而不是贪婪的选择程序。ABC 的新变体性能与两种方法相关，即粒子群优化（PSO）和遗传算法（DE），结果相似，ABC 的性能明显。对于大规模问题的解决方案，ABC 被应用（[Karaboga and Basturk 2007](#ch9.xhtml#ref9_26)）。对有限处理技术的应用限制了 ABC 选择阶段，使得整个搜索空间的可行区域得以到达。在选择观察者蜜蜂和工蜂时，引入了 Deb 的规则。针对选择和修改的 ABC 进行了三种策略。这三种策略的修改在 ABC 中被报告为 [Zhu and Kwong (2010)](#ch9.xhtml#ref9_57) 用于数值基准优化。食物来源的选择由观察者蜂进行，以防止早期收敛并提高种群多样性。这些策略包括基于排名选择的选择（RABC）、锦标赛选择（TABC）以及扰动选择（DABC）。修改后的 ABC 性能主要与基本版本和改进版本的结果相关，这三种选择策略分别展示了基本版本和改进版本的表现，并用于提高种群多样性和防止收敛。

## 9.11 ABC 摘要

1. 采集行为通常受蜜蜂的觅食行为启发

2. 为了优化目的，ABC 采用全局搜索

3. 数值优化最初提出（[Karaboga and Basturk 2007](#ch9.xhtml#ref9_26)）

4. 组合优化问题在优化过程中被分析（[Pan et al. 2011](#ch9.xhtml#ref9_42)）

5. 同时用于无约束和受约束优化问题（[Djaballah and Nouibat 2022](#ch9.xhtml#ref9_13); [Karaboga et al. 2014](#ch9.xhtml#ref9_27); [Kasihmuddin et al. 2021](#ch9.xhtml#ref9_29)）

6. 用户预先确定控制参数（即种群规模、最大迭代次数和限制）

7. 它相对简单、灵活且稳健（[Rao et al. 2008](#ch9.xhtml#ref9_43); [Singh 2009](#ch9.xhtml#ref9_47); [Lin et al. 2021](#ch9.xhtml#ref9_34)）

## 9.12 ABC 的应用

ABC 因其易于应用和稳健性而成为最常用的算法。研究人员成功地将其应用于许多不同领域的复杂问题。首先，[Karaboga et al. (2014)](#ch9.xhtml#ref9_27) 的数学问题被扩展到受约束优化问题，随后应用于大脑神经网络（[Karaboga and Basturk 2007](#ch9.xhtml#ref9_26)）、医学模式分类以及聚类问题（[Table 9.2](#ch9.xhtml#table9_2)）([Seyman and Taşpınar, 2013](#ch9.xhtml#ref9_58); [Ilie and Bădicǎ 2013](#ch9.xhtml#ref9_24))。

[Table 9.2 Applications of ABC in Different Fields](#ch9.xhtml#R_table9_2)

| S. No. || Application of ABC || Reference |
| --- | --- | --- |
| 1 || ABC is used for training the multilayer perceptron neural network for classifying the acoustic emission signal toward their particular source || [Omkar and Senthilnath (2009)](#ch9.xhtml#ref9_40) |
| 2 || Investigation of the comparison of the RBF neural network training algorithms in inertial sensor-based terrain classification || [Kurban and Beşdok (2009)](#ch9.xhtml#ref9_30) |
