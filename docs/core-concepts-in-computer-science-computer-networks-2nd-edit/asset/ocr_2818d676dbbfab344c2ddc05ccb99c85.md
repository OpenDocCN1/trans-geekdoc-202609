# CORE CONCEPT: THE OSI MODEL

OSI (Open Systems Interconnection) is a reference model for how applications communicate over a network. A reference model is a conceptual framework for understanding relationships. The purpose of the OSI reference model is to guide vendors and developers so the digital communication products and software programs they create can operate, and to facilitate a clear framework that describes the functions of a networking or telecommunication system.

International standards organization/open system interconnection (ISO/OSI) model is a standard reference model for communication between two ends in a network. It can be helpful to have a basic understanding of how the network works in order to troubleshoot future problems.

It would be difficult to overstate the importance of the OSI model. Virtually all networking vendors and users understand how important it is that network computing products adhere to and fully support the networking standards this model has generated. When a vendor's products adheres to the ISO model has generated, connecting those products to other vendors' products is relatively simple. Conversely, the further a vendor departs from those standards, the more difficult it becomes to connect that vendor's products to those of other vendors.

In addition, if a vendor were to depart from the communication standards the model has engendered, software development efforts would be very difficult because the vendor would have to build every part of all necessary software, rather than being able to build on the existing work of other vendors.

The first two problems give rise to a third significant problem for vendors: a vendor's products become less marketable as they become more difficult to connect with other vendors' products.

Thus, the ISO model defines a networking framework for implementing protocols according to layers. Each layer is functionally independent of the others, but provides services to the layer above and it receives services from the layer below.

The layers are in two groups. The upper layers are used whenever a message passes from or to a user. The lower layers are used when any message passes through the host computer. Messages intended for this computer pass to the upper layers but are not passed to another host.

# Layers of OSI Model

Layers of OSI model are as follows:

+   - Application layer