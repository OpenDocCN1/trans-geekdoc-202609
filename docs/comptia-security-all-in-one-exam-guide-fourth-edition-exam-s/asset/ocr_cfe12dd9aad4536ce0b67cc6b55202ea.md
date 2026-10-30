A web application firewall can be configured to examine inside an SSL session. This is important if an attacker is attempting to use an SSL-encrypted channel to mask their activity. Because legitimate SSL channels are instantiated by the system, the appropriate credentials can be passed internally to the WAF to enable SSL inspection.

# Application-aware Devices

Network security was developed before application-level security was even a concern, so application-level attacks are not seen or blocked by traditional network security defenses. The security industry has responded to the application attack vector with the introduction of application-aware devices. Firewalls, IDSs/IPSs, proxies, and other devices are now capable of doing stateful inspection of traffic and detecting and blocking application-level attacks as well as network-level attacks.

# Next-Generation Firewalls

Next-generation firewalls is a term used to describe firewalls that are capable of content-level filtering and hence are capable of application-level monitoring. Depending on the level of programming and sophistication, next-generation firewalls can perform many advanced security checks based on defined application rules.

# IDS/IPS

Intrusion detection and prevention systems perform their security tasks by screening network traffic and then applying a set of rules. When the process is application aware, the specificity of rules can be even more exacting. Adding advanced rule-processing power that manages both stateful and content-aware rule processing allows these devices to detect malicious attacks to applications based on the application, not just based on an address. The engines used for IDS/IPS are being incorporated into firewalls, turning a simple network firewall into a next-generation firewall.

# Application-Level Proxies

Proxies serve to manage connections between systems, acting as relays for the traffic. Proxies can function at the circuit level, where they support multiple traffic types, or they can be application-level proxies, which are designed to relay specific application traffic. An HTTP proxy can manage an HTTP conversation, as it understands the type and function of the content. Application-specific proxies can serve as security devices if they are programmed with specific rules designed to provide protection against undesired content.

# Chapter Review

This chapter described network devices and their configurations. Firewalls, routers, switches, sniffers, load balancers, proxies, web security gateways, and VPN concentrators were covered. Security devices, including intrusion detection systems, protocol analyzers, spam filters, and all-in-one security appliances, were presented. The chapter concluded with an examination of application-aware devices, including next-generation firewalls and web application firewalls.