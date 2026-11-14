
patchify

flatten

# Feedforward layer

"classification token" + positional encoding

# Transformer encoder blocks

"classification token" extracted

# Feedforward head

Output

Figure 9.9 ViT architecture overview.

of 1D vectors. These vectors are first fed into a linear/dense layer to reduce the dimensionality of the flattened vectors, which now form the embedding vector representations of the patches. Then, a helper “classification token” embedding is added to the beginning of the sequence, which is dynamically learned, and later used to make the final prediction of the class. This tensor of shape `(num_patches + 1, emb_size)` forms the input to the transformer encoder model. The input tensor is added with a sinusoidal positional encoding matrix as per the original transformer paper [Vaswani et al., 2017]. The sinusoidal positional encoding of the transformer encoder model inputs is defined as

```
PE(pos, 2i) = sin(pos/10000^(2i/d_model))
PE(pos, 2i + 1) = cos(pos/10000^(2i/d_model))
```

- where
  - pos is the position along the sequence dimension.
  - i is the index of the embedding dimensions. For every even index of the embedding, we apply a sine function; for every odd index, we apply a cosine function.
  - d_model is the embedding size of the tokens.

This forms a 2D matrix of `(sequence:length, embed_size)`, which is illustrated in Figure 9.8. The positionally encoded inputs are then fed into multiple blocks of transformer encoders (see Figure 9.10). ViT uses a Pre-LayerNormalization or Pre-LN transformer encoder architecture which is more common nowadays instead of the architecture from the original transformer paper, which is now often referred to as a Post-LayerNormalization or Post-LN architecture. See [Xiong et al., 2020] for a more detailed discussion. Finally, we extract the first “classification token” embedding from the output sequence and use this vector to make the final multi-class classification prediction by feeding it into a dense layer that outputs the probability of each class (Figure 9.9).

As mentioned in Section 9.2, we will use ViT to illustrate how reshaping and grouping are used in practical applications. The following code block implements a ViT for the task of image classification using PyTorch.

```
import torch
from torch import nn
from torchsummary import summary # !pip install torch-summary==1.4.5

class TransformerEncoderBlock(nn.Module):
    def __init__(self, embed_dim, ffn_size, num_heads=2, dropout=0.1):
        super(TransformerEncoderBlock, self).__init__()
        self.mhattn = nn.MultiheadAttention(
            embed_dim=embed_dim,
            num_heads=num_heads,
            dropout=dropout,
            batch_first=True,
        )
        self.ffn = nn.Sequential(
            nn.Linear(embed_dim, ffn_size),
            nn.GELU(),
            nn.Dropout(dropout),
            nn.Linear(ffn_size, embed_dim),
        )
        self.input_ln = nn.LayerNorm(embed_dim)
        self.ffn_ln = nn.LayerNorm(embed_dim)

    def forward(self, x):
        y = self.input_ln(x)
        Y, _ = self.mhattn(y, Y, y)
        y += x
        z = self.ffn_ln(y)
        z = self.ffn(z)
        z += y
        return z

class VisionTransformer(nn.Module):
    def __init__(
        self,
        image_dim=(1, 28, 28), # channel, height, width
        num_patches=(7, 7), # along each dimension
        num_classes=10,
        embed_dim=8,
        ffn_size=32,
        num_heads=2,
        dropout=0.1,
        num_blocks=2,
    ):
        super(VisionTransformer, self).__init__()
        self.image_dim = image_dim
        self.num_patches = num_patches
        # Compute patch sizes
        err_msg = "Cannot evenly divide into patches"
        assert image_dim[1] % num_patches[0] == 0, err_msg
        assert image_dim[2] % num_patches[1] == 0, err_msg
        px_size = image_dim[1] // num_patches[0]
        py_size = image_dim[2] // num_patches[1]
        self.patch_size = px_size, py_size
        # Linear embedding of each patch
        self.patch_embed = nn.Linear(px_size * py_size, embed_dim)
        # Class token
        self.class_token = nn.Parameter(torch.rand(1, embed_dim))

        # Sinusoidal Positional encoding
        seq_len = num_patches[0] * num_patches[1] + 1
        positions = torch.arange(seq_len)
        timescales = torch.pow(
            1 / seq_len, 2 * torch.arange(embed_dim) // 2 / embed_dim
        )
        angles = positions[:, None] * timescales[None, :]
        pos_encoding = torch.zeros((seq_len, embed_dim))
        pos_encoding[0::2, :] = torch.sin(angles[0::2, :])
        pos_encoding[1::2, :] = torch.cos(angles[1::2, :])
        self.register_buffer("pos_encoding", pos_encoding)

        # Transformer encoder blocks
        self.blocks = nn.ModuleList(
            TransformerEncoderBlock(embed_dim, ffn_size, num_heads,
            dropout)for _ in range(num_blocks)
        )

        # final layer norm
        self.blocks.append(nn.LayerNorm(embed_dim))

        # Prediction head
        self.prediction_head = nn.Linear(embed_dim, num_classes)

    def patchify(self, x: torch.Tensor):
        # (batch_size, channel, patch_x, height, patch_y, width)
        patches = x.view(
            x.shape[0],
            x.shape[1],
            self.num_patches[0],
            self.patch_size[0],
            self.num_patches[1],
            self.patch_size[1],
        )
        # (batch_size, patch_x, patch_y, channel, height, width)
        patches = patches.transpose(3, 4).moveaxis(1, 3)
        # Flatten the patch dims
        # (batch_size, num_patches, channel, height, width)
        patches = patches.flatten(1, 2)
        # Flatten the patch
        # (batch_size, num_patches, num_pixels)
        patches = patches.flatten(2, 4)
        return patches

    def forward(self, x: torch.Tensor):
        # Create patches
        # (batch_size, num_patches, num_pixels)
        patches = self.patchify(x)

        # Pass through linear embedding
        # (batch_size, seq_len, emb_size)
        patches = self.patch_embed(patches)

        # Adding in the class embedding
        patches = torch.cat(
            [
                self.class_token.expand(patches.size(0), 1, -1),
                patches,
            ],
            dim=1,
        )
        # Add positional encoding
        hidden = patches + self.pos_encoding[None, :, :]
        # Pass through transformer encoder layer
        for block in self.blocks:
            hidden = block(hidden)
        # Get the class token embedding only
        output = hidden[:, 0, :]
        # Output
        output = self.prediction_head(output)
        return output
```

- TransformerEncoderBlock: This is the implementation of the transformer encoder block using Pre-LN architecture.
  - __init__ (Lines 7–22): This initializes all the necessary parameters and layers in the encoder block.
  - forward (Lines 24–33): This implements a single block of transformer encoder layer using the Pre-LN architecture. See Figure 9.10 for an illustration when reviewing the code.

- VisionTransformer: This is the main module of the ViT model.
  - __init__ (Lines 37–88): This initializes the parameters and layers in the ViT model.
    - Lines 50–51 store some parameters to be used later on.
    - Lines 54–59 compute the patch size based on the input image size and the number of desired patches. Notice that the image width and height need to be divisible by the number of desired patches along each dimension. Otherwise, an assertion error will be thrown.
    - Line 62 initializes a feedforward layer which will be used to reduce the dimensionality of the patches.
    - Line 65 initializes a model parameter for “classification token” embedding. This embedding vector will be added at the beginning of the input sequence before feeding into the transformer encoder blocks.

**Figure 9.10** Transformer pre-LN architecture. After L blocks of encoder layers, the outputs will be additionally passed to a normalization layer before outputting the final token sequence representation.

![](img/e891acaacd4fb5b80dab2ed824618203_332_0.png)

- Lines 68-77 implement the sinusoidal encoding based on Equation 9.1. See Figure 9.8 for an illustration of the resulting positional encoding added to the patches. The self.register_buffer method keeps the precomputed sinusoidal positional embeddings as a static copy in the class attributes which will then be later referenced by the forward method.
- Lines 80-83 create a series of transformer encoder blocks.
- Line 85 adds a final LayerNormalization layer after the series of transformer encoder blocks, as designed by the Pre-LN architecture (see Figure 9.10).
- Line 88 creates the prediction head, which outputs the logit value (i.e. before softmax activation) of the probabilities of each class.
- patchify (Lines 91-110): This method converts the 2D images into flattened 1D vectors of each patch.
  - Lines 93-100 reshape the images in the height and width dimensions, creating a tensor of shape (batch_size, channel, patch_x, height, patch_y, width).
