# Chapter 5 Hacking MFA in General 129

# API

Many MFA solutions come with a private or open (i.e., shared) application programming interface (API). These APIs can contain vulnerabilities or be maliciously used by an attacker. Chapter 19, "API Abuses," will cover this category in more detail.

# Authentication Factors

The authentication factors themselves can be compromised. For example, by biometric attribute (fingerprint, retina print, etc.) can be captured and reused maliciously. Malware can steal passwords and PINs, or users can be tricked into giving them out. Authentication secrets can be stolen over authentication devices.

It is also possible for an invalid claim/assertion to be maliciously manipulated. For example, a user's authentication solution may have verified them as not belonging to an elevated security group but the attribute is modified to appear as if the user does belong to an elevated security group. Many hacks are against the authentication factor or claim.

> NOTE Another increasing concern is the privacy rights of a claimant. Every authentication system should strive to allow the subject to decide which claims are revealed in specific authentication events. Many attacks seek to gain access to more claims than the relying party is supposed to be privy.

# Authentication Secrets Store

Many times, the hack is made against the database/store where authentication secrets are stored. Unauthorized access to authentication secrets are among the most devastating attacks possible, because an attacker can get access to every secret the store has and reuse them.

For example, as covered previously, Windows network authentication secrets are stored on Active Directory controller databases with the file NTDS.DIT. There are many hacker tools, such as Mimikatz (github.com/gentilki/mimikatz), that attempt to "dump" all the authentication secrets stored, if they have elevated clearance. The NT hashes of user and computer passwords are stored in NTDS.DIT. As covered in Chapter 1,Logon Processes," those hashes can be replayed to create new network, drive, and device connections. They can also be "cracked" back to their plaintext password equivalents and used anywhere that accepts the plaintext password alone (email, logon portal, etc.). An attacker gaining access to an authentication secrets is a "game over" attack. When an attack obtains access to the ultimate authentication secret, there is