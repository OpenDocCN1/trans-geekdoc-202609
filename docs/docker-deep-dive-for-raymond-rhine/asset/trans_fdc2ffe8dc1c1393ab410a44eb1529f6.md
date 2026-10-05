

```
$ docker service inspect --pretty web-fe
ID: z7ovearqmruwk0u2vc5
Name: web-fe
Service Mode: Replicated
Replicas: 5
ContainerSpec:
 Image: nigelpoulton/gsd:1.0
 init: false
Endpoint Mode: vip
Ports:
  PublishedPort = 8080
  Protocol = tcp
  TargetPort = 80
  PublishMode = ingress
UpdateConfig:
  Parallelism: 1
  On failure: pause
```

# Docker 深度解析
## 一本书读通 Docker

2024 年版

作者：Docker 队长 (Docker Captain)
igel Poulton

# Docker 深度解析

2024 年 5 月

# 一本书读通 Docker 🚀

Nigel Poulton @nigelpoulton

# 关于本版本

本版本于 2024 年 5 月出版。

在编写本版时，我仔细检查了每一个章节的每一个字，确保所有内容都与 Docker 最新版本以及行业最新趋势保持同步。我还删除了重复内容，并使每个章节都更加简洁。

主要变化包括：

- 增加了大量关于 BuildKit、buildx 和全新的 Docker Build Cloud 的内容
- 关于 Docker Scout 的全新章节
- 使用 `docker init` 命令的全新内容
- 关于 Docker Debug 和使用 `docker debug` 命令的全新内容
- 关于在 Docker 中使用 WebAssembly (Wasm) 的新章节
- 更新了所有图片以获得更高质量
- 添加了术语表

祝你阅读愉快，准备好掌握容器技术吧！

![](img/aae0230bf8529bd80767c4c780dca8d3_3_0.png)

(c) 2024 Nigel Poulton

感谢所有阅读我的书籍和观看我培训视频的朋友。我对所有的内容都充满热情，当你们与我联系并提供反馈时，对我意义重大。我也很喜欢我们在活动、机场以及其他其他随机场合相遇。请务必过来打个招呼——不要害羞！

特别感谢 Niki Kovacs 对 2023 年版提供的详尽反馈。感谢每一位提供反馈的读者，但 Niki 对这本书非常关注，他的反馈非常慷慨，并且对我缓慢的回复非常有耐心。你可以在这里找到 Niki：

https://www.microlinux.fr

https://blog.microlinux.fr

https://twitter.com/microlinux_eu

# 关于作者

Nigel Poulton (@nigelpouton)

Nigel 是一个技术极客，致力于钻研酷炫的技术，并创作让这些技术更容易学习的书和视频。他是 Docker 和 Kubernetes 畅销书籍的作者，也是这些领域最受欢迎的在线培训视频作者。

Nigel 是一位 Docker 队长，他最近痴迷领域是服务器端 WebAssembly (Wasm)。此前，Nigel 曾在中小型企业担任高级技术职位。

在空余时间，他喜欢听声书和看科幻电影。他希望自己生活在未来，能够探索时空、宇宙和其他令人大脑爆炸的现象。他热爱学习、汽车和足球。他与出色的妻子和三个孩子住在英国。

- X: @nigelpouton
- LinkedIn: Nigel Poulton
- Mastodon: @nigelpouton@hachyderm.io
- 网站: nigelpouton.com
- 邮箱: ddd@nigelpoulton.com

# 目录

1. 0: 关于这本书
2. 第一部分：宏观概念
   1. 1: 容器
3. 第二部分：技术细节
   2. 2: Docker
   3. 3: 获取 Docker
   4. 4: 整体视图
   5. 5: Docker
   6. 6: 镜像操作
   7. 7: 容器操作
   8. 8: 应用程序容器化
   9. 9: Docker Compose
   10. 10: Swarm
   11. 11: 使用 Stacks 部署应用
12. 12: Docker 与 WebAssembly
13. Docker 网络
14. Docker Overlay 网络
15. 卷与持久化数据
16. Docker 安全

