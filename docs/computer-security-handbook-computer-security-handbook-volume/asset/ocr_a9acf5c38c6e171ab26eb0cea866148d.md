![](bbox=[0.1, 0.1, 0.92, 0.6])

# Exhibit 33.4 802.1X Authentication to Authentication Server

For an IBSS, the client wanting to associate to another client is the supplicant, and the target client is the authenticator. This means that clients in an IBSS can simultaneously be supplicants and authenticators depending on who initiated the association. Additionally, each IBSS client will need an authentication server unless the network uses PSKs.

As covered in stage 1, a secure channel has to be established between the authenticator and authentication server prior to this exchange; this serves two purposes. The first is to protect the integrity and authenticity of the authentication exchange, the second is to allow the AS to securely send the PMK to the authenticator once authentication is complete.

# Stage 4—Mutual Authentication and Establish Pairwise Working Keys

Stage 3 established a PMK in both the supplicant and authenticator. If the network uses a pre-shared key (PSK) then the PSK is the PMK. This stage is called the 4-way handshake and has the following purposes:

+   1. To mutually authenticate the supplicant and authenticator to one another by confirming they both have the same valid PMK.
+   2. To generate a Pairwise Transient Key (PTK) from the PMK and fresh temporal keys bound to their MAC addresses.
+   3. To synchronize the installation of the keys in both devices.