# Table 9.3 Accuracy results for all combinations of lab study sensors across the three classification problems

| | Enclosed | On Person | Pocket/Bag/Out/Hand |
|---|---|---|---|
| Accelerometer (AC) | 89% | 82% | 79% |
| Light/proximity (L/P) | 98% | 71% | 70% |
| Multispectral (MS) | 89% | 80% | 76% |
| Capacitive (CAP) | 58% | 88% | 73% |
| AC + L/P | **100%** | 84% | 83% |
| AC + MS | 92% | 82% | 78% |
| AC + CAP | 85% | **90%** | 79% |
| AC + L/P + MS | 99% | 80% | 81% |
| AC + L/P + CAP | 97% | **90%** | **85%** |
| AC + L/P + MS + CAP | 98% | 88% | **85%** |

The top accuracies are bolded in the table for each classification problem.

the single most useful sensor, achieving an accuracy of 88% on its own. Again the addition of accelerometer is most helpful, improving the accuracy to 90%, while the multispectral and light/proximity sensors do not seem to improve the accuracy. The capacitive sensing grid was likely so helpful because it can sense grasping of a device as well as detect a person's leg through the lining of many trouser pockets.

+   3. In Bag, In Pocket, Out, or In Hand: In the four-way classification, the accelerometer performs the best of any single sensor (79%), with the multispectral sensor also demonstrating its value (76%). Interestingly, the combination of these two sensors is not as valuable as the combination of the accelerometer with the light/proximity sensor, which achieved a combined accuracy of 83%. Ultimately, the combination of accelerometer, light/proximity sensor, and capacitive sensor is most effective, achieving an accuracy of 85%. The errors in this model come primarily from confusion over when the device is in a pocket or a bag. We had hoped that the capacitive sensor would be more valuable in this case, helping to disambiguate between being in a bag and being up against somebody's skin. Regardless, the overall improvement from accelerometer-only is still very notable.

**Comparison with ESM data:** Overall, there were not major differences between the accelerometer-only models in the lab study and those from the ESM study, even though the ESM data came from a broad variety of different devices and was collected *in situ*.