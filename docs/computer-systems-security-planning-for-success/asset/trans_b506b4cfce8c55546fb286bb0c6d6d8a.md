

要登录，客户端会联系 AS，AS 从运行在 KDC 上的 TGS 获取 TGT 并将其提供给客户端。客户端获取其想要使用的服务的 SPN，并将其连同 TGT 一起发送到 TGS。假设客户端有权访问该服务，TGS 会向客户端颁发票据和会话。然后使用该票据连接到服务。

### 7.3.11. Tokenization

令牌化可作为访问控制方案的一部分，用于保护敏感信息。如果泄露，价值极高的信息会被替换为涉及交易的各方知晓的随机令牌。在典型场景中，一旦令牌建立，仅在不可信网络上发送令牌。

想象一下，你不希望信用卡号暴露给商家。一种解决方案是使用支付服务，该服务为每笔交易向你发放一个新的信用卡号。该信用卡号仅对单笔交易有效，并会计入你的常规信用卡（支付服务可以访问该卡）。在这种情况下，令牌是一次性信用卡号，敏感信息是你的实际信用卡号。ApplePay 和 GoogleWallet 等支付服务正是如此。

## 7.4. Lab: Linux File Permissions

在本实验中，我们将探索 UNIX 风格的文件权限，确定它们能做什么以及为什么存在局限性。最后，我们将了解 Linux ACL 如何在分配权限方面提供更多灵活性。

我们将在一个原生 Ubuntu 容器中工作，手动安装软件并添加用户。让我们启动容器，安装所需的软件包，并添加一些用户：

```
C:\Users\rxt1077\it230\docs>docker run -it ubuntu bash
root@11ce9e5ee80e:/# apt-get update
<snip>
root@11ce9e5ee80e:/# apt-get install acl
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  acl
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 37.8 kB of archives.
After this operation, 197 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu focal/main amd64 acl amd64 2.2.53-6 [37.8 kB]
Fetched 37.8 kB in 0s (94.1 kB/s)
debconf: delaying package configuration, since apt-utils is not installed
Selecting previously unselected package acl.
(Reading database ... 4127 files and directories currently installed.)
Preparing to unpack .../acl_2.2.53-6_amd64.deb ...
Unpacking acl (2.2.53-6) ...
Setting up acl (2.2.53-6) ...
root@11ce9e5ee80e:/# useradd alice
root@11ce9e5ee80e:/# useradd bob
root@11ce9e5ee80e:/# useradd carol
root@11ce9e5ee80e:/# useradd dave
```

传统 UNIX 文件权限支持文件的用户和组所有权。可以为用户、组或其他用户设置文件的读、写和执行权限。可以使用 `ls -l` 命令查看文件的权限。让我们为 Alice、Bob 和 Carol 创建主目录，并查看默认权限：

```
root@11ce9e5ee80e:/# cd home
root@11ce9e5ee80e:/home# mkdir alice bob carol
root@11ce9e5ee80e:/home# ls -l
total 12
drwxr-xr-x 2 root root 4096 Oct 28 01:28 alice
drwxr-xr-x 2 root root 4096 Oct 28 01:28 bob
drwxr-xr-x 2 root root 4096 Oct 28 01:28 carol
```

文本 `drwxr-xr-x` 告诉我们这些文件是目录，所有者具有读/写/执行权限，组具有读/执行权限，其他用户具有读/执行权限。需要注意的是，查看目录内容需要执行权限。

文件所有者和组使用 `chown` 命令设置，格式为 `chown <user>.<group> <filename>`。让我们尝试使用此命令将 alice、bob 和 carol 的主目录设为私有：

```
root@11ce9e5ee80e:/home# chown alice.alice alice
root@11ce9e5ee80e:/home# chown bob.bob bob
root@11ce9e5ee80e:/home# chown carol.carol carol
root@11ce9e5ee80e:/home# ls -l
total 12
drwxr-xr-x 2 alice alice 4096 Oct 28 01:28 alice
drwxr-xr-x 2 bob   bob   4096 Oct 28 01:28 bob
drwxr-xr-x 2 carol carol 4096 Oct 28 01:28 carol
```

当使用 `useradd` 命令将用户添加到 UNIX 系统时，会创建一个同名组。这允许我们将一个组传递给 `chown`，只有该用户可以访问。虽然这是一个好的开始，但其他用户仍然有能力读取和执行这些目录，这意味着 `任何人` 都可以查看内容。为了证明这一点，让我们假设 dave 的角色，并尝试对每个目录执行 `ls`：

```
root@11ce9e5ee80e:/home# su dave ①
$ ls alice
$ ls bob
$ ls carol
$ exit
```

1. `①` `su` 允许我们假设任何人的角色，通常用于假设 `超级用户` 的角色

`ls` 命令成功了，即使没有文件可查看。如果我们无法查看内容，将会收到权限被拒绝错误。`chmod` 命令用于修改用户 (`u`)、组 (`g`)、其他用户 (`o`) 或所有用户 (`a`) 的文件权限。`chmod` 可以用 `-` 移除权限，用 `+` 添加权限，或用 `=` 设置权限（移除其他用户）。让我们使用 `chmod` 将这些主目录实际设为私有：

```
root@11ce9e5ee80e:/home# chmod u=rwx,g=,o= alice
root@11ce9e5ee80e:/home# chmod u=rwx,g=,o= bob
root@11ce9e5ee80e:/home# chmod u=rwx,g=,o= carol
root@11ce9e5ee80e:/home# ls -l
total 12
drwx------ 2 alice alice 4096 Oct 28 01:28 alice
drwx------ 2 bob   bob   4096 Oct 28 01:28 bob
drwx------ 2 carol carol 4096 Oct 28 01:28 carol
```

情况好多了，但让我们测试一下，看看 Dave 是否可以查看任何目录：

```
root@11ce9e5ee80e:/home# su dave
$ ls alice
ls: cannot open directory 'alice': Permission denied
$ ls bob
ls: cannot open directory 'bob': Permission denied
$ ls carol
ls: cannot open directory 'carol': Permission denied
$ exit
```

最后，让我们确保 Alice 可以查看她主目录的内容：

```
root@11ce9e5ee80e:/home# su alice
$ ls alice
$ exit
```

看起来不错！

不幸的是，传统 UNIX 文件权限通常无法提供现代系统所需的细粒度。例如，假设我们希望 Web 服务器能够查看 Alice、Bob 和 Carol 主目录的内容。通常这样做是为了允许用户在主目录中放置 `public_html` 目录并设置个人 Web 空间。我们可以通过使他们的主目录对其他用户可见来实现这一点，但这样我们又回到了最初的问题。我们也可以通过将他们主目录的组所有权更改为 Web 服务器所属的组来实现这一点，但这样会将主目录开放给该组中的任何其他用户或服务。

解决这个问题的方法是使用 Linux ACL，它允许你精细调整权限。使用 `setfacl` 和 `getfacl` 两个命令来调整 Linux ACL。例如，让我们添加一个 http 用户，使用 `setfacl` 命令明确授予 http 用户对所有三个目录的读取和执行权限，列出新权限，并列出新 ACL：

```
root@11ce9e5ee80e:/home# useradd http
root@11ce9e5ee80e:/home# setfacl -m u:http:rx alice bob carol
root@11ce9e5ee80e:/home# ls -l
total 12
drwxr-x---+ 2 alice alice 4096 Oct 28 01:28 alice ①
drwxr-x---+ 2 bob   bob   4096 Oct 28 01:28 bob
drwxr-x---+ 2 carol carol 4096 Oct 28 01:28 carol
root@11ce9e5ee80e:/home# getfacl alice bob carol
# file: alice
# owner: alice
# group: alice
user::rwx
user:http:r-x
group::---
mask::r-x
other::---

# file: bob
# owner: bob
# group: bob
user::rwx
user:http:r-x
group::---
mask::r-x
other::---

# file: carol
# owner: carol
# group: carol
user::rwx
user:http:r-x
group::---
mask::r-x
other::---
```

1. `①` 注意表示有额外权限的 `+` 符号

完成后，可以键入 exit 退出 bash 并停止容器。

## 7.5. Review Questions

