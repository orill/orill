==========
MULTILLABY
==========
Multi-compartment model dispersion and transmutation.

Purpose
-------

MULTILLABY is a multi-compartment model for nuclide dispersion with the following physical phenomenon:

:mixing: in a compartment volume
:transfert: from one compartment to another compartment
:deposition: on a compartment walls or inside a filter
:filtration: from one compartment to another
:release: from walls of a compartment or from a filter into another compartment
:decay: between isotopes individualized with one or several chemical form

Isotopes are individualized with one or several chemical form (example Iodine: I2, ICH3 or I aerosol). Parameters of each physical phenomenon can be set for each chemical form.

General Features
----------------

:Small: Code and nuclear data are small (only 200 Ko).
:Fast: Quantities and integral of quantities are computed directly from generalized H. Bateman equations.
:User friendly: A simple input instruction text file is needed.
:Limits: The choice of the algorithm enables maximal speed and precision but loops are not possible (example: recirculation of air in a loop from a compartment back to a previous compartment is not computed).
