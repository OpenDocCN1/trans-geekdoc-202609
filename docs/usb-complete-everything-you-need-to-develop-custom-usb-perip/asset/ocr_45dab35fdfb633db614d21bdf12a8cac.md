# Hub-class Requests

All hubs accept or return data for seven of the USB’s eleven standard requests. Some 2.0 hubs support an additional request. Of the other standard requests, one is optional and the other two are undefined for hubs. Like all devices, hubs must return STALL for unsupported requests.

Hubs respond in the standard way to Clear_Feature, Get_Configuration, Get_Descriptor, Get_Status, Set_Address, Set_Configuration, and Set_Feature requests. Set_Descriptor is optional and should return STALL if not supported. Only 2.0 hubs that support multiple transaction translators support Get_Interface and Set_Interface. A hub can’t have an isochronous endpoint, so Synch_Frame is undefined for hubs.

The hub class defines eight hub-specific requests that build on the standard requests with hub-specific values. For example, a Get_Status request directed to a hub with Index = 0 causes the hub to return a value in a Data packet indicating whether the hub is using an external power supply and whether an over-current condition exists.

Table 15-2 shows the hub-specific requests. One request from the 1.x specification, Get_Bus_State, isn’t included in the 2.0 spec. This request enables the host to read the states of D+ and D- at a specified port on the hub.

The host uses many of the hub-specific requests to monitor and control the status of the hub and its ports. Get_Hub_Status reads status bits in a hub. Set_Hub_Feature and Clear_Hub_Feature set and clear status bits in a hub. Table 15-3 shows the bits and their meanings. In a similar way, Get_Port_Status, Set_Port_Feature, and Clear_Port_Feature enable the host to read and control status bits for a selected port in a hub. Table 15-4 shows the bits and their meanings.

In 2.0 hubs, Set_Port_Feature can place a port in one of five Test Modes. Chapter 18 has more about these modes.

The four new requests in the 2.0 spec all relate to monitoring and controlling the transaction translator (TT). The requests enable the host to clear a buffer in the TT, stop the TT, retrieve the state of a stopped TT using a vendor-specific format, and restart the TT by resetting it.