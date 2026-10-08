

# php|architect 的 PHP 网络抓取指南

Matthew Turland

![](img/1e839861f06c77df9ecabc0aed9127b5_0_0.png)

php|architect
nanobooks

![](img/1e839861f06c77df9ecabc0aed9127b5_0_1.png)

# php|architect 的 PHP 网络抓取指南

作者 Matthew Turland

# **php|architect 的网络抓取指南**

正文版权 ©2009–2010 Matthew Turland – 版权所有
书籍及封面排版、设计和文字版权 ©2004–2010 Marco Tabini & Associates, Inc. – 版权所有

初版：2010年3月
ISBN: **978-0-9810345-1-5**
加拿大制作
美国印刷

未经出版方事先书面许可，不得复制、存储于检索系统或以任何形式或手段传输本书的部分内容，简短引用嵌入在评论或文章中者除外。

# **免责声明**

尽管在制作本书时已尽一切努力确保其中包含的信息准确无误，但本书是“按原样”提供的。出版方、作者、其分销商和零售商，以及所有关联方、关联公司或附属机构对因使用该信息（无论是直接还是间接）导致的任何不准确以及任何损害均不承担任何责任。我们已努力通过适当使用大写，对书中提及的所有公司和产品提供正确的商标信息。然而，我们无法保证此类信息的准确性。

Marco Tabini & Associates、MTA 徽标、php|architect、php|architect 徽标、NanoBook 以及 NanoBook 徽标是 Marco Tabini & Associates, Inc. 的商标或注册商标。

- **作者**: Matthew Turland
- **出版方**: Marco Tabini & Associates, Inc.
  28 Bombay Ave.
  Toronto, ON M3H 1B7
  加拿大

  (416) 630-6202 / (877) 630-6202
  info@phparch.com / www.phparch.com
- **出版人**: Marco Tabini
- **技术审稿人**: Luke Giuliani
- **排版与设计**: Arbi Arzoumani
- **编辑**: Beth Tucker Long
- **财务与资源管理**: Emanuela Corso
- **封面图片**: Vladimir Fofanov

# 目录

- 致谢 xiii
- 前言 xvii
- 第 1 章 — 简介 1
  - 目标受众 1
  - 如何阅读本书 2
  - 网络抓取的定义 2
  - 网络抓取的应用 3
  - 网络抓取的适当使用 4
  - 网络抓取的合法性 4
  - 涵盖的主题 4
- 第 2 章 — HTTP 7
  - 请求 8
    - GET 请求 9
    - URL 的解剖学 10
    - 查询字符串 11
    - POST 请求 12
    - HEAD 请求 13
  - 响应 13
  - 头部 15
    - Cookie 15
    - 重定向 16
      - 来源 URL 16
      - 持久连接 17
      - 内容缓存 18
      - 用户代理 18
      - 范围 19
      - 基本 HTTP 身份验证 20
      - 摘要 HTTP 身份验证 21
      - 小结 24
- 第 3 章 — HTTP 流包装器 27
  - 简单的请求和响应处理 28
  - 流上下文和 POST 请求 29
  - 错误处理 31
  - HTTP 身份验证 32
  - 其他一些选项 33
  - 小结 33
- 第 4 章 — cURL 扩展 35
  - 简单的请求和响应处理 36
  - GET 和 POST 的对比 36
  - 设置多个选项 38
  - 处理头部 38
  - 调试 39
  - Cookie 40
  - HTTP 身份验证 41
  - 重定向 42
  - 参照 42
  - 内容缓存 42
  - 用户代理 42
  - 字节范围 43
  - DNS 缓存 43
  - 超时 44
  - 请求池 44
  - 小结 46
- 第 5 章 — pecl_http PECL 扩展
  - GET 请求 50
  - POST 请求 50
  - 处理头部 52
  - 调试 54
  - 超时 54
  - 内容编码 54
  - Cookie 55
  - HTTP 身份验证 56
  - 重定向和参照 57
  - 内容缓存 57
  - 用户代理 57
  - 字节范围 57
  - 请求池 58
  - 小结 59
- 第 6 章 — PEAR::HTTP_Client
  - 请求和响应 62
  - 数据处理 64
  - 头部处理 65
  - 使用客户端 66
  - 观察请求 67
  - 小结 68
- 第 7 章 — Zend_Http_Client
  - 基本请求 71
  - 响应 72
  - URL 处理 73
  - 自定义头部 73
  - 配置 74
  - 连接 75
  - 调试 75
  - Cookie 76
  - 重定向 77
  - 用户代理 77

