

# 第8章 搜索引擎 Dorks 171

23 BOOROW
24 GOOGLE(CSE) 通用随机

# 特殊引擎

+   e1 - TOR 查找器
e2 - ELEPHANT
e3 - TORSEARCH
e4 - WIKILEAKS
e5 - OTN
e6 - EXPLOITS SHODAN

all - 所有搜索引擎 / 非特种引擎

+   --proxy 选择你想要通过搜索引擎使用的代理：
--proxy-file 设置字体文件（文件）以为每个搜索引擎随机分配代理。

+   --time-proxy 设置代理更换的频繁时间。
--tor-random 启用 TOR 功能，每次使用都会关联一个唯一的 IP。
--t 选择验证类型：

+   --dork 定义将要使用的 d 个搜索搜索引擎。
--dork-file 设置包含你的搜索 dorks 的文件。
-a 指定将将用于搜索脚本的字符串：
-m 开启在指定的 url 上搜索电子邮件。

+   -u 开启在指定的 url 上搜索 URL 列表。
--save-as 将结果保存在特定位置。
--user-agent 定义在针对目标发送请求时使用的用户代理。

+   --regexp 使用正则表达式验证其研究结果
--replace 替换目标 URL 中的值。
--cms-check 启用简单的检查 url/目标是否在使用 CMS。
--sall 保存扫描器找到的所有 url。
--ifcode 根据你返回的 http 状态码验证结果。
--delay 搜索处理过程之间的延迟。

+   --command-all 使用此命令为找到每一个 URL 指定单个命令。

# 使用 Inurlrb

现在应该已经显而易见，Inurlrb 实际上是一个用于扫描易受利用漏洞的黑帽工具。这意味着它没有正当且实用的用途。

# 提示：如果你是一个想要创业或获得某些安全经验的安全创业者，你可以将此工具作为进入有漏洞组织的敲门砖。一旦你识别出漏洞，你就可以通知组织该漏洞。他们会对你的工作留下深刻印象，甚至聘佣你来帮助保护他们的系统！

但要小心。在正式成为他们的客户之前，你必须告诉他们漏洞的情况并帮助他们修复，否则他们可能会将这种行为视为勒索。

Inurlrb 是基于 PHP 的，因此其运行方式可能与其他 Python 脚本略有不同。确保你已经搭建好了 PHP 环境。首先，让我们仅使用 Bing 搜索深度导出，以查找活跃的 AXIS 摄像头（结果如图 8.11 所示）：

```
inurlrb.php --dock inurl:view/index.shtml -q 2 -s save.txt
```

![](img/ceaab52f5a948b18995b8efe89758781_191_0.png)

+   - 黑客之间的网络战，系统没有和平。
- http://inurlrb.com/
- http://inurlrb.com/
- http://github.com/inurlrb
- [3] 骗子警示 (): 2019-03-19 23:39-165-Ubuntu Ubuntu Wed Oct 24 18:55:20 x86_64
- [2] per -- /apt/scanner-SCANNER-INDEXER
- [1] 正在启动 SCANNER 2.1 于 [2019-01-27 18:27:08]
- 此工具在未经先许可的情况下针对对象是非法的。
你有责任遵守所有相关的当地、州和联邦法律。
开发者声明不承担任何责任，且对程序造成的任何误用或损坏不负责。

```
[INFO] 完成: [inurlrb/output/save.txt]
[INFO] 完成: [inurlrb/view/index.shtml]
[INFO] BING
[INFO] 正在处理...
[INFO] 找到的值: [ 164 ]
[INFO] * [2019-01-27]
[+] 目标: http://www.onlinecameras.com/inurl-view-index.shtml-live-webcam/
[+] 信息 服务器: HTTP/1.1 Modified by Proxy, Server: Linux-ubuntu/8.5 X-Powered-By: PHP/7.1.1, IP:104.193.175.80
[+] 找到: 未识别
```

图 8.11

那是164 个结果，而且只是 Bing！如果你想将搜索扩展到不仅仅是特定的，请使用 -q all。

天空才是真正的限制。随着你深入搜索，你几乎会遇到引擎封锁（例如验证码），用以验证你是人类。你可以通过切换代理来尝试绕过这些检查。

如果你在寻找用于搜索的 dorks，不要忘记漏洞数据库 (https://www.exploit-db.com)。

