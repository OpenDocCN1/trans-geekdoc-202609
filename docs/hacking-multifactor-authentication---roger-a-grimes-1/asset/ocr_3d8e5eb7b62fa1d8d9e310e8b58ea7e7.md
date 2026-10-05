# Prevent OTP Replay

Some OTP solutions allow previously generated or used OTP codes to continue to be valid into the future. This is crazy! All OTP codes surpassed by newer OTP codes should no longer be valid. Some OTP solutions include timestamps that are recorded and stored with the OTP code when it is generated and used. This can help prevent easy replay. An OTP system should not allow multiple OTP codes to be generated, or remain valid at once. This prevents an attacker from obtaining older OTP codes and re-using them as easily.

> NOTE This recommendation causes an issue for MFA solutions with master codes, which are often generated in the same time and never expire, are given long expiration periods, or don expire until the user generates new ones or cancels the old ones.

# Make Your RNG NIST-Certified or Quantum

OTP security protection relies on the true randomness of the static value and the involved hash. Mess up that and the rest does not matter. Most traditional operating systems contain freely trusted random number generators (RNGs) and you can rely on them. Don’t “roll your own.” Today's best RNGs are known as pseudo-RNGs (PRNGs) and inspire a bit of confidence because we are acknowledging that they aren’t perfect. Funny, but by acknowledging that they aren’t perfect as they seem from themselves. I avoid RNGs that don’t understand that they aren’t perfect as they pretend. Quantum random number generators are truly and random. All other factors consider equal, I would trust any quantum random number generator (QRNG) over an RNG/PRNG.

NIST created a series of tests that any—quantum or otherwise—RNG vendor or customer can run to see how bad their RNG/PRNG is compared to a theoretically perfect number generator. NIST documented the tests and requirements in NIST Special Publication 800-22 (nvpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication-800-22la.pdf).

# Increase Security by Requiring Additional Entry Upon OTP Code

One thing RSA got right early on was requiring logins involving TOTP devices also use an static code that the user provided during the time of login. When the adding static code could be compromised as easily as a seed or typed value, it does make that sort of attack slightly harder to accomplish. Additionally, if the seed database gets compromised and the other static values are not located in the same place, the seed value alone will not give the hackers immediate access.

# Stop Brute-Forcing Attacks

When OTP codes are typed, in the authentication system should have an “account lockout” feature that prevents attackers from guessing over and over again unsuccessfully until they guess successfully.