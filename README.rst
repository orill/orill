===========================================
`ORILL Code <http://orill.readthedocs.io>`_
===========================================

Purpose
-------

ORILL Code is a 1D transmutation, fuel depletion (burn-up), and radiological protection code useful for nuclear research reactors design and operational safety. ORILL has been cooked at the **Nuclear Safety Unit** of the `Institut Laue Langevin (ILL) <http://www.ill.eu>`_, Grenoble, France. 

General Features
----------------

:Small: Code and nuclear data are small (only 4 Mo).
:Fast: Vectorization and parallelization associated with Scipy is transparently available.
:User friendly: ORILL is designed to address practical questions about isotopes inventories, decay heat, dose rate, photons spectrum. It is usable by everyone for 1D point-flux calculation at the speed of light.

Prerequisites
-------------
ORILL needs only Python 2.7 or later, with `Numpy <http://www.numpy.org/>`_, `Scipy <https://www.scipy.org/>`_ and standard modules installed (re, io, yaml, time). Python is available on all platforms (WinPhyton, MiniConda, Debian/Ubuntu).


Installation
------------

Uncompress ORILL files in a directory where a Python 2.7+ shell is available (with Numpy and Scipy). In the Python shell, type:

>>> from ORILL import ORILL_CODE
>>> ORILL_CODE('ORILL_TEST.yml')

The command input file 'ORILL_TEST.yml' located in (/input) subdirectory is processed and the corresponding output files are created in (/output) subdirectory. Have a look at ORILL_TEST.yml file to understand the file syntax. It is recommended to edit this file with `Notepad++ <https://notepad-plus-plus.org/>`_ with the `YAML <https://en.wikipedia.org/wiki/YAML>`_ markup language.


Contribute
----------

If you want to contribute, let us know.We have a mailing list located at: orill_code@googlegroups.com

Support
-------

If you are having issues, please let us know.
We have a mailing list located at: orill_code@googlegroups.com

License
-------

**© Copyright 2017-2018**, Franck CHANTELOUP, all rights reserved. ORILL Code is for educational purpose.

````

Redistribution and use in source and binary forms, **without** modification,
are permitted provided that the following conditions are met:

1. Redistribution of source code must retain the above copyright notice, this list of conditions and the following disclaimer.
2. Redistribution in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NON INFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.