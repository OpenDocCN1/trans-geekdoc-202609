
# Preface

machine learning algorithms and numerical methods in the form of stand-alone functions, we believe the reader will get an opportunity to appreciate the nuances of each algorithm, and at the same time, acquire, improve and enhance their programming skills. In this sense, we believe the reader can not only utilise the provided code in their every day, but also expand on it.

The objective of this book is to provide educational material, to encourage readers to code on their own and learn the principles of machine learning and q through implementation and interactively running and building the code while illustrating the concept. We have chosen a slight bias towards clarity of code rather than building a fully optimised production system, which should enable someone new to q to follow the code flow and appreciate the main concepts of both the algorithm and the language itself.

We encourage readers to play – we use the word "play" rather than work – with the functions in order to increase their learning experience and become more fluent in q. For that reason, we created a github repository available at https://github.com/hansmall/quantQ, we plan to keep the functions and examples created within this book. We encourage readers to participate in contributing to the repository, extend and improve the codebase and implement more machine learning methods.

# STRUCTURE OF THE BOOK

We organise the text into four parts. In the first part, we introduce the principles of the q programming language. This is not an exhaustive deep dive into kdb+ and all its database features, prior knowledge of the language is expected and the fundamental concepts learned enable us to proceed with the more advanced sections.

In the second part, we focus on the necessary tools for us to efficiently work with large data sets, and we joins, parallelisation, data cleaning, and parse trees. Some of these concepts may be first compelling, yet appreciation of them increases the flexibility of the language syntax, and speeds up calculations tremendously. The section concludes with a set of practical working examples from the financial domain.

In the third part, we present elements of data science. We start with a basic overview of statistics, a first part of call when facing a new data set. We then present one of the most powerful techniques of data science, linear regression. We extend the concepts of linear regression into a time series domain, where we implement ARIMA models and Granger causality framework. This section also covers complex numbers, Fourier transforms, Eigensystem calculations, and outlier detection techniques. Finally, we show how to simulate time series data for economic research.

The fourth section focuses on machine learning methods. We start with formulating basic principles, before biasing-variance trade-off and its regularity. In particular, we present two ways of the linear regression regularisation – Ridge regression and Lasso Regression. Further, we discuss several supervised machine learning methods: the nearest neighbours principles – in particular, three different methods for employing the nearest neighbours, neural networks, and tree-based methods – AdaBoost with decision stumps, decision trees, and random forests. We continue with unsupervised machine learning methods, namely the Apriori algorithm, an algorithm initially developed for exploring shopping patterns. We move on to Foundations of Artificial Intelligence and define the multi-arm bandit problem and extend the notions of exploration and exploitation into a Monte Carlo Tree Search algorithm, which is an advanced logic behind many decision engines. We illustrate it on the game engine for the tic-tac-toe game and discuss its links to Alpha Go. Finally, we show some leading findings from econophysics. Last but not least, we conclude the book by encouraging readers to use the programming language beyond the daily workflow and perform some algorithmic art.

# PREREQUISITES

We aim to keep the prose of the book such that we fully explain all the presented topics and, at the same time, introduce readers to the intricacies of the q language. It is worth noting that we tacitly assume some relevant prerequisite knowledge. Firstly, we expect that our readers already have some programming experience. We do not expect prior experience with q, though. Secondly, we assume our readers have a working knowledge of algebra, basic calculus and probability theory. These two ingredients are sufficient to enjoy our book.

# About the Authors

Jan Novotny

Jan is an eFX quant trader at Deutsche Bank. Before his current role, he was a front office quant at HSBC in the electronic FX markets. Before joining HSBC team, he was working in the Centre for Econometric Analysis on the high-frequency time series econometric models analysing the dynamics of multivariate price jumps. Prior to that, he worked on several research projects at Manchester Business School, CERGE-EI, and Czech Academy of Sciences. He was a visiting lecturer at Cass Business School, Warwick Business School, Politecnico di Milano and New York University in Prague. Jan co-authored a number of papers in peer-reviewed journals in finance and physics.

Paul A. Bilokon

Paul is CEO and founder of Thalesians and an expert in electronic trading across multiple asset classes, having helped businesses at Deutsche Bank and Citigroup. Before focusing on electronic trading, Paul worked at Nomura, Lehman Brothers and Morgan Stanley. Paul has been educated at Christ Church College, Oxford and Imperial College. Apart from mathematical and computational finance, his academic interests include machine learning.

Aris Galiotos

Aris is currently the global technical lead for the eFX kdb+ team at HSBC, where helps architect, develop and support big data installation. Before that, he was the APAC head of the Equities Data and Analytics team at Citi, where he implemented pre- and post-trade analytics, alerts and real-time signals for the trading team. Before moving to Hong Kong, he worked as a consultant for various investment banks and financial institutions in London, New York and Toronto. He came across kdb and q in the mid-2000s, was astonished by the speed, elegance, simplicity of the language and direct user support, and never looked back. Aris holds an MSc in Financial Mathematics with Distinction from the University of Edinburgh, after completing a degree in Mathematics at the University of Patras, Greece.

Frédéric Délèle

Frédéric is an independent algorithm trader and consultant. He has been playing several roles in quantitative finance for the last 15 years. As a quantitative trader, he has designed and implemented automated trading strategies for hedge funds. As a financial engineer and risk manager, he developed qualitative models for market and counterparty credit risks for several investment banks and financial software companies. He has also consulted for clearing houses to optimise margin requirements. Frédéric is the co-author of several peer-reviewed articles in market microstructure, asset pricing and econophysics. He holds an MSc in Computer Science from the Swiss Federal Institute of Technology Lausanne (EPFL), an MSc in Banking and Finance from HEC Lausanne and a PhD in Finance from Hanken School of Economics in Helsinki, Finland.
