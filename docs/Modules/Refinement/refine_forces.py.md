---
layout: default
title: refine_forces.py
parent: Refinement
nav_order: 2
---

# refine_forces.py

Using ORCA, this module reads all the labels of explored structures from an input HDF5 file and computes energies and forces. The calculations employ DFT with the wB97X functional and the 6-31G basis set. The results are stored in an ASE database. Ensure that you provide the exact path to the ORCA binary file.
