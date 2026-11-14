Disadvantages:

+   - the strategy must be manually created;

+   - difficult to apply in the case of large networks.

# ## 6.7.3.2. Anomaly-based detection

The IPS generally looks for network traffic that deviates from the norm. A statistical reference must be developed to define the normal behavior of network traffic.

Advantage: can detect new types of attacks.

Disadvantages:

+   - difficult to accurately standardize the traffic on extremely large networks;

+   - may cause “false positive” alarms if valid network traffic changes significantly.

# ## 6.7.3.3. Reputation-based detection

Cisco Global Correlation is a feature that allows Cisco IPS detectors to filter network traffic using the “reputation” of the source IP address of a packet.

The reputation of an IP address, among other elements, is computed by the “Cisco SensorBase” service, specialized in this domain, based on this IP address’ previous actions. This information is gathered from the flows of over 1.5 million Cisco IPS detectors and firewalls, among other devices, deployed worldwide. This feature supplies the network with valuable information that helps in detecting, preventing and reacting to recently–detected threats.

Advantages:

+   - makes use of the experience of other existing security systems;

+   - considered to be an early-warning system.

Disadvantage: requires continuous updates.

# ## 6.8. Signature micro-engines

A signature micro-engine is a component in an IPS (or IDS) detector that supports a particular category of signatures. All signatures from a signature micro-engine are scanned in parallel, which increases the efficiency and fluidity of the data.