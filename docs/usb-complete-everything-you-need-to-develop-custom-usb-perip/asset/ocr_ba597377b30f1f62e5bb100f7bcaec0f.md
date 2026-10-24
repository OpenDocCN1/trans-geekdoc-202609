# # Other Control Requests

In addition to the requests defined in the USB 2.0 specification, a device may respond to class-specific and vendor-specific control requests.

# ## Class-specific Requests

A class may define requests for devices in its class. A class-specific request may be required or optional for devices in the class. Some requests are unrelated to the standard requests, while others build on the standard requests by defining class-specific fields in a request. An example of a request that’s unrelated to the standard requests is the Get_Max_LUN request supported by some mass-storage devices. The host uses this request to find out the number of logical units the interface supports. An example of a request that builds on an existing request is the Get_Port_Status request that hubs must support. This request is structured like the standard Get_Status request. But Get_Port_Status has different values in two fields. In bmRequestType, bits 6 and 5 are 01 to indicate that the request is defined by a standard USB class, and bits 4 through 0 are 00011 to indicate that the request applies to a unit other than the device or an interface or endpoint. (The request applies to a port on a hub.) The wIndex field holds the port number.

# ## Vendor-specific Requests

A vendor may define custom requests for control transfers with specific devices. Implementing a custom request in a control transfer requires all of the following:

+   - Vendor-defined fields as needed in the Setup and optional Data stages of the request. Bits 6 and 5 in the Setup stage’s data packet are set to 10 to indicate a vendor-defined request.
+   - In the device, code that detects the request number in the Setup packet and knows how to respond.
+   - In the host, a vendor-specific device driver to initiate the request. Applications can’t initiate vendor-specific requests on their own. The application must call a function exposed by a driver that defines the request.