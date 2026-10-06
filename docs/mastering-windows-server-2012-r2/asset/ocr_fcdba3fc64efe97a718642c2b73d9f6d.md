# PRINT SERVICES OVERVIEW 829

the entire print job was completed. During this time, the user wasn't able to do anything with the computer.

# WORKING WITHOUT A PRINT SERVER

We have spent a lot of time working in organizations that do not use print servers. Instead, print devices are placed directly on the network with an IP address, and each computer needs to be configured to use the print device.

One of the significant drawbacks to this method is that users often have problems connecting to the print device and installing the correct driver. They'd have to learn the printer's IP address to connect, and even then, the wrong driver can be selected, resulting in useless prints. The help-desk professional knows exactly what driver is needed, she often has to go to a driver hunt

When a print server is used, users just need to use the universal naming convention (UNC) path of the printer (\\server\share) when adding it. The server will then automatically download the correct driver. As an example, a printer could be Laser1 on a server named BF1, and users would only need to connect to \BF1 to automatically download the correct driver for their operating system. Additionally, if the print device is moved to a different subnet, only the server needs to be reconfigured, not every client.

The trade-off is the cost of the print server and associated maintenance. However, since servers can easily share roles, file servers act as print servers too.

You can be irritated by many users, the print spooler accepts the job and stores it in memory or on the hard drive until the print device can accept it. If you print a document, you can almost immediately begin working on something else, even if it takes 10 minutes for your document to print.

When users post documents to a print server, two spoolers are actually involved. The spooler on the user's computer spools the document (usually to memory) and then sends the job to the print server. When the print server receives the job, it also spools. The print server may be working on other jobs, it will spool print jobs to the hard drive.

The default folder for spooled documents is C:\\windows\System32\Spool\Printers. You'll see how this change later in this chapter.

# The Printer Driver

Print drivers are the software that enables the operating system to communicate with a printer and ultimately send the print job to the print device. Print drivers have been unified in recent years, making them easier to work with. You'll come across three print drivers:

+   * Itanium Type 3 – User Mode
* x64 Type 3 – User Mode
* x86 Type 3 – User Mode