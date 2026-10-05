# Hacking Multifactor Authentication

![](bbox=[0.95, 0.103, 0.393, 0.646])

**Figure 8.1:** An SMS message including messages, pictures, and emoticons

Every SMS message includes all of the following information, even if much of it is not displayed directly to the user:

+   - Originating address (originating mobile number or generated code)
- Header – Message Type, Service Center Time Stamp, Protocol Identifier, Data Coding Scheme, Length Of User Data
- User Data (the message)

The originating address is usually the sender's phone number, but it can be a variety of codes, usually all numeric. It can be a simulated phone number or any code that part of the network involved in sending and directing the SMS message wants to inject. It doesn't have to be a valid phone number or even originate from the phone number it says it is from. Phone numbers can