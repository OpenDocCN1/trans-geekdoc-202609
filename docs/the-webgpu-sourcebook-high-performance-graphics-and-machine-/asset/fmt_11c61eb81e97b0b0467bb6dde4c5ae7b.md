
```
const computePass = timeSupport ?
    encoder.beginComputePass({
        timestampWrites: {
            querySet,
            beginningOfPassWriteIndex: 0,
            endOfPassWriteIndex: 1
        }}) :
    encoder.beginComputePass({})
```

Once the compute pass encoder is created, it will be able to deliver timestamp queries to the device.

## Encode Command to Record Timestamps

Applications encode rendering commands by calling methods like `draw` and encode compute commands by calling methods like `dispatchWorkgroups`. To tell the GPU to record timestamp queries, the application needs to call the command encoder's `resolveQuerySet` method. This requires five parameters, and [Table 8.7](#chapter8.xhtml#tbl8_7) lists each of them.

[Table 8.7](#chapter8.xhtml#b8tbl8_7) Parameters of the `resolveQuerySet` method

| PARAMETER || DATA TYPE || DESCRIPTION |
| --- | --- | --- |
| `querySet` || `GPUQuerySet` || The query set to hold the timestamp |
| --- | --- | --- |
| `firstQuery` || `unsigned int` || Index of the first query |
| `queryCount` || `unsigned int` || Number of timestamp queries to be performed |
| `destination` || `GPUBuffer` || The query buffer to hold the results |
| `destinationOffset` || `unsigned int` || Byte offset into the query buffer |

In the `Ch08_DotProduct` application, queries are contained in `querySet`, the index of the first query is 0, and the number of queries is 2. The timestamp data should be written at Byte 0 of `queryBuffer`. This is configured with the following code:

```
if (timeSupport) {
    encoder.resolveQuerySet(querySet, 0, 2, queryBuffer, 0);
}
```

This should be called after the operation, whose timing should be measured. It should be called before the command that copies the data from the query buffer to a staging buffer. After the GPU executes its commands, the application can access the timestamps using the same methods that read regular data from storage buffers.

## Atomic Variables and Functions

In a shader, hundreds or thousands of invocations may want to update a variable at the same time. For normal variables, this can result in unpredictable behavior. But if a variable is `atomic` and the invocations operate on the variable using `atomic functions`, each operation will be guaranteed to complete before another operation can start.

A variable can be made `atomic` if it contains integers and is stored in `workgroup memory` or `storage buffer memory`. In code, a variable is `atomic` if its declared type is `atomic<u32>`, `atomic<i32>`, or an array of these types. To demonstrate, the following code declares an `atomic` array of unsigned integers accessed in a `storage buffer`.

```
var<storage, read_write> counter: array<atomic<u32>>
```

As a result of this declaration, each element of the `counter` array can be updated using one of `WGSL`'s `atomic functions`. [Table 8.8](#chapter8.xhtml#tbl8_8) lists these functions and provides a description of each.

[Table 8.8](#chapter8.xhtml#b8tbl8_8) Atomic functions

| FUNCTION || DESCRIPTION |
| --- | --- |
| `atomicStore(atom_ptr, val)` || Stores the value in the atomic object |
| --- | --- |
| `atomicLoad(atom_ptr, val)` || Returns the value stored in the atomic object |
| `atomicExchange(atom_ptr, val)` || Stores the value in the atomic object and returns its original value |
| `atomicAdd(atom_ptr, val)` || Adds the value to the atomic object |
| `atomicSub(atom_ptr, val)` || Subtracts the value from the atomic object |
| `atomicMax(atom_ptr, val)` || Writes the value to the atomic object if it's larger |
| `atomicMin(atom_ptr, val)` || Writes the value to the atomic object if it's smaller |
| `atomicAnd(atom_ptr, val)` || Sets the atomic object to the AND of the atomic value and the value |
| `atomicOr(atom_ptr, val)` || Sets the atomic object to the OR of the atomic value and the value |
| `atomicXor(atom_ptr, val)` || Sets the atomic object to the XOR of the atomic value and the value |

The first argument of these functions is a `pointer` to the `atomic variable`, not the variable itself. For this reason, the first argument is commonly preceded by the reference operator, `&`. To demonstrate this, the following code atomically adds the value 5 to the address of the third element of the `counter` array:

```
atomicAdd(&counter[2], 5)
```

There are two more points to know about `atomic functions`. First, they return the value of the `atomic variable` before the operation is performed. Second, they can be called in `compute shaders` and in `fragment shaders`, but not in `vertex shaders`.

## Example Application—Dot Product

The code in the `Ch08_DotProduct` application demonstrates how a `compute shader` can create and operate on `atomic variables`. Each invocation reads two vectors, computes their `dot product`, and adds the `dot product` to an `atomic variable`. After displaying the result of the `dot product`, the application displays the time that was needed to execute the `compute command`. [Figure 8.4](#chapter8.xhtml#fig8_4) shows what this looks like.

![Figure 8.4 The Ch08_DotProduct application.](images/fig8_4.jpg)

[Figure 8.4](#chapter8.xhtml#b8fig8_4) The `Ch08_DotProduct` application.

This section describes the application's operation in five parts:

1. Creating the storage buffers
2. Configuring the compute pipeline
3. Executing the compute shader
4. Retrieving the result
5. Measure and display elapsed time

As will be shown, `atomic variables` are helpful when an application needs to keep track of a running total among several invocations.

### The Storage Buffers

The application passes data to the `GPU` in three `storage buffers`. The first two contain arrays of 1,024 integers. The third contains a single integer that identifies the result of the `dot product`. For each buffer, the application performs four operations:

* Creates a mapped buffer by calling `device.createBuffer`
* Accesses the buffer's mapped range by calling its `getMappedRange` method
* Creates an array containing the buffer's data
* Unmaps the buffer

The following code shows how these operations are implemented in the `ch08_dotproduct.js` source file.

```
// Set the number of values
const numVals = 1024;

// Create compute buffers
const aBuffer = device.createBuffer({
    mappedAtCreation: true,
    size: numVals * 4,
    usage: GPUBufferUsage.STORAGE 
});
const aRange = aBuffer.getMappedRange();

// Create compute buffers
const bBuffer = device.createBuffer({
    mappedAtCreation: true,
    size: numVals * 4,
    usage: GPUBufferUsage.STORAGE
});
const bRange = bBuffer.getMappedRange();

// Create compute buffers
const resBuffer = device.createBuffer({
    mappedAtCreation: true,
    size: 4,
    usage: 
        GPUBufferUsage.STORAGE | 
        GPUBufferUsage.COPY_SRC
});
const resRange = resBuffer.getMappedRange();

// Create the data arrays
const aArray = new Array(numVals);
const bArray = new Array(numVals);
const res = new Array([0]);

// Initialize vectors
for (let i = 0; i < numVals; i++) {
    aArray[i] = i + 1;
    bArray[i] = numVals - i;
}

// Create arrays in buffer memory
new Uint32Array(aRange).set(aArray);
new Uint32Array(bRange).set(bArray);
new Uint32Array(resRange).set(res);
// Unmap buffers
aBuffer.unmap();
bBuffer.unmap();
resBuffer.unmap();
```

When each buffer is created, the `mappedAtCreation` property is set to `true`. This enables the application to access the buffer's mapped data by calling `getMappedRange`. The `usage` property includes `GPUBufferUsage.STORAGE` to configure the buffer as a `storage buffer`. The last buffer, `resBuffer`, also has the flag `GPUBufferUsage.COPY_SRC` because the application will copy data from it.

After creating the buffers, the application stores an array of unsigned 32-bit integers inside each of them. The first buffer contains 1,024 integers that increase from 1 to 1,024. The second buffer contains 1,024 integers that decrease from 1,024 to 1. The third buffer contains a single integer whose value is 0. This buffer stores the result of the `dot product`.
