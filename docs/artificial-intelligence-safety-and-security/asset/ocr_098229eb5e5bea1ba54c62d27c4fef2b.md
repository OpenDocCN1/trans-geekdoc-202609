# TABLE 8.2
Accuracy on Photos of Adversarial Images in the Prefiltered Case (Clean Image Correctly Classified, Adversarial Image Confidently Incorrectly Classified in Digital Form Being Being Printed and Photographed)

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

# TABLE 8.3
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