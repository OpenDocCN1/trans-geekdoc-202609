So, \(\frac{\partial S(i)}{\partial(a_i)}\) can be given as follows:

\(\frac{\partial S(i)}{\partial(a_i)} = \left[ \begin{matrix} \frac{\partial S(i1)}{\partial a(i1)} & \frac{\partial S(i2)}{\partial a(i1)} & \frac{\partial S(i3)}{\partial a(i1)} & ..... \\ \frac{\partial S(i1)}{\partial a(i2)} & \frac{\partial S(i2)}{\partial a(i2)} & \frac{\partial S(i3)}{\partial a(i2)} & ..... \\ ..... & ..... & ..... & \\ ..... & ..... & ..... & \frac{\partial S(id)}{\partial a(id)} \end{matrix} \right]\)

The preceding matrix can be written as follows:

\(\frac{\partial S(i)}{\partial(a_i)} = \left[ \begin{matrix} \sigma'(a(i1)) & 0 & 0 & 0 \\ 0 & \sigma'(a(i2)) & 0 & 0 \\ 0 & 0 & ..... & ..... \\ 0 & 0 & ..... & \sigma'(a(id)) \end{matrix} \right]\)

The preceding matrix can also be written as follows:

\(\frac{\partial S(i)}{\partial(a_i)} = diagonal(\sigma'(a(i)))\)

And

\(\frac{\partial(a_i)}{\partial S(i - 1)} = W\)

Therefore, we can write

\(\frac{\partial S(i)}{\partial S(i - 1)} = diagonal \left( \sigma'(a(i)) \right).W\)

So, the magnitude of the preceding equation can be written as follows:

\(\left\| \frac{\partial S(i)}{\partial S(i - 1)} \right\| = \left\| diagonal \left( \sigma'(a(i)) \right).W \right\|\)

Now, we know that if ||z|| = ||xy|| then, we can write as ||z|| <= ||x||. ||y||

Therefore, we can write

\(\left\| \frac{\partial S(i)}{\partial S(i - 1)} \right\| \leq \left\| diagonal \left( \sigma'(a(i)) \right) \right\| . \|W\|\)

Now, we know that as we are using the logistic activation function, therefore we can say that \(\partial(a_i)\) is a bounded function, and hence, \(\sigma'(a(i))\) is also bounded here.