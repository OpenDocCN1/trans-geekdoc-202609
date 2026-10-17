
# 配置和部署服务到Kubernetes中使用Helm

Helm^([\[60\]](#f_0083.xhtml#FOOTNOTE-60)) 是Kubernetes的包管理器，用于在Kubernetes集群中分发和安装服务。Helm包被称为chart。chart定义了运行服务在Kubernetes集群中所需的所有资源，例如部署、服务、持久化卷声明等。Kubernetes上的chart类似于Debian上的Debian包或macOS上的Homebrew公式。作为服务开发者，你想要构建并共享一个Helm chart以便让其他人更容易运行你的服务。（如果你在dogfooding你自己的服务，你将获得相同的好处。）

A release 是运行一个chart的实例。每次你将chart安装到Kubernetes中，Helm都会创建一个release。在Debian包和Homebrew公式的例子中，releases类似于进程。

最后，repositories是用于共享和从中安装charts的地方；它们类似于Debian的sources和Homebrew的taps。
