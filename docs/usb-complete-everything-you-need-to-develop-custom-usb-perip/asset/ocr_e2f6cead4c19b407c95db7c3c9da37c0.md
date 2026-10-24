# Chapter 5

Table 5-1: The USB specification defines eleven standard requests for Control transfers.

| Request Number | Request | Data source (Data stage) | Recipient | wValue | wIndex | Data Length (bytes) in Data stage (wLength) | Data (in Data stage) |
|---|---|---|---|---|---|---|---|
| 00h | Get_Status | device | device, interface, endpoint | 0 | device, interface, or endpoint | 2 | status |
| 01h | Clear_Feature | no Data stage | device, interface, endpoint | feature | device, interface, or endpoint | – | – |
| 03h | Set_Feature | no Data stage | device, interface, endpoint | feature | device, interface, or endpoint | – | – |
| 05h | Set_Address | no Data stage | device | device address | 0 | – | – |
| 06h | Get_Descriptor | device | device | descriptor type and index | device or language ID | descriptor length | descriptor |
| 07h | Set_Descriptor | host | device | descriptor type and index | device or language ID | descriptor length | descriptor |
| 08h | Get_Configuration | device | device | 0 | device | 1 | configuration |
| 09h | Set_Configuration | no Data stage | device | configuration | device | – | – |
| 0Ah | Get_Interface | device | interface | 0 | interface | 1 | alternate setting |
| 0Bh | Set_Interface | no Data stage | interface | interface | interface | – | – |
| 0Ch | Synch_Frame | device | endpoint | 0 | endpoint | 2 | frame number |