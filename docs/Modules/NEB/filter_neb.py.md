---
layout: default
title: filter_neb.py
parent: NEB
nav_order: 2
---

# filter_neb.py

This module filters NEB jobs and samples geometries for refinement by extracting calculated energy and validating reactions. Non-convergent reactions and transition states lacking a single negative eigenvalue in their Hessian matrix are filtered out. Additionally, reactions with energy differences below 5 kcal/mol or insufficient activation energy are excluded. The module also counts significant imaginary frequencies to confirm valid transition states. The NEB data filtering process includes criteria to prevent redundancy in similar structural data. A new band is only sampled when the cumulative sum of 𝐹max exceeds 0.1 eV/Å since the last inclusion. This approach helps save computational resources and avoids overfitting to narrow regions of the PES. The filtered final structures then undergo high-level refinement.
