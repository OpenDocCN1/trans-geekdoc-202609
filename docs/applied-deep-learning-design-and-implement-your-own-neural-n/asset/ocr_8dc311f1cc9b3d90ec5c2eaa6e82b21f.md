# General formulation of the feed-forward network in matrix form

Consider the following training sample data with three samples having two features in each sample:

$$ x = \begin{bmatrix} x_1 & x_2 \\ x_3 & x_4 \\ x_5 & x_6 \end{bmatrix}_{3*2} $$

$$ y = \begin{bmatrix} y_1 \\ y_2 \\ y_3 \end{bmatrix} = \sigma(tanh(xw+b)v+c) $$

$$ xw = \begin{bmatrix} x_1 & x_2 \\ x_3 & x_4 \\ x_5 & x_6 \end{bmatrix}_{3*2} \begin{bmatrix} w_{11} & w_{12} & w_{13} \\ w_{21} & w_{22} & w_{23} \end{bmatrix}_{2*3} $$

$$ xw + b = \begin{bmatrix} x_1 w_{11} + x_2 w_{21} & x_1 w_{12} + x_2 w_{22} & x_1 w_{13} + x_2 w_{23} \\ x_3 w_{11} + x_4 w_{21} & x_3 w_{12} + x_4 w_{22} & x_3 w_{13} + x_4 w_{23} \\ x_5 w_{11} + x_6 w_{21} & x_5 w_{12} + x_6 w_{22} & x_5 w_{12} + x_6 w_{22} \end{bmatrix} + \begin{bmatrix} b_1 & b_2 & b_3 \\ b_1 & b_2 & b_3 \\ b_1 & b_2 & b_3 \end{bmatrix} $$

$$ xw + b = \begin{bmatrix} k_1 & k_2 & k_3 \\ k_4 & k_5 & k_6 \\ k_7 & k_8 & k_9 \end{bmatrix} + \begin{bmatrix} b_1 & b_2 & b_3 \\ b_1 & b_2 & b_3 \\ b_1 & b_2 & b_3 \end{bmatrix} $$

$$ y = \sigma \left( tanh \begin{bmatrix} k_1+b_1 & k_2+b_2 & k_3+b_3 \\ k_4+b_1 & k_5+b_2 & k_6+b_3 \\ k_7+b_1 & k_8+b_2 & k_9+b_3 \end{bmatrix}_{3*3} \right) v + c $$

$$ v = \begin{bmatrix} v_1 \\ v_2 \\ v_3 \end{bmatrix}_{3*1} $$

$$ y = \left[ \sigma \left( tanh \begin{bmatrix} k_1+b_1 & k_2+b_2 & k_3+b_3 \\ k_4+b_1 & k_5+b_2 & k_6+b_3 \\ k_7+b_1 & k_8+b_2 & k_9+b_3 \end{bmatrix}_{3*3} \right) \begin{bmatrix} v_1 \\ v_2 \\ v_3 \end{bmatrix}_{3*1} \right] + c $$

$$ y = \left[ \left( \begin{bmatrix} z_1 & z_2 & z_3 \\ z_4 & z_5 & z_6 \\ z_7 & z_8 & z_9 \end{bmatrix}_{3*3} \right) \begin{bmatrix} v_1 \\ v_2 \\ v_3 \end{bmatrix}_{3*1} \right] + c $$

$$ y = \begin{pmatrix} z_1 \times v_1 + & z_2 \times v_2 + & z_3 \times v_3 \\ z_4 \times v_1 + & z_5 \times v_2 + & z_6 \times v_3 \\ z_7 \times v_1 + & z_8 \times v_2 + & z_9 \times v_3 \end{pmatrix}_{3*1} + c_{1*1} $$

$$ y = \begin{pmatrix} y_1 \\ y_2 \\ y_3 \end{pmatrix}_{3*1} $$