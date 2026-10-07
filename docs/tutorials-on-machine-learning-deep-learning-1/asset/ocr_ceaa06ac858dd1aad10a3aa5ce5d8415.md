We are creating an auxiliary mechanism for us to solve the problem. So we're not trying to recreate these machines we're
creating the possible way these machines could have been created.

For example consider the four-bloats; they are the possible position for the actual Blue-colored-vertical line or central
distribution. And based on those four values we constructed which will showing us possible positions
for that value; it shows the high likelihood or low likelihood for the position of the actual Blue-Vertical line. And same goes
for the Green and Orange distribution.

| Where we think the u^j values be |
| I. We are Not trying to guess the distributions behind the machines |

![](bbox=[0.153, 0.197, 0.843, 0.318])

Hence the Thompson Sampling is Kind of a Probabilistic algorithm. Upper-bound is a Deterministic Algorithm.

So in simple word, we've created our own Bandit-Configuration, where we know all the distribution. It is some kind of imaginary
distribution.

![](bbox=[0.153, 0.427, 0.843, 0.548])

| We've generated our one bandit configuration |

Now from above three points we choose the green one (because it lies in the right side of the imaginary central tendency.
hence may give positive result); According to our own Bandit-Configuration; we generate a value and we compare the value
with the value generated in the real world. Then our sample grows and we make correction to our own version of distribution.

![](bbox=[0.153, 0.648, 0.843, 0.769])

So our green version shifted a little bit and got narrow (because sample is increased) and increased little higher. These happens
because our real world value lies in the left side of the imaginary central tendency, i.e. we get the wrong expected value in
our imaginary distribution (however we were lucky to get positive value in real world). Hence we shifted the imaginary
distribution to the left. Since the sample grows bigger the distribution narrowed and grows higher.

![](bbox=[0.153, 0.83, 0.843, 0.951])

That's the point that every time we add New INFORMATION our distribution becomes more and more REFINED.