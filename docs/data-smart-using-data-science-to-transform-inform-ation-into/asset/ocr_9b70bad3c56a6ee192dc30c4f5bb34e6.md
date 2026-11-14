# Outlier Detection: Just Because They're Odd Doesn't Mean They're Unimportant

Statisticians 100 years ago had a lot in common with the Borg from Star Trek: a data point needed to assimilate or die. This is because a single data point can move averages and mess with spread measurements in the data. Such points are often the odd ones in the dataset. And in the simplest case, that has meant *extreme values*—quantities that were either too large or too small to have come naturally, or so it was assumed, from the same process as the other observations. Statisticians call these points *outliers*.

Outliers have a knack for messing up machine learning models. Consider a simple mistake. An analyst can’t understand why a property in their company’s portfolio is valued at billions and billions of dollars. After a little research, the culprit is found. Turns out someone had typed it into the database with too many zeros. A mistake like this can throw off the analysis by a lot.

So that's one reason to care about outliers: *to facilitate cleaner data analysis and modeling*.

But there's another reason to care about outliers. They tell us interesting things about the data, how it was collected, and they provide additional context and meaning to our analysis. In other words, by being so different, they have their own story. As I wrote in my last book *Becoming a Data Head: How to Think, Speak, and Understand Data Science, Statistics, and Machine Learning*:

> Just because certain points [are classified] as “outliers,” don’t turn off critical thinking and automatically delete these points assuming they can’t be useful. You’ll never catch [big companies] removing useful information from its datasets simply because . . . [they’ve] described these as outliers.

This chapter is all about outliers. How to detect them, and what to do once they’ve been found.