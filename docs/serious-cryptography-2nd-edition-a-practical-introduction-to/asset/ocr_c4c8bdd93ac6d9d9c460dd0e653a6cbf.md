maximum number of malicious participants that can be compromised without compromising the security of the protocol:

**Honest majority**  Here, the attacker is limited to corrupting less than half of the key-sharing parties. Therefore, the threshold *t* must satisfy *t* < *n*/2. By definition, a threshold signing protocol with parameters (*t*, *n*) must be safe even with compromised *t* participants. Protocols designed under the honest majority assumption are typically more efficient, but they can’t accommodate arbitrary values of *t*. For instance, a protocol with parameters (4, 5) is infeasible in this model, as it requires tolerating up to four corrupted parties.

**Dishonest majority**  This model allows the protocol to support any value of *t* from 1 to *n* − 1. It enables the creation of protocols where all but one of the *n* parties could be corrupted, yet the malicious parties would still be incapable of forging signatures or recovering the private key. This model offers more flexibility in terms of the threshold value but often requires more complex and robust security mechanisms.

We also characterize an attacker by what they can do once they corrupt a party and learn their secret values (including the key share). There are two attacker models defining this:

**Passive, or honest-but-curious**  They learn information from corrupted parties but can’t force them to deviate from the protocol. This models “read-only” compromises, where an attacker gets a snapshot of a system’s memory, both storage and volatile memory (RAM, processor registers).

**Active, or malicious**  Parties may arbitrarily deviate from the prescribed protocol. This models systems fully compromised by an attacker or controlled by a malicious insider (such as an operator, administrator, or cloud provider).

A protocol secure against active attackers is therefore always secure against passive attackers, but not the other way around.

There are two ways for an attacker to choose which parties to corrupt, which are defined by the following models of corruption type:

**Static corruption**  The attacker must choose which participants to corrupt before starting the protocol.

**Adaptive corruption**  The attacker may wait until after the protocol begins to choose which participants to corrupt—and then learn the history of their operations throughout the protocol.

A protocol secure against static corruption is always secure against adaptive corruption, but not the other way around. However, there are techniques to convert a protocol from secure against static corruption to secure against adaptive corruption.