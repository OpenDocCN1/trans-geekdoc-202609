![](bbox=[0.13, 0.12, 0.86, 0.46])

FIGURE 4.4 A Second Life sculpture by SL artist Starax created using “prim-torture”.

was, assembling and distorting simple Platonic solid “primitives” (usually shortened to “prims”) such as cubes, cones, and cylinders in a process called prim-torture into quite incredible structures, devices, and artworks (see Figure 4.4). Second Life introduced mesh (i.e. 3D model imports) in 2011 and is starting to support glTF, and users can now freely choose between the two approaches.

# Physics

If the virtual world is going to act anything like the physical world, it needs physics – if a user lets go of something, it should drop, and if they throw something, it should arc. Of course, this is a virtual world, so users might want to be able to selectively switch physics off or change values, so they can experience being on a moon or another planet or even in weightlessness. Another key element is how objects react when they touch or bump into each other: should they just pass through and ignore the other object, should they bounce off like billiard balls (so-called hard-body physics), or should they deform slightly as they touch and repel (so-called soft-body physics).

Physics in virtual worlds are typically implemented by “physics engines” from specialist providers such as Havoc (https://www.havok.com/) and the open-source Bullet Physics (https://github.com/bulletphysics/bullet3/), which are then plugged into the virtual world or game engine in use. The