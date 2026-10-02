Substitute Equation (12) and Equation (13) into Equation (8)

X'X ⎡ β̂₀ ⎤ = X' H_O
      ⎢ β̂₁ ⎥
      ⎣ β̂₂ ⎦
(14)

Thus, the regression coefficients are obtained by Equation (15)

⎡ β̂₀ ⎤   (X'X)⁻¹ X' H_O
⎢ β̂₁ ⎥ =
⎣ β̂₂ ⎦
(15)

By taking the regression coefficients into the multiple linear regression model, a compensation function can be obtained. To verify the rationality of the model, the coefficient of determination R² is used to estimate the fit of the model to the measured data. In multiple regression analysis, the coefficient of determination is the square of the path coefficient, that is

R² = SSR / SST = Σᵢ (Ĥ_Oi − H̄_Oi)² / Σᵢ (H_Oi − H̄_Oi)²
(16)

In Equation (16), H̄_Oi is the average expected humidity value of H_Oi. The total dispersion square sum SST reflects the discrete state of all expected humidity values H̄_Oi. The regression square sum SSR reflects the difference after regression. The sum of squared residuals is SSE = Σᵢ εᵢ², so SST = SSR + SSE. Then, Equation (16) can be rewritten to Equation (17)

R² = SSR / (SSR + SSE) = 1 − SSE / SST = 1 − Σᵢ εᵢ² / Σᵢ (H_Oi − H̄_Oi)²
(17)

The coefficient of determination R² represents the interpretation degree of the estimated value Ĥ_Oi to the ideal value H_Oi. The larger the R², the closer the regression curve is to the ideal humidity value [16].

Therefore, the regression coefficients β̂₀, β̂₁, β̂₂ and coefficient of determination R² are calculated by using the actual measured humidity value H_i, temperature value T_i and the expected ideal humidity value H_Oi. The coefficient of determination R² is used to judge whether to segment and to determine the segmentation point. The specific implementation steps are as follows.

+   1. The error curve of humidity sensor is linear at room temperature. So the initial temperature value T_x is determined to be about 25 °C. The measured error of humidity sensor at the ambient temperature 25 °C is −6%--1% when the humidity is 10%–90% RH.
2. Read the previous temperature value T_{x-1} and the next temperature value T_{x+1} and their respective humidity values.
3. Each time a set of temperature and corresponding humidity data are read, a regression is performed to obtain a coefficient of determination R².
4. If R² ≥ 0.911, return to step 2, if R² < 0.911, get the segmentation points T1 and T2.
5. When the temperature interval of the linear interval is greater than 5 °C, that is, T1 − T2 > 5, the segmentation compensation will be performed according to Figure 3. If T1 − T2 ≤ 5, the whole process will be compensated by GSA-BP. An adaptive segmentation flowchart based on multiple linear regression is shown in Figure 4.