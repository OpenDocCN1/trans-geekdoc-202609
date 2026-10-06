

# 第 8 章

## C# 投资组合定价应用程序

## 8.1 引言

本节详细介绍一个 C# 投资组合估值应用程序。包含此部分的目的是为了说明书中之前章节中讨论的定价函数如何整合到银行、金融机构或教育机构常见的软件中。

在这里，我们提供了应用程序的代码片段；然而，额外的源代码可以在出版者网站获取。
该应用程序的主要功能如下：

- 用户可以定义的交易组合进行估值，无需编译 C++ 或 C# 程序。这意味着该应用程序易于使用，并且那些具备业务或金融知识但缺乏编写计算机代码所需的技术技能的人可以使用。
- 此应用程序仅处理股票和外汇衍生品——例外是包含了利率远期利率。然而，软件可以轻松扩展以包含新的交易类型。
- 应用程序的所有输入/输出均通过文本文件进行，可以方便编辑。
- 软件是模块化的，由一个主 C# 程序组成，该程序同时调用了编译后的 C# `DealLibrary` 和编译后的库 `GeorgeLevy_ComputationalFinance_UtilsLibrary`。读者也可以选择使用一个名为 `DealValuer` 的较简单的 C# 项目；该项目不使用文本输入，并且独立于 `GeorgeLevy_ComputationalFinance_UtilsLibrary`。

我们将对应用程序的每个组件提供概要概述，在描述特定类时将提供更详细的信息。

## C# 代码

应用程序由 C# 解决方案 `PortfolioValuer.sln` 定义，其中包含 `DealLibrary.csproj` 和 `PortfolioValuer.csproj` 项目。
`PortfolioValuer.csproj` 项目是应用程序的驱动器，参见代码片段 8.2。用户界面是一个带有启动应用程序按钮的简单窗口，如果需要，读者可以对其进行自定义。应用程序启动后，它首先加载市场数据文件并读取投资组合配置文件，以确定对哪些投资组合进行估值。对投资组合文件中包含的所有交易进行估值，并将结果写入相应的投资组合结果文件中。

`DealLibrary.csproj` 项目涉及应用程序中结果的估值和可用交易。每种交易类型都提供了一个派自单一抽象类 `BaseDeal` 的独立 C# 交易。`BaseDeal` 类提供了诸如 `Price()` 和 `Validate()` 等方法，这些方法需要在派生类中实现。我们将主要关注 `Price()` 方法，它用于返回交易的当前值。

```csharp
public abstract class BaseDeal
    // The declaration for BaseDeal
    public abstract string Name();
    public abstract double Price();
    protected abstract void Validate();
    public string Reference_ { get { return Reference_; set { Reference_ = value; } }
    protected string Reference_;
    public string BaseCurrency(get { return MarketDataDictionaries.GetBaseCurrency()); }
}

public class OptionDeal: BaseDeal
    // The declaration for OptionDeal
    public string EquityName_ { get { return EquityName_; set { EquityName_ = value; } }
    public int NumberUnits_ { get { return NumberUnits_; set { NumberUnits_ = value; } }
    public double Time_Expiry_ { get { return Time_Expiry_; set { Time_Expiry_ = value; } }
```

```csharp
public override string Name() // implement method Name()
{
    return "Option";
}

public override double Price() // implement method Price()
{
    Validate();
    double[] greeks = new double[6];
    double s = 0.0;
    double fx_spot = 0.0;
    try {
        fx_spot = MarketDataDictionaries.EquityTable[EquityName_].Spot; // get current equity price
        Currency_ = MarketDataDictionaries.EquityTable[EquityName_].Currency; // get equity volatility (assumed constant)
        Dividend_ = MarketDataDictionaries.EquityTable[EquityName_].DivYield; // get equity dividend yield
    } catch {
        throw new Exception("No Market Data supplied for " + EquityName_);
    }
    double val = fx_spot * NumberUnits_; // return value in base currency
    return val;
}

protected override void Validate() // implement method Validate()
{
    string Pre_string_ = Name() + " ( " + Reference_ + ";";
    if (Time_Expiry_ < 0.0) {
        throw new Exception(Pre_string_ + " ---- to expiry cannot be less than zero years");
    }
    if (Strike_ < 0.0) {
        throw new Exception(Pre_string_ + " ---- The strike cannot be less than zero");
    }
}
```

**代码片段 8.1** 显示 `BaseDeal` 类定义的 C# 代码，并说明了 `Price()`、`Validate()` 和 `Name()` 的实现。

代码片段 8.1 提供了 `BaseDeal` 的定义，并说明了交易 `EquityOptionDeal` 如何实现必要的方法；一系列交易的完整 C# 代码将在稍后提供。

可以看出，交易还需要指定将呈现给用户的属性，以及额外的访问方法（如股票）。

```csharp
namespace PortfolioValue
{
    public partial class Form : Form
    {
        public Form()
        {
            InitializeComponent();
        }
        private void button1_Click(object sender, EventArgs e)
        {
            StreamReader sr_config;
            StreamReader sr_tests;
            StreamWriter sw;

            MessageBox.Show("Value of portfolio: " + val.ToString());
            string AppPath = Path.GetDirectoryName(Application.ExecutablePath);
            string config_filename = AppPath + "\\config.txt";
            string test_filename = AppPath + "\\MarketData.txt";
            try {
                BaseDeal.MarketData(MDData);
                // Load and execute the specified;
                sr_config = new StreamReader(config_filename);
                string assembly_name = AppPath + "\\DataLibrary.dll";
                Assembly asm = Assembly.Load(assembly_name);
                Type[] Types = asm.GetTypes();
                string test_file;
                int block_count = 0;
                double port_val = 0;
                string currency_Base = BaseDeal.GetCurrency();
                while ((test_file = sr_config.ReadLine()) != null) {
                    sr_tests = new StreamReader(test_file + ".txt");
                    string current_test;
                    DateTime Date = DateTime.Now.ToString("yyyy-MM-dd");
                    string result = AppPath + "\\" + test_file + "\\results.txt";
                    sw = new StreamWriter(result, false, Encoding.ASCII);
                    sw.WriteLine("==========================");
                    while ((current_test = sr_tests.ReadLine()) != null) {
                        sw.WriteLine(test_file + " = " + units + " " + currency_Base);
                        sw.WriteLine("==========================");
                        port_val = 0;
                        block_count++;
                        if ((current_test.length > 1) && (current_test.Substring(0, 2) == "==") 1; 0;
                        block_count--; if (current_test.length > 2) && (current_test.Substring(0, 2) == "//") 1; 0;
                        try {
                            deal_value = acl.Price(); // return the value of the deal
                        } catch (Exception Exception) {
                            sr_config.Close();
                            sw.Close();
                            sr_tests.Close();
                            throw new Exception(Exception.Message);
                        }
                        port_val += deal_value; // add the value to the portfolio
                    }
                    string str_deal_val = deal_val.ToString("0.0000; 0.0000; 0.0000");
                    sw.WriteLine(str_deal_val + " = " + acl.Reference + "," + acl.Name());
                }
                // // end of tests for a given portfolio
                // write the portfolio value
                sw.WriteLine("==========================");
                string str_port_val = port_val.ToString("0.00; 0.00; 0.00");
            }
            }
        }
    }
}
```

**代码片段 8.2** C# 投资组合估值应用程序的主驱动器。在读取市场数据文件后，它会处理投资组合定义文件中包含的交易。每个投资组合的总值将输出输出。

