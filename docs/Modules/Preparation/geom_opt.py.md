---
layout: default
title: geom_opt.py
parent: Preparation
nav_order: 2
---

# geom_opt.py

This module get list of all `.xyz` files in input path, optimize the input structures using GFN2-xTB method using BFGS algorithm and store the result with optimized structures with `struc.xyz` in output path.


|  Parameter / Method    |  Tool | Description |
|---------------|-------|---------|
| `XTB` | ASE | xtb calculator in ASE, an extended semiempirical tight-binding model. |
| `BFGS ` | ASE | Local optimization algorithm in ASE.  |
| `write_xyz ` | Dandelion | Store Atom object in the '.xyz' file format. |

