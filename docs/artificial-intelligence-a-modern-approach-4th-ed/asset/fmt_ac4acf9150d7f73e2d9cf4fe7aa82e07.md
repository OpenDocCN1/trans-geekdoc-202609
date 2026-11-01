
The key problem is to establish which point in the first view corresponds to which in the second view. Detailed descriptions of the local appearance of a point using simple texture features (like those in [Section 27.3.2](#Chapter27-03.xhtml#sec27-3-2)) are often enough to match points. For example, in a scene of traffic on a street, there might be only one green light visible in two images taken of the scene; we can then hypothesize that these correspond to each other. The geometry of multiple camera views is very well understood (but sadly too complicated to expound here). The theory produces geometric constraints on which point in one image can match with which point in the other. Other constraints can be obtained by reasoning about the smoothness of the reconstructed surfaces.

There are two ways of getting multiple views of a scene. One is to have two cameras or two eyes ([Section 27.6.2](#Chapter27-06.xhtml#sec27-6-2)). Another is to move ([Section 27.6.3](#Chapter27-06.xhtml#sec27-6-3)). If you have more than two views, you can recover both the geometry of the world and the details of the view very accurately. [Section 27.7.3](#Chapter27-07.xhtml#sec27-7-3) discusses some applications for this technology.

## 27.6.2 Binocular stereopsis

Most vertebrates have two eyes. This is useful for redundancy in case of a lost eye, but it helps in other ways too. Most prey have eyes on the side of the head to enable a wider field of vision. Predators have the eyes in the front, enabling them to use binocular stereopsis. Hold both index fingers up in front of your face, with one eye closed, and adjust them so the front finger occludes the other finger in the open eye’s view. Now swap eyes; you should notice that the fingers have shifted position with respect to one another. This shifting of position from left view to right view is known as disparity. In the right choice of coordinate system, if we superimpose left and right images of an object at some depth, the object shifts horizontally in the superimposed image, and the size of the shift is the reciprocal of the depth. You can see this in [Figure 27.14](#Chapter27-06.xhtml#fig27-14), where the nearest point of the pyramid is shifted to the left in the right image and to the right in the left image.

×![](images/Fig-413.jpg)

Figure 27.14 Translating a camera parallel to the image plane causes image features to move in the camera plane. The disparity in positions that results is a cue to depth. If we superimpose left and right images, as in (b), we see the disparity.

Binocular stereopsis
Disparity

To measure disparity we need to solve the correspondence problem—to determine for a point in the left image, its “partner” in the right image which results from the projection of the same scene point. This is analogous to what is done in measuring optical flow, and the most simple-minded approaches are somewhat similar. These methods search for blocks of left and right pixels that match, using the sum of squared differences (as in [Section 27.3.3](#Chapter27-03.xhtml#sec27-3-3)). More sophisticated methods use more detailed texture representations of blocks of pixels (as in [Section 27.3.2](#Chapter27-03.xhtml#sec27-3-2)). In practice, we use much more sophisticated algorithms, which exploit additional constraints.

Assuming that we can measure disparity, how does this yield information about depth in the scene? We will need to work out the geometrical relationship between disparity and depth. We will consider first the case when both the eyes (or cameras) are looking forward with their optical axes parallel. The relationship of the right camera to the left camera is then just a displacement along the x\-axis by an amount `b`, the baseline. We can use the optical flow equations from [Section 27.3.3](#Chapter27-03.xhtml#sec27-3-3), if we think of this as resulting from a translation vector `T` acting for time `δt`, with `Tx = b/δt` and `Ty = Tz = 0`. The horizontal and vertical disparity are given by the optical flow components, multiplied by the time step `δt`, `H = vxδt`, `V = vyδt`. Carrying out the substitutions, we get the result that `H = b/Z`, `V = 0`. In other words, the horizontal disparity is equal to the ratio of the baseline to the depth, and the vertical disparity is zero. We can recover the depth `Z` given that we know `b`, and can measure `H`.

Baseline

Under normal viewing conditions, humans fixate; that is, there is some point in the scene at which the optical axes of the two eyes intersect. [Figure 27.15](#Chapter27-06.xhtml#fig27-15) shows two eyes fixated at a point `P0`, which is at a distance `Z` from the midpoint of the eyes. For convenience, we will compute the angular disparity, measured in radians. The disparity at the point of fixation `P0` is zero. For some other point `P` in the scene that is `δZ` farther away, we can compute the angular displacements of the left and right images of `P`, which we will call `PL` and `PR`, respectively. If each of these is displaced by an angle `δθ/2` relative to `P0`, then the displacement between `PL` and `PR`, which is the disparity of `P`, is just `δθ`. From [Figure 27.15](#Chapter27-06.xhtml#fig27-15), $\\tan\\theta = \\frac{b/2}{Z}$ and $\\tan(\\theta - \\delta\\theta/2) = \\frac{b/2}{Z + \\delta Z}$, but for small angles, tan θ ≈ θ, so

×![](images/Fig-414.jpg)

Figure 27.15 The relation between disparity and depth in stereopsis. The centers of projection of the two eyes are distance `b` apart, and the optical axes intersect at the fixation point `P0`. The point `P` in the scene projects to points `PL` and `PR` in the two eyes. In angular terms, the disparity between these is `δθ` (the diagram shows two angles of `δθ/2`).

Fixate

$\\delta\\theta/2 = \\frac{b/2}{Z} - \\frac{b/2}{Z + \\delta Z} \\approx \\frac{b\\delta Z}{2Z^{2}}$

and, since the actual disparity is `δθ`, we have

$\\text{disparity} = \\frac{b\\delta Z}{Z^{2}}$

In humans, the baseline `b` is about 6 cm. Suppose that `Z` is about 100 cm and that the smallest detectable `δθ` (corresponding to the size of a single pixel) is about 5 seconds of arc, giving a `δZ` of 0.4 mm. For `Z = 30 cm`, we get the impressively small value `δZ = 0.036 mm`. That is, at a distance of 30 cm, humans can discriminate depths that differ by as little as 0.036 mm, enabling us to thread needles and the like.

## 27.6.3 3D cues from a moving camera

Assume we have a camera moving in a scene. Take [Figure 27.14](#Chapter27-06.xhtml#fig27-14) and label the left image “Time t” and the right image “Time t +1”. The geometry has not changed, so all the material from the discussion of stereopsis also applies when a camera moves. What we called disparity in that section is now thought of as apparent motion in the image, and called optical flow. This is a source of information for both the movement of the camera and the geometry of the scene. To understand this, we state (without proof) an equation that relates the optical flow to the viewer’s translational velocity `T` and the depth in the scene.

The optical flow field is a vector field of velocities in the image, (`vx(x, y)`, `vy(x, y)`). Expressions for these components, in a coordinate frame centered on the camera and assuming a focal length of `f = 1`, are

$\\begin{matrix} {v\_{x}(x,y) = \\frac{- T\_{x} + xT\_{z}}{Z(x,y)}\\text{and}} & {v\_{y}(x,y) = \\frac{- T\_{y} + yT\_{z}}{Z(x,y)}} \\\\ \\end{matrix}.$

where `Z(x, y)` is the z\-coordinate (that is, depth) of the point in the scene corresponding to the point in the image at (`x`, `y`).

Note that both components of the optical flow, `vx(x, y)` and `vy(x, y)`, are zero at the point `x = Tx/Tz`, `y = Ty/Tz`. This point is called the focus of expansion of the flow field. Suppose we change the origin in the x–y plane to lie at the focus of expansion; then the expressions for optical flow take on a particularly simple form. Let (`x'`, `y'`) be the new coordinates defined by `x' = x – Tx/Tz`, `y' = y – Ty/Tz`. Then
