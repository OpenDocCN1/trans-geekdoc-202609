# Internet of Things with Raspberry Pi and Arduino

If “404 error” occurs, then do an update by using the command `sudo apt-get update.`

+   6. Run to install the i2c-tools again.

NOTE: The installation can take a few minutes, depending on how busy the server is.

+   7. Now add a new user to the i2c group: `sudoadduser pi i2c`

+   8. Reboot the PC with the help of the command: `sudo shutdown -r now`

+   9. After the reboot, test to see the connection of any device by: `sudo i2cdetect -y 0`

+   For Rev 2 board command: `sudo i2cdetect -y 1`

A window will appear (Figure 5.22).

+   10. Now install the python-smbuspython module with the help of the command: `sudo apt-get install python-smbus`

+   11. Now Raspberry Pi is ready to use the i2c with Python.

![](bbox=[0.118, 0.636, 0.872, 0.887])

FIGURE 5.22
Window after reboot test command.