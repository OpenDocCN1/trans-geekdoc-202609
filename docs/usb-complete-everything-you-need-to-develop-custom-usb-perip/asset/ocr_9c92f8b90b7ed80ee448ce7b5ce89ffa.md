# Clear_Feature

**Purpose:** The host requests to disable a feature on a device, interface, or endpoint.

**Request Number (bRequest):** 01h.

**Source of Data:** no Data stage

**Data Length (wLength):** none

**Contents of wValue field:** the feature to disable

**Contents of wIndex field:** For a device feature, 0. For an interface feature, the interface number. For an endpoint feature, the endpoint number.

**Contents of data packet in the Data stage:** none.

**Supported states:** Default: undefined. Address: OK for address 0, Endpoint 0. Otherwise the device returns a STALL. Configured: OK.

**Behavior on error:** If the feature, device, or endpoint specified doesn’t exist, or if the feature can’t be cleared, the device responds with a STALL. Behavior is undefined when wLength is greater than 0.

**Comments:** This request can clear the DEVICE_REMOTE_WAKEUP feature and the ENDPOINT_HALT feature, but not the TEST_MODE feature. Clear_Feature(ENDPOINT_HALT) resets the endpoint’s data toggle to DATA0. See also Set_Feature and Get_Status.