# Computing Free Volumes 139

![](bbox=[0.225, 0.115, 0.775, 0.313])

Figure 7 (Left) Typical configuration of particles before particle i is removed. (Right) After particle $i$ is removed, tessellations must be reconstructed within the “super-polyhedron” (bold, dashed line). The volume and surface area of the cavity that once held the removed particle can then be determined. (Adapted from Ref. 71).

Voronoi vertices completely encloses the associated cavity. This union volume provides an upper bound of the cavity's volume.
3. Determine the actual cavity volume and surface area within the Delaunay tetrahedra: The overlap of the exclusion spheres with the relevant Delaunay tetrahedra is subtracted analytically, leaving only the actual cavity volume and surface area. This nontrivial calculation is from the multiple overlap of exclusion spheres, but a systematic method for carrying it out is available.$^{70,71}$

# COMPUTING FREE VOLUMES

The calculation of free volumes and free surface areas requires an efficient way of extending the cavity algorithm. To calculate the free volume of a particle $i$, the particle and its associated exclusion sphere are effectively removed from a snapshot of the particle configuration. The volume and surface area of the cavity that is produced in the absence of particle $i$ are equal to the free volume and free surface area of particle $i$, respectively.

After particle $i$ has been removed from the configuration, the Voronoi and Delaunay tessellations must be reconstructed before the resulting cavity volume can be calculated. It can be shown rigorously that, at least in the case of monodisperse sphere packings, the tessellations be redone only for the neighboring particles of the removed particle (i.e., within a local “superpolyhedron”). Once the local re-tessellations are completed, the cavity volume algorithm described above is used to determine the free volume and free surface area particle $i$. Particle $i$ is then replaced into