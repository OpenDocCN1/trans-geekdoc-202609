
Listing 3-6 说明了一个使用上下文（context）而不是 DialTimeout 来完成相同功能的测试。

package ch03

import (
    "context"
    "net"
    "syscall"
    "testing"
    "time"
)

func TestDialContext(t *testing.T) {
    dl := time.Now().Add(5 * time.Second)

    ctx, cancel := context.WithDeadline(context.Background(), dl)

    defer cancel()

    var d net.Dialer // DialContext 是 Dialer 上的方法

    d.Control = func(_, _, _ string, _ syscall.RawConn) error {
        // 睡够长的时间以确保超过上下文的截止时间。
        time.Sleep(5*time.Second + time.Millisecond)
        return nil
    }

    conn, err := d.DialContext(ctx, "tcp", "10.0.0.0:80")

    if err == nil {
        conn.Close()
        t.Fatal("connection did not time out")
    }

    nErr, ok := err.(net.Error)
    if !ok {
        t.Error(err)
    } else {
        if !nErr.Timeout() {
            t.Errorf("error is not a timeout: %v", err)
        }
    }

    if ctx.Err() != context.DeadlineExceeded {
        t.Errorf("expected deadline exceeded; actual: %v", ctx.Err())
    }
}

[/content]

[content]
通过取消上下文（context）来取消连接，如下 Listing 3-7 所示。

package ch03

import (
    "context"
    "net"
    "syscall"
    "testing"
    "time"
)

func TestDialContextCancel(t *testing.T) {
    ctx, cancel := context.WithCancel(context.Background())

    sync := make(chan struct{}

    go func() {
        defer func() { sync <- struct{}{} }()

        var d net.Dialer

        d.Control = func(_, _, _ string, _ syscall.RawConn) error {
            time.Sleep(time.Second)
            return nil
        }

        conn, err := d.DialContext(ctx, "tcp", "10.0.0.1:80")

        if err != nil {
            t.Log(err)
            return
        }

        conn.Close()
        t.Error("connection did not time out")
    }

    cancel()

    <-sync

    if ctx.Err() != context.Canceled {
        t.Errorf("expected canceled context; actual: %q", ctx.Err())
    }
}

[/content]

[content]
直接取消上下文（context）来取消连接，如下 Listing 3-7 所示。

package ch03

import (
    "context"
    "net"
    "syscall"
    "testing"
    "time"
)

func TestDialContextCancel(t *testing.T) {
    ctx, cancel := context.WithCancel(context.Background())

    sync := make(chan struct{}

    go func() {
        defer func() { sync <- struct{}{} }()

        var d net.Dialer

        d.Control = func(_, _, _ string, _ syscall.RawConn) error {
            time.Sleep(time.Second)
            return nil
        }

        conn, err := d.DialContext(ctx, "tcp", "10.0.0.1:80")

        if err != nil {
            t.Log(err)
            return
        }

        conn.Close()
        t.Error("connection did not time out")
    }

    cancel()

    <-sync

    if ctx.Err() != context.Canceled {
        t.Errorf("expected canceled context; actual: %q", ctx.Err())
    }
}

[/content]

[content]
使用同一上下文取消多个 DialContext 调用，并在收到第一个响应后取消所有剩余的 Dialer，如下 Listing 3-8 所示。

package ch03

import (
    "context"
    "net"
    "sync"
    "testing"
    "time"
)

func TestDialContextCancelFanOut(t *testing.T) {
    ctx, cancel := context.WithDeadline(
        context.Background(),
        time.Now().Add(10*time.Second),
    )

    listener, err := net.Listen("tcp", "127.0.0.1:")
    if err != nil {
        t.Fatal(err)
    }
    defer listener.Close()

    go func() {
        // 只接受一个连接。
        conn, err := listener.Accept()
        if err == nil {
            conn.Close()
        }
    }()

    dial := func(ctx context.Context, address string, response chan int, id int, wg *sync.WaitGroup) {
        defer wg.Done()
        var d net.Dialer
        c, err := d.DialContext(ctx, "tcp", address)
        if err != nil {
            return
        }
        c.Close()
        select {
        case <-ctx.Done():
        case response <- id:
        }
    }

    res := make(chan int)
    var wg sync.WaitGroup

    for i := 0; i < 10; i++ {
        wg.Add(1)
        go dial(ctx, listener.Addr().String(), res, i+1, &wg)
    }

    response := <-res
    cancel()
    wg.Wait()
    close(res)

    if ctx.Err() != context.Canceled {
        t.Errorf("expected canceled context; actual: %s", ctx.Err())
    }

    t.Logf("dialer %d retrieved the resource", response)
}

[/content]

[content]
使用带有截止时间的上下文创建上下文，以便在检查上下文的 Err 方法时能够得到三种可能的结果：context.Canceled、context.DeadlineExceeded 或 nil。预期 Err 返回 context.Canceled 错误，因为测试通过调用取消函数来取消 Dialer。

首先，你需要一个监听器。该监听器接受一个连接并在此成功握手后关闭它 2。接下来，你创建 Dialer。由于你要并发创建多个 Dialer，因此将拨号代码抽象到独立函数 3 是合理的。这个匿名函数使用 DialContext 拨号到指定地址；如果成功，则会通过 response 通道发送 Dialer 的 ID，前提是上下文尚未被取消。你通过在 for 循环中分别启动多个 Dialer 来并发创建多个 Dialer 4。如果 Dial 因为另一个 Dialer 赢了竞争而阻塞在 DialContext 调用上，你可以通过取消上下文（通过取消函数或截止时间）使 Dial 函数提前退出。你使用 WaitGroup 确保在取消上下文后，所有 Dial goroutine 都已结束，以免测试提前进行。

在 goroutine 开始运行后，有一个会赢得竞争并成功连接到监听器。你在 res 通道上收到获胜 Dialer 的 ID 5，然后通过取消上下文取消剩余的 Dialer。此时，wg.Wait 会阻塞，直到被取消的 Dialer goroutine 返回。

最后，你确认是通过你的取消调用导致上下文取消 6。调用 cancel 并不保证 Err 会返回 context.Canceled。如果截止时间取消上下文，则调用 cancel 成为无操作，Err 会返回 context.DeadlineExceeded。虽然在实践中这种区别可能不重要，但如果你需要它，它是存在的。

***实现截止时间***

