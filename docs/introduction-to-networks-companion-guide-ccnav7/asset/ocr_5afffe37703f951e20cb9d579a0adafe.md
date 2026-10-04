# Basic Device Configuration (2.4)

Before devices can be used in a network, they need to be configured. This section introduces the basic configuration of Cisco IOS devices.

# Device Names (2.4.1)

You have learned a great deal about Cisco IOS, navigating IOS, and the command structure. Now, you are ready to configure devices! The first configuration command on any device should be to give it a unique device name or hostname. By default, every device is assigned a factory default name. For example, a Cisco IOS switch is named “Switch.”

The problem is that if all switches in a network were left with their default names, it would be difficult to identify a specific device. For instance, how would you know that you were connected to the right device when accessing it remotely using SSH? The hostname provides confirmation that you are connected to the correct device.

The default name should be changed to something more descriptive. Choosing names wisely makes it easier to remember, document, and identify network devices. Here are some important naming guidelines for hosts:

+   - Start with a letter
- Include no spaces
- End with a letter or digit
- Use only letters, digits, and dashes
- Be fewer than 64 characters in length

An organization must choose a naming convention that makes it easy and intuitive to identify a specific device. The hostnames used in the device IOS preserve capitalization and lowercase characters. For example, Figure 2-8 shows that three switches, spanning three different floors, are interconnected together in a network. The naming convention that was used incorporates the location and the purpose of each device. Network documentation should explain how these names are chosen so additional devices can be named accordingly.