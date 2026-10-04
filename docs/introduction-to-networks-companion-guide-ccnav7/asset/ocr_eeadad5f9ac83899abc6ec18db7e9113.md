stored records, it contacts other servers to resolve the name. After a match is found and returned to the original requesting server, the server temporarily stores the numbered address in case the same name is requested again.

The DNS client service on Windows PCs also stores previously resolved names in memory. The ipconfig /displaydns command displays all the cached DNS entries.

As shown in Table 15-2, DNS uses the same message format between servers, consisting of a question, an answer, an authority, and additional information for all types of client queries and server responses, error messages, and transfer of resource record information.

Table 15-2 DNS Message Sections

| DNS Message Section | Description |
|---|---|
| Question | The question for the name server |
| Answer | Resource records answering the question |
| Authority | Resource records pointing toward an authority |
| Additional | Resource records holding additional information |

# DNS Hierarchy (15.4.3)

The DNS protocol uses a hierarchical system to create a database to provide name resolution, as shown in Figure 15-21. DNS uses domain names to form the hierarchy.

The naming structure is broken down into small, manageable zones. Each DNS server maintains a specific database file and is responsible for managing name-to-IP mappings for only that small portion of the entire DNS structure. When a DNS server receives a request for a name translation that is not within its DNS zone, the DNS server forwards the request to another DNS server within the proper zone for translation. DNS is scalable because hostname resolution is spread across multiple servers.

Each top-level domain represents either the type of organization or the country of origin. Examples of top-level domains include the following:

+   - **.com:** A business or an industry
- **.org:** A non-profit organization
- **.au:** Australia
- **.co:** Colombia