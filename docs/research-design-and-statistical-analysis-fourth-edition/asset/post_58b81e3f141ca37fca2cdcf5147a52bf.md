
with the same prior experiences, or whether it is due to a chance fluctuation in performance of the two groups. The superintendent may note that the average score in her district below that for the state as a whole. He may ask whether this is a chance result or one that will repeat with future generations of students.

Finally, description of the data is important to ensure that assumptions underlying subsequent, inferential statistics will be valid for the data analyzed. Questions about group differences (e.g., boys and girls), or the performance between a group (e.g., the school district) and some standard (e.g., scores for the state as a whole), are questions of statistical inference. These questions require further analysis, and those analyses rest on assumptions about the shape and variability of the distribution of data. Therefore, we first explore our data to assess whether assumptions underlying planned inferential analyses are met. If not, we may consider modifications of our planned analyses. Among many possibilities, such modifications may include deleting extreme scores, transforming data, or using statistical procedures other than those originally.

In this chapter, we present the tools for the necessary description and exploration of data. The major objectives of this chapter are:

- Present ways of graphing the data that provide different views of the distribution of scores. We graph the data in different ways because different graphs provide different sorts of information. Some data plots provide only a general sense of the distribution, where others provide a more detailed look and enable us more readily to address questions such as whether there are scores that are markedly different from most of the others.
- Present several summary statistics to reflect key properties of distributions. Specifically, we will present measures of average, variability, and shape of the distribution. In measures of average and variability, different indices of the same distribution have different properties that make them more or less desirable depending upon the situation. Thus, in addition to the mean and standard deviation, we will consider the median and interquartile range.
- Introduce ways of characterizing relationships between two variables. We will present scatter diagrams and illustrate two ways of summarizing the relationship between two variables: the correlation coefficient and linear regression. The correlation coefficient is a numerical measure of the direction and strength of a relationship, while linear regression tells us how much one variable changes as a function of changes in the other.

Good statistical practice should begin with the description and visualization of the data using graphs and summary statistics as presented in this chapter.

## 2 Research Design and Statistical Analysis

## 2.2 Graphicalies of the Data

The first step in describing a data set is to get an overall view of the data by graphing the distribution of observations. An understanding of the distribution of scores provides fundamental information, as well as a context for interpreting specific properties, such as its mean and standard deviation.

Table 2.1 Royer second-grade addition scores
| | | | | | | | |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 93 | 82 | 94 | 90 | 82 | 84 | 100 | 85 |
| 95 | 50 | 88 | 100 | 89 | 69 | 94 | 94 |
| 50 | 83 | 95 | 72 | 47 | 100 | 94 | |

In a study of basic arithmetic skills, Royer, Tronsky, and Chan (1999) collected both accuracy and response time scores from students in grades 1 to 8 for addition, subtraction, and multiplication. Table 2.1 presents the perfect score for 28 students in second grade. What do we do with these numbers? Even with only 28 values, it can be hard to get a sense of how the students are doing. For example, is not easy to see if all the children are doing well addition, or if there are particular individuals who are lagging behind or need more help. Let's use different types of graphs to visualize the data. Many of these graphs are available in the Explore module of SPSS or from Graphs menu. Similarly, basic plots can be generated in Excel, and we will focus on plotting using R because doing so is easy and the results are nicely customizable.

### 2.2.1 Histograms

One of the simplest graphical summaries of data is a histogram. Histograms plot the frequency of scores. Figure 2.1 presents a histogram for the data set of Table 2.1. In this graph, the label on the left y-axis (the ordinate) shows the number of scores represented by each bar, that is, the frequency. Histograms sometimes show the proportion of scores in each bin, rather than the frequency, which changes the y-axis but not the distribution of data. The x-axis (the abscissa) represents the addition scores, which have been divided into intervals, bins of five points each (e.g., 96-100, 91-95, etc.). The width of bins or equivalently, the total number of bins, can be adjusted to best capture the shape of data. The goal in constructing a graph of distribution is to summarize the important characteristics of the distribution. A summary involves data reduction and a corresponding loss of information; however, an accurate summary must retain any important information. Thus, researchers must exercise judgment in deciding on an appropriate degree of resolution (i.e., bin size) for a graph.

Once the histogram is constructed, important characteristics of the distribution should be more evident than they are from the list of scores in Table 2.1. It is clear in Figure 2.1 that most students performed well. Indeed, the greatest number of scores appears in the bin showing 96%–100% correct. However, it is also evident that a few students performed very poorly, and there is a gap of at least 10 percent points between the three lowest scores and the lowest of the remaining 25 scores. This gap is typical of many real data sets, as is the obvious asymmetry in the distribution. Miccer (1989) examined 440 distributions of achievement scores from the classic bell shape as asymmetry (skew) and “lumpiness” (more than one mode, the most frequently observed value). Similarly, after analyzing many distributions based on standard chemical analyses of blood samples, Hill and Dixon (1982) concluded that real-life distributions were “asymmetric, lumpy, and have relatively unique values” (p. 393). We raise this point because the inferential procedures most commonly encountered in journal articles rest on strong assumptions about the shape of the distribution of data in the population.

![](img/53d3130502f4ff3b15cbe3697d6e8c5a_43_0.png)

**Figure 2.1** Histogram of the data in Table 2.1.

These assumptions are often not met, and it is therefore important to understand the consequences of the mismatch between assumptions and the distribution of data. We will consider those consequences and alternative analyses later in this book. For now, we again emphasize that exploring the data is a first step in evaluating the validity of assumptions that play a role in the next, inferential, stage of analysis.

### 2.2.2 Box Plots

Histograms provide only one way to look at our data. A very different view is provided by box plots, which emphasize important characteristics of the data while sacrificing much of the detail available in a histogram. Figure 2.2 presents a box plot of the same data depicted in the histogram in Figure 2.1. The box plot quickly provides information about the main characteristics of the distribution of scores: (1) the median, the value at the center of the distribution; (2) the variability, spread, of the scores; (3) the degree of skewness, as asymmetry, in the distribution; and (4) extreme scores, or outliers. We will consider each of the aspects of the box plot, but we first provide an overview of the elements.

# Creating the Box

The construction of a box plot begins by placing the scores of the data set in order by rank, from lowest to highest. Once this is done, we can draw the box depicted in Figure 2.2. The
