+   - Process: Establish security posture management.
+   - Technology: Require passwordless or multifactor authentication.
+   - Technology: Integrate native firewall and network security.
+   - Technology: Integrate native threat detection.
+   - Architecture: Standardize on a single directory and identity.
+   - Architecture: Use identity-based access control (instead of keys).
+   - Architecture: Establish a single unified security strategy.

It is possible to find best practices and capabilities in the Microsoft Cybersecurity Reference Architecture (MCRA) and the Microsoft Cloud Security Benchmarks (MCSBs). Some are embedded in MCRA architecture diagrams (explained in Chapter 1, “Define and Implement an Overall Security Strategy and Architecture”), others are in other MCRA sections, and others are explicitly stated in MCSBs.

The detailed technical diagrams are an integral part of Microsoft Cybersecurity Reference Architecture. They describe Microsoft cybersecurity capabilities, Zero Trust user access, security operations, operational technology (OT), multi-cloud and cross-platform capabilities, attack chain coverage, Azure native security controls, and security organizational functions.

# Essential Best Practices in the MCRA

Essential best practices in the MCRA consist of the following:

+   - Find out what resources are available to you: Know what security controls and capabilities you have access to and use the resources.
+   - Apply the right tool for the job: Use a multi-technology approach rather than relying solely on one technology, such as a network firewall or a SIEM.
+     - Security of the data and management planes: Ensure that both security controls on the data plane (which are available since the days of pre-cloud on-premises data centers) and security controls on the management plane (which can be embedded within the cloud platform to enable additional visibility and control) are included.
+   - Platform and infrastructure security and workload security: Ensure you have controls to protect specific workloads (such as web application firewalls [WAFs]) and the overall infrastructure and development environment.
+   - Adopt cloud-native controls: Ensure that native cloud controls protect your cloud assets.
+   - Adopt consistent tooling: Use consistent tooling across cloud providers to ensure effective control deployment across your infrastructure and platforms. You can accomplish more security with the available resources by reducing the time and effort required to implement and monitor controls.
+   - Consider security holistically: It is essential to have visibility and control over the entire life cycle of an asset to ensure its security. In the case of a cloud-hosted resource, the following would be included: