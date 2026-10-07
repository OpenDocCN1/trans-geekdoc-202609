# Decision Making with Case-Based Learning

| Service | Technology | Location | Time | Throughput | Latency | Power | Dropped Calls | Blocked Calls |

**Figure 6.11** Case representation of the cognitive radio case-based decision maker for service selection.

taught or learned from experience over time. Experience can show that a given service is highly time- and location-dependent. Peak traffic times and poor signal quality can lead to more dropped calls, more blocked calls, and increased latency in the network.

The similarity is determined by the environment. The environment consists of time of day, day of the week, location, and available service providers. This is another multidimensional problem, the problem is to figure out how to combine the information to produce an understanding of the similarity. Service at the same time of day on a weekday in any city might have similar problems due to heavy network use. At other times, usage patterns can be specific to certain locations, such as the difference between urban and rural roads.

In our academic exercise here, have to recognize that this kind of similarity analysis is very difficult without surveying and modeling the influences of location and time. To simplify the scenario, we will break the concepts down to simple measurements of location in the form of longitude and latitude and time in the form of the time of day and day of the week. Further investigation could help tie in concepts like location diversity, as the difference between rural, suburban, and urban areas. The similarity function of (6.10) compares the time and location by calculating an error between the current location, $d(p)$, and the location of the case, $q$, in the case