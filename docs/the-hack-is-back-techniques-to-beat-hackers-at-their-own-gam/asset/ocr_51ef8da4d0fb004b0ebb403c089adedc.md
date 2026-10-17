WireGuard peer on the Internet will not appear to have any open services, no matter how much scanning is completed.

Before using WireGuard, we need to make sure that we have the packages or software installed to operate with. For Windows-based machines, there is a GUI-based system to manage tunnels which can be downloaded at [https://www.wireguard.com/install/](https://www.wireguard.com/install/). For Linux-based machines, most package managers will install it through the **wireguard** package name, such as the command below.

```
sudo apt install wireguard
```

To connect two systems via WireGuard, we must create a set of keys for each machine. WireGuard leverages public key cryptography and will have a public and private key pair to encrypt the activity with. To get started, we can follow the quick-start command on the WireGuard website at [https://www.wireguard.com/quickstart/](https://www.wireguard.com/quickstart/).

We must start by generating the keypairs. This is done with the **wg genkey** command. This information is then plugged into the WireGuard configuration files to ensure that the proper cryptographic functions take place.

```
$ wg genkey > private        # Create the private key
$ cat private
2NK4DMK0o8LrGgfLfqoH8Xtc6IaegUm9alJZiaxDz1s=       # Our sample private key

$ wg pubkey < private        # Create public key from private key
8vBgNPyPBAX/3dRtd0HFEvxbQ+8zN1FiHUb+mtIuu34=       # Our public key
```

To run the WireGuard program, we can use the **wg-quick** command to quickly start a WireGuard tunnel based on a preconfigured file. By default, the **wg-quick** command will search within the **/etc/wireguard** directory for a configuration file provided in the command. For example, the command **wg-quick wg0** will search for the **/etc/wireguard/wg0.conf** file and attempt to start the WireGuard tunnel.

To use this, we must make sure we have a configuration file placed in **wg0.conf**. A sample configuration file is below — this is used to connect to a peer on the Internet. Each configuration file must have the **[Interface]** and the **[Peer]** sections to understand where and how to connect to another host. The **[Interface]** is the local WireGuard interface on the host and will contain the IP address assigned to the WireGuard interface. The **PrivateKey** is used to encrypt the communications originating from the interface and is decrypted with the associated **PublicKey** shared with the endpoint peer.

```
[Interface]
Address = 100.64.0.3/32
ListenPort = 51183
PrivateKey = 2NK4DMK0o8LrGgfLfqoH8Xtc6IaegUm9alJZiaxDz1s=

[Peer]
PublicKey = YpXkz+iuD6kq9cUQPqrekAZGxeD0Ruv0AnIROdRBTs=
Endpoint = 10.0.0.1:443
AllowedIPs = 100.64.0.0/24
PersistentKeepalive = 25
```

The configuration above will set the address **100.64.0.3** on the WireGuard interface and attempt to establish a connection to the host **10.0.0.1**. This requires that we have a separate, traditional interface that can connect to **10.0.0.1** directly. The WireGuard interface will encrypt the traffic across the 10.0.0.1 connection and establish a new set of IPs on the 100.64.0.0 network. The **PersistentKeepalive** is used to send a regular interval of packets to ensure the NAT traversal remains.