singular value, indicating that the original image and the rotated transformed image have the same singular value. By the singular value decomposition theorem, we have

$AA^T u = \lambda^2 u, A^T Av = \lambda^2 v$ .

i.e., A and $A^T$ have the same singular value, i.e., the same singular value feature. It is precisely because the singular value feature of the image has the above attributes. The singularity feature is considered to be an ideal algebraic feature. This method can be used in pattern recognition.

For two different frontal face images, we separately carried out singular value decomposition: $A_1 = U_1 \Lambda_1 V_1^T$, $A_2 = U_2 \Lambda_2 A_2^T$. First, to ensure that the orthogonal matrix $U_1, V_1, U_2, V_2$ is unchanged, transform $\Lambda_1, \Lambda_2$ to reconstruct the images separately. After reconstruction, it is easy to see that, although $A_2$ and $U_1 \Lambda_2 V_1^T$ have the same singular value characteristics, both of which characterise two different images. Based on this method to reconstruct the image, it is easy to see that the reconstructed image still represents the same person compared with the original image. The difference is mainly due to the different angles of image acquisition. In the case of face image recognition, it is not sufficient to adopt such a method, and more useful information is included in the two orthogonal matrices U and V decomposed by singular values. Taking into account the orthogonality of U, V, we can get the equation

$\Lambda = U^T AV$ .

Therefore, recognition based on the singular value feature compares and identifies the representation of the face image in different spaces. As the projection transformation is different, i.e., the choice of benchmarks is different, only the use of singular value characteristics for identification is unreasonable. There are two ways to solve these two problems:

+   (1) Extract the identification information contained in the two orthogonal matrices.
(2) The image is projected onto two orthogonal matrices of each class for feature extraction. The mean values of the various classes are calculated and the singular values are decomposed to obtain the two orthogonal matrices U and V of the mean values.

Then, the samples are projected onto U and V and then the feature is extracted. Let the two orthogonal matrices of the i-th class mean be

$U^i = [u_1^i, \dots, u_p^i], V^i = [v_1^i, \dots, v_q^i] (p \geq q)$ .

The feature obtained by projecting the sample $A_x$ into the space may be represented as $[a_1^i, \dots, a_q^i]^T$, where

$a_j = (v_j^i)^T A_x^T u_j^i$ .

Then, we use the feature extraction method. First, a standard image is given to perform singular value decomposition, and the standard symplectic space and the corresponding feature vectors are obtained. An image is represented as a form of a symplectic matrix. If A is an image of the matrix, $B = AA^T$, we call matrix B the feature matrix of image matrix