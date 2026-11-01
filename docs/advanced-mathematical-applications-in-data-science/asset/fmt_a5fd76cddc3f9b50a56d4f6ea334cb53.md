
## Cluster Identification

Now, we will carry out the process of cluster identification by creating an Elbow plot and further by calculating Inertia. In Fig. ([**4**](#9789815124842-C11.html#f4)), we will calculate Inertia. Inertia is the sum of square error for each cluster hence lowering the inertia denser of the clusters. By applying the `Python` code below:

![](Images/9789815124842-C11-F4.jpg)**Fig. (4))**  
Showing clusters formation for scaled data.

### Cluster formation

As we apply the `python` code below and we get the results for clusters 1 to 3 for different states of India according to their characteristics and features (Fig. [**5**](#9789815124842-C11.html#f5)).

## RESULTS AND ANALYSIS

We categorized the data selected for analysis state-wise into 3 clusters (Fig. [**6**](#9789815124842-C11.html#f6)) in `Python`.

The `k-mean` algorithm (cluster analysis using `Python` Programming) classifies the states of India into three clusters. Cluster one includes 16 states of India *viz.* Arunachal, Assam, Bihar, Himachal Pradesh, Jammu & Kashmir, Jharkhand, Madhya Pradesh, Manipur, Meghalaya, Mizoram, Odisha, Rajasthan, Sikkim, Tripura, Uttar Pradesh, Uttarakhand. Cluster two includes 8 states of the India *Viz* Andhra Pradesh, Goa, Gujarat, Karnataka, Kerala, Maharashtra, Tamilnadu, West Bengal. Cluster three includes 4 states of the India *Viz* Haryana, Nagaland, Punjab, Chhattisgarh.

![](Images/9789815124842-C11-F5.jpg)**Fig. (5))**  
Showing clusters formation results with classification for scaled data. ![](Images/9789815124842-C11-F6.jpg)**Fig. (6))**  
Showing different clusters.

### Cluster One

Cluster one includes 16 states of India *viz.* Arunachal, Assam, Bihar, Himachal Pradesh, Jammu & Kashmir, Jharkhand, Madhya Pradesh, Manipur, Meghalaya, Mizoram, Odisha, Rajasthan, Sikkim, Tripura, Uttar Pradesh, Uttarakhand. In cluster one the highest carbon dioxide per capita is observed in Jharkhand state with 1043.43 per kg per person which is way above the national average of 894.40 per kg per person ([Table **1**](#9789815124842-C11.html#t1)). Cluster one average carbon dioxide is 593.89 per capita CO[2]. The electricity generation plants are the major source of CO[2].> emission in Jharkhand, besides transportation and industrial process emission. The lowest CO[2] emission was observed in the state of Bihar with 179.01, which is below the national average and cluster one average.

Table 1 **Showing greenhouse gases per capita and different cluster classifications.**  

| **State** || **Per Capita CO[2]**  
**(Kg Per Person)** || **Per Capita CO**  
**(Kg Per Person)** || **Per Capita CH[4]**  
**(Kg Per Person)** || **Cluster** |
| --- | --- | --- | --- | --- |
| **Andhra Pradesh** || 974.17 || 27.18 || 16.97 || 1 |
| --- | --- | --- | --- | --- |
| **Arunachal** || 405.9 || 17.43 || 25.82 || 0 |
| **Assam** || 340.91 || 16.63 || 21.29 || 0 |
| **Bihar** || 179.01 || 8.83 || 9.59 || 0 |
| **Chattisgarh** || 1963.88 || 17.56 || 22.37 || 2 |
| **Goa** || 2662.51 || 23.12 || 7.62 || 1 |
| **Gujarat** || 1310.58 || 24.01 || 12.26 || 1 |
| **Haryana** || 1381.86 || 17.9 || 21.57 || 2 |
| **HimachalPradesh** || 784.16 || 16.98 || 18.28 || 0 |
| **Jammu &Kashmir** || 509.03 || 15.59 || 14.42 || 0 |
| **Jharkhand** || 1403.43 || 15.02 || 15.39 || 0 |
| **Karnataka** || 888.86 || 24.93 || 12.2 || 1 |
| **Kerala** || 780.12 || 18.29 || 4.52 || 1 |
| **MadhyaPradesh** || 656.37 || 16.14 || 15.15 || 0 |
| **Maharashtra** || 936.7 || 23.58 || 9.8 || 1 |
| **Manipur** || 379.2 || 10.8 || 22.63 || 0 |
| **Meghalaya** || 691.53 || 12.65 || 19.8 || 0 |
| **Mizoram** || 754.71 || 15.4 || 10.72 || 0 |
| **Nagaland** || 1275.27 || 24.13 || 29.08 || 2 |
| **Odisha** || 700.13 || 18.4 || 19.88 || 0 |
| **Punjab** || 1618.08 || 27.9 || 33.38 || 2 |
| **Rajasthan** || 793.69 || 14.33 || 14.18 || 0 |
| **Sikkim** || 711.39 || 11.68 || 10.04 || 0 |
| **Tamilnadu** || 985.7 || 26.6 || 10.4 || 1 |
| **Tripura** || 295.64 || 17.76 || 19.23 || 0 |
| **UttarPradesh** || 404.26 || 12.4 || 12.87 || 0 |
| **Uttarakhand** || 493.01 || 14.28 || 17.93 || 0 |
| **West Bengal** || 763.13 || 22.69 || 15.99 || 1 |
| **Average** || 894.4010714 || 18.29321429 || 16.54928571 || \- |
| **Max** || 2662.51 || 27.9 || 33.38 || \- |
| **Min** || 179.01 || 8.83 || 4.52 || \- |

The highest CO[2] emission in cluster one is registered in the state of Odisha which is slightly above the national average of 18.29 per capita CO. The average per capita CO[2] is 14.64 kg per person for cluster one which is below the national average of 27.9 per capita CO. The CO[2] level in Odhisha is higher because of petrol and diesel emission by vehicles which played a havoc role. The minimum CO[2] per capita is registered with Bihar 9.59 per capita CO.

The highest CH[4] is measured in Arunachal Pradesh with 25.82 kg per person which is way above the national average of 16.54 per capita CH[4]. The livestock rearing and agriculture activities are the reason responsible for a high level of CH[4]. in the state ([Table **2**](#9789815124842-C11.html#t2)). The state ranked third in CH[4] emission after Nagaland and Punjab. The minimum CH[4] is registered with Bihar 9.59 per capita CH[4].

Table 2 **Showing average, minimum, and maximum greenhouse gases for cluster one.**  

| **State** || **Per Capita CO[2]**  
**(kg per person)** || **Per Capita CO**  
**(kg per person)** || **Per Capita CH[4]**  
**(kg per person)** || **Cluster** |
| --- | --- | --- | --- | --- |
| **Arunachal** || 405.9 || 17.43 || 25.82 || 1 |
| --- | --- | --- | --- | --- |
| **Assam** || 340.91 || 16.63 || 21.29 || 1 |
| **Bihar** || 179.01 || 8.83 || 9.59 || 1 |
| **HimachalPradesh** || 784.16 || 16.98 || 18.28 || 1 |
| **Jammu &Kashmir** || 509.03 || 15.59 || 14.42 || 1 |
| **Jharkhand** || 1403.43 || 15.02 || 15.39 || 1 |
| **MadhyaPradesh** || 656.37 || 16.14 || 15.15 || 1 |
| **Manipur** || 379.2 || 10.8 || 22.63 || 1 |
| **Meghalaya** || 691.53 || 12.65 || 19.8 || 1 |
| **Mizoram** || 754.71 || 15.4 || 10.72 || 1 |
| **Odisha** || 700.13 || 18.4 || 19.88 || 1 |
| **Rajasthan** || 793.69 || 14.33 || 14.18 || 1 |
| **Sikkim** || 711.39 || 11.68 || 10.04 || 1 |
| **Tripura** || 295.64 || 17.76 || 19.23 || 1 |
| **UttarPradesh** || 404.26 || 12.4 || 12.87 || 1 |
| **Uttarakhand** || 493.01 || 14.28 || 17.93 || 1 |
| **Average** || 593.898125 || 14.645 || 16.70125 || \- |
| **MAX** || 1403.43 || 18.4 || 25.82 || \- |
| **MIN** || 179.01 || 8.83 || 9.59 || \- |

### Cluster Two

Cluster two includes 8 states of India, *Viz* Andhra Pradesh, Goa, Gujarat, Karnataka, Kerala, Maharashtra, Tamilnadu, West Bengal. In cluster two, the state of Goa registered the highest CO[2] per capita of 2662.52 which is above the cluster two average of 1162 per capita CO[2] ([Table **2**](#9789815124842-C11.html#t2)). The CO[2] per capita in the state of Goa is above the national average of 894.40 per capita CO[2]. The CO[2]. per capita in Goa ranks number one in the overall national ranking of CO[2] per capita. The reason for high per capita CO[2] is energy emission which contributes to ninety percent.

The highest CO[2] per capita is measured in the state of Andra Pradesh with 27.18 per capita CO[2] which is above the cluster average of 23.8 per capita CO. The reason for high CO[2] per capita is transportation emission ([Table **3**](#9789815124842-C11.html#t3)).

Table 3 **Showing Average Minimum and Maximum GHG Emission for cluster two.**  

| **State** || **per Capita CO[2] (kg per person)** || **Per Capita CO**  
**(kg per person)** || **Per Capita CH[4]**  
**(kg per person)** || **Cluster** |
| --- | --- | --- | --- | --- |
| **Andhra Pradesh** || 974.17 || 27.18 || 16.97 || 2 |
| --- | --- | --- | --- | --- |
| **Goa** || 2662.51 || 23.12 || 7.62 || 2 |
| **Gujarat** || 1310.58 || 24.01 || 12.26 || 2 |
| **Karnataka** || 888.86 || 24.93 || 12.2 || 2 |
| **Kerala** || 780.12 || 18.29 || 4.52 || 2 |
