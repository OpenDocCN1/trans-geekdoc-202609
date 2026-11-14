Thus, we can update the Forecast column to the following:

```
=IF([@t] > $A$2,
[@[One-Step Forecast]] + [@[Forecast Error]],
NA()
)
```

| t | Demanc - Level | Trend | Seasonal Adju - | One-Step - | Forecast Error - | Actuals - | Forecast - | Squared Eri - |
|---|---|---|---|---|---|---|---|---|
| 50 | 34 | 218 | 224.512 | 2.503 | 1.016 | 232.685 | -14.685 | 218 | #N/A | 215.6501255 |
| 51 | 35 | 264 | 234.700 | 4.267 | 1.048 | 237.923 | 26.077 | 264 | #N/A | 679.9839116 |
| 52 | 36 | 304 | 243.145 | 5.226 | 1.204 | 287.718 | 16.282 | 304 | #N/A | 265.1017968 |
| 53 | 37 | 251.458 | 5.935 | 0.988 | 245.448305 | 9.875642399 | #N/A | 255.323947 | 0 |
| 54 | 38 | 256.651 | 5.765 | 1.039 | 267.548848 | -2.494521327 | #N/A | 265.054327 | 0 |
| 55 | 39 | 264.486 | 6.240 | 0.933 | 244.816232 | 6.252079665 | #N/A | 251.068311 | 0 |
| 56 | 40 | 271.252 | 6.361 | 0.913 | 247.063319 | 1.556768646 | #N/A | 248.620088 | 0 |
| 57 | 41 | 274.18 | 5.573 | 1.043 | 289.553225 | -11.59207144 | #N/A | 277.961153 | 0 |
| 58 | 42 | 280.134 | 5.660 | 0.906 | 253.579659 | 1.119993778 | #N/A | 254.699653 | 0 |
| 59 | 43 | 285.592 | 5.614 | 0.921 | 263.170373 | -0.602814274 | #N/A | 262.567558 | 0 |
| 60 | 44 | 293.847 | 6.220 | 0.927 | 269.837772 | 7.922013371 | #N/A | 277.759785 | 0 |
| 61 | 45 | 302.096 | 6.686 | 0.988 | 296.613466 | 6.494305285 | #N/A | 303.107771 | 0 |
| 62 | 46 | 308.293 | 6.574 | 1.016 | 313.784946 | -1.608114847 | #N/A | 312.176831 | 0 |
| 63 | 47 | 310.06 | 5.470 | 1.048 | 329.997285 | -16.31152035 | #N/A | 313.685764 | 0 |
| 64 | 48 | 314.753 | 5.292 | 1.204 | 379.899498 | -3.027479055 | #N/A | 376.872019 | 0 |

Figure 8.49: Simulated future demand

The columns autopopulates (see Figure 8.49).
Once you have that one scenario, by simply refreshing the sheet (press F9 for an auto
recalculation), the demand values change. So, you can generate multiple future demand
scenarios merely by copying and pasting one of the scenarios elsewhere and watching
the sheet refresh itself.

To start then, label cell A69 as Simulated Demand and label A70:L70 as months 37
through 48. Now, paste-special the transposition of the first demand scenario into A71:L71.
To insert a second scenario, simply right-click row 71 and select Insert to insert a new
blank row 71. Then paste-special some more demand values in from A70:L70 (they should
have updated when you pasted the last set).

You can just keep doing this operation to generate as many future demand scenarios
as you want. That's tedious, though. Instead, you can record a quick macro.
Just as you've done previously, record the following steps into a macro:

+   1. Insert a blank row 71.
+   2. Copy I53:I64.
+   3. Paste-special transposed values into row 71.
+   4. Press the Stop recording button.

Once you've recorded those keystrokes, you can hammer on whatever macro shortcut
key you selected over and over until you get a ton of scenarios. You can even hold the
shortcut key down—1,000 scenarios should do it. If the idea of holding a button down is
abhorrent to you, you can read up on how to put a loop in your macro code using Visual