![](bbox=[0.12, 0.08, 0.88, 0.47])

Click the Check for New Firmware button and then follow the TCP stream within Wireshark. We now see that the device goes to http://wrpd.dlink.com.tw/router/firmware/query.asp?model=DAP-1320_Ax_Default in the first two lines and the response is XML-encoded data, as shown next.

![](bbox=[0.12, 0.57, 0.88, 0.83])

By going to the URL we captured, we can see that the XML contains the FW version's major and minor numbers, the download site, and release notes.