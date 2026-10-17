Terraform is a well-known tool to help rapidly provision and configure infrastructure for cloud servers. Terraform can be leveraged to help provision certain types and configurations of cloud servers when setting up infrastructure. There are many blog posts and tutorials online which can help

If we know that we are planning on leveraging certain types of packages in a package manager, we can have them automatically added to our system when running a script.

In conclusion, utilize and learn the various VPS providers on the Internet. There are certain levels of trust and activity provided by each provider which makes them unique. Learn how your target will be expected to respond and ensure that the way you position your attack will be fruitful.

# PROXY TECHNOLOGY

Proxies are used to mask and perform requests on behalf of ourselves, allowing us to effectively hide our locations. During a paid penetration testing engagement, it is very common for penetration testers to utilize various proxies to ensure that all testing traffic originates from a known location. At the same time, proxies are used by malicious individuals as a disposable location to mask their true locations. We can use this technology to our advantage to ensure that our location is properly protected.

It’s important to understand that the use of this technology is not illegal or immoral in any way. How the technology is used is entirely another manner, where the malicious use of technology to defraud others is an illegal and immoral activity. We will learn how to effectively utilize this to protect ourselves and provide security services to others.

# SOCKS PROXIES

Socket Secure (SOCKS) proxies are some of the easiest and most common forms of proxy servers on the Internet. They can be easily created and tunneled through an SSH connection allowing for a secure and protected connection to the Internet. Additionally, various free and paid providers offer SOCKS proxies available for use on the Internet.

The idea of using a proxy is to have another server on the Internet take your request and send it on its behalf. By serving this request, the target website does not know who the original requesting identity is. Instead, the server only sees the middle proxy server which is directly sending the request.

Establishing a SOCKS proxy can be done using an SSH command to connect to a server that we control. This SSH tunnel for the SOCKS proxy opens a port on our localhost, which we can direct our tools and browsers to direct our traffic toward the Internet. Establishing a SOCKS connection is easy, and can be completed with a command similar to below:

```
ssh -D 9123 m4lwhere@myserver.lol
```

What this command does is establish an SSH connection for the username m4lwhere on the server **myserver.lol**. The **-D 9123** switch tells SSH to open local TCP port 9123 on my machine to send traffic through **myserver.lol**. After logging into the server, the SSH tool will open the local port 9123 on the client side, on our machine, to allow SOCKS connections to be tunneled over the SSH connection. This assumes that you have access to the account on that server, otherwise, the SOCKS connection will not be established.

Once we have established the SOCKS proxy, we can connect to it by pointing our browser toward the correct location. Most major browsers offer a SOCKS proxy configuration within their settings, which we can use to provide our local port of 9123 we have opened.