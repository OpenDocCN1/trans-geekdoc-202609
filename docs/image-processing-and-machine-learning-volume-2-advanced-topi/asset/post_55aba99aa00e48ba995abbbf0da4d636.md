

![](img/fa2d7e8bd88af7122f764c748b0a3723_36_0.png)

**FIGURE 1.24** Effect of the sequential filter. (a) Original image and (b) the result of the filter, obtained from a repetition of three stages varying r from 1 to 3.

```
ALGORITHM 1.2 SEQUENTIAL FILTER

Sequential filter (I(x,y))
Where I(x,y) is an intensity image
1. for r=1:t
2. Opening operation I_1 = I \circ H
3. Closing operation I_2 = I_1 \bullet H
4. I = I_2
5. end for
6. The final result of the complete process is I
```

## 1.5.4 Top-Hat and Bottom-Hat Transformation

This operation is defined by the subtraction of the original grayscale image minus the opening of that image [7]. This operation can be defined as follows:

$I_{TopH} = I - (I \circ H)$ (1.21)

The operation takes its name from the shape of the reference structure in this operation, which, as Figure 1.25 shows, is similar to a hat.

This operation is useful for enhancing details in the presence of shadows. Figure 1.26 shows the result of this operation in images. The bottom-hat operation is defined as the subtraction between the closure of an image and the original image, such that:

$$ I_{BottomHat} = (I \bullet H) - I $$ (1.22)

| 1 | 1 | 1 | 1 | 1 | 1 | 1 |
|---|---|---|---|---|---|---|
| 1 | 1 | 1 | 1 | 1 | 1 | 1 |
| 0 | 0 | 1 | 1 | 1 | 0 | 0 |
| 0 | 0 | 1 | 1 | 1 | 0 | 0 |
| 0 | 0 | 1 | 1 | 1 | 0 | 0 |
| 0 | 0 | 1 | 1 | 1 | 0 | 0 |
| 0 | 0 | 1 | 1 | 1 | 0 | 0 |
| 0 | 0 | 1 | 1 | 1 | 0 | 0 |

**FIGURE 1.25** Reference structure used in the top-hat transformation.

![](img/fa2d7e8bd88af7122f764c748b0a3723_37_0.png)

![](img/fa2d7e8bd88af7122f764c748b0a3723_37_1.png)

**FIGURE 1.26** Result of the top-hat transformation. (a) Original image and (b) result of the top-hat transformation.

## 1.6 MATLAB Functions for Morphological Operations

MATLAB® has a large number of functions that allow the implementation of most of the morphological operations discussed in this chapter [8]. This section explains one by one the functions that allow executing morphological operations as well as some auxiliary functions.

### 1.6.1 Strel Function

All morphological operations perform their function on images using a structural element called the reference structure. MATLAB has the strel function, which allows building reference structures of different sizes and shapes. Its basic syntax is:

```
esref = strel(shape, parameters);
```

where shape is a string chain that specifies the shape to implement, of which there are several predefined options, while parameters is a list of data that specifies the properties of the form. For example, strel('disk', 3) returns a disk-shaped reference structure with dimension ±3 pixels. Table 1.1 summarizes the shapes and parameters that the strel function can implement.

In this chapter, the property of dividing a reference structure into several parts has been considered to implement the morphological operation of dilation when a large-dimensional reference structure is involved. In order to speed up the execution of operations when using morphological functions, strel produces a set of composite reference structures that allow an associative representation of a large reference structure.

If we consider the case previously treated as an example, we have:

```
>> esref = strel('disk', 3)

esref =

Flat STREL object containing 25 neighbors.
Decomposition: 6 STREL objects containing a total of 14 neighbors

Neighborhood:

1   1   1   1   1
1   1   1   1   1
1   1   1   1   1
1   1   1   1   1
1   1   1   1   1
```

From the above, it can be seen that esref is not considered as a normal array but as a special structure called a strel object. This object includes different elements. The Neighborhood element is an array of ones and zeros that defines the reference structure. Another element reports the number of elements contained in the structure, which in this case is 25. An important part of the object is the number of elements into which the reference structure can be divided (in the case of this example, it is 6). Therefore, if these elements are associated, they could formulate a larger reference structure. Within the strel object, there is a set of ones (14 elements) present in the structures into which the reference structure has been decomposed. Table 1.1 describes the shapes and structures that can be implemented using the MATLAB strel function.

## TABLE 1.1 Shapes and Structures That Can Be Implemented Using the MATLAB® strel Function

| Syntax | Description |
| --- | --- |
| `esref=strel('diamond', r)` | Creates a diamond-shaped structure, where the value of `r` specifies the distance from the end of the shape to the center |
| `esref=strel('disk', r)` | Create a disk-shaped structure where `r` specifies the radius of the disk |
| `esref=strel('line', long, grad)` | Constructs a structure in the form of a line, where the parameter long represents the length of the line, while grad defines the direction of the line |
| `esref=strel('octagon', r)` | Create an octagonal frame, where `r` specifies the distance from the center to one of the sides |
| `esref=strel('square', w)` | Create a square structure of width defined by `w` |
| `esref=strel('arbitrary', Matriz)` | Constructs a structure of an arbitrary shape defined by an array whose elements are “zeroes” and “ones” |

![](img/fa2d7e8bd88af7122f764c748b0a3723_39_0.png)

![](img/fa2d7e8bd88af7122f764c748b0a3723_39_1.png)

![](img/fa2d7e8bd88af7122f764c748b0a3723_39_2.png)

![](img/fa2d7e8bd88af7122f764c748b0a3723_39_3.png)

![](img/fa2d7e8bd88af7122f764c748b0a3723_39_4.png)

The whos command delivers the number of variables that are present in the MATLAB environment. When this command is applied after inquiring about the components of esref, six elements are displayed. They represent the elements used to decompose the final structure. These commands are as follows:

```
>> components=getsequence(esref);
>> whos
Name Size Bytes Class Attributes
components 6x1 1870 strel
esref 1x1 2599 strel
```

```
>> components(1)
ans =
Flat STREL object containing 3 neighbors.
Neighborhood:
1
1
1
```

### 1.6.2 MATLAB Functions for Dilation and Erosion

The imdilate function implements the dilation operation, and its basic syntax is as follows:

```
IR = imdilate(I, H)
```

where I is the image to which the dilation is applied using H as the reference structure. IR is the dilated image. If I is a binary image, then IR will also be binary, while if I is an image of intensity IR, it will be too. Therefore, by using the same function, we can perform this operation for binary images and for grayscale images. The reference structure H can be obtained by using the strel function.

The imerode function implements the erosion operation, and its basic syntax is as follows:

```
IR = imerode(I, H)
```

where I is the image to which the erosion is applied using H as the reference structure. IR is the eroded image. If I is a binary image then IR will also be binary, while if I is an intensity image, it will be too.

In order to show how to use the dilation and erosion functions, an example has been conducted. In this example, the morphological gradient (Section 1.5.2) of a grayscale image is implemented. Assuming that I is the image from which you want to extract the morphological gradient, the following commands are used:

```
>> H = strel('square', 3);
>> I1 = imdilate(I, H);
>> I2 = imerode(I, H);
>> IG = I1 - I2;
```

where H is the reference structure that is generated considering a square shape of dimension 3. When dilation and erosion are obtained using the same image and the same reference structure, a subtraction is produced between the dilated and eroded versions of the image, thus finding the morphological gradient of I.

### 1.6.3 MATLAB Functions Involving the Open and Close Operations

The imopen and imclose functions implement the opening and closing operations. The basic syntaxes of these functions are as follows:

```
IR = imopen(I, H)
IR = imclose(I, H)
```

where I is the image to which the opening or closing is applied using H as a reference structure. IR is the resulting image, if I is a binary image, then the result IR is binary, while if I is a grayscale image, the resulting IR element is also an intensity image. The reference structure H can be obtained by using the strel function.

