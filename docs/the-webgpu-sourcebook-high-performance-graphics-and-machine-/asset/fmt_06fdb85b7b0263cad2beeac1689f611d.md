
# Superposition and FFT Merge Process

Because of the superposition property, we know that the frequency components of a sum of sequences equal the sum of the individual frequency components. That is, if we add `x[n]` and `y'[n]` to form `z[n]`, `Z[k] = X[k] + Y'[k]`. In this example, adding `x[n]` and `y'[n]` gives us `z[n] = [12.5, 6.0, –9.5, 2.0]`. Adding `X[k]` and `Y'[k]`, we get `Z[k] = [3.0, 22.0, 3.0, 22.0] + [8.0, i4.0, –8.0, –i4.0] = [11.0, 22.0 + i4.0, –5.0, 22.0 – i4.0]`.

This may seem complicated, but by stretching, shifting, and adding, we can compute the Fourier transform of `[12.5, 6.0, –9.5, 2.0]` without performing a full DFT. The general rules for computing a four-element FFT are as follows:

## General Rules for Computing a Four-Element FFT

1. Compute the 2-element FFT of the first and third elements and the 2-element FFT of the second and fourth elements.
2. Obtain the frequency components of the stretched sequences by repeating the original frequency components.
3. Multiply the frequency components of the second sequence by a sinusoid. This corresponds to shifting the sequence.
4. Add the frequency components of the first sequence to those of the second sequence.

This merge process is the heart of the FFT, and when I first encountered the algorithm, I had to work through several examples before this process made sense. I also found it helpful to trace through butterfly diagrams. [Figure 12.9](#chapter12.xhtml#fig12_9) presents the diagram corresponding to our full 4-element example.

![Figure 12.9 Butterfly diagram of a 4-element FFT.](images/fig12_9.jpg)

[Figure 12.9](#chapter12.xhtml#b12fig12_9) Butterfly diagram of a 4-element FFT.

## Butterfly Diagram and Bit Reversal

There are two important points to note. First, the input elements are split into even/odd pairs before the processing starts. That is, this FFT processes elements `x[0]`, `x[2]`, `x[1]`, and `x[3]` in that order. If there were eight input elements, they would be processed as follows: `x[0]`, `x[4]`, `x[2]`, `x[6]`, `x[1]`, `x[5]`, `x[3]`, `x[7]`.

This rearranging is called `bit reversal` because the bits that make up an element's index must be reversed to obtain the element's position. For example, if you reverse the bits of the index 3, `0x011`, you get `0x110`, or 6. This means `x[3]` takes the position that `x[6]` would normally take in an 8-element FFT. Similarly, `x[6]` takes the position that `x[3]` would normally take.

It's also important to notice the `w[k]` terms on the right side of the diagram. These identify the elements of the sinusoid used to multiply a shifted sequence. For a four-element FFT, the `w[k]` terms equal `cos(2πk/4) – i sin(2πk/4)` as `k` runs from 0 to 3, or `[1, –i, –1, i]`. These `w[k]` elements scale values on the nearby lines. For example, the upward arrow from the node equaling 4.0 is multiplied by `w[1]`, or –i. Therefore, the final node returns 22 – 4i. In an 8-element FFT, `w[k]` equals `cos(2πk/8) – i sin(2πk/8)` as `k` runs from 0 to 7.

The process used to merge 2-element FFTs into a 4-element FFT can be further extended to compute FFTs of any size, so long as the size is a power of 2. In each case, the input elements are stretched, shifted, and added to form 2-element FFTs, then 4-element FFTs, and so on until the entire `N`-element FFT is computed. Next, we'll look at how to code this algorithm in a compute shader.

## Example Application: Filtering Audio with the FFT

If a sequence contains `N` complex values, the FFT requires `log[2]N` stages to compute its frequency components. The first stage computes 2-element FFTs, the second stage merges the results to form 4-element FFTs, and this merging continues all the way up to the final stage, which computes the `N`-element FFT. In general, Stage `k` performs `N/2^k` FFTs, each of whose size is `2^k`.

If the FFT computation is partitioned among `D` invocations, and `D` is a power of 2 less than `N`, then each invocation computes the first `log[2](N/D)` stages of the FFT. In the final stages (`log[2]N – log[2](N/D) = log[2]D`), the invocations need to synchronize their processing.

### Parallel FFT Execution with Multiple Invocations

An example will make this clear. Suppose `x[n]` contains 64 elements (6 stages) and you want to compute its FFT with 4 invocations. Each invocation will process the first `log[2](64/4) = 4` stages on its own. Then, after the fourth stage is complete, the invocations need to synchronize their processing to compute the fifth and sixth stages. [Figure 12.10](#chapter12.xhtml#fig12_10) depicts this relationship graphically.

![Figure 12.10 A 64-element FFT with four invocations.](images/fig12_10.jpg)

[Figure 12.10](#chapter12.xhtml#b12fig12_10) A 64-element FFT with four invocations.

### Workgroup Memory Allocation

In theory, invocations can access workgroup memory faster than storage buffers. Therefore, it's a good idea to use workgroup memory when possible. The `Ch12_FFT` application allocates the maximum amount of workgroup memory and uses it to store intermediate results. It's assumed that the size of workgroup memory is a power of 2.

On my system, the maximum size of workgroup memory is 16,384 bytes. Each pair of real and imaginary values occupies 8 bytes, so the largest FFT/IFFT result that can be stored in workgroup memory is 16,384/8 = 2,048. Each group needs to perform a 2,048-point FFT/IFFT, so `pts_per_group` is set to 2048. Each group contains 256 invocations, so the largest FFT/IFFT that can be performed by an invocation in workgroup memory is 2048/256 = 8. For this reason, `pts_per_inv` is set to 8.

### Five-Step Audio Filtering Process

The `Ch12_FFT` application defines two compute shaders. The first, `fftInit`, performs the FFT and IFFT up to the size of workgroup memory. The second, `fftStage`, performs stages of the FFT and IFFT that are too large to fit in workgroup memory. Combining the two shaders, the full audio filtering process consists of five steps:

1. The `fftInit` shader performs FFT stages up to the size of workgroup memory.
2. The `fftStage` shader is called repeatedly to perform FFT stages up to the total number of samples.
3. The `fftInit` shader is called to perform an IFFT. Before it starts processing, it sets frequencies in the desired ranges to 0.
4. After setting frequencies to 0, the `fftInit` shader performs the IFFT stages up to the size of workgroup memory.
5. The `fftStage` shader is called repeatedly to perform IFFT stages up to the total number of samples.

### Invocation Steps in fftInit

In the `fftInit` shader, each invocation performs four steps:

1. Computes bit-reversed addresses and loads input data from storage buffers.
2. Performs 4-point FFTs/IFFTs and stores the results in workgroup memory.
3. Performs successive stages independently (up to `pts_per_inv`).
4. Performs successive stages with other invocations in the workgroup (up to `pts_per_group`).

This discussion explores these steps and presents the corresponding code. Keep in mind that, after `fftInit`, the `fftStage` shader must be executed repeatedly until the full FFT/IFFT is complete.

#### Loading Data from Bit-Reversed Addresses

In the `fftInit` shader, each invocation uses its global ID to obtain an address (`g_addr`) in the input storage buffer. Then it computes the four bit-reversed addresses corresponding to `g_addr`, `g_addr+1`, `g_addr+2`, and `g_addr+3`, and stores them in a vector named `bitrev`. The following code shows how this is done.
