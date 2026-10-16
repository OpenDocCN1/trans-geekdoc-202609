
Another aspect that varies from one version of `802.11` to another is the distance the signal is expected to travel. Some of the `802.11` versions will carry only `11` feet or so. Others are expected to carry up to a couple of hundred feet. This varies quite a bit depending on the number of walls and the composition of the walls. A `Wi‑Fi` signal can carry quite a bit farther outside because there is nothing to impede the signal. Inside is a very different story. In terms of capturing signal without actually being in the building, how far from the building you need to be will depend on how close the nearest access point is to an external wall and how many windows there are. Windows would generally allow the signal to pass out unimpeded.

There are two different ways to set up `Wi‑Fi` networks from a topological perspective. One of these is far more common than the other, but it's still possible to see both. Beyond that, you need to be concerned with how the `Wi‑Fi` network handles authentication and encryption. Both authentication and encryption mechanisms provide possible ways to attack the wireless network. This is especially true in cases where companies allow employees to attach their own devices to the corporate network.

### `Wi‑Fi` Network Types

There are two types of wireless networks you are going to run into. We can talk about topology here because it's technically relevant, though it may be harder to conceptualize than with wired networks. Let's give it a shot, though. The first type of network, and one that is less common, especially in a business environment, is an ad hoc network. An ad hoc network is one that exists without any central routing or switching device. [Figure 11.1](#c11.xhtml#c11-fig-0001) shows an ad hoc wireless network with different device types connected to it. You can think of it as a dynamic mesh network. Each device communicates directly with another device. The connections are stood up dynamically as two devices have a need to talk to one another. When a device comes onto the network, it shares its information with the other devices. They then know how to make a connection to that device if they need to.

![FIGURE 11.1 Wireless ad hoc network](images/c11f001.png)

[**FIGURE 11.1**](#c11.xhtml#R_c11-fig-0001) Wireless ad hoc network

This is not to say that anyone can connect to an ad hoc network. When an ad hoc network is started up by someone, they have to give the network a name. In addition to the network name, a password may be required to gain access. In an ad hoc network, all the devices have to be within range of each other because there is nothing else in place to forward messages to other devices at a distance. Ad hoc networks also don't provide encryption. `Wi‑Fi Direct`, which replaces ad hoc networks, will allow encryption between stations.

While ad hoc networks are easy to set up and they can be fast, managing them is difficult, and they are certainly not suitable for an enterprise environment. Instead, there are infrastructure networks. An infrastructure network has a central device, which acts like a switch. Computers don't talk to one another directly. Instead, all messages go through an access point. [Figure 11.2](#c11.xhtml#c11-fig-0002) shows an infrastructure‑based network. The difference between a switch and an access point is that the switch controls the electrical signal. Since that's the case, the switch really does determine whether a system gets the traffic or not. An access point has no control over whether systems see the traffic or not because everything is in the air. The only thing you need to see it is a radio that can catch the signals.

![FIGURE 11.2 Wireless infrastructure network](images/c11f002.png)

[**FIGURE 11.2**](#c11.xhtml#R_c11-fig-0002) Wireless infrastructure network

To demonstrate that idea, take a look at [Figure 11.3](#c11.xhtml#c11-fig-0003). This is a Wireshark capture with monitor mode enabled on the wireless interface. This means Wireshark gets everything down to the radio headers, which is the layer 1/2 set of headers for the frame. This particular system is not connected to any wireless network. You can think of that as having a wired interface being disconnected. As that's the case, Wireshark shouldn't be seeing anything, and if monitor mode was turned off, even with promiscuous mode on, there wouldn't be anything in the capture.

![FIGURE 11.3 Wireshark capture of radio traffic](images/c11f003.png)

[**FIGURE 11.3**](#c11.xhtml#R_c11-fig-0003) Wireshark capture of radio traffic

What you can see in the capture, though, is a lot of traffic. This is because wireless networks are very chatty. They have to be because there is no electrical connection that tells a system there is a network in place. Once monitor mode is on, though, you can see the messages between the access point and the clients. For example, access points send out beacon frames periodically. These are used to announce the presence of the network in the area. Additionally, clients will send out probe requests to identify networks in the area. When a probe request is sent out, the access point will send out a probe response. If you pull up a list of the wireless networks in the area, you may see your operating system, indicating that it is looking for networks in the area. This means it is sending out probe messages. To connect to a network, you need to first identify the network.

### `Wi‑Fi` Authentication

There are different forms of authentication that happen on `Wi‑Fi` networks. The first we are going to go over is a simple machine‑level authentication. This is where your client associates with the network. For that to happen, your system will send out probe requests to identify wireless networks in the area. Your client is looking for a service set identifier (SSID), which is essentially the name of your network. There may be multiple access points in a network that carry the same SSID, though, since you may have a large facility and the signal from a single access point isn't enough to carry through all of it. To distinguish from one access point to another when they are using the same SSID, there is a base service set identifier (BSSID). This looks like a MAC address and provides a way for a client to communicate with a specific access point, as needed. You can see an example of multiple BSSIDs using the same SSID in [Figure 11.4](#c11.xhtml#c11-fig-0004). The Atlantis‑Guest network has two entries. Each has their own BSSID, while sharing the SSID of Atlantis‑Guest.

![FIGURE 11.4 Multiple BSSIDs for a single SSID](images/c11f004.png)

[**FIGURE 11.4**](#c11.xhtml#R_c11-fig-0004) Multiple BSSIDs for a single SSID

The process for getting your client connected to the access point requires that it authenticate with the access point. This may be a simple process, particularly if the access point has Open Authentication enabled. This is done to allow the client to start the conversation with the network. Actual authentication, particularly at the user level, happens later. The client sends an authentication request, and the access point will typically respond with an authentication response indicating “Successful.” This allows the client to move to the next stage.

Once the client has been authenticated, the next step is to associate the client with the network. This involves the client sending an association request to the access point. In the association request, the client, or *station* as it may be called, sends its capabilities. This would include the versions and speeds it supports. This allows for the access point and the station to negotiate the way they are going to communicate going forward. In [Figure 11.5](#c11.xhtml#c11-fig-0005), you can see a diagram of the process that is required to get the station authenticated and associated with the access point.

![FIGURE 11.5 Authentication and association steps](images/c11f005.png)
