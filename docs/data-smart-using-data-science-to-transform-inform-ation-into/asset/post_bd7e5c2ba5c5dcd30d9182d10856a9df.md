
## The Limitations of This Simple Approach

Tukey's fences work only when these three things are true:

- The data is vaguely normally distributed. It doesn't have to be perfect, but it should be bell curve–shaped and ideally symmetric without some long tail jutting out one side of it.
- The definition of an outlier is an extreme value on the perimeter of a distribution.
- You're looking at one-dimensional data.

Let's look at an example of an outlier that violates the first two of these assumptions. In *The Fellowship of the Ring*, when the adventurers finally form a single company (the fellowship for which the book is named), they all stand in a little group as the leader of the elves, Elrond, pronounces who they are and what their mission is.

This group contains four tall people: Gandalf, Aragorn, Legolas, and Boromir. There are also four short people. The hobbits themselves: Frodo, Merry, Pippin, and Sam.

And in between them, there's a single dwarf: Gimli. Gimli is shorter than the men by a couple heads and taller than the hobbits by about the same (see Figure 10.4).

![](img/9c4b3d77873bec9e7da149a75c568d36_370_0.png)

**Figure 10.4:** Gimli, son of Gloin, Dwarven outlier

In the movie, when we see this group presented to us for the first time, Gimli is the clear outlier by height. He belongs to neither group.

But how is he the outlier? His height is neither the least nor the greatest. Most interesting, his height is the closest to the average of the group's.

Of course, the height distribution isn't anywhere near normal. If anything, you could call it *multimodal* (a distribution with multiple *modes* or peaks). And Gimli is an outlier not because his height is extreme but because it's between these two peaks. These types of data points can be even harder to spot when you're looking over several dimensions. Going back to a common thread of this chapter—don't always assume outliers are the most extreme and unlikely points.

In fact, this kind of outlier crops up in fraud pretty frequently—someone who's *too ordinary* to actually *be ordinary*. Bernie Madoff is a great example of this. Although most Ponzi schemes offer outlier rates of return of 20-plus percent, Madoff offered reliably modest returns that blended into the noise each year—he wasn't jumping any Tukey's fences. But across years, his multiyear returns in their reliability became a multidimensional outlier. In opposition to what you might expect, that's what made people think he was a genius investor. Though in hindsight it's easy to call his performance an outlier, at the time people were too enamored with their returns to consider it anything but fortunate. So how do you find outliers in the case of multimodal, multidimensional data (you just as easily could call it *real-world data*)?

One awesome way to approach this is to treat the data like a graph dataset, just as you did to find clusters in previous chapters. Think about it. What defines Gimli as an outlier is his relationship to the other data points: his distance from them in relation to their distance from each other.

All of those distances, each point from every other point, defines edges on a graph. Using this graph, you can tease out the isolated points. To do that, you start by creating a k-nearest neighbors graph and going from there.

## Terrible at Nothing, Bad at Everything

The Excel workbook used in this section, *SupportCenter.xlsx*, is available for download at the book's website at www.wiley.com/go/datasmart2e.

For this next section, imagine that you manage a large customer support call center. Each call, email, or chat from a customer creates a ticket, and each member of the support team is required to handle at least 140 tickets daily. At the end of each interaction, a customer is given the opportunity to rate the customer on a five-star scale. Support employees are required to keep an average rating above 2, or they are fired.

High standards, I know.

The company keeps track of plenty of other metrics on each employee as well. How many times they've been tardy over the past year. How many graveyard and weekend shifts they've taken for the team. How many sick days they've taken, and out of those, how many have been on Friday. The company even tracks how many hours the employee uses to take internal training courses (they get up to 40 hours paid) and how many times they've put in a request for a shift swap or been a good Samaritan and fulfilled another employee's request.

You have all this data for all 400 call center employees in a spreadsheet. The question is which employees are outliers, and what do they teach you about being a call center employee? Are there some baddies slipping through who don't get culled by the ticket requirements and minimum customer ratings? Perhaps the outliers will teach you how to write better rules.

If you open the spreadsheet for this section of the chapter, you'll find all this tracked performance data on the SupportPersonnel sheet (see Figure 10.5). There's already an Excel table included called SupportPersonnelData.

| Employee ID | Avg Tix / Day | rating | Customer | Tardies | Graveyard Shifts Taken | Weekend Shifts Taken | Sick Days Taken | % Sick Days Taken on Friday | Employee Dev. Hours | Shift Swaps Requested | Shift Swaps Offered |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 144624 | 151.8 | 3.82 | 1 | 1 | 0 | 2 | 3 | 0% | Hours | Requested | Offered |
| 142619 | 155.2 | 3.16 | 1 | 3 | 1 | 1 | 1 | 0% | 12 | 1 | 2 |
| 142285 | 164.2 | 4.00 | 3 | 3 | 1 | 0 | 2 | 0% | 23 | 2 | 0 |
| 142158 | 174.9 | 2.77 | 0 | 3 | 1 | 2 | 2 | 50% | 13 | 1 | 0 |
| 141500 | 155.5 | 2.22 | 4 | 1 | 1 | 3 | 3 | 67% | 16 | 1 | 0 |
| 145082 | 153.8 | 3.90 | 3 | 2 | 0 | 3 | 3 | 100% | 5 | 1 | 0 |
| 139410 | 162.1 | 3.45 | 3 | 3 | 1 | 3 | 3 | 0% | 13 | 2 | 1 |
| 135014 | 154 | 3.67 | 0 | 3 | 1 | 1 | 1 | 0% | 18 | 1 | 2 |
| 139356 | 157.5 | 3.40 | 0 | 1 | 1 | 4 | 4 | 25% | 14 | 0 | 3 |
| 137368 | 160.8 | 3.30 | 1 | 3 | 1 | 0 | 0 | 0% | 33 | 2 | 4 |
| 141982 | 157.3 | 3.85 | 2 | 3 | 1 | 2 | 2 | 0% | 8 | 1 | 2 |
| 144753 | 164.1 | 2.75 | 1 | 2 | 0 | 0 | 0 | 0% | 5 | 0 | 2 |
| 132229 | 152.9 | 3.77 | 1 | 1 | 1 | 3 | 3 | 67% | 19 | 2 | 2 |
| 135254 | 158 | 2.74 | 1 | 2 | 0 | 0 | 0 | 0% | 8 | 0 | 0 |
| 131177 | 154.8 | 3.21 | 1 | 1 | 2 | 0 | 0 | 0% | 14 | 2 | 3 |
| 140074 | 153.3 | 3.13 | 1 | 3 | 1 | 0 | 0 | 0% | 18 | 1 | 3 |
| 135633 | 159.7 | 3.45 | 3 | 2 | 2 | 4 | 4 | 0% | 10 | 0 | 0 |
| 139582 | 155.7 | 3.19 | 2 | 2 | 1 | 5 | 5 | 0% | 9 | 1 | 0 |
| 135197 | 160.7 | 4.43 | 2 | 4 | 1 | 2 | 2 | 0% | 6 | 1 | 3 |
| 131975 | 143.1 | 4.37 | 0 | 3 | 1 | 3 | 3 | 33% | 0 | 2 | 3 |
| 127282 | 150.2 | 4.33 | 1 | 1 | 1 | 0 | 0 | 0% | 0 | 3 | 0 |
| 139071 | 151.5 | 3.43 | 1 | 1 | 2 | 0 | 0 | 0% | 4 | 2 | 3 |
| 141520 | 152.4 | 3.82 | 1 | 2 | 1 | 0 | 0 | 0% | 0 | 1 | 0 |
| 133358 | 157.8 | 2.80 | 2 | 3 | 2 | 7 | 7 | 43% | 0 | 3 | 3 |
| 134858 | 157.1 | 3.18 | 1 | 2 | 0 | 6 | 6 | 17% | 2 | 2 | 2 |
| 137434 | 152.5 | 4.42 | 1 | 2 | 2 | 2 | 2 | 50% | 9 | 0 | 0 |

Figure 10.5: Multidimensional employee performance data

## Preparing Data for Graphing

There's a problem with this performance data. You can't measure the distance between employees to figure out who's “on the outside” when each column is scaled so differently. What does it mean to have a difference of 5 between two employees on their average tickets versus a difference of 0.2 in customer rating? You need to standardize each column so that the values are closer to the same center and spread.

This is how columns of data are usually standardized:

- 1. Subtract the mean of a column from each observation.
- 2. Divide each observation by the standard deviation of the column.

For normally distributed data, this centers the data at about 0 (gives it a mean of 0) and gives it a standard deviation of 1. Indeed, a normal distribution with mean 0 and standard deviation 1 is called the standard normal distribution.

## STANDARDIZING USING ROBUST MEASURES OF CENTRALITY AND SCALE

Not all data you'll want to scale is normally distributed to begin with. Subtracting the mean and dividing by the standard deviation tends to work well anyway. But outliers can screw up mean and standard deviation calculations, so sometimes folks like to standardize by subtracting more robust statistics of centrality (the “middle” of the data) and dividing through by more robust measures of scale/statistical dispersion (the spread of the data).

Here are some centrality calculations that work better against one-dimensional outliers than the mean:

- **Median**: Yep, just the 50th percentile.
- **Midhinge**: The average of the 25th and 75th percentiles.
- **Trimean**: The average of the median and the midhinge. I like this one, because it sounds intelligent.
- **Trimmed/truncated mean**: The mean, but you throw away the top and bottom N points or top and bottom percentage of points. You see this one in sports a lot (think gymnastics where they throw out the top and bottom scores). If you throw away the top and bottom 25 percent and average the middle 50 percent of the data, that has its own name: the interquartile mean (IQM).
- **Winsorized mean**: Like the trimmed mean, but instead of throwing away points that are too large or too small, you replace them with a limit.

As for robust measures of scale, here are some others worth using instead of the standard deviation:

- **Interquartile range**: You saw this one earlier in the chapter. It's just the 75th percentile minus the 25th percentile in the data. You can use other n-tiles too. For example, if you use the 90th and 10th percentiles, you get the inter-decile range.
- **Median absolute deviation (MAD)**: Take the median of the data. Then take the absolute value of the difference of each point from the median. The median of these deviations is the MAD. It's kinda like the median's answer to the standard deviation.
