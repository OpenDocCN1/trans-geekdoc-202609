# Hacking Multifactor Authentication

B-Unit 2, and B-Unit 3. Figure 21.3 shows the front of one version of the device with functionality callouts. You can read more about the B-Unit here: www.bloomberg.com/professional/support/b-unit.

![](bbox=[0.91, 0.163, 0.483, 0.365])

Figure 21.3: Example of a Bloomberg MFA device

As Figure 21.3 shows, the B-Unit has a fingerprint reader, an OLED screen (for displaying information and statuses), and a power button. The back of the card, not shown in Figure 21.3, has an eight-digit serial number and a photodiode light sensor. The bottom of the card has a micro-USB port for charging the internal lithium battery and updating. You can see see this is no ordinary MFA device. Using a B-Unit device with Bloomberg software requires each user to register their device to link to the user and each other and to their Bloomberg software instance. Therefore, the user follows a similar but different set of steps to log on.

# New User B-Unit Registration and Use

New Bloomberg Terminal users get a B-Unit device, start the B-Unit Terminal software, and log on to the software instance with their username and password to begin the registration process. The software will prompt them to enter their eight-digit B-Unit serial number (tying their identity to a particular B-Unit device and software instance). Then, they power on their B-Unit device.

If the B-Unit has been used before and contains information from a previous instance, the user is instructed to reset the unit the first time they use it to wipe away any remaining information and make sure they are starting with a blank slate.

The Bloomberg Terminal software will start to emit a series of light flashes from the center of the screen (similar to what an optical Morse code might look like). The user holds up their B-Unit within inches of the screen, and the light sensor reads the code from the Bloomberg Terminal screen that is flashing the light codes. This further syncs the user's B-Unit with their instance of the Bloomberg software. The user's B-Unit will then collect their fingerprint using the fingerprint scanner