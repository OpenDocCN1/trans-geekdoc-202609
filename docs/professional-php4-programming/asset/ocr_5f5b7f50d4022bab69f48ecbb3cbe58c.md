# # NIS Servers

NIS works using a client-server mechanism in which the clients query NIS servers for information. The information can range from username-password mappings to hardware addresses of network interface cards. The primary NIS server for a domain is called a master server. A master server exists for each NIS domain. The domain is essentially the network that the NIS servers service.

Other servers exist which clients may contact rather than contact the master server directly. Such servers are called slave servers. The NIS information databases are updated on the master server, which propagates the changes to each of the slave servers that depend on it.

NIS clients are free to contact the master or slave servers. However, only the master server can be updated with changes to the information databases. There is another set of servers, which are not exactly servers since when they are started on a certain client machine, they connect to the slave servers (or the master server) effectively binding the clients on that machine to the particular slave server (or the master server).

# # NIS Clients

NIS clients are applications that access NIS servers for information about various resources. However, a pure NIS client is not of much use except for diagnostic purposes, but the NIS clients are often built into applications that need access to specific resources. For example, the UNIX login program accepts a user's login name and contacts the NIS server for password information, thereby acting as an NIS client.

# # NIS Maps

NIS maintains databases for storing information about various resources on the network. Such databases are known as NIS maps. NIS maps are constructed out of standard configuration files of an operating system such as /etc/passwd which is the password information file on UNIX systems.

All NIS maps need not belong to one domain, and there can be several domains with the same type of NIS maps with their own servers. The same information can be represented in two maps, the only difference being the key used to index the information. For example, host information is available in two maps, hosts.byname, which can be indexed by the host name, and hosts.byaddr, which can be indexed using IP addresses. Additionally, each of these maps can have a nickname, which is a shorter name for the map, for example hosts.byaddr has the nickname hosts.

Below is a list of the various NIS maps and the UNIX configuration files they are derived from:

| Map names | Nickname | Configuration File | Description |
|---|---|---|---|
| passwd.byname | passwd | /etc/passwd | Returns password information by using user names as keys. |
| passwd.byaddr | n/a | /etc/passwd | Resolves passwords by address. |
| group.byname | group | /etc/groups | Retrieves group information using the group name as a key. |