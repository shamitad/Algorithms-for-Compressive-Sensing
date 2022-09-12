# Algorithms-for-Compressive-Sensing
Comparison of L1 Minimization, Iterative Hard Thresholding (IHT) and Newton Step based Iterative Hard Thresholding Algorithms (NSIHT) for Compressive Sensing

Project completed as part of MITACS GRI program.

Notation-

A is an Nxm random gausian measurement matrix. [A=A/||A||] 

x is a Nx1 vector with a sparsity s.

y is obtained by solving y=Ax.

A_trans is the transpose of measurement matrix.

I is the identity matrix 

h is the stepsize for IHT ans NSIHT

e is the parameter greater than 0 such that A*A_trans+ eI is positive definite 
______________________________________________________________________________________________________________________________________________

L1 MINIMIZATION or BASIC PURSUIT

( algorithm for L1 Minimization as explained in the book A Mathematical Introduction to Compressive Sensing by Simon Foucart, Holger Rauhut )

Input: measurement matrix A, measurement vector y.

Instruction:
x#= argmin ||z|| subject to Az = y. (BP)

Output: the vector x#

________________________________________________________________________________________________________________________________________________

IHT

( algorithm as explained in the paper Iterative hard thresholding for compressed sensing by Thomas Blumensath, Mike E. Davies )

Input: measurement matrix A, measurement vector y, sparsity level s.

Initialization: s-sparse vector x0 = 0.

Iteration: repeat the following step until a stopping criterion is met 
x[n+1] = Hs(x[n]+h A_trans(y-Ax[n]))

Output: the s-sparse vector x[n+1]

Hs is the non-linear operator that sets all but the largest (in magnitude) s elements of a to zero

________________________________________________________________________________________________________________________________________________


NSIHT

( algorithm as explained in the paper Newton-Step-Based Hard Thresholding Algorithms for Sparse Signal Recovery by Nan Meng and Yun-Bin Zhao )

Input: measurement matrix A, measurement vector y, sparsity level s.

Initialization: s-sparse vector x0 = 0.

Iteration: repeat the following step until a stopping criterion is met 
x[n+1] = Hs(x[n]+h((A_transA+eI)^-1)A_trans(y-Ax[n]))

Output: the s-sparse vector x[n+1]

________________________________________________________________________________________________________________________________________________









