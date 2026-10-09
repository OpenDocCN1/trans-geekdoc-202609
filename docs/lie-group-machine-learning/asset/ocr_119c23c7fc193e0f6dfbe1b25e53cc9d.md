often in a partial order relationship, i.e., ‘before’. Further, [a<sub>i</sub>, a<sub>j</sub>] is called an interval and a<sub>i+1</sub> is the coverage of a<sub>i</sub>.

**Definition 2.10.** Let the LML sample data set $P$ be a partial set and $P'$ be a nonempty subset of $P$. Obviously, $P'$ for the partial order of $P$ is also a partial order, called a sub-partially ordered set of $P$.

A chain (i.e., a totally ordered set) that contains a limited number of elements is known as a finite chain; otherwise, it is known as an infinite chain.

If the sub-partially ordered set $S$ of a partially ordered set $P$ is a chain, $S$ is called a chain of $P$.

Let $P$ be a partially ordered set, $x$, $y \in P$, and $x < y$. If there exists $x = x_0$, $x_1$, …, $x_n = y$, make

$$x = x_0 < x_1 < x_2 < \dots \le x_n = y \tag{2.1}$$

where $x$ is called the starting point and $y$ is the ending point of the chain, referred to as $x$, $y$ chain, and $n$ is called its length.

If $x_i < \cdot x_{i+1}$, chain (2.1) is called the maximal chain of $x$, $y$. If

$$x = x'_0 < x'_1 < x'_2 < \dots < x'_m = y \tag{2.2}$$

is also a chain with $x$ as the starting point and $y$ as the ending point, and each $x_i$ ($1 \le i \le n$) appears in (2.2), then (2.2) is called the refinement of (2.1). Assuming that $x$ is the starting point and $y$ is the ending point, the chain with $y$ as the ending point can be refined into a maximal chain and the maximum value of the maximal chain with the starting point of $x$ and ending point of $y$ exists, and it is denoted by $d(x$, $y)$. Obviously, $d(x$, $x) = 0$. If a chain with $x$ as the starting point and $y$ as the ending point cannot be refined into a maximal chain, or the length of a maximal chain with $x$ as the starting point and $y$ as the ending point is without a maximum, define $d(x$, $y) = \infty$. If the chain with $x$ as the starting point and $y$ as the ending point can be refined into a maximal chain, and the maximum chain with $x$ as the starting point and $y$ as the ending point length is equal, make $l(x$, $y) = d(x$, $y)$, and call it ‘long’ from $x$ to $y$.

In the above-mentioned case of determining whether a dog is dangerous, $m_{321} < m_3 < P$ is the chain with the starting point as $m_{321}$ and the ending point as $P$, and it can be refined into $m_{321} < m_{32} < m_3 < P$.

In the learning problem, although the sample data are sometimes very large, the research object is often limited. Let $x$ ($x_0$) be the initial state of the sample, $x_1 \cdots x_{n-1}$ be the states generated during the learning process, $Y(x_n)$ be the target state, and $n$ be the generated orbital length. If the length of the orbit is used as a measure, (2.2) is superior to (2.1) in the form of orbital (2.1), thus take the price generated in each state as the standard, to compare the cost of both. $d(x$, $y)$ is the maximum possible length of the learning orbit.

**Definition 2.11.** The partial order $P$ is said to satisfy the Jordan–Dedekind condition, referred to as the $JD$ condition, if for any $a$, $b \in P$, and $a < b$, all great chains with $a$ as the starting point and $b$ as the ending point have the same limited length.