bhSPARSE: A Sparse BLAS Library
========

<br><hr>
<h3>Introduction</h3>

The bhSPARSE provides basic linear algebra subroutines (BLAS) used for sparse matrix computations on heterogeneous parallel processors. Currently, the bhSPARSE library only supports general sparse matrix-matrix multiplication (SpGEMM) operation, using an algorithm described in paper: Weifeng Liu and Brian Vinter, "An Efficient GPU General Sparse Matrix-Matrix Multiplication for Irregular Data," Parallel and Distributed Processing Symposium, 2014 IEEE 28th International (IPDPS '14), pp.370-381, 19-23 May 2014, [LINK](http://dx.doi.org/10.1109/IPDPS.2014.47).

Other sparse BLAS routines are in preparation.

<br><hr>
<h3>Branches</h3>

Now bhSPARSE has two separate branches: CUDA and OpenCL. The CUDA version requires an nVidia GPU, CUDA SDK and CUSP library. The OpenCL version only needs an OpenCL-enabled GPU and OpenCL compiling environment. 

<br><hr>
<h3>Preparation</h3>

To use this SpGEMM program, the first thing you need to do is to change the 'Makefile' with correct CUDA installation path and OpenCL libs path. Further, if you are using a CUDA device, check its compute capability (e.g., 3.5, 5.0 or above) and change item like '-arch=sm_35' if needed. Then you can build the code.

<br><hr>
<h3>Execution</h3>

This program executes C=AB operation, where A, B and C are all sparse matrices. 

You can either (1) use bhSPARSE class and call its SpGEMM method in your own code, or (2) load an off-line square matrix file (*.mtx in matrix market format) as input matrix A, then benchmark C=A^2 operation. In 'main.cpp' file, see function 'test_small_spgemm()' or 'benchmark_spgemm()' for details.

Here are some command-line execution examples using CUDA version:

(1) run SpGEMM on a small matrix

`./spgemm -cuda -spgemm 0`

(2) run SpGEMM on poisson5pt matrices generated by CUSP

`./spgemm -cuda -spgemm 1`

(3) run SpGEMM on poisson9pt matrices generated by CUSP

`./spgemm -cuda -spgemm 2`

(4) run SpGEMM on poisson7pt matrices generated by CUSP

`./spgemm -cuda -spgemm 3`

(5) run SpGEMM on poisson27pt matrices generated by CUSP

`./spgemm -cuda -spgemm 4`

(6) run SpGEMM on a matrix loaded from a matrix market file

`./spgemm -cuda -spgemm cage4.mtx`

(7) run SpGEMM on a matrix loaded from a matrix market file

`./spgemm -cuda -spgemm /home/username/matrices/cage4.mtx`


Here are some command-line execution examples using OpenCL version:

(1) run SpGEMM on a small matrix

`./spgemm -cuda -spgemm 0`

(2) run SpGEMM on a matrix loaded from a matrix market file

`./spgemm -opencl -spgemm cage4.mtx`

(3) run SpGEMM on a matrix loaded from a matrix market file

`./spgemm -opencl -spgemm /home/username/matrices/cage4.mtx`

(4) run SpGEMM (using re-allocatable system memory of AMD APU) on a matrix loaded from a matrix market file

`./spgemm -opencl-hcmp -spgemm /home/username/matrices/cage4.mtx`

<br><hr>
<h3>Tested environments</h3>

The CUDA version has been tested on nVidia GeForce GTX 680, GTX Titan, GTX Titan Black and GTX 980 with CUDA SDK v6.0/v6.5 and CUSP v0.4.0.

The OpenCL version has been tested on AMD Radeon HD 7970, R9 290X and A10-7850k APU with OpenCL v1.2/v2.0.
