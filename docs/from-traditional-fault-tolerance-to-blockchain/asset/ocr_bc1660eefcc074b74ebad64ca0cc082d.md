# 3

# Recovery-Oriented Computing

Recovery-oriented computing was pioneered by a joint research project of Stanford University and the University of California, Berkerly [7] in early and mid 2000. The main focus of the research is to develop guidelines, methodologies, and tools to enable fast recovery for Internet-based servers. This research complements other research efforts that aim to extend the mean time to failure (MTTF) of the software systems, for example, by using replication to mask low-level failures. The rational is that, by reducing the mean time to recover (MTTR), the system availability can be improved as well due to the inverse relationship between the availability and the mean time to recover (i.e., Availability = MTTF / (MTTF+MTTR)).

The first step in achieving fast recovery is quick fault detection and localization. Fault detection means to determine if some component of a system has failed, and it may not pinpoint exactly which component has failed. Fault localization, on the other hand, is to find the exact component that has failed. While low level