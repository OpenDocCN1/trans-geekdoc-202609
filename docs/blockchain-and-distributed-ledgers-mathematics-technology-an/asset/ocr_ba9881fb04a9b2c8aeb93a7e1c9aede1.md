# Chapter 5 Bitcoin — A Deep Dive | 199

Table 5.15 Block 600,000 header verification.

| Serialized header |
| 0000002045569776d88d3962a3ffb9a0776f1f97 |
| c63f37d8ec0300000000000000000026ed8403 |
| a598b6e5d1720530db42aebfe76700add17e6b2 |
| ce416b92a1c4b76605553a5d5ca3517a73dad93f |
| SHA256 |
| dbef7e9232cc45719faa452fafde765 |
| dc694c02ea740c8b3163b0ddd460105c5 |
| SHA256 |
| 915fd963dc18429a8fbbf9c13a9f7b4 |
| 760e9055683107000000000000000000 |
| Byte Reversion |
| 00000000000000000073168569000e76 |
| b4f7a9139cfba8984a2c8d196cd59f1 |

We can represent this header in the serialized form and check that the byte-reversed double hash is clearly below the required threshold. Notice conversion from the big-endian to the little-endian format.¹

Table 5.15 demonstrates that this block is self-consistent the corresponding big-endian hash (Byte Reversion) is lower than the difficulty threshold given by Eq. (5.34) and Table 5.14.

The summary statistics for Block 600,000 are presented in Figure 5.34, while its place in the blockchain is shown in Figure 5.35.

# 5.7 Bitcoin pros and cons

There are heated debates between Bitcoin's supporters and its skeptics over its pros and cons; see, e.g., Bhutoria (2020). Skeptics argue that:

+   (1) Bitcoin's volatility prevents it from being a store of value.
(2) Bitcoin is not suitable as a means of payment.
(3) Bitcoin's mining wastes energy on an immense scale.
(4) Bitcoin's usage facilitates illicit activity.
(5) Bitcoin has no backing.
(6) A competitor will replace Bitcoin.

> ¹Mixing big-endian and little-endian formats in the Bitcoin protocol is likely a small design flaw. While standard hashes are big-endian, Bitcoin displays them in little-endian format because it considers hashes as little-endian integers rather than strings.