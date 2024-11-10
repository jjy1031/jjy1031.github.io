---
layout: default
title: filter_neb.py
parent: NEB
nav_order: 2
---

# filter_neb.py

This module filters NEB jobs and samples geometries for refinement by extracting calculated energy and validating reactions. The filtering process ensures reaction quality and validity through two main criteria:

Non-convergent reactions: Reactions that fail to converge during optimization are considered unstable and excluded to prevent incomplete or unreliable results.

Transition state validation: Transition states lacking a single negative eigenvalue in their Hessian matrix are filtered out.

Additionally, reactions with energy differences below 5 kcal/mol or insufficient activation energy are excluded. The module also counts significant imaginary frequencies to confirm valid transition states.
