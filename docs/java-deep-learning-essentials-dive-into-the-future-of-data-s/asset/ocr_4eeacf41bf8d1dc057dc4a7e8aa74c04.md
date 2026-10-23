To proceed with this equation, we define the following:

$\delta_{ij}^{(k)} := \frac{\partial E}{\partial a_{ij}^{(k)}}$

We also define:

$c_{ij}^{(k)} := z_{ij}^{(k)} + b^{(k)}$

With these, we get:

$\frac{\partial E}{\partial b^{(k)}} = \sum_{i=0}^{M-m} \sum_{j=0}^{N-n} \delta_{ij}^{(k)} \frac{\partial a_{ij}^{(k)}}{\partial c_{ij}^{(k)}} \frac{\partial c_{j}^{(k)}}{\partial b_{(k)}}$ 
$= \sum_{i=0}^{M-m} \sum_{j=0}^{N-n} \delta_{ij}^{(k)} h'\left(c_{ij}^{(k)}\right)$

We can calculate the gradient of the weight (kernel) in the same way:

$\frac{\partial E}{\partial w_{st}^{(k,c)}} = \sum_{i=0}^{M-m} \sum_{j=0}^{N-n} \frac{\partial E}{\partial z_{ij}^{(k)}} \frac{\partial z_{ij}^{(k)}}{\partial w_{st}^{(k,c)}}$ 
$= \sum_{i=0}^{M-m} \sum_{j=0}^{N-n} \frac{\partial E}{\partial z_{ij}^{(k)}} \frac{\partial a_{ij}^{(k)}}{\partial z_{ij}^{(k)}} x_{(i+s)(j+t)}^{(c)}$ 
$= \sum_{i=0}^{M-m} \sum_{j=0}^{N-n} \delta_{ij}^{(k)} h'\left(c_{ij}^{(k)}\right) x_{(i+s)(j+t)}^{(c)}$