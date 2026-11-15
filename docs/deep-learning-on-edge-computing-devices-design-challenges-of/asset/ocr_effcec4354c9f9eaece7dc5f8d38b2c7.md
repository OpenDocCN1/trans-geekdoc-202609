![](bbox=[0.19, 0.09, 0.76, 0.29])

Figure 8.3 The proposed object tracking VLSI architecture.

low-cost memory-centric architecture, as memory cells are much cheaper than computing resources in modern nanometer semiconductor technology. Multiple-level pipelines and parallel processing circuits are adopted to improve the system throughput with such minimized computing resources.

# 8.3.2 Block circuit design

To reduce system cost while realizing fine-grained pipelines with parallel circuits to boost processing speed, we carefully design and optimize the computational block circuits. Fig. 8.4 shows the circuit details of the feature extracting block, which is based on a pixel stream processing structure to minimize computational units, at a matched rate of real-time image sensors [12].

Fig. 8.4(a) is the input image integrator. A row buffer is used to cache one row of the latest obtained pixels of current integral image for iterative usage. A 4-input adder calculates the integral image following Eq. (8.2). It can produce one IP pixel per clock cycle.

Fig. 8.4(b) shows the circuit of the pixelwise temporal high-pass filter embedding the spatial DoG filter, which computes Eq. (8.6). The filter coefficient c is unsigned 8-bit and can be configured to flexibly adjust the pass band to adapt to various motion scenarios. The filter receives the unsigned 32-bit pixel stream of the textural integral image (IP) from the image integrator, generates a signed 40-bit (including 8-bit fractional) pixel stream of the dynamic integral image (IH), and updates the IP and IH memories along the streams. It uses a 10-stage (one clock cycle per stage) pixel-level pipeline to realize the pixel stream processing and match the high throughput of the image integrator.