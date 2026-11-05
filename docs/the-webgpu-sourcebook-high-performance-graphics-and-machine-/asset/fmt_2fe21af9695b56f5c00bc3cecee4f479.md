
| indirect-first-instance || Applications can set the `firstInstance` argument of indirect draw calls to a value greater than 0 |
| shader-f16 || Shaders can access half-precision (16-bit) floating-point values |
| rg11b10ufloat-renderable || Applications can use `rg11b10ufloat` as a texture format |
| bgra8unorm-storage || Applications can create storage buffers whose data is formatted according to `bgra8unorm` |
| float32-filterable || The GPU can smooth textures by filtering 32-bit floating-point values |

An example will demonstrate how these capabilities can be accessed. Suppose an application needs to know if the client's GPU supports control of depth clipping. It could use code like the following:

```
// Check if the client supports the depth clip control feature
if (adapter.features.has("depth-clip-control")) {
    console.log("Supported");
} else {
    console.log("Unsupported");
}
```

If you want to print all the features available on the system, you can use the following code:

```
// Display all of the supported features
adapter.features.forEach((value) => {
    console.log(value);
});
```

The `limits` property is helpful when an application needs to know the maximum parameters for a given capability. For example, the following code identifies the maximum number of vertex buffers an application can create:

```
const maxBuffers = adapter.limits.maxVertexBuffers;
```

The most important role of a `GPUAdapter` is to provide access to a `GPUDevice`. This is made possible by the `requestDevice` method, which returns a `Promise` that provides a `GPUDevice` upon fulfillment. The following code shows how this can be used:

```
// Access the GPU
const device = await adapter.requestDevice();
```

Once an application has accessed the `GPUDevice`, it can perform several operations needed for WebGPU processing. The following section discusses this in detail.

## GPUDevice

The `GPUDevice` serves as a logical connection to the client's GPU, and it plays a central role in WebGPU development. Listed in [Table 2.3](#chapter2.xhtml#tbl2_3), its methods create objects that make it possible to perform computational tasks and graphical operations.

[Table 2.3](#chapter2.xhtml#b2tbl2_3) `GPUDevice` Methods

| METHOD || DESCRIPTION |
| --- | --- |
| `createBindGroup()` || Identifies a set of resources to be bound together |
| --- | --- |
| `createBindGroupLayout()` || Identifies the structure and purpose of related resources |
| `createBuffer()` || Returns a GPUBuffer that can be used to store raw data |
| `createCommandEncoder()` || Creates an object that prepares and packages commands for execution |
| `createComputePipeline()` || Creates a pipeline for commands that perform computation |
| `createComputePipelineAsync()` || Asynchronously creates a pipeline for commands that perform computation |
| `createPipelineLayout()` || Defines the structure and purpose of each buffer created by the device |
| `createQuerySet()` || Creates a query set that can be used to run queries |
| `createRenderBundleEncoder()` || Creates a special encoder that records commands in bundles |
| `createRenderPipeline()` || Creates a pipeline for commands that render graphics |
| `createRenderPipelineAsync()` || Asynchronously creates a pipeline for commands that render graphics |
| `createSampler()` || Creates a sampler, which is used to extract data from textures |
| `createShaderModule()` || Creates an object that stores code and data related to the application's shaders |
| `createTexture()` || Creates a resource on the GPU to store pixel data for images |
| `destroy()` || Destroy the logical connection to the client's GPU |
| `importExternalTexture()` || Converts a video snapshot into a texture |
| `popErrorScope()` || Pops an error scope from the stack or is null if no error has occurred |
| `pushErrorScope()` || Pushes a new error scope onto the stack, which makes it possible to catch errors of a given type |

These methods are important in WebGPU development, but most are too complicated to be discussed here. For this reason, I'll introduce them in later chapters as they become needed. For example, the `createTexture` and `createSampler` methods are related to textures, so a proper introduction will have to wait until [Chapter 6](#chapter6.xhtml).

## GPUCommandEncoder

One of the most important methods of `GPUDevice` is `createCommandEncoder`, which returns a `GPUCommandEncoder`. This object is responsible for creating and storing commands that will be sent to the GPU. The following code shows how this can be created:

```
// Create a command encoder
encoder = device.createCommandEncoder();
```

Once the object has been created, the methods of `GPUCommandEncoder` make it possible to define operations that will be sent to the device for processing. [Table 2.4](#chapter2.xhtml#tbl2_4) lists each of these methods.

[Table 2.4](#chapter2.xhtml#b2tbl2_4) `GPUCommandEncoder` Methods

| METHOD || DESCRIPTION |
| --- | --- |
| `beginRenderPass()` || Starts encoding a render pass to perform graphical rendering |
| --- | --- |
| `beginComputePass()` || Starts encoding a compute pass to perform computational tasks |
| `finish()` || Returns a command buffer containing the encoder's commands in sequence |
| `clearBuffer()` || Encodes a command that fills a buffer with zeros |
| `copyBufferToBuffer()` || Encodes a command that copies data from one buffer to another |
| `copyBufferToTexture()` || Encodes a command that copies data from a buffer to a texture |
| `copyTextureToBuffer()` || Encodes a command that copies data from a buffer to a texture |
| `copyTextureToTexture()` || Encodes a command that copies data from one texture to another |
| `insertDebugMarker()` || Inserts a marker into the command sequence that can be used for debugging |
| `pushDebugGroup()` || Starts a debug group with a given label |
| `popDebugGroup()` || Ends a debug group |
| `resolveQuerySet()` || Encodes a command that writes the results of a query set to a buffer |
| `writeTimestamp()` || Encodes a command that writes a timestamp to a query set |

In general, the first three methods are the most important. The first, `beginRenderPass`, returns a `GPURenderPassEncoder` that will define graphical operations for the GPU. It will take several chapters to fully explore the capabilities of a `GPURenderPassEncoder`.

The second method in the table, `beginComputePass`, returns a `GPUComputePassEncoder`. The fields of this object store information that tells the GPU how to execute computational tasks. Starting in [Chapter 8](#chapter8.xhtml), I'll explain how this can be used to perform operations related to math, machine learning, and image processing.

The last method, `finish`, is required in every non-trivial WebGPU application. It converts the encoder's data into a `GPUCommandBuffer` containing one or more commands for the GPU. Once the application sends this buffer to the device's queue, the GPU will begin executing the commands.

## GPUQueue

The `GPUDevice` has an important property named `queue`, which provides access to a `GPUQueue`. To perform GPU operations, an application needs to call the methods of the `GPUQueue`, which include the following three:

* `writeBuffer`—updates data in a buffer object on the GPU
* `writeTexture`—updates data in a texture object on the GPU
* `submit`—tells the GPU to perform one or more commands

The `submit` method is particularly important because it tells the GPU what tasks to execute (graphical rendering or general-purpose computation). To be specific, `submit` accepts the commands created by the `GPUCommandEncoder` discussed earlier. Once this is called, the GPU will start executing commands in the buffer.

After calling `submit`, an application can monitor the execution of the queue's commands by calling `onSubmittedWorkDone`. This returns a `Promise` that resolves after the queue finishes its processing tasks.

## Canvas Element
