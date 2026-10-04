
The application layer, in particular, seems out of place in a model of network transport. Why should the application using the data be considered part of the transport system? Because early systems considered the *human user* the ultimate user of the data, and the application as primarily a way to munge data to be presented to the actual user. Much of the machine-to-machine processing, heavy processing of data before it is presented to a user, and simple storage of information in digital format were not even considered viable use cases. As information was being transferred from one person to another, the application was just considered a part of the transport system.

Two other points might help the inclusion of the application make more sense. First, in the design of these original systems, there were two components: a terminal and a host. The terminal was really a display device; the application lived on the host. Second, the networking software was not thought of as a separate “thing” in the system; routers had not yet been invented, nor any other separate device to process and forward packets. Rather, a host was just connected to either a terminal or another host; the network software was just another application running on these devices.

Over time, as the OSI model came into more regular use, the DoD model was modified to include more layers. For instance, in [Figure 3-2](#ch03.xhtml#ch03fig02), a diagram replicated from a 1983 paper on the DoD model, there are seven layers (seven being a magic number for some reason).^([1](#ch03.xhtml#ch03fn-1))

![Image](graphics/03fig02.jpg)

**Figure 3-2** *A Later Version of the DoD Model*

Here three layers have been added:

• The utility layer is a set of protocols living between the more generic transport layer and applications. Specifically, the Simple Mail Transfer Protocol (SMTP), File Transfer Protocol (FTP), and other protocols were seen as being a part of this layer.

• The network layer from the four-layer version has been divided into the network layer and the internetwork layer. The network layer represents the differing packet formats used on each link type, such as radio networks and Ethernet (still very new in the early 1980s). The internetwork layer unifies the view of the applications and utility protocols running on the network into a single internet datagram service.

• The link layer has been inserted to differentiate between the encoding of information onto the various link types and a device’s connection to the physical link. Not all hardware interfaces provided a link layer.

Over time, these expanded DoD models fell out of favor; the four-layer model is the one most often referenced today. There are several reasons for this:

• The utility and application layers are essentially duplicates of one another in most cases. FTP, for instance, multiplexes content on top of the Transmission Control Protocol (TCP), rather than as a separate protocol or layer in the stack. TCP and the User Datagram Protocol (UDP) eventually solidified as the two protocols in the transport layer, with everything else (generally) running on top of one of these two protocols.

• With the invention of devices primarily intended to forward packets (routers and switches), the separation between the network and internetwork layers was overcome by events. The original differentiation was primarily between lower-speed long haul (wide area) links and shorter-run local area links; routers generally took the burden of installing links into wide area networks out of the host, so the differentiation became less important.

• Some interface types simply do not have a way to separate signal encoding from the host interface, as was envisioned in the split between the link and physical layers. Hence these two layers are generally munged into a single “thing” in the DoD model.

The DoD model is historically important because

• It is one of the first attempts to codify network functionality into a model.

• It is the model on which the TCP/IP suite of protocols (on which the global Internet operates) was designed; the artifacts of this model are important in understanding many aspects of TCP/IP protocol design.

• It had the concept of multiple protocols at any particular layer in the model “built in.” This set the stage for the overall concept of narrowing the focus of any particular protocol, while allowing many different protocols to operate at once over the same network.

### Open Systems Interconnect (OSI) Model

In the 1960s, carrying through to the 1980s, the primary form of communications was the switched circuit; a sender would ask a network element (a switch) to connect it to a particular receiver, the switch would complete the connection (if the receiver was not busy), and traffic would be transmitted over the resulting circuit. If this sounds like a traditional telephone system, this is because it is, in fact, based on the traditional network system (now called Plain Old Telephone Service \[POTS\]). Large telephone and computer companies were deeply invested in this model, and received a lot of revenue from systems designed around circuit switching techniques. As the DoD model (and its set of accompanying protocols and concepts) started to catch on with researchers, these incumbents decided to build a new standards organization that would, in turn, build an alternate system providing the “best of both worlds.” They would incorporate the best elements of packet switching, while retaining the best elements of circuit switching, creating a new standard that would satisfy everyone. In 1977, this new standards organization was proposed, and adopted, as part of the International Organization for Standardization (ISO).

This new ISO working group designed a layered model similar to the proposed (and rejected) packet-based model, grounded in database communications. The primary goal was to allow intercommunication between the large database-focused systems dominant in the late 1970s. The committee was divided between telecom engineers and the database contingent, making the standards complex. The protocols developed needed to provide for both connection-oriented and connectionless session control, and invent the entire application suite to create email, file transfer, and many other applications (remember, *applications are part of the stack)*. For instance, various transport modes needed to be codified to carry a wide array of services. In 1989—a full ten years later—the specifications were still not completely done. The protocol had not reached widespread deployment, even though many governments, large computer manufacturers, and telecom companies supported it over the DoD protocol stack and model.

But during the ten years the DoD stack continued to develop; the Internet Engineering Task Force (IETF) was formed to shepherd the TCP/IP protocol stack, primarily for researchers and universities (the Internet, as it was then known, did not allow commercial traffic, and would not until 1992). With the failure of the OSI protocols to materialize, many commercial networks, and networking equipment, turned to the TCP/IP protocol suite to solve real-world problems “right now.”

Further, because the development of the TCP/IP protocol stack was being paid for under grants by the U.S. government, the specifications were free. There were, in fact, TCP/IP implementations written for a wide range of systems available because of the work of universities and graduate students who needed the implementations for their research efforts. The OSI specifications, however, could only be purchased in paper form from the ISO itself, and only by members of the ISO. The ISO was designed to be a “members only” club, meant to keep the incumbents firmly in control of the development of packet switching technology. The “members only” nature of the organization, however, worked against the incumbents, eventually playing a role in their decline.
