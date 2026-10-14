
# 前言

## 本书的设计理念

虽然本书专注于 PHP，但此处描述的技术可应用于任何其他语言或部署，包括但不限于容器发布、Node.js 应用程序、Ruby 等。

我们将主要关注完整的 LEMP（Linux Nginx MySQL PHP）服务器，即所有二进制文件均运行在同一台服务器上。根据您的需求，您可以使用专用的 MySQL 实例，以及一个作为网关的独立 Nginx 实例，您只需修改脚本以匹配您的设置即可。

您可以按任何您喜欢的顺序阅读本书。参考资源均可随时获取，其中部分为开源资源。

所有待执行的 Shell 命令均以前缀 `$` 或 `#` 加一串字符的形式书写，输出将紧随其后，例如：

```
$ echo 'hello world'
hello world
```

## 谁应该阅读本书？

任何软件开发人员或管理员均可阅读本书。本书非常适合自由职业者、初创企业、企业家以及所有从事服务器工作并编写少量代码的人员。

由于本书主要涉及 PHP，您应了解该语言并理解您正在使用的技术栈；无论是 LAMP 还是 LEMP；并对服务器设置、SSH 和终端的使用有少许了解。

## 责任声明

我已竭尽全力确保书中信息的准确性。

然而，本书所含信息不提供任何担保，无论明示或暗示。作者、经销商或分销商均不对因本书中的说明，或因书中所述软件或服务提供商而直接或间接造成的任何损害承担责任。

# 手动服务器设置

## 寻找合适的服务器

有几家提供商（[DigitalOcean](https://www.digitalocean.com/?refcode=9724e049fc4d)、[Linode Cloud](https://www.linode.com/products/standard-linodes/)、[AWS](https://aws.amazon.com/ec2/)、[Vultr](https://www.vultr.com/?ref=7275395) 等）提供极具竞争力的价格，从 [Vultr](https://www.vultr.com/?ref=7275395) 的 10GB SSD、1 vCPU 和 512 MB RAM 每月 2.5 美元，到 [DigitalOcean](https://www.digitalocean.com/?refcode=9724e049fc4d) 的 3,840GB SSD、32 vCPU 和 192GB RAM 每月 960 美元不等。

在我们的案例中，我们将使用 [每月 40 美元的 DigitalOcean Droplet（160GB SSD，4](https://cloud.digitalocean.com/droplets/new?size=s-4vcpu-8gb)
