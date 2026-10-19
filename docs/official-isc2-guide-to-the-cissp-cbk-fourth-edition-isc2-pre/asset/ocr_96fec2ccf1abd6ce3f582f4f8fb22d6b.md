SYN the client initiated. The process of acknowledging the client’s request allows the server to increment the client’s sequence number by one and uses it as its acknowledgement number.

3. Third, the client sends an ACK in order to acknowledge the request from the server for synchronization. The client uses the same algorithm the server implemented in providing an acknowledgement number. The client’s acknowledgment of the server’s request for synchronization completes the process of establishing a reliable connection.

For a listing of protocols associated with layer 4 of the OSI model, see below:

+   - **ATP** — AppleTalk Transaction Protocol
+   - **DCCP** — Datagram Congestion Control Protocol
+   - **FCP** — Fiber Channel Protocol
+   - **RDP** — Reliable Datagram Protocol
+   - **SCTP** — Stream Control Transmission Protocol
+   - **SPX** — Sequenced Packet Exchange
+   - **SST** — Structured Stream Transport
+   - **TCP** — Transmission Control Protocol
+   - **UDP** — User Datagram Protocol
+   - **UDP Lite** — User Datagram Protocol Lite
+   - **μTP** — Micro Transport Protocol

# Layer 5: Session Layer

This layer provides a logical, persistent connection between peer hosts. A session is analogous to a conversation that is necessary for applications to exchange information. The session layer is responsible for creating, maintaining, and tearing down the session. Three modes are offered:

+   1. **Full Duplex** — Both hosts can exchange information simultaneously, independent of each other.
+   2. **Half Duplex** — Hosts can exchange information but only one host at a time.
+   3. **Simplex** — Only one host can send information to its peer. Information travels in one direction only.

For a listing of protocols associated with layer 5 of the OSI model, see below: