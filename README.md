# Frank-Wolfe Methods for SVM Training

### Papers
   * Revisiting Frank-Wolfe: Projection-Free Sparse Convex Optimization (Jaggi, 2013)
   * On the Global Linear Convergence of Frank-Wolfe Optimization Variants (Lacoste-Julien, Jaggi, 2015)
   * An Equivalence between the Lasso and Support Vector Machines (Jaggi, 2014)
   
### Tasks
In this notebook we will implement:
   * Frank-Wolfe Algorithm
   * Away-Step Frank-Wolfe
   * Pairwise Frank-Wolfe
   * Fully Corrective Frank Wolfe
  

to train **soft-margin SVM** on the following datasets:
   * [Australian](https://www.csie.ntu.edu.tw/~cjlin/libsvmtools/datasets/binary.html#australian)
   * [Breast Cancer](https://www.csie.ntu.edu.tw/~cjlin/libsvmtools/datasets/binary.html#breast-cancer)
   * [Mushrooms](https://www.csie.ntu.edu.tw/~cjlin/libsvmtools/datasets/binary.html#mushrooms)
   * [Phishing](https://www.csie.ntu.edu.tw/~cjlin/libsvmtools/datasets/binary.html#phishing)

At the end we will compare the perfomace of the algorithms with each other.


## Description of the Problem
To train soft marging SVM we will formulate the optimization as follows:

$$
min_{w, \xi}  \frac{1}{2} w^{T}w + \frac{C}{2} \sum_{i=1}^{N}\xi_{i}^2
$$

$$
s.t.
$$

$$
y_{i}(wx_{i} + b)\geq 1 - \xi{i}
$$

$$
\xi{i} \geq 0
$$

This is known as the *Primal* problem.

We can transform the *primal* problem into a *dual* one by constructing the lagrangian and applying the KKT conditions. After doing so we find:

Lagrangian of the Dual Problem

$$
L_{D} = -\frac{1}{2C}\sum_{i=1}^{N}\alpha_{i}^2 - \frac{1}{2}\sum_{i=1}^{N}\sum_{j=1}^{N}\alpha_{i}\alpha_{j}y_{i}y_{j}x_{i}^{T}x_{j}
$$

$$
s.t.
$$
$$
\alpha_{i} >= 0
\sum_{i=1}^{N}\alpha_{i} = 1
$$

Which is equivalent to:

$$
min_{\alpha} L_{D} = \frac{1}{2}\sum_{i=1}^{N}\sum_{j=1}^{N}\alpha_{i}\alpha_{j}y_{i}y_{j}x_{i}^{T}x_{j} + \frac{1}{2C}\sum_{i=1}^{N}\alpha_{i}^2
$$

$$
s.t.
$$
$$
\alpha_{i} >= 0
$$

$$  
\sum_{i=1}^{N}\alpha_{i} = 1
$$


We will use Frank-Wolfe and variations of Frank-Wolfe to solve this minimization problem.

### Collaborators
  * Gita Rayung Andadari gitarayung.andadari@studenti.unipd.it
  * Endrit Sveçla endrit.svecla@studenti.unipd.it
  * Santiago Viquez santiago.viquezsegura@studenti.unipd.it 
