
Similarly, `storageBarrier` synchronizes access to storage buffers and storage textures. When an invocation reaches this function, it will halt until every other invocation in the workgroup finishes accessing storage data.

`WGSL` doesn't provide any barriers that affect invocations in different workgroups. The only way to make sure all the invocations have reached a given point is to wait for the GPU's processing to terminate. Another option is to use the atomic variables and operations described later in the chapter.

## Workgroup Memory
If you want invocations to be able to access workgroup memory, you need to declare a variable in the workgroup address space. The main advantage of this memory is that, *in theory*, it should be faster to access than data in a storage buffer.

One disadvantage is that many devices don't provide a great deal of memory for workgroups. On my system, the maximum workgroup storage size is 32,768 bytes. You can check this on your system by accessing the `maxComputeWorkgroupStorageSize` limit provided by the `GPUAdapter` object.

```
// Access the maximum number of bytes in workgroup memory
const maxWorkGroupMemory = adapter.limits.maxComputeWorkgroupStorageSize;
```

To demonstrate how workgroup memory is accessed, the following code defines a variable in the workgroup address space that contains 32 vectors of four floating-point values each:

```
var<workgroup> wg_data: array<vec4f, 32>
```

With this declaration in place, an invocation can access the workgroup's data using its local ID, as in the following code:

```
let v = wg_data[local_id]
```

Unlike memory in buffers and textures, workgroup memory can't be allocated or initialized in JavaScript. Workgroup memory is de-allocated when the compute task is complete, so it's important to transfer results to a storage buffer before the compute shader finishes.

To clearly distinguish variables intended for a single invocation, WGSL makes it possible to declare variables in the private address space. This is shown in the following declaration:

```
var<private> private_data: array<vec4f, 32>
```

As a result, each invocation can access `private_data`. However, because it's stored in private memory, invocations can't share data as they can in workgroup memory.

## Example Application—Simple Computation
The code in the `Ch08_SimpleCompute` project demonstrates how compute shaders can be coded and executed. It creates eight workgroups, each containing four invocations. Each invocation performs four operations:
1. Reads a value from a storage buffer using its global ID (`global_invocation_id`)
2. Multiplies the value by the workgroup ID (`workgroup_ID`)
3. Adds the invocation's ID inside the workgroup (`local_invocation_id`)
4. Writes the value back to the storage buffer

Initially, the storage buffer contains 32 values set to 1.0. When processing is finished, the code updates the page with the input vector and output vector. [Figure 8.3](#chapter8.xhtml#fig8_3) shows what the output looks like.

![Figure 8.3 The Ch08_SimpleCompute application.](images/fig8_3.jpg)

[Figure 8.3](#chapter8.xhtml#b8fig8_3) The Ch08_SimpleCompute application.

This demonstration of `WebGPU`'s compute capability isn't particularly exciting, but it shows how compute shaders can be coded and how compute pass encoders and compute pipelines can be created.

### The Compute Shader
The compute shader in the `Ch08_SimpleCompute` application shows how a variable declaration can access a storage buffer and how the built-in variables can be accessed. Its code is given as follows:

```
@binding(0) @group(0) var<storage, read_write> data : array<f32, 32>;

override group_size: u32;

@compute @workgroup_size(group_size)
fn computeMain(
    @builtin(global_invocation_id) id : vec3<u32>,
    @builtin(workgroup_id) wg_id : vec3<u32>,
    @builtin(local_invocation_id) local_id : vec3<u32>)
{
    data[id.x] = f32(wg_id.x) * data[id.x] + f32(local_id.x);
}
```

As shown, the shader accesses a storage buffer named `data` as an array of 32 floating-point values. Because the declaration contains the keyword `read_write`, the shader can read and write to the buffer.

The compute shader declares a variable named `group_size`. Because the declaration starts with `override`, this is an overridden variable whose value is set when the compute pipeline is created. To be precise, its value will be set to 4 because this is the value given in the constants map provided in the `createComputePipeline` method.

The name of the entry point is `computeMain`, and it accesses three built-in variables available to compute shaders. The first is `global_invocation_id`, which identifies the invocation among all other invocations, the second is `workgroup_id`, which identifies the workgroup among all the workgroups, and the third is `local_invocation_id`, which identifies the invocation among the invocations in the workgroup.

The name of the entry point is preceded by `@workgroup_size(group_size)`. `group_size` is an overridden variable that equals 4, so each workgroup will have 4 invocations. Because there are 8 workgroups, there are a total of 32 invocations. This means `global_invocation_id` will run from 0 to 31, `workgroup_id` will run from 0 to 7, and `local_invocation_id` will run from 0 to 3.

No matter what dimensions your workgroups have, the identifiers must be declared as three-dimensional vectors. For example, if a workgroup has a single dimension, its invocations will need to access IDs using the first element of the vector. This explains why the workgroup ID is accessed as `wg_id.x` and the local ID is accessed as `local_id.x`.

### The Compute Pass Encoder and Pipeline
As mentioned earlier, the central data structures in a compute application are the compute pass encoder and the compute pipeline. The following code shows how these objects are created in the `Ch08_SimpleCompute` application.

```
// Create the compute pass encoder
const computePass = encoder.beginComputePass({
    label: "Compute Pass 0"
});
// Define the compute procedure
const computePipeline = device.createComputePipeline({
    label: "Compute Pipeline 0",
    layout: "auto",
    compute: {
        module: shaderModule,
        entryPoint: "computeMain",
        constants: {
            group_size: 4
        }
    }   
});
computePass.setPipeline(computePipeline);

// Access the bind group layout
const bindGroupLayout = computePipeline.getBindGroupLayout(0);

// Create the bind group
let bindGroup = device.createBindGroup({
    layout: bindGroupLayout,
    entries: [{
        binding: 0,
        resource: { buffer: computeBuffer }
    }]
});
computePass.setBindGroup(0, bindGroup);

// Encode compute commands
computePass.dispatchWorkgroups(8);

// Complete encoding compute commands
computePass.end();
```

This code doesn't create any timestamps, so the object in the `encoder.beginComputePass` method only has a label. The object in `device.createComputePipeline` has a label that describes the pipeline and a `compute` property that identifies the shader module, the entry point, and constants to be passed to the shader.

The `constants` property can be set to an object containing name–value pairs separated by a colon. In this case, it associates the name `group_size` with a value of 4. The compute shader will access this value through an overridden variable named `group_size`. This is a convenient way to set the workgroup size.

After the compute pipeline is created, the application associates it with the compute pass encoder. It also associates the encoder with a bind group containing the application's storage buffer.

After making these associations, the application calls `dispatchWorkgroups` to encode compute commands. Because the argument is set to 8, a total of 8 workgroups will be created. Afterward, the application calls the compute pass encoder's `end` method to complete the encoding process.

### Copying and Mapping Buffers
