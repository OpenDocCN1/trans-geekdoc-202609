
# Compute Application Overview

## Quick Start Steps

1. Create the `GPUAdapter`, `GPUDevice`, and `GPUCommandEncoder` using the same code as in a graphical application.
2. Call the command encoder's `beginComputePass()` method to create a compute pass encoder.
3. Create one or more storage buffers and add them to one or more bind groups.
4. Write a compute shader and add it to a shader module.
5. Call the device's `createComputePipeline()` method with the shader module.
6. Associate the compute pipeline with the compute pass encoder.
7. Associate the bind group with the compute pass encoder.
8. Call the `dispatchWorkgroups()` method of the compute pass encoder.
9. Read the processed data from the buffer.

The two main objects in a compute application are the command pass encoder and the command pipeline. This section looks at both and shows how they can be created in code.

## Core Objects

### The Compute Pass Encoder

Just as a render pass encoder holds state data for graphical rendering, a compute pass encoder holds state data for general-purpose computation. An application can create a compute pass encoder by calling the `beginComputePass()` method of the `GPUCommandEncoder`. This accepts an object with two optional arguments:

* `label`—optional string identifier used in debugging
* `timestampWrites`—optional array of objects that define timestamp events

The second argument is important for applications that need to measure the elapsed time of an operation. I'll explain time stamps and the `timeStampWrites` argument later in the chapter.

After creating a compute pass encoder, an application can call its methods to associate the encoder with other objects. [Table 8.1](#chapter8.xhtml#tbl8_1) lists eight of these methods and provides a description of each.

[Table 8.1](#chapter8.xhtml#b8tbl8_1) Methods of the compute pass encoder

| METHOD | DESCRIPTION |
| --- | --- |
| `dispatchWorkgroups(count)` | Performs computations defined in the compute pipeline |
| `dispatchWorkgroupsIndirect(buffer, offset)` | Performs computation using parameters provided in the indirect buffer |
| `end()` | Marks the end of the commands to be set |
| `setPipeline(pipeline)` | Associates a compute pipeline with the encoder |
| `setBindGroup(group)` | Associates a bind group with the encoder |
| `insertDebugMarker()` | Insert a marker in the encoder's commands |
| `pushDebugGroup()` | Starts a debug group with the given label |
| `popDebugGroup()` | Ends the most-recently pushed debug group |

In a graphical application, the render pass encoder creates rendering commands based on methods like `draw`, `drawIndexed`, and `drawIndirect`. In a computational application, the compute pass encoder creates compute commands based on methods like `dispatchWorkgroups` and `dispatchWorkgroupsIndirect`.

Both methods tell the GPU to perform the operations defined in the compute pipeline. The difference is that `dispatchWorkgroupsIndirect` uses indirect rendering, which tells the GPU to access rendering parameters from a buffer on the device.

The `end()` method of the compute pass encoder performs the same operation as the `end()` method of the render pass encoder. It completes the recording of the encoder's commands, telling the encoder that the commands can be sent to the GPU through the device's queue.

The `setPipeline()` and `setBindGroup()` methods are necessary to associate the encoder with the objects needed for computation. `setPipeline()` associates the encoder with a compute pipeline, which identifies the nature of the computation to be performed. `setBindGroup()` associates the encoder with a bind group, which provides access to the resources (data) needed by the computational task.

### The Compute Pipeline

Like the render pipeline discussed in the preceding chapters, a compute pipeline defines the operations to be performed by the GPU. It can be created by calling the device's `createComputePipeline()` method, which accepts a descriptor with the properties listed in [Table 8.2](#chapter8.xhtml#tbl8_2).

[Table 8.2](#chapter8.xhtml#b8tbl8_2) Compute pipeline descriptor properties

| PROPERTY | REQUIRED? | DESCRIPTION |
| --- | --- | --- |
| `label` | N | Identifier for debugging |
| `compute` | Y | Describes the computation to be performed |
| `layout` | Y | Describes the arrangement of resources used in computation |

Just as the render pipeline has vertex and fragment properties that provide information about vertex and fragment shaders, the compute pipeline has a `compute` property that provides information about the compute shader to be executed. This must be set to an object with the three properties listed in [Table 8.3](#chapter8.xhtml#tbl8_3).

[Table 8.3](#chapter8.xhtml#b8tbl8_3) Compute module properties

| PROPERTY | REQUIRED? | DESCRIPTION |
| --- | --- | --- |
| `module` | Y | Shader module containing the compute shader |
| `entryPoint` | Y | Name of the entry point function in the compute shader |
| `constants` | N | Name–value pairs that can be accessed in the shader |

The `module` property must be set to a shader module, and the process of creating a shader module in a compute application is identical to that of creating one in a graphical application. That is, the application calls the device's `createShaderModule()` with an object containing the properties listed in [Table 8.4](#chapter8.xhtml#tbl8_4).

[Table 8.4](#chapter8.xhtml#b8tbl8_4) Shader module creation properties

| PROPERTY | REQUIRED? | DESCRIPTION |
| --- | --- | --- |
| `label` | N | Identifier for debugging |
| `code` | Y | String containing the shader code |
| `hints` | N | Map that defines compiler hints for the shader |
| `sourceMap` | N | Data used by developer tools |

The `layout` property required by `createComputePipeline()` can be set to a `GPUPipelineLayout` that describes the structure of the pipeline's bind groups. For the sake of simplicity, the example code in this book sets `layout` to `auto`, which tells the pipeline to form a bind group layout by examining the shader code.

For example, the following code creates a compute pipeline that tells the GPU to execute the shader in the module named `computeModule`. The entry point in the compute shader is named `computeMain`.

```javascript
// Creating a compute pipeline
const computePipeline = device.createComputePipeline({
    label: "Compute Pipeline 0",
    layout: "auto",
    compute: {
        module: computeModule,
        entryPoint: "computeMain"
    }
});
```

After the compute pipeline is created, it can be associated with the compute pass encoder by calling the encoder's `setPipeline()` method. If the encoder's name is `computePass`, the following code creates the association:

```javascript
// Associate the pipeline with the compute pass encoder
computePass.setPipeline(computePipeline);
```

As shown, it takes a lot less code to create a compute pipeline than a render pipeline.

## Buffer Operations

There are two major differences between the buffers used in (most) compute applications and those used in graphical applications:

1. Compute applications usually access data from storage buffers or storage textures. Uniform buffers aren't as common because of their small size.
2. After computation is finished, the application needs to retrieve the processed data from GPU memory.

In most graphical applications, buffer data moves in one direction—from the host to the GPU. But in a compute application, buffer data is transferred from the host to the GPU before computation, and from the GPU to the host after computation. This discussion focuses on storage buffers, and storage textures will be introduced in [Chapter 9](#chapter9.xhtml).
