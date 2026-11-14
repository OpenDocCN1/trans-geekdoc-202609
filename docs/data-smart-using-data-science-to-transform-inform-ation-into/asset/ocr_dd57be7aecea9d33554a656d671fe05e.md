Now, this triangle is more generally called a *polytope*. A polytope is nothing more than a geometric shape with flat sides. You’ve probably heard the term *polygon*. Well, a polygon is just a polytope in a two-dimensional space. If you’ve got a big fat rock of an engagement ring on your hand.. . bam! That diamond is a polytope.

All linear programs can have their feasible solutions expressed as polytopes. Some algorithms, as you’ll see momentarily, exploit this fact to arrive quickly at solutions to linear programming problems.

It’s time to consider the second constraint—the cellar. If you produced only tools, you’d be able to pack about 42 of them in the cellar. On the other hand, you could shove 14 tons of butter in the cellar, max. So adding this constraint to the polytope, you shave off part of the feasible region, as shown in Figure 9.2.

![](bbox=[0.13, 0.345, 0.51, 0.645])

**Figure 9.2:** The cellar constraint cuts a chunk out of the feasible region.

# Solving by Sliding the Level Set

Now that you’ve determined the feasible region, you can begin to ask the question, “Where in that region is the best tools/butter mix?”

To answer that question, begin by defining something called the *level set*. A level set for your optimization model is a region in the polytope where all the points give *the same revenue*.

Because your revenue function is $150 * *Butter* + $195 * *Tools*, each level set can be defined by the line $150 * *Butter* + $195 * *Tools* = *C*, where *C* is a fixed amount of revenue.