| user_id | time | level |
| --- | --- | --- |
| 10 | 10:01 | Normal |
| 10 | 11:11 | Warning |
| 10 | 11:13 | Normal |
| 163 | 09:27 | Error |
| 400 | 08:00 | Normal |

![](bbox=[0.178, 0.115, 0.858, 0.439])

**Figure 19.1:** Components of a primary in Cassandra.

In this example with two nodes (Node A and Node B), we assume entries for user 10 are stored in Node A while users 163 and 400 go to Node B. Cassandra uses the partition key to compute a hash