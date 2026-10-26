# 6.2 Swin transformer

The swin transformer, proposed as a hierarchical ViT, is a novel effort in extending the use of transformers for image segmentation. To overcome the drawbacks of prior transformer models that fail to handle high-resolution images and different scales, swin transformer presents a hierarchical strategy in which images are divided into a series of nonoverlapping windows and are processed by shifted window attention methods. This design allows the effective and extensible image processing, and care was taken so as not to lose the global and local contextual information.

# 6.2.1 Secondary-level hires: architectural hierarchy and window-based demand

The major novelty of the swin transformer is in its hierarchical structure that computes the image at different resolutions. In the model, the image is first divided into a number of windows where the areas of the windows do not overlap, and self-attention is used independently within each window. The shifting of windows across different layers allows the model to capture interactions between neighboring windows, effectively integrating information across the entire image. This window-based attention approach enhances the model's efficiency by reducing the computational complexity associated with full-image attention, making it suitable for high-resolution images and large-scale datasets.

# 6.2.2 Advantages over previous transformers

The swin transformer offers several advantages over earlier transformer models, such as ViTs. Its hierarchical design allows for better scalability and more efficient processing of high-resolution inputs. Unlike traditional transformers, which struggle with the quadratic complexity of self-attention, the swin transformer’s window-based approach significantly mitigates computational costs while preserving the ability to capture global context. This makes the swin transformer particularly effective for image segmentation tasks that require both detailed local information and broader contextual understanding.

# 6.2.3 Performance in image segmentation

In image segmentation tasks, the swin transformer has demonstrated superior performance compared to previous transformer-based approaches. High precision input with powerful capability to capture multiscale information further enhances more precise and increased segmentation results. The model has delivered state-of-the-art