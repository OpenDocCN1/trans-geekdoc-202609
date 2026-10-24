

As shown in the above example, it is impossible to ensure that loyal generals reach the same decision if there are only 3 generals total and one of them might be traitorous. This observation can be generalized for the case when more than one general is traitorous. Let $f$ be the number of traitorous generals we want to tolerate. By having each general in the 3-general example simulate $f$ generals, it is easy to see that there is no solution if we use only $3f$ total number of generals. Therefore, the optimal number of generals needed to tolerate $f$ traitorous generals is $3f + 1$.

### 7.1.2 The Oral Message Algorithms

A solution to the Byzantine generals problem is the Oral Message algorithms [26]. The oral message algorithms are defined inductively. The solution starts by running an instance of the Oral Message algorithms $OM(f)$ with $n$ generals, where $f$ is the number of traitors tolerated, and $n \ge 3f + 1$. One of the generals is designated as the commander and the remaining generals are lieutenants. Each general is assigned an integer id, with the commander assigned 0, and the lieutenants assigned $1,...,n-1$, respectively.

$OM(f)$ would trigger $n-1$ instances of the $OM(f-1)$ algorithm (one per lieutenant), and each instance of the $OM(f-1)$ algorithm involves $n-1$ generals (i.e., all the lieutenants). Each instance of $OM(f-1)$ would in turn triggers $n-2$ instances of the $OM(f-2)$ algorithm (each involves $n-2$ generals), until the base case $OM(0)$ is reached (each $OM(0)$ instance involves $n-f$ generals).

Because of the recursive nature of the Oral Message algorithms, a lieutenant for $OM(f)$ would serve as the commander for $OM(f-1)$, and so on. Each lieutenant $i$ uses a scalar variable $v_i$ to store the decision value received from the commander, where $i$ is an integer ranges from $1$ to $n-1$. Furthermore, a lieutenant also uses a variable $v_j$ to store the value received from lieutenant $j$ ($j \neq i$).

### Algorithm $OM(0)$:

- 1. The commander multicasts a message containing a decision (for wider applicability of the solution, the decision could be any value) to all the lieutenants in the current instance of the algorithm.
- 2. For each $i$, lieutenant $i$ set $v_i$ to the value received from the commander. If it does not receive any value from the commander, it defaults to a predefined decision (such as “retreat”).

### Algorithm OM(f):

- 1. The commander multicasts a decision to all the lieutenants in the current instance of the algorithm.
- 2. For each $i$, lieutenant $i$ sets $v_i$ to the value received from the commander. If it does not receive any value from the commander, it defaults to a predefined decision. Subsequently, lieutenant $i$ launches an instance of the $OM(f-1)$ algorithm by acting as the commander for $OM(f-1)$. The $n-1$ generals involved in the instance of the $OM(f-1)$ algorithm consists of all lieutenants in the $OM(f)$ instance.
- 3. For each $i$ and $j \neq i$, lieutenant $i$ sets $v_j$ to the value received from lieutenant $j \neq i$ in step (2). If it does not receive any value from lieutenant $j$, it sets $v_j$ to the predefined default value. When all instances of the $OM(f-1)$ algorithm have been completed, lieutenant $i$ chooses the value returned by the majority function on the set $[v_1, \dots, v_{n-1}]$.

Before further discussion on the OM algorithms, we need to define a notation for the messages in the algorithms. Due to the recursive nature of the OM algorithms, a general may receive multiple messages that belong to different recursion levels. To distinguish these messages and to identify the recursion level in which a message belongs, we denote a message received at a lieutenant $i$ at recursion level $k$ as $M_i^{s_0,\dots,s_k}$, where $k$ ranges from $0$ to $f$, and $s_0, \dots, s_k$ records the hierarchy of the set of OM algorithms from recursion level $0$ to the level $k$, i.e., the commander $s_0$ initiates the $OM(f)$ algorithm, lieutenant $s_1$ then invokes an instance of the $OM(f-1)$ algorithm upon receiving the message sent by the commander, and at the lowest recursion level lieutenant $s_k$ invokes an instance of the $OM(f-k)$ algorithm. We may also denote the receiver id because a traitorous general might send conflicting messages to different lieutenants.

### EXAMPLE 7.2

In this example, we show how the Oral Message algorithms work with $f=1$ and $n=4$. The basic steps and the message flow of the $OM(1)$ algorithms are shown in Figure 7.2. In the first step, the commander, $G_0$, multicasts a message to the three lieutenants, $G_1$, $G_2$, and $G_3$. In step 2, upon receiving a message $M_i^0$ from the commander, lieutenant $i$ invokes an instance of the $OM(0)$ algorithm and multicasts a message $M^{0i}$ to all other lieutenants. Because there are 3 lieutenants, three instances of the $OM(0)$ algorithm are launched.

![](img/7320b1480d74f1d65f74659cab456782_283_0.png)

Figure 7.2 The message flow and the basic steps of the $OM(1)$ algorithms.

In step 3, each lieutenant calculates the final decision based on the three messages it has received, one message from the commander in $OM(1)$, and two messages in the two instances of the $OM(0)$ algorithm. More specifically, lieutenant 1 ($G_1$) receives $M_1^0, M_1^{02}, M_1^{03}$, lieutenant 2 ($G_2$) receives $M_2^0, M_1^{01}, M_1^{03}$, and lieutenant 3 ($G_3$) receives $M_3^0, M_3^{01}, M_3^{02}$.

We consider two cases. In the first case, $G_0$ is a traitor and it sends different values to the three lieutenants, i.e., $M_1^0 = x, M_2^0 = y, M_3^0 = z$, where $x \neq y \neq z$. All three lieutenants are loyal, hence, $M_1^{01} = M_1^{01} = x, M_1^{02} = M_3^{02} = y$, and $M_1^{03} = M_2^{03} = z$. Therefore, G1's decision is $majority(x, y, z)$, G2's decision is also $majority(x, y, z)$, and the same is true for G3. G1, G2, and G3 all uses the predefined default decision.

In the second case, let $G_1$ be the traitor ($G_0$ then must be loyal) and the messages it sends to $G_2$ and $G_3$ contain different values ($x$ and $y$). Hence, $M_1^0 = M_2^0 = M_3^0 = v, M_2^{01} = x, M_3^{01} = y, M_1^{02} = M_3^{02} = v$, and $M_1^{03} = M_2^{03} = v$. Therefore, G2's decision is $majority(x, v, v) = v$, and G3's decision is $majority(x, v, v) = v$.

| | Messages Collected | Case 1: G0 Traitor | Case 2: G1 Traitor |
|---|---|---|---|
| G1 | \(M_1^0, M_1^{02}, M_1^{03}\) | \(majority(x, y, z)=\text{"Retreat"}\) | n/a |
| G2 | \(M_2^{01}, M_2^0, M_2^{03}\) | \(majority(x, y, z)=\text{"Retreat"}\) | \(majority(x, v, v) = v\) |
| G3 | \(M_3^{01}, M_3^{02}, M_3^0\) | \(majority(x, y, z)=\text{"Retreat"}\) | \(majority(y, v, v) = v\) |

Table 7.1 Messages received and final decisions in two cases for OM(1/4).

For clarity, the results for these two cases are summarized in Table 7.1.

As can be seen in Example 7.2, the algorithm descriptions for the \(OM\) algorithms are very clear when applied to the \(f=1\) case. It is apparent that the step (3) in the \(OM(f)\) algorithm is expressed implicitly for \(f=1\) (for only two levels of recursion). If 3 or more recursion levels are involved (\(i.e., f \ge 2\)), the rules outlined for step (3) have the following two issues:

- 1. A lieutenant \(i\) would receive more than one message from each \(j \neq i\) in step (2). In fact, for an integer \(k\) between 1 and \(f\) inclusive, there will be \((n-1)\cdots(n-k)\) instances of the $OM(f-k)$ algorithm executed. Hence, there will be $1 + (\sum_{k=2}^f (n-1)\cdots(n-k+1) - 1)$ such messages for each $j$. It is vague as to exactly which value lieutenant $i$ should set for $v_j$.
- 2. For an intermediate instance of the algorithm, $OM(f-k)$, where $1 \le k < f$, it is unclear what it means by choosing a decision based on the majority function, and especially what the implication is for this operation on the enclosing instance of the $OM$ algorithm.

We can augment the rules for step (3) in the following ways:

- We start by proposing a fix to issue 2. At lieutenant $i$, in step (3) of the $OM(f-k)$ instance started by lieutenant $j \neq i$, $v_j$ is set to the value returned by the majority function. This is what means by choosing the decision stated in the original rule.
- Except for $OM(1)$ and $OM(0)$, a lieutenant only sets the $v$ variable corresponding to itself based on the message received from its commander (there is only one such
