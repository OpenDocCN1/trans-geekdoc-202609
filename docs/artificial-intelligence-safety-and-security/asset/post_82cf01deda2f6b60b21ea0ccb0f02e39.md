
![](img/0e9944c61216c048fa4e12b04c65af0f_134_0.png)

FIGURE 8.2 Top-1 and top-5 accuracy of Inception v3 under attack by different adversarial methods and different ε compared to “clean images”—unmodified images from the dataset. The accuracy was computed on all 50,000 validation images from the ImageNet dataset. In these experiments ε varies from 2 to 128.

We limit all further experiments to ε ≤ 16 because such perturbations are only perceived as a small noise (if perceived at all), and adversarial methods are able to produce a significant number of misclassified examples in this ε-neighbourhood of clean images.

## PHOTOS OF ADVERSARIAL EXAMPLES

### Destruction Rate of Adversarial Images

To study the influence of arbitrary transformations on adversarial images we introduce the notion of destruction rate. It can be described as the fraction of adversarial images which are no longer misclassified after the transformations. The formal definition is the following:

```
d = \frac{\sum_{k=1}^{n} C(X^{k},y_{true}^{k}) \overline{C(X_{adv}^{k},y_{true}^{k})} C(T(X_{adv}^{k}),y_{true}^{k})}{\sum_{k=1}^{n} C(X^{k},y_{true}^{k}) C(X_{adv}^{k},y_{true}^{k})} (8.1)
```

where n is the number of images used to compute the destruction rate, X^k is an image from the dataset, y_{true}^k is the true class of this image, and X_{adv}^k is the corresponding adversarial image. The function T(•) is an arbitrary image transformation—in this article, we study a variety of transformations, including printing the image and taking a photo of the result. The function C(X, y) is an indicator function which returns whether the image was classified correctly:

```
C(X,y) = { 1, if image X is classified as y; 0, otherwise. }
```

We denote the binary negation of this indicator value as \overline{C(X,y)}, which is computed as \overline{C(X,y)} = 1 - C(X,y).

### Experimental Setup

To explore the possibility of physical adversarial examples we ran a series of experiments with photos of adversarial examples. We printed clean and adversarial images, took photos of the printed pages, and cropped the printed images from the photos of the full page. We can think of this as a black box transformation that we refer to as “photo transformation.”

We computed the accuracy on clean and adversarial images before and after the photo transformation as well as the destruction rate of adversarial images subjected to photo transformation.

The experimental procedure was as follows:

- 1. Print the image, see Figure 8.3a. In order to reduce the amount of manual work, we printed multiple pairs of clean and adversarial examples on each sheet of paper. Also, QR codes were put into corners of the printout to facilitate automatic cropping.
  - a. All generated pictures of printouts (Figure 8.3b) were saved in lossless PNG format.
  - b. Batches of PNG printouts were converted to multi-page PDF file using the convert tool from the ImageMagick suite with the default settings: `convert *.png output.pdf`
  - c. Generated PDF files were printed using a Ricoh MP C5503 office printer. Each page of PDF file was automatically scaled to fit the entire sheet of paper using the default printer scaling. The printer resolution was set to 600 dpi.
- 2. Take a photo of the printed image using a cell phone camera (Nexus 5x), see Figure 8.3b.
- 3. Automatically crop and warp validation examples from the photo, so they would become squares of the same size as source images, see Figure 8.3c:
  - a. Detect values and locations of four QR codes in the corners of the photo. The QR codes encode which batch of validation examples is shown on the photo. If detection of any of the corners failed, the entire photo was discarded and images from the photo were not used to calculate accuracy. We observed that no more than 10% of all images were discarded in any experiment and typically the number of discarded images was about 3% to 6%.
  - b. Warp photo using perspective transform to move location of QR codes into pre-defined coordinates.
  - c. After the image was warped, each example has known coordinates and can easily be cropped from the image.
- 4. Run classification on transformed and source images. Compute accuracy and destruction rate of adversarial images.

```
convert *.png output.pdf
```

This procedure involves manually taking photos of the printed pages, without careful control of lighting, camera angle, distance to the page, etc. This is intentional; it introduces nuisance variability that has the potential to destroy adversarial perturbations that depend on subtle, fine co-adaptation of exact pixel values. That being said, we did not intentionally seek out extreme camera angles or lighting conditions. All photos were taken in normal indoor lighting with the camera pointed approximately straight at the page.

![](img/0e9944c61216c048fa4e12b04c65af0f_135_0.png)

FIGURE 8.3 Experimental setup: (a) generated printout which contains pairs of clean and adversarial images, as well as QR codes to help automatic cropping; (b) photo of the printout made by a cellphone camera; (c) automatically cropped image from the photo.

## TABLE 8.2
Accuracy on Photos of Adversarial Images in the Prefiltered Case (Clean Image Correctly Classified, Adversarial Image Confidently Incorrectly Classified in Digital Form Being Printed and Photographed)

| Adversarial Method | Photos Clean Images Top-1 | Photos Clean Images Top-5 | Photos Adv. Images Top-1 | Photos Adv. Images Top-5 | Source Images Clean Images Top-1 | Source Images Clean Images Top-5 | Source Images Adv. Images Top-1 | Source Images Adv. Images Top-5 |
|---|---|---|---|---|---|---|---|---|
| Fast ε = 16 | 81.8% | 97.0% | 5.1% | 39.4% | 100.0% | 100.0% | 0.0% | 0.0% |
| Fast ε = 8 | 77.1% | 95.8% | 14.6% | 70.8% | 100.0% | 100.0% | 0.0% | 0.0% |
| Fast ε = 4 | 81.4% | 100.0% | 32.4% | 91.2% | 100.0% | 100.0% | 0.0% | 0.0% |
| Fast ε = 2 | 88.9% | 99.0% | 49.5% | 91.9% | 100.0% | 100.0% | 0.0% | 0.0% |
| Iter. basic ε = 16 | 93.3% | 97.8% | 60.0% | 87.8% | 100.0% | 100.0% | 0.0% | 0.0% |
| Iter. basic ε = 8 | 89.2% | 98.0% | 64.7% | 91.2% | 100.0% | 100.0% | 0.0% | 0.0% |
| Iter. basic ε = 4 | 92.2% | 97.1% | 77.5% | 94.1% | 100.0% | 100.0% | 0.0% | 0.0% |
| Iter. basic ε = 2 | 93.9% | 97.0% | 80.8% | 97.0% | 100.0% | 100.0% | 0.0% | 1.0% |
| l.l. class ε = 16 | 95.8% | 100.0% | 87.5% | 97.9% | 100.0% | 100.0% | 0.0% | 0.0% |
| l.l. class ε = 8 | 96.0% | 100.0% | 88.9% | 97.0% | 100.0% | 100.0% | 0.0% | 0.0% |
| l.l. class ε = 4 | 93.9% | 100.0% | 91.9% | 98.0% | 100.0% | 100.0% | 0.0% | 0.0% |
| l.l. class ε = 2 | 92.2% | 99.0% | 93.1% | 98.0% | 100.0% | 100.0% | 0.0% | 0.0% |

that, to obtain very high confidence, iterative methods often make subtle co-adaptations that are not able to survive photo transformation.

Overall, the results show that some fraction of adversarial examples stays misclassified even after a non-trivial transformation: the photo transformation. This demonstrates the possibility of physical adversarial examples. For example, an adversary using the fast method with ε = 16 could expect that about 2/3 of the images would be top-1 misclassified and about 1/3 of the images would be top-5 misclassified. Thus by generating enough adversarial images, the adversary could expect to cause far more misclassification than would occur on natural inputs.

## TABLE 8.3
Adversarial Image Destruction Rate with Photos

| Adversarial Method | Average Case Top-1 | Average Case Top-5 | Prefiltered Case Top-1 | Prefiltered Case Top-5 |
|---|---|---|---|---|
| Fast ε = 16 | 12.5% | 40.0% | 5.1% | 39.4% |
| Fast ε = 8 | 33.3% | 40.0% | 14.6% | 70.8% |
| Fast ε = 4 | 46.7% | 65.9% | 32.4% | 91.2% |
| Fast ε = 2 | 61.1% | 63.2% | 49.5% | 91.9% |
| Iter. basic ε = 16 | 40.4% | 69.4% | 60.0% | 87.8% |
| Iter. basic ε = 8 | 52.1% | 90.5% | 64.7% | 91.2% |
| Iter. basic ε = 4 | 52.4% | 82.6% | 77.5% | 94.1% |
| Iter. basic ε = 2 | 71.7% | 81.5% | 80.8% | 96.9% |
| l.l. class ε = 16 | 72.2% | 85.1% | 87.5% | 97.9% |
| l.l. class ε = 8 | 86.3% | 94.6% | 88.9% | 97.0% |
| l.l. class ε = 4 | 90.3% | 93.9% | 91.9% | 98.0% |
| l.l. class ε = 2 | 82.1% | 93.9% | 93.1% | 98.0% |
