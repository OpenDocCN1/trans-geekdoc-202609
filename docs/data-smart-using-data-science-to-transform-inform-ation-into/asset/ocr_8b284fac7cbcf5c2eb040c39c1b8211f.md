| | A | B | C | D | E |
|---|---|---|---|---|---|
| 1 | total cost objective | | | Cost Limit | Average % Relaxed |
| 2 | Total Costs | $1,300,723.32 | | $1,500,000.00 | 115.235% |

Figure 9.41: Solution to the robust optimization model

# AN EXERCISE FOR THE READER

If you're a glutton for pain, I'd like to offer one more formulation to work through. In the previous problem, you minimized the percent you had to lower and raised the quality bounds such that every constraint was satisfied. But what if you cared only that 95 percent of the scenarios were satisfied?

You would still minimize the quality relaxation percentage, but you'd need to stick an indicator variable on each scenario and use constraints to set it to 1 when the scenario's quality constraints were violated. The sum of these indicators could then be set ≤5 as a constraint.

Give it a shot. See if you can work it it.

If you stuck with me on those last couple models, then *bravo*. Those suckers weren't toy problems.

Your head is probably spinning with all sorts of applications of this stuff to your business right now. Or you've just downed a stiff drink and never want to deal with linear programming again. I hope it's the former, because the truth is, you can get incredibly creative and complex with linear programming. In many business contexts you'll often find models with tens of millions of decision variables.

Modeling linear programs, especially when you have to execute funky “squirrel removal” tricks, can be rather nonintuitive. The best way to get good at it is to find some opportunities in your own line of work that could use modeling and have at it. You can't memorize this stuff; you have to get a feel for how to address certain modeling peculiarities. And that comes with practice.