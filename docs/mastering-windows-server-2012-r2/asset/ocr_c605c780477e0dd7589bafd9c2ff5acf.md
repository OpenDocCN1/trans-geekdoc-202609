With Windows Server 2012 failover clusters, Microsoft introduced cluster bootstrapping, which is a new feature that allows the cluster to boot without the need to authenticate with Active Directory. It does this by allowing the cluster node that boots first to create the cluster and then attempt to gain quorum. Once this happens, the remaining cluster nodes will boot up, without needing authentication to a DC.

Cluster bootstrapping happens without the need for you to configure anything in the failover cluster. But be aware that it doesn't mean you don't need to have an Active Directory environment in place to begin with. AD is still required to create the original cluster object and when new nodes are added to the cluster.

# Quick Domain Controller Deployment

Windows Server 2012 includes a new method of deploying any number of DCs very quickly through virtual domain controller cloning. This gives administrators a supported solution to rapidly spin up replica clusters using an existing template DC for reference. Virtual cloning can be beneficial to organizations that want to quickly deploy DCs into new domains. It's also a helpful feature in private cloud environments to meet scalability requirements.
It's possible, that the most frequent use of this feature will be in test and demo environments, where you can deploy numerous configurations of DCs to try out new features and capabilities before rolling them into production.

# VIRTUAL DC CLONING PREREQUISITES

This section discusses the prerequisites that you need to have lined up to get started with virtual DC cloning:

+   * A account is a member of the Domain Admins group in Active Directory.

+   * At least one Hyper-V host (VMHOST1-SRV in our example) running Windows Server 2012 or higher.

+   * Local admin rights on the Hyper-V host server.

+   * An existing Windows Server 2012 or higher DC hosting the PDC emulator FSMO role (WS2012R2-DC1) needs to be deployed.

You can netdom query fsmo into a command prompt to see which server hosts this in an existing Active Directory. This server won't be touched as part of the cloning process and is used primarily for authentication and security auditing.

+   * Virtual DC running Windows Server 2012 (WS2012R2-DC2) in the same domain as the PDC emulator you mentioned.

This will be the template DC that you will use for cloning. This DC shouldn't have the DHCP, Active Directory Certificate Services, or Lightweight Directory Services roles installed because none of them are supported for cloning. It should have the DNS server installed hosting Active Directory integrated zones, but be aware that your cloned DC will then get deployed as a DNS server.

+   * Ensure you eject the virtual floppy drive (VFD) on your template virtual DC because leaving it connected can cause issues when trying to import the new VM.