routing infrastructure to propagate this information throughout the network. We identified scalability as one concern. Suppose that when a mobile user moves from one network to another, the new foreign network advertises a specific route to the mobile user, and the old foreign network withdraws its route. Consider how routing information propagates in a distance-vector algorithm (particularly for the case of interdomain routing among networks that span the globe.)

+   a. Will other routers be able to route datagrams immediately to the new foreign network as soon as the foreign network begins advertising its route?

+   b. Is it possible for different routers to believe that different foreign networks contain the mobile user?

+   c. Discuss the timescale over which other routers in the network will eventually learn the path to the mobile users.

P12. In 4G/5G networks, what effect will handoff have on end-to-end delays of datagrams between the source and destination?

P13. Consider a mobile device that powers on and attaches to an LTE visited network $A$, and assume that indirect routing to the mobile device from its home network $H$ is being used. Subsequently, while roaming, the device moves out of range of visited network $A$ and moves into range of an LTE visited network $B$. You will design a handover process from a base station $BS.A$ in visited network $A$ to a base station $BS.B$ in visited network $B$. Sketch the series of steps that would need to be taken, taking care to identify the network elements involved (and the networks to which they belong), to accomplish this handover. Assume that following handover, the tunnel from the home network to the visited network will terminate in visiting network $B$.

P14. Consider again the scenario in Problem P13. But now assume that the tunnel from home network $H$ to visited network $A$ will continue to be used. That is, visited network $A$ will serve as an anchor point following handover. (Aside: this is actually the process used for routing circuit-switched voice calls to a roaming mobile phone in 2G GSM networks.) In this case, additional tunnel(s) will need to be built to reach the mobile device in its resident visited network $B$. Once again, sketch the series of steps that would need to be taken, taking care to identify the network elements involved (and the networks to which they belong), to accomplish this handover. What are one advantage and one disadvantage of this approach over the approach taken in your solution to Problem P13?

# Wireshark Lab: WiFi

At the Web site for this textbook, www.pearsonhighered.com/cs-resources, also mirrored on the instructors’ website, http://gaia.cs.umass.edu/kurose_ross, you’ll find a Wireshark lab for this chapter that captures and studies the 802.11 frames exchanged between a wireless laptop and an access point.