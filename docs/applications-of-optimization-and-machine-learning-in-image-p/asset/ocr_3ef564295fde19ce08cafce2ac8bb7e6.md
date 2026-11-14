epochs or do not converge. Also, the AUC score of the given model is 1, which provides a verification of an acceptable classification performance.

# 10.6 CONCLUSION AND FUTURE WORK

This chapter proposed a novel CNN-based framework for fire prediction using the fractional order optical flow and the dynamic as well as static features of smoke. The dataset used for experiments contain a total of 16 fire-smoke and 19 non-smoke videos. The dynamic features are estimated as optical flow fields by making use of a variational model based on fraction derivative. The obtained optical flow fields are dense, robust and preserve the moving edges of smoke patterns. The static information is described in terms of smoke color content, which is used in forming a color-based binary mask. Utilizing these binary masks, the smoke active region is successfully segmented from color maps. The proposed CNN architecture has been trained and tested on color maps as well as image dataset. The estimated results are quite better than other existing models. The future scope involves the generalization of the proposed work in determining the fire-smoke fraction in a scene.

# ACKNOWLEDGMENTS

Pushpendra Kumar and Nitish Kumar Mahala acknowledge the support of NBHM, Mumbai for grant no. 02011/24/2021 NBHM (R.P)/R&D-II/8669. Pushpendra Kumar also acknowledges the support of SERB, New Delhi for grant no. EEQ/2020/000154. The author Muzammil Khan thankfully acknowledges MHRD, New Delhi, Government of India.

# REFERENCES

+   1. Sergey V Ablameyko, N Brovko, and R Bogush. Smoke detection in video based on motion and contrast. *Journal of Computer Science and Cybernetics*, 28(3):195–205, 2012.
+   2. Martin Mueller, Peter Karasev, Ivan Kolesov, and Allen Tannenbaum. Optical flow estimation for flame detection in videos. *IEEE Transactions on Image Processing*, 22(7):2786–2797, 2013.
+   3. Arun Singh Pundir and Balasubramanian Raman. Dual deep learning model for image based smoke detection. *Fire Technology*, 55(6):2419–2442, 2019.
+   4. Viet Thang Nguyen, Cong Hoang Quach, and Minh Trien Pham. Video smoke detection for surveillance cameras based on deep learning in indoor environment. In *International Conference on Recent Advances in Signal Processing, Telecommunications & Computing*, 82–86, 2020.