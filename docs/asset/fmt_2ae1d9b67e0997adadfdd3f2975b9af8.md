
该模型用于交互式生成并比较三种不同的网络生成器，涉及生成的网络属性，包括介数中心性、聚类系数、密度和平均最短距离。这些网络生成器分别是 Kleinberg 的小世界模型、Barabasi 和 Barabasi 的无标度网络生成器以及 Epstein 和 Wang 的随机网络生成器。所有生成的网络具有相同数量的顶点。计算所有生成的网络属性后，对上述模型进行比较，以找出这些模型之间的主要差异。

```
;;;;; Code;
turtles-own {
  explored? ;; this is used to mark turtles we have already visited
  node-clustering-coefficient
  distance-from-other ;; list of distances of this node from other turtles
}
links-own{
  rewired? ;; keeps track of whether the link has been rewired or not
}
globals
  component-size ;; number of turtles explored so far in the current component
  giant-component-size ;; number of turtles in the giant component
  giant-start-node ;; node from where we started the giant component
  clustering-coefficient ;; the clustering coefficient of the network; this is the
    ;; average of clustering coefficients of all turtles
  average-path-length ;; average path length of the network
  infinity
  connected? ;; are all nodes connected
  number-rewired ;; number of edges that have been rewired. used for plots.
}
;;;;;;;;;;;;;;;;;; Setup Procedures ;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;
to setup
  clear-all
  set-default-shape turtles "circle"
  set infinity 9999
```

```
go
if Network? = "Random Network" [
;; if the below condition is true then we have a fully connected network and
need to stop
if (2 * count links) >= (count turtles) * (count turtles - 1)) [
display
user-message "fully connected. No more edges can be added."
stop
]
-edge
find-all-components
color-giant-component
ask links [set color [color] of endl] ;; recolor all
nif Network? = "Small World Network" [
rewire-all
]
if Network? = "Scale Free Network" [
ask links [set color gray]
make-nodes find-partner
]

do-calculations
tick
if Network? = "Random Network" [if giant-component-size = num-nodes [stop]]
 Network? = "Small World Network" [if giant-component-size = num-nodes [stop]]
 Network? = "Scale Free Network" [if giant-component-size = num-nodes [stop]]
```

```
100 Appendix
```

```logo
let node2 one-of turtles
let node-count count turtles
;; 初始化距离列表
while [i < node-count]
[
  set j 0
  while [j < node-count]
  [
    set node1 turtle i
    set node2 turtle j
    ;; 节点到自身的距离为 0
    ifelse i = j
    [
      ask node [
        set distance-from-other-turtles lput 0 distance-from-other-turtles
      ]
    ]
    ;; 节点到邻居的距离为 1
    ifelse [ link-neighbor? node ] of node2
    ask node [
      set distance-from-other-turtles lput 1 distance-from-other-turtles
    ]
    ;; 到其他人的距离为无穷大
    [
      ask node [
        set distance-from-other-turtles lput infinity distance-from-other-turtles
      ]
    ]
    set j j + 1
  ]
set i i + 1
]
set i 0
set j 0
let dummy 0
while [k < node-count]
[
  set i 0
  while [i < node-count]
  [
    set j 0
    while [j < node-count]
    [
      ;; 通过第 k 个节点的替代路径长度
      set dummy ( (item k [distance-from-other-turtles] of turtle i) +
      (item j [distance-from-other-turtles] of turtle k))
      ;; 备用路径更短？
      if dummy < (item j [distance-from-other-turtles] of turtle i)
      [
        ask turtle i [
          set distance-from-other-turtles replace- j
        ]
      ]
      distance-from-other-turtles dummy
    ]
    set j += 1
  }
  set i += 1
}
set k += 1
]
end
```

```logo
;; 创建一个新的晶格
to wire-them
;; 遍历所有龟
let n 0
while [n < count turtles]
{
  ;; 与后两个邻居建立边
  ;; 这使得晶格的平均度数为 4
  make-edge turtle n
  turtles ((n + 1) mod count turtles)
  make-edge turtle n
  turtles ((n + 2) mod count turtles)
}
end
```

```logo
;; 连接两只龟
make-edge [node2]
ask model [
  create-link-node2
  set connected? false
]
end

to-do-calculations
set connected? true

find-lengths

let num-connected-pairs sum [length remove infinity (remove 0
distance-from-other-turtles)] of turtles

ifelse num-connected-pairs != (count turtles * (count turtles - 1))
{
  set average-path-length infinity
  ;; 报告网络未连通
  set connected? false
}

set average-path-length [sum distance-from-other-turtles] of turtles
(num-connected-pairs)
{
  find-clustering-coefficient
}
end
```

```logo
to rewire-all
set connected? false
while [not connected]?
{
  ;; 旧的晶格，重置邻居并创建新晶格
  ask links [die]
  wire-them
  set number-rewired 0
  ask links [
    ;; 是否要重新布连？
    if (random-float 1) < rewiring-probability
    [
      ;; "a" 保持不变
      let node endl
      ;; 如果 "a" 没有连接到所有人
      if [count link-neighbors] of endl < count turtles - 1
      [
        let target one-of turtles not in link-neighbors of endl
        die
        make-edge endl target
      ]
    ]
  ]
}
endto wire-them
;; 遍历所有龟
let n 0
while [n < count turtles]
{
  ;; 与后两个邻居建立边
  ;; 这将形成一个平均度数为 4 的晶格
  make-edge turtle n
  turtles ((n + 1) mod count turtles)
  make-edge turtle n
  turtles ((n + 2) mod count turtles)
}
end
```

```logo
;; 连接两只龟
make-edge [node2]
ask model [
  create-link-node2
  set connected? false
]
end

to-do-calculations
set connected? true

find-lengths

let num-connected-pairs sum [length remove infinity (remove 0
distance-from-other-turtles)] of turtles

ifelse num-connected-pairs != (count turtles * (count turtles - 1))
{
  set average-path-length infinity
  ;; 报告网络未连通
  set connected? false
}

set average-path-length [sum distance-from-other-turtles] of turtles
(num-connected-pairs)
{
  find-clustering-coefficient
}
end
```

```logo
to rewire-all
set connected? false
while [not connected]?
{
  ;; 旧的晶格，重置邻居并创建新晶格
  ask links [die]
  wire-them
  set number-rewired 0
  ask links [
    ;; 是否要重新布连？
    if (random-float 1) < rewiring-probability
    [
      ;; "a" 保持不变
      let node endl
      ;; 如果 "a" 没有连接到所有人
      if [count link-neighbors] of endl < count turtles - 1
      [
        let target one-of turtles not in link-neighbors of endl
        die
        make-edge endl target
      ]
    ]
  ]
}
end
```

*(注：由于提供的原始文本后半部分存在逻辑重复和格式乱码，我已根据前文逻辑修复并翻译了核心描述部分，以确保文档的专业性)*

## A1 什么是什么？

在网络中，“连通分量”是指直接或间接连接的节点组。如果一个网络拥有“巨型连通分量”，意味着几乎每个节点都可以到达其他所有节点。

## A2 它是如何工作的？

初始时只有节点，之间没有连接（边）。每一步，我们随机选择两个没有直接连接的节点并在它们之间建立一条边。所有连接产生的概率完全相同。

随着模型运行，会形成链状的“连通分量”，这些分量内部成员之间可以直接或间接连接。如果在不同连通分量之间建立了边，这两个分量就会合并为一个。在任何时刻，成员最多的分量就是“巨型”连通分量，并被涂为红色（如果并列，我们会随机选择一个颜色）。

## A3 如何使用？

`NUM-NODES` 滑块控制节点数量。选择一个大小并点击 `SETUP`。点击 `GO` 按钮添加一条新边。要连续添加边，请点击 `GO`。随着模型运行，节点和边会尝试排列在易于观察的布局中，但这会让模型运行变慢。为了更快获得结果，请关闭 `LAYOUT?` 开关。`REDO` 按钮会持续运行布局以改进布局。

## A4 注意事项

图表的 y 轴显示包含巨型分量中的节点比例。x 轴显示每个节点的平均连接数。图上的垂直线显示了平均连接数等于 1 的位置。在此，巨型分量的增长速率发生了什么变化？

## A5 尝试

让模型运行到结束。“巨型连通分量”名副其实吗？

再次运行模型，这次慢速，一步一步进行。观察分量的增长。当图表最陡峭时发生了什么？

## A.7 网络概念

连通分量的识别是使用一种名为“深度优先搜索”的标准算法完成的。“深度优先”意味着算法首先深入连接的一个分支，沿着路径追踪到末端。对于给定的节点，它在移动到下一个邻居之前，会先探索其邻居的邻居（然后它们的邻居等）。该算法是递归的，因此从特定起始节点的所有可达节点最终会被探索。由于我们需要找到每个可达节点，而且发现它们的顺序并不重要，使用“广度优先搜索”等算法效果同样。我们选择深度优先搜索是因为它的代码最简单。

节点的位置由“弹簧”方法决定，该方法在偏好附着模型中进一步描述。

## A.8 NetLogo 特性

节点和边都是乌龟（`turtles`）。边的乌龟具有“line”形状。边乌龟的“size”变量用于使边的长度正确。

该模型大量使用了列表。每个节点都维护一个邻居节点列表。列表在识别分量的过程中也被使用了。

## A.9 相关模型

请查看模型库中“网络”部分的其他模型，例如偏好附着。

另另“代码示例”部分中的网络示例。

## A.10 致谢与参考文献

作者：

- Md Shapon Talukder

- Venkata Saaketh Gummalla

- Gautam Bhavaraju

附录 113

@@@@ndefault

true

0

Polygon -7500403 true 150 40 250 150 205 260 250

airplane

true

0

Polygon -7500403 true 150 0 135 15 120 60 120 105 165 15 195 220 180

135 240 105 270 120 285 170 285 210 270 165 240 180 180 195

285 165 180 105 60 60 165

arrow

true

0

Polygon -7500403 true 150 0 150 285 225 285 105 150 105 150 293 293 195 195 300 150

box

false

0

Polygon -7500403 true 150 135 175 15 150 285 135

Polygon -7500403 true 150 75 75 225 150 285 150 135

Line -16772216 false 285 130 135

Line -16772216 false 135 15 75

Line -16772216 false 135 35 285

bug

true

0

Circle -7500403 true 96 182 108

Circle -7500403 true 110 127 80

Circle -7500403 true 110 75 80

Line -7500403 true 100 80 30

Line -7500403 true 150 100 220 30

butterfly

true

0

Polygon -7500403 true 150 165 209 199 225 225 225 195 270 165 255 240

Polygon -7500403 true 150 65 89 198 75 225 255 255 270 135 275 240

Polygon -7500403 true 140 138 100 155 55 90 95 20 100 135 280 40 95 194 163
