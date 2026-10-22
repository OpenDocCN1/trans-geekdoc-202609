a full installation, some GSD vendors will provide a preinstalled virtual appliance that minimizes total deployment time. It is important to ensure that the virtualized GSD maintains its priority in obtaining and sustaining resources from the VM instance.

A VM-capable GSD acts as an independent network security entity. Instead of having dedicated hardware, the GSD leverages the hypervisor’s hardware abstraction layer to gain access to the necessary resources. This implementation provides hardware appliance-like capabilities to control the allowed paths based on what networks route through the GSD VM instance.

A VM-embedded GSD virtual appliance integrates with the hypervisor to gain low-level access to the entire VM host/cluster. The GSD now has visibility into previously inaccessible communication paths and is able to conduct allowed path enforcement for both inter- and intra-VM communications.

# 26.2.15 Host-Based Agents.

As mobile devices demand greater internal network access—including data to be stored local to the device—so did the requirement for those host-based protections to be able to minimize the additional risk of allowing such access. Antivirus capabilities, although arguably only marginally effective against new and emerging threats, still maintain a necessary presence to filter known attacks vectors. Firewalling capabilities at the network and application level reduce the host’s network-facing threat profile. The Host Intrusion Prevention System (HIPS) provides protection against known and potentially unknown threats because of its ability to inspect up to the application layer.

When network-security devices fail to detect a threat, host-based protection has additional measures to detect local anomalous behavior due to its increased contextual awareness of how the host—the applications and the operating system—should behave, thus allowing the host an advantage in detecting emerging threats. However, organizations should not underestimate the administrative overhead necessary to manage and monitor this protection.

See Chapter 27 of this Handbook for more details on host-based protections.

# 26.3 NETWORK-SECURITY MECHANISMS.

Network security, once synonymous with the firewall, continues its growth in both scope and depth. Government and organizations are requiring security to be baked into the systems and solutions they produce or purchase.

It is entirely possible for an attack to originate from a system not coinciding with a direct perimeter attack. These attack vectors include likely exposures, such as an employee mobile device infected with malicious code while traveling; the new USB flash drive an employee receives at a conference; or a vendor providing legitimate support that plugs his/her laptop into the internal network.

Those who are selecting network security systems must be able to decipher the hyperbole from reality to ensure the device(s) deployed realistically address(es) the specific risks pertinent to the organization. Gateway security devices maintain their basic allowed path control heritage but now are far more advanced in their ability to integrate protection within the payload and beyond.

# 26.3.1 Allowed Paths.

Network-security devices provide allowed-path protections to ensure network traffic only flows in expected and intended ways. Unfortunately, this base level of enforcement is insufficient because application-layer attacks (e.g., client-side browser exploits) leverage these traditional allowed paths. Regulatory and compliance security requirements are also driving the deployment of more