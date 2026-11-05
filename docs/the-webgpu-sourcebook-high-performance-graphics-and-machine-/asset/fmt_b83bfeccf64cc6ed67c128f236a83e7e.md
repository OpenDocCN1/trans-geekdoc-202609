
Isotropic filtering is ideal when the viewing angle is perpendicular to the texture. But if a viewer looks at a textured object from an angle, the object should appear to stretch in one direction and shrink in the other. To maintain resolution, the renderer should read more samples in the stretched direction. This directional sampling is called *anisotropic filtering*.

In code, anisotropic filtering is enabled by setting the `maxAnisotropy` property to a value between 1 and 16. This identifies the maximum ratio of the number of samples to be read in one direction divided by the number of samples to be read in the other direction. For example, if `maxAnisotropy` is set to 4, the sampler will read a maximum of four times the number of samples in one direction over the number of samples in the other.

### Level of detail

As a viewer moves away from a texture, the texture's resolution should decrease. One way to accomplish this is by reading fewer samples from the texture. Another method is to take advantage of mipmapping. If the texture has mipmap levels, each level's image has a lower resolution than the one preceding it. That is, the Level 0 image has the highest resolution, the Level 1 image has the next highest, and so on.

Many sources refer to mipmap levels as *lods*, where *lod* stands for level of detail. An application can specify which lods should be used by setting values for the `lodMinClamp` and `lodMaxClamp` properties. `lodMinClamp` specifies the minimum mipmap level that should be employed, and `lodMaxClamp` specifies the maximum mipmap level. `lodMaxClamp` must be greater than or equal to `lodMinClamp`.

### Accessing external coordinates

If a shader tries to read texel data beyond the texture's boundary, a question arises regarding what value should be returned. An application can configure this by assigning values to the `addressModeU`, `addressModeV`, and `addressModeW` fields. These fields can be set to one of three values:

* `clamp_to_edge`—Texels beyond the texture are set to the texels at the texture's edge
* `repeat`—In-range coordinates are repeated beyond the texture
* `mirror_repeat`—Texels beyond the texture are set to the reflections of the corresponding in-range texels

The illustrations in [Figure 6.8](#chapter6.xhtml#fig6_8) show what happens when a shader reads texels outside of the texture's boundaries. In each case, the coordinates run from −0.25 to 1.25.

![Figure 6.8 Sampler addressing modes.](images/fig6_8.jpg)

[Figure 6.8](#chapter6.xhtml#b6fig6_8) Sampler addressing modes.

If nearest-neighbor filtering is employed, the `clamp_to_edge` mode is automatically used. If linear filtering is configured, the address mode depends on where the point is located. If the point lies on a horizontal or vertical border, a texel from an adjacent face will be selected. If the point lies on a corner, the texel will be set to the sum of the three adjacent texels.

### Comparison tests

The `compare` property configures a sampler to perform comparisons related to depth testing and stencil testing. When the sampler reads a value from a depth/stencil texture (the *sampled value*), it compares the value to a second value (the *reference value*), and the result of the comparison can be used in filtering operations. The nature of the test can be configured by setting `compare` to one of the values in [Table 6.8](#chapter6.xhtml#tbl6_8).

[Table 6.8](#chapter6.xhtml#b6tbl6_8) Comparison sampler values

| VALUE || DESCRIPTION |
| --- | --- |
| `never` || The comparison test never passes |
| --- | --- |
| `always` || The comparison test always passes |
| `equal` || The comparison passes if the two values are equal |
| `not-equal` || The comparison passes if the two values aren't equal |
| `less` || The test passes if the reference value is less than the sampled value |
| `less-equal` || The test passes if the reference value is less than or equal to the sampled value |
| `greater` || The test passes if the reference value is greater than the sampled value |
| `greater-equal` || The test passes if the reference value is greater than or equal to the sampled value |

These comparisons are important for applications that take advantage of depth testing and stencil testing. A later section of this chapter discusses these topics in more detail.

## Step 5: Update the Bind Group

[Chapter 5](#chapter5.xhtml) explained how bind groups associate resources like uniform buffers with numbers that serve as *binding values*. Shaders access a resource in a bind group by providing the resource's binding value (`@binding`) and the group's value (`@group`). This is shown in the following code:

```
@group(0) @binding(0) var<uniform> exampleVariable: dataStruct;
```

Like uniform buffers, textures and samplers must be added to a bind group before they can be accessed. If the texture created by `device.createTexture` is named `tex` and the sampler created by `device.createSampler` is named `sampler`, the following code adds both to the bind group:

```
// Create a bind group for a sampler and texture
let bindGroup = device.createBindGroup({
    layout: bindGroupLayout,
    entries: [{
        binding: 0,
        resource: sampler
    },
   {
        binding: 1,
        resource: tex.createView({
          dimension: "cube",
        })
   }]
});
```

As shown, the bind group doesn't access the texture directly. Instead, it calls the texture's `createView` method, which provides a specific view of the texture. This accepts an object with several properties, and [Table 6.9](#chapter6.xhtml#tbl6_9) lists them all.

[Table 6.9](#chapter6.xhtml#b6tbl6_9) View creation properties

| PROPERTY || REQUIRED? || DESCRIPTION |
| --- | --- | --- |
| `label` || N || Identifier for the view |
| --- | --- | --- |
| `dimension` || N || Format for the view (`1d`, `2d`, `3d`, `2d-array`, `cube`, or `cube-array`) |
| `aspect` || N || Aspect(s) of the texture are available (`all`, `depth-only`, or `stencil-only`) |
| `format` || N || Texture format (such as those listed in [Table 6.1](#chapter6.xhtml#tbl6_1)) |
| `arrayLayerCount` || N || Number of array layers in the texture |
| `baseArrayLayer` || N || Index of the first array layer to be accessed |
| `mipLevelCount` || N || Number of mipmap levels in the texture |
| `baseMipLevel` || N || Index of the first mipmap level to be accessed |

All of the textures presented in this book are two-dimensional, so the only properties that will be set are the `label` and the `dimension` property, which will be set to `2d`.

After creating the bind group, the application can associate it with the render pass encoder by calling the encoder's `setBindGroup` method. The first argument is a number that a shader can use to access the bind group's resources. For example, the following code associates the bind group with the number 0:

```
// Associate the bind group with the value of 0
renderPass.setBindGroup(0, bindGroup);
```

As a result of this code, a shader can access the group using the `@group(0)` attribute. The following discussion explains how fragment shaders access textures.

## Step 6: Access the Texture and Sampler in the Fragment Shader

Earlier in this chapter, I showed how a fragment shader can access data in a uniform buffer using the `@group` and `@binding` attributes. Fragment shaders can access textures and samplers using the same attributes. For example, the following code uses these attributes to declare variables for a sampler and texture.

```
@group(0) @binding(0) var sam : sampler;
@group(0) @binding(1) var tex : texture_2d<f32>;
```

This code presents two new data types that shaders can access: `sampler` and `texture_2d`. The following discussion looks at these and other data types used when accessing textures.

### Data types
