

# C# 投资组合定价应用程序

声明 `ICleave` 对象 `DF`。然后通过该语句计算 0 到 `Time_To_Expiry` 之间的贴因子：

```csharp
double discount_fac = DF[0, Time_To_Expiry_];
```

其中 `DF[0, Time_To_Expiry_]` 调用了 `ICleave` 访问器（声明为 `public double this[double t_0, double t1]`），且 `t_0 = 0`，`t = Time_To_Expiry`。从代码段 8.3 可以看出，所需的访问器获取线性插值。远利率以类似的方式获取：

```csharp
ICurve FWD = MarketDataDictionaries.CurrencyTable[Currency_].YieldCurve;
```

声明 `ICleave` 对象 `FWD`。然后通过语句返回远利率 $F(0, t1, t2)$：

```csharp
double forward_rate = FWD[0, 0.5, 1.5];
```

其中 `FWD[0, t1, t2]` 调用了 `ICleave` 访问器（声明为 `public double this[double t, double t1, double t2]`），且 `t = 0`，`t1=0.5` 且 `t2 = 1.5`。从代码段 8.3 可以看出，访问器计算了远利率：

```csharp
FWD[0,t1,t2] = (DF[0,t1] / DF[0,t2] - 1.0) / (t2 - t1);
```

# EquityTable 和 CorrelationTable

代码段 8.7 展示了如何将市场数据添加到 `MarketDataDictionaries` 类的内部字典中。例如，添加相关性

```csharp
public class MarketDataDictionaries
{
    public static Dictionary<string, Currency> CurrencyTable = new Dictionary<string, Currency>;
    public static Dictionary<string, Equity> EquityTable = new Dictionary<string, Equity>;
    public static Dictionary<string, Correlation> CorrelationTable = new Dictionary<string, Correlation>;
    protected static string BaseCurrency = "*";

    public static string GetBaseCurrency()
    {
        return BaseCurrency_;
    }

    public static void LoadMarketData(string marketdata_file)
    {
        // 加载数据文件并为字典赋值
        StreamReader FILE = new StreamReader(marketdata_file);
        string cur_line = "*";

        while ((cur_line = FILE.ReadLine()) != null) // 遍历市场数据
        {
        }
    }
}
```

代码段 8.7 `MarketDataDictionaries` 类，插图了如何将市场数据添加到内部。

```csharp
if ((cur_line.Length > 1) && ((cur_line.Substring(0, 2) != "//")))
{
  char[] seps = new char[] {' ', ','};
  string[] v = cur_line.Split(seps, StringSplitOptions.None);

  int num_elems = v.GetUpperBound(0);
  int k = 0;
  double t_, val_;
  bool stop;
  double FXSpot = 0.0;
  if (v[0].Substring(0, 8) == "Currency") // 货币数据
  {
    string CcyCode = v[0].Substring(0, 3);
    if (v[0].IndexOf("--Base") != -1) BaseCurrency_ = CcyCode;
    k += 2;
    if (!CurrencyTable.ContainsKey(CcyCode))
    {
      CurrencyTable.Add(CcyCode, CcyCode);
    }
    else
    {
      throw new Exception("Spot & interest rate market data unavailable for " + CcyCode);
    }
    FXSpot = (double)Convert.ChangeType(v[k], typeof(double));
    CurrencyTable[v[k]].spot = FXSpot;
    CurrencyTable[v[k]].name = CcyCode;
    k += 2;
    t_ = (double)Convert.ChangeType(v[k].Substring(2, v[k].Length - 2), typeof(double));
    k += 1;
    val_ = (double)Convert.ChangeType(v[k].Substring(0, v[k].Length - 1), typeof(double));
    CurrencyTable[v[k]].YieldCurve.Add(new TPair(t_, val_));
    k += 1;
    int vv = v[k].IndexOf("*");
    stop = false;
    while (!stop)
    {
      t_ = (double)Convert.ChangeType(v[k].Substring(1, v[k].Length - 1), typeof(double));
      k += 1;
      if (v[k].IndexOf("*") == -1)
      {
        val_ = (double)Convert.ChangeType(v[k].Substring(0, v[k].Length - 1), typeof(double));
      }
      else
      {
        val_ = (double)Convert.ChangeType(v[k].Substring(0, 2), typeof(double));
        stop = true;
      }
      k += 1;
      CurrencyTable[CcyCode].YieldCurve.Add(new TPair(t_, val_));
    }
    CurrencyTable[CcyCode].YieldCurve.Sort();
  }
  else if (v[0].Substring(0, 6) == "Equity") // 股票数据
  {
    int idx = v[k].IndexOf(".*");
    string EquityName = v[0].Substring(idx + 1, v[k].Length - 2);
    k += 2;
    string CcyCode = v[k];
```

代码段 8.7 续。

```csharp
  k += 2;
  double spot = (double)Convert.ChangeType(v[k], typeof(double));
  k += 2;
  double div = (double)Convert.ChangeType(v[k], typeof(double));
  if (EquityTable.ContainsKey(EquityName))
  {
    EquityTable.Add(EquityName, new Equity());
    EquityTable[EquityName].Currency = CcyCode;
    EquityTable[EquityName].Name = EquityName;
    EquityTable[EquityName].Spot = spot;
    EquityTable[EquityName].Div = div;
  }
  else
  {
    throw new Exception("Spot & currency market data already supplied for " + EquityName);
  }
  else if (v[0].Length >= 12 && v[0].Substring(0, 11) == "Correlation")
    // 相关数据
  {
    int idx = v[0].IndexOf(".*");
    string AssetName1 = v[0].Substring(idx + 1, v[0].Length - idx - 1);
    string AssetName2 = v[k];
    k += 1;
    double corr = (double)Convert.ChangeType(v[k], typeof(double));
    string correlationKey = AssetName1 + "*" + AssetName2;
    if(!CorrelationTable.ContainsKey(correlationKey))
    {
        CorrelationTable.Add(correlationKey, new Correlation());
    }
    CorrelationTable[correlationKey].Corr = corr;
    CorrelationTable[correlationKey].Name = AssetName1;
    CorrelationTable[correlationKey].Name2 = AssetName2;
  }
  string correlationKey = AssetName2 + "*" + AssetName2;
  if(!CorrelationTable.ContainsKey(correlationKey))
  {
      CorrelationTable.Add(correlationKey, new Correlation());
  }
  CorrelationTable[correlationKey].Corr = corr;
  CorrelationTable[correlationKey].Name = AssetName1;
  CorrelationTable[correlationKey].Name2 = AssetName2;
  // 注意: OCR 的逻辑在此处有一些重复/错误, 
  // 但保留了提供的结构。
}
```

