
- 18.8 Chapter 13 ...... 281
  - 18.8.1 EW portfolios with the tidyverse ...... 281
  - 18.8.2 Advanced weighting function ...... 282
  - 18.8.3 Functional programming in the backtest ...... 283

- 18.9 Chapter 16 ...... 285
- 18.10 Chapter 17 ...... 285

## Bibliography ...... 289

## Index ...... 319

## Preface

This book is intended to cover some advanced modelling techniques applied to equity investment strategies that are built on firm characteristics. The content is threefold. First, we try to simply explain the ideas behind most mainstream machine learning algorithms that are used in equity asset allocation. Second, we mention a wide range of academic references for the readers who wish to push a little further. Finally, we provide hands-on R code samples that show how to apply the concepts and tools on a realistic dataset which we share to encourage reproducibility.

## What this book is not about

This book deals with machine learning (ML) tools and their applications in factor investing. Factor investing is a subfield of a large discipline that encompasses asset allocation, quantitative trading and wealth management. Its premise is that differences in the returns of firms can be explained by the characteristics of these firms. Thus, it departs from traditional analyses which rely on price and volume data only, like classical portfolio theory à la Markowitz (1952), or high frequency trading. For a general and broad treatment of Machine Learning in Finance, we refer to Dixon et al. (2020).

The topics we discuss are related to other themes that will not be covered in the monograph. These themes include:

- Applications of ML in other financial fields, such as fraud detection or credit scoring. We refer to Ngai et al. (2011) and Baesens et al. (2015) for general purpose fraud detection, to Bhattacharyya et al. (2011) for a focus on credit cards and to Ravisankar et al. (2011) and Abbasi et al. (2012) for studies on fraudulent financial reporting. On the topic of credit scoring, Wang et al. (2011) and Brown and Mues (2012) provide overviews of methods and some empirical results. Also, we do not cover ML algorithms for data sampled at higher (daily or intraday) frequencies (microstructure models, limit order book). The chapter from Kearns and Nevmyvaka (2013) and the recent paper by Sirignano and Cont (2019) are good introductions on this topic.

- Use cases of alternative datasets that show how to leverage textual data from social media, satellite imagery, or credit card logs to predict sales, earning reports, and, ultimately, future returns. The literature on this topic is still emerging (see, e.g., Blank et al. (2019), Jha (2019) and Ke et al. (2019)) but will likely blossom in the near future.

- Technical details of machine learning tools. While we do provide some insights on specificities of some approaches (those we believe are important), the purpose of the book is not to serve as reference manual on statistical learning. We refer to Hastie et al. (2009), Cornuejols et al. (2018) (written in French), James et al. (2013) (coded in R!) and Mohri et al. (2018) for a general treatment on the subject. Moreover, Du and Swamy (2013) and Goodfellow et al. (2016) are solid monographs on neural networks particularly and Sutton and Barto (2018) provide a self-contained and comprehensive tour in reinforcement learning.

- Finally, the book does not cover methods of **natural language processing** (NLP) that can be used to evaluate sentiment which can in turn be translated into investment decisions. This topic has nonetheless been trending lately and we refer to Loughran and McDonald (2016), Cong et al. (2019a), Cong et al. (2019b) and Gentzkow et al. (2019) for recent advances on the matter.

## The targeted audience

Who should read this book? This book is intended for two types of audiences. First, **postgraduate students** who wish to pursue their studies in quantitative finance with a view towards investment and asset management. The second target groups are **professionals from the money management industry** who either seek to pivot towards allocation methods that are based on machine learning or are simply interested in these new tools and want to upgrade their set of competences. To a lesser extent, the book can serve **scholars or researchers** who need a manual with a broad spectrum of references both on recent asset pricing issues and on machine learning algorithms applied to money management. While the book covers mostly common methods, it also shows how to implement more exotic models, like causal graphs (Chapter 14), Bayesian additive trees (Chapter 9), and hybrid autoencoders (Chapter 7).

The book assumes basic knowledge in **algebra** (matrix manipulation), **analysis** (function differentiation, gradients), **optimization** (first and second order conditions, dual forms), and **statistics** (distributions, moments, tests, simple estimation method like maximum likelihood). A minimal **financial culture** is also required: simple notions like stocks, accounting quantities (e.g., book value) will not be defined in this book. Lastly, all examples and illustrations are coded in R. A minimal culture of the language is sufficient to understand the code snippets which rely heavily on the most common functions of the tidyverse (Wickham et al. (2019), www.tidyverse.org), and piping (Bache and Wickham (2014), Mailund (2019)).

## How this book is structured

The book is divided into four parts.

Part I gathers preparatory material and starts with notations and data presentation (Chapter 1), followed by introductory remarks (Chapter 2). Chapter 3 outlines the economic foundations (theoretical and empirical) of factor investing and briefly sums up the dedicated recent literature. Chapter 4 deals with data preparation. It rapidly recalls the basic tips and warns about some major issues.

Part II of the book is dedicated to predictive algorithms in supervised learning. Those are the most common tools that are used to forecast financial quantities (returns, volatilities, Sharpe ratios, etc.). They range from penalized regressions (Chapter 5), to tree methods (Chapter 6), encompassing neural networks (Chapter 7), support vector machines (Chapter 8) and Bayesian approaches (Chapter 9).

The next portion of the book bridges the gap between these tools and their applications in finance. Chapter 10 details how to assess and improve the ML engines defined beforehand. Chapter 11 explains how models can be combined and often why that may not be a good idea. Finally, one of the most important chapters (Chapter 12) reviews the critical steps of portfolio backtesting and mentions the frequent mistakes that are often encountered at this stage.

The end of the book covers a range of advanced topics connected to machine learning more specifically. The first one is **interpretability**. ML models are often considered to be black boxes and this raises trust issues: how and why should one trust ML-based predictions? Chapter 13 is intended to present methods that help understand what is happening under the hood. Chapter 14 is focused on **causality**, which is both a much more powerful concept than correlation and also at the heart of many recent discussions in Artificial Intelligence (AI). Most ML tools rely on correlation-like patterns and it is important to underline the benefits of techniques related to causality. Finally, Chapters 15 and 16 are dedicated to non-supervised methods. The latter can be useful, but their financial applications should be wisely and cautiously motivated.

## Companion website

This book is entirely available at http://www.mlfactor.com. It is important that not only the content of the book be accessible, but also the data and code that are used throughout the chapters. They can be found at https://github.com/shokru/mlfactor.github.io/tree/master/material. The online version of the book will be updated beyond the publication of the printed version.

## Why R?

The supremacy of Python as the dominant ML programming language is a widespread belief. This is because almost all applications of deep learning (which is as of 2020 one of the most fashionable branches of ML) are coded in Python via Tensorflow or Pytorch. The fact is that R has a lot to offer as well. First of all, let us not forget that one of the most influential textbooks in ML (Hastie et al. (2009)) is written by statisticians who code in R. Moreover, many statistics-orientated algorithms (e.g., BARTs in Section 9.5) are primarily
