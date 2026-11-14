# Outliers Are (Bad?) People, Too

Think about this. How does an email delivery service predict if a particular email comes from a spammy person? Spammers are a small group of people whose behavior lies outside the predictable norm. In this case, then, a spammer is no more than a small but understood class outside what is expected.

This is no different than a bank pinging your phone because it doesn't trust that gas station hot dog you would otherwise never buy except for this one time. The bank is detecting something unusual—a data point that registers as an outlier. Outliers aren't hard to find if you know where to look and what you're looking for. To be fair, I love gas station hot dogs, so this isn't an issue for my bank, just my stomach.

But what if you don't know either of these? Fraudsters will change their behavior so that the only thing you can expect from them is something unexpected. If that error has never happened before, how do you find those odd points for the first time?

This type of outlier detection is an example of unsupervised learning and data mining. It's the intuitive flip side of clustering. In cluster analysis, you look for a data point's group of friends and analyze that group. In outlier detection, you care about data points that differ from the groups. They're odd or exceptional in some way.

This chapter starts with a simple, standard way of calculating outliers in normal-like one-dimensional data. Then it moves on to using k-nearest neighbor (kNN) graphs to detect outliers in multidimensional data, similar to how you used r-neighborhood graphs previously.

# The Fascinating Case of Hadlum v. Hadlum

NOTE

The Excel workbook used in this section, PregnancyDuration.xlsx, is available for download at the book's website at www.wiley.com/go/datasmart2e. Later in this chapter, you'll be diving into a larger spreadsheet, SupportCenter.xlsx, also available on the same website.

In the 1940s, a British guy named Mr. Hadlum went off to war. Some days later, 349 of them in fact, his wife Mrs. Hadlum gave birth. Now, the average pregnancy lasts about 266 days. That places Mrs. Hadlum almost 12 weeks past her due date. Back then, inducing pregnancy wasn't as common.