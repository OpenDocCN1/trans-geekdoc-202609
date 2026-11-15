position numbers for building occupancy was also generated. Sites without buildings were assigned a zero value; sites with buildings were assigned their height values. These values were arranged by site id. These two sets of data combined to generate a 35-dimensional block layout parameter.

Due to the high dimensionality of these parameters, it is challenging to perform CFD simulations for all of them. Therefore it is necessary to sample these parameters. The sampling method directly affects the accuracy and computational cost of the surrogate model [34]. In order for the ML model to capture as much diversity of the sample as possible, it is necessary to guarantee that the block morphology is sufficiently rich. Finding a suitable space-filling methodology to decrease the number of required simulations is a challenging problem in designing computational experiments [55]. This study adopted the LHS technique to create 1000 samples as the database. LHS is a statistical method for generating a near-random sample of parameter values from a multidimensional distribution. The sampling method is often used to construct computer experiments or for Monte Carlo integration. As far as possible, all patterns of block building combinations were included in the sample of 1000 sampled for this study. These included blocks with more dispersed or concentrated building distribution, blocks with different locations of high-rise buildings, etc. (Fig. S1).

To demonstrate the role of building height in pollutant dispersion, two additional control groups were established based on uniform building height. Control group A was the ideal block in the traditional simulation study, where all sites in the block were occupied by buildings, resulting in a slightly higher Rb_c at 0.37. To ensure that the FAR was consistent with the ordinary cases, all buildings in the block were 18.86 m (Fig. 3c). The other control group B followed the same building layout as the ordinary cases but with all building heights set to 31.43 m (Fig. 3d).

The research block was surrounded by 30 m*50 m*30 m background buildings. To investigate vehicle emissions, a traffic pollutant source was located in the upwind canyon of the research block. The source was 0.3 m above the ground, 2.5 m wide, and covered the entire street canyon. The overhanging pollution source was designed to be closer to the height of the vehicle exhaust pipe. The width of the pollution source was set based on lane width [28,56]. This way of setting up the pollution source is closer to the reality than the traditional arrangement of line sources on the ground. CO was used as a tracer gas to represent the continuous and uniform release of traffic pollutants (Fig. 3e and f). The area within 80 m of the pollution source in the block is defined as the areas of the street canyon, which was the most polluted area by traffic [28]. Sampling probes were evenly distributed in the block’s 0–15 m height area to investigate the pollutants’ dispersion (Fig. 3e and f). The areas with heights of 0–2 m and 0–15 m are pedestrian height volume and podium height volume, respectively [21]. Sampling probes in building gaps ensured that calculated average pollutant concentration would not be disturbed by probe location, and probe numbers were consistent for all working conditions. Sampling probes were divided into four parts according to horizontal and vertical distribution: sampling probes within the podium and pedestrian height in the block, sampling probes within the podium and pedestrian height in the AES. The numbers of sampling probes in each part were 3180, 424, 900, and 120.

# 3.2. Assessment of pollutant dispersion

The concentrations of sampling probes were counted to compare the pollutant distribution in different cases. The pollutant concentration was normalized, as indicated in Ref. [57] and described in Eq. (2).

$c^* = \frac{U_H H^2}{m}$ (2)

where $c^*$ is the dimensionless concentration, $\bar{c}$ is the pollutant concentration at the probes [kg/m^3], $U_H = 2m/s$ is the reference speed at the H = 10 m level, and $m$ is the source emission rate of pollutants [kg/s]. The

**Table 1** Air quality index of CO and the corresponding pollutant concentration limit.

| IAQI | 0 | 50 | 100 | 150 | 200 | 300 | 400 | 500 |
|---|---|---|---|---|---|---|---|---|
| CO (mg/m^3) | 0 | 2 | 4 | 14 | 24 | 36 | 48 | 60 |

pollutant release rate is consistent for all working conditions and is set to 3.7×10^-6 kg/s according to the traffic flow and motor vehicle emissions [58,59].

The study computed the mean values of pollutant concentrations at sampling points for four different components. The average normalized concentration of the block in the podium volume and pedestrian volume is denoted as C_pod_Block and C_ped_Block, respectively. Similarly, C_pod_AES and C_ped_AES represent the average normalized concentration of AES in the podium volume and pedestrian volume. Among these metrics, C_pod_Block and C_ped_Block are global metrics, while C_pod_AES and C_ped_AES are local metrics.

The Air Quality Index (AQI) was introduced as an evaluation index to evaluate the impact of traffic-related air pollutants on each case. Previous studies have shown that pollutants can penetrate neighborhoods up to 100 m–200 m away [60]. Still, such findings do not limit the concentration of pollutants that would affect human health. Therefore, this study proposes using AQI to determine the pollutant concentration criteria that will affect residential life and to weigh the impact range of pollutants in horizontal and vertical directions.

In this study, AQI was calculated by simplifying the concentration of one air pollutant (CO) according to the ambient air quality standards of China (HJ633-2012) [61]. AQI has been categorized into different classes [62]: I (AQI: 0–50), II (AQI:51–100), III (AQI:101–150), IV (AQI:151–200), V (AQI:201–300) and VI (AQI:301–greater), which indicate air quality are excellent, good, lightly polluted, moderately polluted, heavily polluted, and severely polluted, respectively Eqs. (3) and (4):

$IAQI_{Co} = \frac{IAQI_{Hi} - IAQI_{Lo}}{BP_{Hi} - BP_{Lo}} (C_p - BP_{Lo}) + IAQI_{Lo}$ (3)

$AQI = IAQI_{Co}$ (4)

where IAQI_Co is the air quality index of CO, C_p is the concentration of sampling probes, BP_Hi represents the AQI values at the upper limits of CO, BP_Lo represents the AQI values at the lower limits of CO, IAQI_Hi is the breakpoint concentrations of pollutant at the upper limits of CO, and IAQI_Lo is the breakpoint concentration of a pollutant at the lower limits of CO. The air quality index of CO and the corresponding pollutant concentration limits can be found in Table 1.

# 3.3. CFD models

A dataset for ML was generated by conducting a total of 1000 Reynolds-Averaged Navier-Stokes (RANS) simulations. The CFD calculation domain was defined as suggested by the Architectural Institute of Japan (AIJ) guidelines [63]. The distance from the model to the inflow boundary is 5H, the distance from the outflow boundary is 15H, and the distance from the symmetrical boundary on both sides is 6H. The height of the calculation domain is 6H, where H is the tallest building height of the case (Fig. 4). The computational domain and background mesh were first defined via constructed hexagonal meshes created using the blockMesh utility, followed by refinement via the built-in snappyHexMesh utility. The grids varied between 0.6 and 1.5 million cells across the various cases.

A numerical model was formulated and solved using OpenFOAM 5.0. A customized solver, tsSimpleFoam, was developed based on the built-in simpleFoam solver to incorporate the advection-diffusion concentration transport equation. The Semi-Implicit Method for Pressure-Linked Equations (SIMPLE) algorithm numerically resolves the coupling between pressure and velocity fields in the RANS equations.