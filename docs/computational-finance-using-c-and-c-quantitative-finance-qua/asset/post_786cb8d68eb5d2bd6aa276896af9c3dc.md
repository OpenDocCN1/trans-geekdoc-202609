
# C# portfolio pricing application

// Broad-Investments : Contains equity, FX and IR products

// Example deal Foreign currency = GBP Domestic Currency = USD, Strike = 1.5, Settlement=0.0 years
// The Strike is the number of units of domestic currency that have been agreed to be paid for one unit of foreign currency

```c
Trade+FXForwardDeal,Reference=FX5001, ForeignAmount=100, Strike=1.5, ForeignCurrency=GBP, DomesticCurrency=USD, Settlement=0, BuySell=Buy
Trade+ForwardAgreementDeal,Reference=IR6001, Principal=100.0, Strike=3.0, Currency=GBP, Maturity=4.5, Start=0.4, BuySell=Buy
Trade+OptionDeal,Reference=FX5001, NumberOfUnits=23, Strike=0.5, Volatility=0.1375, ForeignCurrency=USD, DomesticCurrency=GBP, TimeToExpiry=0.2, ExerciseStyle=European, OptionType=Call, BuySell=Buy
Trade+OutOptionDeal,Reference=TECH7001, RealComputers, Volatility=0.2, Strike=100.0, TimeToExpiry=0.1, BarrierLevel=90.0, OptionType=Call, Method=Analytic, NumberScenarios=10000, UseBrownianBridge=true
Trade+OutOptionDeal,Reference=TECH7002, RealComputers, Volatility=0.2, Strike=100.0, TimeToExpiry=0.1, BarrierLevel=90.0, OptionType=Call, Method=MonteCarlo, NumberScenarios=10000
Trade+OutOptionDeal,Reference=TECH7005, RealComputers, Volatility=0.2, Strike=100.0, TimeToExpiry=0.1, BarrierLevel=90.0, OptionType=Call, Method=Analytic
Trade+OutOptionDeal,Reference=TECH7006, RealComputers, Volatility=0.2, Strike=100.0, TimeToExpiry=0.1, BarrierLevel=90.0, OptionType=Call, Method=Numeric
Trade+OutOptionDeal,Reference=TECH7007, RealComputers, Volatility=0.2, Strike=100.0, TimeToExpiry=0.1, BarrierLevel=90.0, OptionType=Call, Method=Numeric, NumberScenarios=10000, UseBrownianBridge=true
Trade+FXOptionDeal,Reference=FX5004, NumberOfUnits=23, Strike=0.5, Volatility=0.1375, ForeignCurrency=USD, DomesticCurrency=GBP, TimeToExpiry=0.5, ExerciseStyle=European, OptionType=Call, BuySell=Buy, Method=MonteCarlo, BarrierLevel=0.01
Trade+FXOptionDeal,Reference=FX5006, NumberOfUnits=23, Strike=0.5, Volatility=0.1375, ForeignCurrency=USD, DomesticCurrency=GBP, TimeToExpiry=0.5, ExerciseStyle=European, OptionType=Call, BuySell=Buy, Method=MonteCarlo, BarrierLevel=0.01
Trade+FXOptionDeal,Reference=FX5008, NumberOfUnits=23, Strike=0.5, Volatility=0.1375, ForeignCurrency=USD, DomesticCurrency=GBP, TimeToExpiry=0.5, ExerciseStyle=European, OptionType=Put, BuySell=Buy, CalcMethod=MonteCarlo, BarrierLevel=0.01, ExerciseStyle=European
```

// American FX Barrier

```c
Trade+FXOptionDeal,Reference=FX5007, NumberOfUnits=23, Strike=0.5, Volatility=0.1375, ForeignCurrency=USD, DomesticCurrency=GBP, TimeToExpiry=0.5, OptionType=Call, BuySell=Buy, CalcMethod=Numeric, BarrierLevel=0.01, ExerciseStyle=American
```

// European Put

```c
Trade+FXOptionDeal,Reference=FX5009, NumberOfUnits=23, Strike=0.5, Volatility=0.1375, ForeignCurrency=USD, DomesticCurrency=GBP, TimeToExpiry=0.5, ExerciseStyle=European, OptionType=Put, BuySell=Buy, CalcMethod=MonteCarlo, BarrierLevel=0.01
```

Exhibit 8.1 We show an example portfolio deal and the individual portfolio files EQ Investments.txt and Broad-Investments.txt. The symbol is used to indicate a line continuation; note the C# requirement each deal to be on a single line.

deal courses, for all foreign derivatives will need access to the current FX rates, and all derivatives will require the current price equity. The contents of the market data can be updated as frequently as required Currency market data. This is for pricing interest rate swaps, FX options, etc...

Currency.USD,FXSpot=0.5565,YieldCurve=[(0.027,0.0184),..., (40.58,0.0533)], Vol=[(0.0,0.1),(1.0,0.1),(3.0,0.13),(6.0,0.14),(20.0,0.15)],
Currency-BaseFXSpot,YieldCurve=[(0.002,0.0147),..., (50.03,0.0542)], Vol=[(0.0,0.10),(1.0,0.1),(3.0,0.13),(6.0,0.14),(20.0,0.15)],
Currency.EUR,FXSpot=0.8904,YieldCurve=[(0.0,0.04),...,(20.0,0.056)], Vol=[(0.0,0.08),(1.0,0.1),(3.0,0.13),(6.0,0.14),(20.0,0.15)],
Currency.CAD,FXSpot=1.51,YieldCurve=[(0.0,0.04),...,(20.0,0.056)], Vol=[(0.0,0.1),(1.0,0.1),(3.0,0.13),(6.0,0.14),(20.0,0.15)]

// Equity market data. This is for pricing equity options, etc...

Equity.Imperial-Art,Currency=GBP,Spot=90.0,DivYield=0.03
Equity.Real-Computers,Currency=USD,Spot=200.0,DivYield=0.04
Equity.Real-Tech,Currency=GBP,Spot=120.0,DivYield=0.09
Equity.Web-Comm,Currency=USD,Spot=100.0,DivYield=0.07
Equity.Hackers,Currency=GBP,Spot=95.0,DivYield=0.05
Equity.Home-Appl,Currency=USD,Spot=100.0,DivYield=0.05
Equity.Smart-Mobile,Currency=GBP,Spot=100.0,DivYield=0.01
Equity.Web-Comm,Currency=GBP,Spot=100.0,DivYield=0.04
Equity.Real-Tech,Currency=GBP,Spot=110.0,DivYield=0.05
Equity.CompAuto,Currency=GBP,Spot=95.0,DivYield=0.11
Equity.The-Booking,Currency=GBP,Spot=100.0,DivYield=0.02
Equity.Mobile-Games,Currency=GBP,Spot=100.0,DivYield=0.03
Equity.Real-Book,Currency=GBP,Spot=100.0,DivYield=0.04
Equity.Drinks,Currency=GBP,Spot=100.0,DivYield=0.05
Equity.Lead-Wire,Currency=GBP,Spot=100.0,DivYield=0.06
Equity.H20-Ltd,Currency=GBP,Spot=100.0,DivYield=0.05
Equity.Fine-Wires,Currency=GBP,Spot=100.0,DivYield=0.03
Equity.Health-Tech,Currency=GBP,Spot=100.0,DivYield=0.2
Equity.English-North,Currency=GBP,Spot=100.0,DivYield=0.03
Equity.Auto-Parts,Currency=GBP,Spot=100.0,DivYield=0.01
Equity.Welsh-Spring,Currency=GBP,Spot=100.0,DivYield=0.06
Equity.Thames-River,Currency=GBP,Spot=100.0,DivYield=0.05
Equity.Edinburgh-Whiskey,Currency=GBP,Spot=100.0,DivYield=0.4
Equity.Wine-Box,Currency=GBP,Spot=100.0,DivYield=0.85

// Bond market data. This is for pricing bonds, and credit swaps as CDS

Bond.Fine-Wines-Ltd-2020,Currency=GBP,Spot=150.0, SurvivalProb=[(0.0,1.0),(1.0,0.9),(3.0,0.9),(6.0,0.9),(20.0,0.5)]
Bond.Hackers-2018,Currency=GBP,Spot=200.0, SurvivalProb=[(0.0,1.0),(1.0,0.9),(2.0,0.95),(8.0,0.8),(20.0,0.6)]
Bond.Hackers-2060,Currency=GBP,Spot=260.0, SurvivalProb=[(0.0,1.0),(1.0,0.32),(20.0,0.8),(25.0,0.65),(60.0,0.7)]
Bond.Computers-2022,Currency=GBP,Spot=100.0, SurvivalProb=[(0.0,1.0),(1.0,0.0),(4.0,0.9),(8.0,0.6),(30.0,0.5)]

// Correlation data. These are used for pricing, 0.5 options

Correlation.Real-Computers,WebComm=0.4
Correlation.Real-Computers,Hackers=0.5
Correlation.Real-Computers,LaserComm=0.3
Correlation.Real-Computers,SmartWeb=0.4
Correlation.TeComm,Hackers=0.5
Correlation.TeComm,LaserComm=0.5
Correlation.TeComm,SmartWeb=0.5
Correlation.TeComm,WebComm=0.5
Correlation.Hackers,Mobile-Tech=0.4
Correlation.LaserComm,Mobile-Tech=0.4
Correlation.SmartWeb,Mobile-Tech=0.5
Correlation.WebComm,Mobile-Tech=0.5

Exhibit 8.2 An example market file, which is used to specify the current market values as equity, spot, interest rate curves, etc. The third line in the file provides currency for GBP and the other currency. Base specifies that the base currency will be GBP, and all portfolio values will be computed in GBP.

# C# fortune pricing application

Correlation.Mobile-Tech,The-Bookshop=0.1
Correlation.Kalyc,Laser=0.3

Correlation.ThamesBeer,French-Wines-Ltd=0.3
Correlation.ThamesBeer,Fine-Wines-Ltd=0.5
Correlation.ThamesBeer,H2O-Ltd=0.5
Correlation.ThamesBeer,Beverage-Ltd=0.6
Correlation.ThamesBeer,Ditch=0.6
Correlation.ThamesBeer,The-Real-Book-Company=0.8
Correlation.ThamesBeer,People-Books=0.1

Correlation.Edinburgh-Whisky,French-Wines-Ltd=0.5
Correlation.Edinburgh-Whisky,Water-Works-Ltd=0.5
Correlation.Edinburgh-Whisky,The-English-Beer-Company=0.6

Exhibit 2. daily, hourly, etc) (i.e., daily, hourly, etc) which will always maintain a set of market values that can be used consistently across all dealings.

It should be noted that the main advantage of type E1 deal entries is not just that the portfolio definition is smaller—it also ensures consistent market data values are used to price all the trades in the portfolio. When E2 deal entries are used, it is necessary to ensure that all the extra deals are attributed as new market data becomes available. This would be a time-consuming task, and if only a partial update occurs, could give rise to invalid deals caused by inconsistent deal attributes such as FXCurrency, DividendYield.

The format of the result is shown in Exhibit 8.3. The output syntax is simply:

```
<value>=<reference>, <type>
```

It can be seen that each deal is valued in base currency (which is the market data file as GBP) and the total value for the portfolio is reported.

# Results for portfolio EQ-investments
===========================
EQ-Investments in units of GBP
===========================

```
43501-EQ:Laser-1001, Equity Option
9278-EQ:Correlation-1002, Equity Option
5716-EQ:Correlation-1003, Equity Option
2024-EQ:Correlation-1004, Equity Option
2027-EQ:MobileTech-1004, Equity Option
41719-EQ:Kulpac-105, Rainbow option (two equities)
14024-EQ:MobileTech-Impacul-106, Rainbow option (two equities)
8651-EQ:MobileTech-1007, Rainbow option (two equities)
70315-EQ:Telcom-1008, Rainbow option (two equities)
```
