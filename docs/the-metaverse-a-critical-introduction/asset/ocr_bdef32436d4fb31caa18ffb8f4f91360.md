![](bbox=[0.146, 0.123, 0.853, 0.403])

FIGURE 4.2
The components of the 3D environment.

+   - **Geometry** – the shape of the object, typically defined by lines (also called edges) and vertices (also called points), which are often used to make up triangles (tris) or other polygons (polys), a collection of which then fit together to form the desired shape. When an object is displayed purely in terms of its geometry, it is called a wire-frame;
+   - **Texture** – how an object looks in terms of colour and pattern. This is often defined by having a two-dimensional (2D) image (in JPG, PNG, or other formats) either “pasted” onto each surface of the object, or having the faces of the object “wrapped” by a complex arrangement of textures in something called a UV map; and
+   - **Material** – how an object reflects light, giving a surface a sense of depth and what people would conventionally call “texture” (i.e. does it look smooth or rough, made of fur or cloth, etc.), defined by what is often called a “bump” or “normal” map.

Figure 4.3 shows a simple wooden cabin in terms of its wireframe, plain texture, image texture, and material.

The more complex an object in terms of geometry, textures, and materials, the more memory it takes to store, the more bandwidth to transmit, and the more processing power to render and display. As a result, virtual environments designed for lower power devices (such as mobiles) have tended to use blockier, more cartoony, objects and a simple, primary colour palette – but improvements in mobile phone processors are increasingly closing the gap in the difference in usable detail between smartphones and desktop computers.