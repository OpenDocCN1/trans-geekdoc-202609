iv. AH Information: It specifies the Authentication Algorithms, associated keys, key life-times, and other related parameters for AH. The hashing algorithms that are supported for HMAC are MD5 and SHA-1.

v. ESP Information: It specifies the Encryption and Authentication Algorithms, associated keys, key life-times, Initialization Values, and other related parameters for ESP. The Symmetric Encryption Algorithms supported by IPSec:

+   - Three-key 3-DES
- IDEA
- Three-key IDEA
- RC5
- Blowfish

vi. SA Lifetime: It specifies the SA Lifetime in terms of period or in terms of byte-count. It also specifies that, after the life-time, whether the SA is to be replaced by a new SA or to be terminated.

vii. IPSec Protocol Mode: It specifies whether the SA supports Transport Mode, Tunnel Mode, or Wildcard Mode.

viii. Path Max Transmission Unit (MTU): It specifies the maximum size of packet that can be transmitted without fragmentation.

# 12.5 SECURITY POLICIES

Security Policies are a set of rules programmed into an IPSec implementation that dictates the way received packets are to processed.

# 12.5.1 Security Policy Database (SPD)

Each IPSec implementation will have a Security Policy Database (SPD). Each entry in SPD defines a subset of IP traffic and points to a SA under which the subset of IP traffic is to be processed.