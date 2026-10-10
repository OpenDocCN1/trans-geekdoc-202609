
## Iteration 3

[**TABLE 2.11**](#C_007_c2.xhtml#t2_11b) Iteration 3 (Case: System Failure)

| Sensor Number | 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|---|
| Current stake (`s`) | 96 | 96.56 | 113.22 | 113.22 | 81 |
| Reading received (`r`) | 119 | 123 | 84 | 95 | 96 |
| Contributor? (`s>min_stake`) | True | True | True | True | True |
| Average reading (`avg`) | 103.4 | 103.4 | 103.4 | 103.4 | 103.4 |
| Deviation (`d`) = \|avg−r\| | 15.6 | 19.6 | 19.4 | 8.4 | 7.4 |
| Accepted reading | | | Accept | | |
| Within the deviation limit? (`d<dev_limit`) | No | No | No | Yes | Yes |
| Stake for transfer (10%) | 9.6 | 9.656 | 11.322 | 0 | 0 |
| Stake for fee (5%) | 4.8 | 4.83 | 5.66 | 5.66 | 4.05 |
| Revised stakes | 86.4 | 86.9 | 101.9 | 128.51 | 96.29 |

## Iteration 4

[**TABLE 2.12**](#C_007_c2.xhtml#t2_12b) Iteration 4 (Case: System Failure)

| Sensor Number | 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|---|
| Current stake (`s`) | 86.4 | 86.9 | 101.9 | 128.51 | 96.29 |
| Reading received (`r`) | 119 | 119 | 89 | 105 | 129 |
| Contributor? (`s>min_stake`) | True | True | True | True | True |
| Average reading (`avg`) | 112.2 | 112.2 | 112.2 | 112.2 | 112.2 |
| Deviation (`d`) = \|avg−r\| | 6.8 | 6.8 | 23.2 | 7.2 | 16.8 |
| Accepted reading | Accept | Accept | | | |
| Within the deviation limit? (`d<dev_limit`) | Yes | Yes | No | Yes | No |
| Stake for transfer (10%) | 0 | 0 | 10.19 | 0 | 9.629 |
| Stake for fee (5%) | 4.32 | 4.35 | 5.09 | 6.43 | 4.81 |
| Revised stakes | 93 | 93.5 | 91.71 | 135.12 | 86.66 |

## Iteration 5

[**TABLE 2.13**](#C_007_c2.xhtml#t2_13b) Iteration 5 (Case: System Failure)

| Sensor Number | 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|---|
| Current stake (`s`) | 93 | 93.5 | 91.71 | 135.12 | 86.66 |
| Reading received (`r`) | 122 | 112 | 91 | 117 | 120 |
| Contributor? (`s>min_stake`) | True | True | True | True | True |
| Average reading (`avg`) | 112.4 | 112.4 | 112.4 | 112.4 | 112.4 |
| Deviation (`d`) = \|avg−r\| | 9.6 | 0.4 | 21.4 | 4.6 | 7.6 |
| Accepted reading | | | Accept | | |
| Within the deviation limit? (`d<dev_limit`) | Yes | Yes | No | Yes | Yes |
| Stake for transfer (10%) | 0 | 0 | 9.171 | 0 | 0 |
| Stake for fee (5%) | 4.65 | 4.68 | 4.59 | 6.76 | 4.33 |
| Revised stakes | 95.3 | 95.8 | 82.54 | 137.41 | 88.95 |

## Iteration 6

[**TABLE 2.14**](#C_007_c2.xhtml#t2_14b) Iteration 6 (Case: System Failure)

| Sensor Number | 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|---|
| Current stake (`s`) | 95.3 | 95.8 | 82.54 | 137.41 | 88.95 |
| Reading received (`r`) | 122 | 129 | 94 | 78 | 76 |
| Contributor? (`s>min_stake`) | True | True | True | True | True |
| Average reading (`avg`) | 99.8 | 99.8 | 99.8 | 99.8 | 99.8 |
| Deviation (`d`) = \|avg−r\| | 22.2 | 29.2 | 5.8 | 21.8 | 23.8 |
| Accepted reading | | | Accept | | |
| Within the deviation limit? (`d<dev_limit`) | No | No | Yes | No | No |
| Stake for transfer (10%) | 9.53 | 9.58 | 0 | 13.741 | 8.895 |
| Stake for fee (5%) | 4.77 | 4.79 | 4.13 | 6.87 | 4.45 |
| Revised stakes | 85.77 | 86.22 | 124.29 | 123.67 | 80.06 |

## Iteration 7

[**TABLE 2.15**](#C_007_c2.xhtml#t2_15b) Iteration 7 (Case: System Failure)

| Sensor Number | 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|---|
| Current stake (`s`) | 85.77 | 86.22 | 124.29 | 123.67 | 80.06 |
| Reading received (`r`) | 84 | 78 | 115 | 99 | 122 |
| Contributor? (`s>min_stake`) | True | True | True | True | True |
| Average reading (`avg`) | 99.6 | 99.6 | 99.6 | 99.6 | 99.6 |
| Deviation (`d`) = \|avg−r\| | 15.6 | 21.6 | 15.4 | 0.6 | 22.4 |
| Accepted reading | | | | Accept | |
| Within the deviation limit? (`d<dev_limit`) | No | No | No | Yes | No |
| Stake for transfer (10%) | 8.577 | 8.622 | 12.429 | 0 | 8.006 |
| Stake for fee (5%) | 4.29 | 4.31 | 6.22 | 4.95 | 4.003 |
| Revised stakes | 77.2 | 77.6 | 111.86 | 161.3 | 72.05 |

At the end of iteration 7, the stake of sensor 5 has reduced below 75, because of repeated invalid readings. Hence, from the next iteration, it will assume only the role of the validator. Even if it generates a value, it will not be taken into account for acceptance.

## Iteration 8

[**TABLE 2.16**](#C_007_c2.xhtml#t2_16b) Iteration 8 (Case: System Failure)

| Sensor Number | 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|---|
| Current stake (`s`) | 77.2 | 77.6 | 111.86 | 161.3 | 72.05 |
| Reading received (`r`) | 114 | 77 | 126 | 118 | 85 |
| Contributor? (`s>min_stake`) | True | True | True | True | False |
| Average reading (`avg`) | 108.75 | 108.75 | 108.75 | 108.75 | 108.75 |
| Deviation (`d`) = \|avg−r\| | 5.25 | 31.75 | 17.25 | 9.25 | 23.75 |
| Accepted reading | Accept | | | | |
| Within the deviation limit? (`d<dev_limit`) | Yes | No | No | Yes | No |
| Stake for transfer (10%) | 0 | 7.76 | 11.186 | 0 | Validator |
| Stake for fee (5%) | 3.86 | 3.88 | 5.59 | 8.07 | Ineligible |
| Revised stakes | 86.67 | 69.84 | 100.67 | 170.77 | 72.05 |

Sensor 5 has acted as the validator in this iteration. Stake transfers happen as usual. The stake is also kept apart for the fee, and there is a validator available for receiving the stake. But no transfer happens since the validator still gave a reading which is quite far from the average and doesn’t seem to be reliable yet. Hence, stakes are returned. In addition, the stake for sensor 2 has moved below 75. Hence, two validators will be available in the next iteration.

## Iteration 9

[**TABLE 2.17**](#C_007_c2.xhtml#t2_17b) Iteration 9 (Case: System Failure)

| Sensor Number | 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|---|
| Current stake (`s`) | 86.67 | 69.84 | 100.67 | 170.77 | 72.05 |
| Reading received (`r`) | 111 | 106 | 123 | 92 | 126 |
| Contributor? (`s>min_stake`) | True | False | True | True | False |
| Average reading (`avg`) | 108.67 | 108.67 | 108.67 | 108.67 | 108.67 |
| Deviation (`d`) = \|avg−r\| | 2.33 | 2.67 | 14.33 | 16.67 | 17.33 |
| Accepted reading | Accept | | | | |
| Within the deviation limit? (`d<dev_limit`) | Yes | Yes | No | No | No |
| Stake for transfer (10%) | 0 | Validator | 10.07 | 17.077 | Validator |
| Stake for fee (5%) | 4.33 | Eligible | 5.04 | 8.53 | Ineligible |
| Revised stakes | 108.12 | 87.74 | 86.07 | 146.01 | 72.05 |

In this iteration, there are two validators. Sensor 2 was able to generate a good reading in this round of execution, while sensor 5 still gave a poor reading. Hence, the stake set apart for fee is transferred completely to sensor 2, and it is able to recover from the validator state back to the contributor state.

## Iteration 10

[**TABLE 2.18**](#C_007_c2.xhtml#t2_18b) Iteration 10 (Case: System Failure)

| Sensor Number | 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|---|
| Current stake (`s`) | 108.12 | 87.74 | 86.07 | 146.01 | 72.05 |
