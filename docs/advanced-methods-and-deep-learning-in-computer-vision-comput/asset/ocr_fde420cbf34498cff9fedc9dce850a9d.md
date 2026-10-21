# TABLE 15.1 Summary of existing adversarial attacks for tasks that use images as input.

KEY – o: white-box, ●: black-box, T: targeted, T̄: untargeted, B: bounded, B̄: unbounded, Opt: optimization-based, Grad: gradient-based, Bound: boundary approximation, GradE: gradient estimation, LocS: local search, RanS: random search, C: classification, S: semantic segmentation, D: object detection, IC: image captioning, E: edge detection.

| Reference | Method | box | T | T̄ | B | B̄ | Approach | Datasets | Task |
|---|---|---|---|---|---|---|---|---|---|
| (Szegedy et al., 2014) | L-BFGS | ○ | ✓ | ✓ | ✓ |  | Opt | ImageNet, MNIST, Youtube | C |
| (Carlini and Wagner, 2017) | CW | ○ | ✓ | ✓ | ✓ |  | Opt | MNIST, CIFAR | C |
| (Goodfellow et al., 2015) | FGSM | ○ |  | ✓ | ✓ |  | Grad | MNIST | C |
| (Kurakin et al., 2017b) | BIM (I-FGSM) | ○ | ✓ | ✓ | ✓ |  | Grad | ImageNet | C |
| (Madry et al., 2018) | PGD | ○ | ✓ | ✓ | ✓ |  | Grad | MNIST, CIFAR | C |
| (Papernot et al., 2016b) | JSMA | ○ | ✓ | ✓ | ✓ |  | Grad | MNIST | C |
| (Moosavi-Dezfooli et al., 2016) | DeepFool | ○ |  | ✓ | ✓ |  | Grad | ImageNet, MNIST, CIFAR | C |
| (Modas et al., 2019) | SparseFool | ○ |  | ✓ | ✓ |  | Grad | ImageNet, MNIST, CIFAR | C |
| (Xie et al., 2019) | DI²-FGSM | ○● | ✓ | ✓ | ✓ |  | Grad | ImageNet | C |
| (Tramèr et al., 2018) | E-FGSM | ○● |  | ✓ | ✓ |  | Grad | ImageNet | C |
| (Li et al., 2019a) | P-FGSM | ○● | ✓ |  | ✓ |  | Grad | Places | C |
| (Sanchez-Matilla et al., 2020) | RP-FGSM | ○ | ✓ | ✓ | ✓ |  | Grad | Places | C |
| (Moosavi-Dezfooli et al., 2017) | UAP | ○ |  | ✓ | ✓ |  | Opt | ImageNet | C |
| (Mopuri et al., 2017) | Fast Feature Fool | ○ |  | ✓ | ✓ |  | Opt | ImageNet, Places-205 | C |
| (Baluja and Fischer, 2018) | ATN | ○ | ✓ | ✓ | ✓ |  | Opt | ImageNet, MNIST | C |
| (Xiao et al., 2018) | AdvGAN | ○● | ✓ | ✓ | ✓ |  | Opt | ImageNet, MNIST | C |
| (Poursaeed et al., 2018) | GAP | ○● | ✓ | ✓ | ✓ |  | Opt | ImageNet, Cityscapes | C,S |
| (Mopuri et al., 2018) | NAG | ○● |  | ✓ | ✓ |  | Opt | ImageNet | C |
| (Bhattad et al., 2020) | Semantic Manipulation | ○ | ✓ |  |  | ✓ | Opt | ImageNet, MSCOCO | C,IC |
| (Shamsabadi et al., 2020a) | EdgeFool | ○ |  | ✓ |  | ✓ | Opt | ImageNet, Places | C |
| (Papernot et al., 2016a) | SBA | ● | ✓ | ✓ | ✓ |  | Bound | MNIST | C |
| (Shi et al., 2019) | Curls & Whey | ● | ✓ | ✓ | ✓ |  | Bound | ImageNet | C |
| (Dong et al., 2019) | TI Attack | ● |  | ✓ | ✓ |  | Bound | ImageNet | C |
| (Chen et al., 2017) | ZOO | ● | ✓ | ✓ | ✓ |  | GradE | ImageNet, MNIST, CIFAR | C |
| (Ilyas et al., 2018) | Query-limited Attack | ● | ✓ | ✓ | ✓ |  | GradE | ImageNet | C |
| (Tu et al., 2019) | AutoZOOM | ● | ✓ | ✓ | ✓ |  | GradE | ImageNet, MNIST, CIFAR | C |
| (Naroditska and Kasiviswanathan, 2017) | LocSearchAdv | ● | ✓ | ✓ | ✓ |  | GradE | ImageNet, MNIST, CIFAR, SVHN, STL | C |
| (Brendel et al., 2018) | BA | ● | ✓ | ✓ | ✓ |  | LocS | ImageNet, MNIST, CIFAR | C |
| (Guo et al., 2019) | SimBA | ● | ✓ | ✓ | ✓ |  | LocS | ImageNet | C |
| (Hosseini and Poovendran, 2018) | SemanticAdv | ● | ✓ | ✓ |  | ✓ | RanS | CIFAR | C |
| (Shamsabadi et al., 2020c) | ColorFool | ● |  | ✓ |  | ✓ | RanS | ImageNet, CIFAR, Places | C |
| (Fischer et al., 2017) | SSA | ○ |  | ✓ | ✓ |  | Grad | Cityscapes | S |
| (Xie et al., 2017) | DAG | ● |  | ✓ |  | ✓ | Grad | VOC | S,D |
| (Wei et al., 2019) | UEA | ○● |  | ✓ | ✓ |  | Opt | ImageNet VID | D |
| (Cosgrove and Yuille, 2020) | Edge Attack | ○ | ✓ | ✓ | ✓ |  | Grad | Cityscapes | E |