============
Nuclear Data
============

Libraries
---------
ORILL data are parsed from evaluated libraries in ENDF-6 or ACE format by using the `PyNE <https://pyne.io/>`_
toolkit. Parsing features are not provided with ORILL public version. However, data provided with public ORILL have been selected from several libraries in order to cover a wide range of situations:

 - Nuclide set consists of 3820 nuclides from the US Evaluated Nuclear Data `ENDF/B-VII.1 <http://www.nndc.bnl.gov/endf/b7.1/>`_ decay sub-library (**only child branching ratios > 0.1% are selected**)
 - Incident neutron data cover 816 nuclides cross sections and multiplicities from the European Activation File (`EAF 2010 <https://www.oecd-nea.org/dbdata/>`_) at 293.6K: **only (n,2n), (n,3n), (n,fission), (n,gamma), (n,p), (n,d), (n,t), (n,3He), (n,alpha) reactions are selected**
 - Direct (independent) fission yields of 83 nuclides are from TENDL 2011 (`TALYS <http://www.talys.eu/>`_ nuclear model code system, **only yields > 0.01%** are selected)
 - Effective dose coefficients for inhalation (adult, public) includes 1975 nuclides from EAF 2010 and ICRP 72
 - Fluence to effective dose coefficients (rotational) are from ICRP 74

The choice of EAF 2010 and TENDL 2011 instead of ENDF/B-VII.1 has been made to enlarge the data set in terms of available cross sections and fission products. Moreover, independent fission yields are sometimes difficult to measure and the TALYS nuclear model has a good agreement with experimental data.