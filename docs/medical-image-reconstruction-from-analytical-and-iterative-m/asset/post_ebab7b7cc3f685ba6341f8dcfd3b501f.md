
- 6.6.4 Iterative methods: accurate modeling — 148
- 6.7 Noise modeling as a likelihood function — 149
- 6.8 Including prior knowledge (Bayesian) — 152
- 6.9 Mathematical expressions — 153
- 6.9.1 ART — 153
- 6.9.2 The Landweber algorithm — 154
- 6.9.3 CG algorithm — 155
- 6.9.4 ML-EM — 157
- 6.9.5 OS-EM — 159
- 6.9.6 MAP (Green's one-step-late algorithm) — 160
- 6.9.7 Matched and unmatched projector/backprojector pairs — 162
- 6.10 Reconstruction using highly undersampled data — 164
- 6.11 Worked examples — 167
- 6.12 Summary — 179
- Problems — 180
- Bibliography — 182

## 7 MRI reconstruction — 185

- 7.1 The "M" — 185
- 7.2 The "R" — 187
- 7.3 The "I" — 190
- 7.3.1 To obtain z-information: slice selection — 190
- 7.3.2 To obtain x-information: frequency encoding — 191
- 7.3.3 To obtain y-information: phase encoding — 192
- 7.4 Mathematical expressions — 195
- 7.5 Image reconstruction for MRI — 198
- 7.5.1 Fourier reconstruction — 198
- 7.5.2 Iterative reconstruction — 199
- 7.6 Worked examples — 200
- 7.7 Summary — 201
- Problems — 202
- Bibliography — 202

## 8 Using FBP to perform iterative reconstruction — 204

- 8.1 The Landweber algorithm: from recursive form to nonrecursive form — 204
- 8.2 The Landweber algorithm: from nonrecursive form to closed form — 205
- 8.3 The Landweber algorithm: from closed form to backprojection-then-filtering algorithm — 206
- 8.3.1 Implementation of (A^T A)^-1 in the Fourier domain — 206
- 8.3.2 Implementation of I - (I - αAᵀA)† in the Fourier domain — 207
- 8.3.3 Landweber algorithm: backprojection-then-filtering algorithm — 207
- 8.3.4 Numerical examples of the window function — 207
- 8.4 The Landweber algorithm: the weighted FBP algorithm — 209
- 8.4.1 Landweber algorithm: FBP without noise weighting — 209
- 8.4.2 Landweber algorithm: FBP with view-based noise weighting — 210
- 8.4.3 Landweber algorithm: FBP with ray-based noise weighting — 211
- 8.5 FBP algorithm with quadratic constraints — 213
- 8.5.1 Example of minimum-norm constrained FBP — 214
- 8.5.2 Example of reference-image constrained FBP — 216
- 8.6 Convolution backprojection — 217
- 8.7 Nonquadratic constraints — 220
- 8.8 A viewpoint from calculus of variations — 223
- 8.9 Noise-weighted FBP algorithm for uniformly attenuated SPECT projections — 226
- 8.10 Other applications of the Landweber-FBP algorithm — 227
- 8.10.1 The Landweber-FBP version of the iterative FBP algorithm — 227
- 8.10.2 Estimation of the initial image's contributions to the iterative Landweber reconstruction — 228
- 8.10.3 FBP implementation of the immediately after-backprojection filtering — 229
- 8.10.4 Real-time selection of iteration number — 230
- 8.11 Summary — 230
- Problems — 231
- Bibliography — 231

## 9 Machine learning — 233

- 9.1 Analytic algorithms versus iterative algorithms versus machine learning algorithms — 233
- 9.2 Basic principles of machine learning — 234
- 9.2.1 Adaptive linear neuron (ADALINE) — 235
- 9.2.2 Universal approximation — 236
- 9.2.3 A deep model for a continuous univariate function — 242
- 9.2.4 When the input is an n-tuple — 245
- 9.2.5 An n-tuple to m-tuple mapping — 246
- 9.3 Image reconstruction as an n-tuple to m-tuple mapping — 249
- 9.4 Convolutional neural network (CNN) as a matched filter for identification — 250
- 9.5 Convolutional neural network (CNN) as a nonlinear denoise filter — 255
- 9.6 Super-resolution — 258
- 9.7 Training — 260
- 9.8 Attention — 261
- 9.9 Perspectives — 262
- 9.10 Summary — 265
- Problem — 266
- Bibliography — 267
- Index — 269

## 1 Basic principles of tomography

This is an introductory chapter that presents the fundamental concepts in tomography. It first defines what the tomography is and shows how a tomographic image can be obtained from its measurements using two simple examples. The concept of projection is then explained. Next, the filtered backprojection (FBP) image reconstruction method is introduced using a point source example. Finally, the concept of backprojection is discussed.

### 1.1 Tomography

The Greek word tomos means a section, a slice, or a cut. Tomography is the process of imaging a cross section. For example, if you are given a watermelon and would like to see inside, the easiest way to do so is to cut it open (Figure 1.1). Clearly, this approach to obtain a cross-sectional image is not a good idea in medicine. Nobody wants to be cut open in order to see what is inside.

![](img/dd555effd38151c67af30d84800c554a_14_0.png)

Fig. 1.1: Cutting open to see what is inside.

Let us look at another example. You are visiting a small park, which is closed for maintenance. You walk around the park and take a few pictures of it. After you get home, you can use your pictures to make a map of the park. To make your life easier, let us assume that there are two large trees in the park, and you take two pictures from the east and the south (Figure 1.2, left). Using these two pictures, you can map out where these two trees are (Figure 1.2, right). This can be done by positioning the pictures at the original orientations at which the pictures were taken, drawing a line from each tree, and finding the intersections. If you have enough pictures, it is not hard to find out where the trees are.

![](img/dd555effd38151c67af30d84800c554a_15_0.png)

Fig. 1.2: Reconstruct a map from two pictures.

Tomography is a mathematical problem. Let us do a fun mathematical exercise here. We have a 2 × 2 matrix. We do not tell you what it is yet. Here are the hints: The sum of the first row is 5, the sum of the second row is 4, the sum of the first column is 7, and the sum of the second column is 2 (see Figure 1.3). Now, you figure out what this 2 × 2 matrix is.

![](img/dd555effd38151c67af30d84800c554a_15_1.png)

Fig. 1.3: A 2 × 2 matrix puzzle.

You can solve this puzzle by setting up a system of linear equations with the matrix entries as unknowns:

x₁ + x₂ = 5,   x₃ + x₄ = 4,   x₁ + x₃ = 7,   and   x₂ + x₄ = 2.   (1.1)

Solving these equations, you will get

x₁ = 3, x₂ = 2, x₃ = 4, and x₄ = 0. (1.2)

Congratulations! You have just mathematically solved a tomography problem. Usually, a tomography problem is solved mathematically; hence, the term “computed tomography” (CT). The row sum or column sum in this example can be generalized as a ray sum, a line integral, or a projection. The procedure to produce a tomographic image from projections is called image reconstruction.

What if the tomography problem gets more complicated? If there are many more trees in the park, taking only two pictures may not provide us enough information to map out the park. If the matrix size is larger than 2 × 2, the row sum and column sum alone do not form enough equations to solve for the matrix entries.

We need more views! For the matrix identification case, we need to sum the matrix diagonally at various angles. In turn, more sophisticated mathematics is required to solve the tomography problem.

### 1.2 Projection

In order to understand the concept of projection (ray sum, line integral, or Radon transform), we will present more examples here.

In the first example, the object is a uniform disk on the x–y plane, the center of the disk is at the origin, and the (linear) density of the disk is ρ (see Figure 1.4). The projection (i.e., the line integral) of this object can be calculated as the chord length t times the linear density ρ, that is,

p(s) = ρt = 2ρ√(R²−s²) if |s| < R; p(s) = 0 otherwise.   (1.3)

In this particular example, the projection p(s) is the same for any view angle θ, which is the orientation of the detector.

If the object is more complicated, the projection p(s, θ) is angle θ dependent (see Figure 1.5).

In the next example we use a point source on the y-axis to further illustrate the angle θ dependency of the projection p(s, θ) (see Figure 1.6). Here we pay attention to the location s of the spike on the one-dimensional detector, which can be evaluated as

s = r sin θ.   (1.4)

This is a sine function with respect to θ. If you display this point source projection data set p(s, θ) in the s–θ coordinate system (see Figure 1.6, right), you will see the trajectory of a sine wave. Because of this observation, people refer to the projection data set as a sinogram.

The fourth example is a discrete object of a 2 × 2 matrix, similar to that in Figure 1.3. The detector is also discrete with four detector bins (see Figure 1.7). Each matrix element
