
2. ImageMagick 没有一个非常活跃更新的 PECL 扩展，因此使用 C 语言库不可行——我们必须使用 `exec()` 来 fork 一个新进程并在命令行中执行它。调用 `exec()` 是一个非常缓慢的操作，在 EC2（或任何基于 Xen 的虚拟化环境）上，仅 `fork()` 这一步就可能需要 1 到 2 秒！不仅它很慢，还可能成为 DOS 攻击你服务器的向量。

3. 在制作多个图片版本时，最好使用已有的最小尺寸图片，而不是多次对原始图片进行缩放。与其每次都处理 10 MB、4096×2048 像素的原始图片来生成 150×150 的缩略图，不如先生成 600×400 的中间图片，再从中创建 150×150 的缩略图，这样要快得多。

#### 这不全是代码——通过栈追踪文件上传

修复前面提到的三个问题肯定会提升图片处理性能，但 LHNMPRR 栈中还存在一个不太明显的问题。

假设用户上传了一个 10 MB 的图片，如果按照本书描述的设计方式，它在栈中流转的过程如下：

##### 拆解文件上传

![Moving a 10MB image through the LNHMPRR stack](images/diag.png)

在 LNHMPRR 栈中移动 10 MB 图片的过程

1. 用户通过浏览器或移动端发送 HTTP POST，上传文件（**+10 MB 网络带宽**）。HAProxy 负载均衡器立即接收该文件并将其流式传输到一台 nginx 应用服务器（**+10 MB 网络带宽**）。HAProxy 不会在内存或磁盘中缓冲任何数据，而是直接通过。

2. Nginx 开始从 HAProxy 接收文件并将其缓冲到内存中。取决于 `client_body_buffer_size` 的大小（默认 8 KB），Nginx 会在数据量超过该阈值时转写到磁盘，停止在内存中缓冲，直到整个文件传输完毕。（**+10 MB 磁盘写入 I/O**）

3. 文件上传完全从 HAProxy 传输到 Nginx 后，Nginx 开始读取文件（**+10 MB 磁盘读取 I/O**），并通过 FastCGI 将其传递给 PHP‑FPM（**+10 MB 本地网络带宽**）。由于 PHP‑FPM 本地运行且（希望）使用 Unix Socket，这一步很快完成。

4. PHP‑FPM 发现文件上传后，会把它再次写入磁盘（**+10 MB 磁盘写入 I/O**）。该 PHP‑FPM 工作进程会一直处于“忙碌”状态，PHP 代码在整个文件接收完毕之前不会开始执行。

5. 文件最终进入 PHP，代码开始运行，ImageMagick 进行缩放，读取文件进入内存两次进行处理。（**+20 MB 磁盘读取 I/O，+20 MB 内存**）。

结果是，虽然原始文件只有 10 MB，实际消耗的资源高达 50 MB 磁盘 I/O、30 MB 网络带宽和 20 MB 内存——这太浪费了！如果是视频文件，情况会更糟。

| 资源 | 数量 |
| --- | --- |
| 网络带宽 | 30 MB |
| 磁盘 I/O | 50 MB |
| 内存 | 20 MB |

这套低效流程只是在不同系统之间不断搬运相同的数据。我们可以通过避免磁盘 I/O、尽可能保持数据在内存中来进行优化。

文件在内存之间传递的两个关键点是：一是 Nginx 的缓冲过程，二是 PHP 接收文件时的读取。我们分别对这两点进行优化。

**在 Nginx 侧**，我们可以将 `client_body_buffer_size` 调整为比默认的 8 KB 大得多的值，这样更多的数据会保持在内存中，减少写入磁盘的次数。

另一种做法是保持 `client_body_buffer_size` 不变，并在系统中配置 `tmpfs`（见第 5 章）。配置 `tmpfs` 后，可将 `client_body_temp_path` 改为 `/tmp` 目录，这样在保持 Nginx 内存占用低的同时，可省去磁盘 I/O 开销。

**在 PHP 侧**，只需修改 `php.ini`，将 `upload_tmp_dir` 改为 `/tmp` 目录。这样文件在从 Nginx 传递到 PHP 时会直接写回内存，避免了多次在磁盘之间来回搬运，虽然仍不是最理想的做法，但比三次磁盘写入要好得多。

![information](images/leanpub_information.png) || 与 HAProxy 不同，使用 Nginx（配合 HTTP Proxy 模块或 FastCGI）时，整个客户端请求会在 Nginx 中缓冲，不会实时流传；这可以防止 [Slowloris 攻击](http://en.wikipedia.org/wiki/Slowloris)，但会破坏 PHP 的文件上传进度条。Nginx 提供了 [Upload Progress Module](http://wiki.nginx.org/HttpUploadProgressModule) 来实现上传进度显示。

| --- | --- |
| ![warning](images/leanpub_warning.png) || 我在 Ubuntu 12.04 上遇到安装 `nginx-extras` 的问题（因 `perlapi` 错误），但在 Debian Squeeze 上可以顺利安装。如果你使用 Ubuntu，可能需要从源码编译 Nginx 以获得 HTTP Upload 模块。 |

| --- | --- |

在此之前，请确保该模块已配置为拦截文件上传。打开 `my_app.conf`（第 5 章），在其中添加如下 `location` 块：

```
 1 > vi /etc/nginx/sites-available/my_app.conf
 2 
 3 location /upload {
 4 	upload_pass /index.php;
 5 	upload_store /tmp/nginx/upload 1;
 6 	upload_set_form_field $upload_field_name.name "$upload_file_name";
 7 	upload_set_form_field $upload_field_name.content_type "$upload_content_type";
 8 	upload_set_form_field $upload_field_name.path "$upload_tmp_path";
 9 	
10 	# 如果 PHP 返回以下任意错误，删除文件
11 	upload_cleanup 400 404 499 500-505;
12 }
```

配置完成后，重新加载 Nginx 并创建所需的临时目录：

```
1 > service nginx reload
2 > mkdir -p /tmp/nginx/upload/{1,2,3,4,5,6,7,8,9,0}
```

最后，代码只需将 `$_FILES["upload"]["tmp_file"]` 替换为 `$_POST["file_path"]` 即可。 

