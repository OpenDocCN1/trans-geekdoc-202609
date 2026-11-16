Organizations should fully define their security requirements for data storage before deploying a technology. For example, NAS devices are small, easy to use, and can be implemented quickly, but physical security is a real concern, as is implementing strong controls over the data. A SAN can be implemented with much greater security than can a NAS. Cloud-based storage offers yet another option but also presents concerns, including the following:

+   ▶ Is it a private or public cloud?
+   ▶ Does it use physical or virtual servers?
+   ▶ How are the servers provisioned and decommissioned?
+   ▶ Is the data encrypted and, if so, what kind of encryption is used?
+   ▶ Where is the data actually stored?
+   ▶ How is the data transferred (data flow)?
+   ▶ Where are the encryption keys kept?
+   ▶ Are there co-tenants?

Keep in mind that storage integration also includes securing virtual environments, services, applications, appliances, and equipment that provide storage.

The Storage Networking Industry Association (SNIA) defines a SAN as “a data storage system consisting of various storage elements, storage devices, computer systems, and/or appliances, plus all the control software, all communicating in efficient harmony over a network.” A SAN appears to the client OS as a local disk or volume that is available to be formatted and used locally as needed.

For the CISSP exam, it is important to know the following terms related to SANs:

+   ▶ Virtual SAN: A virtual SAN (VSAN) is a SAN that offers isolation for devices that are physically connected to the same SAN fabric. The use of VSANs is sometimes called *fabric virtualization*. VSANs were developed to support independent virtual fabrics on a single switch. VSANs improve consolidation and simplify management by allowing for more efficient SAN utilization. A VSAN allows a resource on any