
used to forecast and to rank stocks. Self-adjusting to the most recent data, ALAN computes near-term price movement forecasts and generates narrative texts along with associated audios and videos to describe the past trends and explain the forecast results. ALAN generated multimedia outputs are delivered in the audience’s native language. The entire process is automated.

## 119.2 Analysis Gap and Language Barrier

Recent years have seen two major trends in the investment world: greater participation of do-it-yourself (DIY) investors and global investing. While plenty of investors continue to rely on and delegate investment management to professional financial institutions, an increasing number of investors are choosing to manage their funds themselves and making their own investment decisions. As the pace of globalization accelerates, more investors are venturing outside of their own country to search for investment opportunities around the world. These two trends, in turn, create two corresponding obstacles: analysis gap and language barrier.

In the Information Age, there is an overabundance of news and financial information supplied by numerous exchanges and financial portal sites such as IEX, Yahoo, and Google. With the greater availability of data, it is becoming increasingly difficult for DIY investors to extract knowledge from data and to distinguish useful information from noise. Too much information unaccompanied by proper analysis can be an obstacle to making sound investment decisions. Because knowledge and speed contribute to a large portion of trading profits, financial institutions devote resources to develop and profit from all forms of time-sensitive financial analysis. Consequently, DIY investors without the resources needed to conduct such analysis are at a trading disadvantage.

Furthermore, as investors expand their horizon and search for international investment opportunities, they notice frequently that the corresponding financial data and analysis for such opportunities are available only in the language of the issuer’s country. Even when English is used, as is the case for many large issues, it creates problems for non-English speaking investors. To overcome this language barrier, the first remedial action is usually to employ a machine translation tool such as Google Translate. Unfortunately, the current capability of such translation technology is still lacking, and it is not workable for complex topics including finance and investment analysis. Bad, incomplete, or incorrect translation will contribute to errors in decision making and potentially severe negative financial consequences.

## 119.3 Robo-Adviser and Robo-Journalism

For the benefit of DIY investors, robo-advisers such as Wealthfront and Betterment provide professional financial advice online with moderate to minimal human interaction and intervention. These platforms have been gaining the popularity among small retail investors with perceived ease of use and generally lower fees.

Robo-journalism attempts to overcome the language barrier by producing narratives directly in the reader’s native language without the need for translation. Robo-journalism is an example of an application from the AI subfield of natural language generation (NLG) which investigates how to create narratives using algorithms. Real world examples of NLG include baseball game coverage articles from the Associated Press and quarterly corporate earnings reports from Automated Insights.

## 119.4 ALAN: Algorithmic Analyst

ALAN contributes to the DIY investment community by providing professional research and analysis in order to narrow the analysis gap and to the global investor community by communicating directly to international investors in their native languages in order to overcome the language barrier. ALAN expands the NLG field by using a novel hybrid approach to generate narratives in multiple languages simultaneously.

## 119.5 Demystifying ALAN

ALAN is an application that integrates and automates the processes of collecting global financial information, performing statistical analysis, executing machine-learning algorithms, and producing reports in text, audio and video formats in multiple languages on demand. ALAN incorporates techniques from multiple disciplines including finance, statistics, econometrics, machine learning, and natural language generation.

The three main components of ALAN are the Historical Data Collector (HDC), the Algorithmic Robo-Advisor (ARA), and the Robo Market Commentator (RMC) engines.

The Historical Data Collector (HDC) engine continuously collects and updates a wide range of raw financial time series data. It includes global macroeconomic variables, market indices, and individual company level information such as stock quotes, trading volumes, periodic financial reports, and news, along with corresponding industry sector indices data. The engine scrubs the collected raw data for completeness, a step that is crucial and frequently challenging.

![](img/31ee7e6fa5107b22bbf7960ec96106a1_4247_0.png)

Figure 119.1: ALAN architecture workflow.

The Algorithmic Robo-Advisor (ARA) engine processes the collected data and forecasts equity prices, financial ratios and global macroeconomic variables to be used to rank stocks. The ARA engine uses an extension of a multi-factor risk model (MFR) as the foundation for its stock ranking algorithm. It combines traditional econometrical techniques and time-series analysis with AI machine learning methods to calculate four risk factors associated with stock performance and to generate relative rankings for stock trading and portfolio optimization.

The Robo Market Commentator (RMC) engine uses a scripted template-based hybrid NLG system to generate narrative text reports in html and pdf formats first and then produces corresponding multimedia files in mp3 and mp4 formats subsequently.

Figure 119.1 divides ALAN's architecture into three analytical engines: Historical Data Collector (HDC), Algorithmic Robo-Advisor (ARA), and Robo Market Commentator (RMC).

## 119.6 Multi-Factor Risk Model

Multi-factor risk models have been used in finance since the 70s as a variation of the Arbitrage Pricing Theory (APT) model to attempt to explain the historical returns on stocks and bonds. APT seeks to measure various market and macroeconomic factors without identifying them specifically. In 1993, Fama and French published a model containing three factors: an overall market factor, a factor related to firm size, and a factor related to book-to-market equity. Then in 1997, Carhart added an additional momentum factor to make the four-factor model a starting point for many modern models. Quality and low volatility are two other factors frequently added to expand or enhance the models.

Multi-factor risk models are now commonly used in the industry. Mutual fund institutions such as Fidelity and Vanguard use factor-based models to market their ETF products. Asset management firms use factor-based risk models to allocate portfolio holdings and perform return attributions.

ALAN uses a multi-factor risk model as the analytical foundation to measure and rank stock performances. ALAN identifies fundamental quality, fundamental valuation, technical momentum, and global-macro as the four major risk factors.

A company’s fundamental information derived from financial statements, earnings reports, and corporate news is used to gauge its long-term performance which ALAN defines as the fundamental valuation risk factor and its sustainability which ALAN defines as the fundamental quality risk factor. Historical price performance and trading liquidity data are used to measure the short-term market momentum and sentiment which ALAN defines as the technical momentum risk factor. The global-macro risk factor is derived from such market data as interest rates, currencies, commodities and other macroeconomic variables that affect financial markets.

For each of the four risk factors in ALAN’s MFR model, lower level variables are identified as its subfactor attributes. Table 119.1 lists some of the subfactor attributes for each of the four factors.

Many subfactor attributes are directly observed while others must be calculated from the collected and scrubbed financial data. They are forecast using a variety of algorithms from econometrics, time-series analysis, machine learning methods, and other AI techniques. For technical sentiment analysis, ALAN applies text mining algorithms, for example. The resulting subfactor attribute forecasts are used by the MFR. ALAN’s flexibility allows different sets of subfactor attributes to determine the risk factors for different stocks.

**Table 119.1: Factors and their subfactor attributes.**

| Factor | Subfactor attributes |
|---|---|
| Fundamental Valuation | Earnings per share (EPS) |
| Fundamental Quality | Return on equity (ROE), debt equity ratio (D/E) |
| Technical Momentum | Moving average convergence divergence (MACD), relative strength index (RSI) |
| Global-Macro | Yield curve, inflation outlook, volatility |
