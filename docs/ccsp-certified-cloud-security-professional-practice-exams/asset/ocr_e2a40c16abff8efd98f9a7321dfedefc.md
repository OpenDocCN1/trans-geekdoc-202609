A is incorrect because confidentiality is not important for all data as part of preservation. Obviously, some data that is sensitive has confidentiality requirements, but those are separate from the requirements of chain of custody to catalog the handling of data since its collection.

B is correct for the same reason as confidentiality, in that privacy does not apply to all data and does not preserve its handling processes or procedures.

D is incorrect because aggregation refers to collecting data, typically event data, into a single index and storage system. Aggregation does not apply directly to data preservation at all.

# 7. Which storage type is typically used by the cloud provider to house virtual machine images?

+   A. Volume

+   B. Structured

+   C. Unstructured

+   D. Object

+   Object storage utilizes a flat hierarchy and catalogs data with an opaque file handler or descriptor. When storing virtual machine images, cloud providers typically use object storage because there is no reason to maintain an organized file structure, and an opaque descriptor works perfectly for virtual machine images and easy access to call them.

+   A is incorrect because volume storage resembles a traditional file system structure, with organization and filenames, and would not serve an appropriate or necessary purpose for the storage of virtual machine images. Volume storage is also logically attached to a specific instance and would not be broadly accessible throughout and environment like object storage is.

+   B is correct because structured storage resembles a database-type organization and is used specifically with PaaS implementations; it would not be used for virtual image storage throughout a cloud infrastructure.

+   C is incorrect because unstructured storage is used within a PaaS implementation for support objects such as images and web files; it would not be used for the storage of virtual machines for use throughout a cloud infrastructure.

# 8. When a DLP solution is used to protect data in transit, where is the optimal place to deploy the DLP components?

+   A. On the server originating the traffic

+   B. At the network perimeter

+   C. Between VLANs

+   D. On the server receiving the data

+   B. When protecting data in transit, a DLP solution would optimally be deployed at the network perimeter. Within a network, extensive monitoring can be used in conjunction with other security controls on the data, at the network perimeter