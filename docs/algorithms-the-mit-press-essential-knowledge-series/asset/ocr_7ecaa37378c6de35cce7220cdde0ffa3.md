The image is broken into small distinct parts because that is how we handle images digitally. Taking the whole image as a rectangular plot, we divide it into small patches, $28\times28 = 784$ of them, and each patch is given an integer value from 0 to 255, corresponding to a shade of gray, with 0 being completely white and 255 being completely black. The above image is actually the matrix on the following page.

In reality, neural networks require that we usually scale their inputs to a small range of values, such as between 0 and 1, otherwise they may not work well; you may think of it as having large input values that lead neurons astray. That means that before using this matrix we would divide each cell by 255, but we'll ignore this in the rest of the discussion.

The different items of clothing may belong to ten different classes, which you can see in the table below. To a computer, the classes are just different numbers, which we call *labels*:

| Label | Class | Label | Class |
|---|---|---|--|
| 0 | T-shirt/top | 5 | Sandal |
| 1 | Trouser | 6 | Shirt |
| 2 | Pullover | 7 | Sneaker |
| 3 | Dress | 8 | Bag |
| 4 | Coat | 9 | Ankle boot |