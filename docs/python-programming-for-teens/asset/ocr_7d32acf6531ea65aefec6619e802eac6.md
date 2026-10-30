code and the computer hardware that carries out these instructions. It’s a gap that most programmers (and most other users of computers) never have to worry about; they all just take for granted that the programs they build or use will accomplish their tasks on any computer.

In this section, you learn a bit about what goes on underneath the hood to allow a physical device like a computer to carry out the instructions you write in Python code.

# Computer Hardware

The basic hardware components of a computer are *memory*, a *central processing unit* (CPU), and a set of *input/output devices*, as shown schematically in Figure 4.3.

![](bbox=[0.07, 0.36, 0.52, 0.49])

Figure 4.3
Hardware components of a modern computer system.

Human beings primarily interact with input and output devices. The input devices include a touchscreen, a keyboard, a mouse, a camera, and a microphone. Common output devices include a monitor, a printer, and speakers. Computers can also communicate with the external world through various ports that connect them to networks and to other devices such as handheld music players, digital cameras, and drone robots. The purpose of most of the input devices is to convert information that human beings deal with, such as text, images, and sounds, into information for computational processing. The purpose of most output devices is to convert the results of this processing back to human-usable form.

Computer memory is set up to represent and store information in electronic form. Specifically, information is stored as patterns of binary digits (1s and 0s), also called *bits*. To understand how this works, consider a basic device such as a non-dimming light switch, which can only be in one of two states: on or off. Now suppose there is a bank of switches that controls 16 small lights in a row. By turning the switches off or on, you can represent any pattern of 16 binary digits as patterns of lights that are on or off. Computer scientists have discovered how to represent any information, including text, images, and sound, in binary form.