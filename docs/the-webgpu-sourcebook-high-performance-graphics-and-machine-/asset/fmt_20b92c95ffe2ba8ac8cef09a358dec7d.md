
| deviceLostCallback || DeviceLostCallback || The callback function to be invoked if the connection to the device is lost |

| deviceLostUserdata || void\* || Data to be provided to the callback if the device connection is broken |

The second argument of `RequestDevice` identifies a function to be invoked when the request operation is finished. This callback function must return void and it requires the four parameters listed in [Table B.8](#appb.xhtml#tblb_8).

[Table B.8](#appb.xhtml#btblb_8) Parameters of the RequestDevice Callback

| PARAMETER || DATA TYPE || DESCRIPTION |

| --- | --- | --- |

| status || WGPURequestDeviceStatus || The status of the device request |

| --- | --- | --- |

| adapter || WGPUDevice || The requested device |

| message || char\* || Message that identifies request result |

| userdata || void\* || Associated user data |

As given in the table, the device object provided by the callback is a `WGPUDevice`, which is a C structure. To make the device accessible in C++ code, the `Acquire` function needs to be called. The following code shows how this works:

```
// Request device
adapter.RequestDevice(nullptr, deviceCallback, nullptr);

// Function called when request completes
void deviceCallback(WGPURequestDeviceStatus status,
    WGPUDevice cDevice, const char* message, void* data) {

    if (status == WGPURequestDeviceStatus_Success) {

        // Convert the C type device to the C++ class
        wgpu::Device device = wgpu::Device::Acquire(cDevice);
    }
    …
}
```

After acquiring the device, the application can call its functions. Like the GPUDevice discussed in [Chapter 2](#chapter2.xhtml), most of these functions create instances of other classes, such as `CreateCommandEncoder` and `CreateBindGroup`. The `GetQueue` function is particularly important because it provides access to the device's queue. The following discussion explains how the `CreateBuffer` function makes it possible to create a vertex buffer.

### Vertex Buffer and Layout

To set the triangle's vertices, the application needs to define the vertex coordinates and create a vertex buffer to hold them. The classes and functions that accomplish this are very similar to those discussed in previous chapters.

In code, vertex buffers are represented by instances of the `Buffer` class. To create a `Buffer`, an application needs to call the device's `CreateBuffer` function. This accepts a `BufferDescriptor` structure whose fields identify the buffer's properties. [Table B.9](#appb.xhtml#tblb_9) lists the different fields that can be set.

[Table B.9](#appb.xhtml#btblb_9) Fields of the BufferDescriptor structure

| FIELD || DATA TYPE || DESCRIPTION |

| --- | --- | --- |

| nextInChain || ChainedStruct\* || Points to specialized classes |

| --- | --- | --- |

| label || char\* || Desired label for the device |

| usage || BufferUsage || Methods of accessing the buffer |

| size || uint64\_t || Amount of data that can be stored |

| mappedAtCreation || bool || Identifies if the buffer is mapped to memory when created |

The `usage` field is particularly important because it identifies how the buffer can be accessed. This is set to the `BufferUsage` enumerated type, whose possible values are `MapRead`, `MapWrite`, `CopySrc`, `CopyDst`, `Index`, `Vertex`, `Uniform`, `Storage`, `Indirect`, and `QueryResolve`.

For vertex buffers, usage should include the `BufferUsage::Vertex` flag. This is shown in the following code, which creates a `BufferDescriptor`, sets its fields, and uses it to create a `Buffer`.

```
// Create a buffer descriptor and buffer
wgpu::BufferDescriptor buffDesc {
    .usage = wgpu::BufferUsage::Vertex | wgpu::BufferUsage::CopyDst,
    .size = 24
};
wgpu::Buffer vertexBuffer = device.CreateBuffer(&buffDesc);
```

For the `AppB_DawnTriangle` project, the application needs to store six floating-point values (two coordinates for each vertex) in the vertex buffer. The array of data can be defined with the following code:

```
// Define vertex data to be stored in the vertex buffer
const float vertexData[6] = { 0.0, 0.5, -0.5, -0.5, 0.5, -0.5 };
```

To write this data to the vertex buffer, the application needs to call the `WriteBuffer` function of the device's queue. This accepts the four arguments listed in [Table B.10](#appb.xhtml#tblb_10).

[Table B.10](#appb.xhtml#btblb_10) Arguments of the WriteBuffer function

| ARGUMENT || DATA TYPE || DESCRIPTION |

| --- | --- | --- |

| buffer || Buffer& || The buffer to receive data |

| --- | --- | --- |

| bufferOffset || uint64\_t || Byte offset into the buffer for writing data |

| data || void\* || The data to be written to the buffer |

| size || size\_t || The number of bytes to be written |

To demonstrate, the following code accesses the device's queue and calls `WriteBuffer` to encode a command that writes `vertexData` into `vertexBuffer`:

```
// Encode command to write data to buffer
device.GetQueue().WriteBuffer(vertexBuffer, 0, vertexData, sizeof(vertexData));
```

After creating the vertex buffer, an application needs to define the layout of the data being passed to the vertex shader. This is accomplished by creating a `VertexBufferLayout` structure. [Table B.11](#appb.xhtml#tblb_11) lists the fields of this structure and provides a description of each.

[Table B.11](#appb.xhtml#tblb_11) Fields of the VertexBufferLayout structure

| FIELD || DATA TYPE || DESCRIPTION |

| --- | --- | --- |

| arrayStride || uint64\_t || Number of bytes between each set of attributes |

| --- | --- | --- |

| stepMode || VertexStepMode || Indicates if the vertex buffer should be indexed by vertex or by instance |

| attributeCount || size\_t || Number of attributes passed to the vertex shader for each vertex |

| attributes || VertexAttribute\* || Describes each attribute passed to the vertex shader |

In the `AppB_DawnTriangle` project, the application passes two coordinates to each vertex to sets its location. Each coordinate is given as a floating-point value that occupies four bytes, so `arrayStride` should be set to 8 and `attributeCount` should be set to 1.

To identify the composition of each attribute, the application needs to set the `attributes` field to an array of `VertexAttribute` structures. Each `VertexAttribute` has three fields, and [Table B.12](#appb.xhtml#tblb_12) lists each of them.

[Table B.12](#appb.xhtml#tblb_12) Fields of the VertexAttribute structure

| FIELD || DATA TYPE || DESCRIPTION |

| --- | --- | --- |

| format || VertexFormat || The attribute's format |

| --- | --- | --- |

| offset || uint64\_t || The offset of the attribute in the element |

| shaderLocation || uint64\_t || The location to be associated with the attribute |

The `format` field identifies the number and type of the values that make up the attribute. This must be set to one of the values in the `VertexFormat` enumerated type, which include `Uint8x2`, `Sint32x3`, and `Unorm16x4`. In this example, each attribute contains two 32-bit floating-point values, so `format` should be set to `Float32x2`.

The `offset` field identifies how many bytes separate the attribute from the start of the element. In this example, each element only has one attribute, so `offset` will be 0. Similarly, because there's only one attribute per element, `shaderLocation` will be set to 0.

The following code shows how a `VertexAttribute` structure can be defined in code:

```
// Define the content of the vertex attribute
wgpu::VertexAttribute attr {
    .format = wgpu::VertexFormat::Float32x2,
    .offset = 0,
    .shaderLocation = 0
};
```

Once this is set, the `VertexBufferLayout` structure can be defined with the following code:

```
// Set the layout of the vertex buffer
wgpu::VertexBufferLayout vertLayout {
    .arrayStride = 8,
    .attributeCount = 1,
    .attributes = &attr
};
```
