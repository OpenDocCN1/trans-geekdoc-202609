
# Chapter 8

## C# Portfolio Pricing Application

## 8.1 INTRODUCTION

This section provides details concerning a C# portfolio valuation application. It has been included to illustrate how the pricing functions discussed in the previous sections of the book can be incorporated into the kind of software that may be found in a bank, financial institution, or educational establishment.

Here, we provide code excerpts from the application; however, additional source is available from the publisher's website.
The main features of this application are as follows:

- User-defined portfolios of deals can be valued without the need to compile C++ or C# programs. This means that the application is easy to use and is accessible to those who may possess business or financial knowledge but do not have the technical skills required to write computer code.
- This application only deals with equity, foreign exchange derivatives — the exception is the inclusion of an interest rate forward rate. However, the software can be easily extended to include new deal types.
- All input/output to the application is by main of text files which can be easily edited.
- The software is modular and consists of a main C# program which calls both a compiled C# DealLibrary and also a compiled library GeorgeLevy_ComputationalFinance_UtilsLibrary. The reader also has the choice of using a simpler C# project called DealValuer; this does not use text input and also is independent of GeorgeLevy_ComputationalFinance_UtilsLibrary.

We will provide a brief overview of each component of the application, more detail will be given when specific class is described.

## The C# Code

The application is defined by the C# solution PortfolioValuer.sln, which contains the projects DealLibrary.csproj and PortfolioValuer.csproj.
The project PortfolioValuer.csproj is the driver for the application, see Code excerpt 8.2. The user interface is a simply window with a button to start the application, and if required this could easily customized by the reader. Once the application has been started, it first loads a market data file and reads a portfolio configuration file to determine which portfolios are to be valued. Valuation proceeds for all the deals contained in the portfolio files and the results are written to the appropriate portfolio results' file.

The project DealLibrary.csproj is concerned with the valuation of the results and the available trades in the application. A separate C# deal, derived from a single abstract class BaseDeal, is provided for each trade type. The BaseDeal class provides methods such as Price() and Validate(), which need to be implemented in derived classes. We will be primarily concerned with the method Price(), which is used to return the current value of a trade.

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

**Code excerpt 8.1** C# code showing the declaration of class BaseDeal and illustrating the implementation of Price(), Validate(), and Name().

Code excerpt 8.1 provides the declaration of BaseDeal and illustrates how the deal EquityOptionDeal implements the necessary methods; the complete C# code for a range of deals is provided later.

It can be seen that the deal also needs to specify the attributes which will be present to the user and in addition access method such as equity.

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

**Code excerpt 8.2** The main driver for the C# portfolio value application. After reading the market data file, it processes the trades contained in the portfolio definition files. The total value of each portfolio is output.
