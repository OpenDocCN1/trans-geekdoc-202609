
# FIGURE 9.9

最后一个要查看的功能在“分析”菜单中。Wireshark 在接收到帧和数据包后会对其进行分析。我们之前通过查看帧列表和颜色来观察这些分析。此外，当我们查看协议解码时，可以看到 Wireshark 识别出的信息在方括号中出现错误的情况。你不需要浏览整个数据包捕获文件，逐个查找错误。相反，前往“分析”菜单，选择“专家信息”，即可查看 Wireshark 标记为问题的所有帧。如图 9.12 所示：

![FIGURE 9.10 Protocol Hierarchy Statistics](images/c09f010.png)

**FIGURE 9.10**

![FIGURE 9.11 Conversations statistics](images/c09f011.png)

**FIGURE 9.11**

## Spoofing Attacks

你可能不必只捕获发往你系统的数据包，或者通过重新配置交换机才能接收到的数据包。还有其他方式可以让消息到达你。可以通过使用不同类型的 Spoofing 攻击实现。Spoofing 攻击是指假装自己是一个你不是的系统。你可以从不同层开始进行这种攻击，从第 2 层开始。你也可以在更高层进行 Spoofing，利用 DNS 让系统将流量发送到你想要的系统。Spoofing 攻击让你能够位于两个端点之间的对话中。

这引出了一个需要记住的问题。如果你在进行 Spoofing 攻击，意味着对话的至少一端可能没有到达正确的终点。如果一切看起来不正常，别人就会开始怀疑。这意味着你需要确保对话完整。如果有人怀疑有问题，他们可能会寻找原因，这可能导致你被识别。显然，如果你在进行 Spoofing 攻击，你不想被识别并被捕获。正如以往一样，你需要确保使用这些能力是为了行善而不是作恶。

### ARP Spoofing

**The Address Resolution Protocol (ARP) has two stages.** The first is the request, where a system knows an IP address but doesn't know the corresponding MAC address. It sends an ARP request asking for the system with the IP address to respond with its MAC address. The response is the system replying, indicating its MAC address to the requestor. There is nothing to authenticate that request, though. In theory, anyone could respond to that request with their MAC address to get the requesting system to send the message to the attacker's/spoofer's address. We could make it even easier by simply not waiting for the request to begin with and just sending the reply.

To be efficient, systems will take any ARP responses, even if they didn't ask, and cache the mapping. This keeps them from having to ask for the MAC address should they ever need it. This is a feature we can take advantage of. We could just send out ARP responses, mapping whatever IP address on the network we want to our MAC address. This would get all systems on the local network sending messages to us, as our address is in their ARP cache. The process of just sending out ARP responses without a corresponding ARP request is called *gratuitous ARP*, meaning it's an ARP message that wasn't asked for.

One of the problems we have is the length of time ARP entries are cached for. On Linux systems, the default cache length is 60 seconds. You can check it from an entry in the `/proc` pseudo file system, as you can see in the following code listing. You could also change the behavior by replacing the 60 with another value. On Windows systems, the cache time is different. Microsoft opted to follow RFC 4861, which applies to IPv6, for the IPv4 implementation. Starting with Windows Vista, Microsoft has a base time of 30,000 milliseconds, which is multiplied by a random value between .5 and 1.5 to get the cache duration. This means it's different from one system to another and also from one boot to another.

**ARP Cache Duration on Linux**

```
cat /proc/sys/net/ipv4/neigh/default/gc_stale_time
60
```

Because the cache can time out quickly, we have to keep sending out our gratuitous ARP responses. Obviously, this is something better done programmatically rather than manually. This is especially true since there is another problem. When we redirect messages to our system, we really need to forward them back out onto the network with the correct MAC address in the destination field. Otherwise, conversations don't happen. A TCP connection never completes because the SYN or the SYN/ACK never reaches the appropriate destination system. Instead, it is sent to our system where it dead‑ends unless we do something. This requires turning on forwarding so the message we are hijacking can be forwarded back out the same interface to get to its intended destination.

There are a few programs that can be used to handle ARP spoofing. One of them, `arpspoof`, has been around for a long time now. It was written by Dug Song, who also wrote a program called `fragroute`, which is useful in its own way. Using `arpspoof`, we can inject ourselves in between two systems on the network. We can tell `arpspoof` which two IP addresses we want to pretend to be. It takes care of the rest for us. In the following code listing, you can see a run of `arpspoof` where I've selected the default gateway on my network to be the one I spoof. This means I get messages that are destined for the default gateway, so anything that's going off‑net gets sent to the system running `arpspoof`. You'll see the gratuitous ARP responses being sent. They get sent out every few seconds to ensure that no ARP cache entries age out. On some Linux systems, such as Kali Linux, you will need to install `arpspoof` along with other sniffing tools in a package called `dsniff`.

**Using `arpspoof`**
