
# WGSL Variable Declarations and Address Spaces

WGSL supports `let`, `const`, and `var`, but there are major differences between their usage in WGSL and JavaScript. When you use `let` or `const` in a shader, you're declaring a *value*. The declaration assigns a name to a value, but the data won't be stored anywhere. In addition, `let` can only be used inside a function, while `const` can be used inside and outside of functions.

When a declaration starts with `var`, it creates a *variable* whose data will be stored in memory. This is more complicated than using `let` and `const` because a `var` declaration needs to identify the type of memory that will contain the variable's data.

To set a variable's memory type, a declaration can follow `var` with the name of an *address space* between angle brackets. For example, the following code declares a 32-bit floating-point variable to be stored in the private address space:

```
var<private> foo: f32;
```

Another way to set a variable's type is to provide a value. In the following code, it's understood that the variable will store a floating-point value:

```
var<private> foo = 1234.0;
```

In these declarations, the `private` keyword indicates that the variable should be stored in the `private` address space. This is available for global variables declared outside of a shader function. If a variable is intended to be used inside a function, its address space should be set to `function`. If a variable is declared inside a function without an address space, it's understood that the variable will be stored in the `function` space. This is shown in the following code:

```
// Stored in the function address space
var foo = 1234.0;
```

[Table 4.5](#chapter4.xhtml#tbl4_5) lists all of the address spaces available for storing variables.

[Table 4.5](#chapter4.xhtml#b4tbl4_5) Address spaces for variables

| ADDRESS SPACE || DEFAULT ACCESS MODE || DESCRIPTION |
| --- | --- | --- |
| function || read–write || Variables declared inside functions |
| --- | --- | --- |
| private || read–write || Global variables |
| storage || read || Data in a storage buffer |
| uniform || read || Data in a uniform buffer |
| handle || read || Sampler and texture variables |
| workgroup || read–write || Data used by compute shaders |

[Chapter 3](#chapter3.xhtml) explained how an application can create resources that hold data intended for a shader. The two types of resources are *buffers*, which hold general-purpose data, and *textures*, which hold texture data. To access a resource, a shader needs to declare a variable in the `storage`, `uniform`, or `handle` address spaces. Variables that provide access to resources are called *resource variables*, and I'll discuss them throughout this chapter.

[Chapter 3](#chapter3.xhtml) also explained that attribute data (such as coordinates) changes from vertex to vertex. In contrast, uniform data remains constant (uniform) from one vertex to the next. For this reason, uniform data is stored in uniform buffers that are accessed through the `uniform` address space. [Chapter 5](#chapter5.xhtml) will discuss uniforms in greater depth.

The last two address spaces, `handle` and `workgroup`, will be discussed in later chapters. The `handle` space is only used by applications that access textures, which will be discussed in [Chapter 6](#chapter6.xhtml). The `workgroup` space is only used by applications creating compute shaders, which will be discussed in [Chapter 8](#chapter8.xhtml).

## Constants and Overridden Variables

As we'll see, passing data from the application (JavaScript) to a shader (WGSL) is usually a complex process. You need to create special resource objects (buffers and textures) and associate these resources with specially formatted data and other objects.

If you just want to set scalar values in a shader, you can take advantage of constants (which have nothing to do with the `const` keyword). As mentioned in [Chapter 3](#chapter3.xhtml), the `createRenderPipeline` method accepts an object that includes a `vertex` object and a `fragment` object. The `vertex` and `fragment` objects have an optional property named `constants` that can be set to a sequence of name–value pairs. The following code shows how this works:

```
// Create a render pipeline that defines constants
const renderPipeline = device.createRenderPipeline({
    layout: …,
    vertex: {
        module: …,
        entryPoint: …
        constants: {
            0: false,
            22: 5.4,
            num_pixels: 256,
       }
    },
});
```

In this code, `constants` is set to an object containing three name–value pairs separated by colons. Each name can be an integer or a string. Each value can be an integer, a floating-point value, or a Boolean value.

Inside a shader, these name–value pairs can be accessed through special variables called *overridden variables*. An overridden variable can be declared in one of two ways. If the constant name is an integer, the corresponding declaration starts with the `@id` attribute containing the name in parentheses. The general form of the declaration is given as follows:

```
@id(name) override var_name: type;
```

For example, if the `constants` object maps 0 to false, the corresponding declaration in a shader could be coded as follows:

```
@id(0) override example: bool;
```

Even though this variable isn't set to a value in the shader, it will be set to false when the shader executes.

If the constant name is a string, the `@id` attribute isn't needed. Instead, the variable's name needs to be set to the constant's name. For example, if the `constants` object maps `num_pixels` to 256, the corresponding declaration in the shader could be coded in the following way:

```
override num_pixels: u32;
```

The variable's value isn't set in the shader, but because of the `constants` object, `num_pixels` will be set to 256 when the shader executes.

Overridden variables are convenient when an application needs to pass simple scalars to a shader at compile time. They become particularly helpful when coding compute applications, which will be introduced in [Chapter 8](#chapter8.xhtml).

## Vertex Shaders

Now that you understand the basics of WGSL, let's look at how vertex shaders are coded. The following code presents the vertex shader used in the `Ch04_OrangeTriangle` application:

```
@vertex
fn vertexMain(@location(0) coords: vec2f, @location(1) colors: vec3f) -> @builtin(position) vec4f {
    return vec4f(coords, 0.0, 1.0);
}
```

This function is an entry point for a vertex shader because its name `vertexMain` is preceded by `@vertex`. It accepts two parameters (a `vec2f` and a `vec3f`) and produces a vector as a return value.

There are two aspects of this code that need to be explained: the `@location` attribute that precedes both parameters and the `@builtin` attribute that precedes the return value. In my opinion, these modifiers should be called *annotations* or *decorators* because *attribute* already has a specific meaning in WebGPU. However, the WGSL standard refers to them as attributes.

### The Location Attribute

The `@location` attribute makes it possible for shaders to access data in resources (buffers and textures). In the preceding code, this attribute precedes the shader's arguments, `coords`, and `colors`.

[Chapter 3](#chapter3.xhtml) explained how to create a vertex buffer containing the vertices of a triangle in two dimensions. Each vertex needs two attributes: the (x, y) coordinates and the RGB color of each vertex. The following code shows the vertex data is defined:

```
// Define vertex data (coordinates and colors)
const vertexData = new Float32Array([
    0.0, 0.5, 0.0, 1.0, 0.0,    // First vertex (green)
    −0.5, −0.5, 1.0, 0.0, 0.0,  // Second vertex (red)
    0.5, −0.5, 0.0, 0.0, 1.0    // Third vertex (blue)
]);
```

To make this data available to the shader, the application needs to create a vertex buffer. The following code shows how this can be done:
