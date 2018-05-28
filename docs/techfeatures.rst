==================
Technical features
==================

Neutron flux spectrum
---------------------

The neutron flux is specially formatted in **1-point thermal flux and 2-points fast flux: 0.0253 eV, 0.5 MeV and 14 MeV** respectively.
For thermal and cold neutrons transmutation, only the thermal value is useful.
For fuel depletion, only the relative values of thermal and fast neutrons are useful (because of threshold reactions).
A multiplication factor can be used to adjust the fission power to the right value, without changing the flux shape.

Evolution algorithm
-------------------

The choice of the algorithm (Bateman/TTA, LSODA, Matrix Exponential, Runge-Kutta,...) is a tricky problem in case of loops and stiffness in nuclides chains.
After some trials, only three methods have be selected.

MMPA
^^^^

Mini-Max Polynomial Approximation (`MMPA <https://doi.org/10.1016/j.anucene.2015.02.015>`_) of matrix exponential can be used in ORILL.
It is extremely simple to code on sparse matrix, and has several advantages over Chebyshev Rational Approximation Method (CRAM).
MMPA method is very stable.
It is described by Yosuke Kawamoto and al.,
*Numerical solution of matrix exponential in burn-up equation using mini-max polynomial approximation,
Annals of Nuclear Energy, Volume 80, 2015, Pages 219-224*.

BDF
^^^

ORILL can use the Backward Differentiation Formula
(`BDF <https://en.wikipedia.org/wiki/Backward_differentiation_formula>`_ order 2) as provided with Scipy to solve the stiff differential equations.
BDF is a little bit faster than MMPA and the difference with MMPA is generally < 2%.
This method is generally stable, but instabilities can occur sometimes.

DIAG
^^^^

The DIAG method works with the diagonalization of the evolution matrix.
If diagonalization is possible, each eigenvalue is the decay constant of the corresponding eigenvector.
Then, computing nuclides at numerous time steps is very easy. Pure decay matrix are often diagonalizable.
Unfortunately, burn-up matrix with numerous fission products are not, because of too much forks and loops inside the chains.
If diagonalization is impossible, the DIAG method will fail.

Inside ORILL engine
-------------------

ORILL uses widely Python dictionaries to store data (.npy), but all data are translated into Numpy arrays and Scipy csc.cparse.matrix before hard computation.
Nuclide names are translated in ZAAAm numbers, like 'Am-242m' in 952421, or 'He-4' in 20040.
N nuclides in a dataset are sorted on an index [0,1,...,N-1].
The data set is computed at the beginning: it depends on the problem and on the computation depth into chains (set by the user).
The pure decay matrix is pre-computed since values are independent of neutron flux.