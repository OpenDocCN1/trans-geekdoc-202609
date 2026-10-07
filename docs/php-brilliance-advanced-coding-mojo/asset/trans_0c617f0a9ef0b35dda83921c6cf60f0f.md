

# 寻找闭包。

```php
public function __call($methodName, $args)
{
    if (is_callable($this->this->methods[$methodName])) {
        return call_user_func_array(
            $this->methods[$methodName],
            $args
        );
    }
}
```

结果是什么？视图通过调用各个闭包，*就像它们是公共方法一样*，来访问所需的数据。

账号：<?= echo $model->getAccountNumber(); ?>
客户名称：<?= echo $model->getCustomerName(); ?>

```php
<?php foreach ($model->getOrders() as $order): ?>
// 按需渲染细节。
<?php endforeach; ?>
```

显然，你会根据自己的需求调整输出的生成。我们在这里观察到的全部，就是闭包的调用*类似于*对对象方法的的调用。

# 回到宏（macros）。

一个关于闭包的章节，如果不提到你在实战中可能会遇到闭包的最常见情况，那么它是不完整的。

在最近几年里，PHP 世界中对依赖注入容器（Dependency Injection Containers）有很多讨论，而对路由（routing）的艺术与科学的讨论虽然较少，但同样重要。如果你最近接触过这两个概念中的任何一个，你可能会发现很难注意到它们也广泛地使用了闭包。

因此，这两个概念为我们从真实世界的背景下检查闭包的使用提供了一个理想方式。

我们的第一个例子是路由，它直接来自 Slim 微框架¹⁰ 的首页。

> ¹⁰http://www.slimframework.com/

# 寻找闭包。

```php
<?php
$app = new \Slim();
$app->get('/hello/:name', function ($name) {
    echo "Hello, $name";
});
$app->run();
```

这种路由方法在 PHP 框架世界正变得无处可见，而且也是有原因的。这是一种非常有效且极其灵活的方法，可以将这种类似宏的结构映射到 URL 模式上，从而根据模式与传入的请求路径的匹配结果，自动执行包含在其中的代码。

尽管上面的代码非常简单，但我们应该在这里考虑它。一方面，我们有触发宏执行的各个方面；另一方面，我们有宏本身的定义，每当模式匹配时就会被触发。

当然，这个宏的体（即这个闭包）是极其简单的。一点细微的修改也能非常出色地引入下一个想法。

```php
<?php
$app = new \Slim();
$app->get('/blog/:postId', function ($postId) use ($app) {

    $service = new BlogService();
    $controller = new BlogController($app, $service);
    $controller->renderPostAction($postId);
});
```

好了，也许不那么微妙了，但至少我们的可调用对象已经通过更具相关性的代码充实起来，在此过程中帮助我们将其看作更像一个宏。

在我们可调用对象的体内部有两行代码，导致了 `BlogService` 和 `BlogController` 对象的实例化。鉴于这个可调用对象在它被调用之前不会执行，很容易看出我们是如何延迟到最后一刻才对服务和对象进行实例。

# 寻找闭包。

# 196

当这样使用时，闭包非常积极地帮助我们支持延迟加载（lazy loading）的概念。可以肯定，这种方法会使我们在早期的设置和配置阶段花费相当的时间，但所获得的收益将非常出色地补偿我们早期的努力。

假设我们正在使用一种严谨的自动加载策略，创建闭包来促进在需要的地方再实例化对象，这节省了浪费服务器资源的成本，并在处理端用户请求和交付响应时提供了最大的效率。

这种按需延迟加载对象的概念是依赖注入容器的核心特性。在本书后面探索依赖注入的过程中，我们将更仔细地观察其中的一些内容。

尽管如此，为了我们的目的，让我们简单看看 Pimple¹¹，来自 SensioLabs 的 DI 容器。再次，我将直接从首页借用一些代码，以便我们像上面 Slim 提供的路由示例一样对其进行挑选。

```php
<?php
use Pimple\Container;

$container = new Container();

// 定义一些服务
$container['session_storage'] = function ($c) {
    return new SessionStorage('SESSION_ID');
};

$container['session'] = function ($c) {
    return new Session($c['session_storage']);
};

// 获取 session 对象
$session = $container['session'];
```

除了纯粹为了避免混淆之外，几乎值得注意的是，Pimple 中的 `Container` 类实现了 `ArrayAccess` 接口，这就是为什么我们看到使用数组方括号访问器分配闭包。

> ¹¹http://pimple.sensiolabs.org/

# 寻找闭包。

在任何情况下，我们仍然可以追溯这段代码以检查为什么这种基于闭包的方法是理想的。

从最后一行开始，我们在这里将 `$session` 变量赋值为存储在容器中的 `'session'`键的内容。在 Pimple 中，当你第一次访问容器的键之一时，存储在上面的可调用对象就会被调用，产生它的返回值。在这种情况下，它是一个 `Session` 类的实例。

此阶段真正相关的部分是相应的闭包并不是孤立地返回新实例，而是通过另一个闭包返回的值来配置该实例；这次是对应于 `'session_storage'` 键的那一个。在内部，这个 session 闭包实例化并返回了一个配置好的存储对象。

这正是我们开始从最初设置容器的努力中获得回报的地方。通过将所有闭包都放在一个位置来建立配置，我们再次欣赏那段代码片段中最后一行的力量和简单。

```php
$session = $container['session'];
```

远离原始的配置和设置，`$session` 变量被填充了一个正确配置的 `Session` 实例，一个带有了所有依赖并准备就绪的实例。在执行这一行之前，session 对象并不存在，类也没有被解析。这对于我们希望构建一个不仅仅是“简陋”的网站带来了性能收益。

尽管如此，就我们而言，这一行客户端代码使得我们能够快速方便地更改实现。由于新的 session 继续遵循之前的接口，所有的 session 都不会被破坏。

# 总结

正如我在开始建议的那样，可能最好在午夜不要喂这些小生物。

一方面，我们看到了如何使用它们来获得对另一个对象受严格保护的私有属性的完全读写访问。不这样做是一个特别明智的立场。

另一方面，我们还考虑了如何通过从其他真实的活对象实例中挑选方法来创建完全新的对象，并且这些方法保留了它们原始的作用域。对于从各种模型创建一个只读对象来说，这是一种幸事。然而，正如之前提到的，这种技术在现实世界应用中的用例非常有限。我们显然无法将这样的结构呈现给客户端代码进行进一步处理，因为它本身不带接口。这种缺乏抽象基类或已实现接口的保证意味着不得不诉诸鸭子类型（duck typing）。有了这样一个“弗兰肯斯坦怪物”在手，即使是那样也是痛苦的。

