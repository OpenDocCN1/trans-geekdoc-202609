In the case of performing phase filtering, the DEM results obtained by the phase unwrapping results of these six unwrapping methods are shown in Figure 18. Figure 19 shows the corresponding errors between the DEM solutions and the reference DEM. We can observe that the DEM obtained by the proposed method is closest to the reference DEM among these six methods because most pixels of its error image are closest to zero. To better quantify the DEM errors of these six unwrapping methods, the histogram error curves were fitted and are shown in Figure 20. From Figure 20, compared with the other five unwrapping methods, the error curve of the proposed method is more concentrated near zero and sharper, so the unwrapping accuracy of the proposed method was the highest among these six methods.

For quantitative evaluation, the RMSE between DEM solutions obtained by these six methods and the reference DEM were calculated and are listed in Table 4. As seen from Table 4, the RMSE of the proposed method is the smallest among these six unwrapping methods. In addition, compared with the PUMA method and CNN method [20], the RMSE of the proposed method is 3.73% or 7.0% lower, respectively. The performance improvement was not as large as with the simulated data, because the noise level was greatly reduced after performing phase filtering. As the level of noise decreases, the performance gaps among different unwrapping methods gradually decreases. Based on the above analysis, the unwrapping accuracy of the proposed method is the highest among these six methods.

![](bbox=[0.06, 0.44, 0.31, 0.63])

![](bbox=[0.34, 0.44, 0.59, 0.63])

![](bbox=[0.62, 0.44, 0.87, 0.63])

![](bbox=[0.06, 0.64, 0.31, 0.83])

![](bbox=[0.34, 0.64, 0.59, 0.83])

![](bbox=[0.62, 0.64, 0.87, 0.83])

Figure 18. In the case of performing phase filtering, the DEM results of six phase unwrapping methods on real data. (a) LS. (b) QGPU. (c) PUMA. (d) SNAPHU. (e) CNN [20]. (f) Proposed method.