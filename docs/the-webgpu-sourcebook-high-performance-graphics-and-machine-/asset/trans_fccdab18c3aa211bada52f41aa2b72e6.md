
# HTMLVideoElement 和 HTMLAudioElement

`HTMLVideoElement` 和 `HTMLAudioElement`（将在 [第12章](#chapter12.xhtml) 中讨论）都继承自 `HTMLMediaElement`，它提供了配置视频以进行 `WebGPU` 处理所需的大部分属性和方法。应用程序创建其中一个对象后，可以通过其属性配置其行为。[表10.3](#chapter10.xhtml#tbl10_3) 列出了 `HTMLVideoElement` 及其祖先的七个重要属性。

[表10.3](#chapter10.xhtml#b10tbl10_3) `HTMLVideoElement` 及其祖先的重要属性

| 属性 || 类型 || 描述 |
| --- | --- | --- |
| `loop` || boolean || 指示播放结束后是否应恢复 |
| --- | --- | --- |
| `autoplay` || boolean || 指示播放是否应在足够内容可用时立即开始 |
| `muted` || boolean || 指示音频是否静音 |
| `defaultPlaybackRate` || double || 播放速度（相对于 1.0） |
| `disableRemotePlayback` || boolean || 启用/禁用远程播放 |
| `src` || URL || 要播放的媒体的位置 |
| `volume` || double || 播放音量（0.0 到 1.0） |

这些属性中的大多数都很容易理解。以下代码创建了一个 `HTMLVideoElement` 并将其源设置为名为 `example.webm` 的文件。

```
 // Create video element
 const video = document.createElement("video");
 
 // Set source to URL string in local directory
 video.src = "example.webm"
```

Google 的 WebM 格式（`*.webm`）是支持 `HTMLVideoElement` 的三种主要视频格式之一。其他格式是 MP4（`*.mp4`）和 Ogg 视频（`*.ogv`）。在撰写本文时，Safari 浏览器不支持 `*.ogv` 文件。

应用程序创建 `HTMLVideoElement` 并设置其源后，可以调用其方法。[表10.4](#chapter10.xhtml#tbl10_4) 列出了其中八个可用方法。

[表10.4](#chapter10.xhtml#b10tbl10_4) `HTMLVideoElement` 的方法

| 方法 || 描述 |
| --- | --- |
| `canPlayType(type)` || 标识给定的 MIME 类型是否可以播放 |
| --- | --- |
| `captureStream()` || 返回元素的内容的 `MediaStream` |
| `load()` || 将媒体重置到其起始位置 |
| `fastSeek(time)` || 在媒体中 seek 到给定时间位置 |
| `pause()` || 暂停媒体播放 |
| `play()` || 从当前位置播放媒体 |
| `setSinkId(id)` || 标识用于音频播放的设备 |
| `requestVideoFrameCallback(callback)` || 标识在新帧可用时将被调用的回调 |

当 HTML5 最初发布时，开发人员无法响应每一帧视频。相反，应用程序会使用回调函数调用 `requestAnimationFrame` 方法。因此，回调会在浏览器每次刷新时被调用（通常每秒约 60 次）。

今天，浏览器支持 `requestVideoFrameCallback`。与 `requestAnimationFrame` 类似，它接受一个回调函数。但与 `requestAnimationFrame` 不同，它根据 *视频的* 帧率而不是 *显示的* 刷新率来调用回调。准确地说，它使用帧率和刷新率中较小的一个来确定回调的调用时间。换句话说，`requestVideoFrameCallback` 永远不会超过浏览器。

例如，如果视频提供每秒 30 帧，而浏览器每秒刷新 60 次，`requestVideoFrameCallback` 将每秒调用回调 30 次。但是，如果视频的帧率为每秒 100 帧，`requestVideoFrameCallback` 将每秒调用回调 60 次，因为浏览器的刷新率较低。

以下代码展示了其工作原理。如果浏览器支持 `requestVideoFrameCallback`，应用程序将调用 `requestVideoFrameCallback` 来配置在接收到新帧时将被调用的回调。如果不支持，应用程序将调用 `requestAnimationFrame`。

```
 // Set foo to be called when a new frame is available
 if ("requestVideoFrameCallback" in HTMLVideoElement.prototype) {
     video.requestVideoFrameCallback(foo);
 } else {
     requestAnimationFrame(foo);
 }
```

默认情况下，回调只会被调用一次。因此，如果应用程序需要访问一系列帧，回调在处理完成时应调用 `requestVideoFrameCallback` 或 `requestAnimationFrame`。

### 获取视频帧

新的 `WebCodecs` 规范提供了一套用于编码/解码视频和音频的标准机制。它提供了多个有用的接口，包括 `VideoFrame`，它可以从 `HTMLVideoElement` 获取视频帧。

一个示例将演示 `VideoFrame` 的工作原理。如果 `video` 是 `HTMLVideoElement`，以下代码将检索对应于当前帧的 `VideoFrame`。

```
 // Access frame of HTMLVideoElement
 let frame = new VideoFrame(video);
```

获取 `VideoFrame` 后，应用程序可以通过其属性获取有关其内容的信息。[表10.5](#chapter10.xhtml#tbl10_5) 列出了这些属性，它们都是只读的。

[表10.5](#chapter10.xhtml#b10tbl10_5) `VideoFrame` 属性

| 属性 || 类型 || 描述 |
| --- | --- | --- |
| `format` || string || 视频像素的格式（`I420`、`I420A`、`I422`、`I444`、`NV12`、`RGBA`、`RGBX`、`BGRA` 或 `BGRX`） |
| --- | --- | --- |
| `codedWidth` || integer || 视频帧的像素宽度 |
| `codedHeight` || integer || 视频帧的像素高度 |
| `codedRect` || `DOMRectReadOnly` || 包含帧宽度和高度的矩形 |
| `visibleRect` || `DOMRectReadOnly` || 包含可见尺寸的矩形 |
| `displayWidth` || integer || 宽高比调整后的宽度 |
| `displayHeight` || integer || 宽高比调整后的高度 |
| `duration` || integer || 视频的时长（微秒） |
| `timestamp` || integer || 视频的时间戳（微秒） |
| `colorspace` || `VideoColorSpace` || 视频色彩空间的属性 |

通过访问 `format` 和 `colorspace` 属性，应用程序可以确定不同类型的视频应如何处理。以下代码在 `frame` 的格式为平面 YUV 4:2:2（`I422`）时执行额外的处理：

```
 // Access frame of HTMLVideoElement
 let frame = new VideoFrame(video);
 
 // Check the frame's format
 if(frame.format == "I422") {
     …
 }
```

除了检查 `frame` 的属性外，应用程序还可以调用 `VideoFrame` 的方法来获取信息并访问帧的数据。[表10.6](#chapter10.xhtml#tbl10_6) 列出了这些方法并提供了每个方法的描述。

[表10.6](#chapter10.xhtml#b10tbl10_6) `VideoFrame` 方法

| 方法 || 描述 |
| --- | --- |
| `allocationSize()` || 返回存储视频帧数据所需的字节数 |
| --- | --- |
| `clone()` || 返回包含与原始数据相同的新 `VideoFrame` |
| `close()` || 释放对媒体源的引用 |
| `copyTo(destination)` || 将帧的内容复制到 `ArrayBuffer`、`TypedArray` 或 `DataView` |

`copyTo` 方法特别有趣。一般来说，视频帧必须在处理前转换为 `RGBA` 或 `BGRA` 等格式。但如果视频采用不同格式且颜色转换耗时过长，`copyTo` 使应用程序能够处理帧的原始数据。

### 创建纹理

一旦 `VideoFrame` 可用，应用程序就可以通过调用 `device` 的 `importExternalTexture` 方法并传入描述纹理的对象，从中创建纹理。[表10.7](#chapter10.xhtml#tbl10_7) 列出了此对象的属性。

[表10.7](#chapter10.xhtml#b10tbl10_7) `importExternalTexture` 参数的属性

| 属性 || 是否必需 || 描述 |
| --- | --- | --- |
| `label` || N || 新纹理的标识符 |
| --- | --- | --- |
| `source` || Y || 提供源内容的 `VideoFrame` 或 `HTMLVideoElement` |
| `colorSpace` || N || 新纹理的色彩空间（`srgb` 或 `display-p3`） |

