images, which comprise 50 training and test images each. The goal was to delineate micro-aneurysm sites in the given training images. The Images has resolutions of 1058 × 1061, 1389 × 1383 and 768 × 576 [33].

# 12.2.2 Fundus photography

A special fundus camera is used to record the principal anatomical structures of the eye, including the optical disc, fovea, blood and macula. A laser or a flash camera with a low power microscope is usually used. The fundus camera, which has specific dyes and filters to represent various intrinsic characteristics, captures various joint structures of the eye. Fundus photography has different shapes, including a colour fundus photography, red-free fluorescent angiography and concurrent stereo fundus photography. The retina has white light and full colour photographs. Special filters having spectral wavelength equal to 540–570 nm that can retain green chromaticity while removing red colour capture superficial lesions. A fluorescent colored dye is imparted in the blood circulation of the patient to record the images during the course of fluorescein angiography. The angiography of sodium fluorescein uses 490 nm blue light, and 530 nm yellow light fluoresces. For studying DR, it is a highly standardized photography technique. The choroidal vessels are observed using indocyanine green angiography using an 805 nm infrared diode

# 12.2.3 Challenges in retinal vessel segmentation

The performance of the retinal vessel segmentation methods recorded in the reports in the test sets and evaluation criteria [6, 34, 35] is usually nearer to that of human observers. Both documents and the latter in particular, a restriction which usually controls medical imaging techniques, are not consistent. The debate on the validation of algorithms and the challenge of international design is increasing internationally [36–39]. Several image processing problems affect a coherent segmentation of the retinal fundus. The most important of them can be summed up here.

+   - Central light reflection produces a divide in the segmented vessel and two smaller versions are developed on the segmented image.
+   - Tiny vessels that lack segmentation have poor contrast.
+   - Split vessels at crossover/bifurcation points.
+   - Near, parallel blood vessels are segmented as a big one.
+   - Existence of unwanted imaging artefacts like blur, noise, and non-uniform lighting.
+   - Injuries like microaneurysms, bleeding, hard and soft exudates and neovascularization interrupts the blood vessel images, block and show false positive effects.

The challenges mentioned above are critical to ensure that the data obtained with a variety of different instruments, procedures, operators and patient specimens are secure, reproducible and extremely accurate and eventually allow for the efficient translation of research technologies to the healthcare sector. Recent methods of deep