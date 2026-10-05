
## 7.3 使用 Qiskit 使用 VQE

在本节中，我们将展示如何使用 Qiskit 在模拟器和实际量子硬件上运行 VQE。为了实现这一点，我们将使用一个取自量子化学的问题：确定 `H2`（双氢）分子的能量。我们的第一个子节将致力于定义这个问题。

### 7.3.1 在 Qiskit 中定义分子问题

为了说明如何结合 Qiskit 使用 VQE，我们将考虑一个简单的量子化学问题。假设我们有两个氢原子形成一个 `H2` 分子，并且想要计算它的基态和能量。为此，我们需要获取系统的哈密顿量（Hamiltonian），这与我们习惯的哈密顿量略有不同。我们目前考虑的哈密顿量被称为比特哈密顿量（qubit Hamiltonians），而我们需要描述 `H2` 分子能量的哈密顿量被称为费米哈密顿量（fermionic Hamiltonian）——这个名称来源于涉及费米子，即电子、质子和中子等粒子。

我们不需要深入这种类型哈密顿量计算的所有细节（如果你感兴趣，可以参考 Sharkey 和 Chancé 的书中 [57] 的第 4 章），因为所有必要的方法都在 Qiskit Nature 包中提供。此外，过程并不涉及量子计算机；一切都是在经典上计算和估计的。

为了使用 Qiskit 获取双氢分子的费米哈密顿量，我们需要安装 Qiskit Nature 包以及 `pyscf` 库，后者用于计算化学计算（请参阅附录 D“安装工具”获取安装程序，并注意我们将使用该包的 0.4.5 版本）。

然后，我们可以执行以下指令：

```python
from qiskit_nature.drivers import Molecule
from qiskit_nature.drivers.second_quantization import \
    ElectronicStructureMoleDriver, ElectronicStructureDriverType
from qiskit_nature.problems.second_quantization import \
    ElectronicStructureProblem

mol = Molecule(geometry=[['H', [0., 0., -0.37]], ['H', [0., 0., 0.37]]])
driver = ElectronicStructureMoleDriver(mol, basis='sto3',
    driver_type=ElectronicStructureDriverType.SCF)
problem = ElectronicStructureProblem(driver)
secqop = problem.second_qops
print(secqop[0])
```

在这里，我们定义了一个由两个位于 `(0, 0, -0.37)` 和 `(0, 0, 0.37)`（单位为埃）的原子组成的分子，这接近于该分子的平衡态。我们使用了默认参数，例如分子是不带电的。然后，我们定义了一个电子结构问题；即我们要求 `pyscf` 库计算考虑了两个原子不同构型的费米哈密顿量。这是通过二量化完成的。当我们运行这段代码时，我们得到了以下结果：

```
Fermionic Operator
register=4, terms=36
-1.2533097866459775 (* _0)
+ 0.4750668848721725 (* _1)
-1.2533097866459775 (* _2)
+ 0.4750668848721725 (* _3)
+ 0.3373779634072241 (* _00)
```

### 使用 Qiskit 使用 VQE

这是费米哈密顿量的截断视图，涉及到产生和湮灭算符，描述电子如何从一个轨道移动到另一个轨道（更多细节可以参考 Sharkey 和 Chancé 书 [57] 的第 4 章）。这些都很好，但我们无法在量子计算机上使用它。为此，我们需要将费米哈密顿量转换为比特哈密顿量，涉及到泡利门。实现此点有多种方法。最流行的方法之一是 Jordan-Wigner 变换（再次说明，详细解释请参见 Sharkey 和 Chancé 的书 [57]），我们可以在 Qiskit 中通过以下指令来使用这种变换：

```python
from qiskit.nature.converters.second_quantization import QubitConverter
from qiskit.nature.mappers.second_quantization import JordanWignerMapper

qconverter = QubitConverter(JordanWignerMapper())
qhamiltonian = qconverter.convert(secqop[0])
print("Qubit Hamiltonian")
print(qhamiltonian)
```

运行此代码后，我们将得到以下输出：

```
Qubit Hamiltonian
-0.8121706072487122 (* IIII)
+ 0.1741282644776915 (* IIIZ)
- 0.2234315369081348 (* IIZI)
+ 0.1741282644776915 (* IZII)
- 0.2234315369081348 (* ZIII)
+ 0.12062523483390415 (* IIZZ)
+ 0.16688988170361205 (* IZZZ)
+ 0.0453002866721725 (* IIII)
```

### 7.3.2 使用哈密顿量使用 VQE

现在我们选择了基态，我们将看到如何使用 VQE 找到基态。为了开始，我们需要哈密顿量；即我们定义变分。例如，我们可以使用 Qiskit 的以下指令：

```python
from qiskit.algorithms import VQE
from qiskit import Aer
from qiskit.utils import QuantumInstance, algorithm_globals
import numpy as np
from qiskit.algorithms.optimizers import COBYLA

seed = 1234
np.random.seed(seed)
algorithm_globals.random_seed = seed
optimizer = COBYLA()
initial_point = np.random.random(ansatz.num_parameters)
quantum_instance = QuantumInstance(Aer.get_backend('aer_simulator'))
vqe = VQE(ansatz, optimizer,
    initial_point=initial_point,
    quantum_instance=quantum_instance)
```

# 在 Qiskit 中使用 VQE

```
-6.5083366e-07-1.04178617e-06j, -6.40877389e-06-1.0499914e-05j,
-1.33988128e-06+3.630921e-07j, 1.0844145e-05+7.6175332e-08,
1.04578392e-01+4.15432635e-02j, -5.89251512e-06+4.4706741e-06j,
-1.01179796e-09+1.8561927e-09j, 5.57085679e-05+5.29593190e-05j,
1.47630244e-04+3.0035704e-08j, 1.51330159e-10+9.4186930e-10j
```

```python
'eigenvalue': (-1.8523814170914+0),
'optimal_circuit': None,
'optimal_parameters': {
    ParameterVectorElement([0]): -0.1026398397273155,
    ParameterVectorElement([6]): -0.1315422350421972,
    ParameterVectorElement([8]): 3.141646843294864,
    ParameterVectorElement([13]): 0.624698762927032,
    ParameterVectorElement([9]): 2.467411407579344e-05,
    ParameterVectorElement([14]): -0.1138708129752642,
    ParameterVectorElement([15]): 2.52525490939928,
    ParameterVectorElement([12]): 1.844627924674344,
    ParameterVectorElement([11]): -0.00117894555876669843,
    ParameterVectorElement([10]): 2.7179451047891577e-06,
    ParameterVectorElement([3]): 3.1403232328683655,
    ParameterVectorElement([1]): 9.061128731358724e-06,
    ParameterVectorElement([2]): 3.141570826032646,
    ParameterVectorElement([0]): -0.22553235232529397,
    ParameterVectorElement([5]): 2.151321484244912,
    ParameterVectorElement([4]): 1.7045601611970793
},
'optimal_point': array([-2.2553235253e-05, 9.061128732e-06,
    3.141507833e+00, 3.14032324e+00,
    2.15132148e+00, -2.15342351e-01, -1.02639484e-01,
    3.14164684e+00, 2.46741140e-05, 2.71794510e-06, -1.18794556e-03,
    1.84462729e+00, 6.42698763e-01, -1.13807183e-01, 2.52525491e+00]),
'optimal_value': -1.8523881417094914
```
