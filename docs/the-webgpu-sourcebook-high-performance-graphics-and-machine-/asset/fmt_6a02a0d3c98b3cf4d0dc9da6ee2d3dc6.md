
| `CopyTextureToBuffer(ImageCopyTexture *src, ImageCopyBuffer *dst, Extent3D const* copySize)` || Copies the content of a texture to a buffer |
| `CopyTextureToTexture(ImageCopyTexture *src, ImageCopyTexture *dst, Extent3D const* copySize)` || Copies the content of one texture to another |
| `Finish(CommandBufferDescriptor *desc)` || Ends the encoder's command recording |
| `InsertDebugMarker(char const* label)` || Add message to be displayed during debugging |
| `SetLabel(char const *label)` || Set label for the encoder to be displayed during debugging |
| `WriteTimestamp(QuerySet& set, uint32_t index)` || Add timestamp query to query set |

Of these functions, only two are necessary in rendering applications. The `BeginRenderPass()` function provides a render pass encoder that can be used to define the rendering process. The `Finish()` function is needed to end the encoding.

### Creating the render pass encoder

In Dawn, the render pass encoder is represented by the `RenderPassEncoder` class, and an application can create an instance by calling the `BeginRenderPass()` function of the `CommandEncoder`. This requires a `RenderPassDescriptor` that defines properties of the rendering to be performed. [Table B.22](#appb.xhtml#tblb_22) lists the fields of this structure.

[Table B.22](#appb.xhtml#btblb_22) Fields of the `RenderPassDescriptor` structure

| FIELD || DATA TYPE || DESCRIPTION |
| --- | --- | --- |
| `nextInChain` || `ChainedStruct*` || Points to specialized classes |
| --- | --- | --- |
| `label` || `char const*` || Text identifier |
| `colorAttachmentCount` || `size_t` || Number of color attachments |
| `colorAttachments` || `RenderPassColorAttachment*` || Color attachments |
| `depthStencilAttachment` || `RenderPassDepthStencilAttachment*` || Depth/stencil attachments |
| `occlusionQuerySet` || `QuerySet` || Container of occlusion queries |
| `timestampWrites` || `RenderPassTimestampWrites*` || Timestamp configuration |

Most of these fields are optional, but every rendering application needs to identify the color attachment(s) that serves as the basis for rendering. This requires creating one or more `RenderPassColorAttachment` structures, and [Table B.23](#appb.xhtml#tblb_23) lists each of its fields.

[Table B.23](#appb.xhtml#btblb_23) Fields of the `RenderPassColorAttachment` structure

| FIELD || DATA TYPE || DESCRIPTION |
| --- | --- | --- |
| `nextInChain` || `ChainedStruct*` || Points to specialized classes |
| --- | --- | --- |
| `view` || `TextureView` || Resource accessed by the color attachment |
| `resolveTarget` || `TextureView` || Subresource affected by the color attachment if multisampling is enabled |
| `loadOp` || `LoadOp` || How the view's initial color should be set |
| `storeOp` || `StoreOp` || Identifies if the view's color should be stored after the render pass |
| `clearValue` || `Color` || Color to serve as the view's initial color |

The most important field is `view`, which identifies the texture that serves as the target of the rendering process. If a `SwapChain` has been created, this field can be assigned to the result of the `SwapChain`'s `GetCurrentTextureView()` function.

The `loadOp` field identifies how the view's initial content should be set. If `loadOp` is set to `LoadOp::Load`, the view will retain its existing data. If it's set to `LoadOp::Clear`, the view's content will be set to the `Color` given by the `clearValue` field. In Dawn, `Color` is a structure with four fields of type `double`: `r`, `g`, `b`, and `a`.

The `storeOp` field specifies if the view's data should be stored when rendering is complete. If this is set to `StoreOp::Store`, the view's content will be stored after rendering. If it's set to `StoreOp::Discard`, the view's data will be discarded.

In the `AppB_DawnTriangle` project, the rendering is associated to the canvas through the `SwapChain` created earlier. This association is created by setting the `view` field to the `SwapChain`'s current texture view.

The initial content of the canvas should be set to light gray. To accomplish this, the `loadOp` field must be set to `LoadOp::Clear` and the `clearValue` field must be set to a `Color` structure whose components are (0.9, 0.9, 0.9, 1.0). The following code shows how this can be done:

```
 // Define render pass color attachment
 wgpu::RenderPassColorAttachment attachment {
     .view = swapChain.GetCurrentTextureView(),
     .loadOp = wgpu::LoadOp::Clear,
     .storeOp = wgpu::StoreOp::Store,
     .clearValue = {
         .r = 0.9,
         .g = 0.9,
         .b = 0.9,
         .a = 1.0 }
 };
```

Once the `RenderPassColorAttachment` is created, the application can set the `colorAttachmentCount` and `colorAttachments` fields of a `RenderPassDescriptor`. Then it can obtain a render pass encoder by calling the `BeginRenderPass()` function of the `CommandEncoder`. The following code shows how this can be done:

```
 // Create render pass encoder
 wgpu::RenderPassDescriptor renderDesc {
     .colorAttachmentCount = 1,
     .colorAttachments = &attachment
 };
 wgpu::RenderPassEncoder renderPass = encoder.BeginRenderPass(&renderDesc);
```

After obtaining a `RenderPassEncoder`, an application can configure the rendering process by calling its functions. This discussion focuses on the functions that associate the encoder with other rendering objects and functions that launch the drawing process. [Table B.24](#appb.xhtml#tblb_24) lists the functions that associate the encoder with objects.

[Table B.24](#appb.xhtml#btblb_24) `RenderPassEncoder` functions that associate objects

| FUNCTION || DESCRIPTION |
| --- | --- |
| `SetBindGroup(uint32_t index, BindGroup& group, size_t dynamicOffsetCount, uint32_t* dynamicOffsets)` || Associate the bind group with the encoder at the given index |
| --- | --- |
| `SetBlendConstant(Color* color)` || Associate the encoder with the color used for blending |
| `SetIndexBuffer(Buffer& buffer, IndexFormat format, uint64_t offset, uint64_t size)` || Set the buffer containing index values to be used during rendering |
| `SetLabel(char* label)` || Associate the label with the encoder to be displayed during debugging |
| `SetPipeline(RenderPipeline& pipeline)` || Set the render pipeline to be used during the render process |
| `SetScissorRect(uint32_t x, uint32_t y, uint32_t width, uint32_t height)` || Select a rectangular region to be displayed in the rendering |
| `SetStencilReference(uint32_t reference)` || Sets reference value to be used during stencil tests |
| `SetVertexBuffer(uint32_t slot, Buffer& buffer, uint64_t offset, uint64_t size)` || Associate the encoder with a buffer containing vertex data |
| `SetViewport(float x, float y, float width, float height, float minDepth, float maxDepth)` || Define the viewport used for rendering |

Most of these functions have been discussed in preceding chapters, and are straightforward to use and understand. The code in the `AppB_DawnTriangle` project uses two of these functions: `SetPipeline()` and `SetVertexBuffer()`. This is shown in the following code:

```
 // Create associations for the render pass encoder
 renderPass.SetPipeline(pipeline);
 renderPass.SetVertexBuffer(0, vertexBuffer);
```

After creating and configuring the render pass encoder, the application calls its functions that perform drawing operations. [Table B.25](#appb.xhtml#tblb_25) lists the functions involved.

[Table B.25](#appb.xhtml#btblb_25) `RenderPassEncoder` functions for drawing

| FUNCTION || DESCRIPTION |
| --- | --- |
| `Draw(uint32_t vCount, uint32_t iCount, uint32_t firstVertex, uint32_t firstInstance)` || Draws vertices based on their order in the vertex buffer |
| --- | --- |
| `DrawIndexed(uint32_t iCount, uint32_t instanceCount, uint32_t firstIndex, int32_t baseVertex, uint32_t firstInstance)` || Draws vertices in the order given by the values in the index buffer |
| `DrawIndirect(Buffer const& indirectBuffer, uint64_t indirectOffset)` || Draws vertices in order based on parameters in an indirect buffer |
