
我喜欢使用 `ini_set` 来设置这类 per-app 的值，而不是在 `php.ini` 中定义，但如果你想，也可以把它们放在 `php.ini` 中。

注意 `session.save_path` 可以包含多个服务器、端口号和权重。这使你能够在多个服务器之间分布会话存储，以实现故障转移和扩展。

其余的值都很直观，我快速说明一下。

* `memcached.sess_consistent_hash`: 开启使用 libketama 的 consistent hashing。在有多个 memcache 服务器时是必须的。
* `memcached.sess_binary`: 使用二进制协议来建立会话连接。
* `memcached.sess_prefix`: 为这些会话键设置一个唯一的前缀。如果多个 PHP 应用共享同一个 Memcached 池，这是必要的，否则会出现会话冲突。
* `memcached.sess_remove_failed`: 当 Memcached 服务器变得不可用时，自动将其从池中移除。
* `memcached.sess_number_of_replicas`: PECL Memcached 扩展的一个酷功能是可以将会话数据复制到多个 memcached 服务器，这样即使一个服务器死亡，数据也不会丢失。设置为你想要的复制品数量。
* `memcached.sess_connect_timeout`: 在服务器标记为不可用并跳过之前的连接超时时间。默认是 1000（1 秒），这太高了。在本地以太网上，连接时间应该不超过几毫秒。将其设置为 50ms，给自己留足活力，同时不会因为服务器宕机而拖慢你的应用。

总之，设置会话处理器为 `memcached` 后，你可以像往常一样使用 PHP 会话。

```
 1 <?php
 2 session_start();
 3 $_SESSION["foo"] = "bar";
```

### 通过 Telnet 调试 Memcached

即使你使用二进制协议从 PHP 访问 Memcached，也可以使用 ASCII 协议通过 Telnet 进行测试！这让你很容易通过 Telnet 来调试 Memcached。

```
 1 telnet 127.0.0.1 11211
 2 >
```

从这里，你可以运行任何命令，如 `GET`、`SET`、`STATS` 和 `FLUSH`。

| ![warning](img/leanpub_warning.png) || 如果你不清楚 `flush` 的作用，请小心！它会在没有警告或确认的情况下清空整个缓存。你已被警告。 |

| --- | --- |

最有用的调试命令是 `STATS`。它会给你提供大量有用信息，如已使用的连接数、项数、命中/不命中比率等。

```
 1 telnet 127.0.0.1 11211
 2 > STATS
 3 STAT pid 4061
 4 STAT uptime 9
 5 STAT time 1390339143
 6 STAT version 1.4.14
 7 STAT pointer_size 64
 8 STAT rusage_user 0.000000
 9 STAT rusage_system 0.004994
10 STAT curr_connections 5
11 STAT total_connections 6
12 STAT connection_structures 6
13 STAT reserved_fds 20
14 ....
15 STAT threads 4
16 STAT conn_yields 0
17 STAT hash_power_level 16
18 STAT hash_bytes 524288
19 STAT hash_is_expanding 0
20 STAT expired_unfetched 0
21 STAT evicted_unfetched 0
22 STAT bytes 0
23 STAT curr_items 0
24 STAT total_items 0
25 STAT evictions 0
26 STAT reclaimed 0
27 END
```

你也可以通过命令行轻松地获取和设置值，以便调试。

```
 1 telnet 127.0.0.1 11211
 2 > set foo 0 100 4
 3 > data
 4 < STORED
```

这里是一个快速的 ASCII 协议简介。`set` 是命令，`foo` 是键名，`0` 是一个任意的 16 位无符号整数标记，Memcache 允许我们设置（它是 PHP 标记键为压缩的方式，以便稍后解压缩值，例如），`4` 是该键对应的值的字节数。最后，`data` 是我们想要为键 `foo` 存储的值。

获取项也很简单。

```
 1 telnet 127.0.0.1 11211
 2 > get foo
 3 < VALUE foo 0 4
```

和 `set` 命令类似，我们只需传入键名到 `get`，它会返回键的值、标记以及数据的字节大小。轻松。

### 我的 Memcached 配置

如果没有一些真实案例，案例研究就不完整。以下是我们当前 Memcached 服务器配置的方式。

#### 硬件

* 双 Xeon 2620（12 个 2.0GHz 核心）
* 128GB 内存
* 1Gbps 以太网

我们有若干这些服务器—— 因为 Memcached 是多线程的，而且我们需要大量的内存来缓存大量数据。

#### 为什么要单独运行 Memcached 服务器？

一个常见的误解是，你可以在任何有空闲内存的地方运行一个 Memcached 守护进程。让我告诉你，这并不总是个好主意——我以前也这么做过。我曾在所有应用服务器上运行 memcached，之后经历了很多麻烦，最终才转到专用的 Memcached 服务器。

我的动机是利用所有可用的资源。我注意到应用服务器有相当多的空闲内存，而 25 台左右的服务器加起来有额外的 250GB 内存可以用于 memcached。这真是太棒了！

但这导致了问题。而且是最糟糕的那种问题，它们很隐蔽，几乎花了我一年时间才找到根源。

假设有 5 台服务器，IP 地址分别为 192.168.0.11 到 192.168.0.15。这些服务器同时运行 Memcache 和 PHP-FPM，提供 web 请求。我们将 memcache 负载在所有 5 台服务器之间进行分片，如下：

```
 1 <?php
 2 $m = new Memcached;
 3 $m->setOption(Memcached::OPT_LIBKETAMA_COMPATIBLE, true);
 4 $m->setOption(Memcached::OPT_CONNECT_TIMEOUT, 100);
 5 
 6 $m->addServers(
 7   array(
 8     array('192.168.0.11', 11211, 20),
 9     array('192.168.0.12', 11211, 20),
10     array('192.168.0.13', 11211, 20),
11     array('192.168.0.14', 11211, 20),
12     array('192.168.0.15', 11211, 20),
13       )
14 );
```

一切都很好，超时设置正确，分片运行顺利

## 推荐选项

以下是我推荐用于最佳性能和未来扩展选项（例如添加和移除服务器）的所有 PHP Memcached 客户端选项。

```
 1 <?php
 2 // 使用持久连接
 3 $m = new Memcached("pool");
 4 
 5 if (empty($m->getServerList())) {
 6   // 将超时时间设置为 50ms
 7   $m->setOption(Memcached::OPT_CONNECT_TIMEOUT, 50);
 8   $m->setOption(Memcached::OPT_RETRY_TIMEOUT,   50);
 9   $m->setOption(Memcached::OPT_SEND_TIMEOUT,    50);
10   $m->setOption(Memcached::OPT_RECV_TIMEOUT,    50);
11   $m->setOption(Memcached::OPT_POLL_TIMEOUT,    50);
 12 
13   // 开启一致哈希
14   $m->setOption(Memcached::OPT_LIBKETAMA_COMPATIBLE, true);
15 
16   // 开启压缩
17   $m->setOption(Memcached::OPT_COMPRESSION, true);
18 
19   // 开启二进制协议和 igbinary 序列化
20   $m->setOption(Memcached::OPT_BINARY_PROTOCOL, true);
21   $m->setOption(Memcached::OPT_SERIALIZER, Memcached::SERIALIZER_IGBINARY);
22   
23   $m->addServers(array(
24     array("192.168.0.1"),
25     array("192.168.0.2")
26   ));
27 }
```

### 进一步阅读和工具

#### twmemproxy

Twitter 开源工具 `twmemproxy` 作为 memcached 的代理服务器。它可以自动分片数据、管理持久连接、提供统计信息，并在你有大量 web 工作进程时降低后端 memcached 守护进程的连接数。

[Link to GitHub](https://github.com/twitter/twemproxy)

#### peep

`peep` 是一个工具，用于将 live memcached 服务器的内存内容导出以查看它正在存储的值。如果你想确切了解 memcached 的使用情况，这将很有用。

[Link to GitHub](https://github.com/evan/peep)

#### PHP igbinary / compression / memcached benchmarks

基准测试展示了不同组合的序列化、压缩和 memcached 扩展的效果（提示：igbinary + 二进制协议 + 压缩 + memcached 扩展胜出）。

[Link to GitHub](https://github.com/carlosbuenosvinos/memcache-memcached-benchmarks)

#### twemperf

Twitter 开源工具 `twemperf` 用于基准测试 memcached 服务器性能。

[Link to GitHub](https://github.com/twitter/twemperf)

## 案例研究：HTTP 缓存和 Nginx Fastcgi 缓存

整本书大部分内容都致力于扩展我们的后端服务——通过提升服务器性能、数据库缓存以及尽快将结果返回客户端来加快前端。通常这是一个好的策略，但我们完全跳过了另一种缓存方式：HTTP 缓存。如果我们能让客户端（浏览器或 API 客户端）缓存我们的输出，直接跳过服务器请求，那将是最棒的。

HTTP 缓存提供了定义未来何时让客户端检查新版本的机制。

| ![information](img/leanpub_information.png) || 在下面的示例中，`>` 表示 **客户端请求** 的开始，而 `<` 表示 **服务器响应** 的开始。 |

| --- | --- |

在最简单的版本中，HTTP 缓存通过返回 `Expires` 头来告知浏览器该响应在指定时间戳前有效。

```
 1 > GET /some_page.html
 2 
 3 < HTTP/1.1 200 OK
 4 Expires: Thu, 1 Jun 2015 01:00:00 GMT
 5 Cache-Control: max-age=29557199
```

| ![question](img/leanpub_question.png) || 等等，`Cache-Control` 是什么？它是更新的头。使用 `Expires` 和 `Cache-Control` 与 `max-age` 一起即可。它们在功能上本质相同，能覆盖所有浏览器。`Cache-Control: max-age` 会在更新的浏览器中覆盖 `Expires`。把它们当作同义词处理。 |

| --- | --- |

这对于静态资源（图片、样式表等）非常理想，因为我们可以预知其长期有效期。但有时我们并不知道内容何时过期——例如新闻网站的首页会频繁更新，我们无法预测何时会有新故事。猜测 `Expires` 的时间戳会导致用户缓存了首页可能错过突发新闻。我们需要更可靠的方案。

为了实现更复杂的缓存，我们使用 `ETag` 头：

1. 在第一次 `GET` 请求时，服务器为 `ETag` 生成一个唯一字符串。在新闻首页示例中，可以是 `md5($latest_article->created_at)` 之类的简单值。
2. 在后续请求时，浏览器会先发送 `HEAD` 请求，并在 HTTP 头中加入 `If-None-Match: {$ETag}`。服务器取出该值，与 `md5($latest_article->created_at)` 比较，若相同则返回 HTTP 状态 `304 Not Modified`，不返回任何体。这指示浏览器使用已缓存的页面，从而 **跳过完整页面生成**（返回空体的 `200 OK` 会让浏览器重新下载）。

示例如下：

```
 1 # 发起第一次（未缓存）的 HTTP 请求
 2 > GET /some_page.html
 3 
 4 < HTTP/1.1 200 OK
 5   ETag: "098f6bcd4621d373cade4e832627b4f6"
 6   Cache-Control: public, max-age=86400
 7 
 8 # 以后某次访问页面时，浏览器会先检查是否有新版本
10 > HEAD /some_page.html
11   If-None-Match: "098f6bcd4621d373cade4e832627b4f6"
12 
13 < HTTP/1.1 304 Not Modified
```

顺便提醒，`Cache-Control` 头用于添加更多缓存指令。`public` 表示内容可缓存（可被中间节点缓存），`private` 则表示内容为私有（不可缓存）。例如，你可能不希望缓存包含私人或个人化内容的页面（如 Twitter 的 `/timeline` 或 Facebook 的 `/account`），这时会将其设为 `private`。`max-age` 部分告诉浏览器在多少秒后失效并重新请求。

### 缓存静态资源

对于简单文件（图片、样式表、字体），可以让 Nginx 自动处理缓存头，只需在服务器配置中加入一个 `location` 块。

```
 1 location ~* \.(js|css|png|jpg|jpeg|gif|ico)$ {
 2   expires max;
 3 }
```

这很容易。但当你修改了这些资源，它们已在浏览器和外部被缓存，如何让浏览器下载最新版本？

浏览器根据完整 URL（包括查询字符串）缓存资源。只需在资源的查询字符串末尾添加“缓存失效”参数（cache buster）即可强制浏览器进行冷加载。在部署时递增版本号是最简单的做法（许多框架，如 Rails，会自动完成）。

最简方案例如 `<link rel="stylesheet" type="text/css" href="main.css?v=5">`，每次更新样式表并想立即让浏览器刷新缓存时，只需修改 `?v=5`。

好了，我们已经掌握了静态资源缓存，接下来该如何在 PHP 控制器中处理缓存呢？下面是一个 HTTP 缓存的伪代码示例。

```
<?php

class UsersController {

    public function show($id) {

        $user = $memcache->get("user:{$id}");

        $type = $_SERVER["HTTP_METHOD"];

        if ($type == "HEAD") {

            $theirs = trim($_SERVER["HTTP_IF_NONE_MATCH"], '"');

            $mine = md5($user["updated_at"]);

            if ($theirs == $mine) {

                return header("Status: 304 Not Modified");

            } else {

                return header("Status: 200 Ok");

            }

        }

        // ... Do normal action stuff

        $user->expensiveDatabaseCall();

        $view->render("users/show");

    }

}
```
