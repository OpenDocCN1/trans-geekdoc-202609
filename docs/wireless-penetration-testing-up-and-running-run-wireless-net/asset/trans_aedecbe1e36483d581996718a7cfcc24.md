
上一段描述的所有五个因素都可以通过攻击者嗅探空气和监听整个对话来获取。他缺少的唯一东西就是 PSK。那么，PSK 是如何生成的呢？它是通过将用户提供的 WPA-PSK 密码和 SSID 结合计算得出的。`Password-Based Key Derivation Function`（`PBKDF2`，基于密码的密钥派生函数）用于从两者的组合中生成 256 位共享密钥。

攻击者会在标准的 WPA/WPA2 PSK 字典攻击中，结合攻击工具使用一个包含大量可能密码短语的字典。该工具会从每个密码短语中提取 256 位 PSK，并将其与前面指定的其他参数结合来生成 PTK。握手数据包之一的 `Message Integrity Check`（`MIC`，消息完整性校验）将使用 PTK 进行验证。如果字典中的密码匹配，则猜测准确；如果不匹配，则不正确。

如果授权网络的密码短语存在于字典中，最终就会被识别出来。这就是 WPA/WPA2 的 PSK 破解原理！步骤如 *[Figure 4.10](#c04.xhtml#fig4_10)* 所示：

![](images/Figure-4.10.jpg)

**Figure 4.10:** WPA/WPA2 字典攻击

# 破解 WPA-PSK 和 WPA2-PSK 密码短语

要开始操作，只需遵循提供的说明。

1.  首先连接到我们的 Wireless Lab 接入点，并将其配置为使用 WPA2-PSK [AES]。我们将把 WPA2-PSK [AES] 密码改为 `abcdefgh`，使其容易受到字典攻击，如 *[Figure 4.11](#c04.xhtml#fig4_11)* 所示：

    ![](images/Figure-4.11.jpg)

    **Figure 4.11:** Netgear 路由器设置

2.  在终端中输入以下命令：

    ```
    airmon-ng start wlan0
    ```

    此命令将启动 `wlan0` 接口的监听模式，如 *[Figure 4.12](#c04.xhtml#fig4_12)* 所示：

    ![](images/Figure-4.12.jpg)

    **Figure 4.12:** airmon-ng 命令

3.  输入以下命令后按 *Enter* 键：

    ```
    airodump-ng wlan0
    ```

    这将使我们能够向无线网络注入数据包，如 *[Figure 4.13](#c04.xhtml#fig4_13)* 所示：

    ![](images/Figure-4.13.jpg)

    **Figure 4.13:** airodump-ng 命令_1

4.  输入以下命令后按 *Enter* 键，如 *[Figure 4.14](#c04.xhtml#fig4_14)* 所示：

    ```
    airodump-ng -c 11 -w wpacracking --bssid DC:EF:09:59:B1:1F wlan0
    ```

    ![](images/Figure-4.14.jpg)

    **Figure 4.14:** airodump-ng 命令_2

5.  我们可以等待新客户端连接到接入点以捕获四次 WPA2 握手，也可以通过发送广播解除认证数据包强制客户端重新加入。为了加快进度，我们采用后者。遇到未知通道错误时，也会发生同样的情况。再次使用 `--ignore-negative-one`。这可能需要多次尝试，如 *[Figure 4.15](#c04.xhtml#fig4_15)* 所示：

    ```
    aireplay-ng --deauth 1 -a DC:EF:09:59:B1:1F wlan0 --ignore-negative-one
    ```

    ![](images/Figure-4.15.jpg)

    **Figure 4.15:** aireplay-ng 命令

6.  当我们捕获到 WPA2 握手时，airodump-ng 程序会在屏幕右上角显示 WPA2 握手及接入点的 BSSID。如果你选择了 `– ignore-negative-one`，工具可能会发送固定通道消息，而不是显示 WPA2 握手。请留意短暂闪烁的 WPA2 握手提示。

7.  现在我们可以终止 airodump-ng 实用程序。让我们通过打开 cap 文件在 Wireshark 中查看四次握手。 *[Figure 4.16](#c04.xhtml#fig4_16)* 展示了你的 Wireshark 终端应有的样子。在快照中，我们从跟踪文件中选择了四次握手的第一个数据包。握手数据包使用 EAPOL 协议，如 *[Figure 4.16](#c04.xhtml#fig4_16)* 所示，握手不包含有助于恢复密钥的数据，但包含可用于检查密钥是否有效的数据。

    ![](images/Figure-4.16.jpg)

    **Figure 4.16:** Wireshark

8.  现在，我们将开始真正的密钥破解！为此我们需要一份常用单词的词汇表。Kali 的 `Metasploit` 文件夹中包含许多字典文件，如 *[Figure 4.17](#c04.xhtml#fig4_17)* 所示。必须记住，在 WPA2 破解方面，你的水平取决于你的字典。Kali 自带了一些字典，但它们可能还不够。人们的密码受多种因素影响。这包括用户的祖国、该地区流行的名字和短语、安全意识以及其他各种因素。渗透测试时，最好结合特定国家和地区的词表，如 *[Figure 4.17](#c04.xhtml#fig4_17)* 所示：

    ![](images/Figure-4.17.jpg)

    **Figure 4.17:** Metasploit

9.  如 *[Figure 4.18](#c04.xhtml#fig4_18)* 所示，我们将使用 aircrack-ng 软件，以 `pcap` 文件作为输入，以字典文件链接作为输出。如终端所示，我使用了 `nmap.lst`：

    ```
    aircrack-ng wpacracking-05.cap -w /usr/share/wordlists/nmap.lst
    ```

    aircrack-ng 使用字典文件测试各种密码组合来破解密钥。如果密码在字典文件中，最终会被破解，你的屏幕将显示如 *[Figure 4.18](#c04.xhtml#fig4_18)* 所示的内容：

    ![](images/Figure-4.18.jpg)

    **Figure 4.18:** aircrack-ng 命令

10. 请记住，因为这是字典攻击，密码必须存在于你提交给 aircrack-ng 的字典文件中。如果字典中找不到密码，攻击将会失败！

我们将包含 WPA2 四次握手的捕获文件和一份常用密码短语列表（以词表形式）提供给 Aircrack-ng，因为 WPA2-PSK 容易受到字典攻击。由于密码 `abcdefgh` 包含在词表中，Aircrack-ng 可以破解 WPA2-PSK 共享密码。值得重申的是，在基于字典的 WPA2 破解中，你的水平取决于你拥有的字典。因此，首先编制一份庞大且详细的词汇表至关重要。尽管 Kali 自带自己的词汇表，但有时可能不够用，需要添加更多单词。

# 加速 WPA 和 WPA2 破解

正如我们在上一节所见，如果我们的字典中有正确的密码，破解 WPA2-Personal 易如反掌。那么，为什么我们不直接编译一个包含数百万常用密码和短语的巨大字典呢？这对我们极其有利，我们几乎总能成功破解密码。一切听起来都很美好，但缺少了一样东西：时间。通过 `PBKDF2` 使用 PSK 密码和 SSID 计算预共享密钥，是较为消耗 CPU 和时间的计算之一。在返回 256 位预共享密钥之前，该函数会对两者的组合进行 4,096 次以上的哈希运算。破解过程的下一阶段是使用该密钥，结合四次握手的参数，根据 `MIC` 验证握手。这是一个计算成本低廉的阶段。此外，握手的特性会随时间变化；因此，此阶段无法预先计算。因此，为了加快破解过程，我们必须尽可能快地从密码计算出预共享密钥。

预计算预共享密钥（在 802.11 标准术语中也称为 `Pairwise Master Key`，即 `PMK`，成对主密钥）有助于加快速度。值得注意的是，由于 SSID 也用于计算 `PMK`，如果我们使用相同的密码但不同的 SSID，将会得到不同的 `PMK`。因此，`PMK` 同时取决于密码和 SSID。

# 加速破解过程
