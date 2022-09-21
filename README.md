# Algorithms-for-Compressive-Sensing
Comparison of L1 Minimization, Iterative Hard Thresholding and Newton Step based Iterative Hard Thresholding Algorithms for Compressive Sensing
#  Comparison of L1 minimization, IHT and NSIHT algorithms for Compressed Sensing 


L1 minimization, IHT and NSIHT are algorithms for compressed sensing which are used to recover the signal x after it undergoes the measurement matrix A to obtain the signal y. 
The obtained signal y is related to the vector x by the equation:
$$y=Ax$$



Here, x is a sparse vector of sparsity s of the order Nx1. A is the measurement matrix mxN. When the sparse vector x undergoes the measurement matrix, we obtain the vector y. 
This signal that we have obtained is now used to recover the original signal x. This can be done by various different algorithms, some of which are discussed in this project.

In this project, we try to determine the performance and efficiency of the three algorithms by comparing them in terms of the probability of recovery of the signal x and the relative errors between the original vector x and the vector recovered from y.


Throughout this tutorial, we show the implementation of the three algorithms. We write the codes in python to implement the algorithms using various libraries in python. 

NOTATION USED:

A is an mxN random gausian measurement matrix.

s is the sparsity level 

x is a Nx1 vector with a sparsity s.

y is obtained by solving y=Ax.

A_trans is the transpose matrix of the matrix A.

I is the identity matrix of the order mxN.

H(s) is the hard thresholding function that turns all values other than the s largest values to be zero. 

h is the step size for the iterations in IHT and NSIHT





## L1 minimization

L1 minimization or basic pursuit is an optimization method. It is a convex problem that can be described as: $$ minimize\; ||z||_{1}    \;\;\;  \;\;subject \;\;to\;\;\; Az=y $$

Input: $$measurement\ matrix\ A,\ measurement\ vector\ y,\ sparsity\ s$$

Instruction:
$$x^n =argmin||z||_{1} \ \  subject\   to\ \   Az=y$$

Output:
$$s \ sparse\ vector\ x^n$$


## Iterative Hard Thresholding (IHT)

In the IHT algorithm, we begin with an initial signal x and it undergoes the iterations as described below till the required value of the vector is obtained. The IHT algorithm can be described as:


Input: $$measurement\ matrix\ A,\ measurement\ vector\ y,\ sparsity\ s ,\ step\ size\ h$$


Initialization: $$s \  sparse \ x^0\  initially \ set \ to\  0$$

Iteration: repeat the steps until a stopping criteria is met
$$x_{n+1} = H_s(x_n +h A^\top(y-Ax_n))$$

Output: the s sparse vector $$x_{n+1}=x_{n}$$

For this algorithm, we consider the stopping criteria to be as long as the number of iterations do not exceed the maximum number of iterations and the tolerence limit is met.

Relative increment:
$$\frac{|| x_{n+1}-x_{n}||}{|| x_{n+1} ||}$$


## Newton Step based Iterative Hard Thresholding (NSIHT)

NSIHT algorithm is based on the IHT algorithm with some improvements in the equation for a better and more accurate output.
It can be described as:

Input: $$measurement\ matrix\ A, \ measurement\ vector\ y, \ sparsity\ s, \ stepsize\ \lambda\ and\ parameter\ \epsilon$$

Iteration: $$x_{p+1}=K_{s}[x^p+\lambda(A^TA+ \epsilon I)^{-1}A^T(y-Ax^p)]$$

Output: s sparse vector $$x^*$$


In this project, we run the algorithms for N_mc number of times (no of monte carlo experiments) for different values of m for the measurement matrix. 
This helps us understand the probability of success recovery by calculating the number of succesful recoveries. Similarly, we calculate the relative error for different values of m which shows the different of recovered vector x[n+1] and the true values of the vector x.


We compare the three algorithms with respect to the values of m with respect to different levels of sparsity

# Parameters for comparrison

1. RELATIVE ERROR $$||(x_{n}-x)||$$
2. RESIDUAL $$||Ax^n-y||$$
3. PROBABILITY OF RECOVERY $$\frac{accurate \ recoveries}{total \ attempts}$$



## BIBLIOGRAPHY

<a href="https://users.math.msu.edu/users/iwenmark/Teaching/MTH994/Holger_Simon_book.pdf">Simon Foucart, Holger Rauhut. "A Mathematical Introduction to Compressive Sensing" 
</a>

<a href="https://www.sciencedirect.com/science/article/pii/S1063520309000384">Thomas Blumensath, Mike E. DavieS. "Iterative hard thresholding for compressed sensing"</a>

<a href="https://arxiv.org/pdf/2001.07181.pdf">Nan Meng, Yun-Bin Zhao. "Newton-Step-Based Hard Thresholding Algorithms for Sparse Signal Recovery"
</a> 

