
# Supervised Learning in Trading

This chapter covers the principles of supervised machine learning (ML) with a focus on trading applications. We will examine how algorithms analyze historical data to identify patterns and predict market movements, breaking down their structure into key components such as data input, functional representation, and optimization. The chapter also reviews essential classification and regression algorithms, as well as key evaluation metrics. Unlike other chapters, the focus here is on building a solid conceptual framework for supervised learning in trading rather than on specific implementation examples.

## Structure

In this chapter, we will cover the following topics:

- [Role of supervised learning](#chap05.xhtml#h18)
- [Supervised learning for predictive trading](#chap05.xhtml#h19)
- [Advantages of supervised learning](#chap05.xhtml#h20)
- [Supervised learning landscape](#chap05.xhtml#h21)
- [Core principle of supervised learning](#chap05.xhtml#h22)
- [Main supervised learning algorithms](#chap05.xhtml#h23)
- [Selection criteria for trading applications](#chap05.xhtml#h24)

## Objectives

This chapter introduces supervised learning and its role in creating advanced algorithmic trading strategies. You will learn how to use historical data and labeled outcomes to build predictive models for forecasting market behavior. We will cover key classification algorithms such as logistic regression and Support Vector Machines (SVMs), as well as essential regression methods such as decision tree regressors, gradient boosting, and k-nearest neighbors, with a focus on their practical applications in trading. We will also explore how to choose the right algorithm based on your data, prediction goals, and evaluation metrics, such as accuracy and precision, enabling you to refine and optimize your trading systems effectively.

## Role of Supervised Learning in Trading

This section examines trading from a technological perspective, highlighting how supervised learning plays a key role in building predictive trading systems by using historical data and labeled outcomes to anticipate future market trends.

Before we continue, let us briefly review the main points from the first chapter.

> **Note:** This section focuses only on reviewing these key ideas; new information is introduced in the following section.

### Rise of ML in Trading

ML, a key branch of artificial intelligence, enables computer systems to learn from data and improve themselves without explicit programming. Introduced by Arthur Samuel in 1959, this approach is unique in that it derives rules directly from data rather than relying on predefined instructions. Unlike traditional programming, where rules are set manually, ML algorithms analyze data to uncover patterns and correlations that guide decision-making. In trading, ML demonstrates its value by processing vast amounts of financial data to predict market trends.

## Supervised Learning for Predictive Trading's Foundation

In algorithmic trading, supervised learning, a branch of ML, introduces an important step forward in strategy development. It works with labeled data, where the training set includes both the input features and their corresponding outputs. This method is like guided learning in that the model learns from specific examples of what it should predict.

In the context of trading, these labeled datasets typically consist of various market indicators as inputs (like fundamental data[^1], historical prices, volumes, and technical indicators) and specific outcomes as outputs (such as future price movements or trend classifications), as depicted in the following graph:

![Supervised Learning Workflow](images/fig-5-1.png)

This sketch illustrates the workflow of supervised learning within the context of financial trading, where the model is trained using various types of market data, bar charts, volume histograms, and fundamental data, as inputs. During the training phase, the algorithm learns to correlate these inputs with known outputs, specifically historical price movements and trend classifications.

Once trained, the model enters the inference phase, applying its learned rules to new data to make predictions about future price movements and market trends, thereby informing trading decisions.

Building on the basics of supervised learning with traditional market data, the field is expanding into more sophisticated areas. Techniques such as graph learning, image-based ML, and the analysis of textual and auditory data are increasingly shaping and transforming trading strategies.

Graph learning, for instance, is used to analyze market networks, where stocks are nodes, and correlations are edges, offering insights into market dynamics. ML from images, such as Deep Convolutional Neural Networks, is applied to interpret candlestick charts, identifying patterns that predict price movements. Natural language processing techniques analyze news, social media chatter, and earnings call transcripts for sentiment analysis, influencing trading decisions. Similarly, analyzing auditory data, like fluctuations in tone during earnings calls, provides subtle cues about company performance, aiding in predictive analysis. These innovative approaches leverage diverse data forms, going far beyond traditional numerical data, offering traders a more holistic view of the market and an edge in decision-making.

## Advantages of Supervised Learning in Trading

The quintessence of ML lies in its unparalleled ability to autonomously derive decision-making rules directly from data, a stark contrast to traditional statistical techniques that often rely on pre-established rules. ML models can identify complex patterns and relationships in data, allowing them to make reliable predictions about new, unseen information. Rather than simply recognizing patterns, these models undergo a thorough training process, learning from a wide range of market data and outcomes to understand market behavior. This ability makes them well-suited for developing trading systems that use historical data to predict future market trends more accurately than traditional methods. Furthermore, ML's capability to extract structured insights, such as those gleaned from decision tree analysis, provides clear, interpretable models - an advantage in understanding complex market behaviors.

The following figure is a concrete example[^2] of structured knowledge extracted by an ML algorithm (decision tree):

![Decision Tree Example](images/fig-5-2.png)

ML surpasses traditional statistical methods with its inherent capability to autonomously distill structured knowledge from complex datasets, a feat typically unattainable with conventional techniques. Unlike traditional approaches that often rely on static business rules, which can quickly become outdated due to ever-evolving market conditions, ML stands out with its dynamic adaptability. It continuously updates and refines its predictive rules in response to new data, ensuring that the insights and strategies remain relevant and effective. Furthermore, ML excels in handling high-dimensional data spaces and uncovering non-linear relationships, which are often encountered in financial markets but are challenging for traditional models to capture.

After examining the advantages of supervised learning in trading, we now shift to the mechanics behind it. The next section explores the core principles, such as labeled data, training algorithms, and prediction generation, to understand how these models operate effectively.

## Supervised Learning Landscape

[^1]: [chap05.xhtml#footnote-126]
[^2]: [chap05.xhtml#footnote-125]
