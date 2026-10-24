# High-speed Data J and Data K

The definitions for High-speed Data J and Data K states are identical to those for full-speed J and K:

| Bus State | Data State, High Speed |
|---|---|
| Differential 0 | K |
| Differential 1 | J |

# Chirp J and Chirp K

The Chirp J and Chirp K bus states are present only during the high-speed detection handshake. The handshake occurs when a 2.0 hub has placed a downstream bus segment in the Reset state. Chirp J and Chirp K are defined as DC differential voltages. In a Chirp J, D+ is more positive than D-, and in a Chirp K, D- is more positive than D+.

A high-speed device must use full speed on attaching to the bus. The high-speed detection handshake enables a high-speed device to tell a 2.0 hub that the device supports high speed and to transition to high-speed communications.

As Chapter 4 explained, shortly after detecting device attachment, a device’s hub places a device’s port and bus segment in the Reset state. When a high-speed-capable device detects the Reset, the device sends a Chirp K to the hub for 1 to 7 milliseconds. A 2.0 hub that is communicating upstream at high speed detects the Chirp K and in response, sends an alternating sequence of Chirp Ks and Js. The sequence continues until shortly before the Reset state ends. At the end of Reset, the hub places the port in the High-speed Enabled state.

On detecting the Chirp K and Chirp J sequence, the device disconnects its full-speed pull-up, enables its high-speed terminations, and enters the high-speed Default state.

A 1.x hub ignores the device’s Chirp K. The device doesn’t see the answering sequence and knows that communications must take place at full speed.