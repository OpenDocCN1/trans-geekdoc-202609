
## 计算模型建议

考虑到文献中一般的思路，一些计算模型可以被视为平衡建模结构。在此背景下，第一个模型建议可以采用与旅游活动相关的代理的形式。这样的代理可以定义为：

```
A[ij] = G(a) + T(a) + C
```
(10–17)

其中，多个代理（`A`）可与行为者 `i` 的活动 `j` 相关联，对应的温室气体排放量可通过 `G` 模型计算，而技术排放量则通过 `T` 计算，并且诸如天气事件、温度、需求或经济状况等常数可以根据目标活动以及位置而被包含或排除。这样的常数在另一个模型下定义为 `C`。该模型可以与其他模型集成，定义为财务因素（`F`）和旅行因素（`T`）：

```
F(x[1],x[2],x[3],...,x[n]) = (x[1],x[2],x[3...]+C[1])/(x[10],x[11],x[n-m...]+C[2])
```
(10–18)

```
T(PKT,VKT) = E(PKT,VKT) + C[3]
```
(10–19)

```
A[ij] = G(a) + T(a) + (C+M(F,T))
```
(10–20)

作为 `F` 和 `T` 作为对代理 `A` 的已知常数的有效因子的附加模型被包含在内，它们也采用了一些与直接温室气体排放相关的已知模型。每个代理都应被视为旅游场景中的行为者。这些行为者可以是游客、机构、技术工具（消耗能源的软件/硬件）、ICT 组件，或任何其他与气候效应以及旅游流内部的活动要素相互作用的行为者。除了这些受旅游活动控制的代理之外，还有一些其他代理可以与气候参数相连，例如特定的天气事件（如降雨、降雪和极端温度）或影响旅游活动的已知速率。因此，可以进行代理之间的平衡互动，就像与旅游和气候相关的不同代理正在构建一个顶层系统一样。

另一种模型视图可以是与特定活动相连的更简单方程的组合，例如：

```
Travel = Carbon * distance * time * additional_emission_parameters
```
(10–21)

```
Software_Use = Technology_Carbon(Time) * time * [Carbon(incoming)+Carbon(outgoing)]
```
(10–22)

```
Room_Use = Light(time) + Technology_Carbon(Time) + additional_emission_parameters
```
(10–23)

```
Location_Travel = Carbon * distance * time * location − based_emission_parameters
```
(10–24)

```
Country_Emission = Models on emission measurement + Location_Emission(X)
```
(10–25)
