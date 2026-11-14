- inline mode: the traffic is directed towards the IPS in order to be analyzed.
The IPS blocks part of this traffic based on pre-configured parameters.

# 6.6. Types of alarms

Attacks on a network may generate four types of alarms, coded as follows:

| True positive | An alarm triggered by an intrusion that occurred and was detected
by the IPS. |
|---------------|------------------------------------------------------------|
| True negative | No intrusion took place and no action was taken by the IPS. |
| False positive | An alarm is triggered by normal traffic or an insignificant action. |
| False negative | No alarm was triggered when an intrusion took place. |

An administrator is required to ensure that the “false positive” alarms are
adjusted and that the “false negative” alarms are corrected.

NOTE.— You can now attempt Exercise 8.

# 6.7. Detecting malicious traffic

# 6.7.1. Modes of detection

An IPS may detect malicious traffic using several methods, including signature-
based detection, strategy-based detection, anomaly-based detection and
reputation-based detection.

# 6.7.2. Signature-based detection

# 6.7.2.1. Definition of a signature

A signature is a set of rules configured on an intrusion prevention system that
allows it to detect intrusions. Cisco has grouped together signatures with similar
characteristics into categories for easy management and analysis.