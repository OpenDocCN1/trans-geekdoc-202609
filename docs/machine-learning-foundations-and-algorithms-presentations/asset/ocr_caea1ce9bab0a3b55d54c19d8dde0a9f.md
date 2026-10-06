# Comparison

+   - Ridge Regression

$f(\mathbf{x}) = \phi(\mathbf{x})^T \mathbf{w}^* = \phi(\mathbf{x})^T (\Phi^T \Phi + \lambda \mathbf{I})^{-1} \Phi^T \mathbf{y} = \sum_{i=1}^d w_i \phi_i(\mathbf{x})$
$d 	imes d$ matrix inversion

+   - Use if d < N

+   - Kernel Ridge Regression

$f(\mathbf{x}) = \phi(\mathbf{x})^T \mathbf{w}^* = \phi(\mathbf{x})^T \Phi (\Phi \Phi^T + \lambda \mathbf{I})^{-1} \ \mathbf{y} = \sum_{i=1}^N \alpha_i k(\mathbf{x}, \mathbf{x}_i)$
$N 	imes N$ matrix inversion

+   - Use if N < d