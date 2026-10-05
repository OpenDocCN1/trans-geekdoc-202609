# OSI Model

| Layer Number | Layer Name | Layer Type | Encapsulation / Protocol Data Unit (PDU) | Function |
|---|---|---|---|--|
| 1 | Physical | Media | Bits and Signaling | Converts the data into the stream of electric or analog pulses that will actually cross the medium and oversee the transmission of the data. It is responsible for characteristics of the signaling as voltage levels, timing and clock rates, maximum transmission distances, and the physical connectors used. It activates and deactivates physical link |

FIGURE 1.1 The OSI model.

The Data Link Layer has two sub-layers, the Logical Link Control (LLC) and the Media Access Control (MAC). LLC is responsible for error correction, flow control, and Service Access Points. The Media Access Control (MAC) is responsible for physical addressing and providing access to shared physical media (wire). It is assigned by the manufacturer. The Ethernet is a standardized way of connecting computers to create a network. Figure 1.2 illustrates the OSI model devices and protocols.

| Layer Number | Layer Name | Network Device | Protocols |
|---|---|---|--|
| 7 | Application | PC | • Simple Mail Transport Protocol (SMTP)<br>• Terminal emulation protocol (Telnet)<br>• File Transfer Protocol (FTP)<br>• Trivial File Transfer Protocol (TFTP)<br>• HyperText Transfer Protocol (HTTP) |
| 6 | Presentation | PC | • ASCII (text)<br>• EBCDIC (text)<br>• JPEG (image)<br>• GIF (image)<br>• TIFF (image)<br>• MPEG (sound/video)<br>• Quicktime (sound/video) |
| 5 | Session | PC | • Session Control Protocol (SPC)<br>• Remote Procedure Call (RPC) from Unix<br>• Zone Information Protocol (ZIP) from AppleTalk |