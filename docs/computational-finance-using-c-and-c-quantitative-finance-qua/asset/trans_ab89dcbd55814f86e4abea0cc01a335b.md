

# C# 投资组合定价应用程序

```csharp
namespace PortfolioValuer
{
    public partial class Form1 : Form
    {
        public Form()
        {
            InitializeComponent();
        }
        private void button_Click(object sender, EventArgs e)
        {
            StreamReader sr_config;
            StreamReader sr_tests;
            StreamWriter sw;

            MessageBox.Show("Computing value of portfolios");
            string append = App.GetDirectoryName(Application.ExecutablePath);
            string configfile = append + "\\Portfolios.txt";
            string filename = append + "\\MarketData.txt";
            try
            {
                BaseDeal.LoadMarketData(filename);
                // Execute the specified tests
                sr_config = new StreamReader(configfile);
                string assembly = append + "\\Library.dll";
                Assembly Ass = Assembly.Load(assembly);
                Type[] LoadedTypes = Ass.GetTypes();
                string test_file;
                int block_count = 0;
                double port_val = 0.0;
                string BaseCurrency = BaseDeal.GetBaseCurrency();
                while (test_file = sr_config.ReadLine() != null)
                {
                    sr_tests = new StreamReader(test_file + ".txt");
                    string current_test;
                    string date = DateTime.Now.ToString();
                    string filename = append + "\\" + test_file + "\\Results.txt";
                    bool append = false;
                    sw = new StreamWriter(filename, append, Encoding.ASCII);
                    sw.WriteLine(test_file + " * in units of " + BaseCurrency);
                    sw.WriteLine(test_file + " * " + (date));
                    sw.WriteLine("=====================================");
                    port_val = 0.0;
                    int block_count = 0;
                    while ((current_test = sr_tests.ReadLine()) != null)
                    {
                        block_count = (current_test.Length > 1) ? 
                        (current_test.Substring(0, 2) == "===") ? 1 : 0; 
                        {
                            try
                            {
                                deal_val = deal_value; // return the value of the deal
                                acl.Price.Close();
                            }
                            catch (Exception ex)
                            {
                                sr_config.Close();
                                sw.Close();
                                sr_tests.Close();
                                throw new Exception(ex.Message);
                            }

                            port_val += deal_value; // add to the portfolio
                            string str_data = deal_value.ToString("0.0000;-0.0000;0.0000*");
                            sw.WriteLine(str_data + " *" + acl.Reference + ".*" + acl.Name() + ");
                        }
                    }
                } // end of tests for a given portfolio
            }
}
```

代码示例 8.1 C# 投资组合价值应用程序的主驱动程序。在读取市场数据文件后，它对投资组合定义文件中的交易进行定价。还会计算每个投资组合的总价值。

# 使用 C 和 C# 进行计算金融



```csharp
public abstract class BaseDeal // BaseDeal 的声明
{
    public abstract String Name();

    public abstract double Price();
    protected abstract void Validate();
    public string Reference { get { return Reference_; } set { Reference_ = value; }

    protected string Reference_;

    public string BaseCurrency { get { return MarketDataDictionaries.BaseCurrency(); } }
}

public class EquityOptionDeal : BaseDeal // EquityOptionDeal 的声明
{
    public string EquityName { get { return EquityName_; } set { EquityName_ = value; }
    public int NumberOfUnits { get { return NumberOfUnits_; } set { NumberOfUnits_ = value; }
    public double Time_Expiry { get { return Time_Expiry_; } set { Time_Expiry_ = value; }

    public override String Name() // 实现 Name() 方法
    {
        return "Equity Option";
    }

    public override double Price() // 实现 Price() 方法
    {
        Validate();

        double val=0.0;
        double[] Greeks = new double[6];
        double s0 = 0.0;
        double fx_spot = 0.0;
        try {
            s0 = MarketDataDictionaries.EquityTable[EquityName_].Spot; // 当前股票价格
            Currency_ = MarketDataDictionaries.EquityTable[EquityName_].Currency_;
            DividendYield_ = MarketDataDictionaries.EquityTable[EquityName_].DivYield_;
        } catch {
            throw new Exception(Pre_string_ + "--- No Market data supply for * " + EquityName_);
        }

        val *= fx_spot * NumberOfUnits_; // 返回基础货币的价值
        return val;
    }

    protected override void Validate() // 实现 Validate() 方法
    {
        Pre_string_ = Name() + " * (" + Reference_ + ");");
        if (Time_Expiry_ < 0.0) {
            throw new Exception(Pre_string_ + "--- Time to expiry cannot be less than zero years*");
        }
        if (Strike_ < 0.0) {
            throw new Exception(Pre_string_ + "--- The strike cannot be less than zero*");
        }
    }
}
```

节选 8.2 显示了 BaseDeal 类的声明，并说明了 `Price()`、`Validate()` 和 `Name()` 方法实现的 C# 代码。

# C# 投资组合定价应用程序

```csharp
// 写投资组合价值
sw.WriteLine("=============================");
string str_port_val = port_val.ToString("0.0000;-0.0000;0.00");
sw.WriteLine("TOTAL VALUE = " + str_port_val + " " + BaseCurrency + " ");
```

代码示例 8.2 (续)。股票期权。其他交易属性是 `DealClass` 的公共属性，可以任意排列。交易定价通过首先构建 `DealClass` 实例来实现。该对象被填充了所需的交易数据，`Price()` 方法检索市场数据，计算价值，并将其返回给应用程序输出到投资组合结果文件。引用（或字母数字代码）用于标识，例如 `Reference=EQ:LaserComm-1001` 或 `Reference=Tech-1008_Generic`。投资组合结果包含了每个已估值交易的价值和引用。

# 投资组合驱动程序

# 投资组合定义文件：EQ-investments

```text
// EQ-Investments : 包含股票
=========================================
Trade=EquityOptionDeal,Reference=EQ:LaserComm-1001,Equity=LaserComm,Volatility=0.1,
Strike=95.0,Time_To_Expiry=1.0,OptionType=Put,ExerciseStyle=European

Trade=EquityOptionDeal,Reference=EQ:WebComm-1004,Equity=WebComm,Volatility=0.1,
Strike=95.0,Time_To_Expiry=1.0,OptionType=Call,ExerciseStyle=European

Trade=EquityOptionDeal,Reference=EQ:LaserComm-1004,Equity=LaserComm,Volatility=0.1,
Strike=95.0,Time_To_Expiry=1.0,OptionType=Call,ExerciseStyle=European
```

```text
Trade=EquityOptionDeal,Reference=EQ:Investments-1005,Equity=Mobile,
Strike=95.0,Time_To_Expiry=1.0,OptionType=Put,ExerciseStyle=American
```

```text
Trade=EquityOptionDeal,Reference=EQ:Investments-1006,Equity=Tech,
Strike=95.0,Time_To_Expiry=1.0,OptionType=Call,ExerciseStyle=European
```

```text
Trade=EquityOptionDeal,Reference=EQ:Lasecom-1006,Equity=Telecom,Volatility=0.1,
```

```text
Trade=EquityOptionDeal,Reference=EQ:Lasecom-1007,Equity=SmartWeb,Volatility=0.1,
Strike=95.0,Time_To_Expiry=1.0,OptionType=Call,ExerciseStyle=European
```

```text
Trade=EquityOptionDeal,Reference=EQ:Generic-1008,Equity=Asset,Volatility=0.1,
Strike=95.0,Time_To_Expiry=1.0,OptionType=Put,ExerciseStyle=European
```

```text
Trade=EquityOptionDeal,Reference=EQ:Generic-1009,Equity=Lasecom,Volatility=0.1,
Strike=95.0,Time_To_Expiry=1.0,OptionType=Call,ExerciseStyle=European
```

```text
Trade=EquityOptionDeal,Reference=EQ:Generic-1010,Equity=Generic,Volatility=0.1,
Strike=95.0,Time_To_Expiry=1.0,OptionType=Put,ExerciseStyle=European
```

```text
Trade=EquityOptionDeal,Reference=EQ:Generic-1011,Equity=Barrier,Volatility=0.1,
Strike=95.0,Time_To_Expiry=1.0,OptionType=Call,ExerciseStyle=European
```

```text
Trade=EquityOptionDeal,Reference=EQ:Generic-1012,Equity=Barrier,Volatility=0.1,
Strike=95.0,Time_To_Expiry=1.0,OptionType=Put,ExerciseStyle=European
```

```text
Trade=EquityOptionDeal,Reference=EQ:Generic-1013,Equity=Barrier,Volatility=0.1,
Strike=95.0,Time_To_Expiry=1.0,OptionType=Call,ExerciseStyle=European
```

# 投资组合定义文件：broad-investments

在本书前期开发的衍生品定价函数中，资产价格、无风险利率等所有信息都是显式传递给定价函数的。

例如，我们考虑 `EquityOption` 的价格，`Reference=EQ:WebComm-1004`，如图 8.1 所示。我们在投资组合文件 `EQ-investments` 中将其简称为 `E1`：

```text
Trade=EquityOptionDeal,Reference=EQ:WebComm-1004,Equity=WebComm,Volatility=0.1,
Strike=95.0,Time_To_Expiry=1.0,OptionType=Call,ExerciseStyle=European
```

稍后底层函数中包含波动率的原因。

如果我们显式地放置底层函数 `block_scholes` 需要的所有信息，那么所需条目（称为 `E_2`）的格式将是：

```text
Trade=EquityOptionDeal,Reference=EQ:WebComm-1004,Equity=WebComm,Volatility=0.1,
Strike=95.0,Time_To_Expiry=1.0,OptionType=Put,ExerciseStyle=European,EquitySpot=100,
FXCurrency=0.5565,RiskFreeRate=0.1,DividendYield=0.05
```

市场数据字典在应用程序启动后立即填充。
图 2 显示了一个市场数据文件示例。这是一个纯文本文件，为所需的市场参数提供了一个公共存储库。

