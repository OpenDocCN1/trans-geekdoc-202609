
![](img/05----chart_1.png)![](img/05----chart_2.png)![](img/05----chart_3.png)

### Nginx 与 PHP-FPM

正如第 2 章所讨论，我们将用 `nginx + PHP-FPM` 替代传统的 `Apache + mod_php` 组合。虽然可以保留 Apache 并通过 HAProxy 水平扩展，但 `nginx + PHP-FPM` 的组合更为优雅。Trust me，摒弃 Apache，改用 nginx。

我们在 2010 年将 Twitpic 迁移到此架构，当时我对 nginx 并不熟悉，担心配置会很复杂。结果发现，nginx 的配置文件简洁易读，管理起来比 Apache 更轻松。而且 nginx 官方 Wiki（[`wiki.nginx.org/Main`](http://wiki.nginx.org/Main)）提供了完整的每项配置选项文档。

同样，`PHP-FPM` 也是可靠的软件，和使用 `mod_php` 一样可靠。PHP 5.3 之前它是以补丁形式开发，由与 nginx 同一团队维护，而自 PHP 5.3 起已被整合进 PHP 官方发行版，得到整个 PHP 社区的全力支持，经过充分测试，完全可靠。

假设您的 PHP 应用位于 `/u/apps/my_app`，入口脚本为 `/u/apps/my_app/www/index.php`。大多数框架（如 Zend、Kohana、Cake）都兼容此配置。

下面是我们的部署步骤：

```
1 > apt-get install nginx

2 > vi /etc/nginx/nginx.conf

3

4 user www-data;

5 worker_processes 4;

6 pid /var/run/nginx.pid;

7

8 events {

9   worker_connections 768;

10   multi_accept on;

11 }

12

13 http {

14

15   sendfile on;

16   tcp_nopush on;

17   keepalive_timeout 65;

18   server_tokens off;

19

20   include /etc/nginx/mime.types;

21   default_type application/octet-stream;

22

23   access_log /var/log/nginx/access.log;

24   error_log /var/log/nginx/error.log;

25

26   gzip on;

27   gzip_disable "MSIE [1-6]\\.";

28

29   include /etc/nginx/conf.d/*.conf;

30   include /etc/nginx/sites-enabled/*;

31 }

32
33 > vi /etc/nginx/sites-available/my_app.conf

34 upstream backend {

35   server unix:/u/apps/my_app/tmp/php.sock;

36 }

37

38 server {

39

40   listen 80 default;

41   root /u/apps/my_app/www;

42   index index.php;

43

44   access_log /u/apps/my_app/logs/access.log;

45   error_log /u/apps/my_app/logs/error.log;

46

47   location / {

48     try_files $uri $uri/ /index.php;

49   }

50

51   # This location block matches anything ending in .php and sends it to

52   # our PHP-FPM socket, defined in the upstream block above.

53   location ~ \\.php$ {

54     try_files $uri =404;

55     fastcgi_pass backend;

56     fastcgi_index index.php;

57     fastcgi_param SCRIPT_FILENAME /u/apps/my_app/www$fastcgi_script_name;

58     include fastcgi_params;

59   }

60

61   # This location block is used to view PHP-FPM stats

62   location ~ ^/(php_status|php_ping)$ {

63     fastcgi_pass backend;

64     fastcgi_param SCRIPT_FILENAME $fastcgi_script_name;

65     include fastcgi_params;

66     allow 127.0.0.1;

67     deny all;

68   }

69

70   # This location block is used to view nginx stats

71   location /nginx_status {

72     stub_status on;

73     access_log off;

74     allow 127.0.0.1;

75     deny all;

76   }

77 }
```

```
1 > mkdir -p  /u/apps/my_app/{logs,tmp,www}
2 > ln -s /etc/nginx/sites-available/my_app.conf \
3         /etc/nginx/sites-enabled/my_app.conf
4 > service nginx start
```

Alright. Nginx is up and running now, but nginx doesn’t know how to run PHP. Unlike Apache with mod_php, PHP-FPM runs outside of the webserver in it’s own process- nginx just forwards requests to it using FastCGI. We need to install PHP-FPM and configure it.

```
 1 > apt-get install php5-fpm

 2

 3 > vi /etc/php5/fpm/pool.d/my_app.conf

 4

 5 [my_app]

 6 listen = /u/apps/my_app/tmp/php.sock

 7 user = www-data

 8 group = www-data

 9 pm = dynamic

10 pm.max_children = 100

11 pm.start_servers = 10

12 pm.min_spare_servers = 5

13 pm.max_spare_servers = 15

14 pm.max_requests = 1000

15 pm.status_path = /php_status

16

17 request_terminate_timeout = 0

18 request_slowlog_timeout = 0
```

`pm.max_requests` 是单个子进程在被杀死并重新生成之前可以服务的请求数量。它用于防止内存泄漏，因为 PHP 的垃圾回收器并不设计用于长时间运行。PHP 5.3 为内存管理带来了一些改进，因此可以将其设置得相当高。我建议将其至少设为 1000，具体取决于你的代码以及是否使用 PHP 扩展，因为不同扩展的泄漏情况各不相同。

### 选择适合你应用服务器的硬件

**快速 CPU，大量内存**

预计每个 PHP-FPM 进程会使用多达 20 MB 的内存，假设 `pm.max_children` 设为 100，你至少需要 2 GB 的内存来支撑服务器。

相反，Nginx 记忆消耗极低——即使是负载重的应用服务器，Nginx 的总内存占用也仅 60-80 MB。

你需要最快的 CPU 以及尽可能多的核心。虽然 PHP 是单线程的，只要 PHP-FPM 进程的数量多于 CPU 核心数，就能充分利用每个核心。

截至撰写时，Intel Xeon SandyBridge 26xx 系列是性价比最高的选择。它们支持双 CPU 配置，每个 CPU 最多 8 核，启用 Hyper-Threading 后可提供 32 个可用核心供应用服务器使用。

### 使用 PHP 字节码缓存

PHP 是解释型语言。每次运行 PHP 应用时，解释器需要读取源码、将其转换为内部字节码程序，然后执行这些字节码。可以把字节码程序看作解释器能更好理解的中间语言——实际上是一个虚拟机。

将 PHP 源码翻译成字节码需要非平凡的开销，通过缓存这种 PHP → 字节码的转换结果并重复使用，可以大幅节省开销。那么我们该如何实现呢？使用字节码缓存扩展。如果你目前还没有使用，只需安装一个即可实现 200-300 % 的 CPU 使用率下降。这真是易如反掌！

自 PHP 5.5 起，Zend OpCache 已随 PHP 捆绑。要启用它，只需在 `php.ini` 中加入 `opcache.enable=1`。超级简单。唯一的缺点是，APC 的用户空间 memcache 组件不再包含在 Zend OpCache 中。如果你依赖这个共享缓存，可以安装类似 [APCu](http://pecl.php.net/package/APCu) 的扩展，它在 PHP 5.5 中恢复了 APC 的用户空间缓存功能。我在《CakePHP 缓存文件案例研究》中详细描述了从 APC 迁移到 Zend OpCache 所遇到的心酸史。

如果你使用的是 PHP 5.4 或更低版本，还有其他字节码缓存方案可供选择，下面会逐一说明。

有没有使用字节码缓存的缺点？在大多数配置中，答案是**没有**。唯一的*注意点*是：如果你使用了 PHP 编码/混淆器（如 [ionCube](http://www.ioncube.com/) 或 [Zend Guard](http://www.zend.com/en/products/guard/）），则无法使用字节码缓存。这只会影响少数运行闭源、授权 PHP 代码的用户。

#### 调优 Zend OpCache（仅 PHP 5.5）

常见痛点：“我想使用 Zend Optimizer，但完全不知道怎么设置。”

你有没有发现，花几小时阅读文档却仍然对设置一无所知？
