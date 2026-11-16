The other type of scan is a brute force scan. Whereas an inquiry scan has the receiver listening for inquiry, a brute force scan actively sends messages to devices in order to determine what they are. To do this, it needs addresses to send messages to. This type of connection happens at layer 2, which means we are talking about MAC addresses. In the following listing, you can see the use of btscanner to perform a brute force scan. To run this scan, you need to tell btscanner the starting address and the ending address you want to scan, which you can see being asked for. You would need to provide this in the form of a MAC address. Keep in mind that each octet has 256 values, so the more octets of the address you want to run through, the longer your scan will take.

# btscanner starting a brute force scan

![](bbox=[0.15, 0.31, 0.75, 0.48])

This type of scanning will get you lists of devices. It won’t tell you the profiles that the devices support. Just having the list of devices nearby may be enough to run some of the attacks commonly used against Bluetooth devices.

# Bluejacking

Bluejacking is when an attacker sends data to a Bluetooth device without having to get through the pairing process, or perhaps the pairing happens without the receiver knowing about it. You could use a bluejacking attack to send an unsolicited message to a victim. This might be a picture or a text message. This could be a spoof attack, where you send a message that appears to be from someone else in order to get the recipient to do something. This attack uses the Object Exchange (OBEX) protocol to move the message or picture from one device to another.

Since this is just a one-way message, alone it isn’t harmful. The harm from this sort of attack comes from getting the device owner to do something you want them to do. This may not be beneficial for them, though.