All of these applications and services are server based. Interoperability between these services can be achieved through a server-based approach via XMPP or through multiple protocol clients. As usual, security of all of these applications rests in the strength of the protocol, quality of the implementation, trustworthiness of the operator, and behavior of the user. If these applications are to be used in a business context, stringent architectural and policy measures need to be put in place to prevent security gaps.

This is all the more important as many instant messaging applications by design support a variety of communication channels, offer the ability to tunnel through HTTP, and offer online awareness services that can be misused for technical or social attacks. While there are many business and personal benefits and efficiencies to be gained from adopting instant messaging/chat/IRC technologies, there are also many risks. These risks are faced both by private citizens and businesses trying to protect the integrity of their logical assets (networks, servers, workstations, data, and intellectual property):

# Authenticity

User identification can be easily faked in instant messaging and chat applications by:

+   - Choosing a misleading identity upon registration or changing one's nickname while online.
+   - Manipulating the directory service if the application requires one.
+   - Manipulating either the attacker's or the target's client to send or display a wrong identity.

Although these risks are inherent to all kinds of communication networks (and are also common in email), they present an increased risk in real-time communication, where a user potentially has less time to analyze the communication presented to him or her. Similarly, the continued growth of social networking services and sites like Facebook, Vine, KiK, Twitter, LinkedIn, and others present ample opportunity to create false identity and try and dupe others for criminal purposes.

# Confidentiality

Many chat systems transmit their information in cleartext. Similar to unencrypted email, information can be disclosed by sniffing on the network. A different form of confidentiality breach may occur based upon the fact that chat applications can generate an illusion and expectation of privacy, e.g., by establishing "closed rooms." Depending on the kind of infrastructure used, all messages can however be read in cleartext by privileged users such as the chat system's operators.