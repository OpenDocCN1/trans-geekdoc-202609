# Solution

The system can be described as follows:

+   1. The interval arrival times are exponentially distributed.

+   2. The services times follow a general probability distribution.

+   3. There are five servers.

+   4. The buffer size of the queue is 20.

+   5. The population of customers to be served is 100; that is, only 100 customers occupy this queue.

+   6. The service discipline is first come, first served.

# 2.16 LITTLE'S THEOREM

To obtain the waiting or queuing time, we apply a useful result, known as Little's theorem, after the author of the first formal proof in 1961. The theorem relates the mean number of customers in a queue to the mean arrival rate and the mean waiting time. It states that a queuing system, with average arrival rate $\lambda$ and mean waiting time per customer $E(W)$, has a mean number of customers in the queue (or average queue length) $E(N_q)$ given

```
$E(N_q) = \lambda E(W) \quad (2.119)$
```

The theorem is very general and applies to all kinds of queuing systems. It assumes that the system is in a statistical equilibrium or steady state, meaning that the probabilities of the system being in a particular state have settled down and are not changing with time.

It should be noted that Equation (2.119) is valid irrespective of the operating policies of the queuing system. For example, it holds for an arbitrary number of queues and servers. It also applies to a single queue, excluding the server.

The graphical proof of the theorem will be given here. Suppose we keep track of arrival and departure times of individual customers for a long time $t_a$. If $t_a$ is large, the number of arrivals would approximately equal to the number of departures. If this number is $N_a$, then