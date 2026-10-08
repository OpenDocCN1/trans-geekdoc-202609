
## Table 3 Graph of keywords and reports properties, red representing the keyword duration and yellow representing keywords related to duration

## Table 4 List of 35 tables relevant to "duration" as determined by RF. A higher table health is preferred

| Table Health | Table |
| :--- | :--- |
| 97% | activity |
| 83% | bharun |
| 4% | biostratigraphy |
| 81% | bitrun |
| 66% | casing_section |
| 35% | cement_job |
| 85% | cost_daheet |
| 99% | daily |
| 74% | drilling_parameters |
| 92% | dvd_summary |
| 10% | ftr_drill_equipment |
| 12% | ftr_drilling |
| 5% | ftr_rig |
| 14% | ftr_tripping |
| 85% | hse_incident |
| 30% | leak_off_test |
| 4% | lesson_ticket |
| 64% | marine_properties |
| 79% | mud_properties |
| 69% | mud_volumes |
| 100% | operation |
| 85% | operation_plan_master |
| 85% | operation_plan_phase |
| 86% | personnel_on_site |
| 99% | report_daily |
| 96% | rig_information |
| 21% | rig_parameters |
| 14% | rig_pump_param |
| 10% | rushmore_wells |
| 75% | survey_station |
| 4% | target_zone |
| 81% | transport_daily_param |
| 44% | unwanted_event |
| 100% | well |
| 100% | wellbore |

## Phase Average Duration and RMSE Errors

img/accb0e713daa15f4a51070565405380d_199_0.png

Fig. 2 Model accuracy by phase type

In the end, the FSbP’s performance is determined by the performance of produced predictive models. To this end, the predictive model does not necessarily show the FSbP’s performance due to the long pipeline of data transformations that happen between FSbP and predictive modeling during which introduction of errors or noise could occur.

For example, during data compilation, data undergoes aggregation such as summations, averaging, etc. while also handling missing values, new data may be created by transforming existing data.

Then for the preprocessing steps, missing data imputation and conventional feature selection processes further modify the information before the dataset finally arrives for training.

Returning to reviewing FSbP’s performance based on the resulting predictive models, the predictive model was able to produce believable DvDs (Fig. 3). Although the model seems to have high RMSE, it may be attributed to the nature of the labels themselves, which are mostly close to 0 with many outliers with high values, which must also be identified.

Therefore, FSbP was able to reduce the scope of features while producing a relevant predictive model.

## Introducing Feature Selection Before Propositionalization

| Rank | Model ID | Imputation method | Duration scale | Feature selection | >0 Model | Train | RMSE | Test |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | 1_3_1_rff | DEFAULT_0_BEFORE_ENCODE | 0 - 1 (Seconds) | None | rff | 100 | 328 | 84.14 |
| 2 | 1_4_5_rff | DEFAULT_0_BEFORE_ENCODE | 0 - 1 (Seconds) | K-Best(Mutual Info Regression) | rff | 100 | 370 | 84.56 |
| 3 | 2_1_5_rff | DEFAULT_0_BEFORE_ENCODE | 0 - 1 (Seconds) | K-Best(Mutual Info Regression) | rff | 100 | 318 | 84.64 |
| 4 | 1_1_1_rff | DEFAULT_0_BEFORE_ENCODE | 0 - 1 (Seconds) | None | rff | 100 | 375 | 84.71 |
| 5 | 2_1_4_rff | DEFAULT_0_BEFORE_ENCODE | 0 - 1 (Seconds) | K-Best(Mutual Info Regression) | rff | 100 | 376 | 84.73 |
| 6 | 3_1_5_mlp | DEFAULT_0_BEFORE_ENCODE | 0 - 1 (Seconds) | None | mlp | 100 | 356 | 87.56 |
| 7 | 4_1_2_lr | DEFAULT_0_BEFORE_ENCODE | 0 - 1 (Seconds) | Feature Importance (Decision Tree) | lr | 100 | 398 | 93.76 |
| 8 | 4_1_5_lr | DEFAULT_0_BEFORE_ENCODE | 0 - 1 (Seconds) | K-Best(Mutual Info Regression) | lr | 100 | 353 | 94.04 |
| 9 | 3_1_4_lr | DEFAULT_0_BEFORE_ENCODE | 0 - 1 (Seconds) | K-Best(Mutual Info Regression) | lr | 100 | 374 | 93.27 |
| 10 | 4_1_2_mlp | DEFAULT_0_BEFORE_ENCODE | 0 - 1 (Seconds) | Feature Importance (Decision Tree) | mlp | 100 | 407 | 93.26 |
| 11 | 4_1_1_5_mlp | DEFAULT_0_BEFORE_ENCODE | 0 - 1 (Seconds) | K-Best(Mutual Info Regression) | mlp | 100 | 292 | 102.72 |
| 12 | 3_1_1_5_mlp | DEFAULT_0_BEFORE_ENCODE | 0 - 1 (Seconds) | K-Best(Mutual Info Regression) | mlp | 100 | 278 | |
| 13 | 4_1_1_2_mlp | DEFAULT_0_BEFORE_ENCODE | 0 - 1 (Seconds) | Feature Importance (Decision Tree) | mlp | 100 | 297 | 103.31 |
| 14 | 4_1_1_1_mlp | DEFAULT_0_BEFORE_ENCODE | 0 - 1 (Seconds) | None | mlp | 100 | | |
| 15 | 3_1_1_1_mlp | DEFAULT_0_BEFORE_ENCODE | 0 - 1 (Seconds) | None | mlp | 100 | 318 | 103.58 |

Table 5 Top 15 models of 120 model combinations

## Discussion

The key objective of feature selection is to reduce the number of features while retaining features most relevant to prediction.

One factor to be aware of FSbP is that removal of features at this stage (post-propositionalization) will be more interested in extracting accurate models from given dataset rather than searching back, recompiling data.

Because of this, despite the lax threshold for selection, FS has focus on removing only the least relevant features from the scope for data compilation and data mining.

FSbP proves crucial for the data scientist because it allows the scientist to focus efforts on relevant features during data compilation where otherwise compilation of the entire database would require the immediate understanding of the database and the multi-disciplinary expert knowledge.
