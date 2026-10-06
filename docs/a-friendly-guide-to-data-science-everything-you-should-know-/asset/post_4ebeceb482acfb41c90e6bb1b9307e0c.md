
# CHAPTER 14 READY FOR THE MAIN EVENT: FEATURE ENGINEERING, SELECTION, AND REDUCTION

## Table 14-7. Some student data pre-transformation

| Student | Age | Scholarship Value | # of Clubs | English Grade | Math Grade |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | 18 | | 2 | 81 | 89 |
| 2 | 20 | 1,500 | 0 | 57 | 60 |
| 3 | 21 | 25,000 | 3 | 80 | 92 |
| 4 | 21 | 17,000 | 0 | 93 | 94 |
| 5 | 18 | 9,000 | 4 | 90 | 78 |
| 6 | 22 | 0 | 1 | 49 | 81 |
| 7 | 19 | 12,000 | 2 | 96 | 91 |
| 8 | 21 | 750 | 1 | 75 | 81 |
| 9 | 20 | 21,500 | 3 | 86 | 79 |
| 10 | 18 | 15,000 | 0 | 62 | 58 |

If we scale Age, Scholarship Value, and # of Clubs with min-max scaling (a range of 0–1), we will have also normalized those because we’re using the same scale for all three. We can also binarize the two grades on pass-fail scale (60+ passing). Table 14-8 shows what this would look like.

## Table 14-8. Some student data after scaling, normalizing, and binarizing

| Student # | Age-Scaled | Scholarship-Scaled | Clubs-Scaled | English-Grade-Bin | Math-Grade-Bin |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | 0.00 | 0.00 | 0.50 | 1 | 1 |
| 2 | 0.50 | 0.06 | 0.00 | 0 | 1 |
| 3 | 0.75 | 1.00 | 0.75 | 1 | 1 |
| 4 | 0.75 | 0.68 | 0.00 | 1 | 1 |
| 5 | 0.00 | 0.36 | 1.00 | 1 | 1 |
| 6 | 1.00 | 0.00 | 0.25 | 0 | 1 |
| 7 | 0.25 | 0.48 | 0.50 | 1 | 1 |
| 8 | 0.50 | 0.03 | 0.25 | 1 | 1 |
| 9 | 0.25 | 0.86 | 0.75 | 1 | 1 |
| 10 | 0.00 | 0.60 | 0.00 | 1 | 0 |

## Aggregation Encoding

We can also use group statistics based on aggregations. For instance, if we're working on credit card fraud detection, different types of cardholders may have different behaviors that are “normal” and not likely fraudulent. We can use group statistics to get powerful features. For instance, assume we have a huge table of individual transactions by thousands of cardholders. If we group cardholders into typical monthly spending ranges, with the lowest being up to $1,000 and one of the higher ones $20,000–30,000, a transaction for $900 might be out of the ordinary for the lowest spender, but a drop in the bucket for the higher spender. We might do something with several steps to create a new feature based on this.

We could take the average of all transactions by cardholders in each group and then take the difference between the average for the cardholder’s group and the individual transaction value, so we’ll get a new number that we can store as a new feature.

As an example, let's say we want to flag transactions that may need further investigation for fraud. We just want a simple screen that will only flag some, but we're not worried about false positives as these transactions will just be sent for further automated investigation. See Table 14-9 for an example of some transactions for three card members. Table 14-10 shows the average monthly spend per member through previous month, and Table 14-11 shows a running total of the previous 30 days’ spend for each member through a given date.

## Table 14-9. Some credit card transactions before transformation

| Trans. # | Transaction Date-Time | Member # | Transaction Amount |
| :--- | :--- | :--- | :--- |
| 1 | 2024-05-02 13:04:53 | 1 | 450.23 |
| 2 | 2024-05-02 18:09:11 | 2 | 567.33 |
| 3 | 2024-05-03 00:34:30 | 3 | 75.65 |
| 4 | 2024-05-03 12:04:55 | 1 | 11,200.30 |
| 5 | 2024-05-03 14:21:39 | 1 | 101.92 |
| 6 | 2024-05-04 07:11:45 | 3 | 34.96 |
| 7 | 2024-05-04 10:34:22 | 2 | 120.55 |
| 8 | 2024-05-04 17:43:56 | 3 | 1,356.45 |
| 9 | 2024-05-04 23:54:23 | 1 | 1,204.67 |
| 10 | 2024-05-05 11:08:23 | 2 | 156.96 |

## Table 14-10. Average monthly spending per member through last month

| Member # | Average Spending |
| :--- | :--- |
| 1 | 9,500 |
| 2 | 700 |
| 3 | 1,100 |

## Table 14-11. Running total over the last 29 days by member

| Member # | Date | Previous 29-Day Spend |
| :--- | :--- | :--- |
| 1 | 2024-05-01 | 7,589.64 |
| 2 | 2024-05-01 | 2,587.45 |
| 3 | 2024-05-01 | 441.67 |
| 1 | 2024-05-02 | 8,039.87 |
| 2 | 2024-05-02 | 3,154.78 |
| 3 | 2024-05-02 | 441.67 |
| 1 | 2024-05-03 | 13,145.79 |
| 2 | 2024-05-03 | 567.33 |
| 3 | 2024-05-03 | 117.32 |
| 1 | 2024-05-04 | 12,545.61 |
| 2 | 2024-05-04 | 367.82 |
| 3 | 2024-05-04 | 1,473.77 |

To determine if we should flag a transaction, we calculate a column called Remaining Spend by taking the member's average monthly spend from Table 14-10, subtracting the previous day's 29-day spend from Table 14-11, and finally subtracting all prior transactions for the current day. If this value is negative, we set the Inspect Flag column to 1. This can be seen in Table 14-12.

## Table 14-12. Flagging members who are spending more than their normal amount

| # | Transaction Date | Member # | Transaction Amount | Remaining Spend | Inspect Flag |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | 2024-05-02 13:04:53 | 1 | 450.23 | 1,460.13 | 0 |
| 2 | 2024-05-02 18:09:11 | 2 | 567.33 | -2,454.78 | 1 |
| 3 | 2024-05-03 00:34:30 | 3 | 75.65 | 582.59 | 0 |
| 4 | 2024-05-03 12:04:55 | 1 | 11,200.30 | -9,740.17 | 1 |
| 5 | 2024-05-04 14:21:39 | 1 | 101.92 | -9,842.09 | 1 |
| 6 | 2024-05-04 07:11:45 | 3 | 34.96 | 947.72 | 0 |
| 7 | 2024-05-04 10:34:22 | 2 | 120.55 | 12.12 | 0 |
| 8 | 2024-05-04 17:43:56 | 3 | 1,356.45 | -408.73 | 1 |
| 9 | 2024-05-04 23:54:23 | 1 | 1,204.67 | -4,850.46 | 1 |
| 10 | 2024-05-05 11:08:23 | 2 | 156.96 | 175.22 | 0 |

Given how many of these transactions are flagged, this is sensitive and should probably be modified. An approach like this can be powerful in a lot of situations. You may have already done some imputing missing values during preprocessing, but creating new features can sometimes involve missing values.

## Reshaping the Data

Another type of transformation you might do involves reshaping the data, most commonly pivoting. Pivoting takes many rows and creates new columns. It also involves aggregation such as summing or averaging. For instance, take some data based on what we saw in Table 14-1.

## Table 14-13. Sales by pizza size

| Order # | Date | Size | Quantity | Sales |
| :--- | :--- | :--- | :--- | :--- |
| 1 | 2024-03-01 | Personal | 1 | 12.50 |
| 2 | 2024-03-01 | Large | 1 | 21.00 |
| 3 | 2024-03-01 | Medium | 2 | 34.00 |
| 4 | 2024-03-01 | Large | 1 | 25.00 |
| 5 | 2024-03-01 | Personal | 3 | 37.50 |
| 6 | 2024-03-01 | Large | 2 | 47.50 |
| 6 | 2024-03-01 | Medium | 1 | 18.00 |
| 7 | 2024-03-02 | Personal | 2 | 24.00 |
| 7 | 2024-03-02 | Medium | 1 | 16.50 |
| 8 | 2024-03-02 | Large | 3 | 59.00 |
| 8 | 2024-03-02 | Personal | 2 | 20.00 |
| 9 | 2024-03-02 | Large | 1 | 21.00 |

If we want to see the data per order without having multiple rows for a given order, we could do that by aggregating at the date level. We want to see both quantity and sales summed up for each row. Table 14-14 shows the data at the order level and Table 14-15 at the date level.

## Table 14-14. Pivoted pizza data by order number

| Order # | Date | Qty- Personal | Qty- Medium | Qty- Large | Sales- Personal | Sales- Medium | Sales-Large |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | 2024-03-01 | 1 | 0 | 0 | 12.50 | 0.00 | 0.00 |
| 2 | 2024-03-01 | 0 | 0 | 1 | 0.00 | 0.00 | 21.00 |
| 3 | 2024-03-01 | 0 | 2 | 0 | 0.00 | 34.00 | 0.00 |
| 4 | 2024-03-01 | 0 | 0 | 1 | 0.00 | 0.00 | 25.00 |
| 5 | 2024-03-01 | 3 | 0 | 0 | 37.50 | 0.00 | 0.00 |
| 6 | 2024-03-01 | 0 | 1 | 2 | 0.00 | 18.00 | 47.50 |
| 7 | 2024-03-02 | 2 | 1 | 0 | 24.00 | 16.50 | 0.00 |
| 8 | 2024-03-02 | 2 | 0 | 3 | 20.00 | 0.00 | 59.00 |
| 9 | 2024-03-02 | 0 | 0 | 1 | 0.00 | 0.00 | 21.00 |

## Table 14-15. Pivoted pizza sales by date

| Date | Qty- Personal | Qty- Medium | Qty- Large | Sales- Personal | Sales- Medium | Sales-Large |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 2024-03-01 | 4 | 3 | 4 | 50.00 | 52.00 | 93.50 |
| 2024-03-02 | 4 | 1 | 4 | 44.00 | 16.50 | 80.00 |
