
-   我们以压缩形式存储数据，在压缩 MySQL 备份时实现了超过 100% 的存储空间节省。你可以使用 `gzip` 获得最大的存储空间节省，但它非常慢。相反，对于大型备份，我建议使用 `lzop`（http://www.lzop.org/）。`lzop` 是一个文件压缩工具，运行速度显著更快，但压缩效率稍低。此外，`lzop` 支持并行压缩，从而进一步提升速度。

#### 通知

最后，我想让备份系统非常显眼。由于我们使用 [Campfire](http://campfirenow.com/) 进行团队沟通，我能够通过 API 在备份脚本运行时每次都在 Campfire 中发送消息。每天早上醒来，看到“MySQL Backup Finished”在 Campfire 中发布，真是令人安心。

这很简单，只需在备份脚本中加入类似下面的内容：

```
1 SIZE=`ls -sh $THISBACKUP.tar.gz | cut -f 1 -d " "`
2 curl -i -u $KEY:X -H 'Content-Type: application/json' -d "{\"message\":{\"body\
3 :\"MySQL Backup Finished (size: $SIZE)\"}}" $CAMPFIRE_URL
```

## 案例研究：Async APIs w/ Kestrel 救了我的命

对于网站的扩展来说，后台任务是一个相当新的技术。3 到 4 年前，社交 API 并不常见，将网页请求的部分在后台执行几乎是未闻名的，只有最大的网站才涉及。

Twitpic 依赖 Twitter API 实现许多站点功能。当你上传新图片时，可以选择将其发布到 Twitter 或 Facebook。当你对照片评论时，我们也会将该评论推送到你的 Twitter 流中。

最初，代码是采用笨拙的方式编写的。为什么？我们根本不知道更好的做法。我们是草根、自筹的程序员，在远超想象的规模下工作。你可以想象我们的代码大致像这样：

```
 1 <?php
 2 class Image_Controller extends Controller {
 3 
 4   // 当有人上传新图片时...
 5   public function create() {
 6   	
 7     $image = new Image();
 8     $image->process_image_upload();
 9     $image->save();
10     
11     // 生成要发送到 Twitter 的推文文本...
 12     // 即，“Check out this cool pic. http://twitpic.com/abc123”
13     $tweet = $image->tweet();
14     
15 	 // 通过 API 向 Twitter 发送推文。
16     Twitter::post_tweet($image->user, $tweet);
17   
18   }
19 }
```

从程序角度来看，这很合理。但这是处理第三方 API 时的*错误*做法，无论规模大小都如此。即使你仍然很小，情况也很糟糕。因为即使是最佳情况，PHP 会阻塞等待 I/O，API 请求处理需要 1-2 秒，无可避免。每次用户上传图片时，我们都会额外花费 1 到 2 秒来向 Twitter 发送推文。

你可以说这不算大问题，因为用户正在上传文件，不会注意到几秒的延迟。但对于评论呢？我们想在用户评论时立即发布推文，而这种本应快速的操作因 API 交互而变慢。

而且，这并非针对 Twitter。**所有** HTTP API 都慢。当你通过网络跨国访问 API 时，这本就是常态，会产生延迟。

#### 最坏的情况

别提用户体验了，这种做法还会带来严重问题。你的网站会**依赖**于其他服务。记得 Twitter 曾经每周都会崩溃吗？如果你像我们一样使用 Twitter API，Twitter 的宕机就会直接导致你的网站崩溃！.fail whale 无处不在。

我之前说每个棘手的 API 调用需要 1-2 秒，因为 PHP 会阻塞等待响应。那么，如果 API 请求耗时很长（5 秒以上）会发生什么？PHP 会一直等待响应，无法处理新的 HTTP 请求。当 Twitter 宕机时，这些“阻塞”的 PHP 进程会一直等待响应或超时。

在繁忙的网站上，这会**迅速**耗尽所有可用的 PHP 进程。例如，当每秒上传 100 多张图片并发送到 Twitter 时，若 Twitter 宕机，每秒就会有 100 多个 PHP 进程被阻塞，无法服务任何其他请求。

这会引发连锁反应，最终导致整个网站瘫痪，因为没有可用的（非阻塞）PHP 进程。

当 Twitter 严重宕机时，我们也彻底倒霉。情况很糟糕。

#### 转向 Kestrel 的道路

 fed up with 将我们的可用性依赖于其他公司的可用性，我决定绳之以系，开始研究解决方案。

我的第一个念头是使用数据库（*不要这样做*）。我建了一个表，将推文写入，并启动一个后台进程来发送它们。正如第 8 章讨论的，如果有多个后台工人，除非使用 MySQL 锁定，否则会出现竞争条件。MySQL 锁定虽可行，但它会在队列上产生全局锁，是一个不适合并行和并发的方案。**数据库不是队列**。

因此，我的首次尝试在后台中进行推文发送导致了重复推文和各种失败。我坦白说，我当时并不清楚自己在做什么。

我开始研究其他方案。找到了一些关于 [Starling](https://github.com/starling/starling)（Twitter 的第一个排队守护进程，用 Ruby 编写）的文章。不幸的是，Ruby（或 PHP）并不是构建高并发、高可用排队系统的最佳选择，这引发了大量负面评论。于是，我找到了它的开源后继——Kestrel。

Kestrel 用 Scala 编写，运行在 JVM 上，并使用 memcached 协议，因此无需额外客户端，只需将 Memcached 客户端指向它即可！当时 Resque 还未出现，Kestrel 是最佳（也最简洁）的解决方案。最终，我们迁移到了 Resque，但无论使用哪种队列服务，概念都是一样的。

于是，我设置了 Kestrel，并将 Twitter API 调用推入队列。不再在 web 请求期间执行这些调用，而是将它们移到后台“ eventualy” 处理。

#### 赢

使用 Kestrel 是巨大的胜利，解决了早期的宕机问题。与其在 Twitter 宕机时直接崩溃，我们的网站现在运行 **快速**——我们只会看到 Kestrel 队列中积压大量任务。一旦 Twitter 恢复，所有任务都会被处理！不再有宕机，不再有数据丢失。

这已经是巨大的收获。但也提升了用户体验。记得我之前说，最佳情况下向 Twitter 发送推文需要 1 到 2 秒？这意味着发布新图片或评论需要额外 1-2 秒。有了后台工作者后，新评论**立即**通过，图片上传速度提升了 25%。

## 案例研究：Memcached 的缺失指南

Memcached 很酷。它是早期扩展领域的“坏男孩”之一，也是许多最大网站的核心基础。为什么？它简单、快速且便捷。Memcached 可以轻松安装在几乎所有平台，配置也很简单。

 tempting 考虑市面上各种 Memcached 替代品。我看到一些“现代版本”使用相同协议但实现于 Golang 或 Scala。我建议避免在严肃环境中使用用垃圾回收语言实现的 Memcached 服务器——你不希望你的站点瓶颈因 Memcached 服务器的 **stop-the-world** 垃圾回收而出现。

原生的 C 语言 memcached 仍是绝佳选择——它简单、稳定且可靠。

### 为何选择 Memcached 而非 Redis？

