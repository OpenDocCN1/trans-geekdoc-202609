
An alternative is to predict a depth map—an array giving the depth to each pixel in the image, nominally from the camera—from a single image. For many kinds of scenes, this is surprisingly easy to do accurately, because the depth map has quite a simple structure. This is particularly true of rooms and indoor scenes in general. The mechanics are straightforward. One obtains a data set of images and depth maps, then trains a network to predict depth maps from images. A variety of interesting variations of the problem can be solved. The problem with a depth map is that it doesn't tell you anything about the backs of objects, or the space behind the objects. But there are methods that can predict what voxels (3D pixels) are occupied by known objects (the object geometry is known) and what a depth map would look like if an object were removed (and so where you could hide objects). These methods work because object shapes are quite strongly stylized.

### Depth map

As we saw in [第 27.6.4 节](#Chapter27-06.xhtml#sec27-6-4), recovering the pose of a known object using a 3D model is straightforward. Now imagine you see a single image of, say, a sparrow. If you have seen many images of sparrow-like birds in the past, you can reconstruct a reasonable estimate of both the pose of the sparrow and its geometric model from that single image. Using the past images you build a small, parametric family of geometric models for sparrow-like birds; then an optimization procedure is used to find the best set of parameters and viewpoints to explain the image that you see. This argument works to supply texture for that model, too, even for the parts you cannot see ([图 27.22](#Chapter27-07.xhtml#fig27-22)).

![](images/Fig-421.jpg)

图 27.22 如果你见过某个类别的许多图片——比如鸟类（上）——你就可以利用它们从单张新视角（下）生成 3D 重建。你需要确保所有物体具有相当相似的几何形状（因此如果你在看麻雀，鸵鸟的图片就帮不上忙），但分类方法可以对此进行区分。从众多图像中，你可以估计图像中纹理值在物体上的分布，从而完成尚未看到的鸟类部分的纹理（下）。图由 Angjoo Kanazawa 提供，由 Kanazawa 等人（2018b）中描述的系统生成。上图照片来源：Satori/123RF；左下图来源：Four Oaks/Shutterstock。

## 27.7.5 Making pictures

It is now common to insert computer graphics models into photographs in a convincing fashion, as in [图 27.23](#Chapter27-07.xhtml#fig27-23), where a statue has been placed into a photo of a room. First estimate a depth map and albedo for the picture. Then estimate the lighting in the image by matching it to other images with known lighting. Place the object in the image’s depth map, and render the resulting world with a physical rendering program—a standard tool in computer graphics. Finally, blend the modified image with the original image.

![](images/Fig-422.jpg)

图 27.23 左侧是一张真实场景的图像。右侧，一个计算机图形物体已被插入场景。你可以看到光似乎来自正确的方向，并且物体似乎投射出适当的阴影。即使光照和阴影存在细微误差，生成的图像也令人信服，因为人们并不擅长识别这些误差。图由 Kevin Karsch 提供，由 Karsch 等人（2011）中描述的系统生成。

Neural networks can also be trained to do image transformation: mapping images from type `X`—for example, a blurry image; an aerial image of a town; or a drawing of a new product—to images of type `Y`—for example, a deblurred version of the image; a road map; or a product photograph. This is easiest when the training data consists of (`X`, `Y`) pairs of images—in [图 27.24](#Chapter27-07.xhtml#fig27-24) each example pair has an aerial image and the corresponding road map section. The training loss compares the output of the network with the desired output, and also has a loss component from a generative adversarial network (`GAN`) that ensures that the output has the right kinds of features for images of type `Y`. As we see in the test portion of [图 27.24](#Chapter27-07.xhtml#fig27-24), systems of this kind perform very well.

![](images/Fig-423.jpg)

图 27.24 配对图像转换，其中输入由航拍图像和对应的地图瓦片组成，目标是训练网络根据航拍图像生成地图瓦片。（系统也可以学习根据地图瓦片生成航拍图像。）网络通过比较 `ŷi`（类型为 `X` 的示例 `xi` 的输出）与类型为 `Y` 的正确输出 `yi` 进行训练。然后在测试时，网络必须根据新的类型为 `X` 的输入生成新的类型为 `Y` 的图像。图由 Phillip Isola、Jun-Yan Zhu 和 Alexei A. Efros 提供，由 Isola 等人（2017）中描述的系统生成。地图数据 © 2019 Google。

### Image transformation

Sometimes we don’t have images that are paired with each other, but we do have a big collection of images of type `X` (say, pictures of horses) and a separate collection of type `Y` (say, pictures of zebras). Imagine an artist who is tasked with creating an image of a zebra running in a field. The artist would appreciate being able to select just the right image of a horse, and then having the computer automatically transform the horse into a zebra ([图 27.25](#Chapter27-07.xhtml#fig27-25)). To achieve this we can train two transformation networks, with an additional constraint called a cycle constraint. The first network maps horses to zebras; the second network maps zebras to horses; and the cycle constraint requires that when you map `X` to `Y` to `X` (or `Y` to `X` to `Y`), you get what you started with. Again, `GAN` losses ensure that the horse (or zebra) pictures that the networks output are “like” real horse (or zebra) pictures.

![](images/Fig-424.jpg)

图 27.25 非配对图像转换：给定两组图像（这里类型 `X` 为马，类型 `Y` 为斑马），但没有对应对，学习将马转换为斑马。该方法训练两个预测器：一个将类型 `X` 映射到类型 `Y`，另一个将类型 `Y` 映射到类型 `X`。如果第一个网络将马 `xi` 映射到斑马 `ŷi`，第二个网络应将其映射回原始 `xi`。`xi` 与 `x̂[i]` 之间的差异用于训练这两个网络。`Y` 到 `X` 再返回的循环必须闭合。这类网络可以对图像施加丰富的转换。图由 Alexei A. Efros 提供；参见 Zhu 等人（2017）。奔跑的马照片由 Justyna Furmanczyk Gibaszek/Shutterstock 提供。

Another artistic effect is called style transfer: the input consists of two images—the content (for example, a photograph of a cat); and the style (for example, an abstract painting). The output is a version of the cat rendered in the abstract style (see [图 27.26](#Chapter27-07.xhtml#fig27-26)). The key insight to solving this problem is that if we examine a deep convolutional neural network (`CNN`) that has been trained to do object recognition (say, on ImageNet), we find that the early layers tend to represent the style of a picture, and the late layers represent the content. Let `p` be the content image and `s` be the style image, and let `E(x)` be the vector of activations of an early layer on image `x` and `L(x)` be the vector of activations of a late layer on image `x`. Then we want to generate some image `x` that has similar content to the house photo, that is, minimizes `|L(x) – L(p)|`, and also has similar style to the impressionist painting, that is, minimizes `|E(x) – E(s)|`. We use gradient descent with a loss function that is a linear combination of these two factors to find an image `x` that minimizes the loss.

![](images/Fig-425.jpg)
