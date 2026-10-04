language that convey the message. Her friend listens to the description and decodes the sounds to understand the message he received.

Message encoding also occurs in computer communication. Encoding between hosts must be in an appropriate format for the medium. Messages sent across the network are first converted into bits by the sending host. Each bit is encoded into a pattern of voltages on copper wires, infrared light in optical fibers, or microwaves for wireless systems. The destination host receives and decodes the signals to interpret the message.

# Message Formatting and Encapsulation (3.1.7)

When a message is sent from source to destination, it must use a specific format or structure. Message formats depend on the type of message and the channel used to deliver the message.

A common example of requiring the correct format in human communications is when sending a letter. As shown in Figure 3-3, an envelope has the addresses of the sender and receiver, each located at the proper place on the envelope. If the destination address and formatting are not correct, the letter is not delivered.

![](bbox=[0.3, 0.52, 0.82, 0.66])

| Recipient (destination) Location address | Sender (source) Location address | Salutation (start of message indicator) | Recipient (destination) identifier | Content of Letter (encapsulated data) | Sender (source) identifier | End of Frame (End of message indicator) |
|---|---|---|---|---|---|---|
| Envelope Addressing | Encapsulated Letter |  |  |  |  |  |
| 1400 Main Street Canton, Ohio 44203 | 4085 SE Pine Street Ocala, Florida 34471 | Dear | Jane | I just returned from my trip. I thought you might like to see my pictures. | John |  |

Figure 3-3 Format for Sending a Letter