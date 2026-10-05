
[content]
# Chapter 16 Attacks Against Biometrics 351

Why doesn't Microsoft enable anti-spoofing by default? The answer is proved foolish. One, they don't know for sure that your hardware supports it, although they likely require vendors to include a way to verify it using an API if they really wanted. Second, and more importantly, enabling anti-spoofing causes high false rejection rates and slower acceptance. That's the double-edged sword with all biometrics. As you decrease acceptance rates, you unavoidably cause higher rejection rates and slower processing. I've yet to see a metric vendor that did not struggle with this issue. Companies using Windows with facial recognition should probably enable anti-spoofing. Of those at use are probably fine without it.

## Faking Out Apple's Face ID

In 2017, a Vietnamese company printed out and 2D face images on 3D masks and fooled Apple's Face ID on iPhone X: security.sophoms.com/2017/11/16/apples-face-id-security-fooled-by-simple-face-mask/. There is a long, 52-minute video of the spoofing if you want to watch: www.youtube.com/watch?v=88FL10qt8I-youtube.be. Start at the 8:30 minute if you just want to see it. Other hackers did this using pictures of eyes taped over eyeglasses here: www.forbes.com/sites/daveynicker/2019/08/10/apple-faceid-acked-in-than-120-seconds.

Here's a video of 3D-printed head of different cell phones, but not Apple's iPhone: www.youtube.com/watch?v=zCNGkKFds.

## Twins Spoof Face ID

If you want to see a set of identical twins Face ID, (NSFW because of crude language): www.youtube.com/watch?v=GFtOUpyqx4. They aren't the most perfect-looking set of identical twins I can imagine. They have different attributes on their faces and look to me, 100 percent clones clones of each other. So, why did it work? Apple allowed the false-acceptance rate of Face ID to be higher than Windows Hello so more legitimate users were able to quickly log on Face ID if they set it.

Conversely, I saw Microsoft's Windows Hello not faked by out of nearly perfect set of identical twins. Here's a video of a test against Windows Hello: www.youtube.com/watch?v=JINL246P9g. Windows Hello failed.

## Spoofing 2D Smartphones

In 2019, Dutch researchers tested 110 different smartphones by holding up a simple 2D face picture. It worked on 42 of the phones, but not the Apple Touch: zdnet.com/article/facial-recognition-does-work-as-intended-on-42-of-110-tested-smartphones.

Tech editor Nachiner tried to spoof Android's 2D Trusted Face biometrics: www.youtube.com/watch?v=_L_UFY38bg74. He placed his low-resolution picture on a high-quality laptop screen, and it was good enough to fool the Android facial recognition check. According to this article

## Hacking Multifactor Authentication

(www.androidpolice.com/2019/09/04/trusted-smart-unlock-method-has-been-removed-android-devices) and intends to build a more reliable facial recognition feature closer to Apple's Face ID.

To summarize all these different types of biometric attacks: there are lot of them and they are hard to stop. Biometric vendors are improving their ability to prevent spoofing attacks, but it is a constant war between the good and the bad trying to get around their biometric solutions. So far, no one has ever invented a biometric device that could be fooled, and probably will never be such a device.

## Defenses Against Biometric Attacks

This section explores developer and user defenses to mitigate attacks against biometrics.

## Developer Defenses Against Biometric Attacks

First, we'll look at some developer defenses against biometric attacks.

### Education

Developers must be educated to understand all the threats to each type of biometric solution they are developing and how to mitigate those threats. Developers must threat-model their solution and use security development lifecycle (SDL) programming techniques to lower potential vulnerabilities and errors.

### Strive for Lower Error Rates

It goes without saying that developers should strive for lower error rates. Microsoft Windows Hello proved that lower error rates could be required and implemented without upsetting the customer too much. Apple's Face ID used to be very hackable, and now it is less so. The conventional wisdom that high error rates must be acceptable on use devices to make customers happy is being denied every day. All developers should strive for lower error rates whenever possible.

### Implement Anti-Spoofing Measures

Implement the strongest anti-spoofing, liveness-detection technology you can. What means depends on the biometric technology used, but in general means recognizing and discounting the very simple presentation attack methods and ensuring that the sample comes from a live person.

Biometric has a great article on liveness detection regarding fingerprint scans here (www.biometric.com/spoofing-fingerprint-scanner-and-spoof-detection/) and here (www.biometric.com/liveness-detection-anti-spoofing-challenges). They are using a variety of methods to prevent spoofed fingerprints. One way is to use a light embedded in the fingerprint sensor to sense various common, inorganic spoofing materials are being used. Another is how to take the submitted fingerprint and compare them to

[PAGE 371]

# Chapter 16 Attacks Against Biometrics 353

"ridge distortion" there is. Supposedly real fingers have more distortion. They look for perspiration. Apparently spoofed fingerprints showed more uniformity than non-spoofed fingerprints. They do other things, such as looking for artificial artifacts (such as air bubbles in glue) and confirming the presence of a pulse. A lot of research is going on liviveness-detection techniques, and these are getting better all the time. But no matter what liviveness-detection, they can always be hacked around.

## Limit Number of Attempts

Most of the hackers in the attack demo talk about how many times the biometric device failed or successful. Limiting the number of failed attempts before a successful authentication is a good way to reduce spoofing. Treat biometric attacks like a password and enable account lockout. On a related note, extend wait times between failed attempts so that each failed attempt begins to exert more of a cost on the hacker. Don't just let them over really fast until they are eventually successful.

## Require MFA with Biometrics

Biometric authentication should always be paired with a second, non-biometric factor. The whole reason most going to MFA is because it requires two or more factors and makes it harder for a hacker to be successful against a potential victim. Biometrics should not change that. 1FA solutions are usually weak combinations. Biometrics don't change that and, in some cases, are weaker than simple passwords.

## Securely Protect Biometric Trust Databases

All developers need to ensure that their biometric trait databases, wherever they are, are strongly secure. They need to be secured with least privilege permissions and encrypted. For example, Windows Hello uses symmetric and asymmetric ciphers and protects the most critical keys with an additional private key stored on a Trusted Platform Module (TPM) chip on the motherboard and OS protected by Unified Extensible Firmware Secure Boot. It's a pretty great combination.

Fairly secure storage can be done without encryption and symmetric chips ensure the stored biometric patterns are obscured enough to be unrecognizable outside the system from which it was stolen. I've heard of biometric systems where the data—fingerprints, prints patterns, or hand vein—is converted into a digital matrix that is unusable and unrecognizable outside of the system. As earlier, most pattern-recognition systems convert the images they see to inflection points, or like star constellations, and it is those "star constellations" that are stored and not the actual images. Going one step further, star constellations can be mapped to a matrix grid, which is converted to numbers or coordinates. As a simple example,
