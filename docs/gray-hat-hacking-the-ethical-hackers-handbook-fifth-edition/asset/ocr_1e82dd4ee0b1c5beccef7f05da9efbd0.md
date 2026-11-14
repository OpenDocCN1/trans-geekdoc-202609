![](bbox=[0.116, 0.083, 0.88, 0.49])

Figure 5-8 Measuring the symbols

+   - The smallest duration pulse is 272µs.
+   - The longest duration pulse is three times the smallest duration pulse.
+   - Four 272µs symbol periods occur between the beginning of one pulse and the beginning of the next pulse.

Now that we have what appears to be the symbol period, we should increase the number of symbols and see if we continue to line up with the edges of the dashes throughout the entire packet of data. Simply zoom out on the diagram and see where the last pulse aligns. In our case, we were slightly off, and I needed to stretch the period slightly such that the symbol period is 275µs instead of 272µs. This is not unexpected, considering that any errors in the initial measurement are multiplied by 100 in this case.

With the symbol rate and period confirmed, we can now extract the symbols and translate them into binary data. To accomplish this, we use the amplitude plot from the middle mouse. When the amplitude plot is added, a new bracket is added to the spectrum graph with three horizontal lines. The bracket must be aligned (centered) on the symbol data to get an amplitude plot of the symbol data on the newly added amplitude plot. In this case, when the brackets are centered over the symbol data and the Power Max/Min settings are reasonable, the plot begins to look like a square wave (see Figure 5-9). Once the square wave looks like a square wave, we use the middle mouse once again to extract the symbols