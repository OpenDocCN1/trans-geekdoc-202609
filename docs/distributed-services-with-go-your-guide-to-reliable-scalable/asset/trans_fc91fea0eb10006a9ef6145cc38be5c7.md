
| | require.NoError(t, err) |
| | res, err := stream.Recv() |
| | require.NoError(t, err) |
| | if res.Offset != uint64(offset) { |
| | t.Fatalf( |
| | "got offset: %d, want: %d", |
| | res.Offset, |
| | offset, |
| | ) |
| | } |
| | } |
| | } |
| | } |
| | stream, err := client.ConsumeStream( |
| | ctx, |
| | &api.ConsumeRequest{Offset: 0}, |
| | ) |
| | require.NoError(t, err) |
| | } |
| | for i, record := range records { |
| | res, err := stream.Recv() |
| | require.NoError(t, err) |
| | require.Equal(t, res.Record, &api.Record{ |
| | Value: record.Value, |
| | Offset: uint64(i), |
| | }) |
| | } |
| | } |
| | } |
| | testProduceConsumeStream(\*testing.T, api.LogClient, \*Config) is the streaming counterpart to testProduceConsume, testing that we can produce and consume through streams. |
| | Run $ make test to test your code. In the test output, you’ll see your TestServer test passing. |
| | Wahoo! You’ve written and tested your first gRPC service. |
| | |
| | You now know how to define a gRPC service in protobuf, compile your gRPC protobufs into code, build a gRPC server, and test that everything works end-to-end across your client and server. You can build a gRPC server and client, and you can use your log over the network. |
| | Next we’ll improve the security of our service by encrypting the data sent between the client and server with SSL/TLS, and authenticating requests so we can know who’s making each request and whether they’re allowed to. |
| | |
| | ### Encrypt In-Flight Data |
| | Encryption of data in-flight prevents man-in-the-middle attacks (MITM).^([\[21\]](#f_0046.xhtml#FOOTNOTE-21)) An example of a MITM attack is active eavesdropping, where the attacker makes independent connections with the victims to make them think they’re talking directly with each other when in fact the conversation is controlled by the attacker. This is bad because not only can the attacker learn confidential information, but also the attacker can maliciously change the messages sent between the victims. For example, say Bob was trying to send money to Alice using PayPal, but Mallory changed the account the money was sent to from Alice’s to her own. |
| | |
| | | Cryptography’s Conventional Names |
| | | --- |
| | | ![images/aside-icons/info.png](Images/info.png) || Bob, Alice, and Mallory are placeholder names commonly used when discussing cryptography ([https://en.wikipedia.org/wiki/Alice_and_Bob#Cast_of_characters](https://en.wikipedia.org/wiki/Alice_and_Bob#Cast_of_characters)). Typically Alice and Bob want to exchange a message, and Mallory is a malicious attacker. There’s a whole cast of characters, and they’re named with rhyming mnemonics to their role (for example: Mallory the malicious attacker, Eve the eavesdropper, Craig the password cracker). |
| | | --- | --- | --- |
| | | The most widely used technology for preventing MITM attacks and encrypting data in-flight is TLS, the successor to SSL. TLS used to be considered necessary only for "serious" websites like online banks, but these days all sites should use TLS.^([\[22\]](#f_0046.xhtml#FOOTNOTE-22)) Modern browsers highlight websites that don’t use TLS as unsafe and recommend their users to not even use them. |
| | | The process by which a client and server communicate is kicked off by a TLS handshake. During this handshake, the client and server: |
| | | 1. Specify which version of TLS they’ll use; |
| | | 2. Decide which cipher suites (the set of encryption algorithms) they’ll use; |
| | | 3. Authenticate the identity of the server via the server’s private key and the certificate authority’s digital signature; and |
| | | 4. Generate session keys for symmetric encryption after the handshake is complete. |
| | | Once this handshake process is complete, the client and server can communicate securely. |
| | | Fortunately we don’t have to worry about implementing these TLS handshake steps, as TLS handles them for us behind the scenes. Our job is to obtain certificates for our client and server to use and to tell gRPC to communicate over TLS using the given the certs. |
| | | We’ll build TLS support into our service to encrypt data in-flight and authenticate the server. |
| | |
| | ### Authenticate to Identify Clients |
