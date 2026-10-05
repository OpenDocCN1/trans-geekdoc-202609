# 8.4.7 Poisson distribution (packet arrivals and traffic bursts)

```
$P(k\text{ packets in interval } t) = \frac{\lambda^k e^{-\lambda}}{k!} \quad (8.10)$
```

$\lambda$ is the average rate of packet arrivals (per second) and $k$ is the number of packets.

In the GA-RL combination, the Poisson distribution informs the RL agent about changes in traffic patterns (such as bursty traffic), triggering slice modifications. The RL agent monitors real-time traffic, adapting the slice's bandwidth and resource allocation based on the packet arrival rates. It minimizes over-provisioning and under-provisioning by dynamically adjusting slice capacity according to Poisson-modeled traffic arrivals.

# 8.4.8 Gaussian distribution (jitter and noise modeling)

Gaussian distributions are employed to model fluctuations (jitter) in network performance, such as delays due to queuing or packet loss caused by transient network issues.

```
$f(x\mu, \sigma^2) = \frac{1}{\sqrt{2\pi\sigma^2}} e^{\frac{(x-\mu)^2}{2\sigma^2}} \quad (8.11)$
```

where $\mu$ is the mean delay and $\sigma^2$ is the variance (jitter).

The RL agent uses Gaussian distribution to learn and predict jitter behavior in the network. The GA component can then optimize slice configurations by selecting parameters that minimize jitter, ensuring real-time communication in uRLLC (ultra-reliable low-latency communication) slices. A truncated Gaussian distribution is used in the GA to prioritize configurations that are more likely to meet KPI constraints, avoiding configurations that are highly unlikely to perform well.

The truncated Gaussian limits the range of potential values for a KPI (e.g., latency) that outliers are excluded:

```
$f(x) = \frac{1}{\sqrt{2\pi\sigma^2}} e^{\frac{(x-\mu)^2}{2\sigma^2}}, \ a \le x \le b \quad (8.12)$
```

where $a$ and $b$ are the lower and upper bounds based based on QoS constraints.