Now, you'll need to insert a new line in the Excel table (at row 5 of the worksheet) at the top for the initial level estimate for time 0 (see Figure 8.3). Next create three additional columns for the table: Level Estimate column (C), a One-Step Forecast column (D) and a Forecast Error column (E). Take a look at Figure 8.3 to see my setup. Once yours looks like mine, we're ready to calculate.

| A | B | C | D | E | F |
|---|---|---|---|---|---|
| Total Months | | Level Smoothing Alpha | | | |
| 36 | | 0.50 | | | |
| t | Demand | Level Estimate | One-Step Forecast | Forecast Error | |
| 0 | | | | | |
| 1 | 165 | | | | |
| 2 | 171 | | | | |
| 3 | 147 | | | | |
| 4 | 143 | | | | |
| 5 | 164 | | | | |
| 6 | 160 | | | | |
| 7 | 152 | | | | |
| 8 | 150 | | | | |
| 9 | 159 | | | | |
| 10 | 169 | | | | |
| 11 | 173 | | | | |
| 12 | 203 | | | | |
| 13 | 169 | | | | |
| 14 | 166 | | | | |
| 15 | 162 | | | | |
| 16 | 147 | | | | |
| 17 | 188 | | | | |
| 18 | | | | | |

Figure 8.3: Initial worksheet design for simple exponential smoothing

# # Adding in the One-Step Forecast and Error

To create our one-step forecast and then understand the error, we'll have to define the correct level estimate calculation. Because this calculation has multiple conditions associated with it, we're going to build it as we go. That means we'll start with a few formula stubs and then reedit them. For instance, I will tell you to update a formula you've already input into a cell. So, don't assume just because we've placed a formula in a cell, it's the last step. You'll see this as we continue through this chapter.

Second, we'll be building toward dynamic formula interaction for the most part. That means if you want to test scenarios beyond what's described here, you should easily be able to update only a few cells and perhaps stretch out an Excel table. Everything else should be set up and ready to go as we attempt to avoid hard-coded values. So feel free to play around with the examples in this chapter going beyond what we do in the text.

So far we have a few conditions that will help us build our formula: what happens when t = 0, what happens when t = 1, what happens when t > 1, and what happens when t > 36 (that's our total month count).