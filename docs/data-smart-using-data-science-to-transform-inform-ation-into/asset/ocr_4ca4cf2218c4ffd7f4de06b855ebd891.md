To create a forecast sheet, click the Time-series tab. Click inside the table. Then, from on the ribbon, select Data ▶ Forecast Sheet (from within the Forecast group). Take a look at Figure 8.55 to see what the Forecast Sheet looks like.

![](bbox=[0.135, 0.19, 0.385, 0.44])

Figure 8.55: The forecast sheet is found in the Forecast group on the Data ribbon tab.

Once clicked, Excel creates a preview fan chart with a few options (see Figure 8.56). To mimic our own analysis, I set Forecast End to 48. I clicked the Options drop-down to set a few more parameters. Go ahead and manually set the seasonality to 12 months and select Include forecast statistics so that we can get some of those stats we worked on by hand in this chapter. (Why isn't this checked by default?) Click Create when you're ready.

Once the sheet appears (see Figure 8.57), you can rename the tacky Sheet4 (or whatever it's named on your end) to Forecast Sheet.

Because of what you've learned in this chapter, you now have the skill to manipulate the forecast sheet. You might be wondering, as I was, what algorithm Excel uses for these forecasts. If you look at Excel's help on the forecast sheet, you'll see it uses a method called triple exponential smoothing. Perhaps you remember this is another name for the Holt-Winters algorithm.

If you made it through the entire chapter, bravo. Seriously, that's a lot of forecasting for one chapter.

I hope you now feel empowered to go forth and “organize your ignorance!”