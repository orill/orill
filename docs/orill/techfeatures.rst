==================
Technical features
==================

Neutron flux spectrum
---------------------

The neutron flux is specially formatted in:

 - 1-point **thermal** flux at **0.0253 eV**
 - 2-points **fast** flux at **neutron fission spectrum average (U-235)** and **14 MeV**
 
For thermal and cold neutrons transmutation, only the thermal value is useful.
For fuel depletion, only the relative values of thermal and fast neutrons are useful (because of threshold reactions).
A multiplication factor can be used to adjust the fission power to the right value, without changing the flux shape.

Evolution algorithm
-------------------

The choice of the algorithm (Bateman/TTA, Matrix Exponential, Runge-Kutta, Adams, BDF...) is a tricky problem in case of loops and stiffness in nuclides chains.
After some trials, only three methods were selected.

BDF
^^^

ORILL can use the F77 `VODE <http://dx.doi.org/10.1137/0910062>`_ code (*Brown, Byrne, Hindmarsh, 1989*) with Backward Differentiation Formula (BDF)
as provided with Python/Scipy to solve the stiff differential equations.
VODE/BDF is faster than MMPA on old CPU and the difference with MMPA is generally < 2%.
This method is generally stable, but instabilities can occur sometimes.

MMPA
^^^^

Mini-Max Polynomial Approximation `MMPA <http://dx.doi.org/10.1016/j.anucene.2015.02.015>`_ of matrix exponential can be used in ORILL.
It is extremely simple to code on sparse matrix, and has several advantages over Chebyshev Rational Approximation Method (CRAM).
MMPA method is very stable.
It is described by *Yosuke Kawamoto and al.,
Numerical solution of matrix exponential in burn-up equation using mini-max polynomial approximation,
Annals of Nuclear Energy, Volume 80, 2015, Pages 219-224*.

DIAG
^^^^

The DIAG method uses diagonalization of the evolution matrix in **C** field, which is a more general
analytical method than the classic Bateman / TTA.
If diagonalization is possible, each eigenvalue is the pseudo decay constant of the corresponding eigenvector.
A decay matrix is always diagonalizable because
it hasn't any loop and it can be rearranged into a lower triangular matrix with its real eigenvalues
on the diagonal.
Unfortunately, large burn-up matrix with loops in transmutation chains due to neutron absorbtion are not
always diagonalizable in **C** field with enough accuracy.
If diagonalization is impossible, the DIAG method will fail.

Inside ORILL engine 
-------------------

Nuclide names are translated in ZAAAm numbers, like 'Am-242m' in 952421, or 'He-4' in 20040.
ORILL uses Python dictionaries and Numpy arrays to process data before hard computation.
A nuclide set is defined at the beginning: it depends on the problem and on the computation depth into chains (set by the user).
In the set, nuclides are sorted on an index [0,1,...,N-1], from which a sparse
evolution matrix is build. The sparse matrix is processed with previously described numerical methods.
At the end of each time step, the desired values are computed and the nuclide list is build back from the index.
