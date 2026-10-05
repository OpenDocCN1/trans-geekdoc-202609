# Intrusion Detection System

# 125

Complex Environment for Security
Analysts include many tools but SIEM
is the primary tool that security teams use.

Growing Need to use Big Data - SIEM\oes not natively support custom ML model
development and forces exports of large
amount of data which is not often enough or
feasible due to performance challenges.

SIEM is overwhelmed with use cases
that are beyond the scope for its original
purpose. This is making it an ineffective
Operational Security Tool.

Lack of Grained Controls for
Retention - attempts to address the
regulatory requirements for
retention of the evidence data are
very insufficient.

![](bbox=[0.338, 0.105, 0.638, 0.365])

Storage Tiering in SIEM is optimized
for searches over shorter data history (30
days). The searches become too long
To execute.

Lack of Data Governance Controls
dplicated data inside SIEM. No console
naming standard; SIEM's security model does
not map to Adobe's needs.

Competing workloads in SIEM
imp each other; On-prem limited
shared infrastructure and SIEM's internal
workload solution flat when addressing
this.

Poor visibility inside SIEM cost for
Security's usage.

**FIGURE 7.2** Security needs a big data platform separate from traditional SIEM to correlate
security events in IDS.

# 7.4 MACHINE LEARNING

Computer science is the discipline of machine learning. This is a part of artificial
intelligence enables computer systems to discover patterns within information.
Programs that really can draw from information and make forecasts about it are
invest by machine learning [46]. Such methods are termed machine learning
procedures. We use data to create projections, a machine learning system must first
train. The program must be taught by exposing to numerous data samples and
the appropriate projections for each case.

The method must be deployed anywhere from a few thousand to a hundred
thousand instances. Once algorithms for machine learning have gained information
from the data, it may be applied to other information to make forecasts.
instance, machine learning could be applied to monitor a hospital patient's pulse
rate [47]. The patient's heartbeat and timestamp are displayed in the machine-
learning model during the training phase. That machine learning system can fore-
cast patient's expected heartbeat depending on the present time once learning
is complete. Contrasting the anticipated heartbeat with the actual pulse rate, this
Medical Interoperability Gateway (MIG) is used to evaluate whether the patient's
heartbeat is healthy.

+   **Evaluating ML for an IDS:** The F-score can be combined with the machine
learning system to gauge accomplishment [48]. This, though, is insufficient
s own for intrusion detection all on their own. The F-scores for accu-
acy recall are equally important. While analyzing intrusion detection
systems, this isn't always the situation. When a study population is labeled as