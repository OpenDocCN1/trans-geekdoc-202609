
## 11.3.4 Testing and Evaluation Framework

This study makes a comparative analysis between the proposed EP-MCPHS and the Min-max fairness algorithm (MMFA). The MMFA was proposed in the base paper of EdgeSimPy architecture. The study performs an in-depth analysis of the bandwidth, latency, resource utilization, and data flow rate across both techniques. The study further compares the mean and standard deviation under statistical analysis to show the evaluation of the EP-MCPHS architecture to the baseline MMFA. The study provides a detailed discussion of how the reduction in data transfer and enhanced latency are the output of the incorporated minheap-based task priority system. It also compares the results in the upcoming section under the bar plots for intervals of 5, 10, 15, and 20-second cycles showcasing the sturdiness of the architecture across time ranges and upcoming cloudlets.

## 11.4 Results and Discussion

### 11.4.1 Evaluation Metrics

In this, we primarily compare the results among Start, End, Actual bandwidth and Data transfer. Let's discuss in detail on the meaning and utilization of these.

Start and End times showcase the actual lapse of time to process the cloudlets. The edge server tries to minimize the difference between these as much as possible. The actual bandwidth refers to the potential to cater to more services, which should be high as possible. This also showcases the low latency of the edge servers. Finally, the data flow is a paramount effect of having the most optimal cloudlet placed allowing for low data flow, accommodating high bandwidth and low latency for the algorithm.

### 11.4.2 Edge Servers

Edge server details showcase the instances, coordinates. CPU demand, RAM demand, disk demand, and services (Table 11.1). These will be used for the below-mentioned simulations.

### 11.4.3 Simulation Results

This section presents the results obtained by the comparison of simulation dataset 2 (Table 11.2). User data with the statistical measures of count, mean, standard deviation, minimum, 25% quartile, 50% quartile, 75% quartile, and maximum, these are calculated across time steps and serve instance ID.

Network flow using first come first serve showcases the statistical measures across time stamp, instance ID, start, end time, source, target, bandwidth, and data transfer rate (Table 11.3).

#### Table 11.1 Edge Server Details

| Time Step | Instance ID | Coordinates | CPU Demand | RAM Demand | Disk Demand | Services |
|---|---|---|---|---|---|---|
| 0 | 1 | [0, 0] | 0 | 0 | 0 | [] |
| 0 | 2 | [0, 2] | 0 | 0 | 0 | [] |
| 0 | 3 | [6, 0] | 0 | 0 | 0 | [] |
| 0 | 4 | [1, 3] | 0 | 0 | 0 | [] |
| 0 | 5 | [7, 1] | 1 | 1024 | 1017 | [] |
| 0 | 6 | [6, 2] | 0 | 0 | 0 | [] |
| 1 | 1 | [0, 0] | 6 | 12288 | 82 | [] |
| 1 | 2 | [0, 2] | 0 | 0 | 0 | [] |
| 1 | 3 | [6, 0] | 0 | 0 | 0 | [] |
| 1 | 4 | [1, 3] | 0 | 0 | 0 | [] |
| 1 | 5 | [7, 1] | 1 | 1024 | 1017 | [] |
| 1 | 6 | [6, 2] | 0 | 0 | 0 | [] |
| 2 | 1 | [0, 0] | 6 | 12288 | 82 | [1, 2] |
| 2 | 2 | [0, 2] | 0 | 0 | 0 | [] |
| 2 | 3 | [6, 0] | 0 | 0 | 0 | [] |
| 2 | 4 | [1, 3] | 0 | 0 | 0 | [] |
| 2 | 5 | [7, 1] | 1 | 1024 | 1017 | [] |
| 2 | 6 | [6, 2] | 0 | 0 | 0 | [] |
| 3 | 1 | [0, 0] | 6 | 12288 | 82 | [1, 2] |
| 3 | 2 | [0, 2] | 0 | 0 | 0 | [] |
| 3 | 3 | [6, 0] | 0 | 0 | 0 | [] |
| 3 | 4 | [1, 3] | 0 | 0 | 0 | [] |
| 3 | 5 | [7, 1] | 1 | 1024 | 1017 | [] |
| 3 | 6 | [6, 2] | 0 | 0 | 0 | [] |
| 4 | 1 | [0, 0] | 6 | 12288 | 82 | [1, 2] |
| 4 | 2 | [0, 2] | 0 | 0 | 0 | [] |
| 4 | 3 | [6, 0] | 0 | 0 | 0 | [] |
| 4 | 4 | [1, 3] | 0 | 0 | 0 | [] |
| 4 | 5 | [7, 1] | 1 | 1024 | 1017 | [] |
| 4 | 6 | [6, 2] | 0 | 0 | 0 | [] |
| 5 | 1 | [0, 0] | 6 | 12288 | 82 | [1, 2] |
| 5 | 2 | [0, 2] | 0 | 0 | 0 | [] |
| 5 | 3 | [6, 0] | 0 | 0 | 0 | [] |
| 5 | 4 | [1, 3] | 0 | 0 | 0 | [] |
| 5 | 5 | [7, 1] | 1 | 1024 | 1017 | [] |
| 5 | 6 | [6, 2] | 0 | 0 | 0 | [] |
| 6 | 1 | [0, 0] | 6 | 12288 | 82 | [1, 2] |
| 6 | 2 | [0, 2] | 0 | 0 | 0 | [] |
| 6 | 3 | [6, 0] | 0 | 0 | 0 | [] |
| 6 | 4 | [1, 3] | 0 | 0 | 0 | [] |
| 6 | 5 | [7, 1] | 1 | 1024 | 1017 | [] |
| 6 | 6 | [6, 2] | 0 | 0 | 0 | [] |
| 7 | 1 | [0, 0] | 6 | 12288 | 82 | [1, 2] |
| 7 | 2 | [0, 2] | 0 | 0 | 0 | [] |
| 7 | 3 | [6, 0] | 0 | 0 | 0 | [] |
| 7 | 4 | [1, 3] | 0 | 0 | 0 | [] |
| 7 | 5 | [7, 1] | 1 | 1024 | 1017 | [] |
| 7 | 6 | [6, 2] | 0 | 0 | 0 | [] |
| 8 | 1 | [0, 0] | 6 | 12288 | 82 | [1, 2, 3, 4, 5, 6] |
| 8 | 2 | [0, 2] | 0 | 0 | 0 | [] |
| 8 | 3 | [6, 0] | 0 | 0 | 0 | [] |
| 8 | 4 | [1, 3] | 0 | 0 | 0 | [] |
| 8 | 5 | [7, 1] | 1 | 1024 | 1017 | [] |
| 8 | 6 | [6, 2] | 0 | 0 | 0 | [] |

## Optimizing Edge and Fog Computing Applications with AI

#### Table 11.2 User Data

| Statistical Measure | Time Step | Instance ID |
|---|---|---|
| count | 54 | 54 |
| mean | 4 | 3.5 |
| std | 2.60623 | 1.72386 |
| min | 0 | 1 |
| 25% | 2 | 2 |
| 50% | 4 | 3.5 |
| 75% | 6 | 5 |
| max | 8 | 6 |

Similarly in Table 11.4 EP-MCPHS network flow showcases the network route changes in bandwidth, timestamp, and data transfer.

Table 11.5 makes a comparison of EP-MCPCHS and MMFA, showcasing that the proposed hybridized placement algorithm presents lower start time statistics across mean, standard deviation, 25%, 50%, and 75% scores. Similarly, the end time is reduced to 2.615 in comparison to 3.6 seconds. Further, the placement algorithm has a standard deviation of 0, meaning that most algorithms are placed in the first unit of time simulation. The utility of EPMCPCHS algorithm is the increase in bandwidth from 3.811828 in MMFA to 6.42851. The algorithm also reduces the inherent data transfer rate as the most optimal task in case of resources is running on the top edge server. Henceforth, smaller tasks need to be migrated. This is showcased by the parameter 4.91 in comparison to MMFA 6.53, well as the standard deviation of 7.54 during EP-MCPCHS 8.10. Figure 11.3 makes a comparison between EP-MCHS and MMFA, showing the start, end, and data transfer for the two algorithms. The figure shows improvement in the mean of start, end, and data transfer wherein increase of data transfer from 6.53 to 4.91 on EP-MCHS. Table 11.6 presents simulation analysis across time intervals. The concept of edge computing is gaining popularity as a paradigm that may provide applications with minimal latency by processing from typical cloud centers to the periphery. To ensure that edge computing goes from a promise to reality, it is necessary to create effective approaches for resource management because of potential advantages.

#### Table 11.3 Network Flow Using Max-Min Fairness

| Statistical Measure | Time Step | Instance ID | Start | End | Source | Target | Bandwidth | Data to Transfer |
|---|---|---|---|---|---|---|---|---|
| count | 31.000000 | 31.000000 | 15.000000 | 31.000000 | 31.000000 | 31.000000 | 31.000000 |
| mean | 4.612903 | 2.451613 | 1.225806 | 3.600000 | 5.0 | 1.0 | 3.811828 | 6.532258 |
| std | 2.275631 | 1.120676 | 0.425024 | 2.898275 | 0.0 | 1.511640 | 8.107522 |
| min | 1.000000 | 1.000000 | 1.000000 | 5.000000 | 1.0 | 0.000000 |
| 25% | 3.000000 | 1.500000 | 1.000000 | 5.000000 | 1.0 | 2.041667 | 0.000000 |
| 50% | 5.000000 | 2.000000 | 1.000000 | 5.000000 | 1.0 | 4.166667 | 1.875000 |
| 75% | 6.500000 | 3.000000 | 1.000000 | 6.500000 | 5.0 | 1.0 | 4.687500 | 12.875000 |
| max | 8.000000 | 4.000000 | 2.000000 | 7.000000 | 5.0 | 1.0 | 6.250000 | 23.75000 |

#### Table 11.4 EP-MCPHS Network Flow

| Time Step | Instance ID | Start | End | Source | Target | Bandwidth | Data to Transfer |
|---|---|---|---|---|---|---|---|
| count | 42.000000 | 42.000000 | 42.000000 | 26.000000 | 42.000000 | 42.000000 | 42.000000 | 42.000000 |
| mean | 3.500000 | 4.000000 | 1.0 | 2.615385 | 5.0 | 2.714286 | 6.428571 | 4.916667 |
| std | 1.728527 | 2.024243 | 0.0 | 1.626700 | 0.0 | 1.686181 | 3.857320 | 7.548959 |
| min | 1.000000 | 1.000000 | 1.0 | 1.000000 | 5.0 | 1.000000 | 2.000000 | 0.000000 |
| 25% | 2.000000 | 2.000000 | 1.0 | 1.000000 | 5.0 | 1.000000 | 2.000000 | 0.000000 |
| 50% | 3.500000 | 4.000000 | 1.0 | 3.000000 | 5.0 | 2.000000 | 6.250000 | 0.000000 |
| 75% | 5.000000 | 6.000000 | 1.0 | 4.000000 | 5.0 | 4.000000 | 6.250000 | 10.000000 |
| max | 6.000000 | 7.000000 | 1.0 | 5.000000 | 5.0 | 6.000000 | 12.500000 | 23.750000 |
