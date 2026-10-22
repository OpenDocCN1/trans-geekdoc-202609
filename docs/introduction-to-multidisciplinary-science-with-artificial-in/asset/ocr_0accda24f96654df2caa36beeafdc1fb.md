# Table 2.8. Matlab commands for computing and plotting Stefan-Boltzmann law. The Stefan-Boltzmann law is written in terms of the fundamental physical constants h, c, and k.

```
>> h = 6.626e-34; % Planck's constant in J-sec
>> k = 1.381e-23; % Boltzmann constant in J-K-1
>> c0=2.997*10.^8; % m/s speed of light in vacuum
>> n=1; %refractive index of the medium
>> step= 2.8429e-007; lambda=[10.^-7:step:2* ...
    10.^-5]; T=1;
>> figure(1);
for i=300:50:800
    VD = 2*pi*h.*(c0.^2);
    Mi=VD./((n.^2).*(lambda.^5).*(exp((h.*c0)./(n.*k.*T.*lambda.*i))-1));
plot(lambda,Mi); hold on; end; grid; xlabel('lambda'); ylabel('M(lambda)')
```

that can confirm existence of some present or past oxygenic and/or anoxygenic photosynthesis in these exoplanets, through, for example, the amount of N₂, O₂, H₂O, CO₂, and Ar in their atmospheres, the existence of present or past plate tectonics in the interiors of these planets, and the existence of magnetosphere and moons,

![](bbox=[0.1, 0.48, 0.8, 0.85])

# Figure 2.21. An illustration of results of Stefan-Boltzmann law in terms of the fundamental physical constants h, c, and k. The mathematical formula illustrated is derived from classical physics (statistical thermodynamics) instead of quantum mechanics.