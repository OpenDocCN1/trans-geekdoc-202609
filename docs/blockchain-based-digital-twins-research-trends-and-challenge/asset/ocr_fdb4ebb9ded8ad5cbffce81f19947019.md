by edge computing devices that act as aggregators. The aggregator computes the aggregate representation of all the virtual entities. These aggregates are grouped based on the parts to which they belong. Depending on the block size, either a separate block for each part can be created, or aggregates of multiple parts can be stored in a single block along with part identification and time. This information helps to track the status of machine parts at different times. The possible aggregate functions are SUMMATION, AVERAGE, COUNT, MAXIMUM, or MINIMUM. The description of the aggregation function is provided in Table 10.1. Depending on the kind of virtual entity and the parts to which it belongs, different aggregation functions can be applied. Hence, information regarding the kind of aggregate function has to be stored along with the aggregate. Figure 10.7 exhibits the structure of data which describes the state of a machine part to be stored in the chain block. Let the values that occurred during the particular time intervals be $v_{1},v_{2},...v_{j}$.

# TABLE 10.1 Aggregation function

| Aggregate Function | Description |
|---|---|
| SUMMATION | $\sum_{i=1}^{n} v_{i}$ |
| AVERAGE | $\frac{\sum_{i=1}^{j} v_{i}}{j}$ |
| MAXIMUM | maximum $(V_{1},V_{2},...,V_{j})$ |
| MINIMUM | mininmum $(V_{1},V_{2},...,V_{j})$ |
| COUNT | 'j' |