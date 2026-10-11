
# 第 70 章：事件循环

## 第 70.7 节：使用 Amp 事件循环

[Amp](https://github.com/amphp/amp/tree/v1.x) 利用 Promise（Awaitable 的另一种叫法）和生成器来创建协程。

```php
public function _onTimeout(EvTimer $w) {
    $w->stop();
    $this->close();
}

/**
 * 当套接字变为可写时调用的回调
 */
public function _onWritable(EvIo $w) {
    $this->timeout_watcher->stop();
    $w->stop();
    $in = implode("\r\n", [
        "{$this->method} {$this->resource} HTTP/1.1",
        "Host: {$this->host}",
        'Connection: Close',
    ]) . "\r\n\r\n";
    if (!socket_write($this->socket, $in, strlen($in))) {
        trigger_error("Failed writing $in to socket", E_USER_ERROR);
        return;
    }
    $loop = $this->http_client->getLoop();
    $this->read_watcher = $loop->io($this->socket, Ev::READ, [$this, '_onReadable']);
    // 继续运行循环
    $loop->run();
}

/**
 * 当套接字变为可读时调用的回调
 */
public function _onReadable(EvIo $w) {
    // 在非阻塞模式下 recv() 20 字节
    $ret = socket_recv($this->socket, $out, 20, MSG_DONTWAIT);
    if ($ret) {
        // 仍有数据可读。将读取的块追加到缓冲区。
        $this->buffer .= $out;
    } elseif ($ret === 0) {
        // 全部读取完毕
        printf("\n <<<< \n %s \n >>>>", rtrim($this->buffer));
        fflush(STDOUT);
        $w->stop();
        $this->close();
        return;
    }
    // 捕获 EINPROGRESS、EAGAIN 或 EWOULDBLOCK
    if (in_array(socket_last_error(), static::$e_nonblocking)) {
        return;
    }
    $w->stop();
    $this->close();
}
```

测试

```http
http://my-host.local/test.php
```

假设脚本正在打印 `$_GET` 的转储：

```bash
php http-client.php
```

那么命令的输出将类似于以下内容：

(已裁剪)

注意，在 PHP 5 中，sockets 扩展可能会为 `EINPROGRESS`、`EAGAIN` 和 `EWOULDBLOCK` errno 值记录警告。可以通过以下方式关闭日志：

```php
error_reporting(E_ALL & ~E_WARNING);
```

```php
// 使用 Amp\resolve() 转换为协程
$promise = Amp\resolve(queryStackOverflow(Dns\Record::NS));
list($ns, $type, $ttl) = // 我们只需要一个 NS 结果，而不是全部
    current(yield Amp\timeout($promise, 2000 /* 毫秒 */));
echo "The result of the fastest server to reply to our query was $ns";

} catch (Amp\TimeoutException $e) {
    echo "We've heard no answer for 2 seconds! Bye!";

} catch (Dns\NoRecordException $e) {
    echo "No NS records there? Stupid DNS nameserver!";
});
```

# 第 71 章：如何检测客户端 IP 地址

## 第 71.1 节：HTTP_X_FORWARDED_FOR 的正确用法

鉴于最新的 [httpoxy](https://httpoxy.org/) 漏洞，还有一个变量被广泛滥用。

`HTTP_X_FORWARDED_FOR` 常用于检测客户端 IP 地址，但如果不进行任何额外检查，这可能会导致安全问题，特别是当该 IP 稍后用于身份验证或在未经清理的情况下用于 SQL 查询时。

大多数可用的代码示例都忽略了这样一个事实：`HTTP_X_FORWARDED_FOR` 实际上可以被视为客户端自身提供的信息，因此它不是检测客户端 IP 地址的可靠来源。一些示例确实添加了关于可能滥用的警告，但代码本身仍然缺乏任何额外的检查。

因此，这里提供了一个用 PHP 编写的函数示例，说明如何检测客户端 IP 地址，前提是你知道客户端可能位于代理后面，并且你知道该代理是可信的。如果你不知道任何可信代理，可以直接使用 `$_SERVER['REMOTE_ADDR']`。

```php
function getClientIp(array $trustedProxies = []) {
    $ip = $_SERVER['REMOTE_ADDR'];
    if (in_array($ip, $trustedProxies)) {
        $forwarded = $_SERVER['HTTP_X_FORWARDED_FOR'] ?? '';
        $ips = array_map('trim', explode(',', $forwarded));
        $ip = array_shift($ips);
    }
    return $ip;
}
```

# 第 72 章：在 PHP 中创建 PDF 文件

## 第 72.1 节：PDFlib 入门

此代码要求你使用 [PDFlib 库](http://php.net/manual/en/ref.pdf.php) 才能正常运行。

```php
$p = new PDFlib();
if ($p->begin_document("", "") == 0) {
    die("Error: " . $p->get_errmsg());
}
$p->set_info("Creator", "hello.php");
$p->set_info("Author", "Rainer Schaaf");
$p->set_info("Title", "Hello world (PHP)!");
$p->begin_page_ext(595, 842, "");
$font = $p->load_font("Helvetica-Bold", "unicode", "");
$p->setfont($font, 24.0);
$p->set_text_pos(50, 700);
$p->show("Hello world!");
$p->continue_text("says PHP");
$p->end_page_ext("");
$p->end_document("");
$buf = $p->get_buffer();
$len = strlen($buf);
header("Content-type: application/pdf");
header("Content-Length: $len");
header("Content-Disposition: inline; filename=hello.pdf");
echo $buf;
$p = 0;
```

# 第 73 章：PHP 中的 YAML

## 第 73.1 节：安装 YAML 扩展

YAML 不随标准 PHP 安装提供，而是需要作为 PECL 扩展安装。在 linux/unix 上，可以通过简单的命令安装：

```bash
pecl install yaml
```

```text
libyaml-devel
```

请注意，系统上必须安装 `libyaml-devel` 包，因为 PECL 包只是对 libYAML 调用的简单封装。

Windows 机器上的安装方式不同——你可以下载预编译的 DLL 或从源代码构建。

## 第 73.2 节：使用 YAML 存储应用程序配置

[YAML](http://www.yaml.org/) 提供了一种存储结构化数据的方式。数据可以是一组简单的名称-值对，也可以是值甚至为数组的复杂层级数据。

请考虑以下 YAML 文件：

```yaml
database:
  host: localhost
  port: 3306
  username: root
  password: secret
  name: myapp
debug: true
paths:
  - /var/www
  - /opt/app
```

```text
config.yaml
```

假设它保存为 `config.yaml`。然后可以使用以下代码在 PHP 中读取此文件：

```php
$config = yaml_parse_file('config.yaml');
```

`print_r` 将产生以下输出：

```text
Array
(
    [database] => Array
        (
            [host] => localhost
            [port] => 3306
            [username] => root
            [password] => secret
            [name] => myapp
        )
    [debug] => 1
    [paths] => Array
        (
            [0] => /var/www
            [1] => /opt/app
        )
)
```

现在可以通过简单地使用数组元素来使用配置参数：

```php
$host = $config['database']['host'];
$port = $config['database']['port'];
```

# 第 74 章：使用 GD 进行图像处理

## 第 74.1 节：图像输出

| [image](http://php.net/manual/en/function.imagepng.php#refsect1-function.imagepng-seealso) |
| --- |

可以使用 [image*](http://php.net/manual/en/function.imagepng.php#refsect1-function.imagepng-seealso) [函数](http://php.net/manual/en/function.imagepng.php#refsect1-function.imagepng-seealso) 创建图像，其中 * 代表文件格式。

它们具有通用的语法：

```php
imagepng($image, $to = null, $quality = -1, $filters = -1);
```

### 保存到文件

如果要将图像保存到文件，可以将文件名或打开的文件流作为 `$to` 传递。如果传递流，则无需关闭它，因为 GD 会自动关闭它。

例如，保存 PNG 文件：

```php
imagepng($im, 'test.png');
```

使用 `fopen` 时，请确保使用 `b` 标志而不是 `t` 标志，因为该文件是二进制输出。

```php
fopen("php://temp", "wb", $f) or fopen("php://memory", "wb", $f)
```

不要尝试将 `fopen("php://output", "wb")` 传递给它。由于调用后函数会关闭流，你将无法进一步使用它，例如检索其内容。

### 作为 HTTP 响应输出

如果你想直接将此图像作为响应返回（例如创建动态徽章），则不需要传递任何内容（或传递 `null`）作为第二个参数。但是，在 HTTP 响应中，你需要指定内容类型：

```php
header('Content-Type: image/png');
imagepng($im);
```

```text
image/png, image/gif
```

`$mimeType` 是你返回的格式的 MIME 类型。示例包括 `image/png` 和 `image/gif`。

```text
image/jpeg
```

。

### 写入变量

有两种方法可以写入变量。

#### 使用 OB（输出缓冲）

```php
ob_start();
imagepng($im);
$png_data = ob_get_clean();
```

#### 使用流包装器

你可能有很多理由不想使用输出缓冲。例如，你可能已经开启了 OB。因此，需要一种替代方案。

使用 `stream_wrapper_register` 函数，可以注册一个新的流包装器。因此，你可以将流传递给图像输出函数，稍后再检索它。

```php
class GlobalStream {
    public $varname;
    public function stream_open($path, $mode, $options, &$opened_path) {
        $this->varname = parse_url($path, PHP_URL_HOST);
        return true;
    }
    public function stream_write($data) {
        $GLOBALS[$this->varname] .= $data;
        return strlen($data);
    }
    public function stream_eof() { return true; }
    public function stream_close() { return true; }
}
stream_wrapper_register('global', 'GlobalStream');
$png_data = '';
imagepng($im, 'global://png_data');
echo strlen($png_data);
```

在本例中，`GlobalStream` 类将任何输入写入引用变量（即间接写入给定名称的全局变量）。稍后可以直接检索全局变量。

有一些特别需要注意的事项：
