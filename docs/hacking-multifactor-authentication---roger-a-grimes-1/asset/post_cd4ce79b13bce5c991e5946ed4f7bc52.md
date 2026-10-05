
# Hacking Multifactor Authentication

- 1. The user is given an approved token (notice it's no longer a request token).
- 2. The user gives the approved access token to the first website.
- 3. The first site gives the access token to the second site as proof of authentication on behalf of the user.
- 4. The second site lists the first one their site on behalf of the user.
- 5. The user sees a successfully completed transaction occurring.

There have been a lot of federated authentication schemes, like Microsoft Passport, that have tried to take over the online world. All OAuth have failed after a few years; OAuth seems to be the one that finally made it. For more information on OAuth, visit oauth.net.

> Josh Fruhlinger and I wrote an article for CSOOnline, and of this chapter's information on OAuth comes from September 2019 article: www.csonline.com/article/3216404/what-is-oauth-how-the-open-authorization-framework-html.

The biggest advantage is that OAuth gives the user an SSO-like experience across multiple, distinct sites and services. The biggest risk is, as is with SSO, that a single promise could lead to easier or even immense compromise of the other participating sites and services.

# APIs

Application programming interfaces (API) are created by developers of their underlying technologies to allow other developers and users to programmatically interface with their product. APIs allow other people to quickly interact with a product and to extend its functionality. APIs are a staple of the computer world, especially you want your product to be widely adopted and used.

APIs can be abused by bad people. APIs allow malicious hackers to do bad things utilizing the technology faster and more destructively across a wide group of people. APIs have been used to rob people of hundreds of thousands of dollars in seconds and to compromise millions of accounts of very popular websites and services. These types of attacks will be covered in more detail in Chapter 19, "API Abuses."

# Contextual/Adaptive

As you'll recall from Chapter 2, "Authentication Basics," authentication services are increasingly considering many other additional types of authentication factors known as contextual or adaptive. These factors include the device the user is to authenticate, the location of the current authentication as compared to past authentication events, how long it took the user to type a password, actions the user is actively taking, sequence of actions, and numerous other factors. Some authentication services can use over a hundred different types of contextual factors to determine whether someone is unauthenticated.

The reason I'm including here again is because not only are these types of factors used themselves to determine authentication, but they are increasingly likely to be an important part of future authentication solutions. They already are for many authentication scenarios.

A great example is how your bank or credit card vendor determines to approve or deny any particular transaction you are performing in real time. Both of these look at your current transaction to see if it fits into a pattern that is usual and custom for you.

For example, if you always use taxis, why are you suddenly using Uber? If you never travel, live in Florida, it should be strange that your credit card is being used to buy airline tickets from Texas to Missouri? If you normally watch every television on an iPad, it would be strange for you to suddenly buy an 80-inch TV? It is possible for you to buy something in Boston, Massachusetts at 10 a.m. and then something in Spokane, Washington at 11 a.m.

Banks and credit card companies are comparing your current transaction to your past behavior all the time. And, after decades of experience, they are pretty good at it. Most of the time we are prevented from buying what we want to, and most of the bank or credit card company proactively catches and stops the fraud (faster than most of the legitimate card holders). Contextual and behavioral authentication are becoming an increasingly popular way authentication decisions are made, even if we're often aware of it. The only disadvantage is that these comparisons aren't perfect. They stop legitimate transactions and sometimes fraud is allowed. But there is an entire cottage dedicated to improving accuracy. We will talk more about this in Chapter 24, “The Future of Authentication.”

# Less Popular Methods

The authentication methods discussed in this scenario are far less popular today but are still used in specialized scenarios.

# Voiceover Radio

Good authentication is key in any communication's scenario where the two parties do not know each other. One of the earliest forms of communication was the radio (invented in 1885 by Italian Guglielmo Marconi). And nearly as quickly as radio was used to communicate confidential information, it was being used by malicious people to eavesdrop and block. Analog radio signals have been replaced by digital signals in most places, but radio communications still exist in many specialized scenarios. For example, radio communications are used in military operations, on the ground, at sea, and in the air, to communicate between participants.

During military operations, many participants will communicate with each other using radio (or other types of wireless waves). They communicate to coordinate actions, update each other on accomplishments, discuss new plans, call in airstrikes, and so forth. Today, the radio equipment they use has authentication and encryption built-in so that everything communicated is protected. But back in the days of World War II, the Korean War, and the Vietnam War, did not. During those times, the enemy would intentionally seek out the communications specialist, kill or kidnap them, and then use their radio to listen to current accents, such as a Texas drawl, to mimic the accent they captured. To fight this before the days of cryptographic radios, the soldiers would each call names to identify themselves, as well as codes (i.e., knowledge-based authentication) to confirm their participation. These verbal codes helped keep communication lines free of adversarial instructions.

# Paper-Based

Before the days of computers and pervasive digital cryptography, most cryptography was done by hand. The encryption and decryption codes were written down and copied between participating subjects. This method persisted for over a thousand years. History is replete with failed murderous acts and royal assassinations because the written-secret code and related messages were discovered and deciphered. Starting around World War II, paper-based codes and cryptography diminished machines, and later on, computers were the preferred way to do cryptography.

Still, paper-based cryptography persists. Paper-based codes. There are even digital authentication and encryption solutions that rely on printed, paper times alternative backup option for the digital option in case the digital option gets lost or damaged. For example, many password managers generate printed codes that users may need in order to recover their implementation of the password manager program if it gets lost or corrupted. Those printed codes risk losing all stored passwords at once. It can be a real pain. It's also a pain because you have to securely store that piece of paper containing the code. The theory is that you should store it in fireproof safe, a bank deposit box, or something like that, and it should be stored in two separate physical locations that cannot be compromised by a single disaster event (fire, flood, hurricane, tornado, earthquake, etc.). Many people keep a single copy in their house in a paper file or desk drawer.
