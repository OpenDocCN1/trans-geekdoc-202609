
On some systems, the CPU and GPU access the same memory. On these shared memory systems, moving data to and from the GPU is simple. But on most systems, the GPU is located on a graphics card with its own separate memory. To access the GPU's memory, applications need to map and unmap buffers. Applications also need to copy data from one buffer to another. The following discussion presents both operations.

## Mapping and Unmapping Buffers

A buffer is *mapped* if its data can be accessed through an `ArrayBuffer`. After creating a buffer, an application can perform mapping operations by calling three of its methods:
* `getMappedRange(offset, size)`—returns an `ArrayBuffer` containing the mapped data of the `GPUBuffer` in the specified range
* `mapAsync(mode, offset, size)`—returns a `Promise` that resolves to an `ArrayBuffer` when the buffer is successfully mapped
* `unmap()`—destroys the mapped range of the buffer, allowing it to be used for other operations

If a buffer is created with the `mappedAtCreation` property set to true, its mapped content can be accessed using `getMappedRange`. This makes it easy to initialize its content.

To demonstrate this, the following code creates a buffer containing 16 bytes. Then it calls `getMappedRange` to access the underlying `ArrayBuffer` and sets four floating-point values in the `ArrayBuffer`.
```
// Create buffer
const computeBuffer = device.createBuffer({
    mappedAtCreation: true,
    size: 16,
    usage: GPUBufferUsage.STORAGE
});
 
// Access the mapped data
const buff = computeBuffer.getMappedRange();
 
// Set the content of the mapped data
new Float32Array(buff).set([1.0, 2.0, 3.0, 4.0]);
 
// Unmap buffer
computeBuffer.unmap();
```

After the GPU completes the computation, the application will want to read the buffer containing the processed data (the results). In this case, the application can call `mapAsync`. If the mapping was successful, the application can read the buffer's data by calling `getMappedRange` and destroy the mapping by calling `unmap`.

For example, suppose processed data is stored in a buffer named `procBuffer`, which was created with the `GPUBufferUsage.MAP_READ` flag. The following code accesses the `ArrayBuffer` containing the buffer's data.
```
// Establish a mapping
await procBuffer.mapAsync(GPUMapMode.READ);
// Read the mapped data in an ArrayBuffer
const procData = procBuffer.getMappedRange();
 
// Access the floating-point values
const floatData = new Float32Array(procData);
 
// Destroy the mapping
procBuffer.unMap();
```

As shown, `mapAsync` requires an argument that identifies how the buffer's mapped data will be accessed. This can be set to `GPUMapMode.READ` or `GPUMapMode.WRITE`.

When coding compute applications, it's important to understand how to map and unmap a buffer. The example code in this chapter and later chapters will use similar code to read and write data to compute buffers.

## Copying Buffers

If a GPU accesses memory separate from the GPU, applications can't directly map storage buffers for reading. Put another way, if a buffer's usage property includes `GPUBufferUsage.STORAGE`, it can't include `GPUBufferUsage.MAP_READ`. This means an application needs to perform four operations to read data from a storage buffer:
1. Create a mappable buffer whose usage includes `GPUBufferUsage.MAP_READ`.
2. Encode a command that copies the data from the storage buffer to the mappable buffer.
3. When the device is done executing its commands, map the mappable buffer to an `ArrayBuffer`.
4. Read data from the `ArrayBuffer`.

For Step 2, it's important to be familiar with the `copyBufferToBuffer` method of the `GPUCommandEncoder`. [Table 8.5](#chapter8.xhtml#tbl8_5) lists the five arguments of this method.

[Table 8.5](#chapter8.xhtml#b8tbl8_5) Arguments of the `copyBufferToBuffer` method

| ARGUMENT || TYPE || DESCRIPTION |
| --- | --- | --- |
| source || GPUBuffer || The buffer to copy data from |
| --- | --- | --- |
| sourceOffset || Integer || Byte offset into the source where copying should begin |
| destination || GPUBuffer || The buffer to receive data |
| destinationOffset || Integer || Byte offset into the destination where data should be copied |
| size || Integer || The number of bytes to be copied from the source buffer to the destination buffer |

Calling `copyBufferToBuffer` doesn't immediately copy the buffer's content. Instead, it encodes a command that tells the GPU to perform the copy operation. For this reason, it's important to call `copyBufferToBuffer` *after* the compute pass encoder has encoded the computational command(s), but *before* the encoder sends the commands to the GPU. The following code gives an idea of the necessary sequence of steps.
```
// Encode compute commands
computePass.dispatchWorkgroups(…);
 
// Complete encoding compute commands
computePass.end();
 
// Create mappable buffer
const mappableBuffer = device.createBuffer({ …
    usage: 
        GPUBufferUsage.COPY_DST | 
        GPUBufferUsage.MAP_READ
});
 
// Encode command to copy data into mappable buffer
encoder.copyBufferToBuffer(…);
// Submit the commands to the GPU
device.queue.submit([encoder.finish()]); 
```

As a result of this code, the mappable buffer will hold the copied data. The application can read the buffer's data by calling its `mapAsync` and `getMappedRange` methods. This process will be used to read result data in every compute application presented in this book.

## Workgroups and Invocations

In a graphical application, the `vertex shader` executes once for each vertex, and the `fragment shader` executes once for each fragment. But when you run a compute application, you can directly control how many times the `compute shader` is executed. This control is made possible through `workgroups`, and this section explains what they are and how they can be configured.

### Introduction to Workgroups

To understand how compute shaders execute, you need to be familiar with two terms:
* an *invocation* is a single execution of a `compute shader`
* a *workgroup* is a collection of `invocations`

An application specifies the number of `invocations` by setting the number of `workgroups` and the size of each `workgroup`. If there are four `workgroups` and each `workgroup` contains eight `invocations`, the `compute shader` will execute thirty-two times.

Why are `workgroups` important? There are two reasons: memory and synchronization. `Invocations` in the same `workgroup` can access shared memory specific to that `workgroup`. This group-specific memory is distinct from storage buffer memory, and in theory, shaders can access workgroup data much faster than storage data. This makes workgroup memory a good place to store intermediate computation results.

Normally, there's no way to know when one `invocation` executes relative to another. But `WebGPU` provides barriers that can make it possible to synchronize `invocations` in a `workgroup`. A `workgroup barrier` forces each `invocation` to halt until every other `invocation` has finished accessing data in workgroup memory. A `storage barrier` forces each `invocation` to halt until every other `invocation` has finished accessing data in storage memory. Note that these barriers can't synchronize `invocations` across different `workgroups`.

### Workgroup Analogy

Workgroups can be hard to grasp, so I'll present an analogy. Suppose a school contains multiple classrooms, and each classroom has a blackboard. Each classroom's blackboard can only be used by the students in that class. In addition, the school has a global blackboard that every student in the school can access.

Each student has two identifiers. The `Local ID` identifies the student inside the classroom, and the `Global ID` identifies the student across the entire school. Students in different classrooms may have the same `Local ID`, but no two students will ever have the same `Global ID`.
