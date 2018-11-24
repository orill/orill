==================
Usage and download
==================

Download
--------

ORILL is located at `Github <https://github.com/orill/orill/>`_

If you want to contribute, let us know.We have a mailing list located at: orill_code@googlegroups.com

Run test
--------

Uncompress ORILL files in a directory where a Python 2.7+ shell is available (with Scipy). In the Python shell, type:

>>> from ORILL import ORILL_CODE
>>> ORILL_CODE('ORILL_TEST.yml')

The command input file 'ORILL_TEST.yml' located in (/input) subdirectory is processed and the corresponding output files are created in (/output) subdirectory.

Input file syntax
-----------------

Have a look at 'ORILL_TEST.yml' file to understand the file syntax. It is recommended to edit this file with `Notepad++ <https://notepad-plus-plus.org/>`_ with the `YAML <https://en.wikipedia.org/wiki/YAML>`_ markup language.

.. code:: YAML
  
  Flux: [1.0e+14, 1.0e+14, 1.0e+14]
  
  # 3-points flux at [0.0253 eV, 0.5 MeV, 14.0 MeV] (neutron/cm2/s)
  # Fuel depletion: 3-points flux values, adjust the flux multiplier in "Periods:" to adequate Fission Power
  # Transmutation with cold neutrons only: adjust thermal flux with wavelength(cold)/wavelenght(T) factor [adjusted_thermal_flux, 0.0, 0.0]
  
  Nuclides:
   Cl: 0.1
   Na: 0.1
   U-235: 0.1
  
  # Valide nuclides names are: 'U','PU239','94Pu238','PU-240','Bi-194m','BI194M2','83-BI-194m2',...
  # Names are not case sensitive, metastable states are m = m1, m2, m3
  # Elements like 'U','Al','Ni' are converted into isotopes (according natural abundance fraction)
  
  Mass: 10.0
  Unit: 'w'
  
  # Mass (total, grams) used only if Unit = 'w'
  # Unit for nuclides set: mass fraction('w'), grams('g'), mol('mol'), atoms('atm'), becquerels('bq')
  
  Periods: [['Period1', [3600], 1.0, 'MMPA'], ['Period2', [1.0e+3,1.0e+4,1.0e+5], 0.0, 'DIAG']]
  
  # [['Identifier', [Duration(s),...], Flux multiplyer, 'Method'],...]
  # 'Identifier' is used to identifiy output files on each period
  # [Duration(s),...] are durations steps to compute in each period
  # Flux multiplyer: 1.0 (full flux), 0.0 (zero flux, pure decay), 0.5 (50% flux)
  # 'Method' are: 'MMPA', 'BDF' or 'DIAG'
  
  Depth: 6
  
  # Computation depth into chains: 6 to 12 recommanded (more depth = more nuclides = more computation time)
