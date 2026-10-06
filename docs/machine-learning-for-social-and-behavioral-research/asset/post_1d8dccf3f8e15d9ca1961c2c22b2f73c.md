
# Preface

**FIGURE 1.** The complexity of modern data analysis necessitates a transition from primarily focusing on the interplay of data and theory, to now understanding how data, theory, and algorithms are integrated in practice.

![](img/5047f0f064e22688ceb5d0cdfaf3e964_10_0.png)

Of machine learning, data, and theory (see Figure 1), we start with detailing our perspective in Chapter 2 to address the question we often receive when teaching classes or workshops on machine learning, namely: “Can machine learning analyses be incorporated into my traditional confirmatory research?” The follow-up question is: “Given the exploratory nature of machine learning, how can we be sure our results are trustworthy?” We address this question specifically in Chapter 3 by providing details on a number of cross-validation strategies that help prevent overfitting.

One glance at the table of contents from any of the recently published books on machine learning, data, statistical learning, data science, or artificial intelligence reveals a dizzying array of algorithms not detailed in statistical textbooks. This book is different in a number of ways. The first is our aforementioned focus on theory. While Chapter 1 provides an orientation to the book's organization, the primary substance of our book begins with a focus on theory (Chapter 2)—how machine learning fits into research that has been traditionally done from a hypothesis-driven perspective. This is followed by a chapter (Chapter 3) on principles, specifically, how practitioners can apply machine learning algorithms to produce trustworthy results. These chapters set the stage for our discussion of algorithms for univariate outcomes (Chapters 4–6); however, in contrast to other books, we focus largely on regularization and tree-based methods. This allows us to discuss the integration of these algorithms with complex models that are commonly applied in social and behavioral research, namely, latent variable models. This enables us to provide additional detail on handling measurement error, an extremely important component of survey data, longitudinal data analysis, and the assessment of heterogeneity through the identification of subgroups. Measurement is the focus of Chapters 7 and 8, followed by a discussion of modeling longitudinal data (Chapter 9), and assessing heterogeneity (Chapter 10). Finally, we focus on the last two chapters on alternative data types, with an introduction to text analysis (Chapter 11), where we detail the processing of text data and implementing commonly applied algorithms, and social network data (Chapter 12), with an emphasis on network modeling.

Chapters 1 through 6, 9, and 11 have been used as the primary source material for an advanced undergraduate and graduate course. Further, this book can be used as a supplement reading for courses on regression, multivariate, longitudinal data, and structural equation modeling, among others.

Chapters 4 through 6 have considerable overlap with content found in other books oriented towards supervised learning, Chapter 7 and the subsequent chapters provide a more detailed/advanced account of machine learning methodologies.

Chapters pair a breadth in coverage of methodologies and algorithms with a depth in focusing on fundamental topics, which are detailed at the beginning of each chapter in a "Key Terminology" section to prepare readers for the fundamental concepts of each chapter. Further, we end Chapters 3-12 with a "Computational Time and Resources" section that discusses how to put each into practice, denoting the R packages that can be used. Every application of machine learning detailed in this book was programmed in the R statistical environment. While the book does not detail R code, code for all analyses is provided on the book's website. Readers can apply this to reproduce every example in the book.

# Acknowledgments

Each author of this book became interested in machine learning because of mentorship, collaboration, and friendship with John (Jack) J. McArdle, who passed away before this book was completed. Jack was one of the first psychological researchers who became interested in machine learning, writing a host of papers and an edited book on the topic dating back to the early 2010s. Jack gave the inspiration and motivation for each of us to pursue research in machine learning, spurred by his novel application of machine learning to understanding heterogeneity in longitudinal trajectories. Simply put without Jack, this would never have been written. In addition, we would like to thank the helpful reviewers of the book who guided us in the development of the manuscript. These reviewers were initially anonymous, but agreed to have their identities revealed now, and we would like to thank them for their insightful feedback: Sonya K. Sterba, Department of Psychology and Human Development, Vanderbilt University; George Coles, Texas A&M University; Alexander Christensen, Department of Psychology and Human Development, Vanderbilt University. Finally, we would like to thank the staff at Guilford Press, whose patience allowed the writing of this book to continue through the COVID-19 pandemic.

# Contents

## Part I. Fundamental Concepts

### 1 Introduction / 3
- 1.1 Why the Term Machine Learning? / 4
- 1.2 Do We Need Machine Learning? / 5
- 1.3 How Is This Different? / 6
- 1.4 Definitions / 8
- 1.5 Software / 9
- 1.6 Datasets / 10

### 2 The Principles of Machine Learning / 13
- 2.1 Key Terminology / 13
- 2.2 Overview / 14
- 2.3 Principle #1: Machine Learning Is Not Just Statistics / 17
- 2.4 Principle #2: Orienting Our Goals to Prediction, Explanation, and Description / 20
- 2.5 Principle #3: Labeling a Study as Exploratory or Confirmatory is simplistic / 25
- 2.6 Principle #4: Report Everything / 36
- 2.7 Summary / 38

### 3 The Practices of Machine Learning / 40
- 3.1 Key Terminology / 40
- 3.2 Comparing Algorithms and Models / 41
- 3.3 Model Fit / 42
- 3.4 Bias-Variance Trade-Off / 47
- 3.5 Resampling / 51
- 3.6 Classification / 57
- 3.7 Imbalanced Outcomes / 66
- 3.8 Conclusion / 70

## Part II. Algorithms for Univariate Outcomes

### 4 Regularized Regression / 75
- 4.1 Key Terminology / 75
- 4.2 Linear Regression / 76
- 4.3 Logistic Regression / 77
- 4.4 Regularization / 80
- 4.5 Alternative Forms of Regularization / 92
- 4.6 Bayesian Regression / 101
- 4.7 Summary / 103

### 5 Decision Trees / 105
- 5.1 Key Terminology / 105
- 5.2 Introduction / 107
- 5.3 Describing the Tree / 112
- 5.4 Decision Tree Algorithms / 119
- 5.5 Miscellaneous Topics / 123
- 5.6 Summary / 133

### 6 Ensembles / 136
- 6.1 Key Terminology / 136
- 6.2 Bagging / 137
- 6.3 Random Forests / 144
- 6.4 Gradient Boosting / 148
- 6.5 Interpretation / 151
- 6.6 Empirical Example / 157
- 6.7 Important Notes / 163
- 6.8 Summary / 165
