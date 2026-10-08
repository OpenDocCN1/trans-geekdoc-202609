basis. (TLS stands for Transport Layer Security. AMQP stands for Advanced Message Queuing Protocol, an open standard application layer protocol for message-oriented middleware.)

Corda nodes discover each other via the Network Map Service. The network map service publishes the IP addresses through which every node on the network can be reached. Also, it broadcasts the identity certificates of those nodes and the services they provide. You can imagine the service as a phone book, which publishes a list of peer nodes containing information.

# 7.2.5 The Doorman

Corda networks are semi-private, which means it needs to impose a kind of gateway control before a node can join a network. This control is called doorman. Each network has a doorman service that enforces rules regarding the information that nodes must provide. These nodes need to go through the know-your-customer (KYC) process before being admitted to the network.

To join the network, a node must contact the doorman and provide the required information. If the doorman is satisfied, the node will receive a root-authority-signed TLS certificate from the network's provisioning service. This certificate certifies the node's identity when communicating with other participants on the network.