
To the best of my knowledge, the Khronos Group has never formally stated that Vulkan is OpenGL's replacement. However, the latest version of OpenGL (4.6) is seven years old, and the latest version of Vulkan (1.3.270) was released less than a month ago.

## WebGPU

In 2017, the Khronos Group started to explore possibilities for the next generation of browser-based graphics, which they called WebGL Next. Apple's developers saw the potential of accessing the GPU in web applications, and they realized that creating a proprietary technology would be pointless.

With this in mind, Apple proposed an API named `WebGPU` based on their Metal language. The Mozilla Foundation, which leads the development of the free Firefox browser, proposed a similar API based on Vulkan. In time, the WebGPU API has incorporated features of Vulkan, Metal, and Direct3D 12.

Google has taken the lead with WebGPU integration, and the latest versions of Chrome (for Windows and macOS systems) enable WebGPU by default. Microsoft's Edge browser supports WebGPU, and Firefox users can enable WebGPU by setting the `dom.webgpu.enabled` flag.

## OVERVIEW OF WebGPU DEVELOPMENT

Now that you understand what WebGPU is, I'd like to provide a simple introduction to WebGPU development. In general, the code that makes up a WebGPU application is about 90% JavaScript and 10% WebGPU Shader Language (WGSL). To be more specific, coding a non-trivial WebGPU application requires three steps:

1. Create the JavaScript objects needed to access the GPU.
2. Create the JavaScript objects containing data and instructions to be processed by the GPU.
3. Send the data and instructions to the GPU for execution.

Steps 1 and 2 rely on JavaScript, and if you're already familiar with the language, then most of the API won't present any difficulty—you simply create objects and call their methods. But there are a *lot* of objects that need to be created, and it can be difficult to keep track of them. Thankfully, once you've coded a working application, it's straightforward to use similar code in other applications.

Step 3 is the hard part. To execute code on a GPU, you need to write special programs (*shaders*) in the WebGPU Shader Language (WGSL). WGSL is like the C programming language, but it's stripped down to focus on crunching numbers. That is, you won't need string-handling functions and you probably won't use a lot of pointers. The goal is to process numbers at high speed, and the better you understand linear algebra, the easier you'll find it to write shaders.

There are two main types of WebGPU applications:

* *graphical applications* display graphics in an HTML canvas
* *compute applications* perform a computational task, such as operating on matrices or analyzing data with machine learning

The following discussion explores the process of coding both types of applications.

### Graphical Application Development

At a high level, the purpose of a graphical WebGPU application is to define the content of an HTML canvas. To be precise, the goal is to transform a three-dimensional world into a two-dimensional scene, and display the scene in the canvas. This transformation process is called *rendering*.

To implement rendering in WebGPU, an application needs to create several objects in JavaScript, including a `GPURenderPassEncoder` and a `GPURenderPipeline`. The application also needs to create special objects that contain the data needed by the GPU to define the graphical scene.

In addition to providing data, the application needs to deliver instructions to the GPU that tell it how to position the scene's objects and compute the objects’ colors. These instructions must be provided in two programs:

* vertex shader—tells the GPU where to place objects in the scene
* fragment shader—tells the GPU what colors and depths to assign to the scene's fragments

These programs must be written in WGSL, and the following code shows what a simple vertex shader looks like:

```
@group(0) @binding(0) var<uniform> rotMat: mat4x4f;

@vertex
fn vertexMain(@location(0) coords: vec2f) -> @builtin(position) vec4f {    
    return rotMat * vec4f(coords, 0.0, 1.0);
}
```

This may look scary, but once you become acquainted with WGSL's data types (such as `mat4x4f` and `vec4f`) and attributes (such as `@vertex` and `@builtin`), you'll find this code to be straightforward. [Chapter 4](#chapter4.xhtml) discusses WGSL's features in glorious detail.

### Compute Application Development

In addition to graphical rendering, WebGPU applications can tell the GPU to crunch numbers. Throughout this book, we'll call these applications *compute applications*. Popular uses of compute applications include machine learning, image processing, frequency analysis, and matrix operations.

Compute applications are usually simpler to code than graphical applications. There are fewer JavaScript objects to be created, and there's no need to access a canvas. Instead of being concerned with vertex buffers, an application can store its data in storage buffers, which are easier to work with.

In addition, compute applications don't require vertex shaders and fragment shaders, as graphical applications do. Only one type of shader is needed—the *compute shader*. Like vertex shaders and fragment shaders, compute shaders are written in WGSL. The following code shows what a basic compute shader looks like:

```
@binding(0) @group(0) var<storage, read_write> data : array<f32, 32>;

@compute @workgroup_size(4)
fn computeMain(
    @builtin(global_invocation_id) id : vec3<u32>,
    @builtin(workgroup_id) wg_id : vec3<u32>,
    @builtin(local_invocation_id) local_id : vec3<u32>)
{
    data[id.x] = f32(wg_id.x) * data[id.x] + f32(local_id.x);
}
```

One major difference between compute applications and graphical applications is that a compute application can organize the GPU's processing into *work groups*. The elements of a work group, called *invocations*, can access memory specifically allocated for their group. This enables the group's invocations to work together and enables the shader to synchronize their operation.

## Example Code

The best way to learn WebGPU is to get your hands dirty and wrestle with working code. For this reason, every chapter and appendix of this book has at least one example application. The code is freely available from my Github page at [https://github.com/mattscar/webgpu_book](https://github.com/mattscar/webgpu_book).

Every project folder contains a file named `index.html` and a JavaScript file (`*.js`). `index.html` defines the structure of the web page, and the JavaScript file contains code to be executed when the page is opened. You can launch many of the applications simply by opening the HTML file (`index.html`) in a browser.

Unfortunately, many applications need to access external files. For these applications, you'll get an error if you open `index.html` in a browser. One way to get around this is to launch a local HTTP server and serve the page locally. The Node ecosystem provides the `http-server` package for this purpose, and [Appendix A](#appa.xhtml#appa) explains how to install Node and the `http-server` package.

## Summary

This chapter has introduced the topic of WebGPU, from its history to its current adoption. Simply put, WebGPU makes it possible for web applications to access the client's GPU. By accessing the GPU, applications can render graphics and crunch numbers at high speed. Applications of the first type are called graphical applications, and applications of the second type are called compute applications.

This book explains how to code graphical and compute applications using WebGPU. The theory and practice aren't easy to grasp, but if you follow best practices, the performance gains can be extraordinary. With great power comes great complexity…

# Fundamental Objects2

DOI: [10.1201/9781003422839-2](https://doi.org/10.1201/9781003422839-2)
