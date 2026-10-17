

也可以从 PHP 脚本中发送信号。这可以用于（粗略地）与其他脚本通信，如果脚本有足够权限，还可以用于控制进程。要发送信号，只需使用名字具有误导性的 `posix_kill()` 函数即可。这个函数实际上允许你发送 *任何* PHP 支持的信号，而不仅仅是用于终止进程的信号。要使用它，你需要知道要通信的进程的 PID（进程 ID，例如 123456），然后只需调用 `posix_kill(123456, SIGINT)` 即可。

### 8.9 Linux 定时事件信号

有时我们希望脚本每隔一段时间执行某些操作，例如检查资源状态、执行清理工作、更新日志文件或类似操作。实现这一点有几种方法。最简单的是使用 `sleep()` 或 `usleep()` 函数等待若干秒/微秒后再执行任务。但这并不总是有用，因为当你调用 `sleep()` 时，脚本会停止并等待那段时间，而不是继续做其他有用的工作。在上一节中，我们简要介绍了 PHP “ticks”，它允许我们每执行 N 条（潜在有用）语句后运行一个回调函数。这使得我们可以在回调函数调用之间执行有用的工作，但无法保证这些语句执行需要多长时间，因此我们无法等待特定的时间长度。事实上，PHP 没有内部方式以这种方式跟踪时间。但是，使用我们在上一节中介绍过的 POSIX 信号，我们可以要求系统在未来的若干秒后为我们设置一个“闹钟”。当“闹钟”响起时，系统会用一个信号中断 PHP，我们可以处理该信号来运行回调函数。

在上一节中，我们介绍了如何监听和处理 Linux 信号，如果你还没有读过那一节，我建议你现在就读一下，以便完全理解下面的示例。

```
<?
# We enable ticks for pcntl to use as before.

declare(ticks = 1);

$keepRunning = true;

# This is the function that we want to execute every 5 seconds.

function takeABreak($signal) {
   
   echo("\n\n ======== HAVING A BREAK, BE BACK SOON ========");

   sleep(3);

   echo("\n\n ======== BREAKS OVER, BACK TO WORK! ======== \n\n");

   # We need to request an alarm again each time.

   pcntl_alarm(5);

};

# This is a function to gracefully exit our program

function timeToGo($signal) {

	global $keepRunning;

	$keepRunning = false;

};

# In a moment we will ask the system to set an alarm, but before that
# we will register the callback function that will happen when the
# alarm goes off, i.e. when the system sends us a SIGALARM signal

pcntl_signal(SIGALRM, "takeABreak", true);

# Just to show that we can handle any and all signals with more than
# one callback function, we'll also register a different handler for 
# the SIGINT/SIGTERM signals

pcntl_signal(SIGINT, 'timeToGo');
pcntl_signal(SIGTERM, 'timeToGo');

# Once we have got a callback function registered, we can go ahead and
# ask the system to set an alarm for us. The alarm only works once, so
# you'll notice this call to pcntl_alarm is repeated at the end of the
# callback function to set the alarm again

pcntl_alarm(5);

# Now we enter our main work loop

while ( $keepRunning ) {
   
   echo('...doing work...');

   usleep(50000);

};

# If we get here, then we've had the SIGINT or SIGTERM signals

echo("\nBye Bye, see you tomorrow.\n");
```

如果你运行上面的脚本，你会看到屏幕上每隔半秒打印一次‘…doing work…’。每隔 5 秒，我们的闹钟回调函数会启动并暂停工作 3 秒钟，然后工作恢复。

使用闹钟信号时，有几个重要概念需要理解：

*   闹钟回调函数会中断正常的脚本执行。也就是说，在闹钟函数执行期间，正常脚本不会在后台继续运行（它不是多线程的）。

*   闹钟函数可以在脚本的任何位置启动。如果你修改了脚本的状态（例如设置全局变量、使用资源和连接），你的脚本应该能够在执行的任何时间点处理该新状态。

*   你无法提前知道主脚本或其任何部分运行需要多长时间。这受系统负载和资源、用户交互等因素的影响。因此，你不应该设置假设底层脚本进度的闹钟。

*   同一时间只能设置一个闹钟。任何进一步的 `pcntl_alarm()` 调用都会取消第一个闹钟，尽管它也会返回之前闹钟剩余的秒数。

*   你可以通过调用 `pcntl_alarm(0)` 来取消闹钟，它同样会返回该闹钟剩余的秒数。

*   任何接收到的 SIGALRM 都会导致正在进行的任何系统调用（例如对 `sleep()` 的调用）退出的副作用。因此，你应该确保脚本能够容忍此类中断（或者你的闹钟回调函数应修复/重置脚本状态可能受到的任何损坏）。

*   如果在任何时间点你希望主脚本等待直到下一个闹钟发生，你可以调用 `pcntl_sigwaitinfo(array(SIGALRM))`，它会暂停执行直到闹钟发生。

### 8.10 打印（到纸上）

尽管我们可能希望在无纸化办公环境中工作，但迟早我们仍然需要巧妙地将一些碳粉溅到一张 A4 或法律纸上。PHP 有一个打印扩展，但它很有问题，因为它仅适用于 Windows，官方仅支持 Windows 2000 及以下版本（尽管它通常适用于 Windows 7 及以下版本），并且所需的 dll 文件不再作为 PHP 的标准组件提供。它也不再在 PHP 手册中详细说明。出于这些原因，我们不会在本书中介绍它。它仍然可以在 pecl 上找到，详细信息的旧 PHP 手册地址如下，你可能可以在互联网档案中找到。

| ![information](Images/image00248.jpeg) || **进一步阅读**Pecl 网站上的打印机扩展  

[http://pecl.php.net/package/printer](http://pecl.php.net/package/printer)PHP 手册中的打印机扩展  

[http://www.php.net/manual/en/book.printer.php](http://www.php.net/manual/en/book.printer.php) |

| --- | --- |

相反，我们将介绍一种从 PHP 打印的不同方法，经过一些调整后，它通常可以在所有平台上工作。那就是从 PHP 创建和打印 PDF 文件。

我们将使用一个名为 FPDF 的免费 PHP 编写的 PDF 库。无需安装，你只需在脚本中 `require()` `fpdf.php` 文件并开始使用它。一旦我们用它创建了 PDF 文件，我们就需要打印它。最简单的方法是使用系统默认的 PDF 查看器打开它，它将充当“打印预览”，允许用户像打印普通文件一样打印它。另一种方法是在后台直接打印而不打开预览，其操作方式类似。

让我们看一个 Linux 下的示例：

