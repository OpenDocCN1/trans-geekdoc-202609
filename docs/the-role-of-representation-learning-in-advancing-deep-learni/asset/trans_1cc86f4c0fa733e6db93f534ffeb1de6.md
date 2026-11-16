

## 表 E.5.42：列出了每个谜题的动作空间及其基数。动作按原始谜题集合 C 代码中的名称列出。

| 谜题 | 基数 | 动作空间 |
| :--- | :--- | :--- |
| 黑盒 | 5 | UP, DOWN, LEFT, RIGHT, SELECT |
| 桥梁 | 5 | UP, DOWN, LEFT, RIGHT, SELECT |
| 立方体 | 4 | UP, DOWN, LEFT, RIGHT |
| 多米诺 | 5 | UP, DOWN, LEFT, RIGHT, SELECT |
| 十五数码 | 4 | UP, DOWN, LEFT, RIGHT |
| 填充 | 13 | UP, DOWN, LEFT, RIGHT, 1, 2, 3, 4, 5, 6, 7, 8, 9 |
| 翻转 | 5 | UP, DOWN, LEFT, RIGHT, SELECT |
| 涂色 | 5 | UP, DOWN, LEFT, RIGHT, SELECT |
| 星系 | 5 | UP, DOWN, LEFT, RIGHT, SELECT |
| 猜谜 | 5 | UP, DOWN, LEFT, RIGHT, SELECT |
| 惯性 | 9 | 1, 2, 3, 4, 6, 7, 8, 9, UNDO |
| 基肯 | 14 | UP, DOWN, LEFT, RIGHT, SELECT2, 1, 2, 3, 4, 5, 6, 7, 8, 9 |
| 点灯 | 5 | UP, DOWN, LEFT, RIGHT, SELECT |
| 循环 | 6 | UP, DOWN, LEFT, RIGHT, SELECT, SELECT2 |
| 磁铁 | 6 | UP, DOWN, LEFT, RIGHT, SELECT, SELECT2 |
| 地图 | 5 | UP, DOWN, LEFT, RIGHT, SELECT |
| 扫雷 | 7 | UP, DOWN, LEFT, RIGHT, SELECT, SELECT2, UNDO |
| 马赛克 | 6 | UP, DOWN, LEFT, RIGHT, SELECT, SELECT2 |
| 网络 | 5 | UP, DOWN, LEFT, RIGHT, SELECT |
| 网格滑块 | 5 | UP, DOWN, LEFT, RIGHT, SELECT |
| 栅栏 | 5 | UP, DOWN, LEFT, RIGHT, CTRL |
| 图案 | 6 | UP, DOWN, LEFT, RIGHT, SELECT, SELECT2 |
| 珍珠 | 5 | UP, DOWN, LEFT, RIGHT, SELECT |
| 钉子 | 6 | UP, DOWN, LEFT, RIGHT, SELECT, UNDO |
| 范围 | 5 | UP, DOWN, LEFT, RIGHT, SELECT |
| 矩形 | 5 | UP, DOWN, LEFT, RIGHT, SELECT |
| 同类消除 | 6 | UP, DOWN, LEFT, RIGHT, SELECT, UNDO |
| 路标 | 6 | UP, DOWN, LEFT, RIGHT, SELECT, SELECT2 |
| 单数 | 6 | UP, DOWN, LEFT, RIGHT, SELECT, SELECT2 |
| 十六数码 | 6 | UP, DOWN, LEFT, RIGHT, SELECT, SELECT2 |
| 斜线 | 6 | UP, DOWN, LEFT, RIGHT, SELECT, SELECT2 |
| 数独 | 13 | UP, DOWN, LEFT, RIGHT, 1, 2, 3, 4, 5, 6, 7, 8, 9 |
| 帐篷 | 6 | UP, DOWN, LEFT, RIGHT, SELECT, SELECT2 |
| 塔 | 14 | UP, DOWN, LEFT, RIGHT, SELECT2, 1, 2, 3, 4, 5, 6, 7, 8, 9 |
| 轨迹 | 5 | UP, DOWN, LEFT, RIGHT, SELECT |
| 旋转 | 6 | UP, DOWN, LEFT, RIGHT, SELECT, SELECT2 |
| 不死 | 8 | UP, DOWN, LEFT, RIGHT, SELECT2, 1, 2, 3 |
| 不等式 | 13 | UP, DOWN, LEFT, RIGHT, 1, 2, 3, 4, 5, 6, 7, 8, 9 |
| 不规则 | 6 | UP, DOWN, LEFT, RIGHT, SELECT, SELECT2 |
| 解缠 | 5 | UP, DOWN, LEFT, RIGHT, SELECT |

## E.5.2 可选参数

我们在表 E.5.43 中显示了所有受支持谜题的可选参数。如果在初始化时未提供任何参数，则谜题生成过程将使用一组默认参数。

**表 E.5.43：** 对于每个谜题，均展示并说明了用户可提供的所有可选参数。如适用，我们还会给出变量所需的数据类型（例如 `int` 或 `char`）。对于仅接受少数几个选项的参数（例如难度），可接受的值及其对应说明将以花括号形式给出。例如：难度参数列为 d{int}，允许的值为 {0 = 简单, 1 = 中等, 2 = 困难}。在此示例中，选择中等难度对应 d1。

| 谜题 | 示例 | 参数 | 描述 | 最优步数上界 |
| :--- | :--- | :--- | :--- | :--- |
| 黑盒 | `6b8SaS55` | `w{int}`<br>`h{int}`<br>`n{int}`<br>`M{int}` | 网格宽度<br>网格高度<br>球的最小数量<br>球的最大数量 | (w · h + w + h + 1)<br>· (w + 2) · (h + 2) |
| 桥梁 | `7x7l5e2x2d0` | `{int}x{int}`<br>`i{int}`<br>`e{int}`<br>`n{int}`<br>`d{int}` | 网格宽度 ×<br>网格高度<br>岛屿方格百分比<br>扩展因子<br>每个方向的最大桥梁数<br>难度 {<br>0 = 简单<br>1 = 中等<br>2 = 困难} | 3 · w · h · (w + h + 8) |
| 立方体 | `c4x4` | `{char}`<br>`{int}x{int}` | 类型 { c = 立方体,<br>t = 四面体,<br>o = 八面体,<br>d = 十二面体,<br>i = 二十面体 }<br>网格宽度 × 网格高度 | w · h · F<br>F = 立体的面数 |
| 多米诺 | `6db` | `{int}`<br>`d{char}` | 骨牌的最大数量<br>难度 {<br>t = 平凡,<br>b = 基础,<br>h = 困难,<br>e = 极端,<br>a = 含糊 } | ½ (w² + 3w + 2)<br>· (4√(w² + 3w + 2) + 1) |
| 十五数码 | `4x4` | `{int}x{int}` | 网格宽度 × 网格高度 | (w · h)⁴ |
| 填充 | `13x9` | `{int}x{int}` | 网格宽度 × 网格高度 | (w · h) · (w + h + 1) |
| 翻转 | 5x5c | {int}x{int}<br>{char} | 网格宽度 × 网格高度<br>类型 { c = 十字, r = 随机 } | (w · h) · (w + h + 1) |
| 涂色 | 12x12c6a5 | {int}x{int}<br>c{int}<br>u{int} | 网格宽度 × 网格高度<br>c{int} = 颜色数量<br>u{int} = 允许的额外移动次数（高于求解器的最小值） | (w · h) · (w + h + 1) |
| 星系 | 7x7dn | {int}x{int}<br>d{char} | 网格宽度 × 网格高度<br>难度 {n = 普通, u = 不合理} | (2 · w · h - w - h) · (2 · w + 2 · h + 1) |
| 猜谜 | c6p4g10bnm | c{int}<br>p{int}<br>g{int}<br>{char}<br>{char} | 颜色数量<br>p{int} = 每次猜测的谜题数量<br>g{int} = 最大猜测次数<br>{char} = 允许空白 {B = 是, N = 否}<br>{char} = 允许重复 {M = 否, m = 是} | (p + 1) · g · (c + p) |
| 惯性 | 10x8 | {int}x{int} | 网格宽度 × 网格高度 | 0.2 · w² · h² |
| 基肯 | 6dn | {int} 网格大小<br>d{char}<br>{char} | 网格大小<br>难度 {e = 简单, n = 普通, h = 困难, x = 极端, u = 不合理}<br>(可选) 仅乘法 {m = 是} | (2 · w + 1) · w² |
| 点灯 | 7x7b20s4d0 | {int}x{int}<br>b{int}<br>s{int}<br>d{int} | 网格宽度 × 网格高度<br>黑色方格百分比<br>b{int} = 方块对称性 {0 = 无, 1 = 二向轴对称, 2 = 二向旋转对称, 3 = 四向对称},<br>d{int} = 难度 {0 = 简单, 1 = 棘手, 2 = 困难} | ½ · (w + h + 1) · (w · h + 1) |
| 循环 | 10x10:12dh | {int}x{int} | 网格宽度 × 网格高度<br>类型 {0 = 正方形, 1 = 三角形, 2 = 菱形, 3 = 蜂窝, 3 = 扭正方形, 4 = 开罗, 5 = 大六边形, 6 = 八边形, 7 = 鸢形, 8 = 花朵, 9 = 十二边形, 10 = 大十二边形, 11 = 彭罗斯 (鸢形/镖形), 12 = 彭罗斯 (菱形), 13 = 大六边形, 14 = 镰刀形, 15 = 指南针十二边形, 16 = 帽子} | (2·w·h+1)·3·(w·h)² |
| 循环 | | t{char} | 难度 (e = 简单, n = 普通, t = 棘手, h = 困难) | |
| 磁铁 | 6x5dS | {int}x{int} | 网格宽度 × 网格高度 | w·h·(w + h + 2) |
| 磁铁 | | d{char} | 难度 (e = 简单, t = 棘手) | |
| 磁铁 | | {char} | (可选条形线索 {S = 是}) | |
| 地图 | 20x15n30dn | {int}x{int} | 网格宽度 × 网格高度<br>区域数量 | 2 · n · (1 + w + h) |
| 地图 | | d{char} | 难度 (e = 简单, n = 普通, h = 困难, u = 无法回答) | |
| 扫雷 | 9x9n10 | {int}x{int} | 网格宽度 × 网格高度<br>地雷数量 | w·h·(w + h + 1) |
| 扫雷 | | p{char} | (可选) 可解性 {a = 否} | |
| 马赛克 | 10x10n0 | {int}x{int} | 网格宽度 × 网格高度<br>(可选) 激进生成 {h0 = 否} | w·h·(w·h + 1) |
| 马赛克 | | {str} | | |
| 网络 | 5x5b0.5 | {int}x{int} | 网格宽度 × 网格高度<br>(可选) 墙壁环绕 {w = 是} | w · h · (w + h + 3) |
| 网络 | | b{float} | 障碍概率区间：[0, 1] | |
| 网络 | | {char} | (可选) 确保唯一解 {a = 否} | |
| 网格滑块 | 4x4bins2 | {int}x{int} | 网格宽度 × 网格高度<br>(可选) 墙壁环绕 {w = 是} | 2 · w · h · (w + h - 1) |
| 网格滑块 | | b{float} | 障碍概率区间：[0, 1] | |
| 网格滑块 | | n{int} | (可选) 洗牌移动次数 | |
| 栅栏 | 5x5n5 | {int}x{int} | 网格宽度 × 网格高度<br>区域大小 | (2 · w · h - w - h) · (w + h + 3) |
| 图案 | 15x15 | {int}x{int} | 网格宽度 × 网格高度 | w · h · (w + h + 1) |
| 珍珠 | 8x8dn | {int}x{int} | 网格宽度 × 网格高度<br>难度 {e = 简单, t = 棘手}<br>允许可解 {n = 是} | w · h · (w + h + 2) |
| 珍珠 | | d{char} | | |
| 珍珠 | | {char} | | |
| 钉子 | 7x7cross | {int}x{int} | 网格宽度 × 网格高度<br>类型 {十字, 八边形, 随机} | w · h · (w + h + 2) |
| 钉子 | | {str} | | |
| 范围 | 9x6 | {int}x{int} | 网格宽度 × 网格高度 | w · h · (w + h + 1) |
| 矩形 | 7x7e4 | {int}x{int} | 网格宽度 × 网格高度<br>扩展因子 | 2 · w · h · (w + h + 1) |
| 矩形 | | e{int} | | |
| 矩形 | | {char} | 解唯一 {a = 否} | |
| 同类消除 | 5x5c3e2 | {int}x{int} | 网格宽度 × 网格高度<br>颜色数量 | w · h · (w + h + 2) |
| 同类消除 | | c{int} | | |
| 同类消除 | | s{int} | 计分系统 {1 = (n - 1)^2, 2 = (n - 2)^2} | |
| 同类消除 | | {char} | (可选) 确保可解性 {r = 否} | |

