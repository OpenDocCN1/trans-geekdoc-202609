
# DFT 矩阵和逆变换

$$\\left| \\begin{matrix} {w\_{0}\\left\\lbrack 0 \\right\\rbrack} & {w\_{0}\\left\\lbrack 1 \\right\\rbrack} & {w\_{0}\\left\\lbrack 2 \\right\\rbrack} & \\begin{matrix} \\cdots & {w\_{0}\\left\\lbrack {N - 1} \\right\\rbrack} \\\\ \\end{matrix} \\\\ {w\_{1}\\left\\lbrack 0 \\right\\rbrack} & {w\_{1}\\left\\lbrack 1 \\right\\rbrack} & {w\_{1}\\left\\lbrack 2 \\right\\rbrack} & \\begin{matrix} \\cdots & {w\_{1}\\left\\lbrack {N - 1} \\right\\rbrack} \\\\ \\end{matrix} \\\\ \\begin{matrix} {w\_{2}\\left\\lbrack 0 \\right\\rbrack} \\\\ \\vdots \\\\ \\end{matrix} & \\begin{matrix} {w\_{2}\\left\\lbrack 1 \\right\\rbrack} \\\\ \\vdots \\\\ \\end{matrix} & \\begin{matrix} {w\_{2}\\left\\lbrack 2 \\right\\rbrack} \\\\ \\vdots \\\\ \\end{matrix} & \\begin{matrix} \\begin{matrix} \\cdots & {w\_{2}\\left\\lbrack {N - 1} \\right\\rbrack} \\\\ \\end{matrix} \\\\ \\begin{matrix} \\; & \\vdots \\\\ \\end{matrix} \\\\ \\end{matrix} \\\\ {w\_{N - 1}\\left\\lbrack 0 \\right\\rbrack} & {w\_{N - 1}\\left\\lbrack 1 \\right\\rbrack} & {w\_{N - 1}\\left\\lbrack 2 \\right\\rbrack} & \\begin{matrix} \\cdots & {w\_{N - 1}\\left\\lbrack {N - 1} \\right\\rbrack} \\\\ \\end{matrix} \\\\ \\end{matrix} \\right|\\left| \\begin{matrix} {x\\left\\lbrack 0 \\right\\rbrack} \\\\ {x\\left\\lbrack 1 \\right\\rbrack} \\\\ {x\\left\\lbrack 2 \\right\\rbrack} \\\\ \\begin{matrix} \\vdots \\\\ {x\\left\\lbrack {N - 1} \\right\\rbrack} \\\\ \\end{matrix} \\\\ \\end{matrix} \\right| = \\left| \\begin{matrix} {X\\left\\lbrack 0 \\right\\rbrack} \\\\ {X\\left\\lbrack 1 \\right\\rbrack} \\\\ {X\\left\\lbrack 2 \\right\\rbrack} \\\\ \\begin{matrix} \\vdots \\\\ {X\\left\\lbrack {N - 1} \\right\\rbrack} \\\\ \\end{matrix} \\\\ \\end{matrix} \\right|$$

该矩阵表示为 `W`，称为 `DFT matrix`。如果适当缩放，`W` 既是酉矩阵又是对称矩阵，这意味着其逆矩阵 `W^(-1)` 等于其共轭 `W*`。我们通过反转每个虚部符号来得到矩阵的共轭。对于 `DFT` 来说，这意味着将 `w[k][n]` 中的负虚部正弦转换为正虚部正弦。

该逆矩阵很重要，因为它可用于计算逆 `DFT`，即 `IDFT`。`IDFT` 将频域数据转换为空域数据，可表示为矩阵-向量形式 `x = W^(-1)X`。`IDFT` 方程如下所示：

$$x\\left\\lbrack n \\right\\rbrack = X\\left\\lbrack k \\right\\rbrack \\cdot w\_{k}^{}{}\_{}^{\*}\\left\\lbrack n \\right\\rbrack = \\frac{1}{N}\\sum\\limits\_{k = 0}^{N - 1}X\\left\\lbrack k \\right\\rbrack\\left( {\\cos\\left( \\frac{2\\pi nk}{N} \\right) - i\\sin\\left( \\frac{2\\pi nk}{N} \\right)} \\right)$$

`w[k]^* [n]` 项标识 `w[k][n]` 的共轭，其中 –i sin(x) 被替换为 +i sin(x)。这与 `DFT` 方程的唯一其他区别是缩放因子 `1/N`。这是必要的，以确保一旦 `x[n]` 转换 为 `X[k]`，逆变换将产生原始的 `x[n]`。另外，`DFT` 方程和 `IDFT` 方程都可以用 `1/√n` 缩放。

## 示例应用——使用 DFT 进行音频滤波

到目前为止，你应该对 `DFT` 和 `IDFT` 有了中等的熟悉程度。本节探讨 `Ch12_DFT` 应用中的代码，该应用使用 `DFT` 和 `IDFT` 来去除音频中的噪声。准确地说，该项目执行五个操作：
1. 使用 Web Audio API 从 `noisy.wav` 读取音频数据。
2. 使用 `DFT` 将时域序列 `x[n]` 转换为频域序列 `X[k]`。
3. 将噪声范围内的频率分量设为 0。
4. 使用 `IDFT` 将修改后的频域序列 `X[k]` 转换为空域序列 `x[n]`。
5. 当用户在页面中按下按钮时播放滤波后的音频数据。

本章的第一部分解释了如何完成步骤 1 和 5。本节重点关注步骤 2、3 和 4。

### 实现 DFT 和 IDFT

`Ch12_DFT` 应用中的计算着色器根据名为 `factor` 的变量执行 `DFT` 或 `IDFT`。计算着色器在名为 `dftShader` 的字符串中定义，其代码如下所示：

// Real part of time-domain sequence
@binding(0) @group(0) var<storage, read_write> xn_real : array<vec4f>;

// Imaginary part of time-domain sequence
@binding(1) @group(0) var<storage, read_write> xn_imag : array<vec4f>;

// Real part of frequency-domain sequence
@binding(2) @group(0) var<storage, read_write> xk_real : array<vec4f>;

// Imaginary part of frequency-domain sequence
@binding(3) @group(0) var<storage, read_write> xk_imag : array<vec4f>;

// Whether to perform the DFT or IDFT @binding(4) @group(0) var<storage, read_write> factor : f32;

override group_size: u32;
override filter_start: u32;
override filter_end: u32;

@compute @workgroup_size(group_size)
fn computeMain(@builtin(global_invocation_id) gid : vec3<u32>,
    @builtin(num_workgroups) num_groups : vec3<u32>) {

    let N = group_size * num_groups.x;
    let two_pi_k_over_N = (-1.0 * 2.0 * 3.14159 * f32(gid.x))/f32(N);
    let num_vectors = N/4;
    var real_sum = 0.0;
    var imag_sum = 0.0;
    var real_val: vec4f;
    var imag_val: vec4f;

    // Iterate through input vectors
    for (var i: u32 = 0; i < num_vectors; i++) {

        // Form vectors of wk values
        var arg = vec4f(two_pi_k_over_N * f32(4 * i),
                        two_pi_k_over_N * f32(4 * i + 1),
                        two_pi_k_over_N * f32(4 * i + 2),
                        two_pi_k_over_N * f32(4 * i + 3));

        var w_real = cos(arg);
        var w_imag = sin(arg);
        // Process input vector
        if (factor == -1.0) {
            real_val = xn_real[i];
            imag_val = xn_imag[i];
        } else {
            real_val = xk_real[i];
            imag_val = xk_imag[i];
        }
        real_sum += dot(real_val, w_real) - dot(imag_val, w_imag);
        imag_sum -= dot(real_val, w_imag) + dot(imag_val, w_real);
    }

    // Store results to memory
    if (factor == -1.0) {

        // Apply filter
        if((gid.x > filter_start) && (gid.x < filter_end)) {
            xk_real[gid.x/4][gid.x % 4] = 0.0;
            xk_imag[gid.x/4][gid.x % 4] = 0.0;
        } else {
            xk_real[gid.x/4][gid.x % 4] = real_sum;
            xk_imag[gid.x/4][gid.x % 4] = imag_sum;
        }
    } else {
        xn_real[gid.x/4][gid.x % 4] = real_sum/f32(N);
        xn_imag[gid.x/4][gid.x % 4] = imag_sum/f32(N);
    }
}

如图所示，着色器接收五个存储缓冲区：
1. `xn_real`—时域序列 `x[n]` 的实部
2. `xn_imag`—时域序列 `x[n]` 的虚部
3. `xk_real`—频域序列 `X[k]` 的实部
4. `xk_imag`—频域序列 `X[k]` 的虚部
5. `format`—确定执行 `DFT` 还是 `IDFT` 的值

如果将 `format` 设为 `-1`，计算着色器将执行 `DFT` 并将 `xn_real` 和 `xn_imag` 中的数据转换为序列 `xk_real` 和 `xk_imag`。如果将 `format` 设为 `1`，计算着色器将执行 `IDFT`，并将 `xk_real` 和 `xk_imag` 中的数据转换为序列 `xn_real` 和 `xn_imag`。

在读取输入数据之前，每个调用通过将工作组大小乘以工作组数量来确定样本总数 `N`。由于数据有 131,072 个样本，应用程序创建了 512 个工作组，每个工作组有 256 次调用（`N = 512 * 256 = 131,072`）。

计算出 `N` 后，每个调用通过将 2π 乘以其全局 ID 并将乘积除以 `N` 来计算名为 `two_pi_k_over_N` 的值。每次迭代时，一个调用都会创建一个包含四个此类值的向量。然后它计算该向量的正弦和余弦。
