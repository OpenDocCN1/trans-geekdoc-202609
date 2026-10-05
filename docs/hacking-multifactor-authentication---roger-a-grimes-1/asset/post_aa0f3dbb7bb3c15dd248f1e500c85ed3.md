
## 210 Hacking Multifactor Authentication

Because in the real world the hash outputs are often shorter than the messages they hash, absolutely means you cannot use the same hash for two different messages (i.e., a hash collision). You can't represent all possible set of larger messages with a smaller set of unique messages. You just can't. But unlike the never-repeating and truly random assignments we accepted as not being truly perfect, if the outputted hashes are usually unique (even if not guaranteed to be unique), it's acceptable for most uses.

NOTE Some of the material on hashing has been previously discussed in Chapter 3 but it is repeated for completeness. It also doesn't hurt to read it again.

There have been many different widely accepted, used hash standards over the years, including Digest 5 (MD5), Windows LANManager (LM), Windows NT (NT), and Secure Hash Algorithm-1 (SHA-1). All of these previous standards, for NT, are considered weak and broken.
The most popular hashing algorithm is Secure Hash Algorithm-2 (SHA-2 or SHA2), in 2015 NIST required that SHA-2's successor, Secure Hash Algorithm-3 (SHA-3 or SHA3), be used instead because SHA-2 has weaknesses that only get worse over time. So far, everyone is still using SHA-2. SHA-2 has many different output sizes, including 224, 384, 256, and 512 bits. Table 9.1, which is a repeat of Table 3, shows the result output for the word “frog” using popular hashes.

Table 9.1: Example hash outputs for the word “frog”

| Hash algorithm | Hash result for “frog” |
| --- | --- |
| MD5 | 93B8CC00C5F2B8C6B4287040CFCF51 |
| SHA-1 | B3E0F621A104AC6A85596CD2831B6D1134F56 |
| SHA-2 | 745FA32C00EFC4E947789DD5E989A61824286A59F170 640AC093B37D1AE14 |
| SHA-3 (512) | 66BE9F6734D812746291A3BBBF799D287FE771E816B0C5 611CE1A4F93B8DE3EE2734B571B21AC7436ABE12CD 629B003C6E38EF7053BE987D9D3B92ED52B62 |

An HMAC algorithm uses a strong hash and a truncation algorithm all with a key (seed) in a way to generate unique outputs for use case in the 1997 Internet Engineering Task Force (IETF) Request for Comment (RFC) 2104 (tools.ietf.org/rfc/2104). In 2008, RFC 2104 was published by NIST in Federal Information Processing Standards (IPS) Publication 198 (src.nist.gov/publications/detail/ips/198/final). Although back in 1997 the original developers were talking about MD5 and SHA-1 hashes, which were deprecated, it speaks to the resilience of the idea and the math didn't substantially change. HMACs and HMAC-based OTPs have proven to be a very good idea. See de-facto de-facto. See en.wikipedia.org/wiki/HMAC for more information on HMACs in general.

## Chapter 9 One-Pass Password Attacks

Most OTP vendors immediately understand the value of using a tried-and-true HMAC-based OTP algorithm and stopped trying to "roll their own" OTP algorithms. You can read more about HMAC-based OTP solutions based on the agreed-standard here: en.wikipedia.org/wiki/HMAC-based_one_time_password_algorithm. A popular specification and implementation of HMAC-based OTPs is the Initiative for Open Authentication (OATH) and is known as the OATH HOTP-standard. You can learn more about it here: openauthentication.org. Several vendors provide HOTP devices, including Yubico (www.com/wp-content/uploads/2016/02/YubicoBestPracticesOATH-HOTP.pdf), one of the leading OTP vendors in the world.

Most HMAC-based OTPs deliver 6 to 8 digit OTP codes, usually numeric only, for use authentication. There are still custom OTP algorithms, but most are fairly close to the standard one and (hopefully) include security improvements. In order for HMAC-based OTP solutions to be secure, the following components must be trusted, secure, and strong:

- Hash algorithm
- Seed value to be randomly generated.
- Seed value must remain a secret between the involved authenticating parties.
- Counter value should change and not.

Of these components, only the seed value needs to be secret. Everything else, including the counter and algorithm, could be known and the overall OTP result should remain secure. The overall protective power is in the ability to hash out a unpredictable and seemingly random string based on the inputs. If you have a good hash and a good algorithm used against something that involves a secret, you're good to go.

When you're using an OTP with a counter, the question is what would increment the counter and cause the solution to use a new counter value. There are several different possibilities.

### Event-Based OTP

One answer is what is known as an event-based OTP, which is really a subset of HOTP. The event can be odd and simply the passage of time. For example, every 10 minutes the OTP device updates its code. This requires both the OTP device and the authenticator to keep in sync (which is often more difficult than it sounds). Even identified time sources using identical materials can vary in time they report over.

The “event” can be a user pressing a button on the OTP device or setting a physical set of characters, such as an initialization code, to kick off the new OTP calculation. In those cases, the authentication system may start by communicating with the authenticator, and communicate some set of numbers, letters, colors, sounds, and so forth. The user has been instructed to look or listen for the codes and then input them into their OTP device. Another example could be that the user needs to biometrically authenticate to the OTP device first or hold the device up to a computer screen so that an optical code can be communicated to the OTP device (the latter example will be discussed in more detail in Chapter 21, “Test - Can You Spot the Vulnerabilities?”).

With any MFA solution, the device or software the subject is to authenticate must be synchronized with the authenticating resource. Both the subject and the authenticator must share, use, and store the same seed value to compute resulting OTP codes. They must also share the same method for generating current and future counter codes and algorithms. And they often get time-synchronized.

In practice, there is an authentication database (store) on both sides, and they share the seed value and also track a globally unique identifier value that ties the subject's authentication device/ or software to the right record within the authenticator. Usually the identification number is some sort of unique serial number or ID. It may globally unique or just for the vendor’s implementation. The database can be stored in a number of places, but must always be stored (or readily accessible) in a location where the authenticator can access it during authentication of the subject.

During authentication, the subject’s authentication solution and the authenticator’s service must be separately, and accurately calculate the resulting OTP for any instant (when all involved requirements are satisfied). They must be able to calculate the result separately, and then the authenticator compares what it calculated by itself to what the subject’s authentication solution submitted. If they match, the result is considered successfully authenticated.

There is a chance that someone learning all the involved components except for the secret value could, with enough time and processing power, compute the secret value, which, if learned, would make everything tumbling down. If even enough OTP outputs, there’s always a chance that an attacker can figure out what the static value is. The counter value helps offset the risk so that part of the computation is always changing, and an attacker will have a harder time determining which part of the changing output is due to the static seed point and which part is due to the changing value.

OTP designers help further counteract by routinely changing the counter value. That way, if an attacker was ever able to successfully compute a single OTP result code (never mind figuring out the seed value, which is much harder), by the time they did so, the resulting OTP code would be expired and no longer work. OTP designers expire the codes, and when they do, both sides must use the new counter value to generate a new OTP output code.

### TOTP

Time-based one-time password (TOTP) authentication solutions involve a current date and/or time value in the counter calculation. As the times change, so too does the counter value, usually at fixed
