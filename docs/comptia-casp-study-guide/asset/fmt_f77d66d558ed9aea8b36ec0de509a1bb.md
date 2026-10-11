
Unfortunately, one of the largest vulnerabilities in the cloud is simple customer error or misconfiguration. Cloud misconfiguration can be any errors or gaps that leave risk exposure. This risk could be exploited by an attacker or malicious insider, and it doesn't take much technical knowledge to extract data or compromise cloud assets. Security researchers disclosed that a nonprofit organization in Los Angeles exposed more than 3.5 million records including PII because an AWS S3 storage bucket leaked databases of information because they were programmed to be “public and anonymously accessible.” Misconfigured cloud services pose a high security risk, so make sure the people administering your cloud are well trained.

## Storage Models

Even though your data is in the cloud, it must physically be located somewhere. Is your data on a separate server, is it co-located with the data of other organizations, or is it sliced and diced so many times that it's hard to know where it resides? Your cloud storage provider should agree in writing to provide the level of security required for your customers.

Tape was the medium of choice for backup and archiving for most businesses for many years. This was in part due to the high cost of moving backup and archival data to a data warehouse. Such activities required hundreds of thousands of dollars in infrastructure investment. Today that has started to change as cloud service providers are beginning to sell attractively priced services for cloud storage. Such technologies allow companies to do away with traditional in-house technologies. Cloud-based archiving and warehousing have several key advantages.

*   **Content Management** The cloud warehousing provider manages the content for you.
*   **Geographical Redundancy** Data is held at more than one offsite location.
*   **Advance Search** Data is indexed so that retrieval of specific datasets is much easier.

How much storage is enough? How big a hard drive should I buy? These are good questions—there never seems to be enough storage space for home or enterprise users. Businesses are no different and depend on fast, reliable access to information critical to their success. This makes enterprise storage an important component of most modern companies. *Enterprise storage* can be defined as computer storage designed for large-scale, high-technology environments.

Think of how much data is required for most modern enterprises. There is a huge dependence on information for the business world to survive. Organizations that thrive on large amounts of data include government agencies, credit card companies, airlines, telephone billing systems, global capital markets, e-commerce, and even email archive systems. Although the amount of storage needed continues to climb, there is also the issue of terminology used in the enterprise storage market. Terms such as *heterogeneous*, *SAN*, *NAS*, *virtualization*, and *cloud storage* are frequently used.

Before any enterprise storage solution is implemented, a full assessment and classification of the data should occur. This would include an analysis of all threats, vulnerabilities, existing controls, and the potential impact if loss, disclosure, modification, interruption, or destruction of the data should occur.

Now that we've explored some of the security issues of enterprise storage, let's look at some of the technologies used in enterprise storage.

*   **Virtual Storage** Virtual storage options have grown, evolved, and matured. These online entities typically focus either on storage or on sharing. The storage services are designed for storing large files. Many companies are entering this market and now giving away storage, such as Microsoft's OneDrive, Amazon Drive, and Google Drive.

    Virtual file sharing services are a second type of virtual storage. These services are not meant for long-term use. They allow users to transfer large files. Examples of these services include Dropbox, DropSend, and MediaFire. These virtual services work well if you are trying to share very large files or move information that is too big to be sent as an attachment.

    On the positive side, there are many great uses for these services, such as keeping a synchronized copy of your documents in an online collaboration environment, sharing documents, and synchronizing documents between desktops, laptops, tablets, and smartphones.

    The disadvantages of these services include the fact that you are now placing assets outside the perimeter of the organization. There is also the issue of loss of control. If these providers go out of business, what happens to your data? Although these services do fill a gap, they can be used by individuals to move data illicitly. Another concern is the kind of controls placed on your data. Some of these services allow anyone to search sent files.

    In [Exercise 9.4](#c09.xhtml#c09-fea-0010), you'll look at security issues involved in online storage.

*   **Network-Attached Storage** *Network-attached storage (NAS)* is a technology that contains or has slots for one or more hard drives using a hierarchical storage methodology. These hard drives are used for network storage. NAS is similar to direct access storage (DAS), but DAS is simply an extension of one system and has no networking capability.

    Many NAS devices make use of the Linux OS and provide connectivity via network file sharing protocols. One of the most common protocols used is Network File System (NFS). NFS is a standard designed to share files and applications over a network. NFS was developed by Sun Microsystems (now part of Oracle) back in the mid-1980s. The Windows-based counterpart used for file and application sharing is Common Internet File System (CIFS); it is an open version of Microsoft's Server Message Block (SMB) protocol.

    For the CASP+ exam, this is often referred to as *object storage* or *file-based storage*. This type of cloud solution is seen in Amazon Simple Storage Services (S3).

*   **SAN** The Storage Network Industry Association (SNIA) defines a *storage area network (SAN)* as “a data storage system consisting of various storage elements, storage devices, computer systems, and/or appliances, plus all the control software, all communicating in efficient harmony over a network.” SANs are similar to NAS. One of the big differences is that NAS appears to the client as a file server or stand-alone system. A SAN appears to the client OS as a local disk or volume that is available to be formatted and used locally as needed.

    For the CASP+, this is referred to in the objectives as *block storage*. Block cloud storage solutions include Amazon Elastic Block Store (EBS) and are provisioned with ultra-low latency for high performance.

*   **Virtual SAN** A *virtual SAN (VSAN)* is a SAN that offers isolation among devices that are physically connected to the same SAN fabric. A VSAN is sometimes called *fabric virtualization*. (*Fabric* can be defined as the structure of the SAN.) VSANs were developed to support independent virtual networking capability on a single switch. VSANs improve consolidation and simplify management by allowing for more efficient SAN utilization. A resource on any individual VSAN can be shared by other users on a different VSAN without merging the SAN's fabrics.
