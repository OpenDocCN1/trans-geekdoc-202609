precision with IoU (intersection over union) = 50%. AP refers to the value of IoU from 50% to 95% in steps of 5% and then calculates the average value of AP under these IoUs. Normally, AP50 is higher than AP. AP50 and AP are usually used in PASCAL VOC and MS COCO, respectively. Since the dataset contains only one class of ships, the mAP value is the same as the AP value.

In the table, the italics represent the performance of two-stage detectors, and the non-italics represent the performance of single-stage detectors. The blue, red, green, purple, and golden colors represent anchor-free, train from scratch, oriented bounding box, multi-scale, and attention detectors. The underlines represent real-time detectors.

The number of papers in Tables 5–11 is less than in Table 2. This is because some of the papers in Table 2 did not use the AP or AP50 as the evaluation indicator, so we do not show them in Tables 5–11.

From Table 5, we can see that there are 52 papers that are trained and tested on SSDD. Additionally, in the past five years, AP50 of detectors on SSDD boosted from 78.8% in 2017 to 97.8 % in 2022. The testing time is also getting faster and faster. What should be noticed is that as the train-test division is ambiguous in the original SSDD, so the AP in Table 5 is not comparable to some extent. That is also why we recommend the following researchers adopt the Improve SSDD [170] as the new standard.

# Table 5. The performance evolution of detectors on SSDD (The data come from the 177 papers).

| No. | Date | AP | Time | No. | Date | AP | Time |
|---|---|---|---|---|---|---|---|
| 11 | 1 December 2017 | 78.8% | 173 ms | 104 | 14 October 2020 | 92.6%\n56.5% | 7.39 ms |
| 15 | 9 March 2019 | 91.3% | 96 ms | 111 | 16 November 2020 | 91.84% |  |
| 39 | 2 April 2019 | 89.76% | 10.938 ms | 115 | 2 December 2020 | 89.79% |  |
| 40 | 21 May 2019 | 90.16% | 21 ms | 116 | 3 December 2020 | 90.7% | 74 FPS |
| 43 | 24 July 2017 | 79.78% | 28.4 ms | 117 | 4 December 2020 | 88.33% | 15 FPS |
| 51 | 23 September 2019 | 80.12% | 9.28 ms | 118 | 7 December 2020 | 94.6% | 3.9 ms\n258 FPS |
| 54 | 24 October 2019 | 94.13% | 9.03 ms\n111 FPS | 121 | 28 December 2020 | 95.1% | 33 ms |
| 55 | 24 October 2019 | 90.04% | 87 ms | 131 | 12 February 2021 | 95.7%\n63.4% |  |
| 56 | 14 November 2019 | 94.7% |  | 132 | 17 February 2021 | 93.78% | 202 FPS |
| 62 | 14 November 2019 | 83.4% |  | 134 | 27 February 2021 | 80.45% |  |
| 63 | 14 November 2019 | 90.44% | 96.04 ms | 149 | 17 March 2021 | 94.41% | 31 FPS |
| 68 | December 2019 | 96.93% | 8.72 ms | 146 | 23 March 2021 | 95.52% |  |
| 69 | 2 January 2020 | 97.9%\n64.6% | 103 ms | 148 | 31 March 2021 | 92.09% |  |
| 74 | 19 March 2020 | 96.4%\n67.4% | 106.4 ms | 151 | 13 May 2021 | 88.08% | 12.25 ms |
| 78 | 30 March 2020 | 94.2%\n59.5% | 0.93 M | 154 | 9 June 2021 | 98.4% |  |
| 81 | 3 April 2020 | 94%\n90.08%\n68.1% |  | 157 | 30 June 2021 | 61.4% | 45 FPS |
| 82 | 16 April 2020 |  |  | 158 | 1 July 2021 | 96.8%\n62.7% | 438 ms |
| 84 | 22 April 2020 | 97.07% | 233 FPS | 160 | 13 July 2021 | 97.2%\n61.5% |  |
| 90 | 25 May 2020 | 93.96% |  | 161 | 14 July 2021 | 95.29% | 11 FPS |
| 93 | 24 June 2020 | 94.72% | 63.2 ms | 170 | 6 December 2021 | 97.8%\n64.9% |  |
| 96 | 21 July 2020 | 96.08% | 4.51 ms\n222 FPS | 171 | 10 December 2021 | 82.2% | 5.2 ms |
| 98 | 21 August 2020 | 81.17% | 24 ms | 173 | 22 December 2021 | 97.4% | 42.5 FPS |
| 99 | 21 August 2020 | 83.4% |  | 174 | 6 February 2022 | 95.6%\n61.1% |  |
| 100 | 31 August 2020 | 90.57% | 17.2 ms | 175 | 25 February 2022 | 97.8 % | 17.5 FPS |
| 102 | 6 October 2020 | 86.3% |  | 176 | 25 February 2022 | 95.03% | 47 FPS |
| 103 | 14 October 2020 | 95.6%\n61.5% |  | 177 | 19 March 2022 | 97.0% |  |