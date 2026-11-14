# Creating a Distance Matrix

To implement the silhouette, there's one major piece of data you need: the distance between customers. And while cluster centers may move around in our analysis, the distance between two customers never changes. So, you can just create a single Distances tab and use it in all of your silhouette calculations no matter what value of K you use or where those centers end up.

Let's start by creating a blank sheet called Distances. We're going to want to list the names of each customer going both across and down—and then we'll find the distances between them. (See Figure 4.27.) Now, you could copy and paste these names from previous worksheets. But let's try something different for good measure.

| | A | B | C | D | E | F | G | H |
|---|---|---|---|---|---|---|---|---|
| 1 | | Adams | Allen | Anderson Bailey | Baker | Barnes | Bell | |
| 2 | Adams | =Matrix!H1:DC1 | | | | | | |
| 3 | Allen | | | | | | | |
| 4 | Anderson Bailey | | | | | | | |
| 5 | Baker | =TRANSPOSE(B1#) | | | | | | |
| 6 | Barnes | | | | | | | |
| 7 | Bell | | | | | | | |
| 8 | Bennett | | | | | | | |
| 9 | Brooks | | | | | | | |
| 10 | Brown | | | | | | | |
| 11 | Butler | | | | | | | |
| 12 | Campbell | | | | | | | |
| 13 | Carter | | | | | | | |
| 14 | Clark | | | | | | | |
| 15 | Collins | | | | | | | |
| 16 | Cook | | | | | | | |

Figure 4.27: The bare-bones Distances tab

In your new Distances worksheet, start in cell B1 and double-click to go into edit mode. From there, type in an equal sign and select cells H1:DC1 from the Matrix worksheet. This should have the list of names going across horizontally. Next, in cell A2, enter the following formula: =TRANSPOSE(B1#). Then press Enter. This will take the same list of names and have it run horizontally.

If you have a newer version of Excel, this should work perfectly. The hashmark after the B1 tells Excel that you want to reference the same range returned in formula B1. These are the dynamic arrays mentioned in Chapter 1. If you don't yet have this functionality because you are in an older version of Excel, you can always copy and paste these values instead. Make sure to paste column-wise values vertically (aka “transposed”), as shown in Figure 4.27.