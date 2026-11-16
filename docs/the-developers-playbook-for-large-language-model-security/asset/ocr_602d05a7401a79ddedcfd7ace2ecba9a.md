# HTTP flood

This attack involves flooding a web server with a high volume of HTTP requests, overwhelming its capacity to respond effectively to legitimate user traffic. Attackers exploit vulnerabilities in the HTTP protocol by inundating the server with a barrage of requests, aiming to exhaust its resources, disrupt services, and ultimately render the website inaccessible to genuine users.

# Slowloris

Here, the attacker initiates multiple HTTP connections to the target web server, but deliberately keeps them open by sending partial requests slowly, thereby consuming available server resources and preventing the server from serving legitimate requests.

# An Epic DoS Attack: Dyn

In October 2016, the internet faced a massive disruption due to a sophisticated and large-scale DoS attack on Dyn, a leading Domain Name System (DNS) provider. This event made headlines and marked a pivotal moment in understanding cyber threats and their potential impact on global internet infrastructure.

Dyn, known for its role in internet performance management and website application security, became the target of a DDoS attack in which attackers used compromised IoT devices, such as digital cameras and DVRs, to generate malicious traffic. Infected with the Mirai malware, these devices formed a botnet to flood Dyn's servers with overwhelming traffic.

The attack generated traffic volumes estimated at around 1.2 Tbps (terabits per second). At the time, it was one of the most impactful DDoS attacks on record. The assault on Dyn's DNS services had a ripple effect, causing major internet platforms and services to become unavailable to users across Europe and North America. High-profile websites, including Twitter, Netflix, PayPal, and Amazon, faced significant disruptions. The attack was executed in multiple waves, resulting in intermittent outages and widespread uncertainty throughout the attack.

# Model DoS Attacks Targeting LLMs

Unlike traditional DoS attacks that mainly target vulnerabilities in network and server infrastructures, a model DoS attack focuses on exploiting the unique vulnerabilities inherent in LLMs. In a model DoS attack, the attacker's goal is to compromise the functionality or exhaust the resources of an LLM.

An LLM application connected to the web via a web user interface or a REST API could be the target of the traditional DoS attacks we detailed earlier in the chapter, such as volume-based, protocol, and application layer attacks. However, the nature of LLMs opens them up to specific new concerns we'll discuss in this section.