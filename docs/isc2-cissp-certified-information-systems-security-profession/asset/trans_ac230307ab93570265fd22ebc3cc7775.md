
The OSI model divides networking tasks into seven distinct layers. Each layer is responsible for performing specific tasks or operations for the ultimate goal of supporting data exchange (in other words, network communication) between two computers. The layers are always numbered from bottom to top (see [Figure 11.1](#c11.xhtml#figure11-1)). They are referred to by either their name or their layer number. For example, layer 3 is also known as the Network layer. The layers are ordered specifically to indicate how information flows through the various levels of communication. Each layer communicates directly with the layer above it as well as the layer below it, plus the peer layer on a communication partner system.

![FIGURE 11.1 Representation of the OSI model ](images/c11f001.jpg)

[**FIGURE 11.1**](#c11.xhtml#figureanchor11-1) Representation of the OSI model 

The OSI model is an open network architecture guide for network product vendors. This standard, or guide, provides a common foundation for the development of new protocols, networking services, and even hardware devices. By working from the OSI model, vendors are able to ensure that their products will integrate with products from other companies and be supported by a wide range of operating systems. If all vendors developed their own networking framework, interoperability between products from different vendors would be next to impossible.

The real benefit of the OSI model is its expression of how networking actually functions. In the most tangible sense, network communications occur over a physical connection (whether that physical connection is electrons over copper, photons over fiber, or radio signals through the air). Physical devices establish channels through which electronic signals can pass from one computer to another. These physical device channels are only one type of the seven logical communication types defined by the OSI model. Each layer of the OSI model communicates via a logical channel with its peer layer on another computer. This enables protocols based on the OSI model to support a type of authentication by being able to identify the remote communication entity as well as authenticate the source of the received data.

### Encapsulation/Deencapsulation

Protocols based on the OSI model employ a mechanism called encapsulation. *Encapsulation* is the addition of a header, and possibly a footer, to the data received by each layer from the layer above before it’s handed off to the layer below. As the message is encapsulated at each layer, the previous layer’s header and payload combine to become the payload of the current layer. Encapsulation occurs as the data moves down through the OSI model layers from Application to Physical. The inverse action occurring as data moves up through the OSI model layers from Physical to Application is known as *deencapsulation*. The encapsulation/deencapsulation process is as follows:

1.  The Application layer creates a message.

2.  The Application layer passes the message to the Presentation layer.

3.  The Presentation layer encapsulates the message by adding information to it. Information is usually added only at the beginning of the message (called a header); however, some layers also add material at the end of the message (called a footer), as shown in [Figure 11.2](#c11.xhtml#figure11-2).

4.  The process of passing the message down and adding layer-specific information continues until the message reaches the Physical layer.

5.  At the Physical layer, the message is converted into electrical impulses that represent bits and is transmitted over the physical connection.

6.  The receiving computer captures the bits from the physical connection and re-creates the message in the Physical layer.

7.  The Physical layer converts the message from bits into a Data Link frame and sends the message up to the Data Link layer.

8.  The Data Link layer strips its information and sends the message up to the Network layer.

9.  This process of deencapsulation is performed until the message reaches the Application layer.

10.  When the message reaches the Application layer, the data in the message is sent to the intended software recipient.

![FIGURE 11.2 Representation of OSI model encapsulation](images/c11f002.jpg)

[**FIGURE 11.2**](#c11.xhtml#figureanchor11-2) Representation of OSI model encapsulation

The information removed by each layer contains instructions, checksums, and so on that can be understood only by the peer layer that originally added or created the information (see [Figure 11.3](#c11.xhtml#figure11-3)). This information is what creates the logical channel that enables peer layers on different computers to communicate.

![FIGURE 11.3 Representation of the OSI model peer layer logical channels ](images/c11f003.jpg)

[**FIGURE 11.3**](#c11.xhtml#figureanchor11-3) Representation of the OSI model peer layer logical channels 

The message sent into the protocol stack at the Application layer (layer 7) is called the data stream. It retains the label of data stream (or sometimes the label of *protocol data unit \[PDU\]* is applied) until it reaches the Transport layer (layer 4), where it is called a *segment* (TCP protocols) or a *datagram* (User Datagram Protocol \[UDP\] protocols). In the Network layer (layer 3), it is called a *packet*. In the Data Link layer (layer 2), it is called a *frame*. In the Physical layer (layer 1), the data has been converted into *bits* for transmission over the physical connection medium. [Figure 11.4](#c11.xhtml#figure11-4) shows how each layer changes the data through this process.

![FIGURE 11.4 OSI model data names ](images/c11f004.jpg)

[**FIGURE 11.4**](#c11.xhtml#figureanchor11-4) OSI model data names 

### OSI Layers

Understanding the functions and responsibilities of each layer of the OSI model will help you understand how network communications function, how attacks can be perpetrated against network communications, and how security can be implemented to protect network communications. We discuss each layer, starting with the bottom layer, in the following sections.

**Remember the OSI** To make the most of the OSI, you must first be able to remember the names of the seven layers in their proper order. One common method of memorizing them is to create a mnemonic from the initial letters of the layer names so they are easier to remember. One of our favorites is Please Do Not Teach Surly People Acronyms. Do take note that this memorization mnemonic works from the Physical layer up to the Application layer. A mnemonic working from the Application layer down is All Presidents Since Truman Never Did Pot. There are many other OSI memorization schemes out there; just be sure you know whether they are top-down or bottom-up.

#### Physical Layer

The *Physical layer (layer 1)* accepts the frame from the Data Link layer and converts the frame into bits for transmission over the physical connection medium. The Physical layer is also responsible for receiving bits from the physical connection medium and converting them into a frame to be used by the Data Link layer.

The Physical layer contains the device drivers that tell the protocol how to employ the hardware for the transmission and reception of bits. Located within the Physical layer are electrical specifications, protocols, and interface standards such as the following:

*   EIA/TIA-232 and EIA/TIA-449

*   X.21

*   High-Speed Serial Interface (HSSI)

*   Synchronous Optical Networking (SONET)

*   V.24 and V.35

Through the device drivers and these standards, the Physical layer controls throughput rates, handles synchronization, manages line noise and medium access, and determines whether to use digital or analog signals or light pulses to transmit or receive data over the physical hardware interface.
