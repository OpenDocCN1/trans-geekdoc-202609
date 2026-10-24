works on mining network and graph data) but also provided a powerful *context* that links different types of data from different sources with different data mining algorithms. We refer to this phenomenon as *Network-of-X*, where different *X*s (i.e., entities, data sets or data mining models) are interconnected with each other by an underlying *contextual network*. In other words, each node of the underlying contextual network is associated with or mapped to an *X* representing an entity, a data set or a data mining model. In particular, when each *X* represents an entity (e.g., a user, a web page, a device, etc.), Network-of-X is simply equivalent to the typical network or graph data we have seen in Section 12.1.3. When each *X* represents an entire data set or a data mining model, we can leverage Network-of-X to enrich the modeling power and boost the mining performance in various real-world applications. Let us look at some examples, including network of time series, network of networks, and network of regression models.

**Network of time series.** A typical example of network of time series is the complex surveillance system as follows.

**Example 12.5.** A complex surveillance system to detect invasions is often integrated with the devices that monitor multiple types of signals, including ratio frequency and temperature. These devices are connected by a contextual sensor network, and generate specific coevolving time-series data to monitor abnormal activities. Fig. 12.9(a) shows an illustrative example. Nodes represent different devices that are connected by edges indicating the similarities or correlations among devices. Each device monitors

![](bbox=[0.12, 0.485, 0.39, 0.79])

![](bbox=[0.48, 0.485, 0.86, 0.79])

(a) Network of time series

(b) Network of networks

**FIGURE 12.9** Illustrative examples of network-of-X. (a) An example of a sensor network with nodes as time series of temperature (adapted from Cai et al. [CTF+ 15]). (b) An example of a research domain network with nodes as domain-specific collaboration networks.