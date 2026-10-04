

`echo "deb [arch=amd64] http://storage.googleapis.com/bazel-apt stable jdk1.8" | sudo tee /etc/apt/sources.list.d/bazel.list`

`curl https://bazel.build/bazel-release.pub.gpg | sudo apt-key add -`

之后，你可以使用以下命令安装 Bazel：

`sudo apt-get update && sudo apt-get install bazel`

在构建 TensorFlow 之前，你需要安装四个依赖包：NumPy、Python-Dev、pip 和 wheel。如果使用的是 Python 2.*x,* 你可以使用以下命令安装这些依赖：

`sudo apt-get install python-numpy python-dev python-pip python-wheel`

如果使用的是 Python 3.*x,* 你可以使用以下命令安装 TensorFlow 的依赖：

`sudo apt-get install python3-numpy python3-dev python3-pip python3-wheel`

如果安装成功完成，你就可以开始构建 TensorFlow 了。

### Building TensorFlow

在将 TensorFlow 源代码下载到系统并安装 Bazel 和 TensorFlow 的依赖项后，你就可以开始构建 TensorFlow 了。开始时，切换到包含源代码的目录并输入以下命令：

`./configure`

该命令执行 `configure` 脚本，该脚本会提出一系列问题来配置 TensorFlow 包的特性。在下面的列表中，我介绍了在 Linux 上安装时遇到的问 题。每个问题后都有一组默认响应，放在方括号中。你可以通过按 Enter 来选择默认响应。

*   **Python location:** 包含 Python 解释器的目录
*   **Python library path:** 包含 Python 库的目录
*   **jemalloc support:** TensorFlow 是否应使用改进的 `jemalloc` 函数而不是 `malloc` 来分配内存。我建议选择 Yes (Y)。
*   **Google Cloud Platform support:** TensorFlow 是否应为 Google 的云计算服务 Google Cloud Platform (GCP) 提供支持。 [第 14 章](#21_9788126592555-ch14.xhtml) 解释了如何在 GCP 上运行 TensorFlow。
*   **Hadoop File System support:** TensorFlow 是否应支持 Hadoop 文件系统
*   **Amazon S3 File System support:** TensorFlow 是否应为 Amazon 的分布式 S3 文件系统提供支持
*   **XLA JIT support:** TensorFlow 是否应使用实验性的 XLA (Accelerated Linear Algebra) 编译器来加速数学运算
*   **GDR support:** TensorFlow 是否应启用 CUDA 的高速内存访问，GPUDirect RDMA
*   **VERBS support:** TensorFlow 是否应通过 VERBS 包启用远程直接内存访问 (RDMA)
*   **OpenCL support:** TensorFlow 是否应使用 OpenCL 启用 GPU 计算
*   **CUDA support:** TensorFlow 是否应使用 CUDA 启用 GPU 计算
*   **MPI support:** TensorFlow 是否应使用消息传递接口 (MPI) 启用集群计算
*   **Optimization flags:** 构建 TensorFlow 时使用的优化标志

最后一个选项尤其重要。默认情况下，构建过程将包含标志 `–march=native`。该标志告诉编译器检查目标 CPU 并确保 TensorFlow 将使用处理器支持的最先进功能。一般来说，我建议保留默认的优化选项。

完成问卷后，脚本会将你的配置选择存储在名为 `.tf_configure.bazelrc` 的文件中。要继续构建，请输入以下命令：

`bazel build --config=opt //tensorflow/tools/pip_package:build_pip_package`

该命令在 `bazel-bin/tensorflow/tools/pip_package` 目录中创建一个名为 `build_pip_package` 的脚本。要构建 TensorFlow 的安装包，请输入以下命令：

`bazel-bin/tensorflow/tools/pip_package/build_pip_package /tmp/tensorflow_pkg`

该命令在你的 `/tmp/tensorflow_pkg` 目录中创建一个 wheel 文件 `(*.whl`)。你可以通过调用 `pip install` 并使用此 wheel 文件来安装新的 TensorFlow 包。在我的系统上，wheel 文件是 `tensorflow-1.4.0rc1-cp27mu-linux_x86_64.whl`。因此，我可以使用以下命令安装 TensorFlow：

`sudo pip install /tmp/tensorflow_pkg/tensorflow-1.4.0rc1-cp27mu-linux_x86_64.whl`

`pip install` 完成后，TensorFlow 安装完成。你可以像安装默认 TensorFlow 安装一样访问 `tensorflow` 包及其模块。

### Assigning operations to devices

如果你已将 TensorFlow 配置为在 GPU 上执行并且已安装适当的 SDK，TensorFlow 会自动将处理操作分配给 GPU。

例如，TensorFlow 包含两个版本的 `matmul`：一个在 CPU 上执行，一个在 GPU 上执行。当应用程序执行 `matmul` 时，如果 GPU 可用，TensorFlow 会在 GPU 上执行矩阵乘法。

TensorFlow 允许你手动将操作分配给设备，但首先，有助于知道有哪些设备可用。TensorFlow 通过 `tensorflow.python.client` 包中的一个未记录函数 `list_local_devices` 提供此信息。该函数返回 `DeviceAttribute` 协议缓冲区的列表，并且以下代码调用 `list_local_devices` 来打印可用设备的列表：

```
from tensorflow.python.client import device_lib

devices = device_lib.list_local_devices()

for device in devices:
    print(device)
```

在我的廉价笔记本电脑上，此代码打印以下结果：

```
name: "/device:CPU:0"
device_type: "CPU"
memory_limit: 268435456
locality {}
incarnation: 2086003163627480003
```

TensorFlow 识别两种类型的设备：CPU 和 GPU。TensorFlow 为每个设备分配一个名称，并且该名称始终具有相同的格式：

`/job:Part/replica:<replica>/task:<task>/device:<type>:<device_num>`

除非你正在开发分布式应用程序，否则你可以省略 `job`、`replica` 和 `task` 字段，只需使用 `/device:<type>:<device_num>`。这里，`<type>` 可以是 `CPU` 或 `GPU`，而 `<device_num>` 标识给定类型中识别的设备的索引。因此，第一个 CPU 是 `/device:CPU:0`，第二个 GPU 是 `/device:GPU:1`。

如果你有多个给定类型的设备，可以配置会话以限制其可访问的设备数量。`ConfigProto` 缓冲区中的 `device_count` 参数使其成为可能。例如，以下代码将会话配置为最多使用两个 GPU：

```
conf = tf.ConfigProto(device_count={'GPU': 2})
with tf.Session(config=conf) as sess:
    …
```

如果你想在特定设备上执行操作，可以使用设备的名称调用 `tf.device`。此函数返回一个上下文管理器，将上下文中的所有操作分配给给定设备。例如，以下代码指定后续操作应分配给第二个 GPU：

```
with tf.device('/device:GPU:1'):
    …
```

假设你的应用程序正在执行一个会话，你想知道会话正在使用哪些设备。在这种情况下，你可以将 `log_device_placement` 选项设置为 `True`，在会话的构造函数中。

```
a = tf.constant(1.2, name='a_var')
b = tf.constant(3.4, name='b_var')
sum = a + b;
conf = tf.ConfigProto(log_device_placement=True)
with tf.Session(config=conf) as sess:
    print(sess.run(sum))
```

如果系统只有一个 CPU，打印的输出将如下所示：

```
4.6
Device mapping: no known devices.
add: (Add): /job:localhost/replica:0/task:0/device:CPU:0
b_var: (Const): /job:localhost/replica:0/task:0/device:CPU:0
a_var: (Const): /job:localhost/replica:0/task:0/device:CPU:0
```

### Configuring GPU usage

