
![Image](boxx.jpg) **A, B,** and **D** are incorrect. These actions will not necessarily help against vulnerabilities that the firmware is exposing the device to.

##### Performance-Based Questions

[**21.**](#ch08.xhtml#rch8que21) The Security+ exam may present to you a network diagram and expect you to identify rules that need to be configured on the firewall based on criteria presented in the question. The exam will most likely ask you to choose the rules from a list of available rules. The following illustration identifies the rules for this scenario:

![Image](f0388-01.jpg)

[**22.**](#ch08.xhtml#rch8que22) The following is the correct matching of security terms to their descriptions.

![Image](f0388-02.jpg)

## Chapter 9

## Wireless Networking and Security

### CERTIFICATION OBJECTIVES

[9.01 Understanding Wireless Networking](#ch09.xhtml#ch9obj01)

[9.02 Securing a Wireless Network](#ch09.xhtml#ch9obj02)

[9.03 Configuring a Wireless Network](#ch09.xhtml#ch9obj03)

[9.04 Other Wireless Technologies](#ch09.xhtml#ch9obj04)

[✓ Two-Minute Drill](#ch09.xhtml#ch9lev1sec6)

[**Q&A** Self Test](#ch09.xhtml#ch9lev1sec7)

Today’s networks are no longer limited to using cabled, or wired, devices. Networks now have a mix of wired systems and wireless systems that use radio frequencies to send data to a `wireless access point`. The `wireless access point` has a connection to the wired network that allows wireless devices to communicate with hosts on the wired network. Many small office networks and home office networks use a home router (see [Figure 9-1](#ch09.xhtml#ch9fig1)), which is a multifunctional device that acts as a switch, router, and `wireless access point` for wireless clients. Note that in large enterprise networks, the `wireless access point` would have a single port to connect the wired network.

![Image](f0390-01.jpg)

**FIGURE 9-1**  

A `wireless access point`, also known as a `wireless router`

This chapter introduces you to the world of wireless networks. It’s an important topic to know for the Security+ certification exam, so be sure to study this chapter well. This chapter will introduce you to wireless standards and protocols, show you how to set up a `wireless network`, and then discuss some `wireless security` concerns.

### CERTIFICATION OBJECTIVE 9.01

### Understanding Wireless Networking

As mentioned, the `wireless network` uses radio frequencies to transmit data through the air. This means that if you have laptop users who wish to be mobile within the office, you can allow them to access the `network` through a `wireless access point` as long as they have a `wireless network card` in their laptop.

You can create two types of `wireless networks`: an `ad hoc mode wireless network` and an `infrastructure mode wireless network`. With `ad hoc mode`, the `wireless device`, such as a laptop, is connected directly to other `wireless devices` in a peer-to-peer environment without the need for a `wireless access point`. With `infrastructure mode`, the `wireless clients` are connected to a central `wireless access point`. The `wireless client` sends data to the `access point`, which then sends the data on to the destination on the `wired network`, as shown in [Figure 9-2](#ch09.xhtml#ch9fig2).

![Image](f0391-01.jpg)

**FIGURE 9-2**  

A typical `wireless network` running in `infrastructure mode`

Each of these `wireless modes` has its advantages. The advantage of `ad hoc mode` is that you don’t need to purchase the `access point`, because `ad hoc mode` is designed to connect systems directly together using `wireless communication`. With `ad hoc wireless`, your goal is to allow the systems to connect in order for the users to share data or maybe play a LAN game together. The advantage of `infrastructure mode` is that you can use the `wireless access point` to give all `wireless users` access to the Internet. With `infrastructure mode`, you can typically control who can connect to the `wireless network` and you can filter out types of `network traffic`. For example, if you use a `wireless access point` to allow `wireless clients` to connect to the Internet, you can control which web sites the users can connect to. This type of centralized control makes `infrastructure mode` extremely popular.

#### Standards

The `Institute of Electrical and Electronics Engineers (IEEE)` committee has developed `wireless standards` in the `802` project models for `wireless networking`. `Wireless` is defined by the `802.11` project model and has several standards defined.

##### 802.11a

The `802.11a` `wireless standard` is the first of the `wireless standards` that runs at the `5-GHz` (gigahertz) frequency. `802.11a` devices can transmit data at `54 Mbps`.

##### 802.11b

The `802.11b` `wireless standard` has a transfer rate of `11 Mbps` while using a frequency of `2.4 GHz`. `802.11b` devices are not compatible with `802.11a` networks because they run on different frequencies. It should also be noted that `802.11b` started the `Wi-Fi` (wireless fidelity) standard.

##### 802.11g

After `802.11b`, the `802.11g` `wireless standard` came out and was designed to be compatible with `802.11b`, but it also increases the transfer rate. The transfer rate of `802.11g` devices is `54 Mbps` in the `2.4-GHz` frequency range.

All `802.11g` devices are compatible with `802.11b` devices because they all follow the `Wi-Fi` standard and run at the same frequency of `2.4 GHz`.

##### 802.11n

The `802.11n` `wireless standard` was finalized in late `2009`. The goal of `802.11n` is to increase the transfer rate beyond what current standards such as `802.11g` support. The `802.11n` standard was rumored to support transfer rates up to `600 Mbps` in theory, but most `802.11n` networking components are running at `150 Mbps` today. To help accomplish higher transfer rates, `802.11n` uses two new features: `multiple input multiple output (MIMO)` and `channel bonding`. `MIMO` is the use of multiple antennas to achieve more throughput than can be accomplished with only a single antenna. `Channel bonding` allows `802.11n` to transmit data over two channels to achieve more throughput. The `802.11n` standard is designed to be backward compatible with `802.11a`, `802.11b`, and `802.11g` and can run at the `2.4-GHz` or `5-GHz` frequency.

It is important to note that `802.11a` was an early implementation of `wireless networking` and is not compatible with the `Wi-Fi` networks. As an example of the compatibility, my previous `wireless network` at home had an `access point` that was an `802.11g` device, but one of my old laptops had an `802.11b` `wireless network card`. I was still able to have my old laptop communicate on the `network` because the two standards are `100 percent` compatible with one another. In this example, the laptop with the `802.11b` card connects only at `11 Mbps`, while a newer laptop with an `802.11g` card can connect at `54 Mbps`.

##### 802.11ac

The `802.11ac` `wireless standard` was approved in `2014` and is considered a high-throughput `wireless standard` that runs at the `5-GHz` frequency range. The `802.11ac` standard offers throughput of potentially `1 Gbps` by increasing the channel width and offering similar features to the `802.11n` standard such as `MIMO` and `multi-user MIMO (MU-MIMO)`, which involves allowing multiple transmitters to send separate signals and multiple receivers to receive separate signals at the same time.

Most `802.11ac` `wireless routers` have a `USB 3.0` port that allows you to connect an external hard drive to the `wireless router` and stream HD video to clients.

![Image](exam.jpg)

**For the Security+ certification exam, ensure you are familiar with the basics of the IEEE standards for wireless networking: `802.11a/b/g/n/ac`.**

[Table 9-1](#ch09.xhtml#ch9tab1) summarizes key points you need to be familiar with about the different `wireless standards` for the Security+ certification exam.

**TABLE 9-1**  

Comparing the Different `Wireless Standards`

![Image](t0393-01.jpg)

#### Channels
