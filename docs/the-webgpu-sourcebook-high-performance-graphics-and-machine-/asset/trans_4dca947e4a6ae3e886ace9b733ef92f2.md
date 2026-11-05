
Aside from the shaders and the uniform/vertex buffers, most of the code in the `Ch05_Cubes` project is like the code in previous projects. But there's a major difference in the code that creates the render pipeline. This is given as follows:

```
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
        topology: "triangle-strip",
        stripIndexFormat: "uint16",
        frontFace: "cw",
        cullMode: "back"
    }
});
```

In this code, the `primitive` property is different than in previous examples. The `stripIndexFormat` identifies the format of the values in the index buffer. This can be set to `uint16` for 16-bit values and `uint32` for 32-bit values.

The `frontFace` and `cullMode` properties relate to *culling*—removing triangles depending on which way they're facing. For example, if you want to display a teapot in a scene, you only want the triangles facing the viewer to be rendered. The triangles in the rear can be omitted, or *culled*, from the scene.

To configure culling, two steps must be performed:
1. Use the `frontFace` property to identify front-facing triangles. If this is set to `cw`, a triangle will be considered front-facing if its vertices are oriented clockwise. If this is set to `ccw`, a triangle will be considered front-facing if its vertices are oriented counter-clockwise.
2. Use the `cullMode` property to select triangles to be culled. If this is set to `back`, back-facing triangles will be culled. If this is set to `front`, front-facing triangles will be culled. If this is set to `none` (the default value), no triangles will be culled.

If configured correctly, culling can dramatically improve rendering performance. But it's important to make sure that the vertices used to create triangles are arranged in a consistent clockwise or counter-clockwise manner.

In the `Ch05_Cubes` application, `frontFace` is set to `cw`, which means clock-wise triangles will be treated as facing forward. The `cullMode` property is set to `back`, which means back-facing triangles will be culled.

## Launching the Draw Operation

The `Ch05_Cubes` code takes advantage of indexed rendering and instanced rendering. This is accomplished with the following line of code:

```
renderPass.drawIndexed(30, 3);
```

Because the `drawIndexed` method is used, the renderer will read vertices using values in an index buffer. To be precise, it will read 30 values from the index buffer and use them to read 30 vertices from the vertex buffer.

The second argument of `drawIndexed` identifies how many copies, or *instances*, of each shape should be created. In this case, the renderer will draw three instances of the cube.

To separate the three copies, the vertex shader needs to know which instance each vertex belongs to. It accesses this information through the function's `@builtin(instance_index)` parameter, as shown in the following code:

```
fn vertexMain(
    @location(0) coords: vec3f, 
    @location(1) colors: vec3f, 
    @builtin(instance_index) instance: u32) -> DataStruct
```

The shader uses the `instance` parameter to update the z-values of different instances. To be specific, if the instance index is 1, the vertex coordinate's z-value is reduced by 5. If the instance index is 2, the z-value is reduced by 10. In this manner, the vertex shader separates the three copies along the z-axis.

## Summary

To create realistic three-dimensional scenes, developers need to be familiar with many different concepts and operations. A transformation is an operation that adjusts vertices by multiplying them by matrices. This chapter has focused on linear transformations, which include scaling, translation, and rotation.

In WebGPU applications, we can create transformation matrices by calling methods of the open-source `wgpu-matrix` package. In particular, the `mat4` object has several useful methods that provide matrix elements in `Float32Array`s. The `scaling` method creates scaling matrices, the `translation` method creates translation matrices, and the `rotation` method creates rotation matrices.

During rendering, transformation is performed by vertex shaders, which multiply vertex coordinates by transformation matrices. These matrices don't change from vertex to vertex, so they shouldn't be stored in vertex buffers. Instead, they're commonly passed to the GPU using uniform buffers, whose content remains constant from vertex to vertex. Creating a uniform buffer is essentially like creating a vertex buffer, but it needs to be added to a bind group, which needs to be described in a bind group layout.

The `Ch05_Cubes` application created three transformation matrices with `wgpu-matrix` and passes them to the GPU using uniform buffers. The `model` matrix sets the object's position, the `view` matrix accounts for the viewer's location, and the `projection` matrix creates the viewing region that displays objects with perspective. As a result, objects farther from the viewer appear smaller.

# Lighting, Textures, and Depth6

DOI: [10.1201/9781003422839-6](https://doi.org/10.1201/9781003422839-6)

[Chapter 5](#chapter5.xhtml) explained how transformations make it possible to position and orient objects in a viewing region. Transformations are important, but if you want to create realistic scenes in three dimensions, there are other issues to wrestle with. This chapter looks at three important topics in graphical rendering: lighting, textures, and depth.

Lighting refers to the process of changing an object's color depending on light sources in the scene. Objects far from a light source should be darker than objects near a light source, and shiny objects should reflect more light than dull objects. This chapter presents two models that mathematically determine how an object's color should be set: the Phong model and the Blinn–Phong model.

Like buffers, textures contain data that can be passed from the application to the GPU. The difference is that textures contain pixel data and are stored in special memory on the GPU. Using samplers, a fragment shader can read the pixel data and assign colors to fragments.

The last section of this chapter discusses two types of tests that fragment shaders can perform. A depth test checks a fragment's depth to see if it should be displayed in the scene or discarded. A stencil test compares values in a specially configured texture to reference values to determine how fragments should be processed.

## Lighting

To make a two-dimensional scene appear to have three dimensions, it isn't enough to place vertices in a rendering volume. To create the illusion of depth, objects need to reflect light differently based on their orientation relative to a light source.

Many models have been developed to determine how light reflects from an object's surface. This section looks at two popular models: the Phong model and the Blinn–Phong model. In both cases, the methodology contains three steps:
1. Decide on one or more light sources. Pass this information to shaders in uniform buffers.
2. For each vertex, find the vector perpendicular to the surface. This is called the normal vector. Pass the vector data to shaders as part of the vertex buffer.
3. Using light sources and normal vectors, the fragment shader sets the color of each fragment using the lighting model.

This discussion presents the mathematics underlying both models. Then it presents the code in the `Ch06_ShinySphere` project, which uses Blinn–Phong shading to illuminate a sphere.

### The Phong Model

In 1973, a Ph.D. dissertation by Bui Phong presented a method of simulating the reflection of light from a surface. This model treats light sources as point sources and splits each source into three components:
