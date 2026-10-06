# Chapter 5 Bitcoin — A Deep Dive | 189

It determines the difficulty of finding a valid hash. It moves from left to right, reducing $T$ and increasing mining difficulty.$9$ The difficulty adjusts every 2,016 blocks (or approximately two weeks) according to the formula

```
$next\_diff=\frac{prev\_diff \times 2016 \times 10min}{time \ to mine \ last \ 2016 \ blocks}} \ (5.35)$
```

An astute reader should notice that this difficulty is similar to the one behind a centrifugal grower.$^{10}$

Since the difficulty goes up and down depending on the miners' (or, more precisely, mining pools') combined hash power, bitcoin should not be viewed as digital gold, as often claimed. The reason is apparent. On the one hand, if some miners decide to start working, bitcoins' production costs go down. On the other, if some gold mine operators decide to shut down, other operators' production costs will not go. No mechanism limits the bitcoin price in dollars from below, while the gold price in dollar terms is limited by the production costs.

Given bitcoin mining allure, the miners' collective hash rate grows exponentially. However, a 10-minute-per-block rule is preserved by increasing the difficulty to offset any gains in hash rate. The process is illustrated in Figure 5.26.

Figure 5.26(a) shows difficulty and hash rate as function of time, while Figure 5.26(b) demonstrates hash rate as a function of difficulty. A simple linear regression rules the following

```
$hash = p_1 \times difficulty + p_2,$
```

```
$p_1 = 7.257 \times 10^{-6}(7.222 \times 10^{-6}, 7.291 \times 10^{-6}), \quad (5.36)$
```

```
$p_2 = 1.859 \times 10^5(3.022 \times 10^4, 3.415 \times 10^5),$
```

with $R^2 = 0.9917$, which captures the something succinctly. The difficulty is a non-scaling parameter; the hash rate is measured in Terash per second (trillion hashes per second). Let's look at another measure, time-to-find-a-block. It fluctuates with difficulty, with stays between 2 and 12 minutes; see Figure 5.27.

Once a successful miner finds a winning nonce, she broadcasts it to the network, much like Alice broadcasts her desire to see some bitcoins to Bob. For the same reasons as, it takes time until the broadcast reaches intended recipients. Several groups delay the time distribution for the broadcast; e.g., Decker and Winterhofer (2013).

> “The nonzero part of $T$ is somewhat similar to the sliders rules for a good we eye-level physics scale.

> $10$Based on the principle of proportional control, a centrifugal governor is a feedback system that regulates the flow of steam to an engine. In the 17th century. In the 18th century, James Watt adopted one to regulate steam admission to his steam engine, controlling its rotational speed. A simple governor cannot maintain an exact speed; it needs a range instead. Mining difficulty adjustment, accommodating changes in the amount of hash power used by miners, plays the same role as a governor regulating a steam engine's operation. The principle is simple: hashing — greater difficulty, less hashing — lower difficulty.

![](bbox=[0.078, 0.946, 0.922, 0.966])