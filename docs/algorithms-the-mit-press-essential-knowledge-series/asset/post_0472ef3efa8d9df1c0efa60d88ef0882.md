
start on the third, fourth, and fifth onset, other popular rhythms around the world emerge.

Is this just a one-off thing? We can try to create a 12-part rhythm out of seven onsets and five silent parts—kind of mirroring the five onsets and seven silent parts that we had before. If we follow exactly the same procedure, we will arrive at:

× • × • × • × × • •

This, again, is a rhythm. It is used in the Mpre rhythm of the Ashanti in Ghana, and if we start it on the last onset, it is used by the Yoruba in Nigeria as well as in Central Africa and Sierra Leone.

Lest you think we have geographic omissions, if we start with five beats and 11 silent parts, we arrive at the following:

× • × • × • × • • • •

That is the Bossa-Nova rhythm, rotated. The actual Bossa-Nova rhythm starts on the third onset, so the exact correspondence is:

![](img/9d8f96a7d5ef19b95ffbdc3918c1b6f3_35_0.png)

× × • • • × • • × •

If we try with three beats and four silent parts, we get the pattern:

× • × • × •

This rhythm in a seven/four meter is popular, and not just in traditional music. Among other tunes, it is the rhythmic pattern of Pink Floyd’s song “Money”:

![](img/9d8f96a7d5ef19b95ffbdc3918c1b6f3_36_0.png)

× • × • × •

Many more rhythms can be derived in this way by putting crosses and bullets in columns, and moving them around in the way we just described. We illustrated the procedure by measuring remainder columns a pictorial way of showing what really happens. Instead of creating columns, checking the geometry, and moving them around, we can do the same thing more formally with simple numerical operations. To see what, let’s return to the example of 12 parts and seven onsets. We start by dividing 12 by 7, which gives us quotient 1 and remainder 5:

12 = 1×7 + 5

This tells us to put the seven onsets in the beginning, creating seven columns of onsets, followed by a remainder of the five uncounted parts:

× × × × × × • • • •

Now we divide again, but this time we divide the divisor of the previous division, 7, by the remainder of the previous division, 5. This gives us a quotient of 1 again while the remainder is 2:

7 = 1×5 + 2

This means that we need to take the five rightmost columns and place them under the five leftmost columns, leaving a remainder of 2:

× × × × × × • • • •

We repeat the same step: we divide the divisor of the previous division, 5, by the remainder of the previous division, 2. The quotient is 2 and the remainder is 1:

5 = 2×2 + 1

This tells us to take *twice* the two rightmost columns and place them under the two leftmost columns, leaving a remainder of 1:

$\times$ $\times$ $\times$
$\cdot$ $\cdot$ $\cdot$
$\times$ $\times$
$\times$ $\times$
$\cdot$ $\cdot$

Note that *twice* means that this is equivalent to what we would be doing in two steps if we had worked as we were doing before, without using the division. We would go from:

$\times$ $\times$ $\times$ $\times$ $\times$ $\times$
$\cdot$ $\cdot$ $\cdot$ $\cdot$ $\cdot$ $\cdot$

first to:

$\times$ $\times$ $\times$ $\times$ $\times$
$\cdot$ $\cdot$ $\cdot$ $\cdot$ $\cdot$
$\times$ $\times$

and then to to:

If we concatenate the columns, we get the Mpre rhythm:

# Our First Algorithm

We can write down the method we followed in a bit more precise terms as the following steps. We assume that we start with two numbers, $a$ and $b$. We let $a$ be the total number of parts. If the number of onsets $a$ is greater than the number of the silent parts, then $b$ is the number of onsets. Otherwise it is the number of the silent parts. At the beginning, we create a row with the onsets followed by the silent parts.

1. Perform the division of $a$ by $b$. This will give us a quotient and remainder. If we call the quotient $q$ and remainder $r$, we'll have $a = q \times b + r$. This is integer division as we know it. We take $q$ times the rightmost $b$ columns and move them under the leftmost columns, leaving a remainder of $r$ columns on the right.

2. If the remainder $r$ is equal to zero or one, we stop. Otherwise, we go back to step 1, but this time $b$ will be the new $a$ and $r$ will be the new $b$. Or in other words, we go back to step 1, setting $a$ equal to $b$ and $b$ equal to $r$.

In two steps we perform a division repeatedly, until it does not make sense to repeat it. You can trace the steps in the following table, where we start with $a = 12$ and $b = 7$, like we did before; in each row we have $a = q \times b + r$:

| | q | b | r |
|---|---|---|---|
| 12 | 1 | 7 | 5 |
| 7 | 1 | 5 | 2 |
| 5 | 2 | 2 | 1 |

If you examine the table, you can verify that each row corresponds to one step of the column formation and moving, but we have a more precise definition of the method we used. In fact, we have a series of steps that we can perform with pen and paper, so this is our first algorithm! We have an algorithm for creating patterns that correspond to many, and indeed surprisingly many, musical rhythms. Working with different numbers of offsets and silent parts, we can get about 40 rhythmic patterns that are found in different rhythms around the world. That should give us pause for a minute: it is a simple algorithm (only two steps, repeated) and yet able to produce so many interesting results.

Our algorithm does more than that, though. As we are talking about the division of two numbers, let us consider the following general problem: If we have two numbers $a$ and $b$, what is the greatest number that divides them both? This is called the greatest common divisor, or $gcd$, of the two numbers. We encounter the greatest common divisor in elementary arithmetic, in problems such as, If we have 12 packets of crackers and four packets of cheese, how will you distribute them in baskets so that you have the same proportion of crackers and cheese in each basket? As four divides 12, you will have four baskets, each containing three packets of crackers and one packet of cheese; the greatest common divisor of 12 and four is four. Things get more interesting if you have 12 packets of crackers and eight packets of cheese. You cannot divide one by the other, but the greatest number that divides 12 and eight is four, which means that you will make again baskets, each containing three packets of crackers and two packets of cheese.

So how can we find the greatest common divisor of any two integer numbers? We have seen that the greatest common divisor of two numbers is the same as the greatest common divisor of the smaller number and the remainder when the larger is divided by the smaller. This is called Euclid's algorithm, in honor of Euclid, ancient Greek mathematician who first described it in his books (ca. 300 BCE). The basic idea is to replace the larger number with its difference with the smaller number. Try 56 and 24: $56 - 24 = 32$, so we go to 32 and 24, and $32 - 24 = 8$, so we go to 24 and 8. Since $24 = 3 \times 8 + 0$, the greatest common divisor of 56 and 24 is 8. Try 9 and 5: $9 = 1 \times 5 + 4$, so we go to $5 = 1 \times 4 + 1$ and then $4 = 1 \times 4 + 0$, so the greatest common divisor of 9 and 5 is 1.

It may help you to see the algorithm in action with $a = 136$ and $b = 56$ in the following table, similar to the one we saw before with our rhythms. We find that the greatest common divisor of 136 and 56 is the number 8:

| $a$ | $q$ | $b$ | $r$ |
|---|---|---|---|
| 136 | 2 | 56 | 24 |
| 56 | 2 | 24 | 8 |
| 24 | 3 | 8 | 0 |

As we noted with 9 and 5, Euclid’s algorithm works correctly in all cases, even when the two numbers do not
