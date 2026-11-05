
## Error Scopes

1. Push an error scope onto the stack.
2. Perform one or more operations that may produce an error.
3. Pop the error scope to check if the given error occurred.

For the first step, an application needs to call the `pushErrorScope()` method of the `GPUDevice`. This accepts a string that identifies the type of error that should be monitored. [Table 7.1](#chapter7.xhtml#tbl7_1) lists the three types of errors.

[Table 7.1](#chapter7.xhtml#b7tbl7_1) Detected error types

| ERROR ID || DESCRIPTION |
| --- | --- |
| out-of-memory || Not enough memory available to perform the operation |
| --- | --- |
| validation || Invalid inputs to the method (wrong data type or unacceptable value) |
| internal || Error related to system or WebGPU implementation |

After an error scope has been pushed onto the stack, an application can check to see if the error occurred by calling the `popErrorScope()` method. This returns a Promise that resolves to an object describing the first error captured in the scope. It's common to access the error object using a variable named `error`, as demonstrated in the following code:

```
 // Respond to error if error occurred
 device.popErrorScope().then((error) => {
     …
 });
```

If an error occurs, the variable will be of type `GPUError`, which provides a `message` property that identifies the nature of the error. In the following code, the application prints the error's message if an error occurred.

```
 device.popErrorScope().then((error) => {
     
     // Check if error occurred
     if(error) {
         
         // Print error message
         console.log(error.message);
     }
 });
```

Error scopes are helpful when an application attempts to create a rendering pipeline that may not be supported on the client's system. The following code checks to see if creating a rendering pipeline produces an internal error. If so, the application calls the `createSimplerPipeline()` method.

```
 // Monitor internal errors
 device.pushErrorScope("internal");
 
 // Attempt to create rendering pipeline
 const renderPipeline = device.createRenderPipeline(…);
 
 // Check to see if internal error occurred
 device.popErrorScope().then((error) => {
     if(error) {
         console.log("Couldn't create pipeline");
         createSimplerPipeline(…);
     }
 });
```

The `GPUDevice` is a subclass of `EventTarget`, so you can call its `addEventListener()` method to keep track of events. In particular, you can handle uncaptured errors by setting the first argument to uncapturederror. This is shown in the following code:

```
 // Handle errors that haven't been captured in error scopes
 device.addEventListener("uncapturederror", (event) => {

     // Display the error's message in the console
     console.error("Uncaptured error: ", event.error.message);
 });
```

The WebGPU specification has changed frequently in recent months. For this and other reasons, it's a good idea to employ error checking to make sure your application runs properly.

## Viewports and Scissor Rectangles

In every example application presented so far, the rendering has always occupied the entire canvas. The application identifies the canvas area when it provides the color attachments as part of creating the render pass encoder. The following code creates a view from the WebGPU context associated with the canvas:

```
 // Render to the WebGPU context of the canvas
 const renderPass = encoder.beginRenderPass({
     colorAttachments: [{
         view: context.getCurrentTexture().createView(),
         …
     }]
 });
```

If you don't want the rendering to take up the whole canvas, you can set the rendering area (called the *viewport*) by calling the `setViewport()` method of the `GPURenderPassEncoder`. This accepts six values, and [Table 7.2](#chapter7.xhtml#tbl7_2) lists them all.

[Table 7.2](#chapter7.xhtml#b7tbl7_2) Arguments of the setViewport method

| ARGUMENTS || TYPE || DESCRIPTION |
| --- | --- | --- |
| x || Integer || x-Coordinate of the upper left corner of the canvas |
| --- | --- | --- |
| y || Integer || y-Coordinate of the upper left corner of the canvas |
| width || Integer || Width of the rendering surface |
| height || Integer || Height of the rendering surface |
| minDepth || Integer || Minimum depth value (0 by default) |
| maxDepth || Integer || Maximum depth value (1 by default) |

An example will make this clear. Suppose you want the rendering of your application to be limited to the 100-by-100 square in the upper left of the canvas. In this case, you'd call `setViewport()` with the upper left corner set to (0, 0) and the dimensions set to 100 and 100. The following code shows how this works:

```
 // Set the boundaries of the rendering
 renderPass.setViewport(0, 0, 100, 100, 0, 1);
```

In addition to customizing the viewport, applications can define regions called *scissor rectangles* that tell the renderer which fragments should be discarded. This is accomplished by calling the `setScissorRect()` method of the `GPURenderPassEncoder`. This method accepts the coordinates of the upper left corner of the rectangle, followed by its width and height.

For example, suppose an application wants to discard all fragments outside the 150-by-250 rectangle whose upper left corner is at (20, 30). The following code defines a scissor rectangle for this purpose:

```
 // Set the boundaries of the scissor rectangle
 renderPass.setScissorRect(20, 30, 150, 250);
```

As a result of this code, any fragment outside the scissor rectangle won't be drawn. By default, the scissor rectangle has the same bounds as the viewport.

## Occlusion Queries

[Chapter 6](#chapter6.xhtml) explained how applications can discard fragments using depth and stencil testing. Applications can check how many fragments passed these tests by submitting *occlusion queries*. If only a small number of fragments pass, the application may want to draw simpler objects or use simpler shaders.

An application can create and configure occlusion queries by employing six steps:

1. Create a query set and identify it when creating the render pass encoder.
2. Create a buffer to hold the query results.
3. Call the `beginOcclusionQuery()` method of the render pass encoder.
4. After the rendering commands are finished, call `endOcclusionQuery()`.
5. Encode a command to record queries by calling `resolveQuerySet()`.
6. Destroy the query set by calling its `destroy()` method.

The following discussion explores these steps. In each case, it explains what objects and methods are needed and then shows how they can be implemented in code.

### Creating the Query Set

A `GPUQuerySet` object can hold multiple queries, and an application can create a set by calling the `createQuerySet()` method of the `GPUDevice`. This accepts a descriptor with the properties listed in [Table 7.3](#chapter7.xhtml#tbl7_3).

[Table 7.3](#chapter7.xhtml#b7tbl7_3) Query set descriptor properties

| PROPERTY || OPTIONAL? || DESCRIPTION |
| --- | --- | --- |
| label || Y || String identifier for the query set |
| --- | --- | --- |
| count || N || Number of queries that can be accessed |
| type || N || If the set contains occlusion queries (occlusion) or timestamps (queries) |

For occlusion queries, `count` must be set to an integer greater than 1, and `type` must be set to occlusion. For timestamp queries, `type` must be set to timestamp. [Chapter 8](#chapter8.xhtml) will discuss timestamp queries and show how they're used.

To demonstrate this, the following code creates a query set capable of holding four occlusion queries:

```
 // Create a new query set
 const querySet = device.createQuerySet({
     label: "Query Set 0",
     count: 4,
     type: "occlusion"
 });
```

After creating the query set, the application needs to associate it with the render pass encoder. This is accomplished by setting the `occlusionQuerySet` property of the object used in the `beginRenderPass()` method. In the following code, the render pass is configured to use the query set created earlier:
