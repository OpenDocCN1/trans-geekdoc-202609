NOTE.— You can now attempt Exercise 14.

# 10.1.6.5. ACL configuration

— There are many similarities between ASA ACLs and IOS ACLs. The chief differences can be summarized as follows:

+   - ASA ACLs use a netmask rather than a generic mask;
+   - ASA ACLs are named rather than numbered;
+   - by default, the security levels of an interface apply access control without an ACL being configured.

— ACLs can be configured on an ASA by following the below steps:

| Command | Description |
|---|---|
| ciscoasa(config)# access-list id extended { deny | permit } protocol { source_addr source_mask | any | host src_host | interface src_if_name [ operator port [ port ]{ dest_addr dest_mask } | any | host dst_host | interface dst_if_name [ operator port [ port ]] | object-group acl-id } | Creates an extended ACL |
| ciscoasa(config)# access-group acl-id { in | out } interface interface-name | Activates an ACL on an interface |

# 10.1.6.6. NAT service configuration

— ASA supports the following NAT types:

+   - Dynamic NAT: consists of translating several private IP addresses into several public IP addresses;
+   - Dynamic PAT: consists of translating several private IP addresses into a single public IP address;
+   - Static NAT: consists of translating a single private IP address to a single public IP address.

— To configure a dynamic NAT on an ASA, proceed as follows:

| Command | Description |
|---|---|
| ciscoasa(config)# object network public-pool-obj | Creates a network object for the pool of public IP addresses |