3. The JIT VM access configuration enables you to specify the ports and protocols to which JIT VM access will apply. The default ports and protocols are as follows:

+   - Port 22 (SSH)
- Port 3389 (RDP)
- Port 5985 (Remote PowerShell)
- Port 5986 (Remote PowerShell)

4. Do one of the following:

+   - If these are all the ports you want available for JIT VM access, click the Save button to save this configuration as is.
- If you want to omit any ports and protocols from the list, click the entry you want to omit and click Dis.
- If you want to add a port and protocol, click Add. The following steps assume you chose this option.

5. Clicking Add opens the Add port configuration page (see Figure 5-5.) Here, you configure the following settings:

+   - Port: This is the TCP or UDP port used by the protocol.
- Protocol: Typically, you'll choose TCP or UDP, but you can also click Any to configure non-UDP/TCP IP protocols. However, it would be unusual to use these IP protocols for management purposes-except possibly for GRE, which uses IP protocol 47.
- Allowed IPs: You have two options for this setting: Per request or CIDR block. If you choose Per request, whatever IP address is currently assigned to the client system will be allowed access to the VM. If you choose CIDR block, you can define a collection of IP addresses that client systems must have before they can connect to the resource.
- Max request time: This is the maximum amount of time the user can request access to the resource. The default value is 3 hours, but you can allow the user to ask for more (or less) time.

![](bbox=[0.115, 0.658, 0.415, 0.915])

FIGURE 5-5 Add port configuration