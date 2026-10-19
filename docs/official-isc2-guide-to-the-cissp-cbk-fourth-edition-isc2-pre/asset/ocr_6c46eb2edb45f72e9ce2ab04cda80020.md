# Frequency Division Multiple Access (FDMA)

Frequency division multiple access is used in analog cellular only. It subdivides a frequency band into sub-bands and assigns an analog conversation to each sub-band. FDMA was the original "cellular" phone technology and has been de-commissioned in many locations in favor of GSM or CDMA-based technologies.

# Time Division Multiple Access (TDMA)

Time division multiple access multiplexes several digital calls (voice or data) at each sub-band by devoting a small time slice in a round-robin to each call in the band. Two sub-bands are required for each call, one in each direction between sender and receiver.

# Wireless Security Issues

# Open System Authentication

Open System Authentication is the default authentication protocol for the 802.11 standard. It consists of a simple authentication request containing the station ID and an authentication response containing success or failure data. Upon successful authentication, both stations are considered mutually authenticated. It can be used with WEP (Wired Equivalent Privacy) protocol to provide better communication security; however it is important to note that the authentication management frames are still sent in cleartext during the authentication process. WEP is used only for encrypting data once the client is authenticated and associated. Any client can send its station ID in an attempt to associate with the Access Point (AP). In effect, no authentication is actually done.

# Shared Key Authentication

Shared Key Authentication is a standard challenge and response mechanism that makes use of WEP and a shared secret key to provide authentication. Upon encrypting the challenge text with WEP using the shared secret key, the authenticating client will return the encrypted challenge text to the access point for verification. Authentication succeeds if the access point decrypts the same challenge text.

# Ad-Hoc Mode

Ad-hoc mode is one of the networking topologies provided in the 802.11 standard. It consists of at least two wireless endpoints where there is no access point involved in their communication. Ad-hoc mode WLANs are normally less expensive to run because no APs are needed for their communication. However, this topology cannot scale for larger networks and lacks some security features like MAC filtering and access control.

# Infrastructure Mode

Infrastructure mode is another networking topology in the 802.11 standard. It consists of