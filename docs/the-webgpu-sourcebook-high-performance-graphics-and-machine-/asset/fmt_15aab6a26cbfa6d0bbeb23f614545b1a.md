
This code is similar to that of the `ch06_simpletexture` code presented in [Chapter 6](#chapter6.xhtml). The texture has the `rgba8unorm` format, which means each texel stores red, green, blue, and alpha components as 8-bit unsigned normalized integers. The usage property includes `RENDER_ATTACHMENT`, which means it can be displayed in a rendering application. `usage` doesn't include `GPUTextureUsage.STORAGE_BINDING`, so its content is read-only.

Some WebGPU implementations don't support read-write textures, so the application needs to create a second texture to hold the filtered texels. This texture will be written to, so it needs to be created as a `storage texture`. The following code shows how this works:

```
// Create texture to hold storage image
const storageTexture = device.createTexture({
    size: [imageBitmap.width, imageBitmap.height],
    format: "rgba8unorm",
    usage:
        GPUTextureUsage.TEXTURE_BINDING |
        GPUTextureUsage.COPY_DST |
        GPUTextureUsage.STORAGE_BINDING
});
```

The output texture will have the same size as the input texture, so the dimensions are set to `imageBitmap.width` and `imageBitmap.height`. The `STORAGE_BINDING` flag indicates that it will serve as a storage texture, which means shaders can access it as a variable with the `texture_storage_2d` type.

## Create the Compute Pipeline

After creating the textures, the application creates three more objects: the shader module for the compute shader, the compute pass encoder, and the compute pipeline. The following code creates these objects and forms the association between them:

```
// Create the shader module
const computeModule = device.createShaderModule({
    label: "Shader module 0",
    code: computeCode
});

// Create the compute pass encoder
const computePass = encoder.beginComputePass({
    label: "Compute Pass 0"
});

// Define the compute procedure
const computePipeline = device.createComputePipeline({
    label: "Compute Pipeline 0",
    layout: "auto",
    compute: {
        module: computeModule,
        entryPoint: "computeMain",
        constants: {
            group_size_x: 16,
            group_size_y: 16
        }
    }
});
computePass.setPipeline(computePipeline);
```

This code creates the `computeModule` from the content of the `computeCode` string. Then the shader module is used to initialize the compute pipeline. In addition to setting the shader module and entry point, `createComputePipeline` provides two constants (`image_width` and `image_height`), which can be accessed by the compute shader as overridden variables. The last line of this code associates the pipeline with the compute pass encoder.

Next, the application defines the data for the compute operation by creating a bind group that contains the two textures. The following code shows how this is accomplished:

```
// Create the bind group
let computeBindGroup = device.createBindGroup({
    layout: computeBindGroupLayout,
    entries: [
    {
        binding: 0,
        resource: imageTexture.createView({
            dimension: "2d",
        })
    },
    {
        binding: 1,
        resource: storageTexture.createView({
            dimension: "2d",
        })
    }]
});
computePass.setBindGroup(0, computeBindGroup);
```

After the bind group is created, the last line associates it with the compute pass encoder and binds it to the value 0. As a result, shaders can access its resources by setting the `@group` attribute to 0 and the `@binding` attribute to the resource's binding value.

After associating the compute pass encoder with its instructions (`computePipeline`) and data (`bindGroup`), the application encodes the computation commands with the following code:

```
// Encode compute commands
computePass.dispatchWorkgroups(40, 40);

// Complete encoding compute commands
computePass.end();
```

The argument of `dispatchWorkgroups` tells the compute shader to process the data using a 40-by-40 grid of work groups. Each work group contains a 16-by-16 grid of invocations, so there are a total of 640-by-640 invocations. As a result, each invocation can process one pixel of the input image using its global ID.

## The Compute Shader

The compute shader is quite simple. Each invocation calls `textureLoad` to load a texel from the input image. Then it converts the RGB values to grayscale and calls `textureStore` to write the grayscale to the texture storage.

```
@group(0) @binding(0) var in_tex : texture_2d<f32>;
@group(0) @binding(1) var out_tex : texture_storage_2d<rgba8unorm, write>;

override group_size_x: u32;
override group_size_y: u32;

@compute @workgroup_size(group_size_x, group_size_y)
fn computeMain(
    @builtin(global_invocation_id) global_id: vec3<u32>) {

    var x = global_id.x;
    var y = global_id.y;
    var k = array<f32, 9>(-1.0, -1.0, -1.0, -1.0, 9.0, -1.0, -1.0, -1.0, -1.0);

    // Load the texel at the given position
    var texel: vec4f =
        k[0] * textureLoad(in_tex, vec2(x-1, y-1), 0) +
        k[1] * textureLoad(in_tex, vec2(x,   y-1), 0) +
        k[2] * textureLoad(in_tex, vec2(x+1, y-1), 0) +
        k[3] * textureLoad(in_tex, vec2(x-1, y), 0) +
        k[4] * textureLoad(in_tex, vec2(x,   y), 0) +
        k[5] * textureLoad(in_tex, vec2(x+1, y), 0) +
        k[6] * textureLoad(in_tex, vec2(x-1, y+1), 0) +
        k[7] * textureLoad(in_tex, vec2(x,   y+1), 0) +
        k[8] * textureLoad(in_tex, vec2(x+1, y+1), 0);

    // Store result to the storage texture
    textureStore(out_tex, vec2(x, y), texel);
}
```

In this code, `k` contains the elements of the image-sharpening kernel. Each invocation multiplies the elements of `k` by the 3-by-3 block of texels located by its global ID. Then the sum is written to the output texture using the `textureStore` method.

While fragment shaders read texels using `textureSample`, this compute shader reads texel data using `textureLoad`. Unlike `textureSample`, `textureLoad` requires integer coordinates and doesn't use a sampler. Another important difference between the two functions is that compute shaders can't call `textureSample`.

## Displaying the Texture

After the compute shader completes, the application creates a render pipeline to display the storage texture in the canvas. This code resembles that from [Chapter 6](#chapter6.xhtml), but there's one interesting point: the vertex/fragment shaders access the texture as a `texture_2d` instead of `texture_storage_2d`. This clarifies the point that there's no fundamental difference between storage textures and regular textures.

## Video Processing

One of the most fascinating capabilities of WebGPU is its ability to read frames of a video source and process them as textures. This makes it possible to perform the same operations on video as those performed on regular images. The general process of processing video with WebGPU consists of four steps:

1. Create, configure, and play an `HTMLVideoElement`.
2. Create a `VideoFrame` for each frame.
3. Create a texture from each `VideoFrame`.
4. Process the texture in a shader.

This section explores these steps and shows how they can be performed in code. A later section presents an application that processes frames received from a `*.webm` file.

### Video Elements

HTML5 makes it possible to insert <video> elements in web pages. In JavaScript, these elements are accessed as `HTMLVideoElement`s, and applications can create them by calling `document.createElement` with the argument set to `video`. `HTMLVideoElement` plays a central role in this discussion, so it's a good idea to be familiar with its inheritance hierarchy. This is illustrated in [Figure 10.6](#chapter10.xhtml#fig10_6).

![Figure 10.6 HTMLVideoElement inheritance hierarchy.](images/fig10_6.jpg)

[Figure 10.6](#chapter10.xhtml#b10fig10_6) `HTMLVideoElement` inheritance hierarchy.
