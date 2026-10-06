# Text Separation From Document Images

# CONNECTED COMPONENT, AREA COMPUTATION, AND TEXT SEPARATION

# Key Features of the Implemented Method

Essential features of this method are:

+   a. To find the connected components of the boundary extracted part of the image.
b. To calculate the area of the close-loop after boundary/perimeter detection.
c. To separate/segment the text area after finding the closed area.

# Description of the Method

The connected component method helps to find the boxes in the distinct regions of connected black pixels in the document image and computes the area of the box. This area is uniform and helps to fill the zeros in a smaller space. ORing the original image and the image filled by zeros in the image with the entire text separated from the original image.

```
Algorithm 4. Text Separation
Input: Perimeter/Boundary detected of blocks in a document image.
Output: Text extracted image.
Begin
1. Initialize the perimeter detected image for text separation.
2. Find the connected component in the image as:
a) Scan the pixels and assign a label to the pixels which are non-zero and record these label equivalences in a union-find table.
b) Use the union-find algorithm to resolve the equivalence classes.
c) Based on resolved equivalence classes, relabel the pixels.
3. Compare the area of the closed-loop which has the uniform stripes formed by run-length smearing, with the open-loop area
4. Fill zeros in a smaller space.
5. OR the image from step 4 with the original image to get text separated out put image.
End
```

# Results and Discussion

The area inside the extracted block is not uniform