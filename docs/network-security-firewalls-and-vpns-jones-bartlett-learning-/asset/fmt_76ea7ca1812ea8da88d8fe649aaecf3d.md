
# SSL/TLS and VPNs

While SSL/TLS is supposed to authenticate servers, it hasn’t been as robust as originally planned. Phishing attacks—that is, attacks that direct a user’s browser to a counterfeit Web site—are a major problem for security professionals. Users typically do not check to see if a site is encrypted or if the certificate information matches their destination Web site. Newer versions of browsers check encryption status for the user and warn of a mismatch between a certificate and the domain presenting it.

SSL/TLS can also perform bidirectional authentication by using client-based certificates. This is particularly helpful when using this protocol to access a protected network, as it adds a layer of authentication to the access.

## SSL/TLS and VPNs

As you learned in the section on `IPSec`, a VPN creates a secure tunnel through a public network like the Internet. While SSL VPNs still leverage the concept of tunneling, they create their tunnels differently than `IPSec`. An SSL VPN establishes connectivity using the SSL protocol. `IPSec` works at Layer 3 of the OSI model, while `SSH` functions at Layers 4 and 5. SSL VPNs can also encapsulate information at Layers 6 and 7, which makes SSL VPNs some of the most flexible available.

An additional function of an SSL VPN is that it usually connects using a Web browser, whereas an `IPSec` VPN generally requires client software on the remote system.

SSL VPNs create predominantly remote access VPN connections, where a client connects to applications on an internal network. This is different from a site-to-site connection, where two gateways connect disparate private networks across the Internet.

### SSL/TLS VPNs benefits over IPSec VPNs include:

*   **Less expense**—Since an SSL VPN is typically clientless, you don’t have the costs of rolling out, supporting, and updating client software.
*   **Platform independence**—Since the access to an SSL VPN comes through the standard SSL interface, which is a component of virtually every Web browser, virtually any OS that runs a browser is supported. While the operating system (OS) support for VPN clients is good for common OSs, a significant lag can exist in client development following the release of a new OS or the release of a new client version. You may see a Windows client 90 to 180 days earlier than the Mac version.
*   **Client flexibility**—As a general rule, `IPSec` clients are installed only on corporate systems. Due to the additional configuration flexibility, SSL VPNs allow access from a variety of clients, including corporate systems, home systems, customer or supplier systems, or even a kiosk machine in a library or an Internet café. This wider accessibility tends to increase employee satisfaction with the technology.
*   **No problems with network address translation (NAT)**—Historically, NAT caused issues with `IPSec` VPNs. As a result, virtually all `IPSec` vendors have created workarounds. With an SSL VPN, you don’t have these issues because SSL works at a higher layer than `IPSec` and, as a result, is not affected by NAT.
*   **Granular access control**—This is a benefit or a drawback, depending on your environment. SSL VPNs require a greater granularity of access than a typical `IPSec` VPN because instead of creating a tunnel from the host to the internal network, SSL VPNs require explicit definition of each resource accessed. The upside is that, unless you have defined it explicitly, an SSL VPN user cannot access the resource. Although this barrier has significant security benefits, in a complex environment, this could add significant overhead to your VPN support.
*   **Fewer firewall rules required**—To access an `IPSec` gateway across a firewall, you need to open several ports to support the individual protocols for authentication and the tunnel. With an SSL VPN, you need to open only port 443, which is easy because of the prevalence of the HTTPS protocol.

For more information on TLS, see <http://tools.ietf.org/html/rfc5246>.

# Secure Shell (SSH) Protocol

The **Secure Shell (SSH)** protocol is a method for secure remote logon and other secure network services over a public network such as the Internet. SSH services a number of applications across multiple platforms including UNIX, Microsoft Windows, Apple Mac, and Linux.

You can use SSH:

*   For logon to a shell on a remote host, replacing telnet and rlogin (see [Figure 12-3](#19_chapter12.xhtml#fig12-3) for an example of an application that uses SSH for this application)
*   For executing a single command on a remote host, replacing rsh
*   For file transfers to a remote host
*   In combination with rsync to back up, copy, and mirror files securely
*   In conjunction with the OpenSSH server and client to create a full VPN connection

The SSH protocol consists of three major components:

*   Transport Layer Protocol, which provides server authentication, confidentiality, and integrity with perfect forward secrecy
*   User Authentication Protocol, which authenticates the client to the server
*   Connection Protocol, which multiplexes the encrypted tunnel into several logical channels

For more information on SSH, see <http://tools.ietf.org/html/rfc4251>.

![Figure 12-3](images/pg362.jpg)

**FIGURE 12-3** PuTTY is an application that leverages SSH to provide secure connections to hosts.

# Establishing Performance and Stability for VPNs

Now that you have an in-depth understanding of the many options available to you for VPNs as well as other secure access protocols, it’s time to discuss some of the challenges you might encounter when supporting your VPN. For your VPN rollout to be successful, consider two factors: performance and stability.

## Performance

Some critical factors can affect the performance of your VPN:

*   **VPN type**—When considering the performance of your VPN, consider the type of VPN you’ve chosen. The performance characteristics of a VPN supporting remote clients can be very different from the performance characteristics of a VPN supporting site-to-site connections, or even a mixture of remote clients and site-to-site connections.
*   **Protocol**—The performance characteristics associated with an `IPSec` VPN can be very different from what you may find with an SSL VPN implementation. How you apply `IPSec` and `SSL/TLS` in a VPN solution can affect your VPN’s performance. Validating the performance specifications of the solution before you roll out should allow you to address any performance issues associated with the protocol startup.
*   **Load**—The number of remote access or site-to-site VPNs will affect the overall performance of your VPN rollout. The challenge in addressing this issue, particularly in an environment supporting a large pool of remote clients, is that the performance issues will tend to crop up during peak use. To appropriately diagnose these issues, you’ll need to be able to report on use in a way that tracks the peaks. Many of the current reporting tools available for VPNs tend to show averages over time, which can hide peaks and valleys in your use numbers. Be sure you fully understand these performance reports.
