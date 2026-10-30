We are currently witnessing a rapid development in the field of quantum image processing with many exciting opportunities arising from combining classical digital imaging techniques with those enabled by today’s emerging technologies like superconducting qubits, analog signal processors, and neuromorphic microchips. As this technology matures further, it will open up new pathways towards more efficient solutions in terms of speed accuracy and security when tackling complex problems involving large amounts/ types of data such as those encountered in fields like medical imaging or facial recognition, among others [32].

# 2.4 REPRESENTATION OF IMAGES IN QUANTUM COMPUTING

The fundamental difference between classical and quantum computers necessitates different formats for representation of images on a quantum computer. There are multiple such formats, namely Flexible Representation of Quantum Images (FRQI) [7], Real Ket image format [6], and Qubit Lattice format [33].

# 2.4.1 Flexible Representation of Quantum Images (FRQI)

Le et al. [7] proposed a more sophisticated qubit utilizing the lattice’s quantum state superposition. While adding a second qubit to represent each pixel’s position in space, the approach continues to convert each pixel’s greyscale value to amplitude. The entire image then enters a significant quantum superposition state. Each image is a combination of pixel, and each pixel is a qubit state in superposition, as shown in the Equations 2.1 and 2.2.

|pixel_i⟩ = cos θ_i |0⟩ + sin θ_i |1⟩
θ_i ∈ [0, π/2], i = 0,1,...,2^{2n} - 1   (2.1)

|image⟩ = 1/2^n Σ_{i=0}^{2^{2n}-1} (cos θ_i |0⟩ + sin θ_i |1⟩) ⊗ |i⟩   (2.2)
i = pixels encoding in terms of qubit state

As an example, a 2 × 2 image can be represented as in Table. 2.1 [34].

Table 2.1 FRQI image representation
| θ0, |00⟩ | θ1, |01⟩ |
| θ2, |10⟩ | θ3, |11⟩ |