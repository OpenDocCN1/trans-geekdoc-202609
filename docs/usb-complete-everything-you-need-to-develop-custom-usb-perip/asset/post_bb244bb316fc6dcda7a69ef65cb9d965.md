
Table 11-2: The HID class descriptor has 7 or more fields in 9 or more bytes.

| Offset (decimal) | Field | Size (bytes) | Description |
|---|---|---|---|
| 0 | bLength | 1 | Descriptor size in bytes. |
| 1 | bDescriptorType | 1 | This descriptor's type: 21h to indicate the HID class. |
| 2 | bcdHID | 2 | HID specification release number (BCD). |
| 4 | bCountryCode | 1 | Numeric expression identifying the country for localized hardware (BCD). |
| 5 | bNumDescriptors | 1 | Number of subordinate report and physical descriptors. |
| 6 | bDescriptorType | 1 | The type of a class-specific descriptor that follows. (A report descriptor (required) is type 22h.) |
| 7 | wDescriptorLength | 2 | Total length of the descriptor identified above. |
| 9 | bDescriptorType | 1 | Optional. The type of a class-specific descriptor that follows. A physical descriptor is type 23h. |
| 10 | wDescriptorLength | 2 | Total length of the descriptor identified above. Present only if bDescriptorType is present immediately above. May be followed by additional bDescriptorType and wDescriptorLength fields to identify additional physical descriptors. |

The descriptor has two or more bDescriptorType fields. One identifies the HID descriptor and the other(s) identify the type of a subordinate descriptor.

### The Descriptor

**bLength.** The length in bytes of the descriptor.

**bDescriptorType.** The value 21h indicates a HID descriptor.

### The Class

**bcdHID.** The HID specification number that the interface complies with. In BCD format. Version 1.0 is 0100h; Version 1.1 is 0110h.

**bCountryCode.** If the hardware is localized for a specific country, this field is a code identifying the country. The HID specification lists the codes. If the hardware isn't localized, this field is 00h.

## Human Interface Devices: Using Control and Interrupt Transfers

```text
0x06  0xFFA0      Usage Page (vendor-defined)
0x09  0x01        Usage (vendor-defined)
0xA1  0x01        Collection (Application)

0x09  0x03        Usage (vendor-defined)
0x15  0x00        Logical Minimum (0)
0x26  0x00FF      Logical Maximum (255)
0x95  0x02        Report Count (2)
0x75  0x08        Report Size (8 bits)
0x81  0x02        Input (Data, Variable, Absolute)

0x09  0x04        Usage (vendor-defined)
0x15  0x00        Logical Minimum (0)
0x26  0x00FF      Logical Maximum (255)
0x75  0x08        Report Size (8 bits)
0x95  0x02        Report Count (2)
0x91  0x02        Output (Data, Variable, Absolute)

0x09  0x05        Usage (vendor-defined)
0x15  0x00        Logical Minimum (0)
0x26  0x00FF      Logical Maximum (255)
0x75  0x08        Report Size (8 bits)
0x95  0x02        Report Count (2)
0xB1  0x02        Feature (Data, Variable, Absolute)

0xC0              End Collection
```

Listing 11-2: This report descriptor defines an Input report, an Output report, and a Feature report. Each report transfers two vendor-defined bytes.

The report descriptor defines items that a report can contain. Here is what each item in the example descriptor specifies:

The Usage Page item is identified by the value 06h and specifies the general function of the device, such as generic desktop control, game control, or alphanumeric display. In the example descriptor, the Usage Page is the vendor-defined value FFA0h. The HID specification lists values for different Usage Pages and values reserved for vendor-defined Usage Pages.

The Usage item is identified by the value 09h and specifies the function of an individual report in a Usage Page. For example, Usages available for generic desktop controls include mouse, joystick, and keyboard. Because the example's Usage Page is vendor-defined, all of the Usages in the Usage Page are vendor-defined also. In the example, the Usage is 01h.

The **Collection (Application)** item begins a group of items that together perform a single function, such as keyboard or mouse. Each report descriptor must have an application collection.

The Collection contains three reports. Each report has these items:

- A vendor-defined Usage applies to the data in the report.
- A Logical Minimum and Logical Maximum specify the range of values that the report can contain.
- The Report Count item indicates how many data items the report contains. In the example, each report contains two data items.
- The Report Size item indicates how many bits are in each reported data item. In the example, each data item is eight bits.
- The final item specifies whether the report is an Input report (81h), Output report (91h), or Feature report (B1h). The bits provided with the item contain additional information about the report data.

The End Collection item closes the Application Collection.

Chapter 12 has more about report formats.

### HID-specific Requests

Table 11-3: The HID class defines six HID-specific requests.

| Request Number | Request | Data Source (Data stage) | wValue (high byte, low byte) | wIndex | Data Length (bytes) (wLength) | Data Stage Contents | Required? |
|---|---|---|---|---|---|---|---|
| 01h | Get_Report | device | report type, report ID | interface | report length | report | yes |
| 02h | Get_Idle | device | 0, report ID | interface | 1 | idle duration | no |
| 03h | Get_Protocol | device | 0 | interface | 1 | protocol | required for HIDs that support a boot protocol |
| 09h | Set_Report | host | report type, report ID | interface | report length | report | no |
| 0Ah | Set_Idle | no Data stage | idle duration, report ID | interface | – | – | no, except for keyboards using the boot protocol |
| 0Bh | Set_Protocol | no Data stage | 0, protocol | interface | – | – | required for HIDs that support a boot protocol |

**Get_Report**

**Purpose:** The host requests an Input or Feature report from a HID using a control transfer.

**Request Number (bRequest):** 01h

**Source of Data:** device

**Data Length (wLength):** length of the report

**Contents of wValue field:** The high byte contains the report type (1=Input, 3=Feature), and the low byte contains the report ID. The default report ID is zero.

**Contents of wIndex field:** the number of the interface the request is directed to.

**Contents of data packet in the Data stage:** the report

**Comments:** All HIDs must support this request. See also Set_Report

**Get_Idle**

**Purpose:** The host reads the current Idle rate from a HID.

**Request Number (bRequest):** 02h

**Source of Data:** device

**Data Length (wLength):** 1

**Contents of wValue field:** The high byte is zero. The low byte indicates the report ID that the request applies to. If the low byte is zero, the request applies to all of the HID's Input reports.

**Contents of wIndex field:** the number of the interface that supports this request.

**Contents of data packet in the Data stage:** the Idle rate, expressed in units of 4 milliseconds.

**Comments:** See Set_Idle for more details. HIDs aren't required to support this request.

**Get_Protocol**

**Purpose:** The host learns whether the boot or report protocol is currently active in the HID.

**Request Number (bRequest):** 03h

**Source of Data:** device

**Data Length (wLength):** 1

**Contents of wValue field:** 0

**Contents of wIndex field:** the number of the interface that supports this request.

**Contents of data packet in the Data stage:** The protocol (0 = boot protocol, 1 = report protocol).

**Comments:** Boot devices must support this request. See also Set_Protocol.
