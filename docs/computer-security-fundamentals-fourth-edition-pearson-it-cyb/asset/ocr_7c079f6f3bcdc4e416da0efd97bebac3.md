has a very large number of possible combinations. This means there is a limit how how large a rainbow table can be, and this is why longer passwords are more secure than shorter passwords.

Since the development of rainbow tables, there have been methods designed to thwart such attacks. The most common is salting, in which random bits are added to further secure encryption or hashing. This is most often encountered with hashing to prevent rainbow table attacks.

Essentially, the salt is intermixed with the message that is to be hashed. Consider an example. Say that you have a password that is:

In binary that is:

01110000 01100001 01110011 01110011 00110000 00110000 00110001

A salt algorithm would insert bits periodically. Let's assume for our example that we insert bits every fourth bit, giving us:

01111100001 0110100011 0111100111 0111100111 0011100001 0011100001 00111000011

If you convert that to text, you would get:

xZ7

All this is transparent to the end user, who doesn't even know that salting is happening or what it is. However, an attacker using a rainbow table to get passwords would get the wrong password.



Steganography is the art and science of writing hidden messages in such a way that no one, apart from the sender and intended recipient, suspects the existence of the message. It is a form of security through obscurity. Often the message is hidden in some other file, such as a digital picture or an audio file, to defy detection.

The advantage of steganography over cryptography alone is that messages do not attract attention to themselves. If someone is aware that a message is even there, she won't try to decipher it. In many cases, messages are encrypted and hidden via steganography.

The most common implementation of steganography utilizes the least significant bits in a file in order to store data. By altering the least significant bit, you can hide additional data without altering the original file in any noticeable way.

There are some basic steganography terms you should know:

+   Payload is the data to be covertly communicated. In other words, it is the message you wish to hide.

+   The carrier is the signal, stream, or data file into which the payload is hidden.

+   The channel is the medium used. This may be still photos, video, or sound files.

The most common way steganography is accomplished today is via least significant bits. Every file has a certain number of bits per unit of the file. For example, an image file in Windows is 24 bits per pixel. If you change the least significant of those bits, then the change is not noticeable with the naked eye. And you can hide information in the least significant bits of an image file. With least significant bit (lsb) replacement, certain bits in the carrier file are replaced.



In modern times, steganography involves digital manipulation of files to hide messages. However, the concept of hiding messages is not new. There have been many methods used throughout history.