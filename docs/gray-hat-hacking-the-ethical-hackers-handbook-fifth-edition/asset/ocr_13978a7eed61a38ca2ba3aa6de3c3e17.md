pointers to the entry points for each command. The code searches for the command and jumps to the routine pointer that is adjacent to it. You will see the commands for “IPv6 Function,” “Download FW and language to DUT,” and “get_wan_ip,” as shown next. Note that the commands are in the form of the short name, function pointer, and long name. Because this is a lookup table, we need to find the beginning of the table in order to locate a cross-reference to it.

```
LOAD:00446754                 .word aIpv6             # "ipv6"
LOAD:00446758                 .word sub_40E790
LOAD:0044675C                 .word aIpv6Function     # "IPv6 Function"
LOAD:00446760                 .word aDownloadFwLp     # "download_fw_lp"
LOAD:00446764                 .word download_fw_and_lp
LOAD:00446768                 .word aDownloadFwAndL   # "Download FW and language to DUT"
LOAD:0044676C                 .word aGetWlanIp        # "get_wlan_ip"
LOAD:00446770                 .word sub_40D680
LOAD:00446774                 .word aGetWlanIp_0      # "Get wlan ip"
```

Although we have not completely traced the origin of the system call back to the root, it is safe to say that it points back to the cgi command to download the firmware. A few greps ① of the “download_fw_lp” string give us the origin ②③. At this point, we will move on to attempting to exploit the device through the firmware update.

```
①root@kali:~/DAP-1320/fmk/rootfs# grep -r download_fw_lp .
②./www/Firmware.htm:<input type="hidden" id="action" name="action" value="download_fw_lp">
Binary file ./bin/ssi matches
①root@kali:~/DAP-1320/fmk/rootfs# grep -C 7 download_fw_lp www/Firmware.htm
<form id="form3" name="form3" method="POST" action="apply.cgi">
<input type="hidden" id="html_response_page" name="html_response_page" value="Firmware.htm">
<input type="hidden" name="html_response_return_page" value="Firmware.htm">
<input type="hidden" id="html_response_message" name="html_response_message" value="dl_fw_lp">
<input type="hidden" id="file_link" name="file_link" value="">
<input type="hidden" id="file_name" name="file_name" value="">
<input type="hidden" id="update_type" name="update_type" value="">
③<input type="hidden" id="action" name="action" value="download_fw_lp">
</form>
```

# Dynamic Analysis with Hardware

The static analysis portion of the assessment is complete. From this point forward, we will be looking at the system as it runs. We need to set up an environment for intercepting requests from the device to the WAN, connect the DAP-1320 to our test network, and begin exercising the firmware update process. The end goal is to execute something on the wireless extender through command injection.