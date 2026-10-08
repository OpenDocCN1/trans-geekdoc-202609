

# 254

# 使用 C 和 C# 进行计算金融

| 2838.964-Tech-1007 | 三权股票期权 |
| 2838.964-Tech-1008 | 通用股票期权 |
| 399.481-Tech-1009 | 三权股票期权 |
| 409.125-Tech-1001 | 三权股票期权 |
| 6647.263-Drinks-2001 | 四权股票期权 |
| 2644.362-Drinks-2002 | 四权股票期权 |
| 1523.518-Drinks-2003 | 四权股票期权 |
| 21.869-Drinks-2004 | 四权股票期权 |
| 53.810-Drinks-2005 | 五权股票期权 |
| 63.286-Drinks-2006 | 四权股票期权 |
| 1511.643-Drinks-2007 | 四权股票期权 |
| 1524.500-Drinks-2008 | 四权股票期权 |
| 1530.758-Drinks-2009 | 四权股票期权 |
| 1518.867-Drinks-2010 | 四权股票期权 |
| 1531.758-Drinks-2011 | 四权股票期权 |
| 1524.500-Drinks-2012 | 通用股票期权 |
| 1513.758-Drinks-2013 | 通用股票期权 |
| 2024.000-Drinks-2014 | 通用股票期权 |
| 6.128=JFCA, 111 | 突破股票期权 |
| 6.124=JFCA, 112 | 突破股票期权 |
| 3.006=JFCA, 112 | 突破股票期权 |
| 3.006=JFCA, 113 | 突破股票期权 |
| 3.006=JFCA, 114 | 突破股票期权 |
| 3.006=JFCA, 115 | 敲出看涨股票期权 |

=============================================
总价值 = 2987.53 GBP
=============================================

# 投资组合广泛投资的结果文件

=============================================
以英镑为单位的广泛投资
广泛投资 = 14/07/2007 00:00:00
=============================================
| 9.4359=FX-5001 | 外汇远期 |
| 9.4159=FX-5002 | 外汇远期 |
| 0.8661=IR-6002 | 远期利率协议 |
| 1.1755=Tech-7001 | 突破股票期权 |
| 52.6353=Tech-7002 | 突破股票期权 |
| 52.6753=Tech-7003 | 突破股票期权 |
| 52.6538=Tech-7004 | 突破股票期权 |
| 52.6353=Tech-7005 | 突破股票期权 |
| 52.6358=Tech-7006 | 突破股票期权 |
| 52.6505=Tech-7007 | 突破股票期权 |
| 11.6849=FX-5003 | 突破外汇期权 |
| 11.6849=FX-5004 | 突破外汇期权 |
| 11.6811=FX-5005 | 突破外汇期权 |
| 11.5356=FX-5006 | 突破外汇期权 |
| 11.9989=FX-5007 | 突破外汇期权 |
| 2.1973=FX-5008 | 突破外汇期权 |
| 2.9827=FX-5009 | 突破外汇期权 |

=============================================
总价值 = 448.09 GBP
=============================================

8.3 投资组合结果文件。报告货币在市场数据文件中设置；在本示例中，所有值均以英镑给出。

# 8.2 存储和检索市场数据

如前所述，在推导衍生品之前，市场数据存储在市场数据字典（Dictionaries）中。代码片段 8.4 所示的 MarketDataDictionaries 类包含一组 C# Dictionary 成员项，这些项持有交易类所需的所有市场数据。下面给出了 `CurrencyTable`、`EquityTable` 和 `CorrelationTable` 字典的声明：

```csharp
public static Dictionary<string, Currency> CurrencyTable = new Dictionary<string, Currency>();
public static Dictionary<string, Equity> EquityTable = new Dictionary<string, Equity>();
public static Dictionary<string, Correlation> CorrelationTable = new Dictionary<string, Correlation>();
```

每个字典由 `<unique-key, <value-object>` 对组成，其中 `unique-key` 是一个唯一字符串，而 `value-object` 是一个包含对应市场数据的类。我们现在更详细地考虑上述每个字典及其包含的信息。

## 8.2.1 CurrencyTable

在 `CurrencyTable` 字典中，值对象是一个类型为 `Currency` 的类，用于存储货币信息。该类的声明在代码片段 8.3 所示。

```csharp
public class TPair : IComparable
{
    public double t;
    public double val;

    public TPair(double t1, double val1)
    {
        t = t1;
        val = val1;
    }

    int CompareTo(object obj)
    {
        TPair temp = (TPair)obj;
        if (this.t > temp.t)
            return (1);
        if (this.t < temp.t)
            return (-1);
        else
            return (0);
    }
}

// ICurve - 用于存储利率的曲线
public class ICurve : List<TPair>
{
    private double t_pt; // 用于匹配的内部值
    private string name = "";

    public ICurve(string name) {
        name = name;
    }

    public double this[double t_0, double t1]
    { // 返回 t 和 t1 之间的折现因子
        double eps = 1e-6;
        double val = 0;
        // ... (省略实现逻辑)
    }
}
```

