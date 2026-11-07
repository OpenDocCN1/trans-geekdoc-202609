
本质上，`observed variable` 是指我们至少在理论上可以获得直接 `measurement` 的任何变量。例如，`height` 将被视为 `observed variable`。我们可以轻松测量它并拥有描述它的明确单位（例如，英寸、英尺等）。如果我们无法获得某个变量的此类 `direct` 测量值，并且需要或希望基于其他可测量变量推断其存在，那么该变量通常被视为 `unobserved`。`latent variable` 最经典的例子是智力（`IQ`）。智力是一种 `construct`，很难甚至不可能在不基于其他标准进行推断的情况下进行测量，例如 `IQ` 测试、临床访谈等，因此，要测量被称为“`IQ`”的东西，必须通过其他更可观察的变量来 `indicate` 它。因此，这些观察变量通常被称为 `indicators`，原因在于它们 `indicate` 未观察到的变量。

带着这种区分在心中，并再次进行一点批判性思考，很快就会意识到所有变量至少在哲学上都是 `unobservable`，尽管有些变量比其他变量更少不可观察。例如，再次考虑 `height`。`height` 是可观察还是不可观察？如果我们测量你的 `height` 为 70 英寸，从心理测量学角度来看，我们并没有测量你的 `true` `height`。我们仅仅是对你的 `height` 的 `measurement`，作为其 483true height 可能是什么的 `indicator`。因此 `Height` 是一种不可观察的变量，但有人可能会争辩说它比诸如 `IQ` 之类的变量要少得多不可观察。同样，尽管一个人的 `weight` 被认为是可观察的，但最终，`weight` 也是一种不可观察的 `construct`，对 `weight` 的测量只是在尝试“触及”该构念。这就是当我们将这些思想和区分推向其哲学极限时，我们意识到所有变量本质上都是 `unobservable`，但有些比其他更少。然而，为了构建和分析路径和结构方程模型，我们将把较少不可观察的变量视为可观察的，并且能够直接测量。诸如 `height`、`weight`、`distance`、`temperature`、`biometric pressure` 等变量，我们将认为它们是可观察且易于测量的变量。诸如 `IQ`、`self-esteem`、`happiness`、`depression`、`self-actualization` 等变量，我们将认为它们是不可观察的或 `latent` 变量，必须由更可观察的变量来指示。

## 13.4 路径分析：扩展回归并预览 SEM

到目前为止，我们已经非正式地讨论了路径分析。现在我们将模型更正式地呈现。路径分析本质上是一种结构方程模型，仅包含观察变量，而不 `direct` 包含不可观察或潜变量。然而，路径模型确实包含残差或 `error` 变量，而这些变量本质上是 `latent`。它们被认为不可观察，因为我们不能字面地 `see` 或轻松测量此类残差变量内部可能是什么，也不知道它究竟由什么组成，这意味着它必须由更可观察的变量来指示。这符合 `latent variable` 的定义。路径模型的等效解释是作为本书前面介绍的经典回归模型的扩展。

[图 13.2](#c13.xhtml#f13.2) 是一个非常简单的路径模型示例（改编自 [Denis, 2021a](#ref.xhtml#re_CIT000087)），其中一代的 `IQ` 被假设为预测下一代的 `IQ`。

![图 13.2 基本路径图，显示父母 IQ 预测后代 IQ。经 John Wiley & Sons - Books 许可使用，摘自 Daniel J. Denis 所著《Applied Univariate, Bivariate, and Multivariate Statistics》，© 2021；许可通过 Copyright Clearance Center, Inc. 授予。返回正文.⏎](images/fig13.2.jpg)

`Figure 13.2` 基本路径图，显示父母 `IQ` 预测后代 `IQ`。经 John Wiley & Sons - Books 许可使用，摘自 Daniel J. Denis 所著《Applied Univariate, Bivariate, and Multivariate Statistics》，© 2021；许可通过 Copyright Clearance Center, Inc. 授予。[返回正文.⏎](#c13.xhtml#re_f13.2)

我们在 [图 13.2](#c13.xhtml#f13.2) 中看到，父母 `IQ` 是其后代 `IQ` 的预测因子，而后代 `IQ` 则是下一代 `IQ` 的预测因子。在图中，`d1` 和 `d2` 是 `residual` 或 `error` 变量，包含由前一个预测因子未解释的方差。这些通常将路径系数设为 1，而模型中的其他参数（例如，沿箭头的路径系数）需要进行估计。

路径模型对研究人员和科学家有用，因为它们允许陈述更复杂的假设，而这些假设在经典回归模型中否则难以甚至不可能操作化和检验。然而，正如已经强调的那样，它们并不能比典型的回归模型更允许得出因果结论。在 `IQ` 传递模型中，认为父母 `IQ` 至少是后代 `IQ` 的 `partial cause` 可能并不错误，但该因果陈述是基于 `IQ` 传递的可遗传证据得出的，而不是因为我们使用了路径模型。`The causal statement is supported by the variables used in the model, not the fact that we are using a path analysis.` 这种区分非常重要。484

### 13.4.1 外生变量与内生变量

`exogenous` 变量是指源自系统外部且没有箭头指向它的变量。在 [图 13.2](#c13.xhtml#f13.2) 中，父母 `IQ` 就是这样一个外生变量。`endogenous` 变量至少有一个箭头指向它，例如路径图中的后代 `IQ`。[图 13.3](#c13.xhtml#f13.3) 是另一个路径模型示例，其中包含父母 `intelligence`、`environment` 与孩子 `IQ` 之间假设关系的模型。该模型中唯一的内生变量是孩子的 `IQ`，因为父母 `intelligence` 和 `environment` 都是外生的。

![图 13.3 路径模型的示例，显示孩子的 IQ 是父母智力和环境的功能。返回正文.⏎](images/fig13.3.jpg)

`Figure 13.3` 路径模型的示例，显示孩子的 `IQ` 是父母 `intelligence` 和 `environment` 的函数。[返回正文.⏎](#c13.xhtml#re_f13.3)

图中存在相关性（`r` = 0.6036，`r` = 0.4771，`r` = 0.7653），然而理论化的关系包括父母 `intelligence` 和 `environment` `predicting` 孩子的 `IQ`。父母 `intelligence` 与 `environment` 之间的双向箭头通常被称为 `unanalyzed` 关系，这仅仅意味着只对相关性进行建模，而不对一个变量对另一个变量的方向路径进行估计。例如，来自父母 `intelligence` (`a`) 的路径被视为 `analyzed` 关系，因为它不是双向的，而是假设了一种方向性关系，即父母 `intelligence` 预测孩子的 `IQ`。

## 13.5 验证性因子分析模型
