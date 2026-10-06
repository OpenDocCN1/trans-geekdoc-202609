

# 第 20 章：编写高质量代码

```php
} elseif ($factor > 9) {
    throw new InputException("Warp factor exceeds drive specifications", 2,
    $factor);
} elseif (WarpDrive::$dithiumLevel < $factor) {
    throw new FuelException("Insufficient fuel", 3, WarpDrive::$dithiumLevel);
} else {
    WarpDrive::$dithiumLevel = $factor;
    echo "<p>Now traveling at warp factor $factor</p>";
}
```

为了控制曲速驱动器，脚本创建了一个 `ChiefEngineer`（首席工程师）类。该类包含一个方法 `doWarp()`，它接受一个因子（factor）。它会创建一个新的 `WarpDrive` 对象并尝试设置正确的速度。

在这种情况下，`ChiefEngineer` 有点像是一个“唯诺诺”（yes man）。他接收指令——即所需的曲速因子——并通过其 `setWarpFactor()` 方法将其传递给新的 `WarpDrive` 对象。他没有对请求的速度进行任何检查，也没有尝试捕获由 `WarpDrive` 对象可能抛出的任何异常。

```php
class ChiefEngineer {
    public function doWarp($factor) {
        $wd = new WarpDrive;
        $wd->setWarpFactor($factor);
    }
}
```

最后创建的类是 `Captain`（船长）。该类包含一个方法 `newWarpOrder()`，它接受一个因子。该方法随后创建一个新的 `ChiefEngineer` 对象，并通过其 `doWarp()` 方法将指令传递给该对象。

与 `ChiefEngineer` 类不同，`Captain` 的 `newWarpOrder()` 方法使用 `try ... catch` 块检查曲速指令是否存在问题。由于异常会通过调用链向上抛，`WarpDrive` 对象抛出的任何异常都会在这里被捕获。`try` 块调用 `doWarp()` 方法，而多个 `catch` 块处理可能抛出的不同类型的异常：

```php
class Captain {
    public function newWarpOrder($factor) {
        $ce = new ChiefEngineer;

        try {
            $ce->doWarp($factor);
        } catch (InputException $e) {
            echo "<p>Captain's log: Warp factor " . $e->getInvalidWarpFactor() . ". I must be losing my mind...</p>";
        } catch (FuelException $e) {
            echo "Captain's: I'm getting a fuel problem from the warp engine. It says: " . $e->getMessage() .
            echo "We have " . $e->getRemainingFuel() . " dilithium left. I guess we're not going anywhere.";
        } catch (Exception $e) {
            echo "Captain's: Something else happened, I don't know what. The message is " . $e->getMessage() . "./";
        }
    }
}
```

# 第三部分：在实践中使用 PHP

如果该方法捕获到 `InputException`，它会通过调用 `InputException::getInvalidWarpFactor()` 显示一条消息，包括请求的曲速因子。同样，如果捕获到 `FuelException`，该方法会显示不同的消息，通过 `FuelException::getMessage()` 获取消息，并从 `FuelException::getRemainingFuel()` 显示剩余燃料。最后，该方法会捕获任何可能抛出的其他 `Exception`，并显示通用的错误消息。在你可能创建的任何自定义 `Exception` 中，捕获通用 `Exception` 对象始终是一个好主意。

最后，脚本创建了一个新的 `Captain` 对象并使用其 `newWarpOrder` 方法设置各种速度。从图 20-2 中可以看到，随着脚本的执行，各种异常被抛出并显示。

# 分离应用逻辑与显示逻辑

当你第一次编写 PHP 脚本时，你可能会发现自己自然地想要将 PHP 代码（应用逻辑）和 HTML 标记（显示逻辑）混合在同一个脚本文件或页面中。事实上，本书中的大多数示例都遵循这种格式，因为这样在一个地方解释代码会更简单。

虽然这种方法对于小型脚本是可以接受的，但随着项目规模的扩大，它会变得难以维护。将逻辑与显示分离可以提高代码的可读性和可重用性。

