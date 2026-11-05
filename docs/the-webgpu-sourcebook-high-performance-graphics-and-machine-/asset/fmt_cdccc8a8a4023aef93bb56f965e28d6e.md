
To see how this interpolation can be performed in JavaScript, it's important to be familiar with the `requestAnimationFrame` method. This tells the browser that the application wants to be notified when the window is redrawn. The method accepts a callback function that will be invoked just before the next repaint.

When the callback function is invoked, it receives an integer that identifies the number of milliseconds that have elapsed since `requestAnimationFrame` was called. In this manner, the application can keep track of the current time and set the interpolation properly. In the following code, the name of the callback function is `newFrame`, and it receives the elapsed time through an argument named `t`:

```
// The callback to be invoked when the window repaints
function newFrame(t) {
     … update transformation matrices …
    window.requestAnimationFrame(foo);
}
// Set the callback to be invoked
window.requestAnimationFrame(newFrame);
```

For animation to work properly, `requestAnimationFrame` needs to be called again at the end of the callback function. This tells the window to call `newFrame` the next time the screen is refreshed.

## Example Application—Animation

The code in the `Ch07_Animation` project demonstrates how animation can be performed using WebGPU. It creates a red triangle and initializes its transformation matrix to an identity matrix. Then it calls `requestAnimationFrame` with a callback function. When the function is called, the transformation matrix is updated to translate the triangle.

The entire animation lasts four seconds, and the nature of the triangle's movement is given as follows:

* For the first two seconds, translate the triangle right until it reaches the right edge of the viewing region.
* For the next two seconds, translate the triangle left until it reaches the right edge of the viewing region.

The callback function receives the current time and subtracts it from the old time. This elapsed time is used to update the transformation matrix in the application's uniform buffer. The following code shows how the callback function is coded.

```
// Called just before the window is repainted
function newFrame(currentTime) {

    // Skip first frame
    if(oldTime == 0.0) {
        oldTime = currentTime;
        window.requestAnimationFrame(newFrame);
        return;
    }
    // Compute elapsed time in seconds
    t = (currentTime - oldTime)/1000;
    oldTime = currentTime;

    // Update total time
    totalTime += t;

    // Stop animation after four seconds
    if (totalTime > 4.0) {
        return;
    }

    // Update the uniform buffer
    motionChange = totalTime < 2.0 ? t * motionPerSec : -t * motionPerSec;
    uniformData = mat4.translate(uniformData, [motionChange, 0.0, 0.0]);
    device.queue.writeBuffer(uniformBuffer, 0, uniformData);

    // Create the command encoder and the render pass encoder
    const encoder = device.createCommandEncoder();
    const renderPass = encoder.beginRenderPass({
        colorAttachments: [{
            view: context.getCurrentTexture().createView(),
            loadOp: "clear",
            clearValue: { r: 0.9, g: 0.9, b: 0.9, a: 1.0 },
            storeOp: "store"
        }]
    });

    // Set the vertex buffer and pipeline
    renderPass.setVertexBuffer(0, vertexBuffer);
    renderPass.setPipeline(renderPipeline);

    // Associate bind group with render pass encoder
    renderPass.setBindGroup(0, bindGroup);

    // Draw vertices
    renderPass.draw(3);
    renderPass.end();

    // Submit the render commands to the GPU
    device.queue.submit([encoder.finish()]);
    window.requestAnimationFrame(newFrame);
}
```

The callback's argument, `currentTime`, identifies the current time in milliseconds. The function computes the elapsed time, `t`, by subtracting `oldTime` from `currentTime` and dividing the difference by 1000. Then it adds the elapsed time to the total time. If this is greater than four seconds, the callback exits.

If `t` is less than 2.0, the triangle should move right. For this reason, `motionChange` is set equal to `t` times `motionPerSec`, which identifies how much the triangle should move per second. This value is used to update the transformation matrix in the `uniformData` array, which is written to the uniform buffer.

The command encoder needs to be rebuilt after each rendering, as does the render pass encoder. But the shader code doesn't change, so there's no need to reconstruct the shader module or the render pipeline. After the render pass encoder is created and configured, the callback function calls `draw` to launch the rendering operation. The callback function ends by calling `requestAnimationFrame` to ensure that it will be called when the window is refreshed.

## Summary

This chapter has covered a lot of ground. The first two sections, which discuss debug groups and error handling, are helpful when you're searching for elusive problems with an application. Similarly, occlusion queries make it possible to determine how many primitives are being displayed and how many are being discarded.

By default, WebGPU's rendering fills the entire area of its associated canvas. However, an application can configure the rendering area by configuring the viewport associated with the render pass encoder. Similarly, it can specify a specific portion of the rendering to be displayed by defining a scissor rectangle.

WebGPU doesn't provide any objects or methods for displaying text. For this reason, this chapter has explained how to create texture atlases from TrueType fonts. Once these atlases are available, an application can display characters by reading rectangles from the texture. In addition to displaying the characters, it's important to adjust the spacing with proper kerning.

The last part of the chapter discussed animation. The overall process is simple—rotate, scale, and translate objects by changing their transformation matrices over time. In practice, however, animation presents difficulties. It's crucial to understand how and when `requestAnimationFrame` executes callback functions and which WebGPU resources must be reconstructed each time the callback function is invoked.

# Compute Applications8

DOI: [10.1201/9781003422839-8](https://doi.org/10.1201/9781003422839-8)

This chapter puts aside graphical rendering and shows how WebGPU can be used to crunch numbers. Compute applications are like graphical applications in many respects, but they require different objects to manage the GPU's operations. For example, compute applications create compute pass encoders instead of render pass encoders and compute pipelines instead of render pipelines.

Compute shaders are simpler than vertex shaders and fragment shaders because they deal with basic numbers instead of vertices, textures, samplers, and fragments. But unlike vertex and fragment shaders, compute shaders are executed by *invocations* organized into *workgroups*. Understanding how to divide processing among invocations and workgroups is a major issue when coding compute applications.

The primary advantage of running compute shaders is performance. To measure this performance, WebGPU makes it possible to create timestamp queries. These queries run on the GPU and provide precise measurements of the time needed to execute commands.

When several invocations of a compute shader attempt to access a variable, race conditions can lead to undefined behavior. For this reason, WebGPU provides atomic variables, whose operations are always performed atomically. The last part of this chapter explains how to create these variables and update them in atomic functions. The chapter ends with an example project that shows how an atomic variable can be used in a compute shader to obtain the dot product of two long arrays of values.

## Introducing Compute Applications

The overall process of developing a compute application is like that of developing a graphical application. There are at least nine steps involved:
