
### TCP Session Setup
### QUIC
### ICMP
### Final Thoughts
### Further Reading
### Review Questions

## Chapter 6: Interlayer Discovery
### Interlayer Discovery Solutions
### Well-Known and/or Manually Configured Identifiers
### Mapping Database and Protocol
### Advertising Identifier Mappings in a Protocol
### Calculating One Identifier from the Other
### Interlayer Discovery Examples
### The Domain Name System
### DHCP
### IPv4 Address Resolution Protocol
### IPv6 Neighbor Discovery
### The Default Gateway Problem
### Final Thoughts
### Further Reading
### Review Questions

## Chapter 7: Packet Switching
### Physical Media to Memory
### Processing the Packet
### Switching
### Routing
### Why Route?
### Equal Cost Multipath
### Packet Processing Engines
### Across the Bus
### Crossbars and Contention
### Memory to Physical Media
### Final Thoughts on Packet Switching
### Further Reading
### Review Questions

## Chapter 8: Quality of Service
### Defining the Problem Space
### Why Not Just Size Links Large Enough?
### Classification
### Preserving Classification
### The Unmarked Internet
### Congestion Management
### Timeliness: Low-Latency Queueing
### Fairness: Class-Based Weighted Fair Queueing
### Overcongestion
### Other QoS Congestion Management Tools
### Queue Management
### Managing a Full Buffer: Weighted Random Early Detection
### Managing Buffer Delay, Bufferbloat, and CoDel
### Final Thoughts on Quality of Service
### Further Reading
### Review Questions

## Chapter 9: Network Virtualization
### Understanding Virtual Networks
### Providing Ethernet Services over an IP Network
### Virtual Private Access to a Corporate Network
### A Summary of Virtualization Problems and Solutions
### Segment Routing
### Segment Routing with Multiprotocol Label Switching
### Segment Routing with IPv6
### Signaling Segment Routing Labels
### Software-Defined Wide Area Networks
### Complexity and Virtualization
### Interaction Surfaces and Shared Risk Link Groups
### Interaction Surfaces and Overlaid Control Planes
### Final Thoughts on Network Virtualization
### Further Reading
### Review Questions

## Chapter 10: Transport Security
### The Problem Space
### Validating Data
### Protecting Data from Being Examined
### Protecting User Privacy
### The Solution Space
### Encryption
### Key Exchange
### Cryptographic Hashes
### Obscuring User Information
### Transport Layer Security
### Final Thoughts on Transport Security
### Further Reading
### Review Questions

# Part II: The Control Plane

## Chapter 11: Topology Discovery
### Nodes, Edges, and Reachable Destinations
### Node
### Edge
### Reachable Destination
### Topology
### Learning about the Topology
### Detecting Other Network Devices
### Detecting Two-Way Connectivity
### Detecting the Maximum Transmission Unit
### Learning about Reachable Destinations
### Learning Reactively
### Learning Proactively
### Advertising Reachability and Topology
### Deciding When to Advertise Reachability and Topology
### Reactive Distribution of Reachability
### Proactive Distribution of Reachability
### Redistribution between Control Planes
### Redistribution and Metrics
### Redistribution and Routing Loops
### Final Thoughts on Topology Discovery
### Further Reading
### Review Questions

## Chapter 12: Unicast Loop-Free Paths (1)
### Which Path Is Loop Free?
### Trees
### Alternate Loop-Free Paths
### Waterfall (or Continental Divide) Model
### P/Q Space
### Remote Loop-Free Alternates
### Bellman-Ford Loop-Free Path Calculation
### Garcia’s Diffusing Update Algorithm
### Final Thoughts
### Further Reading
### Review Questions

## Chapter 13: Unicast Loop-Free Paths (2)
### Dijkstra’s Shortest Path First
### Partial and Incremental SPF
### Calculating LFAs and rLFAs
### Path Vector
### Disjoint Path Algorithms
### Two-Connected Networks
### Suurballe’s Disjoint Path Algorithm
### Maximally Redundant Trees
### Two-Way Connectivity
### Final Thoughts
### Further Reading
### Review Questions

## Chapter 14: Reacting to Topology Changes
### Detecting Topology Changes
### Polling to Detect Failures
### Event-Driven Failure Detection
### Comparing Event-Driven and Polling-Based Detection
### An Example: Bidirectional Forwarding Detection
### Change Distribution
### Flooding
### Hop by Hop
### A Centralized Store
### Consistency, Accessibility, and Partitionability
### Final Thoughts
### Further Reading
### Review Questions

## Chapter 15: Distance Vector Control Planes
### Control Plane Classification
### Spanning Tree Protocol
### Building a Loop-Free Tree
### Learning about Reachable Destinations
### Concluding Thoughts on the Spanning Tree Protocol
### The Routing Information Protocol
### Tying Bellman-Ford to RIP
