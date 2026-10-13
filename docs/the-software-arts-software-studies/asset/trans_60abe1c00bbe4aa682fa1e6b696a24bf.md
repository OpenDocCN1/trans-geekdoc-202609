

# Abelson、Sussman 和 Sussman 的教科书

Abelson、Sussman 和 Sussman 的教科书在计算机科学界广为人知，以至于它经常被称为其首字母缩写 `SICP`。`SICP` 中的编程示例使用 Scheme 编程语言。为了本书的目的，我选取了其中的一个示例，并将其从 Scheme 翻译成了 JavaScript，以便可以使用任何现代网页浏览器进行检查（因为 JavaScript 不同于 Scheme，在如今几乎所有的浏览器中都得到原生支持）。我将要讨论的示例是将逻辑翻译成软件。

## 一个逻辑电路模拟器

考虑电路设计的问题。设计师需要一种在将设计提交给硬件之前进行“草拟”的方法，通常这种方法就是软件。首先，使用软件模拟器设计电路，然后在芯片材料中最终确定之前对其进行改进和调试。几乎每种计算机编程语言都原生支持 AND、OR 和 NOT 这些布尔运算符，但对于电路设计师来说这还不够，因为前面讨论的所有时序问题：电很快但不是瞬间到达的，因此任何电路模拟器都必须包含某种概念，说明电流从 a 到 b、从逻辑门的输入到其输出等需要多长时间。

因此，电路模拟器必须具有定义导线、逻辑门以及导线如何将门连接在一起的方法；此外，模拟器必须提供一种方法来跟踪电流通过导线和门的流向。我的 JavaScript 程序的完整文本可以在本书的网站上找到。^[52](#chapter_5.xhtml#chapter5-52) 在接下来的页面中，我将主要关注电路模拟器提供的一些抽象，而较少关注实现模拟器的 JavaScript 代码部分。

下面是一小段代码，它设置模拟器，定义一个 OR 门以及通向门内外的导线，在通向门的导线上施加电流，然后运行模拟器。代码中的注释以 "//" 开头。

```javascript
// Create an instance of a circuit simulator, call it "cs."
var cs = makeCircuitSimulator();

// Create an instance of an agenda, call it "ag."
var ag = cs.getAgenda();

// Set up and run an OR gate.
// First define three wires: two input wires (a and b) and one output (c).
var a = cs.makeWire();
var b = cs.makeWire();
var c = cs.makeWire();

// Introduce a new instance of an OR gate into the simulator and attach the
// input and output wires to the gate.
cs.orGate(a, b, c);

// Put no current on the input wire a by setting its value to 0.
a.setValue(0);

// Put a current on the input wire b by setting its value to 1.
b.setValue(1);

// Now, put "probes" on all of the wires so that at every time step, the
// simulator prints out whether or not there is a current on each of the wires.
a.probe("wire a");
b.probe("wire b");
c.probe("wire c");

// Finally, turn on the simulator by propagating, via the agenda, the currents
// (i.e., the values 1 and 0) through the circuit.
ag.propagate();
```

当执行 `propagate()` 命令时，“探针”将向 JavaScript 控制台打印以下内容：

```
value for wire a @ time 0 is 0
value for wire b @ time 0 is 1
value for wire c @ time 0 is 0
value for wire c @ time 5 is 1
```

请注意，在模拟开始时（时间 0），导线上的电流要么是定义好的（`a` 为 0；`b` 为 1），要么是预期的：`c` 为 0，因为 OR 门的输出尚未确定。稍后（时间 5），`c` 导线有了电流，因为正如前面讨论的，如果任一输入或两个输入均为 1，OR 门的输出就是 1。

在实现电路模拟器的代码中，可以规定电流通过给定类型的逻辑门需要多少个时间增量。在本例中，我决定 OR 门的延迟为 5 个增量，AND 门为 3 个，NOT 门（即反相器）也为 3 个。这就是为什么 OR 门输出导线上的探针直到时间 5 才报告值为 1 的原因。虽然这些延迟可以在模拟器代码中轻松更改，但请注意，延迟之间的比率（5:3:3）需要与在硬件电路中可能观察到的延迟比率相对应——如果模拟旨在类似于硬件的性能。

在这个电路模拟器的翻译版本中，我没有提供给导线分配延迟的方法。所有导线都被理想化为可以零延迟地传播电流。显然，可以修改模拟器以允许导线被分配延迟，就像为门所做的那样。

在编写这样的模拟器时，需要做出一系列简化决策。在这里，导线被定义为瞬时传播电流，门不需要电源，门不产生热量，布局问题完全被忽略了。

布局是电路物理生产中的一个主要问题：门需要放置在一个平面上（通常是一小块硅片），然后用导线连接在一起，使得导线不重叠，并且考虑到门的延迟，以便输入在应该到达时到达，输出在需要时被记录。

时序问题（称为“竞态条件”）加剧了布局问题。想象一下，一个非常复杂的电路的电流和一个非常简单的电路的输出被用作 AND 门的输入。由于复杂电路中门的所有延迟与简单电路中少量的延迟相比，复杂电路将在简单电路停止工作很久之后才输出其结果。因此，要么必须设计某种方法来延迟简单电路输出的到达——使其与复杂电路的输出同步——要么延迟读取依赖于这两个输入的 AND 门的输出，直到复杂电路完成工作。

Abelson、Sussman 和 Sussman 称他们的方法——以专用编程语言的设计和实现为中心——为“元语言抽象”。^[53](#chapter_5.xhtml#chapter5-53) 电路模拟器就是这种方法的一个例子。为每个感兴趣的对象或主题设计一种抽象——在本例中为 `orGate`、`andGate`、`inverter`、`wire` 和 `current`（仅表示为 1 或 0）。为每个感兴趣的过程定义一种抽象；在本例中，agenda（议程）是定义电流如何通过导线和门传播的抽象。然后，定义一种将抽象组合在一起的方法。在本例中，方法是 JavaScript 的“函数”和 JavaScript 中称为“对象”的数据结构定义。这些抽象和组合方法共同构成了一种用于设计电路的专用编程语言。我们可以将这个电路模拟器理解为 JavaScript 语言的一个专用子集。

下面是这种专用语言在使用中的另一个简单示例。它通过将同一根导线连接到反相器的输入和输出来定义一个振荡器，即一个时钟。

```javascript
var cs = makeCircuitSimulator();
var ag = cs.getAgenda();
var a = cs.makeWire();
cs.inverter(a, a); // The wire "a" is both the inverter's input and output
a.setValue(1);
a.probe("wire a");
ag.propagate();
```

模拟器输出以下跟踪信息。请记住，我已将反相器的延迟设置为 3 个时间单位。

```
value for wire a @ time 0 is 1
value for wire a @ time 3 is 0
value for wire a @ time 6 is 1
value for wire a @ time 9 is 0
```

