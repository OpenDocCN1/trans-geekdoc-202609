
Smart asset management provides users the benefit of monitoring a product during its entire lifespan and the possibility of prolonging the product lifecycle, which is a circular economy cornerstone. This case describes how collecting individual device data helps remanufacturers monitor each unique device’s performance and personalize their service based on the needs of individual users. To clarify the concept, we will review a case of monitoring lithium-ion laptop batteries. The data presented in this case study has been collected over three years on 500 laptop batteries used by students in an all-girl high school in Illinois, USA as part of a prior study published in ([Sabbaghi et al., 2015b](#ch10.xhtml#ref10_45), [2015a](#ch10.xhtml#ref10_44)).

The dataset includes battery weight, serial number, type, voltage, used cycles, full charge capacity, battery age, and the class of students. To explain the dataset, [Figure 10.3](#ch10.xhtml#fig10_3) (a) shows the boxplot of batteries’ current capacity, and [Figure 10.3](#ch10.xhtml#fig10_3) (b) illustrates the voltage versus the current capacity of batteries of different ages. The variation in the dataset reveals the importance of collecting data on individual devices. Users have different charging and discharging behaviors that influence the number of used cycles and the lifecycle of individual batteries.

![Fig. 10.3 (a) The current capacity, and (b) voltage versus current capacity of batteries with 1 year, 2 years, and 3 years of usage.](images/fig10_3_C.jpg)

[Fig. 10.3 (a) The current capacity, and (b) voltage versus current capacity of batteries with 1 year, 2 years, and 3 years of usage.](#ch10.xhtml#R_fig10_3)

The product lifecycle data helps remanufacturers customize their end-of-use decision on whether to reuse or retire batteries based on the number of remaining cycles and the potential for future device reusability. Moreover, the products offered in the second-hand market can be appropriately priced based on their potential for reuse and remanufacturing. For example, [Figure 10.4](#ch10.xhtml#fig10_4) shows the distribution of the number of used cycles for the 500 batteries over three years. Consider a value of 300 used cycles as the threshold for degrading the battery. From the distribution of the used cycles and the area under the curve, we can calculate the likelihood that the battery has 200 remaining used cycles and the chance of future reusability. The authors have conducted a battery reusability analysis study on this dataset. For more information, we refer readers to ([Sabbaghi et al., 2015b](#ch10.xhtml#ref10_45), [2015a](#ch10.xhtml#ref10_44)). Overall, the concept of Carfax used in the automobile industry can be employed for other smart devices where the data on the product’s profile of usage, repair, and upgrade would give some information about the device’s lifespan and future user experience. Moreover, the product lifecycle data could also help remanufacturers decide when would be a good time to offer upgrade, repair, and maintenance services for individual devices.

 ![Fig. 10.4  The distribution of the number of used cycles](images/fig10_4_B.jpg)

[Fig. 10.4  The distribution of the number of used cycles](#ch10.xhtml#R_fig10_4)

### 3.2 Case study 2: product Lifecycle Data for optimizing repair, Maintenance, and Upgrade Decisions

This case study discusses the repair and maintenance log data for three types of medical devices. It provides descriptive statistics on the frequency and nature of product failures, along with information such as mean time to failure, mean time to repair, and total operating time of these devices. The objective is to show the practical usage of this data in improving decision-making for healthcare providers when purchasing devices. In addition, it shows how repair shops can use this data to optimize human resource allocation and job scheduling in response to repair demand and specific repair requirements.

The data includes three rebranded medical devices: M1, M2, and P1, that serve the function of infusion pumps and multitherapy. These labels are assigned as per the initial letter of each device’s name. [Table 10.3](#ch10.xhtml#tab10_3) provides an overview of these medical devices. M1 has the highest quantity of individual units, while P1 has the most extended period of usage, which is approximately 14 years from 2004 to 2018.

[Table 10.3  Basic information of three product categories.](#ch10.xhtml#R_tab10_3)

| Product Category || Function Description || Number of maintenance records || Number of individual products || First and last record date || The average of Failure count |
| --- | --- | --- | --- | --- | --- |
| M1 || Infusion || 15903 || 1593 || 04-23-2004 / 06-24-2011 || 10 |
| --- | --- | --- | --- | --- | --- |
| M2 || Pumps, || 4274 || 599 || 02-18-2004 / 10-10-2011 || 7 |
| P1 ||  || 6085 || 805 || 01–06–2004 / 01–11–2018 || 8 |

These devices show a similar average failure count, ranging from 8 to 10, as listed in [Table 10.3](#ch10.xhtml#tab10_3). [Table 10.4](#ch10.xhtml#tab10_4) shows the failure causes requiring maintenance for these products. The dataset includes 12 different failure reasons, including batteryrelated issues, random failures, and instances where no problems are detected, among others. Among these reasons, the three main drivers of maintenance are battery-related concerns, random failures, and cases where no issues are identified.

[Table 10.4 The number of repair and maintenance records for each product for different reasons.](#ch10.xhtml#R_tab10_4)

| Maintenance Description || M1 || M2 || P1 |
| --- | --- | --- | --- |
| Battery Related (BR) || 5859 || 533 || 1887 |
| --- | --- | --- | --- |
| Random Failure (RF) || 5487 || 2229 || 826 |
| No Problem Found (NPF) || 2475 || 731 || 1251 |
| Modification/Upgrade (MU) || 571 || 87 || 812 |
| Use Error (UE) || 385 || 119 || 352 |
| Physical Damage (PD) || 240 || 111 || 640 |
| Random Software Failure (RSF) || 202 || 116 || 139 |
| Accessory Problem (AP) || 56 || 10 || 119 |
| PM Related (PMR) || 19 || 4 || 59 |
| Tech Support (RS) || 605 || 334 || 0 |
| Environment Related (ER) || 3 || 0 || 0 |
| Normal Retire/Replacement (NR) || 1 || 0 || 0 |

While M1 and P1 share battery-related problems as their primary maintenance concern, M2’s primary maintenance need is attributed to random failures.

[Figure 10.5](#ch10.xhtml#fig10_5) presents the maintenance records for each product annually. [Figure 10.5](#ch10.xhtml#fig10_5) (a) illustrates the period from 2004 to 2007, during which each product shows a similar trend. All three products experienced their initial peak in maintenance cases in 2006. M1 follows a different trajectory compared to M2 and P1. After 2011, only a few P1 products were used while it seems M1 and M2 are retired based on the source of the dataset.

 ![Fig. 10.5  Annual Maintenance Records: (a) All Failures, and Specific Reasons for (b) M1, (c) M2, and (d) P1](images/fig10_5_C.jpg)

[Fig. 10.5  Annual Maintenance Records: (a) All Failures, and Specific Reasons for (b) M1, (c) M2, and (d) P1](#ch10.xhtml#R_fig10_5)

[Figures 10.5](#ch10.xhtml#fig10_5) (b) and (c) underline the battery-related maintenance, which becomes major after 2007 for all three products. The random failures consistently show up as the primary maintenance reason every year for M1 and M2. However, a shift occurred after 2008, as battery-related issues became the primary maintenance concern for M1 and P1.
