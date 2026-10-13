
# Use of a DMZ

Use of a DMZ is attractive to many network managers because it has some security but allows public access outside of the corporate network. It is important to ensure that application-level firewalls are restricting access properly prior to deployment of the DMZ. This is especially important if external people will access high-value information, such as customers accessing inventory available for purchase. Once access is granted, poorly constructed firewall rules may allow access to data that should have been restricted.

## Firewalling in a Subnet Architecture

Imagine a larger organization with multiple subnets. There may be a need to limit specific types of traffic within subnets. For example, they may want to ensure that traffic within a specific subnet is encrypted with Internet Protocol Security (`IPSec`). Additionally, they may want to allow `NNTP` traffic on one subnet, but not on others. You can configure routers to provide basic packet filtering. In other words, the routers can block or allow traffic based on IP addresses, ports such as port `119` for `NNTP`, and some protocols such as Internet Control Message Protocol (`ICMP`) or `IPSec`.

If the organization wants to protect subnets within the network, basic packet filtering provided by routers might be the most appropriate choice. This model supports each type of client and service within the internal network. No hardware or software modifications or special client software would be necessary. The access through the routers used as packet-filtering firewalls is transparent for both the user and the applications. The existing routers can handle the packet filtering. This solution does not require the purchase of a host or firewall product as an expensive UNIX host, or firewall product would be unnecessary.

## Installing the pfSense Firewall

One of the best ways to learn about a technology is to use it. Installation of the pfSense firewall can be completed by a person with a basic understanding of computer hardware using the web interface for configuration.

Because pfSense is based on FreeBSD, the list of compatible hardware is the same. The FreeBSD Hardware Notes webpage at <https://www.freebsd.org/releases/11.2R/hardware.html> includes a detailed listing of processors, system boards, and self-contained devices, including cameras and video recording devices. The website is updated as new options become available.

You can install pfSense on a local firewall, on a large-scale security device, or in the cloud. pfSense is the software element of the firewall, which means you must select specific hardware based on known compatibilities. The pfSense support documentation offers guidance and troubleshooting resources.

pfSense software can be downloaded from <https://www.pfsense.org/download>. On the website, you will need to make selections based on the version, architecture (hardware), and installer type (options listed below) to identify the specific download version needed.

To install pfSense, choose between three installer options for the `ISO image` (an `.iso` file is an exact copy of a file system):

*   **Optical disc**—Systems with a CD or DVD drive can use an optical disc.
*   **USB**—The BIOS of the system must be set to boot from USB (if not, make the necessary modification or elect a different method).
*   **Memstick**—This option uses a serial memory stick (Memstick) via a serial console.

As with most Unix and Linux products, a hash value is provided for verification of the file after download. If the hashes match, the contents are unaltered. If the hashes do not match, the file may have been altered; it should be discarded and the file should be downloaded again.

Once successfully downloaded, the file must be saved to the appropriate media from the list above so that it may be installed on the selected hardware. (Although it is possible to install pfSense via `PXE`, most installations are on local media.) Specific information about each installation is available on the website.

After booting, pfSense automatically checks the hardware components to determine which hardware is accessible, if it meets the minimum specifications required, and if it is communicating properly. If the hardware does not meet the minimum requirements, a message is displayed; it identifies the issue and whether it can be corrected, such as the need to add additional RAM. The message also notes that pfSense will not install unless the minimum requirements are met. If the hardware is sufficient, pfSense starts and displays a prompt. You must accept the copyright notice or the system will not progress. After you select OK, the installation options display in a menu. The first option, Install, is the one to select.

> **WARNING**
>
> During the installation process, pfSense deletes all data on the memory device. Before you start the installation, ensure that all valuable data is safely backed up.

Next, pfSense prompts you for the filesystem you wish to use ([**FIGURE 6-4**](#16_chapter06_07.xhtml#fig6-4)). Unix File System (`UFS`) is the default in the current version, but you may choose the Z File System (`ZFS`), which is experimental but offered as an option. If you plan to use a partition on the hard drive for storing the application, that partition should be created prior to beginning the installation process for the most seamless installation.

![FIGURE 6-4 pfSense partitioning options during the installation. ¶ � pfSense](Images/9781284183658_CH06_FIGF04.png)

**FIGURE 6-4** pfSense partitioning options during the installation. ¶ � pfSense

The next prompt is for keymap selection ([**FIGURE 6-5**](#16_chapter06_07.xhtml#fig6-5)). The standard US keyboard is the default option. After pressing “Select,” the installation process begins, which includes a wipe of all files from the destination media and then installation of pfSense. The installation process typically completes within several minutes.

![FIGURE 6-5 pfSense keymap options during the installation. ¶ � pfSense](Images/9781284183658_CH06_FIGF05.png)

**FIGURE 6-5** pfSense keymap options during the installation. ¶ � pfSense

After installation, you are prompted for manual configuration options. Unless you are well versed in those options, you should select “No” and then allow the system to reboot. Remove the drive or disk you saved pfSense to first so that the system will not boot from it the next time the system starts.

After boot-up, you will need to assign interfaces using the system console. Most people use the default installation, with pre-selected options common to most applications of the product, because it is configured for the most common use of the product. The next questions are predicated by your specific use for the product. You are first prompted to assign a virtual local area network (`VLAN`), if used. There are additional instructions for using a `VLAN` on the installation website.

> **NOTE**
>
> Netgate provides step-by-step installation troubleshooting guidance on its website: <https://docs.netgate.com/pfsense/en/latest/install/installation-troubleshooting.html>. Many YouTube videos demonstrate the installation process, as well.
