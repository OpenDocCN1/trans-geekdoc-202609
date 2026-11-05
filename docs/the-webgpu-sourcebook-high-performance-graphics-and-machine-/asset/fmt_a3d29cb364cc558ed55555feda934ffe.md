
| `DrawIndexedIndirect(Buffer const& indirectBuffer, uint64_t indirectOffset)` || Draws vertices according to index based on parameters in an indirect buffer |
| `End()` || Complete recording of rendering commands |
The `AppB_DawnTriangle` project doesn't use an index buffer or an indirect buffer, so it calls `Draw`. This tells the renderer to access attributes in the order in which they're stored in the vertex buffer. Then the application calls the `End` function to complete the encoding of rendering commands.

```
// Launch draw operation
renderPass.Draw(3);
renderPass.End();
```
At this point, the render pass encoder has completed encoding the rendering commands. To send these commands to the GPU, the application needs to perform two steps:
1. Obtain the `CommandBuffer` by calling the `CommandEncoder`'s `Finish()` function.
2. Submit the commands to the device by calling the `Queue`'s `Submit()` function with the `CommandBuffer`.
The following code shows how this works. The application accesses the `Queue` by calling the `device`'s `GetQueue()` function and then passes it the `CommandBuffer`.

```
// Send the rendering commands to the GPU
wgpu::CommandBuffer commands = encoder.Finish();
device.GetQueue().Submit(1, &commands);
```
Unlike the `submit` method in JavaScript, Dawn's `Submit` function can accept multiple command buffers. The first argument identifies the number of command buffers and the second argument points to them.

## EXAMPLE PROJECT—DRAWING AN ORANGE TRIANGLE
This section has discussed the code in the `AppB_Triangle` project at length, so you should have a solid understanding of the code in the `dawn_triangle.cpp` source file.
However, the `Makefile` in the `AppB_DawnTriangle` project is different from the `Makefile` in the `AppB_SimpleWasm` project. Its content is given as follows:
```
PROJ=dawn_triangle

CPP=em++

CPPFLAGS=-sUSE_WEBGPU=1 -std=c++17

$(PROJ).js: $(PROJ).cpp
     $(CPP) $(CPPFLAGS) -o $@ $^

.PHONY: clean

clean:
     rm $(PROJ).js $(PROJ).wasm
```
While the preceding `Makefile` told `Emscripten` to create a WebAssembly module (`*.wasm`), this `Makefile` tells `Emscripten` to compile the C++ code into a JavaScript file (`*.js`). This is important to understand. If you run the build with `emmake make`, you'll see that `Emscripten` produces two files: a JavaScript file and a WebAssembly module.
If you look at the JavaScript file, you'll see that its content is practically unreadable. So you may wonder how you're supposed to access `WebAssembly` and launch the rendering application. As it happens, the JavaScript code will handle this for you. That is, it will load `WebAssembly` and execute its `main` function when the code is invoked.
The good news is that you don't have to export functions or call `WebAssembly` methods in JavaScript. The bad news is that you lose control of executing your code.

## Summary
At the time I write this, `WebAssembly` hasn't made a major impact on web development. Professional developers argue over JavaScript frameworks and laugh at the idea of using anything besides JavaScript. Despite this, `WebAssembly` development provides two major advantages: improved performance and the ability to compile high-level languages to `WebAssembly`.
The first part of this appendix showed how `Emscripten` makes it possible to compile C++ code to `WebAssembly`. This discussion introduced the `em++` compiler and its many flags, as well as the `emmake` tool. This section also explained how to write `Makefiles` capable of telling `Emscripten` how C++ code should be compiled.
The rest of the appendix focused on `Dawn`, Google's unofficial implementation of `WebGPU`. `Dawn` makes it possible to run `WebGPU` on multiple platforms, and this appendix has focused on running `WebGPU` in `Emscripten`. More precisely, this appendix explained how to code a C++ application that uses `Dawn` to render an orange triangle in an HTML canvas.
While drawing a triangle may not seem interesting, the potential advantages of combining `Dawn` and `WebAssembly` are very exciting. Developers of high-performance graphical applications, such as computer-aided drafting (`CAD`) and games, will be able to run their code in a browser without significant loss of performance and without needing to learn a new language.

## Index
A
*   Activation functions, [204](#chapter9.xhtml#p204), [206](#chapter9.xhtml#p206) 
    *   logistic (sigmoid) function, [207](#chapter9.xhtml#p207)
    *   nodes, [221](#chapter9.xhtml#p221)
    *   rectified linear unit (ReLU) function, [206](#chapter9.xhtml#p206)–[207](#chapter9.xhtml#p206), [*207*](#chapter9.xhtml#fig9_8)
    *   softmax function, [208](#chapter9.xhtml#p208)
*   Adapter class, functions of, [**342**](#appb.xhtml#tblb_5)
*   Adaptive gradient (adagrad) optimization, [218](#chapter9.xhtml#p218)–[219](#chapter9.xhtml#p218)
*   Adaptive moment estimation, [219](#chapter9.xhtml#p219)
*   Adaptive momentum (Adam) optimization, [219](#chapter9.xhtml#p219)–[220](#chapter9.xhtml#p219)
*   AddEventListener method, [152](#chapter7.xhtml#p152)
*   Address spaces for variables, [**57**](#chapter4.xhtml#tbl4_5)
*   Advanced audio coding files, [274](#chapter12.xhtml#p274)
*   Advanced scalable texture compression (ASTC), [135](#chapter6.xhtml#p135)–[136](#chapter6.xhtml#p135)
*   AlphaMode, [18](#chapter2.xhtml#p18)
*   Animation, [165](#chapter7.xhtml#p165)–[166](#chapter7.xhtml#p165) 
    *   example application, [167](#chapter7.xhtml#p167)–[169](#chapter7.xhtml#p167)
    *   interpolation and, [166](#chapter7.xhtml#p166)–[167](#chapter7.xhtml#p166)
*   Anisotropic filtering, [128](#chapter6.xhtml#p128)
*   AppB_DawnTriangle application, [354](#appb.xhtml#p354)
*   Argtype, [46](#chapter4.xhtml#p46)
*   Arguments of setViewport method, [**153**](#chapter7.xhtml#tbl7_2)
*   ArrayBuff, [276](#chapter12.xhtml#p276)
*   ArrayBuffer, [121](#chapter6.xhtml#p121), [274](#chapter12.xhtml#p274), [276](#chapter12.xhtml#p276)
*   ArrayStride, [72](#chapter4.xhtml#p72)
*   Array types, [55](#chapter4.xhtml#p55)
*   Artificial neural networks (ANNs), [199](#chapter9.xhtml#p199); *see also* [Machine learning with neural networks](#index.xhtml#ieidx_295)
*   Assembly, [25](#chapter3.xhtml#p25)
*   Atomic functions, [191](#chapter8.xhtml#p191), [**191**](#chapter8.xhtml#tbl8_8)
*   Atomic variables, [191](#chapter8.xhtml#p191)
*   Attachments, [26](#chapter3.xhtml#p26)
*   Attribute data, [24](#chapter3.xhtml#p24), [75](#chapter5.xhtml#p75) 
    *   for drawing triangle, [*39*](#chapter3.xhtml#fig3_3)
    *   layout properties of, [*42*](#chapter3.xhtml#fig3_4)
*   Audio 
    *   filtering, [282](#chapter12.xhtml#p282), [291](#chapter12.xhtml#p291)
    *   filtering with DFT, [288](#chapter12.xhtml#p288) 
        *   DFT and IDFT, implementation, [288](#chapter12.xhtml#p288)–[291](#chapter12.xhtml#p288)
    *   processing, [281](#chapter12.xhtml#p281)–[283](#chapter12.xhtml#p281)
    *   source, [281](#chapter12.xhtml#p281)
*   AudioBuffer, [274](#chapter12.xhtml#p274), [276](#chapter12.xhtml#p276)–[277](#chapter12.xhtml#p276), [**277**](#chapter12.xhtml#tbl12_2) 
    *   methods, [277](#chapter12.xhtml#p277)–[278](#chapter12.xhtml#p277)
*   AudioContext, [275](#chapter12.xhtml#p275)–[276](#chapter12.xhtml#p275) 
    *   creation properties, [275](#chapter12.xhtml#p275)
*   Automatic variables, [337](#appb.xhtml#p337)
*   Await operator, [11](#chapter2.xhtml#p11)
*   Axon, [202](#chapter9.xhtml#p202)
B
*   BaseAudioContext, [276](#chapter12.xhtml#p276)
*   BaseVertex, [96](#chapter5.xhtml#p96)
*   Batching and mini-batching, [220](#chapter9.xhtml#p220)–[221](#chapter9.xhtml#p220)
*   Beethoven's *Moonlight Sonata,* [283](#chapter12.xhtml#p283)
*   BeginComputePass(), [**15**](#chapter2.xhtml#tbl2_4), [16](#chapter2.xhtml#p16), [170](#chapter8.xhtml#p170)–[171](#chapter8.xhtml#p170)
*   BeginningOfPassWriteIndex, [189](#chapter8.xhtml#p189)
