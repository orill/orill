==========
MULTILLABY
==========
Multi-compartment model dispersion and transmutation.

Purpose
-------

MULTILLABY is a general multi-compartment model for nuclide dispersion with the following physical phenomenon:

:mixing: in a compartment volume
:extraction: from one compartment to another compartment (flow at each time interval)
:transfert: instantaneous, from one compartment to another compartment
:deposition: on a compartment walls or inside a filter
:desorption: from one compartment to another compartment
:evaporation: steam distillation, from one compartment to another compartment
:filtration: from one compartment to another
:release: from walls of a compartment or from a filter into another compartment
:decay: between isotopes individualized with one or several chemical form

Isotopes are individualized with one or several chemical form (example Iodine: I2, ICH3 or I aerosol). Parameters can be set for each chemical form, each Z or each isotope.

Up to 64 compartments and 3820 isotopes from ENDF/B-VIII.0.

General Features
----------------

:Small: Code and nuclear data are small (only 500 Ko).
:Fast: Quantities and integral of quantities are computed directly from generalized H. Bateman equations or a stiff ODE solver.
:User friendly: A simple input instruction text file is needed.
:Limits: The choice of the analytical algorithm (generalized H. Bateman) enables maximal speed but loops can only be computed with a stiff ODE solver (example: recirculation of air in a loop from a compartment back to a previous compartment).
