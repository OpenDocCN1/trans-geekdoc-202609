where $R_c = |R_c|$ and the equation of charged particles in (6.31) becomes

$$m\frac{d\boldsymbol{v}(\boldsymbol{x},t)}{dt}=q\left(\frac{\boldsymbol{F}_{\text{cent}}}{q}+\boldsymbol{v}\times\boldsymbol{B}\right).\tag{6.47}$$

This force can be directly inserted into (6.32) to obtain the centrifugal drift velocity as follows:

$$\boldsymbol{v}_{\text{drift}}=\frac{\boldsymbol{F}_{\text{cent}}\times\boldsymbol{B}}{qB^2}=\frac{mv_{\parallel}^2}{qR_c^2}\left(\frac{\boldsymbol{R}_c\times\boldsymbol{B}}{B^2}\right)=\frac{2U_{\parallel}}{qR_c^2}\left(\frac{\boldsymbol{R}_c\times\boldsymbol{B}}{B^2}\right),\tag{6.48}$$

where $U_{\parallel}=(mv_{\parallel}^2)/2$. Drift is therefore into or out of the page depending on the sign of $q$. Figure 6.14 shows an example of the guiding center trajectory of a charged particle in a non-homogeneous magnetic field with a toroidal geometry. The particles drift around the curvature of the magnetic field lines.

Because $B$ is proportional to $1/R_c$ as we can see in (6.48), we can verify that $\nabla B/B=\boldsymbol{R}_c/R_c^2$ [i.e., $\nabla(R_c^{-1})=-\boldsymbol{R}_c/R_c^3$]. Thus, we can alternatively write the drift velocity as follows:

$$\boldsymbol{v}_{\text{drift}}=\frac{2U_{\parallel}}{q}\left(\frac{\boldsymbol{B}\times\nabla\boldsymbol{B}}{B^3}\right).\tag{6.49}$$

In this form, we can directly compare grad-B and curvature drifts. To summarize, gradient and curvature drifts are in the same direction and are proportional to particle energies. Finally we can write the total guiding center drift as

$$\boldsymbol{v}_D=\underbrace{\frac{\boldsymbol{E}\times\boldsymbol{B}}{B^2}}_{E\times B\text{ drift}}+\underbrace{\frac{\boldsymbol{F}\times\boldsymbol{B}}{B^2}}_{\text{Ext--force drift}}+\underbrace{\frac{U_{\perp}}{qB^3}[\boldsymbol{B}\times\nabla\boldsymbol{B}]}_{\text{Grad--B drift}}+\underbrace{\frac{2U_{\parallel}}{qB^3}[\boldsymbol{B}\times\nabla\boldsymbol{B}]}_{\text{Curvature drift}}.$$

These are just examples of particle drift, which is the motion of the particle's guiding center. There are a variety of known as well as unknown drifts caused by a combination of magnetic fields and external forces. The last exercise of this chapter along with the codes in Tables 6.4 and 6.6 provide readers with opportunities to experiment with the drifts described here and to explore possible new drifts. Note that particle drifts can be used to explain and describe many phenomena, such as planetary fields, coronal loops, and tokamaks.

# 6.2.3. Magnetic Mirrors

Let us stay with the case of charged particle motion in a nonuniform magnetic field with zero electric field. We can see in Figure 6.15 that as particles move in regions of strong magnetic fields, they can reflect because these regions act like mirrors. The bounce motion of a charged particle is the motion up and down along (parallel to) the magnetic field between mirrors. Our objective here is to explain this mirror effect behind bounce motion. We will start by introducing the second constant of charged particle motion, known as the magnetic moment. The other constant introduced in (6.6) is the conservation of the kinematic energy of charged particles.