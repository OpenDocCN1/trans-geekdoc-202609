# 1. Preparing for the attack.

# 1.1. Release station PC1.

# 1.2. Create the Trojan.

From the list of attacks, choose the following path: “windows/meterpreter/reverse_tcp” and double-click. Then, from the drop-down option “Output”, choose the “.exe” option and click on the “Launch” button.

![](bbox=[0.235, 0.285, 0.765, 0.535])

Note down the value of the LPORT parameter (9,257). This value could be any value of your choice between 1024 and 65,536.

Save the resulting file as “Trojan” on your desktop.

# 1.3. Activate the vulnerability.

Copy the file “Trojan.exe” onto PC1 and run it.

NOTE.– In practice, the file already created will either be integrated into another program that appears legitimate (a game, a screensaver etc.) or will be linked to an office file (pdf, Word etc.) or even an image and will then be triggered when executed by the user.

# 2. Launch the attack.

From the directory of attacks, choose the following path: “exploit/multi/handler” and double-click.