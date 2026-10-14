
# 这段代码的作用是将用户登录时 offset `$user->id` 位改为 1（默认是 0），这成为一种非常高效的存储 true/false 值的方式，即使有数百万用户，`logins:2012-Nov-04` 的大小也小于 1MB。

![](images/07----bitmap.png)

用户 ID 映射到位置，操作非常快速。在上图中，我们可以看到 User #10、User #6、User #5、User #4 和 User #2 在 2012 年 11 月 4 日登录。

你可能会说，这很好，但相比直接存储哈希或计数器，这有什么优势？优势在于可以对位进行位运算。

## Population Count（人口计数）

使用 `bitcount` 可以进行人口计数，即统计被设置为 1 的位的数量，从而快速统计在特定日期登录的用户数量。

```
1 <?php
2 
3 $r->bitcount("logins:2012-Nov-04"); // 返回 5
```

## 位运算

在位图上执行位运算是真正的强项。你可以对两个不同的位图执行任何位运算，例如，如果你想知道在特定日期登录过桌面端和移动端应用的用户有哪些？

数据如下：

```
1 web:logins:2012-Nov-04    => 001001001
2 mobile:logins:2012-Nov-04 => 101110001
```

对应的代码如下：

```
1 <?php
2 
3 $r->bitop("and", "both:logins:2012-Nov-04",
4                  "web:logins:2012-Nov-04",
5                  "mobile:logins:2012-Nov-04");
6                  
7 $r->bitcount("both:logins:2012-Nov-04"); // 返回 2
```

此外，你还可以使用 `or`、`xor` 和 `not` 进行操作，从而快速创建各种聚合，且数据量消耗极低。

### Redis 通知队列

Redis 另一个流行的用途是创建通知队列。与数据库相比，Redis 更适合处理通知，因为通知通常是写入密集的一次性数据——用户查看后即可删除，且本质上是列表。Redis 完美契合这一场景。

想象你想在有人点赞用户写的评论时通知该用户，可以这样实现：

```
1 <?php
2 
3 function notify_of_like($comment, $current_user) {
4   $r = new Redis;
5   $r->lpush("notifications:{$comment->user->id}", "{$current_user->username} l\
6 ikes your comment.");
7 }
```

![](images/07----notifications.png)

使用 `lpush` 可以快速在通知列表头部预pending 新通知，从而形成 LIFO（后进先出）队列，按创建时间排序。

要获取某用户最近 20 条通知，只需调用 `lrange(notifications:user_id, 0, 20)`。如果想查看通知总数，只需 `llen(notifications:user_id)`。通知查看后，可使用 `ltrim(notifications:user_id, 0, 20)` 删除已处理的通知。

## Worker Server：异步 Resque 工作进程

所有网站的终极目标是尽可能快速地渲染页面给用户。事实证明，更快的网站意味着更幸福的用户、更高的收入和更多的页面浏览量。速度是重要因素，快速的应用会直接影响你的底线。

Amazon 曾提到，速度每提升 100ms，收入可增长 1% [5]。2011 年，Amazon  revenue 达到 500 亿美元，速度提升 100ms 为其底线带来 5000 万美元的增益。

这很了不起。我们之前讨论了通过优化数据库性能、缓存慢查询、以及使用更可扩展的软件组件来提升速度的方法。但当存在固定成本时，即无论怎么优化，某些代码仍需秒级完成（如计算密集型查询或第三方 API 调用），如何让这些 workload 不影响页面响应速度？

答案是：将工作放到背景中！所谓“在背景中”，即在独立进程中执行，脱离 web 请求。这样 web 请求可以尽快渲染页面给用户，而耗时的任务则被推迟执行。

### 为什么使用队列？

存在很多不佳的方式来推送工作，但这里不再赘述。
