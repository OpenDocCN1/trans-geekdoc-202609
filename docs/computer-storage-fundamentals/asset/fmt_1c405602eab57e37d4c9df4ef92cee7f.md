
# Fibre Channel Fundamentals

When `N_Port` device (server or storage) is connected to a switch, it sends a fabric login (`FLOGI`) request to switch to obtain Fibre Channel ID (`FCID`). `FCID` in `FC` is like an `IP` address in `TCP/IP` network, using which it communicates with other devices in the fabric. `FLOGI` request is similar to `DHCP` client request for an `IP` address.

An `IP` address has two parts, network ID and host ID. Similarly, `FCID` also has two parts, domain ID, which is unique for all devices that are connected to a switch, and the port ID, which is unique to each `N_Port` device connected to the switch.

Login server process running in switch provides a unique `FCID` to each device connected to it. Similar to `DHCP`, server provides each network device a unique `IP` address.

`WWPN` in `FC` is equivalent to `MAC` address in network.

## Link Reset and Fabric Login

| `N_Port` | `F_Port` | Sequence | Result |
| --- | --- | --- | --- |
|  |  | `NOS` | Link not operational |
| `OLS`→ |  |  | `N_Port` powered-up-offline state |
|  | `LR`← |  | Link reset (`LR`) |
| `LRR`→ |  |  | LR response (`LRR`) | Link active |
| `FLOGI`→ |  |  | Fabric login |
|  | `ACC`← |  | Fabric login accept | Address obtained |

Table 4.3: Link reset and fabric login

After the `N_Port` begins the initialization process by sending `OLS`, the `F_Port` then tries to reset the port by sending a sequence of `LR`. The `N_Port` responds with a sequence of `LRR`. From this point on, the link is active and idles flow in both directions on the link.

Idle frames are sent continuously when no frames are being transmitted to maintain synchronization and to make the link active. In an idle transmission word the first character is a `K28.5`, the second is the idle character, and the last two characters are any characters that satisfy disparity. `Idles` are transmitted between frames.

## Name Server and Port Login

After `N_Port` device completes the `FLOGI` process, it requires to reach other devices connected to the fabric. A service run in is called name server. `PLOGI` is used by one `N_Port` to log in to another `N_Port`, open a session, and exchange service parameters. `LOGO` is used to terminate a login session and free its associated resources.

| `N_Port` | `F_Port` | Sequence | Result |
| --- | --- | --- | --- |
| `PLOGI`→ |  |  | Port login to name server |
|  | `ACC`← |  | Port login accept |
| `FCS`→ |  |  | Request directory |
|  | `Directory`← |  | Directory services response |
| `LOGO`→ |  |  | Logout from name server |
|  | `ACC`← |  | Logout accept | Directory obtained |
| `PLOGI`→ |  |  | Port login to another `N_Port` |
|  | `ACC`← |  | Port login accept | Parameters exchanged |

Table 4.4: Port login

Now, the `N_Port` can log in to each of the other ports and exchange service parameters. The initiator sends a `PLOGI` with its operating parameters. The target `N_Port` responds with `ACC` frame that specifies its own operating parameters. `N_Port` informs the name server of its personality and capabilities.

## Process Login

| `N_Port` | `F_Port` | Sequence | Result |
| --- | --- | --- | --- |
| `PRLI`→ |  |  | Process login |
|  | `ACC`← |  | Process login response | Communication established |

Table 4.5: Process login

After successful `PLOGI`, `N_Port` knows about each of the other ports and the driver has stored their details in a parameter block, the driver in this node can open a channel with each of the other drivers associated with each node. When a channel has been successfully opened, like in the case of a `SCSI` initiator, opening a channel with a `SCSI` target, an image pair is established and communication can take place while the channel is open. If an image pair is closed by the driver when it logs out (`PRLO`), the image pair must be established again before further communication can take place.

`PRLI` establishes an `FC-4` session between the originator and responder ports so that the driver's process service parameters can be exchanged between process image pairs.

`PRLO` terminates an existing session between an image pair and releases driver resources.

## Fibre Channel Layers

`FC-0`: Physical interface, transmission, signalling, cables/connectors

`FC-1`: `8b/10b` encode/decode, link control, ordered set specifications

`FC-2`: Framing, flow control, classes, exchange/sequence management

`FC-3`: Application-specific layer for encryption, compression, `RAID` striping

`FC-4`: Protocol mapping of existing protocols and native `FC` protocols

![Figure 4.9: FC layers](images/Fig_4.9.png)

Figure 4.9: FC layers

- `OX_ID` Unique 16-bit ID set by the exchange originator
- `RX_ID` Unique 16-bit ID set by the exchange responder

There are multiple exchanges active at any time.

![Figure 4.10: FC exchange, sequence, frame and word](images/Fig_4.10.png)

Figure 4.10: FC exchange, sequence, frame and word

Upper layer protocols (`ULPs`), such as `SCSI`, `ESCON`, and `IP` are mapped to the `FC-4` layer for transmission:

- Information units are `ULP` units that are mapped into `FC` sequences.
- Sequences are uni-directional collections of frames making up a single group of information from one `FC` client to another.
- Information units consist of one or more chunks that are mapped onto frames.
- A frame consists of `SOF`, header, payload, `CRC` and `EOF`.
- Frames are individual units of transfer that can typically contain mapped commands or data packets from `ULPs`.
- The maximum frame payload size is 2112 bytes (including optional headers) with a typical maximum data payload of 2048 bytes.
- The receiving port may only be able to handle 2KB or 1KB frames, so the `FC-4` layer must break up information units into correctly sized chunks for delivery by `FC`.

Exchanges are bi-directional groups of sequences which describe a conversation between the two nodes.

FC constructs can be compared to grammatical equivalents in the following way:

- Words are the basic unit of conversation in both speech and `FC`.
- Frames are complete collections of words, and relate to complete thoughts, or sentences.
- Sequences are the collection of frames in a transmission by a single sequence initiator, represented as a paragraph in written speech.

Exchanges are conversations between nodes that consist of multiple sequences:

- The exchange is the mechanism used by two `FC` ports to identify and manage an operation between them.
- An exchange is opened whenever an operation is started between two ports. The exchange is closed when this operation ends.

In summary, `FC` constructs are similar to grammatical equivalents. Word is also similar to word in any language. `FC` frame (36 to 2148 bytes) is equivalent to Sentence. Sequence (uni-directional) is like paragraph and exchange (bi-directional) is like conversation.

## Classes of Service

`FC-2` provides different classes of service (`CoS`) for different levels of delivery guarantee, bandwidth, and connectivity. Different applications require different levels of these services.

### Class 1

**Characteristics**: Exclusive connection-oriented, 100% reserved bandwidth, in order frame delivery of frame, confirmed delivery

**Usage**: Specialized applications; not widely supported

### Class 2

**Characteristics**: Frame-switched, meaning a frame or packet of data is routed to a destination based on the address in the frame or packet header, connectionless, confirmed delivery

**Usage**: Clustering, `OLTP`

### Class 3

**Characteristics**: Frame-switched, connectionless, no delivery confirmation, controlled environments

**Usage**: Most commonly implemented in `FC` fabrics today

### Class 4

**Characteristics**: Fractional or shared bandwidth, connection-oriented through virtual circuit, in order frame delivery and confirmed delivery

**Usage**: Specialized applications, best recommended for a multi-media, such as video/audio application, not widely supported

| Note: Class 5 is not defined. |
| --- |

### Class 6
