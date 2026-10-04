

虚拟主机在你想在单台服务器上托管多个域名或子域名时非常有用。在 Caddy 中，每个虚拟主机只需在 Caddyfile 中声明为一个块即可。

下面是如何定义两个虚拟主机的示例：

```
example.com {
    reverse_proxy localhost:8080
}
api.example.com {
    reverse_proxy localhost:5000
}
```

* `example.com` 和 `api.example.com` 是两个不同的虚拟主机。
* 每个域名指向不同的后端服务，例如一个运行在端口 `8080`，另一个运行在端口 `5000`。

你可以根据需要添加任意数量的域名或子域名，Caddy 会自动处理它们。

## 自动 SSL 证书管理

Caddy 的突出特性是其自动 SSL 证书管理。默认情况下，Caddy 会：

* 自动为 Caddyfile 中列出的每个域名或子域名请求并安装 SSL 证书。
* 在证书过期前自动续期 SSL 证书。
* 将所有 HTTP 流量重定向到 HTTPS，确保安全通信。

以下 Caddyfile 配置将自动为 `example.com` 和 `api.example.com` 生成 SSL 证书：

```
example.com {
    reverse_proxy localhost:8080
}
api.example.com {
    reverse_proxy localhost:5000
}
```

无需人工干预 — Caddy 会在幕后处理所有与证书相关的任务。

## 通配符域名

Caddy 还支持通配符证书，如果你想保护域名的所有子域名，这会很有用。例如：

```
*.example.com {
    reverse_proxy localhost:8080
}
```

在这种情况下，Caddy 将为 `*.example.com` 请求通配符证书，并将任何子域名的流量，例如 `api.example.com`、`blog.example.com` 等，转发到指定的后端服务。

## 自定义 SSL 证书

虽然 Caddy 使用 Let’s Encrypt 自动管理 SSL 证书，但它也允许你根据需要指定自定义 SSL 证书。以下是如何提供自定义证书和密钥的方法：

```
example.com {
    reverse_proxy localhost:8080
    tls /path/to/your/cert.pem /path/to/your/key.pem
}
```

在此示例中，`tls` 指令指向 `example.com` 的你自己的证书和密钥文件。

## 管理多个 SSL 证书

如果你的服务器需要处理多个具有不同 SSL 证书的域名，你可以为每个虚拟主机指定其 SSL 证书：

```
example.com {
    reverse_proxy localhost:8080
    tls /path/to/your/cert.pem /path/to/your/key.pem
}
anotherdomain.com {
    reverse_proxy localhost:5000
    tls /path/to/your/another-cert.pem /path/to/your/another-key.pem
}
```

## TLS 配置

Caddy 还允许高级 TLS 配置，例如设置协议、密码套件和互 TLS `mTLS`：

```
example.com {
    reverse_proxy localhost:8080
    tls {
        protocols tls1.2 tls1.3
        ciphers ECDHE-ECDSA-AES128-GCM-SHA256 ECDHE-RSA-AES128-GCM-SHA256
    }
}
```

此配置将协议限制为 TLS 1.2 和 1.3，并指定安全通信中使用的密码。

# 结论

在本章中，我们探讨了 Caddy 和 Nginx 作为 Go 基于 HTTP 服务器的反向代理的强大功能。两者都为管理流量、配置虚拟主机和处理 SSL 证书提供了稳健的解决方案。虽然 Nginx 以其性能和灵活性而广为人知，但 Caddy 因其简洁性而脱颖而出，尤其是在自动 HTTPS 和证书管理方面。了解如何在反向代理后面部署、配置和保护你的 HTTP 服务器，对于在生产环境中构建可扩展、安全且可维护的 Web 应用至关重要。通过正确的设置，你可以确保服务的平稳运行、优化性能和安全通信。

下一章将探讨文件处理，教你如何使用 multipart 表单数据上传和下载文件，并在你的 Go API 中处理文件存储和检索。

# 关键术语

* `Reverse Proxy`: 一个位于后端服务前面的服务器，转发客户端请求，同时提高安全性、性能和负载均衡。
* `Forward Proxy`: 一个位于客户端和互联网之间的代理，将客户端请求转发到外部资源。
* `Load Balancing`: 将客户端请求分发到多个后端服务器的过程，以防止过载并提高可扩展性。
* `SSL Termination`: 反向代理处理 SSL/TLS 加密并将未加密流量转发到后端服务器的过程。
* `Caching`: 将经常访问的内容副本存储在内存或磁盘中以减少负载并提高响应时间。

# 第 10 章

# 高级文件处理和实时通信

## 引言

随着现代 API 的不断发展，高效处理文件和实现实时通信的能力变得至关重要。在本章中，我们将深入探讨 `Advanced File Handling and Real-Time Communication` 技术，帮助你构建功能丰富且响应迅速的 Go API。

我们将首先通过 multipart 表单数据探索 `file upload and download processes`，随后介绍 `secure file storage and retrieval` 的最佳实践，以确保可扩展性和数据完整性。接下来，我们将处理用于管理大型数据集的 `pagination techniques`，以便在你的应用中实现高效的数据交付。

在实时通信方面，本章介绍了 `WebSockets` 及其集成到 REST API 中，使服务器和客户端之间能够进行动态双向通信。你将学习如何实现向连接用户 `broadcasting real-time updates` 的功能，以及处理 `WebSocket authentication and authorization` 以实现安全通信。

本章提供了管理文件的高效工具和技术，同时使你的 API 通过实时交互焕发生机，使其更具响应性和用户友好性。

## 结构

在本章中，我们将涵盖以下主题：

* Uploading and Downloading Files in REST APIs Using Multipart Form Data
* File Storage and Retrieval Best Practices in Go APIs
* Implementing Pagination Techniques for Large Data Sets
* Real-Time Communication Using WebSockets in REST APIs
* Integrating WebSocket Functionality into Go Servers

# 使用 Multipart 表单数据在 REST API 中上传和下载文件

上传和下载文件是现代 REST API 的基本功能。这些功能对于云存储平台、内容管理系统和电子商务网站等应用至关重要，在这些应用中文件处理是核心需求。REST API 依赖 multipart 表单数据格式来促进文件上传和下载，确保在单个 HTTP 请求中高效处理二进制和文本数据。本主题深入探讨 REST API 中使用 multipart 表单数据处理文件的方式，探索其结构、在 Go 中的实现以及最佳实践。

## Multipart 表单数据

Multipart 表单数据是 HTTP 中的一种内容类型，允许在同一请求中传输文件和其他表单字段。它广泛用于文件上传，因为它提供了一种包含文本和二进制数据的方法。Multipart 表单数据将请求体拆分为多个部分，每个部分都有自己的内容类型和 disposition，由边界字符串分隔。这种格式非常适合 REST API，因为它确保文件传输期间的数据完整性。

## 在 REST API 中上传文件

