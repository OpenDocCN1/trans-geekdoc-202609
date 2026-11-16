+   2. Push–pull
+   3. Publisher–subscribe
+   4. Exclusive pair

The communication devices are used to establish communication between
the client and the server.

+   1. **Services:** Various types of services are used in IoT. The most apt example
+   of this would be the monitoring of crops.
+   
+   2. **Security:** Security consists of various protocols that govern the applica-
+   tion. Some of the protocols that are used are LoRa, cellular networks, etc.
+   
+   3. **Application:** The application block acts as an interface.
+   
+   4. **Management:** The management block is used to govern various sys-
+   tems in the application.

# 16.4.7 Implementation model for digital twins (Figure 16.12)

# 16.4.8 Control model of the weeding use case (Figure 16.13)

The below use case is that of weed control. The decision maker consists of the
prediction of yield and the harvest plan. The crop growth is monitored, and
the weed pressure is also monitored. The digital twin holds the field, weeds,
weeding machine, and lettuce. The effector controls the weeds and the har-
vesting. These are taken care of by the weeding machine and the harvesting
machine, respectively. The sensor is used to sense the weed pressure and crop
growth rate from the weeding machine and the field, respectively [14]. These
data are collected by the sensor and sent to the digital twins. The physical
objects consist of the weeding machine, the planting machine, the field, and
the harvesting machine. The planting machine corresponds to young plants.
The weeding machine corresponds to the weeds. The harvesting machine dis-
plays the amount of lettuce harvested. The field displays the amount of lettuce
growth and the weeds. The data is collected from the customers and passed on
to the digital twin, which processes the data in the corresponding areas and is
then sent to the discriminator. Finally, the source produces the lettuce, which
is harvested and finally delivered to the customer from the supplier.

The figure is that of the digital twin implementation model of the above
use case. The explanation is going to be a bottom-up approach. The func-
tional block diagram has already been discussed in this chapter. Now, some
of the use cases and applications are discussed below. The management and