# External Memory Data Format

To load the input image to the deployed deep learning processor IP core and retrieve the output results, you can read data from the external memory and write data to the external memory by using dHdl. Workflow workflow. This workflow formats your data. Or, you can manually format your input data. The processor formatted output data by using the external memory data format.

# Key Terminology

+   - Parallel Data Transfer Number refers to the number of pixels that are transferred every cycle through the AXI master interface. The letter N in place of the Parallel Data Transfer Number. Mathematically N is the square root of the ConvTransferNumber. See "ConvThreadNumber"
- Feature Number refers to the value of the z dimension of an x-y-by-z matrix. For example, most input images are of dimension x-y-by-three, referring to red, green, and blue channels of an image. Use the letter Z in place of the Feature Number.

# Convolution External Memory Data Format

The inputs and outputs of the deep learning processor convolution module are typically three-dimensional (3-D).The external memory stores the data in a one-dimensional (1-D) vector. Converting the 3-D input image into 1-D to the external memory :

+   1 Send N number of data in the z dimension of the matrix.
2 Send the image information along the x dimension of the input image.
3 Send the image information along the y dimension of the input image.
4 After the first NXY block is completed, we then send the next NXY block along the z dimension of the matrix.

The image demonstrates how the data stored in a 3-3-by-4 matrix is translated into a 1-by-36 matrix that is stored in the external memory.

![](bbox=[0.163, 0.646, 0.438, 0.755])

When the image Feature Number (Z) is not a multiple of the Parallel Data Transfer Number (N), we then pad a zeros matrix of size x-by-y along the z dimension of the matrix to make the image Z value a multiple of N.

For example, if your input image is an x-y-by-z matrix with a Z value of three and the value of N is four, pad the image with a zeros matrix of size x-by-y to make the input to the external memory an x-by-y-by-4 matrix.

This is the input image format before padding.