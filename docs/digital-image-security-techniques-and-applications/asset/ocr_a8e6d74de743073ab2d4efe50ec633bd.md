image. In Eq. (5.20), R₁W is the upper triangular matrix for HL₁W sub-band. In Eq. (5.21), d₁W is the diagonal component of R₁W, and D₁W is the diagonal matrix corresponding to d₁W. In Eq. (5.22), R₂W is the upper triangular matrix for LH₁W sub-band. In Eq. (5.23), d₂W is the diagonal component of R₂W, and D₂W is the diagonal matrix corresponding to d₂W.

[Q₁W,R₁W] = qr(HL₁W) (5.20)

{ d₁W = diag(R₁W) 
  D₁W = diag(d₁W) } (5.21)

[Q₂W,R₂W] = qr(LH₁W) (5.22)

{ d₂W = diag(R₂W) 
  D₂W = diag(d₂W) } (5.23)

**Step 4:** Apply inverse process as shown in Eqs. (5.24) and (5.25):

sw₁ = (D₁W − D₁)/α (5.24)

sw₂ = (D₂W − D₂)/α (5.25)

where sw₁ and sw₂ are the extracted diagonal components corresponding to their watermark images.

**Step 5:** Add the above extracted diagonal components corresponding to their components, excluding diagonals (s₁₋W and s₂₋W).

**Step 6:** Apply inverse QR decomposition and LWT to get the first watermark image back.

**Step 7:** Apply inverse QR decomposition, Hénon decryption, and inverse LWT to get the second watermark image back.

# 5.4 SIMULATION RESULTS AND DISCUSSION

The proposed algorithm is implemented with the help of MATLAB R2017a installed in the system with specifications as Lenovo 11th generation Intel(R) Core (TM) i5-1135G7 @ 2.40GHz - 2.42 GHz. The proposed watermarking method is tested on an ultrasound image of the liver of three different patients taken from the cancer imaging archive [6] shown in Figure 5.6, and two watermark images are used, shown in Figure 5.7. The cameraman image is the first watermark image, and the details of the patient are the