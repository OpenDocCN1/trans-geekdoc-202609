
# AWS 认证考题集锦

## 118. 哪个 AWS 服务提供分析型数据仓库的预置和工具？

1.  Aurora
2.  ElastiCache
3.  DynamoDB
4.  **Redshift**

## 119. 以下哪项是 AWS 容错的基本原则？

1.  在不同的 VPC 中启动实例。
2.  在不同的区域中启动实例。
3.  **在不同的子网中启动实例。**
4.  在边缘位置启动实例。

## 120. 以下哪些服务使用 AWS 边缘位置？

1.  **CloudFront**
2.  Customer gateway
3.  Storage gateway
4.  Snowball

## 121. 在两个可用区中运行应用程序有什么好处？

1.  比在单个可用区中运行更安全。
2.  比在单个可用区中运行性能更高。
3.  **增加了在单个可用区中运行应用程序的容错能力。**
4.  降低了在单个可用区中运行应用程序的网络延迟。

## 122. 以下哪些 AWS 服务可用于存储文件？（选择两项。）

1.  Amazon Athena
2.  **S3**
3.  MySQL
4.  **EBS**

## 123. 以下哪些 AWS 服务可用于存储大对象？（选择两项。）

1.  Redshift
2.  **S3**
3.  Oracle
4.  EC2

## 124. 如何加快向 S3 传输数据的速度？

1.  使用 Snowball 更快地传输大文件。
2.  **启用 S3 Transfer Acceleration。**
3.  配置 AWS 使用多条网络路径到达您的 S3 存储桶。
4.  配置 AWS 使用互联网网关路由流量到您的 S3 存储桶。

## 125. 哪些用户最能从 S3 Transfer Acceleration 中受益？

1.  地理位置最接近您的 S3 存储桶的用户
2.  **地理位置最远离您的 S3 存储桶的用户**
3.  利用 HTTPS 进行上传的用户
4.  所有用户受益均等。

## 126. 以下哪些是使用 S3 Transfer Acceleration 的充分理由？（选择两项。）

1.  **您有来自世界各地上传到您存储桶的客户。**
2.  您有客户抱怨应用程序的性能。
3.  **您定期跨大陆传输千兆字节的数据。**
4.  您看到上传到 S3 存储桶时出现网络延迟。

## 127. 您可以使用哪些服务来托管网站？（选择两项。）

1.  **EC2**
2.  Elastic Load Balancing
3.  **S3**
4.  Glacier

## 128. 您在 US West 1 区域有一个名为 `newyorkhotdogs` 的存储桶。您已在此存储桶上启用了静态网站托管，并想将其 URL 提供给测试客户。您应该提供哪个 URL？

1.  `http://newyorkhotdogs.s3-website.us-west-1.amazonaws.com`
2.  `https://s3-us-west-1.amazonaws.com/newyorkhotdogs`
3.  **`http://newyorkhotdogs.s3-website-us-west-1.amazonaws.com`**
4.  `http://newyorkhotdogs.s3-website.us-east-1.amazonaws.com`

## 129. 您创建了一个静态网站，并将名为 `home.html` 的 HTML 页面放在 S3 存储桶的根级别。存储桶名为 `californiaroll`，位于 US West 2。您可以通过什么 URL 访问该 HTML 页面？

1.  `http://californiaroll.s3-website.us-west-1.amazonaws.com/home.html`
2.  `http://s3-website-us-west-1.amazonaws.com/californiaroll/home.html`
3.  `http://californiaroll.s3-website-us-west-2.amazonaws.com/public_html/home.html`
4.  **`http://californiaroll.s3-website-us-west-1.amazonaws.com/home.html`**

## 130. 您在 EU West 1 区域创建了一个名为 `phoneboothPhotos` 的 S3 存储桶，其中包含各种图像，名称类似 `image-001.jpg` 和 `image-002.jpg`。您已在此存储桶上启用了网站托管。哪个 URL 可以访问这些照片？

1.  **`http://phoneboothPhotos.s3-website-eu-west-1.amazonaws.com/image-001.jpg`**
2.  `http://phoneboothPhotos.s3-website-eu-west-1.amazonaws.com/phoneboothphotos/image-001.jpg`
3.  `http://phoneboothPhotos.s3-website-eu-west-1.amazonaws.com/public_html/phoneboothPhotos/image-001.jpg`
4.  `http://phoneboothPhotos.s3-website.eu-west-1.amazonaws.com/phoneboothPhotos/image-001.jpg`

## 131. 您拥有自己的自定义域名，并希望在该域名上托管静态网站。您还希望将计算成本降至最低。您将使用以下哪些 AWS 服务在自定义域名上托管您的网站？（选择两项。）

1.  **S3**
2.  EC2
3.  Lambda
4.  **Route 53**

## 132. 您拥有自己的自定义域名，并希望在该域名上托管动态网站。您还希望将计算成本降至最低。您将使用以下哪些 AWS 服务在自定义域名上托管您的网站？（选择两项。）

1.  S3
2.  **EC2**
3.  **Lambda**
4.  **Route 53**

## 133. 以下哪些提供无服务器网站的功能？（选择两项。）

1.  **S3**
2.  EC2
3.  **Lambda**
4.  Route 53

## 134. 以下哪些提供动态网站的功能？（选择两项。）

1.  S3
2.  **EC2**
3.  **Lambda**
4.  Route 53

## 135. 以下哪些是 Elastic Beanstalk 提供的功能？（选择两项。）

1.  **代码部署**
2.  安全性
3.  **容量预置**
4.  成本优化

## 136. 以下哪些不是 Elastic Beanstalk 提供的功能？（选择两项。）

1.  代码部署
2.  **安全加固**
3.  应用程序运行状况监控
4.  **日志检查和备份**

## 137. Elastic Beanstalk 支持以下哪些技术？（选择两项。）

1.  **Docker**
2.  C++
3.  Scala
4.  **Node.js**

## 138. Elastic Beanstalk 支持以下哪种应用程序类型？

1.  Node.js
2.  Java
3.  Python
4.  **以上皆是**

## 139. Elastic Beanstalk 支持以下哪些数据库技术？（选择两项。）

1.  **所有 AWS 支持的 RDS 选项**
2.  **DynamoDB**
3.  运行在 EC2 上的 Oracle
4.  Redshift

## 140. 如何将由 Elastic Beanstalk 管理的应用程序代码从测试环境转换为生产环境？

1.  更新代码库以使用面向生产的 CloudFormation 文件。
2.  在应用程序代码中更新数据库连接字符串。
3.  **在特定环境的 Elastic Beanstalk 配置中，将 Elastic Beanstalk 环境设置为使用您的生产数据库。**
4.  您无法使用 Elastic Beanstalk 部署到生产环境。

## 141. 哪个 AWS 服务允许您在无需预置代码所需的任何底层资源的情况下运行代码？

1.  EC2
2.  ECS
3.  DynamoDB
4.  **Lambda**

## 142. 以下哪些 AWS 服务允许您在无需担心为代码预置特定资源的情况下运行代码？（选择两项。）

1.  **Elastic Beanstalk**
2.  ECS
3.  DynamoDB
4.  **Lambda**

## 143. Lambda 函数在服务器上运行吗？

**是的，Lambda 函数在服务器上运行，但 AWS 负责管理这些服务器的预置、维护和扩展。您无需管理底层基础设施。**
