intercept the traffic, hack the VoIP server, or launch DoS attacks against VoIP servers and cause network outages. Attacks against IP phones are also problematic, as are LAN hopping and TFTP alteration for phone firmware image loading. Another consideration is that the vulnerabilities of the operating system the VoIP application is running on are inherited.

One key concern with VoIP is sniffing because protocols like SIP provide little security by default. Without the proper security controls, sniffing a VoIP call can be as easy as using the common network sniffer Wireshark. One security issue related to VoIP is loss of the data network, which can disable VoIP. Other VoIP vulnerabilities include the following:

+   **Open network**: After VoIP packets leave an organization’s network, the network is not in charge of where they are routed or who might have access to them. Therefore, any unencrypted traffic could potentially be recovered.

+   **DoS attacks**: Because VoIP uses UDP for portions of the communication process, it is extremely susceptible to disruption and DoS attacks. VoIP uses an isochronous process in which data must be delivered within strict timelines.

+   **Eavesdropping**: Because VoIP relies on UDP and Session Initiation Protocol (SIP), it is an open service, and communications can potentially be sniffed and replayed. Other protocols used by various vendors of VoIP products include IAX, IAX2, SCCP, and UNISTIM.

+   **Unauthorized phone use**: Services like Skype and GoogleTalk open a corporate network to exposure to attack and potential policy violations. Such tools can even result in violations of regulation, depending on the industry or how they are used.

+   **Spam over Internet Telephony (SPIT)**: SPIT is bulk unsolicited SPAM delivered using VoIP.

> **Note** You can use Secure Real-Time Transport Protocol (SRTP) to secure VoIP. SRTP uses AES for confidentiality and SHA-1 for integrity.