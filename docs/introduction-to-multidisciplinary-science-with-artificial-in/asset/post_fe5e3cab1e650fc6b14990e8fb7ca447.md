
## Table 5.4. A Matlab code for simulating beta, alpha, theta, and delta waves.

```matlab
Zc=0.057501127785; Zri=0.0001;Zlc=.001; time=0:1:128;
AA= [2195 1998 1932 2014 2015 1965 1900 1883 1883 1966 1916 1932 1916 ...
1883 1916 1769 1752 1769 1785 2015 2080 2080 2162 2129 2097 2014 ...
1949 1982 1998 1818 1801 1851 1736 1506 1457 1687 1850 1966 2047 ...
1982 1966 2146 2195 2506 2637 2637 2604 2342 2179 1867 1818 1785 ...
1753 1720 1769 2031 2031 2162 2162 2145 2227 2424 2440 2424 2326 ...
1900 2178 2178 2146 2194 1998 2015 1982 1785 1752 1523 1523 1752 ...
1736 1867 1851 1867 2047 2097 2129 2064 2048 2031 2031 2224 2277 ...
2276 2260 2113 2080 2162 2129 2129 2244 2309 2391 2473 2473 2572 ...
2604 2719 2670 2358 2359 2244 2146 2145 2080 1998 2113 2015 2064 ...
2179 2227 2621 2686 2441 2309 2129 2080 1998 1932 1818 1];
ffx=AA';
%% Original
plot(time,ffx,'k'); grid; axis([-10 138 -100 3000]);
fs=500; Afft=fft(ffx,1024); Lfft=length(Afft); L=(0:Lfft-1)*(fs/Lfft);
plot(L,20*log10((abs(Afft)))); grid; axis([-20 520 80 260]);
%% delta wave
[nn,fo,ao,ww] = firpmord([0.3, 4.0]/(fs/2), [1 0], [Zc, Zri]);
qq = firpm(nn,fo,ao,ww); xdel=filter(dfilt.dffir(qq),ffx);
plot(time,xdel,'k'); grid; axis([-10 138 -20 450]);
Afft=fft(xdel,1024);
plot(L,20*log10((abs(Afft)))); grid; axis([-20 520 80 200]);
%% theta wave
[nn,fo,ao,ww] = firpmord([3.75 4 7.75 8]/(fs/2), [0 1 0], [Zlc, Zc, Zri]);
qq = firpm(nn,fo,ao,ww); xth=filter(dfilt.dffir(qq),ffx);
plot(time,xth,'k'); grid; axis([-10 138 -8 10]);
Afft=fft(xth,1024);
plot(L,20*log10((abs(Afft)))); grid; axis([-20 520 10 120]);
%% alpha wave
[nn,fo,ao,ww] = firpmord([7.75 8 13.75 14]/(fs/2), [0 1 0], [Zlc, Zc, Zri]);
qq = firpm(nn,fo,ao,ww); xalp=filter(dfilt.dffir(qq),ffx);
plot(time,xalp,'k'); grid; axis([-10 138 -10 15]);
Afft=fft(xalp,1024);
plot(L,20*log10((abs(Afft)))); grid; axis([-20 520 20 130]);
%% beta wave
[nn,fo,ao,ww] = firpmord([13.5 14 29.5 30]/(fs/2), [0 1 0], [Zlc, Zc, Zri]);
qq = firpm(nn,fo,ao,ww); xbet=filter(dfilt.dffir(qq),ffx);
plot(time,xbet,'k'); grid; axis([-10 138 -15 20]);
Afft=fft(xbet,1024);
plot(L,20*log10((abs(Afft)))); grid; axis([-20 520 -50 130]);
```

To summarize, electrophysiology is the study of the electromagnetic properties of biological cells and tissues. It is done through the measurement and interpretation of electromagnetic responses of the body, particularly those of the heart and nervous system. As an example, an electrophysiology study of the heart might involve placing electrodes inside the heart to measure its electrical activity. This would enable us to detect abnormalities. No detectable abnormalities means the patient’s electrophysiology is normal. This can be a valuable diagnostic tool, as it can help rule out certain conditions or diseases that might cause symptoms. Abnormalities may indicate an underlying condition or disease, such as an arrhythmia or neurological disorder. They are used to diagnose and treat a variety of conditions such as epilepsy, heart rhythm disorders, and arrhythmias. Treatments include medication to keep the rhythm normal, or to speed it up or slow it down, putting a pacemaker in the heart to keep the heartbeat fast enough or to electrically resynchronize several portions of the heart, shocking the heart out of serious/fatal rhythms, removing a small portion of the conduction system to fix a malfunctioning area and re-routing the electricity. In more general terms, electrophysiology has improved our understanding of the electromagnetic properties of the human body and how they relate to health and disease.

![](img/f5b5b8709fc3a81631262f22d3552c5e_569_0.png)

Figure 5.26. (Continued.)

![](img/f5b5b8709fc3a81631262f22d3552c5e_570_0.png)

Figure 5.26. (a and b) EEG wave samples and (c and d) delta wave, (e and f) theta wave, (g and h) alpha wave, and (i and j) beta wave.

## 5.2. Electricity from the Ground

Our objective in this section is to describe some possible ways electricity can be spontaneously generated from the ground and vacuum. We will start by introducing the integral form of Maxwell’s equations and Faraday’s induction. These equations are fundamental to understanding electricity generation.

### 5.2.1. Electromagnetic Induction

### Integral form of Maxwell’s equations.

The four Maxwell’s equations derived in Chapter 3 can alternatively be written in the integral form, as shown in Table 5.5. The integral forms of Gauss’s laws for electric and magnetic fields are obtained by using the divergence theorem, and Ampère’s and Faraday’s laws are obtained by applying Stokes’ theorem. Let us look at a specific example. It is easy to make the transition from Maxwell’s differential equations to integral equations with the help of these two theorems. For example, by integrating both sides of Gauss’s law for the electric field over a closed volume D bounded by the closed surface ∂D and using the divergence theorem, we obtain the integrated form; i.e.,

∬_{∂D} [D(x,t)·n(x)] dS(x) = Q_E(t)   (5.22)

with

Q_E(t) = ∭_{D} ρ(x,t) dV(x) ,   (5.23)

Table 5.5. Differential and integral forms of Maxwell’s equations. These two forms are related through Stokes’ and divergence theorems (e.g., Ikelle, 2020). Note that dS = n dS and S is any surface, not necessarily closed, whereas ∂D is a closed surface (the boundary of the volume D). The line integrals of the electric and magnetic fields are closed paths along the boundary C of the surface S; C is always a closed curve. Note that Gauss’s laws are integrals over closed surfaces whereas Ampère’s laws are integrals over closed paths.

| Differential form | Integral form |
|---|---|
| ∇ × H = J + ∂D/∂t | ∮_C H·dl = ∬_S (J + ∂D/∂t)·dS  Ampère |
| ∇ × E = -∂B/∂t | ∮_C E·dl = -∬_S ∂B/∂t·dS  Faraday |
| ∇·D = ρ | ∬_{∂D} D·dS = ∭_D ρ dV  Gauss (electricity) |
| ∇·B = 0 | ∬_{∂D} B·dS = 0  Gauss (magnetic) |

where n is the unit vector normal to surface ∂D and pointing outward, Q_E is the total charge within volume D. Similarly, we can obtain the integral form of Gauss’s laws for magnetic fields by using the divergence theorem. We can obtain the integral form of the charge conservation law in the same way; i.e.,

∬_{∂D} [J(x,t)·n(x)] dS(x) = - d/dt [∭_D ρ(x,t) dV(x)] .   (5.24)

The left-hand side represents the total amount of charge flowing outwards through the surface ∂D per unit time. The right-hand side represents the amount by which charge decreases inside the volume D per unit time. In other words, charge does not disappear into (or is created out of) nothingness—it decreases in a region of space only because it flows into other regions.

Let us integrate the differential form of Faraday’s law over the surface S bounded by the contour C. We arrive at

∬_S [(∇ × E(x,t))·n(x)] dS(x) = - d/dt ∬_S [B(x,t)·n(x)] dS(x) .   (5.25)

Note S is any surface and not necessarily closed. By applying Stokes’ theorem to the left-hand side of (5.25), we obtain the integral form of Faraday’s law; i.e.,

∮_C [E·dl(x)] = - d/dt ∬_S [B(x,t)·n(x)] dS(x) .   (5.26)

The line integral of the electric field carried out along the boundary C of a surface S. C is always a closed curve. A similar application of Stokes’ theorem to the differential form of Ampère’s law yields the integral form of Ampère’s law in Table 5.5. We can deduce the integral form of Maxwell’s equations for electrostatics and magnetostatics by assuming that the time derivative of the fields in Table 5.5 is zero.

### Faraday’s law of induction.

The integral form of Faraday’s law in (5.26) can also be written as

ℰ(t) = - dΦ_B(t)/dt ,   (5.27)

where ℰ(t), which is known as the electromotive force (emf) or induced voltage, is defined as follows:

ℰ(t) = ∮_C E(x,t)·dl(x) ,   (5.28)

and Φ_B(t) is the magnetic flux and defined as follows:

Φ_B(t) = ∬_S [B(x,t)·n(x)] dS(x) .   (5.29)

The closed line integral of the electric field carried out along the boundary C of the surface S. As illustrated in Figure 5.27, C is always a closed curve.

Let us expand on the definition of electromotive force and magnetic flux. Consider a region of an electric field and the motion of a charge q from A to B along a defined path. As we discussed in Chapter 3, at each and every point along the AB path, the electric field exerts a force on this charge and, hence, does a certain amount of work in moving the charge to another point along this path. The total

![](img/f5b5b8709fc3a81631262f22d3552c5e_572_0.png)

Figure 5.27. Closed path C in a region of electric field.
