---
layout: default
title: filter_neb.py
parent: NEB
nav_order: 2
---

# filter_neb.py

This module filters NEB job directories to identify valid chemical reactions based on energy differences and transition state verification.

| Method         | Description                                                               |
|-----------------|---------------------------------------------------------------------------|
|    `is_valid_rxn`      |  Check if the reaction is valid based on energy.  |
|   ` is_transition_state`  |   Ensures the transition state has exactly one significant imaginary frequency. |

## is_valid_rxn
Reactions with energy differences below 5 kcal/mol or insufficient activation energy are excluded.


## is_transition_state
The module counts significant imaginary frequencies to confirm valid transition states.
