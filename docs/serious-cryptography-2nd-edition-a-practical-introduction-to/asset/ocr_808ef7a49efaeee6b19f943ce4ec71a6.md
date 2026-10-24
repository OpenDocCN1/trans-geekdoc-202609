NOTE Nonce is short for “number used only once.” In the context of stream ciphers, we sometimes call it the IV, for “initial value.”

From a high-level perspective, there are two types of stream ciphers: stateful and counter based. Stateful stream ciphers have a secret internal state that evolves throughout keystream generation. The cipher initializes the state from the key and the nonce and then calls an update function to update the state value and produce one or more keystream bits from the state, as Figure 5-2 shows. For example, RC4 is stateful while Salsa20 is counter based.

![](bbox=[0.24, 0.3, 0.72, 0.44])

Figure 5-2: A stateful stream cipher

Counter-based stream ciphers produce chunks of a keystream from a key, a nonce, and a counter value, as in Figure 5-3. Unlike stateful stream ciphers, counter-based stream ciphers such as Salsa20 don’t keep track of a secret during keystream generation, apart from the counter’s value.

![](bbox=[0.25, 0.6, 0.7, 0.75])

Figure 5-3: A counter-based stream cipher

These two approaches define the high-level architecture of the stream cipher, regardless of how the core algorithms work. The internals of the stream cipher also fall into two categories, depending on the target platform of the cipher: hardware oriented and software oriented.

# Hardware-Oriented Stream Ciphers

When cryptographers talk about hardware, they mean application-specific integrated circuits (ASICs), programmable logic devices (PLDs), and field-programmable gate arrays (FPGAs). A cipher’s hardware implementation