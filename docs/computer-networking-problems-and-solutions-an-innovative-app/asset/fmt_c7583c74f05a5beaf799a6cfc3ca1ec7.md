
A key component of `NETCONF` is the management station. The management station provides a networkwide viewpoint for network management and automation. It will have a graphical user interface (`GUI`) or `CLI` interface, enabling network administrators to focus on the deployment automation of an entire networkwide service. A sample service may be provisioning a new `VPN` customer or changing an `SNMP` password. Network administrators can use a management station to manage the entire lifecycle of a service. By default, and because of `NETCONF`, network management stations support multivendor networks. To provide additional extensibility, some network management stations feature other southbound configuration methods or protocols—for example, `SNMP` or `CLI`—and robust northbound `API` for integration into other systems.

`NETCONF` is a modular protocol, organized in layers, as shown in [Figure 26-1](#ch26.xhtml#ch26fig01).

![Image](graphics/26fig01.jpg)

**Figure 26-1** *NETCONF Layers*

These layers allow for other tools or protocols to be inserted to extend functionality.

The bottom layer is concerned with the transport of messages between devices. `NETCONF` supports many different transport protocols; however, `SSH` is commonly used because it is well known and provides authentication, integrity, and confidentiality. Because `SSH` runs over the Transmission Control Protocol (`TCP`), it also provides reliable transport.

The message layer frames and encodes remote procedure calls (`RPCs`). An `RPC` appears to be a local function (or procedure) call to the calling application, but is actually executed on a remote device (see the “Further Reading” section at the end of the chapter for more information on `RPCs`). `NETCONF`’s use of `RPC` enables `NETCONF` to instruct the remote device what to do with the command—for example, apply the configuration detailed in the operations layer. `NETCONF` `RPC` messages are encoded in the eXtensible Markup Language (`XML`) and must contain a `message-id` element allowing `NETCONF` to track messages. Finally, the messages layer supports notifications, where devices notify the management station of a configuration change.

The operations layer defines the actions for `NETCONF` clients and servers. `NETCONF` operations are a set of create, read, update, and delete (`CRUD`) actions used on the data stores. Common operations include `get-config`, `edit-config`, and `delete config`.

The base protocol includes the following operations shown in [Table 26-2](#ch26.xhtml#ch26tab02).

**Table 26-2** *NETCONF Operations*

| **NETCONF Operations** || **Description** |

| --- | --- |

| get || Retrieve running configuration and device state information |

| get-config || Retrieve all or part of a specified configuration datastore |

| edit-config || Load all or part of a specified configuration to the specified target configuration datastore |

| copy-config || Create or replace an entire configuration datastore with the contents of another complete configuration datastore |

| delete-config || Delete a configuration datastore |

| lock || Lock the entire configuration datastore system of a device |

| unlock || Release a configuration lock |

| close-session || Gracefully terminate the NETCONF session |

| kill-session || Force the termination of a NETCONF session |

The content layer contains the formatted data, either configuration or notification, sent to or from the network node. The `NETCONF` specification does not define how the data should be formatted; it does, however, suggest the use of the `YANG` data modeling language. Data modeling ensures compatibility between systems.

`YANG` is a data modeling language defined in `RFC6020` and updated in `RFC7950`; it is used to format configuration, notification, and state data in the operations and content layers of `NETCONF`. Data modeling is a definition of both the syntax and the semantics or schema of the data and is critical when working between remote systems. The data model ensures the requests of the `NETCONF` management station are faithfully carried out on the `NETCONF` server (network device).

There are two sets of widely deployed and supported `YANG` models:

• The `IETF` standardizes a data model in `YANG` for each protocol, for basic routing functionality, and for common equipment management requirements.

• The `OpenConfig` group maintains another set of data models, largely overlapping, and often coordinated with the `IETF` data models.

Beyond these models, each vendor also supports a vendor- and equipment-specific model set that can (often) be downloaded from their support sites.

The underlying syntax of `YANG` is `XML` in a keyed hierarchical model, much like a Type Length Value (`TLV`) format. The hierarchy of the model enables multiple organized levels of parent/child relationships of key/value paired data. The keys in `YANG` must be unique within a layer with single values or lists of data. `YANG` data is typed—for example, integer, string, etc.—and is enforced by the server and client implementations. Because `YANG` data is in `XML`, the data is generally human readable. The following code snippet is an example of `YANG` data showing “show interface brief”:

[Click here to view code image](#ch26_images.xhtml#p26pro03a)

```
01 <?xml version="1.0"?>  
02 <nf:rpc xmlns:nf="urn:ietf:params:xml:ns:netconf:base:1.0"  
     xmlns="http://www.cisco.com/nxos:7.0.3.I6.1.:if_manager"  
     message-id="1">  
03 <nf:get>  
04 <nf:filter type="subtree">  
05 <show>  
06  <interface>  
07   <brief/>  
08  </interface>  
09  </show>  
10   </nf:filter>  
11   </nf:get>  
12   </nf:rpc>  
13 ]]>
```

In the code snippet, line 1 declares the document as `XML`. Line 2 is the `RPC` call from the standard `NETCONF` library. Line 3 is the `NETCONF` operation. Lines 5 through 7 are the `NETCONF` content and the command to show the interface information.

**Note**

`RFC7951` defines JavaScript Object Notation (`JSON`) encoding of data modeled with `YANG`. Both `XML` and `JSON` are discussed later in this chapter.

Together `NETCONF` and `YANG` provide an open-standards-based, easy-to-use toolset to automate a network. Commercial tools (for example, Cisco’s `Tail-F`) leverage `NETCONF/YANG` and enable network administrators to manage the network in terms of the service the network provides—for example, Quality of Service (`QoS`) or Virtual Private Networks (`VPNs`).

### RESTCONF

`RESTCONF` is an emerging extension of `NETCONF` that leverages the widely deployed Hypertext Transfer Protocol (`HTTP`) over the Secure Sockets Layer (`SSL`, combined with `HTTPS`) to interact with network devices. `RESTCONF` uses `YANG` as a data modeling language and has the same basic functionality as `NETCONF`; however, it uses `HTTP` methods such as `POST`, `PUT`, and `DELETE` to implement the equivalent of `NETCONF` operations. The `RESTful` methods available in `REST-CONF` enable basic create, read, update, and delete (`CRUD`) operations on a hierarchy of data stores via `HTTP`.

The “REST” is in `RESTCONF` because it provides a `RESTful` interface; the concept of Representational State Transfer (`REST`) and `RESTful` interfaces is discussed further in the next section.

### Automation with Programmatic Interfaces

Some modern network operating systems, for example, Cisco `NX-OS`, offer additional vendor-specific automation programmatic interfaces. These interfaces, known as Application Programming Interfaces, or `APIs`, are exposed on standard `TCP` ports and require a higher-level language such as `Python` to interact with a device. The higher-level program contains the specific interaction—for example, a configuration or troubleshooting routine—and leverages the `API` to connect to the device. Most network operating systems require the `API` to be enabled via `CLI` and require authentication.
