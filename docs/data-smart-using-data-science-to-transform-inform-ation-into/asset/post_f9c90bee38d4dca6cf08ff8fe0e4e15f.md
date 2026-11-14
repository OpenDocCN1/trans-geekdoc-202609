

![](img/9c4b3d77873bec9e7da149a75c568d36_329_0.png)

Figure 9.11: A graph of Pierre's $500 bonus

If you were to open Solver and use Simplex LP again to solve this problem, Excel would politely complain that “the linearity conditions required by this LP Solver are not satisfied.”

So we’ll give the evolutionary approach a shot here because it can better handle non-linearity. By now, you’ve seen this in action. But what that means in brief is that when modeling a linear program in Excel, you’re limited to things like the +/- signs, the SUM and AVERAGE formulas, and the SUMPRODUCT formula, where only one range contains decisions.

Though you have already seen this throughout the book, let’s reiterate here that there are a number of problems with the evolutionary solver:

- It gives no guarantees that it can find an optimal solution. All it does is keep track of the best solution in a population until time runs out, until the population hasn’t changed enough in a while to merit continuing, or until you kill Solver with the Esc key.
- The evolutionary solver can be quite slow. With complex feasible regions, it often barfs, unable to find even a good starting place.
- To get the evolutionary algorithm to work in Excel, you need to specify hard bounds for each decision variable. If you have a decision that’s more or less unbounded, you have to pick a really large number to bound it.

Concerning this last bullet point, for this example, you should add a constraint that both decisions must stay below 25, giving the new setup pictured in Figure 9.12.

Click OK and then Solve. The algorithm kicks off and should eventually find a solution of 6 tools and 9 tons of butter. So the evolutionary algorithm decided to take Pierre up on his $500 bonus. Nice! But notice that even on such a small problem, this took a while. Think about what that might mean for a production model.

OK, so that’s an imaginary problem. In the next section, I’m going to demonstrate the powers of Solver on something a bit... juicier. You’ll also spend time learning how to model nonlinear functions (such as Pierre’s $500 bonus) in linear ways so that you can still use the fast Simplex LP algorithm.

![](img/9c4b3d77873bec9e7da149a75c568d36_330_0.png)

Figure 9.12: Formulation for the evolutionary solver

As you’ve gone through this book, you’ve been exposed to some interesting constraints required by Solver. For instance, we talked about the “Big M” constraint while clustering in graphs. In this chapter, we’ll zero in on these constraints and what they mean.

## Fresh from the Grove to Your Glass...with a Pit Stop Through a Blending Model

> **NOTE**
> 
> The Excel workbook used in this section OrangeJuiceBlending.xlsx is available for download at the book's website at www.wiley.com/go/datasmart2e.

Perhaps there came that day when you learned Santa Claus wasn’t real; that the “cracking” sound from your knuckles is gas, not bone; that your veins are blue because of light waves, not deoxygenation; and that we get colds when we’re inside, where it’s warm and moist—not because of wet hair exposed to chilly temperatures.

Well, today I’m going to burst another bubble. Your not-from-concentrate premium orange juice was not hand squeezed. In fact, the pulp in it is probably from different oranges than the juice, and the juice has been pulled from different vats and blended according to mathematical models to ensure that each sip tastes more or less the same as the last.

Consistent taste in OJ year round isn’t something that just anyone can pull off. Oranges aren’t always in season depending upon where you live. That means at different times of the year, different orange varietals are ripe. Pull fruit too early or too late and it tastes different. Moreover, across the world, fruit will taste just slightly different to the palette. Blame the soil composition, position relative to sun, and that little extra something that’s hard to describe (is it love?).

Consumers demand consistency. How do you get that out of a bunch of vats of freshly squeezed, very chilled orange juice? We’ll answer that question in this chapter.

By averaging the risk and return of an investment portfolio across multiple investments, the odds of you striking it rich probably decrease, but so do the odds of your going broke. This same approach applies to orange juice production today.

Juice can be procured from all around the world, from different oranges in different seasons. Each product has different specs—some might be a bit tarter, some a bit more astringent, and others might be sickly sweet. By blending this “portfolio” of juices, a single consistent taste can be maintained.

How do you build a blending model that reduces cost while maintaining quality, and what type of wrenches might get thrown into the works that would need to get mathematically formulated along the way?

**NOTE**
We won't be using Excel tables as we did in previous chapters. Because we aren't building models from raw data, we won't need the table structure.

**WARNING**
**Nonlinearity Warning When Using OpenSolver**
If you get a nonlinearity warning when using OpenSolver, don't worry. You just need to turn off the warning. Once your problem is set up, click the Data tab, select the Open-Solver Model drop-down, click Options, and then deselect the check box Perform A Quick Linearity Check On The Model. For more detailed instructions, see Chapter 1, “Everything You Ever Needed to Know About Spreadsheets but Were Too Afraid to Ask.”

## Let's Start with Some Specs

Let's say you’re an analyst working at JuiceLand and your boss, Mr. Juice R. Landingsly III has asked you to plan the procurement of juice from your suppliers for January, February, and March of this coming year. Along with this assignment, Mr. Landingsly hands you a sheet of specs from your suppliers containing the country of origin and varietal, the quantity available for purchase over the next three months, and the price and shipping cost per 1,000 gallons.

The specs sheet rates the color of the juice and three flavor components:

- **Brix/Acid ratio:** Brix is a measure of sweetness in the juice, so Brix/Acid ratio is a measure of sweetness to tartness, which, in the end, is really what orange juice is all about.
- **Acid (%):** Acid as a percentage of the juice is broken out individually, because at a certain point, it doesn’t really matter how sweet the juice is; it’s still too acidic.
- **Astringency (1–10 scale):** This is a measure of the “green” quality of the juice. It’s that bitter, unripe, plenty flavor that can creep in. This scale is assessed by a panel of tasters at each juicing facility on a scale of 1–10.

All of these specifications are represented in the specifications spreadsheet (the Specs worksheet tab in OrangeJuiceBlending.xlsx pictured in Figure 9.13.

| Varietal | Region | Qty Available (1,000 Gallons) | Brix / Acid Ratio | Acid (%) | Astringency (1-10 Scale) | Color (1-10 Scale) | Price (per 1K Gallons) | Shipping |
|---|---|---|---|---|---|---|---|---|
| Hamlin | Brazil | 672 | 10.5 | 0.60% | 3 | 3 | $500.00 | $100.00 |
| Mosambi | India | 400 | 6.5 | 1.40% | 7 | 1 | $310.00 | $150.00 |
| Valencia | Florida | 1200 | 12 | 0.95% | 3 | 3 | $750.00 | $0.00 |
| Hamlin | California | 168 | 11 | 1.00% | 3 | 5 | $600.00 | $60.00 |
| Gardner | Arizona | 84 | 12 | 0.70% | 1 | 5 | $600.00 | $75.00 |
| Sunstar | Texas | 210 | 10 | 0.70% | 1 | 5 | $625.00 | $50.00 |
| Jincheng | China | 588 | 9 | 1.35% | 7 | 3 | $440.00 | $120.00 |
| Berna | Spain | 168 | 15 | 1.10% | 4 | 8 | $600.00 | $110.00 |
| Verna | Mexico | 300 | 8 | 1.30% | 8 | 3 | $300.00 | $90.00 |
| Biondo Commune | Egypt | 210 | 13 | 1.30% | 3 | 5 | $460.00 | $130.00 |
| Belladonna | Italy | 180 | 14 | 0.50% | 3 | 9 | $505.00 | $115.00 |

Figure 9.13: The specs sheet for raw orange juice procurement

Whatever juice you choose to buy will be shipped to your blending facility in large, aseptic chilled tanks, either by cargo ship or by rail. That’s why there isn’t a shipping cost

