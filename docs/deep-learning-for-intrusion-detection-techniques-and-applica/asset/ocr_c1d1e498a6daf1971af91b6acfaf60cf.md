# Table 6.2 Basic features of individual TCP connections.

| Feature name | Description | Type |
|---|---|---|
| duration | Length (number of seconds) of the connection | Continuous |
| protocol-type | Type of the protocol e.g., TCP, UDP, etc | Discrete |
| service | Network service on the destination e.g., http, telnet, etc. | Discrete |
| src-bytes | Number of data bytes from source to destination | Continuous |
| dst-bytes | Number of data bytes from destination to source | Continuous |
| Flag | Normal or error status of the connection | Discrete |
| Land | 1 if connection is from/to the same host/port, 0 otherwise | Discrete |
| wrong-fragment | Number of wrong fragments | Continuous |
| urgent | Number of urgent packets | Continuous |

(two seconds) to identify patterns related to protocol behavior and service use. Host-based traffic features, which examine connections to the same destination host over a larger window of 100 connections, address the needs of probing attacks that operate over extended intervals. Content-based features were also included to detect suspicious behaviors within the data portions of packets, such as failed login attempts, particularly useful for R2L and U2R attacks, which are often embedded in packet data rather than reflected in sequential patterns. Table 6.2 describes basic features of individual TCP connections, Table 6.3 describes **content features within a connection suggested by domain knowledge**, and Table 6.4 describes **traffic features computed using a two-second time window** of the KDDCUP dataset.

This comprehensive approach to feature engineering made the DARPA dataset and its derivatives a valuable resource for intrusion detection research. However, challenges remain, particularly in mining unstructured data portions of packets and identifying subtle patterns in complex attacks. These limitations highlight the ongoing need for innovation in algorithm development and feature extraction, ensuring that IDSs can keep pace with the ever-evolving landscape of cyber threats.

# 6.4.3 NSL-KDD

The NSL-KDD dataset [14] is an improved iteration of the KDD CUP 99 dataset, designed to address its shortcomings and serve as a more dependable benchmark for IDSs). In essence, researchers at the University of New Brunswick Canadian Institute for Cybersecurity removed redundant records from the original KDD-Cup99 dataset to create a more concise and efficient intrusion