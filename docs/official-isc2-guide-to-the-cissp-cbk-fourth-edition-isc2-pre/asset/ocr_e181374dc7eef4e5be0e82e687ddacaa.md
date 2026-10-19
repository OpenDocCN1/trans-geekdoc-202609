warm spares because they are powered up and will wear down like any powered equipment.

These are some of the reasons why most facilities do not rely solely on redundant components but make use of redundant systems instead. In a typical redundant configuration such as an active–passive pair, the primary system will provide all services while the passive system monitors the primary for any problems. If the primary fails for some reason, the secondary system can take over. Ideally, this means that there is little or no disruption in service caused by system failure. Assuming that the passive system is a duplicate of the primary, there is not even degradation in service.

Redundant networks are similar. In the case that the primary network is unavailable, a secondary path is available. For example, it is common to use a redundant connection to an alternate service provider to deal with the failure of the primary connection. It is also common to deploy core enterprise networks to allow for portions of the core to fail while still providing service. However, duplicate systems often come at over twice the price! The security professional must assure the cost of the system is less than the benefit derived.

Clustering may also be used, although it should not be confused with redundancy. In clustering, two or more members are joined into the cluster and may all provide service at the same time. For example, in an active–active pair, both systems may provide services at any time. In the case of a failure, the remaining partners may continue to provide service but at a decreased capacity.

That degradation in service may not be acceptable in some environments, so often clusters will be deployed with "passive partners" that are intended to join into the active cluster in the case that one of the active systems fails. Naturally, a wide variety of components, systems, and networks can be configured with appropriate levels of fault tolerance and redundancy where needed and where the additional cost is justified.

# Power Supplies

If the power fails or becomes unreliable, then systems will obviously fail or become unreliable. Redundant (or dual) power supplies are common in systems where such failures cannot be tolerated (such as in core network switches, for example).

Alternatively, failures that occur outside of an individual system can be dealt with using appropriate uninterruptible power supply (UPS) systems and alternative sources of power from the main grid (such as diesel-based generators common to many data center facilities).