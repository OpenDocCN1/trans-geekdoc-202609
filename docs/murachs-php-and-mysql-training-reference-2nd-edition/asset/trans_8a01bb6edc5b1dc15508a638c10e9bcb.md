

## 如何执行INSERT、UPDATE和DELETE语句

图4-6展示了如何准备和执行INSERT、UPDATE和DELETE语句。该图中的示例使用了前几幅图介绍的prepare、bindValue、execute和closeCursor方法。因此，你应该不难理解这些示例的工作原理。

第一个示例向数据库插入一行。这里，INSERT语句指定了四个参数：每一列对应一个值。

第二个示例更新数据库中的一行。这里，UPDATE语句指定了两个参数：第一个指定产品的新价格，第二个唯一标识要更新的产品。

第三个示例从数据库中删除一行。这里，DELETE语句指定了一个参数，该参数唯一标识要删除的产品。

### 如何执行INSERT语句

```php
$category_id = 1;
$code = 'strat';
$name = 'Fender Stratocaster';
$price = 699.99;

$query = "INSERT INTO products
            (categoryID, productCode, productName, listPrice)
        VALUES
            (:category_id, :code, :name, :price)";

$statement = $db->prepare($query);
$statement->bindValue(':category_id', $category_id);
$statement->bindValue(':code', $code);
$statement->bindValue(':name', $name);
$statement->bindValue(':price', $price);
$statement->execute();
$statement->closeCursor();
```

### 如何执行UPDATE语句

```php
$product_id = 4;
$price = 599.99;

$query = "UPDATE products
        SET listPrice = :price
        WHERE productID = :product_id";

$statement = $db->prepare($query);
$statement->bindValue(':price', $price);
$statement->bindValue(':product_id', $product_id);
$statement->execute();
$statement->closeCursor();
```

### 如何执行DELETE语句

```php
$product_id = 4;

$query = "DELETE FROM products
        WHERE productID = :product_id";

$statement = $db->prepare($query);
$statement->bindValue(':product_id', $product_id);
$statement->execute();
$statement->closeCursor();
```

图4-6：如何执行INSERT、UPDATE和DELETE语句

## Product Viewer应用程序

现在你知道了如何使用PHP操作MySQL，可以准备了解数据库驱动的PHP应用程序是如何工作的。首先，图4-7展示了一个简单的Product Viewer应用程序，它允许你按类别查看产品数据。在查看完这个应用程序后，你将学习一个更复杂的应用程序。

### 用户界面

Product Viewer应用程序的主页面分为两部分。左侧的侧边栏显示类别链接列表，让用户选择类别。页面的主要部分以HTML表格的形式列出该类别的产品。

当应用程序启动时，该应用程序显示名为Guitars类别中的产品。然后，如果用户想要查看另一个类别的产品，用户可以点击该类别的链接。例如，如果用户点击Basses链接，该应用程序就会显示该类别的产品。为了实现这一点，category_id字段将随同一页面的HTTP请求一起发送。图4-7中第二个屏幕的URL说明了这一点，该URL请求ch04_product_viewer目录中的默认页面。

为了便于识别产品数据的列和行，该应用程序使用CSS来格式化HTML表格。这种格式化在表格外围添加实线边框，在列和行之间添加虚线边框。

![](img/b7dd5fec6684a99ab526c7fe8e21e7de_162_0.png)

### 用户选择新类别后的用户界面

![](img/b7dd5fec6684a99ab526c7fe8e21e7de_162_1.png)

### 代码

database.php文件包含创建PDO对象并将其存储在名为$db的变量中的代码。该文件由下一页显示的index.php文件执行。

然而，如果执行此文件时发生错误，catch块会将错误消息存储在名为$error_message的变量中。然后，catch块使用include函数包含database_error.php文件，该文件显示包含错误消息的页面。最后，catch块退出脚本。

请注意，在database.php文件中，连接的用户名是“mgs_user”，密码是“pa55word”。要使此连接正常工作，MySQL数据库中必须存储具有该用户名和密码的用户。事实上，正如你在第3章所学到的，该用户是由为本书创建数据库的SQL脚本创建的。此外，该用户被授予了针对my_guitar_shop1数据库中任何表运行SELECT、INSERT、UPDATE和DELETE语句所需的权限。因此，此连接将可用于此应用程序。

### database.php文件

```php
<?php
    $dsn = 'mysql:host=localhost;dbname=my_guitar_shop1';
    $username = 'mgs_user';
    $password = 'pa55word';

    try {
        $db = new PDO($dsn, $username, $password);
    } catch (PDOException $e) {
        $error_message = $e->getMessage();
        include('database_error.php');
        exit();
    }
?>
```

### database_error.php文件

```php
<!DOCTYPE html>
<html>
    <!-- the head section -->
    <head>
        <title>My Guitar Shop</title>
        <link rel="stylesheet" type="text/css" href="main.css">
    </head>

    <!-- the body section -->
    <body>
    <main>
        <h1>Database Error</h1>
        <p>There was an error connecting to the database.</p>
        <p>The database must be installed as described in appendix A.</p>
        <p>The database must be running as described in chapter 1.</p>
        <p>Error message: <?php echo $error_message; ?></p>
    </main>
    </body>
</html>
```

## 自动化集装箱码头——运筹学贡献文献综述

Nils Kemper, Asir Asad, Jürgen W. Böning

收稿日期：2021年3月24日 / 修订日期：2021年11月10日 / 录用日期：2021年11月15日 © 作者2021

**摘要** 由于集装箱吞吐量持续增长和集装箱船舶规模不断扩大，集装箱码头的优化与自动化变得越来越重要。特别是在运营领域，通过优化设计和利用现有资源，可以提高码头吞吐能力。本综述的重点是评估过去和现在对集装箱码头自动或半自动控制的研究贡献。由此，可以为未来与码头自动化标准化相关的规划决策提供支持，涉及物流流程、设备和控制系统。特别关注物流过程的（半）自动化控制，如配载计划、资源分配及其调度。我们还详细介绍了用于解决这些通常复杂优化问题的运筹学方法。检索的文献包括近十年来发表在一流学术期刊以及相关会议论文集上的研究文章。我们可以表明，大多数最先进的方法都具有复杂的数学模型特征，并针对码头环境进行了测试，而现代自动化集装箱码头的完整流程链在文献中很少出现。在大多数情况下，只考虑单个过程的优化。此外，所应用的模型很少被重复使用，甚至很少与同一背景下的替代模型进行比较。为此，我们提出在自动化集装箱码头背景下规范整体及子流程的定义，以促进不同方法之间的可比性。

**关键词：** 自动化集装箱码头 · 集装箱码头 · 运筹学 · 物流 · 自动化

## 1 引言

全球集装箱航运流量的持续增长和集装箱船舶规模的不断扩大，给海港集装箱码头带来了提高生产率、吞吐量和效率的压力。尤其是自集装箱化时代以来，港口已成为全球供应链中最重要的节点之一。事实上，全球约90%的贸易量是通过海运处理的。集装箱码头的运营是一个高度复杂的过程，需要多个不同子系统的协同作用。自动化集装箱码头尤其如此。由于流程复杂程度高，需要采用复杂的方法来规划和控制码头内的流程。然而，现有方法往往针对特定的子流程或优化问题。

## 2 自动化集装箱码头的最新技术水平

### 2.1 功能区域、物料搬运设备和流程

一般来说，集装箱码头可以分为六个不同的区域。这些区域是泊位、码头前沿、堆场、闸口、铁路区和空箱堆场。泊位是船只停泊以及集装箱装卸的区域。码头前沿是集装箱在运往堆场之前临时存放的区域。堆场是集装箱长期存放的区域。闸口是集装箱通过卡车进出码头的区域。铁路区是集装箱在码头和铁路之间转运的区域。空箱堆场是存放空集装箱的区域。集装箱码头使用的物料搬运设备（MHE）可分为三类：岸边起重机、堆场起重机和内部运输车辆。这些设备用于在码头的不同区域之间运送集装箱。集装箱码头执行的流程可分为四组：船舶流程、码头前沿流程、堆场流程和闸口流程。船舶流程包括与船舶相关的所有活动，如船舶靠泊和离泊。码头前沿流程包括船舶的装卸。堆场流程包括堆场中集装箱的堆存和取回。闸口流程包括与闸口相关的所有活动，如卡车的进场和出场登记。

| | 类型 | 简短描述 |
|---|---|---|
| ACC | 自动化集装箱码头 | 具有自动化流程的集装箱码头 |
| AGV | 自动导引车 | 自动化运输车辆 |
| ALV | 自动升降车 | 具有升降能力的自动化车辆 |
| ASC | 自动化堆场起重机 | 用于堆场作业的自动化起重机 |
| ARMG | 自动化轨道式龙门起重机 | 轨道式自动化龙门起重机 |
| ARTG | 自动化轮胎式龙门起重机 | 轮胎式自动化龙门起重机 |
| ATLS | 自动化运输和升降系统 | 具有升降能力的自动化运输系统 |
| AV | 自动化车辆 | 通用自动化车辆 |
| BCO | 货主 | 货物的所有者 |
| BAP | 泊位分配问题 | 分配泊位的问题 |
| BEO | 集装箱交接点 | 集装箱交接的点 |
| BLAP | 泊位布局问题 | 泊位布局的问题 |
| BMH | 集装箱处理机械 | 用于处理集装箱的机器 |
| BPM | 业务流程模型 | 业务流程的模型 |

