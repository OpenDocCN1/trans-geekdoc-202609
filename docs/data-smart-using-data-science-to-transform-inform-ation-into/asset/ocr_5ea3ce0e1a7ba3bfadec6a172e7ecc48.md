![](bbox=[0.13, 0.1, 0.47, 0.26])

Figure 9.11: A graph of Pierre's $500 bonus

If you were to open Solver and use Simplex LP again to solve this problem, Excel would politely complain that “the linearity conditions required by this LP Solver are not satisfied.”

So we’ll give the evolutionary approach a shot here because it can better handle non-linearity. By now, you’ve seen this in action. But what that means in brief is that when modeling a linear program in Excel, you’re limited to things like the +/- signs, the SUM and AVERAGE formulas, and the SUMPRODUCT formula, where only one range contains decisions.

Though you have already seen this throughout the book, let’s reiterate here that there are a number of problems with the evolutionary solver:

+   - It gives no guarantees that it can find an optimal solution. All it does is keep track of the best solution in a population until time runs out, until the population hasn’t changed enough in a while to merit continuing, or until you kill Solver with the Esc key.
+   - The evolutionary solver can be quite slow. With complex feasible regions, it often barfs, unable to find even a good starting place.
+   - To get the evolutionary algorithm to work in Excel, you need to specify hard bounds for each decision variable. If you have a decision that’s more or less unbounded, you have to pick a really large number to bound it.

Concerning this last bullet point, for this example, you should add a constraint that both decisions must stay below 25, giving the new setup pictured in Figure 9.12.

Click OK and then Solve. The algorithm kicks off and should eventually find a solution of 6 tools and 9 tons of butter. So the evolutionary algorithm decided to take Pierre up on his $500 bonus. Nice! But notice that even on such a small problem, this took a while. Think about what that might mean for a production model.

OK, so that’s an imaginary problem. In the next section, I’m going to demonstrate the powers of Solver on something a bit... juicier. You’ll also spend time learning how to model