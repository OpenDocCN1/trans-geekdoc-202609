# SMS Attacks

Chapter 8 covers Short Message Service (SMS) attacks. Today's incredibly functional smart-phones are where a lot of the world conducts most or all of their computing. Many people have only a cell phone to connect remotely to another person, be a phone call, messaging, or email. For many people, especially younger people, most of their Internet browsing is conducted from a cell phone. So, it makes sense that criminals will go where their potential victims are.

The small form factor and inability to easily distinguish between real and fraudulent SMS messages has led to an entire new genre of crime. In many cases, the insecurity of SMS MFA solutions rely on it even less safe than simple logins and passwords.

This chapter describes what SMS is and why it is abused, presents examples of real-world attacks, and finishes with how SMS MFA developers and users should defend themselves.

# Introduction to SMS

SMS is a popular text-based messaging service standard that nearly all cell phones support. Already in widespread use by the 1990s, it is rare that a cell phone does not support SMS. It was the original chat-based "killer app" that took over the world. Today, many people use other chat apps like WhatsApp, Skype, Facebook Messenger, Google Hangouts, and Instagram, but almost everyone uses SMS because everyone else has and it's always active and loaded.

> NOTE There is a competing service Multimedia Messaging Service (SMS), but it's not as popular or is used as part of SMS to deliver multimedia content. Either way, it's not covered in this book. If you want to learn more about SMS, visit en.wikipedia.org/wiki/Multimedia_Messaging_Service.

SMS originally allowed a maximum of 140 to 160 characters to be sent in a single message to one or more recipients using their cell phone number. Today, depending on the mobile network vendor and applications, SMS-based apps can send longer messages and more than simple text-based characters (such as emoticons, pictures, and videos). Figure 8.1 shows an example of an SMS message including messages, pictures, and emoticons from my wife one day.