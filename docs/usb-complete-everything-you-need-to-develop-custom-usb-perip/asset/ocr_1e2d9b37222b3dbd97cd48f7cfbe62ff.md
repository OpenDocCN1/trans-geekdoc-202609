# Introduction

niques can go a long way in avoiding snags and simplifying what needs to be done.

If you’re involved with designing USB devices, writing the firmware that resides inside USB devices, or writing applications that communicate with USB devices, this book will help you along the way.

# What’s Inside

These are some of questions the book answers:

+   - *How do USB devices communicate?* The USB interface can seem daunting at first. The USB 2.0 specification is over 600 pages, not counting the class specifications and other supplementary documents. This book doesn’t attempt to restate everything in the specifications. Instead, the focus is on what you’ll need to know to enable your devices to communicate efficiently and reliably.
+   - *How can I decide if my device should use a USB interface?* USB isn’t the best choice for every application. Find out whether your design should use USB or another interface. The chances are good that you will choose USB, however, and if so, you’ll learn how to decide which of USB’s three speeds and four transfer types are appropriate for your application.
+   - *What controller chip should my device use?* Every USB device must contain an intelligent controller to implement the USB interface. Dozens of manufacturers offer controller chips with differing architectures and abilities. This book includes descriptions of popular chips and tips to help you select a controller based on your project’s needs and your background and preferences.
+   - *How do applications communicate with USB devices?* PC applications access a USB device by communicating with the device driver the operating system has assigned to the device. Some devices can use class drivers that are included with Windows. Others devices require custom drivers. This book will introduce you to the classes and will help you determine if a defined class is appropriate for your device. If your device requires a custom driver, you’ll learn what’s involved in writing a driver, what tools