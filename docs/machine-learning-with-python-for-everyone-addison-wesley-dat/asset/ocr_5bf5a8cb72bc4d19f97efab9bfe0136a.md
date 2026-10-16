```
ax.plot(0, -3,'ro')  # y-intercept
ax.plot(2, 0,'ro');  # two steps to the right should be three whole steps up
```

![](bbox=[0.33, 0.26, 0.68, 0.5])

Here are the two forms we used in the code: ys = m*xs + b and ys = np.dot(xs_p1, w). Mathematically, these look like y = mx + b and y = wx⁺. Here, I'm using x⁺ as an abbreviation for the x that has ones tacked on to it. The two forms defining ys mean the same thing. They just have some differences when we implement them. The first form has each of the components standing on its own. The second form requires x⁺ to be augmented with a 1 and allows us to conveniently use the dot product.

# 2.6.2 Beyond Lines

We can extend the idea of lines in at least two ways. We can progress to wiggly curves and polynomials—equations like f(x) = x³ + x² + x + 1. Here, we have a more complex computation on one input value x. Or, we can go down the road to multiple dimensions: planes, hyperplanes, and beyond! For example, in f(x, y, z) = x + y + z we have multiple input values that we combine together. Since we will be very interested in multivariate data—that's multiple inputs—I'm going to jump right into that.

Let's revisit the rock concert scenario. What happens if we have more than one kind of item we want to purchase? For example, you might be surprised to learn that people like to consume beverages at concerts. Often, they like to consume what my mother affectionately refers to as “root beer.” So, what if we have a cost for parking, a cost for the tickets, and a cost for each root beer our group orders. To account for this, we need a new formula. With rb standing for root beer, we have:

total_cost = ticket_cost × number_people + rb_cost × number_rbs + parking_cost