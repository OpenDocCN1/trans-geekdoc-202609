
# Ch05_RotateSquare 示例

`Ch05_RotateSquare` 项目中的代码展示了 WebGPU 开发的三个新且重要的方面：
1. 它创建了一个 uniform 缓冲区和一个绑定组。
2. 顶点着色器将 uniform 缓冲区作为矩阵变量访问，并将矩阵与每个顶点的坐标相乘。然后它返回变换后的坐标和顶点的位置。
3. 它配置管线将顶点组装成三角形条带而不是三角形列表。

第三点很重要，需要理解。默认情况下，顶点被组装成 *三角形列表*，它从顶点 `v[0]`、`v[1]` 和 `v[2]` 创建一个三角形，从顶点 `v[3]`、`v[4]` 和 `v[5]` 创建第二个三角形。但如果管线配置为创建 *三角形条带*，第一个三角形将由顶点 `v[0]`、`v[1]` 和 `v[2]` 创建，第二个三角形由顶点 `v[1]`、`v[2]` 和 `v[3]` 创建。这使得可以用四个顶点绘制一个正方形（两个三角形）。

[图 5.1](#chapter5.xhtml#fig5_1) 显示了页面的外观。正如项目名称所暗示的，渲染结果是一个旋转的正方形。

![图 5.1 Ch05_RotateSquare 页面.](images/fig5_1.jpg)

[图 5.1](#chapter5.xhtml#b5fig5_1) Ch05_RotateSquare 页面。

以下代码列表展示了 `Ch05_RotateSquare` 应用程序的代码。如前例所示，顶点着色器和片段着色器代码被合并到一个名为 `shaderCode` 的字符串中。

```
const shaderCode = `
@group(0) @binding(0) var<uniform> rotMat: mat4x4f;
@vertex
fn vertexMain(@location(0) coords: vec2f) -> @builtin(position) vec4f {    
    return rotMat * vec4f(coords, 0.0, 1.0);
}
@fragment
fn fragmentMain() -> @location(0) vec4f {
    return vec4f(0.2, 0.2, 1.0, 1.0);
}
`;
// Create top-level asynchronous function
async function runExample() {
// Check if WebGPU is supported
if (!navigator.gpu) {
    throw new Error("WebGPU not supported");
}
// Access the GPUAdapter
const adapter = await navigator.gpu.requestAdapter();
if (!adapter) {
    throw new Error("No GPUAdapter found");
}
// Access the GPU
const device = await adapter.requestDevice();
if (!device) {
    throw new Error("Failed to create a GPUDevice");
}
// Access the canvas
const canvas = document.getElementById("canvas_example");
if (!canvas) {
    throw new Error("Could not access canvas in page");
}
// Obtain a WebGPU context for the canvas
const context = canvas.getContext("webgpu");
if (!context) {
    throw new Error("Could not obtain WebGPU context for canvas");
}
// Configure the context with the device and format
const canvasFormat = navigator.gpu.getPreferredCanvasFormat();
context.configure({
    device: device,
    format: canvasFormat,
});
// Create the command encoder
const encoder = device.createCommandEncoder();
if (!encoder) {
    throw new Error("Failed to create a GPUCommandEncoder");
}
// Create the render pass encoder
const renderPass = encoder.beginRenderPass({
    colorAttachments: [{
        view: context.getCurrentTexture().createView(),
        loadOp: "clear",
        clearValue: { r: 0.9, g: 0.9, b: 0.9, a: 1.0 },
        storeOp: "store"
    }]
});
// Define vertex data
const vertexData = new Float32Array([
    -0.5, -0.5,    // First vertex
    0.5, -0.5,     // Second vertex
    -0.5, 0.5,    // Third vertex
    0.5, 0.5,     // Fourth vertex
]);
// Create vertex buffer
const vertexBuffer = device.createBuffer({
    label: "Vertex Buffer 0",
    size: vertexData.byteLength,
    usage: GPUBufferUsage.VERTEX | GPUBufferUsage.COPY_DST
});
device.queue.writeBuffer(vertexBuffer, 0, vertexData);
renderPass.setVertexBuffer(0, vertexBuffer);
// Define layout of vertex buffer
const bufferLayout = {
    arrayStride: 8,
    attributes: [
       { format: "float32x2", offset: 0, shaderLocation: 0 }
    ],
};
// Define uniform data
const uniformData = new Float32Array([
   0.866, 0.5, 0.0, 0.0,    // First column of matrix
   -0.5, 0.866, 0.0, 0.0,   // Second column of matrix
   0.0, 0.0, 1.0, 0.0,      // Third column of matrix
   0.0, 0.0, 0.0, 1.0,      // Fourth column of matrix
]);
// Create uniform buffer
const uniformBuffer = device.createBuffer({
    label: "Uniform Buffer 0",
    size: uniformData.byteLength,
    usage: GPUBufferUsage.UNIFORM | GPUBufferUsage.COPY_DST});
device.queue.writeBuffer(uniformBuffer, 0, uniformData); 
// Create the shader module
const shaderModule = device.createShaderModule({
    label: "Shader module 0",
    code: shaderCode
});
// Define the rendering procedure
const renderPipeline = device.createRenderPipeline({
    layout: "auto",
    vertex: {
      module: shaderModule,
      entryPoint: "vertexMain",
      buffers: [bufferLayout]
    },
    fragment: {
      module: shaderModule,
      entryPoint: "fragmentMain",
      targets: [{
        format: canvasFormat
      }]
    },
    primitive: {
        topology: "triangle-strip"
    }
});
renderPass.setPipeline(renderPipeline);
// Access the bind group layout
const bindGroupLayout = renderPipeline.getBindGroupLayout(0);
// Create the bind group
let bindGroup = device.createBindGroup({
    layout: bindGroupLayout,
    entries: [{
        binding: 0,
        resource: { buffer: uniformBuffer }
    }]
});
// Associate bind group with render pass encoder
renderPass.setBindGroup(0, bindGroup);
// Draw vertices and complete rendering
renderPass.draw(4);
renderPass.end();
// Submit the render commands to the GPU
device.queue.submit([encoder.finish()]);
}
// Run example function
runExample();
```

在浏览这段代码时，重要的是要看到顶点缓冲区和 uniform 缓冲区如何协同工作。顶点缓冲区为每个顶点提供不同的坐标，而 uniform 缓冲区包含一个在顶点之间保持不变的 4×4 矩阵。将矩阵与顶点坐标相乘会产生一组新的坐标，它们是原始坐标的旋转版本。

## 存储缓冲区

在离开 uniform 缓冲区主题之前，我想指出它们有一个主要缺点：它们只能包含有限量的数据。你可以通过访问 `GPUAdapter` 对象提供的 `maxUniformBufferBindingSize` 限制来检查这一点。

```
// Check the maximum size of uniforms
const maxSize = adapter.limits.maxUniformBufferBindingSize;
```

在我的系统上，uniform 缓冲区的最大大小为 65,536 字节，因此如果需要传输超过该量的 uniform 数据，你需要创建多个 uniform 缓冲区。或者，你可以创建一个 *存储缓冲区*。在我的系统上，存储缓冲区的最大大小为 2,147,483,644 字节。

在代码中，使用存储缓冲区与使用 uniform 缓冲区类似，但有三个主要区别：
1. 创建缓冲区时，`GPUBufferUsage.UNIFORM` 标志必须更改为 `GPUBufferUsage.STORAGE`。
2. 创建绑定组布局时，缓冲区属性的类型属性应设置为 `storage` 或 `read-only-storage`。
3. 在着色器中访问缓冲区时，uniform 模板应更改为 `storage`。

为了阐明第三点，以下代码声明了一个矩阵变量，其数据从存储缓冲区读取：

```
// Declare a variable that accesses a storage buffer
@group(0) @binding(0) var<storage> mat: mat4x4f;
```

默认情况下，存储缓冲区是只读的，就像 uniform 缓冲区一样。然而，存储缓冲区也可以创建为读写访问。在这种情况下，着色器的变量声明应具有更新的模板类型：

```
@group(0) @binding(0) var<storage, read_write> mat: mat4x4f;
```

使用存储缓冲区的缺点是性能。如果你的应用程序需要重复更新数据，使用 uniform 缓冲区比使用存储缓冲区更好。
