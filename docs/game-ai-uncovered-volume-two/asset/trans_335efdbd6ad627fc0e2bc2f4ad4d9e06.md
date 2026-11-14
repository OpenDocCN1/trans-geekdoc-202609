

庄园宅邸整体边界内的庭院空间。如果这个空间有自己的房间体积，标记为室外，并且一个代理站在这里，他们将嵌套三个体积深，并且因为庭院"房间"是最小的，他们现在又是室外了。

从示例中可以看出，这是一个非常简单但又巧妙的标记系统，NPC可以很好地利用它，如果你的游戏世界异常小，并且很少被修改，这可能足以满足你的游戏需求。然而，“异常小”和“很少被修改”并不适用于正在开发的绝大多数游戏！例如，你不可能指望关卡设计师去标记*侠盗猎车手5*规模开放世界中的每一个房间和每一栋建筑，然后还现实地指望他们在游戏世界不可避免地在开发过程中发生变化时，时刻掌握大量的触发体积。对于非常独特的情况，回退到这种手动标记系统固然不错，但理想情况下，你需要为设计团队提供一个系统，当环境被微调时，该系统能尽可能自我维护，甚至能在不需要插入虚拟路标的情况下，提供尽可能多的自动环境标记。

## 16.3 使用体素分析环境

你可以使用多种地形分析方法来帮助自动化手动标记，但一种强大且经典的方法是八叉树，用于将环境细分为体素。你的游戏引擎中可能甚至已经在进行此操作，供渲染或照明系统使用，这意味着你甚至可能能够为AI系统利用一些共享技术。

无论如何，你需要从八叉树中得到的是细分空间，最终得到环境的一个体素化区域，其中包含一组覆盖碰撞的体素（封闭体素）和一组占据可导航空间的体素（开放体素）。一旦有了这个，你就可以使用NPC的当前位置来查询其当前占据的开放体素，并开始标记和询问这些体素以获取空间信息。

## 16.4 生成阶段

完整的环境标记过程可以离线进行，生成的数据可以保存并存储为二进制数据文件。但是，如果环境被修改，可能会出现需要在运行时重新生成部分或全部数据的情况。

生成阶段如下所示，这些阶段将在后面详细探讨：

- 1. 使用用户定义的种子边界生成八叉树，以及所有开放和封闭体素。
- 2. 剔除生成后完全位于种子边界之外的任何体素。
- 3. 对开放体素执行内部测试。
- 4. 在体素空间中传播标记种子。
- 5. 将任何标记边界的标记继承到体素空间中。

### 16.4.1 生成体素空间

要开始生成过程，将一个定向包围盒放置到环境中，它定义了你想要生成体素标记空间的区域。在八叉树生成期间，该区域会被拉伸为三个维度上均匀（如果还不是均匀的话），然后任何完全超出原始包围区域的生成体素可以在最后被剔除。

八叉树生成是一个递归函数，最初使用拉伸的种子包围区域调用，随后使用八叉限界调用，在简单的算法级别上，它看起来类似于代码清单16.1。

**代码清单16.1：八叉树生成的递归函数。**

```csharp
private void GenerateOctree(Bounds boundingBox)
{
    bool containsCollision = CheckCollisionInside(boundingBox);

    if (boundingBox.size.sqrMagnitude <= m_MinVoxelSizeSqr)
    {
        // Reached minimum voxel size
        CreateVoxel(boundingBox, containsCollision);
    }
    else if (containsCollision)
    {
        // Break up octant into 8 pieces to isolate the collision further
        var min = boundingBox.min;
        var center = boundingBox.center;
        var halfHeight = new Vector3(0.0f, 0.0f, boundingBox.size.z *
        0.5f);
        var octantSize = (boundingBox.size / 2.0f);
        var octantHalfSize = octantSize * 0.5f;

        // Bottom row 34
        var octants = new Bounds[8];
        octants[0] = new Bounds(min + octantHalfSize, octantSize);
        octants[1] = new Bounds( new Vector3(center.x, min.y, min.z) +
        octantHalfSize, octantSize);
        octants[2] = new Bounds( new Vector3(min.x, center.y, min.z) +
        octantHalfSize, octantSize);
        octants[3] = new Bounds( new Vector3(center.x, center.y, min.z) +
        octantHalfSize, octantSize);

        // Top row 78
        // 56
        octants[4] = octants[0];
        octants[4].center = (octants[4].center + halfHeight);

        octants[5] = octants[1];
        octants[5].center = (octants[5].center + halfHeight);

        octants[6] = octants[2];
        octants[6].center = (octants[6].center + halfHeight);

        octants[7] = octants[3];
        octants[7].center = (octants[7].center + halfHeight);

        for (int iOctant = 0; iOctant < octants.Length; ++iOctant)
            GenerateOctree(octants[iOctant]);
    }
    else
    {
        ////Fully open space voxel - potentially larger than the minimum
        //// voxel size.
        CreateVoxel(boundingBox, true);
    }
}
```

该函数中的第一个检查是确定所提供的八叉限界的包围区域是否包含任何碰撞。随后它会检查边界是否至少和我们定义的最小体素大小一样小，如果是，则在此位置创建一个开放或封闭体素，并从此处不再进行递归调用。否则，如果包围区域确实包含碰撞，它将细分接下来的八个八叉限界，并对每个递归调用。如果它不包含碰撞，你可以创建一个开放体素，其大小可能介于最小体素和原始种子八叉限界之间，这个特定分支即完成。

此处所做的是标记原始边界内的所有空空间，尽可能使用最大的体素，同时以最小允许体素大小等效的密度标记碰撞。这是一种快速有效的方法，用于确定世界位置占据哪个体素、该体素在八叉树中有哪些连接，以及一个可用于将与体素相关的元数据应用到供NPC查询的地图。

生成过程的下一阶段是剔除完全存在于原始种子边界区域之外的任何体素。如果必须将边界拉伸以适应均匀形状，就可能发生这种情况。任何与边界边缘重叠的体素都将被保留，因此体素空间可以超出原始边界，但只能延伸到与其相交为止。

### 16.4.2 内部测试

在手动放置环境标记触发体积的方法中，关卡设计师将空间标记为室内或室外。现在可以使用体素方法轻松实现这一点，即从每个开放体素发送一系列简单的向上射线投射。

一种相当有效且简单的测试方法是，对每个开放体素，从顶部中心和每个顶部角落向最高处发射一条射线。如果这五条射线中达到一定比例（例如50%）与多边形碰撞，则该体素为室内，或至少是被遮挡不受天空照射。图像16.1描绘了这一过程。

![](img/f4a4f6e4de5338a867590c30638990cf_153_0.png)

图像16.1 测试体素是室内还是室外。

你现在有一个八叉树，可以查询世界位置，并被告知该位置是室内还是室外。

### 16.4.3 标记种子和门户边界

在用于标记房间和区域的简单基于触发的体积方法中，如果要将房间内部标记为厨房，你会拉伸一个触发体积来填充空间，并为该体积设置room:kitchen标签。如前所述，这在开发过程中艺术家修改房间之前没问题，之后设计师就必须跟进这些更改，重建触发体积以匹配。使用体素空间生成，你现在可以通过让设计师仅放置一个标记种子——仅仅是一个世界空间位置——而不是体积，来使这个过程更加健壮。

在生成过程的“在体素空间中传播标记种子”（第四阶段）期间，你定位八叉树边界内放置的每个种子，找到它所在的八叉限界/体素，并用种子标记标记该体素。你可以假设，如果该种子被标记为 room:kitchen，它将放置在厨房内部空间内的开放体素中。现在你在所有连接的开放体素上执行泛洪填充算法，并将每个连接也标记为 room:kitchen。这种泛洪填充例程的明显问题是，它很可能也会从门口泄漏出去，即使由于碰撞层的排序方式而没有泄漏，你可能仍然希望划定厨房空间，以更受控的方式完全隔离标记标记所使用的体素。这就是门户派上用场的地方。

门户边界只是一个体积，可以在关卡设计标记过程中放置，与放置种子同时进行，以封锁入口和出口至

