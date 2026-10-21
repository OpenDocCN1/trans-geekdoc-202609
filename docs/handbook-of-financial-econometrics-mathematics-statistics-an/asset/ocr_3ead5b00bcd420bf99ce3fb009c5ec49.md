# Speed-up

![](bbox=[0.16, 0.18, 0.84, 0.38])

Figure 39.2: GPU speedup performance when the random vector size n ranges from 1000 to 8000.

# 39.3.2 Example II: Fast Fourier transform

Fourier transform method can be used to characterize option prices under various financial models (Kienitz and Wetterau, 2012). Fast Fourier transform (FFT) is applied and becomes a major computational method in finance.

Let’s introduce basic instructions on CPU and GPU both in Matlab by considering a random vector with the size n and its FFT. Next line shows how Matlab CPU is programmed:

```
>> n = 2^16; T = rand(n,1); F = fft(T); % on CPU.
```

To perform the same operation on the GPU, recall that one has to use the command gpuArray to transfer data from the MATLAB workspace to GPU device memory. Then fft, a GPU-enabled function, can be executed. One can use the command gather to transfer the result stored on GPU back to CPU for further serial operation.

```
>> gT = gpuArray(T); gF = fft(gT); % on GPU
>> F = gather(gF);  % on CPU.
```

It is worth noting that in this particular example the running time of FFT on GPU might be less than the time taken to transfer data between CPU and GPU. This means data transfer can possibly degrade the whole performance on GPU computing.

Figure 39.3 shows the speedup performance for pricing European options under Heston model by FFT (Carr and Madan, 1999). A comparison of execution times for CPU and GPU computing is implemented under a CPU (Intel Core i5-3230M Processor, 2.6 GHz) and a GPU (Geforce GT635M).