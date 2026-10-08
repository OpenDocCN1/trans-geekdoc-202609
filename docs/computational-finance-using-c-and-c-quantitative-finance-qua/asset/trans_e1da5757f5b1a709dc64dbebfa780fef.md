

# 使用 C 和 C# 进行计算金融

```cs
int iflag=0;
nval = MonteCarloSim(ref iflag);
```

```cs
if (iflag != 0)
throw new Exception(Pre_string_ + "---- An error occurred in a call to the pricing library");
```

```cs
val *= fx_spot * NumberOfUnits_;
return val;
```

```cs
Pre_string_ = Name() + "(* + Reference_ + *)";
if (Time_To_Expiry_ < 0.0)
throw new Exception(Pre_string_ + "---- Time to be less than zero years");
```

```cs
if (NumberOfUnits_ < 0)
throw new Exception(Pre_string_ + "---- Number of units cannot be less than zero");
```

```cs
if (Strike_ < 0)
throw new Exception(Pre_string_ + "---- The strike cannot be less than zero");
```

```cs
private double MonteCarloSim(ref int iflag)
{
    double[] C = new double[n_ * n_];
    double half = 0.5;
    double zero = 0.0;
    double sum_val = zero;
    double tol = 1e-8;
    double opt_val = 0.0;

    // 设置协方矩阵
    for (int i = 0; i < n_; i++) {
        for (int j = 0; j < n_; j++) {
            C[i * n_ + j] = Sigma[i] * Sigma[j] * Time_To_Expiry_;
        }
    }

    double[] MEANS = new double[n_];
    // 设置均值
    for (int i = 0; i < n_; i++) {
        MEANS[i] = (RiskFreeRate - Sigma[i] * Sigma[i] * half) * Time_To_Expiry_;
    }

    int seed = 111;
    PricingUtils.set_seed(seed);
    int len_rvec = (n_ + 1) * (n_ + 2) / 2 + 1;
    double[] R = new double[len_rvec];
    double[] Z = new double[n_];
    double disc = Math.Exp(-RiskFreeRate * Time_To_Expiry_);
```

### 代码片段 8.12（续上）。

```cs
int is_fcall = 1;
PricingUtils.multivariate_normal(is_fcall, ref MEANS[0], C, n_, tol, rvec[0], Z[0], iflag);

is_fcall = 0;
for (int i = 1; i <= NumberScenarios; i++) {
    PricingUtils.multivariate_normal(is_fcall, ref MEANS[0], C, n_, tol, rvec[0], Z[0], iflag);
    for (int j = 0; j < n_; j++) {
        ST_[j] = S_[j] * Math.Exp(Z[j]);
    }
    sum_val += Payoff();
}
opt_val = sum_val * disc / (double)NumberScenarios;
return opt_val;
```

### 代码示例 8.12（续接）。

在任意数量的底层资产上；派生类实现了抽象方法 `Payoff`。在本书的早期章节中，我们考虑了具有标准收益的期权，例如：普通看跌期权、普通看涨期权以及基于最小/最大资产的看涨/看跌期权。然而，`GenericEquityBasketOption` 现在提供了提供自定义 `Payoff` 函数的可能性，以便对非标准收益的期权进行定价。

下面我们提供了针对两种资产和十种资产的期权示例。资产分别为 Drinks、Beverage-Ltd、H-Ltd 和 Wines-Ltd。交易属性为到期时间为一年，所有波动率均为 0.2，数量为 100。为期权定价所需的其他信息（如股票之间的相关性和无风险利率）则从市场字典中获取。

结合投资组合定义使用交易类 `GenericEquityBasketOption` 的语法如下：

| 属性 | 值 |
| :--- | :--- |
| Trade | GenericBasketOptionDeal:Payoff=MaxPut |
| Reference | A |
| Strike | 100.0 |
| Volatilities | 0.2, 0.2, 0.2, 0.2 |
| Equities | Drinks, Beverage-Ltd, H-Ltd, Wines-Ltd |
| NumberOfUnits | 100 |
| Time_Expiry | 1.0 |
| NumberScenarios | 100 |

而对于交易类 `FourEquityOption`：

| 属性 | 值 |
| :--- | :--- |
| Trade | FourEquityOptionDeal |
| Reference | B |
| Volatility1 | 0.2 |
| Volatility2 | 0.2 |
| Volatility3 | 0.2 |
| Volatility4 | 0.2 |
| Equity1 | Drinks, Beverage-Ltd |
| Equity3 | H-Ltd, Wines-Ltd |
| NumberOfUnits | 100 |
| Strike | 100.0 |
| Time_Expiry | 1.0 |
| OptionType | put, MinMax |
| MonteCarlo | Yes |
| NumberScenarios | 1000 |

关键区别在于 `GenericEquityBasketOption` 的条目包含了额外的指令 `Trade=GenericEquityOptionDeal:Payoff=MaxPut`，而 `FourEquityOption` 是常用的 `Trade=FourEquityOptionDeal:Payoff=MaxPut`，这意味着文件 `Payoff_Max.txt` 的内容将在运行时编译，从而创建子类 `GenericEquityOptionMaxPut`，该类派生自抽象基类 `GenericEquityBasketOption`。包含 `GenericEquityOptionMaxPut` 类的 .NET 程序集存储在内存中，并调用其 `Price()` 方法来验证期权。

文件 `PayoffMaxPut.txt` 包含以下 C# 代码：

```cs
using System;
namespace ComputationalLib
{
    public class GenericEquityOptionMaxPut : GenericEquityOptionOption
    {
        public override string Name()
        {
            string temp_string = "";
            temp_string = "Generic option: Put on maximum " + n_.ToString() + " assets";
            return temp_string;
        }

        public override double Payoff() // 实现 max, put
        {
            double the_max = 0.0;
            double pay_val = 0.0;
            double zero = 0.0;
            for (int j = 0; j < n_; j++)
            {
                if (ST_[j] > the_max)
                    the_max = ST_[j];
            }
            pay_val = Math.Max(Strike - the_max, zero);

            return pay_val;
        }
    }
}
```

在上述代码中 `ST_`、`Strike_` 和 `n_` 是 `GenericEquityBasketOption` 类的成员。我们现在展示投资组合文件的其他条目，以说明 `GenericEquityBasketOption` 类的功能性。

- 4 种资产的平均看涨期权：
Trade=GenericEquityBasketOptionPayoff=AvgCall, Reference=5, Strike=100.0, Volatility=0.2, 0.24, 0.2, 0.24, Equities=Drinks-4, H-Ltd, Wines-Ltd, NumberOfUnits=100, Time_Expiry=1.0, NumberScenarios=100

- 10 种资产的平均看跌期权：
Trade=GenericEquityBasketOptionPayoff=AvgPut, Reference=9, Strike=99, Volatility=0.2, 0.24, 0.2, 0.24, Equities=Drinks, Beverage-Ltd, H-Ltd, Wines-Ltd, NumberOfUnits=100, Time_Expiry=1.0, NumberScenarios=100

### C# 投资组合应用

```cs
int is_fcall = 1;
PricingUtils.multivariate_normal(is_fcall, ref MEANS[0], C, n_, tol, rvec[0], Z[0], iflag);

is_fcall = 0;
for (int i = 1; i <= NumberScenarios; i++) {
    PricingUtils.multivariate_normal(is_fcall, ref MEANS[0], C, n_, tol, rvec[0], Z[0], iflag);
    for (int j = 0; j < n_; j++) {
        ST_[j] = S_[j] * Math.Exp(Z[j]);
    }
    sum_val += Payoff();
}
opt_val = sum_val * disc / (double)NumberScenarios;
return opt_val;
```

`Payoff_AvgPut` 文件的内容可以从 `Payoff_AvgCall` 显而易见地推导出。应用程序的输出如下：

| | | |
| :--- | :--- |
| TestEQ 单位为 GBP | |
| TestEQ :31/07/2007 19:05:10 | |
| 23.0101a6 | 4 种资产的最大值看跌期权 |
| 23.0101a18 | 四种股票期权 |
| 681.4035 | 4 种资产的平均看涨期权 |
| 338.32126 | 10 种资产的平均看跌期权 |
| 302.60569 | 10 种资产的平均看跌期权 |
| TOTAL_VAL | 1993.18 GBP |

