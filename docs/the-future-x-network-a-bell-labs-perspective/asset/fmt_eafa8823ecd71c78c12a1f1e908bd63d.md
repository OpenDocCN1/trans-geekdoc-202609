
In the area of 5G cellular access,[¹](#14-9781315365756_chapter-chap8.xhtml#fn8_1) a consensus is building within the industry for both mm-wave (20–100 GHz) and low-band (sub-6 GHz) carriers. Compared with 4G, low-band 5G carriers are expected to provide better optimization for diverse traffic profiles, supporting connectionless access for short data bursts, and higher throughputs and lower latency if required by applications. Starting around 2020, 5G mm-wave or high-band carriers will be able to provide massive capacity due to the large spectrum bandwidth available at high frequencies, enhancing both device throughput and network capacity. Using smart-beam steering and an ability to track a user through direct and reflected paths, the 5G high-band carrier will be able to work in concert with a low-band carrier to provide service to fixed and mobile devices.

## Shared spectrum

In the area of shared spectrum, there are significant blocks of spectrum around the world in the sub-6 GHz frequency bands that are ideally suited for mobile communications. However, because they were allocated to commercial or government use prior to the explosion in mobile connectivity, they remain under-utilized. Attempts to relocate incumbent users of this inefficiently used spectrum have proven expensive and time-consuming.

A more viable approach is to share spectrum in these bands by establishing multiple usage tiers. Incumbent users are considered primary and are given unimpeded access, whereas secondary or tertiary users only have access at places and times when a higher tier user is not active. They must immediately cease usage when a higher tier user pre-empts them. This is orchestrated in real-time by a spectrum access system that uses a database and dynamic software controls to ensure interference is avoided.

The US Federal Communications Commission (FCC) voted in April 2015 to adopt three-tier sharing in the 3.5 GHz band, which contains 150 MHz of spectrum currently used for military and satellite operations. Shared spectrum in the 3.5 GHz band is particularly well suited for indoor small cells. The propagation characteristics are good for enterprise-scale coverage, and the likelihood of interference with the outdoor primary user is low. In addition, the FCC and the National Telecommunications & Information Administration (NTIA) is considering sharing spectrum in the 1750–1850 MHz range (NTIA 2015a–b). In late 2014, the FCC auctioned AWS-3, which contains the 1755–1780 MHz paired band, with mandated provisions for sharing with federal systems for an indefinite period (FCC 2014b). In the 2020–2025 timeframe, the 2700–2900 MHz and 4200–4400 MHz bands, currently used by the Federal Aviation Administration, have also been identified as candidates for spectrum sharing.

![](images/fig8_3.jpg)

As a result of these evolutions, we predict that the spectrum available for enterprise usage will massively increase and be spread across these technologies, as shown in [figure 3](#14-9781315365756_chapter-chap8.xhtml#fig8_3).

As mentioned, today enterprise wireless connectivity is often dependent on users successfully executing a sequence of one or more steps to select an access technology, choose an access point, enter security credentials and set up a VPN. Then, once connected, action is again required by the user when coverage drops, or there is insufficient support for QoS, or the limited support for mobility on Wi-Fi affects service. For users, the value of wireless connectivity is based on convenience and transparent access: it saves time and boosts productivity. So when manual intervention is required — to set up connectivity or reconnect after failures — this value is diminished and the wired LAN becomes more attractive.

Fortunately, the advent of a new type of VPN connectivity, based on software-defined networking (SDN) principles, is making progress toward reducing complexity, and the configuration and reconfiguration required. Hardware-based VPNs have existed for several decades to support secure, multi-tenant access to the same IP network infrastructure, allowing the various locations of an enterprise to be connected together to form their own (virtual) private network. However, due to the relative cost and complexity of deploying and managing the required VPN router functionality in each enterprise location, this service has been restricted to only the largest sites of the largest enterprises. The new, SDN-enabled approach creates a software instance of the VPN for each location, leveraging virtualization technologies and cloud infrastructure. A software-defined VPN (SD-VPN) can, in this way, be created for any and every enterprise location, radically simplifying secure connectivity management.

In a fully implemented SD-VPN, a mobile device at an enterprise location can connect over either Wi-Fi or the legacy wired LAN to enterprise applications deployed in centralized data centers. The application flows are routed to a virtual router in the enterprise data cloud and then forwarded to the application server, with no configuration required on the part of the end user, or installation of a security client (for example, an IPSec client).

Unfortunately, when the device leaves the enterprise and attaches to the LTE network, or an external Wi-Fi network, this SD-VPN is not accessible. A dedicated VPN client has to establish a secure connection between the device and an enterprise VPN gateway that resides in an enterprise site, or in a separate data center. IPSec is most often used for these VPNs, as shown in [figure 4](#14-9781315365756_chapter-chap8.xhtml#fig8_4).

There are two issues with this approach:

1. The VPN client must be installed and maintained on the device, requiring user interaction and entering of credentials each time the device connects.
2. Traffic is not directly routed to the enterprise applications from the external network. Instead traffic has to first be sent through an IPSec tunnel across the public internet to an IPSec tunnel-termination router at another enterprise site. It is then sent to the application data center through another VPN tunnel. This results in non-optimal routing, the inability to support QoS due to the traversal of the public internet, and the frequent scaling limitations characteristic of IPSec termination routers.

![](images/fig8_4.jpg)

As indicated in [figure 4](#14-9781315365756_chapter-chap8.xhtml#fig8_4), we believe that in the next decade, the vast majority of growth in secure connections will be in SD-VPNs in order to solve this problem, as discussed in the next section.

Today, enterprise connectivity is bifurcated between two service providers:

1. A cellular service provider for reliable, seamless access for mobile devices
2. An IT provider of Wi-Fi and wired access connectivity for laptops, copiers, IP phones and other user devices

This split is not driven by the enterprise business needs, but by the independent evolution of information networks into the wireless domain (adding Wi-Fi to fixed LAN access) and service provider networks (adding smart devices to the original wired voice service).
