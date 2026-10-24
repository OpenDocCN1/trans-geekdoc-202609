```
void GetInputReport0(void)
{
    byte count;
    // Set pSrc.bRam to point to the report.
    pSrc.bRam = (byte*)&hid_report_in;
}
```

Listing 11-6: The GetInputReport0 function handles report-specific tasks.

When Output report 0 arrives in the Data stage of the transfer, the Framework firmware makes the data available at the RAM location pointed to by pDst.bRam and manages the sending of a zero-length packet in the transfer’s Status stage. In this example, pDst.bRam has been set to point to the char array hid_report_out. The firmware can call a function that uses the report data:

```
if (ctrl_trf_session_owner == MUID_HID)
{
    // Call a function that uses the report data.
    HandleControlOutReport();
}
```

The code for receiving other reports, including Output reports with other report IDs and Feature reports, is much the same except that the firmware’s use of the report’s contents will change depending on the report.