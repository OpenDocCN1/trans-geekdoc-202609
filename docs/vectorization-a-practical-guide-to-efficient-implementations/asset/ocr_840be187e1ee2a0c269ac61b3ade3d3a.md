+   * Line 102: These operations rearrange the dimensions of the tensor so that we can perform subsequent flattening.
+   * Line 105: This flattens the patch_x and patch_y dimensions together, which will result in the final num_patches or sequence_length dimension of the patch embeddings.
+   * Line 108: This flattens channel, patch height, and patch width together, which will result in the final num_pixels dimension. This dimension will then be reduced by the subsequent feedforward layer to form the patch embeddings.

+   - forward (Lines 112–143): The main logic of the ViT is implemented here.
+   * Line 115: This calls the patchify method on the input to reshape the input into patch vector representations, resulting in a tensor of shape (batch_size, sequence_length, num_pixels), where sequence_length is the number of patches from the image.
+   * Line 119: This feeds the output from the above step to a feedforward layer to reduce the dimensionality of the vector of each patch, forming a tensor of shape (batch_size, sequence_length, embed_size).
+   * Lines 122-128: This adds the “classification token” embedding to the sequence, forming a tensor of shape (batch_size, sequence_length + 1, embed_size).
+   * Line 131: Adds the precomputed sinusoidal positional encoding to the image patch embeddings, in preparation for feeding it to the subsequent blocks of transformer encoder layers.
+   * Lines 134-135: Feed the inputs to the transformer encoder layers, then to the final Layer Normalization layer.
+   * Line 138: Extracts the “classification token” embedding from the transformer encoder’s output. This is the latent representation of the final class to be predicted.
+   * Line 141: Decodes the class from the latent embedding vector by outputting the logit values of the probabilities of each class.

Let us train the model using the MNIST dataset to classify the handwritten digits in the images.

```
from tqdm import tqdm
import torch.nn.functional as F
from torch.utils.data import DataLoader
# !pip install torchvision==0.16.0
from torchvision.datasets.mnist import MNIST
from torchvision.transforms import ToTensor
from torchsummary import summary
train_set = MNIST(
```