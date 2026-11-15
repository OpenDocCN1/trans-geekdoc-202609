+   - Portability of scene definitions and interoperability between virtual worlds operating to different formats and standards is enhanced (Soto & Allongue, 1997);
+   - The world can actually be defined by its creator more rapidly using semantic terms (e.g. Kleinermann et al., 2005); and
+   - Any relationships between objects can be extracted into the semantic graph containing the objects and do not need to be explicitly coded into every virtual world.

# Game Servers

Most of technologies described in this chapter are used by single-user computer games and multi-user virtual worlds alike. What sets the latter apart is the technology to allow multiple users to be in the same virtual space at the same time, and ideally to interact with each other.

At the heart of most multi-user systems are game servers (also called reflection servers or multi-user servers) (Gallagher, 2022). Examples of game servers include Photon Engine (https://www.photonengine.com/), Nakama (https://heroiclabs.com/nakama/), and PlayFab (https://azure.microsoft.com/en-gb/products/playfab), or those built into the Unreal and Unity platforms.

When a user first logs into a shared space, they are sent the details of where everything (and everyone) is in that space (this may be as a full set of live data or a base set of data plus recent changes). For performance reasons, this may be limited to what is within a certain distance of the user. As avatars move and objects are moved, created, or deleted, the relevant user's software sends a message about the change to the game server, the server updates the state of the world, and then sends update messages to every user present in that space, and their own software then reflects the changes in their local copy. In addition to this centralised approach, it is also possible to take a peer-to-peer approach – where each user's device communicates directly with other users' devices, but the co-ordination and scaling can then be more challenging (Novotny et al., 2020).

The game server is highly optimized for passing very small messages (e.g. object A has moved to location X,Y,Z) to large numbers of people. However, it is not just the performance of the game server that is crucial to giving the user a smooth experience. There are also the network lags across the Internet as messages are sent from the user to the game server and then on to every user, and then to the ability of each user's own computer to manage the updates. Conventional approaches tend to result in a limit of significantly less than 100 people within any one space.

Trying to get large number of avatars in one virtual space is a challenge. Even the 4000 avatars demonstrated in experiments by Improbable